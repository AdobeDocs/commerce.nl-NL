---
title: Winefront instellen
description: Leer hoe te opstelling uw  [!DNL Adobe Commerce Optimizer]  storefront.
role: Developer
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is op Adobe Commerce as a Cloud Service en  [!DNL Adobe Commerce Optimizer]  slechts projecten (Adobe-Beheerde infrastructuur SaaS) van toepassing."
exl-id: 2b4c9e98-a30c-4a33-b356-556de5bd721a
source-git-commit: 0cd9749574460374a8fe875f1eff54f2a4a8d614
workflow-type: tm+mt
source-wordcount: '1397'
ht-degree: 0%

---

# Winefront instellen

Deze handleiding begeleidt u bij het instellen van een winkel voor uw [!DNL Adobe Commerce Optimizer] -instantie met Adobe Edge Delivery Services. Uw winkel bevat bouwsteencode, voorbeeldinhoud en ondersteuning voor productdetailpagina&#39;s en productdetectie (zoeken en filteren).

**Geschatte tijd om te voltooien:** 30-45 minuten

## Vereisten

* **GitHub rekening** die bewaarplaatsen kan tot stand brengen en voor lokale ontwikkeling (github.com) gevormd is
* **[!DNL Adobe Commerce Optimizer]-instantie** met voorbeeldgegevens en geconfigureerde catalogusweergaven en beleidsregels
   * Zie [&#x200B; steekproefgegevens &#x200B;](get-started.md#add-sample-data) voor opstellingsinstructies toevoegen.

### Vereiste instance-gegevens

Verzamel voordat u begint de volgende informatie van uw [!DNL Adobe Commerce Optimizer] -instantie:

* **Identiteitskaart van de Aannemer** (ook genoemd instantiidentiteitskaart)
   * Beschikbaar bij de [&#x200B; pagina van instantiedetails &#x200B;](get-started.md#manage-instances)
* **eindpunt van GraphQL** voor uw instantie
   * Beschikbaar bij de [&#x200B; pagina van instantiedetails &#x200B;](get-started.md#manage-instances)
* **identiteitskaart van de mening van de Catalogus** voor de globale catalogusmening
   * Beschikbaar bij de [&#x200B; pagina van catalogusdetails &#x200B;](./setup/catalog-view.md#manage-catalog-view)
* **Source scène** voor uw catalogusmening
   * Standaard voor voorbeeldgegevens is `en-US`

>[!NOTE]
>
>Klanten met testtoegang kunnen het GraphQL-eindpunt vinden in de welkome e-mail die is ontvangen toen uw exemplaar werd gemaakt. Proefversies worden vooraf geconfigureerd met voorbeeldgegevens, catalogusweergaven en beleidsregels.

## Stappen instellen

1. **[creeer uw storefront project](#create-your-storefront-project)** - gebruik het [&#x200B; hulpmiddel van de Maker van de Plaats &#x200B;](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator) om een nieuw storefront project met boilerplate code, steekproefinhoud, en een configuratiedossier tot stand te brengen.

1. **[pas de storefrontconfiguratie](#customize-the-storefront-configuration)** aan - werk het `config.json` dossier in uw bewaarplaats bij om met uw [!DNL Adobe Commerce Optimizer] instantie te verbinden.

1. **[verifieer uw opstelling](#verify-your-setup)** (10 min)
   * Een voorvertoning van uw winkelsite weergeven
   * Productdetailpagina&#39;s en zoekfunctionaliteit testen

## Uw winkelproject maken

Met het gereedschap Sitemaker maakt u een volledig storefront-project met de volgende componenten:

* **Plaats**: Storefront het landen pagina met boilerplate inhoud
* **Code**: Bewaarplaats met boilerplate brondossiers
* **Inhoud**: Het milieu van de Auteur van het document met de dossiers van de plaatsinhoud
* **Commerce Config**: `config.json` dossier voor instantie-specifieke configuratie

### Stap 1: Genereer uw project

1. Open het [&#x200B; hulpmiddel van de Maker van de Plaats &#x200B;](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator)

   ![[!DNL Site Creator tool]](./assets/storefront-setup-site-creator.png){width="700" zoomable="yes"}

1. Selecteer **creeer Nieuwe Plaats (Code &amp; Inhoud)**.

1. Voltooi de siteconfiguratie:

   * **GitHub Organisatie/Gebruikersnaam**: Ga uw GitHub gebruikersbenaming of organisatienaam in
   * **Naam van de Plaats**: Kies een beschrijvende naam voor uw storefront
   * **Commerce GraphQL Endpoint (facultatief)**: ga het eindpunt van GraphQL voor uw [!DNL Adobe Commerce Optimizer] instantie in

1. Klik **creeer Plaats** om de bewaarplaats GitHub met de storefront boilerplate code tot stand te brengen.

   Wanneer de gegevensopslagruimte is gemaakt, wordt de Site Creator bijgewerkt en wordt u gevraagd de app Codesync te installeren.

### Stap 2: De app Codesync installeren

1. Klik op **[!UICONTROL Install AEM Code Sync App]** om het installatieprogramma voor codesynchronisatie te openen op een nieuw tabblad.

1. Configureer de app Codesync:
   * Selecteer uw organisatie GitHub, dan klik **[!UICONTROL Configure]**.
   * Klik in de interface Codesynchronisatie op **[!UICONTROL Only select repositories]** .
   * Klik op het menu **[!UICONTROL Select repositories]** en kies vervolgens de opslagplaats voor de storefront-code die u hebt gemaakt.
   * Klik op **[!UICONTROL Save]** om uw opslagplaats te registreren.

1. Terugkeer aan het browser venster waar de Maker van de Plaats open is, en klik **creeer Plaats**.

   De maker van de site kopieert de inhoud van het storefront boilerplate naar de omgeving van de auteur van het document. Dit proces duurt 1 tot 2 minuten.

### Stap 3: Sla uw projectkoppelingen op

1. In de sectie van de Details van de Plaats, herzie de verbindingen voor uw archiefproject:

   ![[!DNL Storefront setup complete]](./assets/storefront-setup-complete.png){width="700" zoomable="yes"}

   Gebruik deze koppelingen om uw winkelcode, inhoud en configuratie te beheren.

1. Kopieer en sla deze verbindingen voor toekomstige verwijzing op: Klik ** [!UICONTROL Copy].

## Uw winkel configureren

Werk uw storefront configuratie bij om met uw [!DNL Adobe Commerce Optimizer] instantie te verbinden.

1. Open het `config.json` -bestand in de opslagplaats voor bouwsteencode.

   `https://github.com/<username or org>/<repo name>/config.json`

1. Zoek de sectie `cs` (Catalog Service) in de configuratie.

1. Vervang de waarden van de plaatsaanduiding door de waarden voor de instantie. Zie [&#x200B; Eerste vereisten &#x200B;](#prerequisites).

   ```json
   "cs": {
      "AC-View-ID": "{catalogViewId}",
      "AC-Source-Locale": "en-US",
      "AC-Price-Book-ID": "{priceBookId}"
   }
   ```

   >[!NOTE]
   >
   >Om prijzenboekidentiteitskaart te vinden, controleer de [&#x200B; details van de catalogusmening &#x200B;](./setup/catalog-view.md) in Adobe Commerce Optimizer om de toegewezen prijzenboeken te zien. Als geen prijzenboeken worden toegewezen, kunt u deze kopbal uit het configuratiedossier verwijderen. Voeg het terug wanneer een prijsboek aan de catalogusmening is toegewezen.

1. Sla het configuratiebestand op.

   De configuratieveranderingen kunnen een paar notulen nemen om zich te verspreiden. Als u gegevens niet onmiddellijk ziet, wacht 2-3 minuten vóór het oplossen van problemen.

## Uw instellingen controleren

Test uw storefront om te controleren of deze correct is verbonden met uw [!DNL Adobe Commerce Optimizer] -instantie.

### Stap 1: je winkelhomepage bekijken

1. Ga naar de URL van uw live voorvertoning:

   `https://main--{SITE}--{ORG}.aem.live`

   Vervang `{ORG}` en `{SITE}` door uw GitHub-organisatie en sitenaam.

1. **criteria van het Succes**: U zou de storefront homepage met boilerplate inhoud moeten zien.

   ![[!DNL ACO storefront site with boilerplate]](./assets/aco-storefront-site-boilerplate.png){width="700" zoomable="yes"}

### Stap 2: pagina&#39;s met productdetails testen

Bekijk de standaardpagina met productdetails om te controleren of de productgegevens correct worden geladen.

1. Ga naar een voorbeeldproductpagina:
   `https://main--{SITE}--{ORG}.aem.live/products/placeholder/{sku}`

   Gebruik om het even welke SKU van uw steekproefgegevens, bijvoorbeeld:
   `https://main--{SITE}--{ORG}.aem.live/products/placeholder/aur-flu-tir-std-2017`

   Voor de standaardwinkel kunt u de `placeholder` -waarde in de route gebruiken om het product weer te geven. Wanneer u begint met het aanpassen van uw winkel, kunt u de storefront code aanpassen om de weg aan de pagina van het productdetail te plaatsen die op productroutes wordt gebaseerd die in uw catalogus worden bepaald.

   >[!TIP]
   >
   >Bekijk beschikbare SKUs van de [&#x200B; pagina van de Synchronisatie van Gegevens &#x200B;](./setup/data-sync.md) in uw [!DNL Adobe Commerce Optimizer] instantie.

1. **criteria van het Succes**: De pagina zou moeten tonen:
   * Productnaam, beschrijving en prijs
   * Productafbeeldingen
   * Toevoegen aan tekengebied
   * Gegevens opgehaald uit uw [!DNL Adobe Commerce Optimizer] -instantie

   ![[!DNL Default product detail page showing a product from the sample data]](./assets/storefront-boilerplate-product-page.png){width="700" zoomable="yes"}

### Stap 3: Test de standaardzoekfunctionaliteit

Test de standaardproductfuncties, inclusief zoeken en filteren.

1. Klik op de startpagina van de winkel op het vergrootglaspictogram in de koptekst.

1. Typ het onderzoekskoord `tires` en druk **binnengaan**.

1. **criteria van het Succes**: U zou moeten zien:
   * Pagina met zoekresultaten met bandenproducten
   * Filteropties in de zijbalk
   * Productaanbiedingen met afbeeldingen en prijzen

   ![[!DNL View search results page]](./assets/storefront-with-aco-search-results-page.png){width="675" zoomable="yes"}

1. Klik op een bandenproduct om de detailpagina weer te geven.

   ![[!DNL View product details page]](./assets/storefront-with-aco-pdp-page.png){width="675" zoomable="yes"}

## Problemen oplossen

Als u tijdens de installatie problemen ondervindt, controleert u op fouten met de console van de webpaginacontrole. Wis ook de browsercache of gebruik een andere browser.

Gebruik de volgende richtlijnen voor het controleren van veelvoorkomende problemen:

### Algemene kwesties

| Probleem | Symptomen | Oplossing |
|-------|----------|----------|
| **de installatie van de Synchronisatie van de Code ontbreekt** | Kan de installatie van Codesynchronisatie niet voltooien | <ul><li>Verzeker u beheerdertoegang tot uw organisatie GitHub hebt.</li><li>Probeer een persoonlijke opslagplaats in plaats van een organisatie te gebruiken.</li><li>Controleer GitHub-machtigingen en probeer het opnieuw.</li></ul> |
| **Plaats laadt niet** | 404 of verbindingsfouten | <ul><li>Verifieer de URL-indeling van uw site: `https://main--{SITE}--{ORG}.aem.live`</li><li>Controleer of de toepassing Codesync correct is geïnstalleerd.</li><li>Zorg ervoor dat de opslagplaats openbaar is of correct is geconfigureerd.</li></ul> |
| **Geen getoonde productgegevens** | Op productpagina&#39;s worden tijdelijke aanduidingen of fouten weergegeven | <ul><li>De configuratiewaarden controleren in `config.json`</li><li>Controleer in de [!DNL Adobe Commerce Optimizer] -instantie de pagina Gegevenssynchronisatie om te controleren of er voorbeeldproducten zijn geladen. Als geen producten beschikbaar zijn, laad de steekproefgegevens opnieuw of voeg een product toe gebruikend [&#x200B; Ingestie API van Gegevens &#x200B;](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/using-the-api/#make-your-first-request). Wacht een paar minuten op configuratieveranderingen om zich te verspreiden.</li><li>Probeer de productdetails terug te winnen gebruikend de Merchandising de productvraag van de Dienst [&#x200B; &#x200B;](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/use-cases/#return-product-details) gebruikend de zelfde kopballen die in het `config.json` dossier worden gevormd. Als u de gegevens kunt ophalen, is dit waarschijnlijk een probleem met de configuratie van de catalogusweergave of een indexfout.</li></ul> |
| **het Onderzoek keert geen resultaten terug** | Lege pagina met zoekresultaten | <ul><li>Verifieer dat u de resultaten van het productonderzoek kunt terugwinnen gebruikend de Merchandising de vraag van de Diensten [&#x200B; productSearch &#x200B;](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/use-cases/#product-search) gebruikend de zelfde kopballen die in het `config.json` dossier worden gevormd. Als u de gegevens kunt ophalen, is dit waarschijnlijk een probleem met de configuratie van de catalogusweergave of een indexfout.</li><li>Controleer of de weergave-id van de catalogus in het `config.json` -bestand overeenkomt met de weergave-id van de catalogus in [!DNL Adobe Commerce Optimizer] .</li><li>In Adobe Commerce Optimizer, verifieer de configuratie van het beleid, de scène, en de prijsboeken die u in de configuratie van de storefrontkopbal gebruikte.</li><li>Verifieer de [&#x200B; montages van attributenmeta-gegevens &#x200B;](https://developer.adobe.com/commerce/services/reference/rest/#operation/createProductMetadata) correct voor onderzoek worden geplaatst.</li></ul> |

### Controlelijst voor validatie

Voordat u verdergaat met de volgende stappen, moet u controleren of de winkel correct werkt. Ga hiervoor als volgt te werk:

![&#x200B; Checklist &#x200B;](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) de waarden van de Configuratie passen uw instantiemontages <br> aan
![&#x200B; Checklist &#x200B;](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) de homepage van de Storefront laadt zonder fouten <br>
![&#x200B; Checklist &#x200B;](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) minstens één pagina van het productdetail toont volledige informatie <br>
![&#x200B; Checklist &#x200B;](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) de functionaliteit van het Onderzoek keert relevante resultaten <br> terug
![&#x200B; Checklist &#x200B;](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) de beelden van het Product laden correct <br>
![&#x200B; Checklist &#x200B;](/help/assets/icons/Smock_CheckmarkCircleOutline_18_N.svg) de waarden van de Configuratie passen uw instantiemontages <br> aan

### Hulp vragen

Als er problemen blijven optreden:

* Herzie de [&#x200B; documentatie van Adobe Commerce Storefront &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/)
* Controle de [&#x200B; de ontwikkelaarsgids van Adobe Commerce Optimizer &#x200B;](https://developer.adobe.com/commerce/services/optimizer/)
* Bezoek de [&#x200B; middelen van de Steun van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview)

## Volgende stappen

Nadat u uw winkel hebt ingesteld en geverifieerd, kunt u:

1. **[installeer Sidekick &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/#install-and-configure-sidekick)** - Browser uitbreiding voor het uitgeven, het previewing, en het publiceren inhoud direct van uw website.

2. **[opstelling een lokale ontwikkelomgeving &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/#set-up-local-environment)** - creeer een lokaal milieu om uw storefront code en inhoud aan te passen.

### Leren en verkennen

* **[voltooi het gebruiksgeval van begin tot eind](./use-case/admin-use-case.md)** - leer meer over storefront opstelling en catalogusbeheer gebruikend [!DNL Adobe Commerce Optimizer].

* **[verken storefront aanpassing &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/)** - leer geavanceerde opstelling en configuratieopties.

* **[drop-ins van Commerce van het Gebruik om storefront ervaring &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/) aan te passen** - voeg pre-gebouwde componenten toe om uw storefront ervaring te verbeteren.

* **Migreer aan de Dienst van de Configuratie Storefront** - nadat u uw aanvankelijke storefront hebt gecreeerd, kunt u de configuratie migreren om de Dienst van de Configuratie te gebruiken die geavanceerde gebruiksgevallen zoals repoless configuratie en bekledingen steunt. Voor details, zie de [&#x200B; documentatie van de Dienst van de Configuratie 0&rbrace; &lbrace;in Adobe Experience Manager.](https://www.aem.live/docs/config-service-setup)

>[!MORELIKETHIS]
>
> Zie de [&#x200B; documentatie van Adobe Commerce Storefront &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/) om meer over het bijwerken van plaatsinhoud te leren en met Commerce frontend componenten en backend gegevens te integreren.
