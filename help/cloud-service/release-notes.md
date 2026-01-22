---
title: '[!DNL Adobe Commerce as a Cloud Service] releaseopmerkingen'
description: Leer over de recentste eigenschappen en de verbeteringen in  [!DNL Adobe Commerce as a Cloud Service].
feature: App Builder, GraphQL, Integration, Saas
role: Admin, Developer, User, Leader
level: Beginner
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: cf06dec6-8d6b-413e-9977-df88373c188e
source-git-commit: 01b7e396f760258279d1314bb7fafe90957db577
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---

# Opmerkingen bij de release

De volgende releaseopmerkingen bevatten updates voor [!DNL Adobe Commerce as a Cloud Service] .

>[!NOTE]
>
>Als u Adobe Commerce op-gebouw of Adobe Commerce op wolkeninfrastructuur gebruikt, zie de [&#x200B; versienota&#39;s van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview).

## januari 2026 {#latest}

[!BADGE &#x200B; Productie &#x200B;]{type=Neutral tooltip="De vermelde items zijn momenteel beschikbaar in productieomgevingen."}

De volgende items zijn op 20 januari 2026 uitgebracht naar de productieomgeving van [!DNL Adobe Commerce as a Cloud Service] .

>[!BEGINSHADEBOX]

### B2B-dropins

De volgende wijzigingen zijn aangebracht in B2B-drop-in onderdelen:

* [!DNL Commerce Storefront on Edge Delivery Services] omvat nu [&#x200B; B2B drop-in componenten &#x200B;](http://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/). De volgende B2B-dropins zijn nu beschikbaar:

   * **[Beheer van het Bedrijf &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/company-management/)** - laat het beheer van het bedrijfprofiel en op rol-gebaseerde toestemmingen voor de storefronts van Adobe Commerce toe.
   * **[de schakelaar van het Bedrijf &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/company-switcher/)** - verstrekt een component UI voor gebruikers om tussen veelvoudige bedrijven te schakelen zij met worden geassocieerd.
   * **[de orden van de Aankoop &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/purchase-order/)** - beheert de werkschema&#39;s van de inkooporde, goedkeuringsregels, en de geschiedenis van de inkooporde voor B2B transacties.
   * **[het beheer van het Citaat &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/quote-management/)** - laat verhandelbare citaten voor B2B klanten met citaatverzoek, onderhandeling, en goedkeuringswerkschema&#39;s toe.
   * **[de lijsten van de Verzoek &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/requisition-list/)** - verstrekt hulpmiddelen om en het leiden van vraaglijsten voor herhaalde aankopen en bulkopdracht tot stand te brengen.

* Release van het B2B Storefront Compatibility Package. Dit pakket verbetert het [!DNL Adobe Commerce] B2B GraphQL-schema om de ontwikkeling op B2B-systemen te helpen verbeteren.

<!-- 
* [!DNL Commerce Storefront on Edge Delivery Services] now includes [B2B drop-in components](http://experienceleague.adobe.com/developer/commerce/storefront/dropins-b2b/). For a complete list of available B2B drop-in blocks, refer to the [storefront documentation](http://experienceleague.adobe.com/developer/commerce/storefront/merchants/b2b-commerce-blocks/).

* Released the [B2B Storefront Compatibility Package](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/storefront-compatibility-b2b/). This package enhances the [!DNL Adobe Commerce] B2B GraphQL schema to help improve development on B2B systems. -->

### Klikbare koppelingen naar externe transporttrackers

Transformeer verzending volgnummers inbegrepen in winkele-mails van gewone tekst in klikbare verbindingen door [&#x200B; toelatend Aangepast die URLs &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/shipping-settings#shipment-tracking-urls) volgen. Deze functie wordt ondersteund voor USPS, UPS, FedEx en DHL. <!-- See PR #716 in commerce-admin -->

### Google reCAPTCHA Enterprise-ondersteuning

[!DNL Adobe Commerce as a Cloud Service] storefronts steunt nu [&#x200B; reCAPTCHA Onderneming &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/captcha/security-google-recaptcha-enterprise). Deze functie biedt geavanceerde botbescherming door gebruik te maken van adaptieve risicoanalyse en machinaal leren om menselijke gebruikers nauwkeurig te onderscheiden van geautomatiseerde bots. Het versterkt de veiligheid van sites, voorkomt frauduleuze activiteiten en beperkt spam en misbruik om een vertrouwde winkelervaring te behouden. <!-- CCSAAS-4242 -->

### Instantiespecifieke beheerderstoegang

U kunt [&#x200B; gebruikerstoegang &#x200B;](./user-management.md#add-users) aan individuele [!DNL Adobe Commerce as a Cloud Service] instanties in Admin Console nu toewijzen. <!-- CCSAAS-4337 --><!-- See PR #332 -->

### Waarneming

Door [!DNL App Builder] te gebruiken, kunt u diepere zichtbaarheid in uw [!DNL Adobe Commerce as a Cloud Service] instantie met [&#x200B; OpenTelemetry observability &#x200B;](https://developer.adobe.com/commerce/extensibility/observability/) verkrijgen, nu automatisch beschikbaar. OpenTelemetry biedt meetgegevens, logboeken en sporen om u te helpen de prestaties te bewaken, problemen sneller op te lossen en uw winkel te optimaliseren. Dit vermogen laat pro-actieve inzichten in systeemgezondheid toe en verbetert betrouwbaarheid voor uw klanten.

>[!NOTE]
>
>Voor het observeren van OpenTelemetry is het gebruik vereist van [!DNL App Builder] of andere OOPE-aanbiedingen (Out-of-Process Rekability).

### Prijsniveau voor catalogusprijzen

U kunt tiered tarifering kortingen met de kortingen van de catalogusregel nu combineren gebruikend [&#x200B; de regels van de catalogusprijs &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier#enable-tier-pricing-for-catalog-price-rules). Deze verbetering staat u toe om dynamischere en concurrerende het tarief strategieën-belonend bulkaankopen te creëren terwijl het toepassen van promotionele kortingen tezelfdertijd. Het resultaat is grotere flexibiliteit om klanten aan te trekken, orde te verhogen waarde, en aandrijvingsomzettingen.<!-- See PR #708 in commerce-admin -->

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

* [&#x200B; Gebruikersbeheer &#x200B;](./user-management.md) - veranderde **rol Admin van het Product** in Admin Console om gebruikerstoegang tot Commerce automatisch bij te werken Admin. <!-- CCSAAS-3012 -->

* Toegevoegd de capaciteit om verhandelbare citaatgehechtheid evenals dossiers en beelden te uploaden en terug te winnen verbonden aan klanten en klantenadressen aan Amazon S3 gebruikend presigned URLs in [&#x200B; GraphQL &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/uploads) en [&#x200B; REST &#x200B;](https://developer.adobe.com/commerce/webapi/rest/modules/s3-uploads). Met REST kunt u ook categorieafbeeldingen uploaden. <!-- CCSAAS-3250 -->

* Toegevoegde `POST /V1/customers` en `PUT /V1/customers/{customerId}` eindpunten aan [&#x200B; REST API &#x200B;](https://developer.adobe.com/commerce/webapi/rest/reference/) om klanten tot stand te brengen en bij te werken. Voor deze eindpunten is beheerderstoestemming vereist. <!-- CCSAAS-3112 -->

* De [`exchangeOtpForCustomerToken` mutatie &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/mutations/exchange-otp-customer-token/) werd toegevoegd, die het e-mailadres en het eenmalige wachtwoord van een klant (OTP) vereist, en ontvangt een klantentoken in ruil. Deze mutatie wordt typisch gebruikt in scenario&#39;s waar een klant gebruikend OTP moet voor authentiek verklaren die naar hun e-mail of telefoon wordt verzonden.

* Als een adres dat in het [!UICONTROL **configuratiescherm van de Adressen van de E-mail van de Opslag**] wordt bepaald een waarde bevat die met `example.com` beëindigt, verzendt Commerce geen e-mails naar dit adres. In plaats daarvan logt het systeem aan dat de e-mail niet is verzonden.  <!-- CCSAAS-3533 -->

#### Aangepaste orderkenmerken

* De gebruikers Admin kunnen [&#x200B; attributen van de douaneorde &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#custom-order-attributes) van de Mening van de Orde nu bekijken en uitgeven, en schermen in het Admin paneel creëren. Deze verbetering verbetert het beheer van aangepaste ordergegevens die via GraphQL zijn gemaakt. <!-- CEXT-5044 -->

>[!ENDSHADEBOX]
