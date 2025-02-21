---
title: Aan boord  [!DNL Payment Services]
description: Verbind uw instantie met  [!DNL Payment Services]  functionaliteit door een paar onboarding stappen te voltooien.
role: User
level: Intermediate
feature: Payments, Checkout, Integration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Aan boord [!DNL Payment Services]

Als u [!DNL Payment Services] for [!DNL Adobe Commerce] en [!DNL Magento Open Source] wilt gaan gebruiken, moet u een aantal instapstappen uitvoeren om uw instantie te verbinden met de betalingsfunctionaliteit.

## Stroom aan boord

In dit stroomdiagram wordt het algemene proces voor instapweigering [!DNL Payment Services] weergegeven.

![ on boarding flow ](assets/onboarding-diagram.svg){width="600" zoomable="yes"}

>[!NOTE]
>
> Voor Adobe Commerce versie 2.4.7 of hoger kunt u de extensiesstap Marketplace overslaan omdat [!DNL Payment Services] offline beschikbaar is.

Nadat u het instappen voor zandbak of levende betalingen hebt voltooid, is de financiële rapportering toegankelijk van [!DNL Payment Services] in Admin.

Als zowel de sandbox als de live betalingen worden gestart en ingeschakeld, kunt u eenvoudig tussen deze modi schakelen vanuit de startmodus van [!DNL Payment Services] .

## Vereisten

Als u [!DNL Payment Services] wilt gebruiken, moet u alle afhankelijke modules hebben ingeschakeld en moet het volgende beschikbaar zijn voor uw instantie:

* Module Services Connector
* Services ID-module
* API-sleutels

De modules van de Verbinding van de Diensten en van identiteitskaart van de Diensten worden automatisch geïnstalleerd tijdens de [ installatie van  [!DNL Payment Services]](install.md).

Wanneer de installatie volledig is, kunt u een nieuwe sectie in de configuratiemontages (**[!UICONTROL Stores]** zien > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) als u **[!UICONTROL Services]**uitbreidt **[!UICONTROL Commerce Services Connector]**.

Leren om tot uw API sleutels te leiden of toegang te hebben, zie [ API geloofsbrieven ](#obtain-api-credentials).

## Stappen aan boord

1. [ installeer de  [!DNL Payment Services]  uitbreiding ](install.md#get-payment-services).
1. [ verkrijg API geloofsbrieven ](connect.md#obtain-api-credentials).
1. [ verbind uw instantie ](connect.md#configure-commerce-services) met de Diensten van Commerce. Deze verbinding moet slechts eenmaal per Commerce-exemplaar worden voltooid.
1. [ opstelling de zandbakdienst ](sandbox.md#enable-sandbox-testing) (of, alternatief, ga aan [ toelatend levende betalingen ](sandbox.md#enable-live-payments) als u functionaliteit in een ander milieu) met een betaalverwerkingsrekening van PayPal van de test hebt getest.
1. [ Reeks  [!DNL Payment Services]  als uw betalingsmethode ](production.md#set-payment-services-as-payment-method), op zandbakwijze, om testbetalingen te beginnen verwerken.
1. [ de toeslagrechten van het verzoek ](production.md#request-payments-entitlement-from-adobe) om levende onboarding toe te laten.
1. [ Volledige handelaars op het instappen ](production.md#complete-merchant-onboarding) om levende betalingen voor uw websites van Commerce toe te laten.
1. [ krijg uw  [!DNL Payment Services]  Merchant identiteitskaart ](production.md#configure-pricing-tier) en geef het aan Verkoop om de correcte tarifering te vormen.
1. [ laat  [!DNL Payment Services]  op levende wijze ](production.md#enable-live-payments) toe beginnen verwerkend levende betalingen.
1. De Betalingen van de test, in zowel [ zandbak ](sandbox.md#test-in-sandbox-environment) als [ productie ](production.md#test-in-production) milieu&#39;s.

>[!NOTE]
>
>Als u uw Commerce-services niet configureert in de beheerfunctie (stap 3), kunt u geen sandbox of live betalingen instellen.

## Problemen oplossen

* [ los  [!DNL Payment Services]  installatie ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en) problemen op
* [ niet geverifieerde Paypal- zandbakrekening ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [ Vertraagde  [!DNL Payment Services]  rapportgegevens ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [ Kredietkaart van de Test ontbreekt met PayPal wanneer het verwerken van betalingen in een milieu Sandbox ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
