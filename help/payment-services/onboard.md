---
title: On-boarding  [!DNL Payment Services]  flow
description: Verbind uw instantie met  [!DNL Payment Services]  functionaliteit door een paar onboarding stappen te voltooien.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
feature: Payments, Checkout, Integration, Paas, Saas
source-git-commit: 999407f00b118441abe39209a15f587ec73fa75d
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---

# On-boarding [!DNL Payment Services] flow

Als u [!DNL Payment Services] wilt gaan gebruiken, moet u een aantal instapstappen uitvoeren. Voor nauwkeurige begeleiding, te selecteren gelieve de optie van Adobe Commerce hieronder die best op de instantie en de versie van uw organisatie richt.

In dit stroomdiagram wordt het algemene proces voor instapweigering [!DNL Payment Services] in alle versies getoond:

![&#x200B; on boarding flow &#x200B;](assets/flow-payment-services.png){width="700" zoomable="yes"}

Zie hieronder voor uw specifieke Adobe Commerce-versie die aan boord moet worden genomen met [!DNL Payment Services] .

## Help mij mijn exemplaar en versie te vinden

### Adobe Commerce of Magento Open Source | v2.4.7+

Deze stroomdiagrammen geven het algemene proces weer voor instapweigering [!DNL Payment Services] met een Adobe Commerce of Magento Open Source nieuwer dan versie 2.4.7.

>[!BEGINTABS]

>[!TAB  Sandbox ]

In dit stroomdiagram wordt het proces van de onboarding-sandbox weergegeven met een Adobe Commerce of Magento Open Source die nieuwer is dan versie 2.4.7, waarbij [!DNL Payment Services] zich buiten de box bevindt met Adobe Commerce.

![&#x200B; on boarding flow &#x200B;](assets/flow-sandbox-configuration-onboarding-2.4.7.png){width="700" zoomable="yes"}

**Aan boord nemende stappen voor versies v2.4.7+ Deel 1: Sandbox**

1. [&#x200B; verbind uw instantie &#x200B;](connect.md#configure-commerce-services) met de Diensten van Commerce. Deze verbinding moet slechts eenmaal per Commerce-exemplaar worden voltooid. [!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."}
1. [&#x200B; opstelling de zandbakdienst &#x200B;](sandbox.md#enable-sandbox-testing) (of, alternatief, ga aan [&#x200B; toelatend levende betalingen &#x200B;](sandbox.md#enable-live-payments) als u functionaliteit in een ander milieu) met een betaalverwerkingsrekening van PayPal van de test hebt getest.
1. De Betalingen van de test in a [&#x200B; zandbak &#x200B;](sandbox.md#test-in-sandbox-environment) milieu.

[![&#x200B; leer meer &#x200B;](assets/learn-more-button.svg) &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/payment-services-for-Adobe-Commerce-and-Magento-Open-Source-On-demand-Services.html)

>[!TAB  Productie ]

In dit stroomdiagram worden de productiestappen weergegeven die nodig zijn om [!DNL Payment Services] in te schakelen.

![&#x200B; on boarding flow &#x200B;](assets/flow-production-payment-services.png){width="700" zoomable="yes"}

**Aan boord gaan stappen voor versies v2.4.7+ Deel 2: Productie**

1. [&#x200B; Reeks  [!DNL Payment Services]  als uw betalingsmethode &#x200B;](production.md#set-payment-services-as-payment-method), op zandbakwijze, om testbetalingen te beginnen verwerken.
1. [&#x200B; de toeslagrechten van het verzoek &#x200B;](production.md#request-payments-entitlement-from-adobe) om levende onboarding toe te laten.
1. [&#x200B; Volledige handelaars op het instappen &#x200B;](production.md#complete-merchant-onboarding) om levende betalingen voor uw websites van Commerce toe te laten.
1. [&#x200B; krijg uw  [!DNL Payment Services]  Merchant identiteitskaart &#x200B;](production.md#configure-pricing-tier) en geef het aan Verkoop om de correcte tarifering te vormen.
1. [&#x200B; laat  [!DNL Payment Services]  op levende wijze &#x200B;](production.md#enable-live-payments) toe beginnen verwerkend levende betalingen.
1. De Betalingen van de test, in zowel [&#x200B; zandbak &#x200B;](sandbox.md#test-in-sandbox-environment) als [&#x200B; productie &#x200B;](production.md#test-in-production) milieu&#39;s.

[![&#x200B; leer meer &#x200B;](assets/learn-more-button.svg)](production.md)

>[!ENDTABS]

### Adobe Commerce of Magento Open Source | v2.4.0-2.4.6 [!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."}

Deze stroomdiagrammen tonen het algemene proces voor het aan boord gaan van [!DNL Payment Services] met Adobe Commerce of Magento Open Source versies 2.4.0 tot 2.4.6. Het is nodig om [!DNL Payment Services] te downloaden en installeren om aan het instappen te beginnen.

>[!BEGINTABS]

>[!TAB  Sandbox ]

In dit stroomdiagram worden de sandboxstappen weergegeven die zijn vereist voor instapweigering [!DNL Payment Services] met Adobe Commerce of Magento Open Source versie 2.4.0 tot en met 2.4.6.

![&#x200B; on boarding flow &#x200B;](assets/flow-sandbox-installation-configuration-onboarding-2.4.0.png){width="700" zoomable="yes"}

**Aan boord plaatsende stappen voor versies v2.4.0-2.4.6 Deel 1: Sandbox**

1. [&#x200B; installeer de  [!DNL Payment Services]  uitbreiding &#x200B;](install.md#get-payment-services) indien nodig.
1. [&#x200B; verkrijg API geloofsbrieven &#x200B;](connect.md#obtain-api-credentials).
1. [&#x200B; verbind uw instantie &#x200B;](connect.md#configure-commerce-services) met de Diensten van Commerce. Deze verbinding moet slechts eenmaal per Commerce-exemplaar worden voltooid.
1. [&#x200B; opstelling de zandbakdienst &#x200B;](sandbox.md#enable-sandbox-testing) (of, alternatief, ga aan [&#x200B; toelatend levende betalingen &#x200B;](sandbox.md#enable-live-payments) als u functionaliteit in een ander milieu) met een betaalverwerkingsrekening van PayPal van de test hebt getest.
1. De Betalingen van de test in a [&#x200B; zandbak &#x200B;](sandbox.md#test-in-sandbox-environment) milieu.

[![&#x200B; leer meer &#x200B;](assets/learn-more-button.svg) &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/payment-services-for-Adobe-Commerce-and-Magento-Open-Source-On-demand-Services.html)

>[!TAB  Productie ]

Dit stroomdiagram toont het algemene proces voor het inschakelen van [!DNL Payment Services] in een productieomgeving met Adobe Commerce of Magento Open Source versies 2.4.0 tot en met 2.4.6.

![&#x200B; on boarding flow &#x200B;](assets/flow-production-payment-services.png){width="700" zoomable="yes"}

**Aan boord plaatsende stappen voor versies v2.4.0-2.4.6 Deel 2: Productie**

1. [&#x200B; Reeks  [!DNL Payment Services]  als uw betalingsmethode &#x200B;](production.md#set-payment-services-as-payment-method), op zandbakwijze, om testbetalingen te beginnen verwerken.
1. [&#x200B; de toeslagrechten van het verzoek &#x200B;](production.md#request-payments-entitlement-from-adobe) om levende onboarding toe te laten.
1. [&#x200B; Volledige handelaars op het instappen &#x200B;](production.md#complete-merchant-onboarding) om levende betalingen voor uw websites van Commerce toe te laten.
1. [&#x200B; krijg uw  [!DNL Payment Services]  Merchant identiteitskaart &#x200B;](production.md#configure-pricing-tier) en geef het aan Verkoop om de correcte tarifering te vormen.
1. [&#x200B; laat  [!DNL Payment Services]  op levende wijze &#x200B;](production.md#enable-live-payments) toe beginnen verwerkend levende betalingen.
1. De Betalingen van de test, in zowel [&#x200B; zandbak &#x200B;](sandbox.md#test-in-sandbox-environment) als [&#x200B; productie &#x200B;](production.md#test-in-production) milieu&#39;s.

[![&#x200B; leer meer &#x200B;](assets/learn-more-button.svg)](onboard.md)

>[!ENDTABS]

>[!NOTE]
>
>Als u uw Commerce Services niet configureert in Beheer (deel 1), kunt u geen sandbox of live betalingen instellen.

>[!MORELIKETHIS]
>
> * [&#x200B; los  [!DNL Payment Services]  installatie &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=nl-NL) problemen op
> * [&#x200B; niet geverifieerde Paypal- zandbakrekening &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html?lang=nl-NL)
> * [&#x200B; Vertraagde  [!DNL Payment Services]  rapportgegevens &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html?lang=nl-NL)
> * [&#x200B; Kredietkaart van de Test ontbreekt met PayPal wanneer het verwerken van betalingen in een milieu Sandbox &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=nl-NL)
> * [&#x200B; maak de  [!DNL Payment Services]  uitbreiding &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure-store/extensions#manage-extensions-1) onbruikbaar