---
title: '[!DNL Adobe Commerce as a Cloud Service] releaseopmerkingen'
description: Leer over de recentste eigenschappen en de verbeteringen in  [!DNL Adobe Commerce as a Cloud Service].
feature: App Builder, GraphQL, Integration, Saas
role: Admin, Developer, User, Leader
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: cf06dec6-8d6b-413e-9977-df88373c188e
source-git-commit: 925df19c2827f474efe85708ea49974b285df29e
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Opmerkingen bij de release

De volgende releaseopmerkingen bevatten updates voor [!DNL Adobe Commerce as a Cloud Service] . Voor versieinformatie voor andere producten, verwijs naar [&#x200B; Adobe Commerce Optimizer &#x200B;](../optimizer/release-notes.md) of [&#x200B; Adobe Commerce op-gebouw en Adobe Commerce op Wolk &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview).

[!DNL Adobe Commerce as a Cloud Service] bevat de meest recente versies van de handelsdiensten, de betalingsdiensten, en de uitbreidingsversies. Gebruik de volgende koppelingen om de releaseopmerkingen voor elke versie weer te geven:

* Services
   * [Catalogusservice](../catalog-service/release-notes.md)
   * [Live zoeken](../live-search/release-notes.md)
   * [Betalingsdiensten](../payment-services/release-notes.md)
   * [Aanbevelingen voor producten](../product-recommendations/release-notes.md)
   * [SaaS-gegevens exporteren](../data-export/release-notes.md)
* Uitbreidbaarheid
   * [&#x200B; Admin UI SDK &#x200B;](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/release-notes/)
   * [&#x200B; API Net &#x200B;](https://developer.adobe.com/graphql-mesh-gateway/mesh/release)
   * [&#x200B; Gebeurtenissen &#x200B;](https://developer.adobe.com/commerce/extensibility/events/release-notes/)
   * [&#x200B; Webhooks &#x200B;](https://developer.adobe.com/commerce/extensibility/webhooks/release-notes/)

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
