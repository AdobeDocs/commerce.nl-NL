---
title: Productvoorraadbeheer
description: Vorm het commerciële voorraadoverseinen en de eigenschappen beschikbaar aan klanten.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Productvoorraadbeheer

Als koopman, kunt u Adobe Commerce [ Inventory management ](https://experienceleague.adobe.com/nl/docs/commerce-admin/inventory/introduction) voorraad en bronopties gebruiken. U kunt ook de oplossing Afhandeling van winkel gebruiken om andere opties voor de beschikbaarheid van voorraden in te stellen die betrekking hebben op de activiteiten van uw winkel.

- Optie voor thuislevering uit Merchant-winkels

- Toestaan / Beschikbaar voor ophalen van winkel

- UPC / SKU / Andere unieke product-id&#39;s

- Drempel voor voorraadverlies

- Het verminderen van Inventaris van specifieke plaatsen op orde

Opties voor productvoorraad configureren van de beheerder: **[!UICONTROL Catalog > Products > Select Product]**

## **Opties van de Voorraad van het Product**

| **Gebied** | **Beschrijving** | **Reikwijdte** | **Vereist** |
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Beschikbaar voor de Levering van het Huis** | <p>Hiermee stelt u de beschikbaarheid van Home Delivery (Ship-from-Store) voor het product in. Als deze optie is ingeschakeld, worden alle toegewezen winkellocaties met een beschikbare voorraad voor het product in aanmerking genomen voor de optie Home Delivery. Als deze optie is uitgeschakeld, komt het product nooit in aanmerking voor thuislevering.</p>Meestal is het voldoende deze optie in te stellen op winkelniveau. Er kunnen zich echter unieke gevallen voordoen voor specifieke producten, zoals producten waarvoor een federale scheepvaartbeperking geldt, die niet in aanmerking mogen komen voor thuislevering.</p> | Website | Nee |
| **[!UICONTROL Available for Store Pickup]** | <p>Stel de beschikbaarheid van de Ophaalservice voor het product in. Als deze optie is ingeschakeld, worden toegewezen winkellocaties met een beschikbare voorraad voor het product in aanmerking genomen voor de optie Ophalen uit winkel. Als het product is uitgeschakeld, komt het nooit in aanmerking voor Ophalen uit winkel.</p><p>Deze optie kan nuttig zijn om winkelvoorraad in het systeem te volgen die u niet van uw e-commerce kanaal wilt verkopen.</p> | Website | Nee |
| **[!UICONTROL UPC / SKU / Custom Scannable Identifier]** | Dit kenmerk moet bestaan als een productkenmerk en heeft betrekking op de instelling **[!UICONTROL Barcode Source / Barcode Type]** . Dit kenmerk wordt gebruikt om een gescande streepjescode voor uw producten bij te houden. Deze waarde kan worden verzonden wanneer een bestelling voor het selecteren naar uw winkels wordt verzonden. De associaties van de opslag kunnen de waarde met de pluklijst gebruiken om producten op de plank aan te passen gebruikend een streepjescodescanner. | Winkelweergave | Nee |

{style="table-layout:auto"}

## Bronnen voor inventarisatie op productniveau

| **Gebied** | **Beschrijving** | **Reikwijdte** | **Vereist** |
|-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Out of Stock Threshold]** | <p>Stel de voorraaddrempel voor het item binnen elke bron in. Wanneer de voorraad onder de drempel daalt, wordt deze als niet-voorraad aan de bron beschouwd.</p><p>Schakel de optie **[!UICONTROL Use Default]** in als u de globale instelling voor Winkelconfiguratie wilt gebruiken.</p> | Algemeen | Nee |
| **[!UICONTROL Allow Store Pickup]** | <p>Expliciet instellen of het item beschikbaar is voor het ophalen van de winkel, ongeacht de beschikbare voorraad of configuratie van de locatie van de winkel.</p><p>Als u de instelling op productniveau wilt gebruiken, schakelt u de optie [!UICONTROL Use Default] uit en maakt u uw selectie. Anders wordt deze instelling gekozen op basis van de configuratie voor **[!UICONTROL Allow In-Store Pickup]** die op de aandelenbron is ingesteld.</p> | Algemeen | Nee |

{style="table-layout:auto"}

