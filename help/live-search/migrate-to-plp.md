---
title: Migreren van zoekadapter naar PLP-widget
description: Leer hoe te van de afgekeurde onderzoeksadapter aan de  [!DNL Live Search]  Van de Lijst van het Product de Widget van de Pagina migreren.
source-git-commit: 8811f0f271928fbc827e5a0164542da473c57224
workflow-type: tm+mt
source-wordcount: '2053'
ht-degree: 0%

---

# Migreren van zoekadapter naar PLP-widget

De onderzoeksadapter is [&#x200B; afgekeurd &#x200B;](release-notes.md#live-search-400) vanaf [!DNL Live Search] 4.0.0 en zal slechts veiligheidsupdates ontvangen. De [&#x200B; Van de Lijst van het Product van de Pagina (PLP) Widget &#x200B;](plp-styling.md) is de gesteunde oplossing voor alle [!DNL Live Search] implementaties die door:gaan. Deze gids helpt u begrijpen wanneer de migratie ongecompliceerd is en wanneer het extra werk wordt vereist.

## Vereisten

Zorg ervoor dat uw omgeving aan deze vereisten voldoet voordat u het migratieproces start.

Voordat u de migratie start:

**Technische vereisten**:

- Adobe Commerce 2.4.4 of hoger.
- [!DNL Live Search] is geïnstalleerd.
- Toegang tot de bevellijn (CLI).
- Toegang tot de Commerce Admin.
- Staging- of QA-omgeving voor testen.

**Steun en voorbereiding**:

1. Maak een back-up van uw database en code.
1. Huidige aanpassingen documenteren.
1. Het overzicht [&#x200B; Grenzen en Beperkingen &#x200B;](boundaries-limits.md) om ervoor te zorgen dat de PLOP widget aan uw behoeften voldoet.
1. De migratie van het programma tijdens een laag-verkeersperiode.
1. Belanghebbenden op de hoogte stellen van mogelijke wijzigingen in het verkoopgedrag.

**herzie de huidige implementatie**:

- Controleer de huidige [!DNL Live Search] versie.
- Document met de gebruikte facetten en hun configuratie.
- Test alle zoekfunctionaliteit en documentgedrag.
- Leg schermafbeeldingen van de huidige presentatie met zoekresultaten vast.

**de verenigbaarheid van de Versie**:

- Bezig met uitvoeren van Adobe Commerce 2.4.4 of hoger.
- Klaar om te upgraden naar [!DNL Live Search] 4.0.0 of hoger.

## Migratiescenario&#39;s

### Eenvoudige migratie (geen extra werk vereist)

U kunt rechtstreeks naar de PLP-widget migreren als uw implementatie aan alle volgende criteria voldoet:

**Standaard op Luma-Gebaseerde storefront**:

- U gebruikt het thema Luma of een thema dat overerft van Luma met minimale aanpassingen.
- U hebt geen aangepaste wijzigingen aangebracht in PLP-indelingen of -sjablonen.
- U hebt geen aangepaste JavaScript-extensies gemaakt die reageren op zoekresultaten.

**Standaard productcatalogus**:

- Alle productkenmerken gebruiken standaardbronmodellen (geen aangepaste bronmodellen).
- Er zijn geen aangepaste producttypen waarvoor speciale renderinglogica vereist is.
- In uw catalogus worden alleen standaardfacetten en filters gebruikt.

**Standaard integraties**:

- U gebruikt Google Tag Manager (GTM) niet voor analyses.
- U gebruikt geen extensies van derden die het zoekgedrag wijzigen.

Als uw implementatie deze criteria aanpast, ga aan [&#x200B; Standaard migratiestappen &#x200B;](#standard-migration-steps) te werk.

### Migratie vereist extra werk

Extra werk is vereist als uw implementatie om het even welke volgend heeft:

**de themawijzigingen van de Douane**:

- Aangepaste PLP-indelingen die Luminasjablonen overschrijven.
- Aangepaste CSS of JavaScript die zich richt op elementen die specifiek zijn voor de zoekadapter.
- Aangepaste sjabloonwijzigingen voor PLP- of verwante bestanden.
- Thema overerft niet van Luma (bijvoorbeeld een volledig aangepast thema).

**de productattributen van de Douane**:

- Productkenmerken met aangepaste bronmodellen die als facetten worden gebruikt.
- Aangepaste producttypen met speciale weergavevereisten.
- Programmatische kenmerken met `"is_user_defined": false` .

**Geavanceerde integraties**:

- Google Tag Manager (GTM) wordt actief gebruikt voor tracering.
- Hulpprogramma&#39;s voor analyse of personalisatie van derden die zijn geïntegreerd in de zoekfunctie.
- Aangepaste gebeurtenistracering of implementatie van gegevenslagen.
- Integratie met externe zoek- of aanbevolen engines.

**Headless of de implementaties van PWA**:

- De architectuur zonder kop gebruiken (bijvoorbeeld PWA Studio, Vue Storefront).
- Aangepast frontend framework (React, Vue, Angular).
- GraphQL alleen gebruiken voor catalogusquery&#39;s.
- Implementatie van aangepaste storefront-gebeurtenissen.

**de widgetcode van de Douane**:

- De code van de zoekadapter is eerder aangepast.
- Aangepaste versies van widgets hosten op uw eigen CDN.
- Aangepaste JavaScript-extensies voor zoekfunctionaliteit.

Als uw implementatie om het even welk van deze scenario&#39;s heeft, zie [&#x200B; Complexe migratiescenario&#39;s &#x200B;](#complex-migration-scenarios).

## Standaardmigratiestappen

Voer de volgende stappen uit voor implementaties zonder speciale aanpassingen:

### Stap 1: Upgrade uitvoeren [!DNL Live Search]

Voer een upgrade van de extensie [!DNL Live Search] naar versie 4.0 of hoger uit om toegang te krijgen tot de PLP-widget.

**Rol**: Merchant of Partner

1. Controleer de huidige [!DNL Live Search] versie:

   ```bash
   composer show magento/live-search | grep version
   ```

1. Als u versie 3.x of eerder gebruikt, schakelt u de module AdvancedSearch in voordat u de upgrade uitvoert:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

1. Werk `composer.json` bij om [!DNL Live Search] 4.0 of hoger te vereisen:

   ```json
   "require": {
      "magento/live-search": "^4.0"
   }
   ```

1. Voer de upgrade uit:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

1. Voer de installatie-upgrade uit en compileer opnieuw:

   ```bash
   bin/magento setup:upgrade
   bin/magento setup:di:compile
   ```

1. Statische inhoud implementeren, indien nodig:

   ```bash
   bin/magento setup:static-content:deploy
   ```

### Stap 2: De PLP-widget inschakelen

Configureer de PLP-widget in Commerce Admin.

**Rol**: Merchant

De PLP-widget is standaard ingeschakeld voor nieuwe installaties van [!DNL Live Search] 4.0.0+. Als u een upgrade uitvoert vanaf een eerdere versie:

1. Ga naar **[!UICONTROL Stores]** > Instellingen > **[!UICONTROL Configuration]** .
1. Ga naar **[!UICONTROL Live Search]** > **[!UICONTROL Storefront Features]**.
1. Vouw de sectie **[!UICONTROL Storefront Features]** uit.
1. Plaats **[!UICONTROL Enable Product Listing Widgets]** aan **ja**.
1. Klik op **[!UICONTROL Save Config]**.
1. Maak de cache leeg: **[!UICONTROL System]** > Gereedschappen > **[!UICONTROL Cache Management]** > **[!UICONTROL Flush Magento Cache]** .

### Stap 3: Testen op afbouw

Valideer de migratie in een niet-productieomgeving voordat u live gaat.

**Rol**: Merchant/Partner

Voordat u gaat implementeren naar productie, moet u de zoekfunctionaliteit grondig testen:

**Functionele het testen**:

- Controleer of de zoekresultaten correct worden weergegeven.
- Test alle geconfigureerde facetten.
- Controleer of de categorienavigatie werkt.
- Test paginering door resultaten.
- Controleer of de sorteeropties naar behoren werken.
- De functionaliteit van de test toe:voegen-aan-kart voor eenvoudige producten.

**Visuele het testen**:

- Controleer of de afbeeldingen correct worden weergegeven.
- Controleren of productnamen en prijzen correct worden weergegeven.
- Kleurstalen testen (indien van toepassing).
- Controleer het responsieve gedrag op mobiele apparaten.
- Controleer of de stijl overeenkomt met uw merk.

**het testen van Prestaties**:

- De laadtijden van de pagina meten.
- Testen met realistische catalogusgrootte.
- Het gebruik van de serverbron controleren.
- Controleer de browserconsole op JavaScript-fouten.

### Stap 4: Distribueren naar productie

Verplaats de gevalideerde configuratie naar uw live winkel.

**Rol**: Merchant/Partner

1. Plan indien mogelijk de implementatie tijdens het onderhoudsvenster.
1. Volg uw standaard implementatieproces.
1. Laat PLP widget in productie toe gebruikend [&#x200B; Stap 2: laat PLP widget &#x200B;](#step-2-enable-the-plp-widget) toe.
1. Bewaak onmiddellijk na de implementatie op eventuele problemen.
1. Hebt u een terugdraaiplan klaar als zich kritieke problemen voordoen.

### Stap 5: Valideren en controleren

Traceer de zoekprestaties en de klantervaring na de migratie.

**Rol**: Merchant

Na plaatsing, controleer zeer belangrijke metriek:

- Zoeksnelheid met nul resultaten
- Omzetsnelheid zoeken naar winkelwagentje
- Prestaties bij laden van pagina
- Feedback van de klant of ondersteuningstickets
- JavaScript-fouten in browserconsole

## Complexe migratiescenario&#39;s

De volgende scenario&#39;s vereisen extra planning, douaneontwikkeling, of gespecialiseerde steun voorbij de standaardmigratiestappen.

### Aangepast thema met layoutwijzigingen

In dit scenario hebt u aangepaste sjablonen of lay-outs die het standaardgedrag voor het aanbieden van producten overschrijven.

**Rol**: Ontwikkelaar/Partner

1. **de aanpassingen van de Controle**:
   - Documenteer alle XML-bestanden met aangepaste layout in uw thema.
   - Bekijk eventuele wijzigingen in de aangepaste sjabloon op pagina&#39;s met productaanbiedingen of verwante bestanden.
   - Identificeer aangepaste CSS-klassen die voor opmaak worden gebruikt.
   - Aangepaste JavaScript-interacties documenteren.

1. **migreren aan op CSS-Gebaseerde aanpassingen**:
   - De PLP widget gebruikt specifieke CSS klassen (zie [&#x200B; PLP het stileren gids &#x200B;](plp-styling.md)).
   - Maak opnieuw visuele aanpassingen met behulp van de CSS-klassen van de PLP-widget.
   - Testen of aangepaste stijlen correct worden toegepast.

1. **verwijder conflicterende aanpassingen**:
   - Verwijder layout-XML die de structuur van de productlijst wijzigt.
   - JavaScript opschonen die zich richt op specifieke elementen voor zoekadapters.
   - Sjabloon bijwerken overschrijft dat conflict met widgetrendering.

1. **Test grondig**:
   - Controleer of alle visuele aanpassingen werken met de PLP-widget.
   - Zorg ervoor dat er geen layoutconflicten optreden.
   - Testen op alle onderbrekingspunten en apparaten.

### Productkenmerken met aangepaste bronmodellen

In dit scenario beschikt u over facetten die productkenmerken gebruiken met aangepaste bronmodellen die niet worden ondersteund door de zoekadapter, maar wel door de PLP-widget.

**Rol**: Merchant (configuratie Admin)

1. **identificeer beïnvloede attributen**:
   - Productkenmerken bekijken die als facetten worden gebruikt.
   - Bepaal welke aangepaste bronmodellen worden gebruikt.
   - Huidige facetconfiguratie van document.

1. **Bevorder en laat PLP widget** toe:
   - Volg [&#x200B; Standaardmigratiestappen &#x200B;](#standard-migration-steps).
   - De PLP-widget ondersteunt aangepaste bronmodelkenmerken.

1. **opnieuw samenstellen facetten**:
   - Ga naar **[!UICONTROL Marketing]** > SEO &amp; Search > **[!UICONTROL Live Search]** .
   - De facetconfiguratie van het overzicht voor beïnvloede attributen.
   - Testfacetten werken correct met aangepaste bronmodellen.

1. **bevestigt**:
   - Het filtreren van de test met de facetten van het douanebronmodel.
   - Controleer of alle kenmerkwaarden correct worden weergegeven.
   - Zorg ervoor dat de prestaties acceptabel zijn.

### Integratie van Google Tag Manager (GTM)

In dit scenario is het bekend dat het inschakelen van de PLP-widget ertoe kan leiden dat GTM mislukt.

**Rol**: Ontwikkelaar/Partner + de Techniek van de Klant

**Optie 1: Ga met onderzoeksadapter (tussentijds slechts)** verder

- Zorg dat de zoekadapter ingeschakeld blijft als GTM bedrijfskritiek is.
- Begrijp dat u alleen beveiligingsupdates ontvangt.
- Plan voor migratie wanneer de GTM-compatibiliteit is opgelost.
- Neem contact op met Adobe Support voor updates over GTM-compatibiliteit.

**Optie 2: Migreer GTM het volgen aan een alternatieve benadering**

1. **voer een inzameling van de douanegebeurtenis** uit:

   - Gebruik [&#x200B; Storefront Gebeurtenissen SDK &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/).
   - Zoek- en productinteractiegebeurtenissen vastleggen.
   - Druk gebeurtenissen handmatig op de GTM-gegevenslaag.

1. **voltooi de volgende stappen**:

   - Huidige GTM-traceervereisten controleren.
   - Wijs GTM-gebeurtenissen toe aan Storefront-gebeurtenissen.
   - Implementeer aangepaste gebeurtenislisteners.
   - Testgegevensstroom naar GTM.
   - Analyserapporten valideren.

**Optie 3: Vervang GTM met Adobe Analytics**

- Overweeg migrerend aan [&#x200B; Adobe Analytics &#x200B;](https://business.adobe.com/nl/products/adobe-analytics.html) als toepasselijk.
- Neem contact op met Customer Engineering voor hulp.

**die om** te contacteren: leg een steunkaartje voor GTM verenigbaarheidsupdates of de hulp van de Techniek van de Klant voor.

### Scenario: implementatie zonder kop of PWA

In dit scenario hebt u een headless- of PWA-winkel die aangepaste gebeurtenisverzameling vereist en die de standaard-interface van de PLP-widget niet kan gebruiken.

**Rol**: Ontwikkelaar/Partner

1. **de verwijzingsimplementaties van het Overzicht**:
   - Onderzoek de [&#x200B; PLOP broncode van widget &#x200B;](https://github.com/adobe/storefront-product-listing-page).
   - Herzie API documentatie voor [[!DNL Live Search]  GraphQL &#x200B;](graphql.md).
   - Begrijp de [&#x200B; vragen van de Dienst van de Catalogus &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/).

1. **voer een douane UI** uit:
   - Gebruik [!DNL Live Search] GraphQL API voor query&#39;s.
   - Aangepaste onderdelen voor productlijsten samenstellen.
   - Voer UI voor faceting uit.
   - Paginering en sorteren verwerken.

1. **voer gebeurtenisinzameling** uit:
   - De documentatie van de Gebeurtenissen van het overzicht [&#x200B; Storefront &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#live-search).
   - Voer de vereiste gebeurtenissen uit:
      - `search-request-sent`
      - `search-response-received`
      - `search-results-view`
      - `product-page-view`
      - `add-to-cart`
   - Test gebeurtenisgegevensstromen naar Adobe Commerce.

1. **vorm facetsortering**:
   - Voor implementaties zonder kop kunnen facetten worden gesorteerd op aantal.
   - Configureer in **[!UICONTROL Live Search]** > **[!UICONTROL Facets]** -werkruimte.
   - Plaats **[!UICONTROL Sort Type]** aan **Telling** voor betere UX.

1. **test en bevestigt**:
   - Controleer de nauwkeurigheid van de zoekresultaten.
   - Functionaliteit van testfacet.
   - Bevestig dat gebeurtenissen correct worden bijgehouden.
   - Prestatiewaarden controleren.
   - Werk met intelligente merchandising-functies.

### Scenario: aangepaste wijzigingen in widgetcode

In dit scenario hebt u eerder de zoekadapter of widgetcode aangepast en moet u aanpassingen migreren.

**Rol**: Ontwikkelaar/Partner

1. **het document bestaande aanpassingen**:
   - Alle aanpassingen weergeven die zijn aangebracht aan de zoekadapter.
   - Identificeer de bedrijfsvereisten die elke aanpassing drijven.
   - Bepaal of er nog aanpassingen nodig zijn.

1. **Controle als de ingebouwde eigenschappen aan uw behoeften** voldoen:
   - De eigenschappen van de overzicht [&#x200B; PLP widget &#x200B;](plp-styling.md#widget-features).
   - Controleer of aanpassing op basis van CSS volstaat.
   - Standaardgedrag voor PLP-widget testen.

1. **als de douanecode nog nodig is**:
   - Kloon de [&#x200B; PLOTSELPAGINA widget bewaarplaats &#x200B;](https://github.com/adobe/storefront-product-listing-page).
   - Implementeer uw aanpassingen.
   - Host op uw eigen CDN.
   - Werk de Commerce-configuratie bij om uw aangepaste widget te gebruiken.

   >[!WARNING]
   >
   >Als u de PLP-widget aanpast met behulp van code uit de repository, bent u verantwoordelijk voor onderhoud en updates. Nieuwe functies van de PLP-widget uit Adobe zijn mogelijk niet compatibel met uw aanpassingen.

1. **Test grondig**:
   - Alle aangepaste functionaliteit testen.
   - Controleer of Commerce-updates de aanpassingen niet onderbreken.
   - Documenteer uw aangepaste implementatie.
   - Plan voor doorlopend onderhoud.

## Bekende beperkingen en randgevallen

Houd rekening met de volgende beperkingen bij het migreren:

**de widgetbeperkingen van de PLAATS**:

- **de orderichting van de Sortering**: Wanneer PPLP widget wordt toegelaten, kan de richting van de soortorde op de pagina&#39;s van de productlijst niet worden veranderd (oplopend/aflopend).
- **toe:voegen aan wagentje**: Voeg aan wortelknopen toe is slechts beschikbaar voor eenvoudige producten in widget.
- **Rij tarifering**: Niet gesteund in PLP widget.
- **de vertoning van BTW**: De prijzen omvatten BTW, maar de BTW kan niet als afzonderlijke waarde worden getoond.

**de verschillen van de Eigenschap van onderzoeksadapter**:

- **de stalen van de Kleur**: Het `color` attribuut moet precies zoals `color` (niet &quot;kleur&quot;of douanenamen) voor monsters worden gespeld om behoorlijk te werken.
- **de stileren van het Thema**: De de themaklassen van de Douane worden niet geërft door widget; moet widget-specifieke CSS klassen richten.
- **de productsoorten van de Douane**: Niet gesteund in widget.

**overwegingen van Prestaties**:

- Bij grote catalogi (50.000+ producten) kan het langer duren om de eerste pagina te laden.
- Meerdere facetten met veel waarden kunnen de prestaties beïnvloeden.
- De prestaties van mobiele apparaten kunnen variëren afhankelijk van de catalogusgrootte.

**de kwesties van de Verenigbaarheid**:

- De verenigbaarheidskwestie van de Manager van de Markering van Google (zie [&#x200B; scenario GTM &#x200B;](#google-tag-manager-gtm-integration)).
- Sommige extensies van derden kunnen een conflict veroorzaken met de PLP-widget.
- Aangepaste uitcheckextensies moeten mogelijk worden bijgewerkt.

## Hulp krijgen

Neem contact op met de juiste bron op basis van uw specifieke behoeften.

**de Steun van Adobe** kan met helpen:

- Standaardprocedures voor migratie van Live Search
- Configuratieproblemen met de PLP-widget
- Problemen met facet- of kenmerkindexering
- Prestatieproblemen met standaardimplementaties
- Upgradefouten

**de partners/de systeemintegrators van de Ontwikkeling van de Ontwikkeling** zouden voor moeten worden gecontacteerd:

- Aangepaste themawijzigingen
- Aangepaste widgetcode-implementaties
- Compatibiliteit met extensies van derden
- Implementaties voor headless of PWA
- Aangepaste gebeurtenistracering

Om de Steun van Adobe te contacteren, zie de [&#x200B; Gids van de Gebruiker van het Centrum van de Hulp &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).

## Veelgestelde vragen

Zoek antwoorden op veelgestelde vragen over het migreren van de zoekadapter naar de PLP-widget.

**Q: Zal de onderzoeksadapter insectenmoeilijke situaties of eigenschapupdates ontvangen?**

A: Nee. De zoekadapter is afgekeurd en ontvangt alleen beveiligingsupdates. Opgeloste problemen, prestatieverbeteringen en nieuwe functies zijn alleen beschikbaar in de PLP-widget. Als u problemen ondervindt met de zoekadapter, is migratie naar de PLP-widget de aanbevolen oplossing.

**Q: Zal de migratie mijn storefront verstoren?**

A: Als u de juiste testprocedures in het opvoeren volgt, moet de migratie naadloos zijn. Beschikt over een terugdraaiplan klaar voor productieplaatsing.

**Q: Hoe lang neemt de migratie?**

A: voor standaardimplementaties: 1-2 uur. Voor aangepaste implementaties: 1-4 weken afhankelijk van de complexiteit.

**Q: Zal mijn onderzoek het verhandelen regels nog werken?**

A: Ja, alle regels, synoniemen en facetten van zoekopdrachten die in de werkruimte van [!DNL Live Search] zijn geconfigureerd, blijven werken met de PLP-widget.

**Q: Moet ik mijn facetten aanpassen?**

A: Over het algemeen niet, maar als u beperkt was door aangepaste bronmodelkenmerken met de zoekadapter, kunt u deze nu gebruiken met de PLP-widget.

**Q: Wat over mijn douane CSS?**

A: U moet CSS bijwerken om de klassen van de PLAP widget te richten. Zie [&#x200B; CSS klassenverwijzing &#x200B;](plp-styling.md#css-classes).

**Q: Zal dit mijn onderzoeksprestaties beïnvloeden?**

A: De PLP-widget is ontworpen om prestaties te leveren. De meeste kooplieden zien gelijke of betere prestaties. Grote catalogi moeten worden getest in ophaling.
