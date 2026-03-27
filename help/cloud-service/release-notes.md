---
title: '[!DNL Adobe Commerce as a Cloud Service] releaseopmerkingen'
description: Leer over de recentste eigenschappen en de verbeteringen in  [!DNL Adobe Commerce as a Cloud Service].
feature-set: Commerce
feature: App Builder, GraphQL, Integration, Saas
role: Admin, Developer, User, Leader
level: Beginner
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: cf06dec6-8d6b-413e-9977-df88373c188e
source-git-commit: 0e01ad2f115a3bb1b2ae5e9d7d4d1d0a7d24c222
workflow-type: tm+mt
source-wordcount: '2249'
ht-degree: 0%

---

# Aanvullende informatie

De volgende releaseopmerkingen bevatten updates voor [!DNL Adobe Commerce as a Cloud Service] .

>[!NOTE]
>
>Als u Adobe Commerce op-gebouw of Adobe Commerce op wolkeninfrastructuur gebruikt, zie de [ versienota&#39;s van Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview).

## April 2026 {#latest}

[!BADGE  Sandbox ]{type=Caution tooltip="De vermelde items zijn momenteel alleen beschikbaar in Sandbox-omgevingen. Adobe stelt nieuwe releases eerst beschikbaar in Sandbox-omgevingen om tijd te bieden voor het testen van aanstaande wijzigingen voordat de release beschikbaar is in Productomgevingen."}

De volgende items worden in april 2026 vrijgegeven voor productieomgevingen.

>[!BEGINSHADEBOX]

### Abonnementsstatus voor prijzen en voorraadberichten controleren via GraphQL

Met de nieuwe GraphQL-query&#39;s `isSubscribedProductAlertStock` en `isSubscribedProductAlertPrice` kunt u de winkeliers laten bepalen of een winkel al is geabonneerd op voorraad- of prijswaarschuwingen voor een product. <!-- ACCS-334 -->

### Query reCAPTCHA-configuratie voor meerdere formulieren in één GraphQL-aanvraag

De query van `recaptchaFormConfigs` kan configuratie voor meerdere formuliertypen in één aanvraag retourneren in plaats van dat er één query per formulier nodig is. <!-- ACCS-628 -->

### Verbeteringen en foutoplossingen

De volgende geselecteerde verbeteringen, optimalisaties en foutoplossingen zijn opgenomen in deze release:

* U kunt de resultaten van de Opdracht en van het Bedrijf REST API nu filtreren gebruikend toepasselijke douanekenmerken, ondersteunend scenario zoals bedrijf-scoped orde onderzoeken. <!-- ACCS-633 -->

* Oplossing voor een fout die in de browserontwikkelaarsconsole kan worden weergegeven. <!-- CCSAAS-4650 -->

{{accs-release}}

>[!ENDSHADEBOX]

## Maart 2026 - release #2

[!BADGE  Productie ]{type=Neutral tooltip="De vermelde items zijn momenteel beschikbaar in productieomgevingen."}

<!-- [!BADGE Sandbox]{type=Caution tooltip="The items listed are currently only available in Sandbox environments. Adobe makes new releases available in Sandbox environments first to provide time to test upcoming changes before the release is available on Production environments."} -->

De volgende items zijn op 24 maart 2026 vrijgegeven voor productieomgevingen.

>[!BEGINSHADEBOX]

### Meld u aan als klant met behulp van eenmalige codes

Admins kunnen [ eenmalig codes ](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customer-accounts/manage/login-as-customer) voor klantenimitatie door [!DNL Commerce Admin] en REST API nu produceren. De eenmalige code kan worden uitgewisseld voor een klanttoegangstoken via de `generateCustomerToken` - of `exchangeOtpForCustomerToken` GraphQL-mutaties, zodat &quot;Login as Customer&quot;-stromen zonder wachtwoord kunnen worden gebruikt voor winkelscenario&#39;s voor verkopers. <!-- ACCS-404 -->

Voor begeleiding bij het uitvoeren van deze eigenschap die APIs gebruikt, zie [ REST API ](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/login-as-customer/) en [ GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/generate-token/) documentatie.

### Kaartaccounts beheren via de REST API

[ de kaartrekeningen van het Cadeautje ](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/gift-card-accounts/) kunnen nu worden gecreeerd, worden bijgewerkt, worden geschrapt, en door REST API worden gevraagd. Daarnaast is JSON-ondersteuning voor bulkimport beschikbaar via het `/V1/import/json` -eindpunt, zodat integratie van andere bedrijven schenkingskaarten programmatisch kan synchroniseren. <!-- ACCS-476 -->

### Transactiee-mails activeren via de REST API

Een nieuw REST API eindpunt (`POST /V1/custom-email/send`) staat u toe [ transactie e-mails ](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/custom-email/) op bestelling teweegbrengen door een e-mailmalplaatje te specificeren identiteitskaart, ontvankelijke e-mail, en malplaatjevariabelen. De API ondersteunt geneste arrays als sjabloonvariabelen voor complexe e-mailinhoud. <!-- ACCS-325, ACCS-481 -->

### Abonneren op de webhaak voor on-process verzending

De `plugin.out_of_process_shipping_methods.api.shipping_rate_repository.get_rates` -webhaak is nu beschikbaar in de lijst Admin Webhooks in [!DNL Adobe Commerce as a Cloud Service] . Gebruik het om [ douane het verschepen methodes ](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/shipping-use-cases/#shipping-methods) uit te voeren. <!-- ACCS-478 -->

### PDF&#39;s en andere bestanden uploaden via productkenmerken

Een nieuw &quot;dossier&quot;[ Type van Input van Attributen ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types) staat u toe om attributenreeksen tot stand te brengen waar u dossiers, zoals PDFs, aan individuele producten kunt uploaden. U kunt toegestane dossieruitbreidingen en maximum dossiergrootte vormen door aan [!UICONTROL **te navigeren Slaat**] > [!UICONTROL **Configuratie**] > [!UICONTROL _Catalogus_] > [!UICONTROL **de Attributen van het Dossier van het Product**]. <!-- ACCS-535, ACCS-565 -->

### Aangepaste bedrijfskenmerken configureren

Beheerders kunnen aangepaste bedrijfskenmerken nu beheren op de pagina Bedrijf bewerken in de [!DNL Commerce Admin] . Aangepaste kenmerken kunnen worden geconfigureerd, opgeslagen en gevalideerd via de beheerinterface voor [!DNL Adobe Commerce as a Cloud Service] .

Om de attributen van de bedrijfdouane te vormen, navigeer aan [!UICONTROL **Klanten**] > [!UICONTROL **Bedrijven**] en selecteer een bedrijf om de uitgeven pagina te openen. Dan selecteer het [!UICONTROL **lusje van de Attributen van de Douane**] om nieuwe attributen toe te voegen.
<!-- ACCS-294 -->

### Abonneer je op prijs- en voorraadberichten via GraphQL

EDS storefronts werken nu met [ prijs en voorraadalarm ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup). <!-- ACCS-334 -->

Daarnaast zijn er verschillende nieuwe mutaties in GraphQL die moeten worden geabonneerd op prijs- en voorraadwaarschuwingen en die moeten worden afgebroken:

+++Nieuwe GraphQL-mutaties

```graphql
mutation {
  subscribeProductAlertStock(input: { sku: "ADB111" }) {
    success
    message
  }
}
```

```graphql
mutation {
  unsubscribeProductAlertStock(input: { sku: "ADB111" }) {
    success
    message
  }
}
```

```graphql
mutation {
  unsubscribeProductAlertStockAll {
    success
    message
  }
}
```

```graphql
mutation {
  subscribeProductAlertPrice(input: { sku: "ADB112" }) {
    success
    message
  }
}
```

```graphql
mutation {
  unsubscribeProductAlertPrice(input: { sku: "ADB115" }) {
    success
    message
  }
}
```

```graphql
mutation {
  unsubscribeProductAlertPriceAll {
    success
    message
  }
}
```

+++

### Verbeteringen en foutoplossingen

De volgende geselecteerde verbeteringen, optimalisaties en foutoplossingen zijn opgenomen in deze release:

* De bedrijfsrol [!UICONTROL Sales] > [!UICONTROL View Orders] functioneert nu naar behoren. <!-- ACCS-604 -->

* Het kenmerk Customer extension van `last_login_at` is nu beschikbaar via de REST API, waardoor integraties de meest recente aanmeldingsdatum voor elke klant kunnen ophalen. <!-- ACCS-555 -->

* Correctie van een probleem met de suggesties voor het [!DNL AEM Assets] -integratieformulier. <!-- ACCS-209 -->

* Probleem verholpen waarbij acties voor het toewijzen en opheffen van grote hoeveelheden aan bedrijven in het raster Gedeelde catalogus tot een fout konden leiden. <!-- CCSAAS-4614 -->

* Probleem verholpen waarbij de aangepaste prijs voor winkelwagentjes werd overschreven toen hetzelfde product opnieuw met een andere hoeveelheid of aangepaste prijs aan het winkelwagentje werd toegevoegd. <!-- ACCS-529 -->

* UID&#39;s van lijstitems voor aanvraag zijn nu consistent met UID&#39;s van winkelwagentje- en wenslijstonderdelen. <!-- ACCS-349 -->

* Probleem verholpen waarbij een time-out voor de pagina met productbewerkingen werd opgelost die kon optreden bij grote gedeelde catalogi. <!-- CCSAAS-4657 -->

* Schakel de GET `/V1/directory/countries` - en GET `/V1/directory/countries/:countryId` REST API-eindpunten voor beheersysteemintegratie opnieuw in, zodat clients geldige land- en regiogegevens kunnen opzoeken. <!-- ACCS-518 -->

* Oplossing voor een time-outprobleem dat in de REST API kan optreden wanneer een gebruiker een grote gedeelde catalogus heeft. <!-- ACCS-4657 -->

* Probleem verholpen waarbij geblokkeerde B2B-bedrijven nog steeds producten aan de winkelwagen konden toevoegen. <!-- ACCS-552 -->

* Als u een grote hoeveelheid gegevens op de rasters van de Klant of van het Bedrijf hebt, zijn de de uitvoerknopen niet meer beschikbaar om fouten te verhinderen. <!-- ACCS-320 -->

* Probleem verholpen waarbij bestandsgrootten in bijlage niet correct werden weergegeven. <!-- ACCS-566 -->

* Probleem verholpen met het maken en verwijderen van &quot;File&quot;-kenmerktypen in de [!DNL Commerce Admin] . <!-- ACCS-605, ACCS-606 -->

{{accs-release}}

>[!ENDSHADEBOX]


## Maart 2026 - release #1

[!BADGE  Productie ]{type=Neutral tooltip="De vermelde items zijn momenteel beschikbaar in productieomgevingen."}

De volgende items zijn op 9 maart 2026 uitgebracht naar de productieomgeving van [!DNL Adobe Commerce as a Cloud Service] .

>[!BEGINSHADEBOX]

### App Builder AI-codeergereedschappen en zelfstudies

U kunt [ het coderen van AI ontwikkelaar nu gebruiken tooling ](./migration/coding-tools.md) om nieuwe [!DNL App Builder] toepassingen tot stand te brengen en bestaande [!DNL Adobe Commerce] PHP uitbreidingen in [!DNL App Builder] toepassingen om te zetten. De volgende zelfstudies zijn beschikbaar om te tonen hoe u de gereedschappen kunt gebruiken:

* [Voorwaarden voor zelfstudie](./tutorials/tutorial-prerequisites.md)
* [Zelfstudie over het verlengen van beoordelingen](./tutorials/ratings-extension.md)
* [Zelfstudie over het verlengen van verzendmethoden](./tutorials/shipping-method-extension.md)

### Toegang tot App Builder-app-beheer via Beheer

[!DNL Commerce Admin] omvat nu een menupunt dat met [ App Management ](https://developer.adobe.com/commerce/extensibility/app-management/){target="_blank"} verbindt, verenigde shell voor het beheren van [!DNL App Builder] apps verbonden aan de instantie van Commerce. Deze toevoeging wordt mogelijk gemaakt door de nieuwste SDK-update voor Admin UI. <!-- CEXT-5755 -->

### Wijziging van limiet voor het aanmaken van een entiteit aanvragen

De limiet voor het aantal websites, winkels en winkelweergaven was voorheen beperkt tot 50. U kunt a [ steunverzoek ](https://experienceleague.adobe.com/home?support-tab=home#support) nu voorleggen om deze grenzen, indien nodig te wijzigen. <!-- ACCS-398 -->

### Verstorefront authentificatieberichten met gestructureerde foutencodes aanpassen

De [`generateCustomerToken` mutatie van GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/generate-token/){target="_blank"} keert nu getypte foutencodes naast foutenmeldingen terug, toelatend storefronts om specifieke berichten UI per mislukkingsreden te tonen. Beschikbare foutcodes zijn: `CUSTOMER_MISSING_EMAIL` , `CUSTOMER_MISSING_PASSWORD` , `CUSTOMER_SIGN_IN_INCORRECT_OR_LOCKED` , `CUSTOMER_ACCOUNT_NOT_CONFIRMED` en `CUSTOMER_GENERIC_ERROR` . <!-- ACCS-301 -->

### Automatische e-mailherinneringen verzenden voor inactiviteit van winkelwagentje en wenslijst

De [ module van de Herinnering E-mail ](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/communications/email-reminders/email-reminder-rules) (`Magento_Reminder`) is nu actief in [!DNL Adobe Commerce as a Cloud Service], toestaand verkopers om geautomatiseerde herinneringsregels tot stand te brengen die e-mails aan klanten teweegbrengen die op kar en vorklijst inactiviteit worden gebaseerd. <!-- CCSAAS-4597 -->

### Abonneren op gebeurtenissen voor het verwijderen van categorieën webhaak

De `observer.catalog_category_delete_before` webhaak is nu beschikbaar in [!DNL Adobe Commerce as a Cloud Service] . Gebruik deze optie om logica uit te voeren voordat een categorie wordt verwijderd. <!-- CEXT-5862 -->

### Gastersorders volgen die met een geregistreerd e-mailbericht zijn geplaatst

Een nieuwe facultatieve opslag-vlakke configuratie staat klanten toe om [ gastorden te volgen ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-guest#allow-guest-order-access-for-registered-emails) zij maakten, als de orde gebruikend een e-mailadres werd geplaatst dat een geregistreerde klantenrekening aanpast. <!-- ACCS-289 -->

### Verbeteringen en foutoplossingen

De volgende geselecteerde verbeteringen, optimalisaties en foutoplossingen zijn opgenomen in deze release:

* Probleem verholpen waarbij sommige organisatiebeheerders ten onrechte toegang hadden tot huurdersinstanties zonder machtiging per huurder. <!-- ACCS-335 -->

* Probleem verholpen waarbij een gebruiker zich kon afmelden bij [!DNL Commerce Admin] wanneer een gebruiker wijzigingen aanbracht in een gedeelde catalogus. <!-- ACCS-318 -->

* Probleem verholpen waarbij sommige webhookvelden onjuist werden weergegeven in de gebruikersinterface van [!DNL Commerce Admin] . <!-- CEXT-5874 -->

{{accs-release}}

>[!ENDSHADEBOX]

## Februari 2026 - release #2

[!BADGE  Productie ]{type=Neutral tooltip="De vermelde items zijn momenteel beschikbaar in productieomgevingen."}

De volgende items zijn op 24 februari 2026 uitgebracht naar de productieomgeving van [!DNL Adobe Commerce as a Cloud Service] .

>[!BEGINSHADEBOX]

### Contextvelden met commerciële gebeurtenissen verzenden

[!DNL Adobe Commerce as a Cloud Service] steunt nu [ contextgebieden ](https://developer.adobe.com/commerce/extensibility/events/context-fields/) in gebeurtenislading, toestaand u om gegevens te omvatten die geen deel van de gebeurtenis door gebrek zijn. <!-- CEXT-5713 -->

### Abonneren om gebeurtenissen voor het opslaan van aanhalingstekens te gebruiken met een nieuwe webhaak

De `observer.sales_quote_item_save_before` webhaak is nu beschikbaar in [!DNL Adobe Commerce as a Cloud Service] . Gebruik deze optie om logica uit te voeren voordat een aanhalingsteken wordt opgeslagen. <!-- ACCS-346 -->

### Verbeteringen en foutoplossingen

De volgende geselecteerde verbeteringen, optimalisaties en foutoplossingen zijn opgenomen in deze release:

* Correctie van een fout die weergaveproblemen in de productlijst van [!DNL Commerce Admin] kon veroorzaken. De productlijst beperkt nu het aantal gedeelde catalogi dat wordt weergegeven om de prestaties te verbeteren. <!-- CCSAAS-1242 -->

* Probleem verholpen met een GraphQL-fout die het toevoegen van aanpasbare cadeaukaarten aan het winkelwagentje kan voorkomen. <!-- ACCS-313 -->

{{accs-release}}

>[!ENDSHADEBOX]

## Februari 2026 - release #1

[!BADGE  Productie ]{type=Neutral tooltip="De vermelde items zijn momenteel beschikbaar in productieomgevingen."}

De volgende items zijn op 10 februari 2026 uitgebracht naar de productieomgeving van [!DNL Adobe Commerce as a Cloud Service] .

>[!BEGINSHADEBOX]

### Verzendmethoden aanpassen en beheerrapporten weergeven

De volgende verbeteringen zijn doorgevoerd in [!DNL Commerce Admin] :

* Verbeterde uit-van-proces [ verscheepende webhaakpayloads ](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/shipping-use-cases/#payload) om het verschepen attributen van de adresdouane te omvatten. Dankzij deze wijziging kunnen verkopers aangepaste verzendmethoden implementeren. <!-- ACCS-235 -->

* Toegevoegde toegang tot Admin- rapporten, met inbegrip van rapporten voor [ Klanten ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/customer-reports), [ Marketing ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/marketing-reports), [ Producten ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/product-reports), en [ Verkoop ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/sales-reports). <!-- CCSAAS-3085 -->

>[!NOTE]
>
>De rapporten niet beschikbaar in [!DNL Adobe Commerce as a Cloud Service] worden geëtiketteerd als slechts PaaS ([!BADGE  PaaS slechts ]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."}).

### Aangepaste factuurbedragen vastleggen via de REST API

Factuur API steunt nu [ douanevangst hoeveelheden ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#custom-capture-amounts) gebruikend uitbreidingsattributen. <!-- ACCS-186, ACCS-197, ACCS-143 -->

>[!NOTE]
>
>Vanwege wettelijke beperkingen is het aangepaste opnamebedrag alleen beschikbaar in de Noord-Amerikaanse (NA) regio en in andere regio&#39;s waar betalingsovernames zijn toegestaan.

### Verbeteringen en foutoplossingen

De volgende geselecteerde verbeteringen, optimalisaties en foutoplossingen zijn opgenomen in deze release:

* Oplossing voor het filter Coupon Grid om alle aangepaste coupons weer te geven die via de API of door importeren zijn gemaakt. <!-- CCSAAS-4509 -->

* Probleem verholpen waarbij de [!DNL Storefront Compatibility B2B Package] -mutatie niet handmatig ingevoerde adressen naar het adresboek van de klant opslaat, zelfs niet wanneer `setNegotiableQuoteShippingAddress` was ingesteld op `save_in_address_book` . `true`<!-- LYNX-1031 -->

<!-- The above change will also be covered by the B2B changelog published on February 13, 2026. -->

* Probleem opgelost waarbij productafbeeldingen niet correct werden weergegeven in [!DNL Edge Delivery Services] vanwege beschadigde `no_selection` -waarden in aangepaste kenmerken met betrekking tot elementrollen. <!-- ACAP-1206 -->

* Oplossing voor een probleem waardoor gefedereerde gebruikersaccounts met een voornaam of achternaam null geen toegang krijgen tot Commerce Admin. <!-- ACCS-200 -->

* De configuratie Asset Selector is vereenvoudigd door automatisch regio-specifieke IMS Client-id&#39;s op te geven. Handelaren hoeven geen ondersteuningstickets meer in te dienen om Asset Selector te configureren voor het toewijzen van images van productcategorieën aan elementen. Het systeem gebruikt nu automatisch toegewezen IMS-client-id&#39;s die zijn gebaseerd op de Commerce-regio. <!-- ACCS-175 -->

* Verschillende verbeteringen op het gebied van prestaties en optimalisatie. <!-- CCSAAS-4485, CCSAAS-4497, ACCS-196 -->

{{accs-release}}

>[!ENDSHADEBOX]

## januari 2026

[!BADGE  Productie ]{type=Neutral tooltip="De vermelde items zijn momenteel beschikbaar in productieomgevingen."}

De volgende items zijn op 20 januari 2026 uitgebracht naar de productieomgeving van [!DNL Adobe Commerce as a Cloud Service] .

>[!BEGINSHADEBOX]

### B2B-dropins

De volgende wijzigingen zijn aangebracht in B2B-drop-in onderdelen:

* [!DNL Commerce Storefront on Edge Delivery Services] omvat nu [ B2B drop-in componenten ](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/). De volgende B2B-dropins zijn nu beschikbaar:

   * **[Beheer van het Bedrijf ](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/company-management/)** - laat het beheer van het bedrijfprofiel en op rol-gebaseerde toestemmingen voor de storefronts van Adobe Commerce toe.
   * **[de schakelaar van het Bedrijf ](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/company-switcher/)** - verstrekt een component UI voor gebruikers om tussen veelvoudige bedrijven te schakelen zij met worden geassocieerd.
   * **[de orden van de Aankoop ](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/purchase-order/)** - beheert de werkschema&#39;s van de inkooporde, goedkeuringsregels, en de geschiedenis van de inkooporde voor B2B transacties.
   * **[het beheer van het Citaat ](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/quote-management/)** - laat verhandelbare citaten voor B2B klanten met citaatverzoek, onderhandeling, en goedkeuringswerkschema&#39;s toe.
   * **[de lijsten van de Verzoek ](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/requisition-list/)** - verstrekt hulpmiddelen om en het leiden van vraaglijsten voor herhaalde aankopen en bulkopdracht tot stand te brengen.

* Release van het B2B Storefront Compatibility Package. Dit pakket verbetert het [!DNL Adobe Commerce] B2B GraphQL-schema om de ontwikkeling op B2B-systemen te helpen verbeteren.

<!-- 
* [!DNL Commerce Storefront on Edge Delivery Services] now includes [B2B drop-in components](http://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/). For a complete list of available B2B drop-in blocks, refer to the [storefront documentation](http://experienceleague.adobe.com/developer/commerce/storefront/merchants/b2b-commerce-blocks/).

* Released the [B2B Storefront Compatibility Package](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/storefront-compatibility-b2b/). This package enhances the [!DNL Adobe Commerce] B2B GraphQL schema to help improve development on B2B systems. -->

### Klikbare koppelingen naar externe transporttrackers

Transformeer verzending volgnummers inbegrepen in winkele-mails van gewone tekst in klikbare verbindingen door [ toelatend Aangepast die URLs ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/shipping-settings#shipment-tracking-urls) volgen. Deze functie wordt ondersteund voor USPS, UPS, FedEx en DHL. <!-- See PR #716 in commerce-admin -->

### Google reCAPTCHA Enterprise-ondersteuning

[!DNL Adobe Commerce as a Cloud Service] storefronts steunt nu [ reCAPTCHA Onderneming ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-google-recaptcha-enterprise). Deze functie biedt geavanceerde botbescherming door gebruik te maken van adaptieve risicoanalyse en machinaal leren om menselijke gebruikers nauwkeurig te onderscheiden van geautomatiseerde bots. Het versterkt de veiligheid van sites, voorkomt frauduleuze activiteiten en beperkt spam en misbruik om een vertrouwde winkelervaring te behouden. <!-- CCSAAS-4242 -->

### Instantiespecifieke beheerderstoegang

U kunt [ gebruikerstoegang ](./user-management.md#add-users) aan individuele [!DNL Adobe Commerce as a Cloud Service] instanties in Admin Console nu toewijzen. <!-- CCSAAS-4337 --><!-- See PR #332 -->

### Waarneming

Door [!DNL App Builder] te gebruiken, kunt u diepere zichtbaarheid in uw [!DNL Adobe Commerce as a Cloud Service] instantie met [ OpenTelemetry observability ](https://developer.adobe.com/commerce/extensibility/observability/) verkrijgen, nu automatisch beschikbaar. OpenTelemetry biedt meetgegevens, logboeken en sporen om u te helpen de prestaties te bewaken, problemen sneller op te lossen en uw winkel te optimaliseren. Dit vermogen laat pro-actieve inzichten in systeemgezondheid toe en verbetert betrouwbaarheid voor uw klanten.

>[!NOTE]
>
>Voor het observeren van OpenTelemetry is het gebruik vereist van [!DNL App Builder] of andere OOPE-aanbiedingen (Out-of-Process Rekability).

### Prijsniveau voor catalogusprijzen

U kunt tiered tarifering kortingen met de kortingen van de catalogusregel nu combineren gebruikend [ de regels van de catalogusprijs ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier#enable-tier-pricing-for-catalog-price-rules). Dankzij deze verbetering kunt u dynamischere en meer concurrerende prijsstrategieën maken, waarbij bulkaankopen worden beloond terwijl tegelijkertijd promotionele kortingen worden toegepast. Het resultaat is grotere flexibiliteit om klanten aan te trekken, orde te verhogen waarde, en aandrijvingsomzettingen.<!-- See PR #708 in commerce-admin -->

### Verbeteringen en foutoplossingen

De volgende geselecteerde verbeteringen, optimalisaties en foutoplossingen zijn opgenomen in deze release:

* Oplossing voor een fout die kan optreden wanneer een bestand naar S3 wordt geüpload. <!-- CCSAAS-4189 -->

* Oplossing voor een `User is not entitled to access this instance` -fout die kan optreden wanneer u zich aanmeldt bij de Commerce-beheerder of de REST-API opent. <!-- CCSAAS-4324 -->

* Correctie van een fout die optrad bij het voorvertonen of een wachtrij maken van een nieuwsbrief in het raster Sjabloon nieuwsbrief. <!-- CCSAAS-4398 -->

* Vaste a `404` fout die voorkwam wanneer het klikken van de [!UICONTROL **knoop van Gegevens**] op het Admin dashboard opnieuw laadt. <!-- CCSAAS-4468 -->

* Correctie van een probleem waarbij aangepaste productkenmerken niet konden worden bijgewerkt via de REST API toen [!DNL AEM Assets integration] was ingeschakeld en het product afbeeldingen bevatte. <!-- ACAP-1178 -->

* Diverse prestaties en optimalisatieverbeteringen.<!-- CCSAAS-4255 --><!-- CCSAAS-4233 --><!-- CCSAAS-4220 --><!-- CCSAAS-4252 --><!-- CCSAAS-4330 --><!-- CCSAAS-3669 --><!-- CCSAAS-4462 -->

{{accs-release}}

>[!ENDSHADEBOX]

## november 2025

>[!BEGINSHADEBOX]

### Verbeteringen

* [ Gebruikersbeheer ](./user-management.md) - veranderde **rol Admin van het Product** in Admin Console om gebruikerstoegang tot Commerce automatisch bij te werken Admin. <!-- CCSAAS-3012 -->

* Toegevoegd de capaciteit om verhandelbare citaatgehechtheid evenals dossiers en beelden te uploaden en terug te winnen verbonden aan klanten en klantenadressen aan Amazon S3 gebruikend presigned URLs in [ GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/schema/uploads) en [ REST ](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/s3-uploads). Met REST kunt u ook categorieafbeeldingen uploaden. <!-- CCSAAS-3250 -->

* Toegevoegde `POST /V1/customers` en `PUT /V1/customers/{customerId}` eindpunten aan [ REST API ](https://developer.adobe.com/commerce/webapi/rest/reference/) om klanten tot stand te brengen en bij te werken. Voor deze eindpunten is een IMS-vergunning vereist. <!-- CCSAAS-3112 -->

* De [`exchangeOtpForCustomerToken` mutatie ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/exchange-otp-customer-token/) werd toegevoegd, die het e-mailadres en het eenmalige wachtwoord van een klant (OTP) vereist, en ontvangt een klantentoken in ruil. Deze mutatie wordt typisch gebruikt in scenario&#39;s waar een klant gebruikend OTP moet voor authentiek verklaren die naar hun e-mail of telefoon wordt verzonden.

* Als een adres dat in het [!UICONTROL **configuratiescherm van de Adressen van de E-mail van de Opslag**] wordt bepaald een waarde bevat die met `example.com` beëindigt, verzendt Commerce geen e-mails naar dit adres. In plaats daarvan logt het systeem aan dat de e-mail niet is verzonden.  <!-- CCSAAS-3533 -->

#### Aangepaste orderkenmerken

* De gebruikers Admin kunnen [ attributen van de douaneorde ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#custom-order-attributes) van de Mening van de Orde nu bekijken en uitgeven, en schermen in het Admin paneel creëren. Deze verbetering verbetert het beheer van aangepaste ordergegevens die via GraphQL zijn gemaakt. <!-- CEXT-5044 -->

>[!ENDSHADEBOX]
