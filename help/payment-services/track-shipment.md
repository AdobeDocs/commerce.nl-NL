---
title: Uw verzendingen bijhouden in  [!DNL Payment Services]
description: Pas  [!DNL Payment Services]  zendingen en het volgen informatie aan die in het PayPal Merchant Dashboard wordt getoond.
feature: Payments, Paas, Saas
exl-id: 17aede1f-56ae-441a-b723-3193e865e469
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Uw verzendingen volgen in [!DNL Payment Services]

Met [!DNL Payment Services] kunnen verkopers de trackinggegevens voor een zending bekijken op hun PayPal Merchant Dashboard.

Zie [ transporten ](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/order-management/shipments){target=_blank} onderwerp voor meer informatie over het ladingsnet voor Adobe Commerce.

## Hoe je verzending kunt volgen werkt

Deze functionaliteit is afhankelijk van het feit of de bestelling is gefactureerd, omdat PayPal een `capture_id` moet ontvangen om de trackinggegevens te verwerken. Als een handelaar de producten verzendt voordat deze wordt vastgelegd, worden de trackinggegevens niet naar PayPal verzonden.

>[!NOTE]
>
> Het wordt aanbevolen één verzending per trackingnummer te maken, waarbij de juiste items aan de verzending worden gekoppeld.

## Het trackingnummer toevoegen

De volgende instructies doorlopen u het proces voor het maken van een verzending in Adobe Commerce met [!DNL Payment Services] :

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.

1. Klik in de kolom **[!UICONTROL Action]** voor de geselecteerde volgorde op **[!UICONTROL View]** .

1. Klik op **[!UICONTROL Ship]**.

1. Blader omlaag naar het **[!UICONTROL Payment & Shipping Method]** -blok en klik op **[!UICONTROL Add Tracking Number]** in **[!UICONTROL Shipping Information]** .

1. Stel de **[!UICONTROL Carrier]** in.

1. Voer **[!UICONTROL Title]** en **[!UICONTROL Number]** in om de verzending te volgen.

1. Klik op **[!UICONTROL Submit Shipment]**.

>[!NOTE]
>
> Je kunt ook een verzendmodule gebruiken om de gegevens over het trackingnummer in te voeren. Zorg ervoor dat de verzendmodule de informatie over het trackingnummer opslaat in het veld `tracking_number` .

### Verenigbaarheid met derden

Om het even welke derdeuitbreiding is compatibel met de functionaliteit wanneer een ladingsentiteit door [ Commerce API ](https://developer.adobe.com/commerce/webapi/rest/attributes/#ShipmentRepositoryInterface){target=_blank} wordt gecreeerd.
