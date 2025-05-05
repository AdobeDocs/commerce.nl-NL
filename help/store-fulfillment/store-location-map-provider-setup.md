---
title: Configuratie van opslaglocatie en toewijzingssysteem
description: Vorm een afstandsleverancier om de afbeelding van de opslagplaats in storefront UI te steunen. De oplossingen van de Afhandeling van de Opslag vereisen een afstandsleverancier om detailhandel onderzoek en andere afbeelding en het plannen mogelijkheden voor het volledige uitvoeringswerkschema toe te laten.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Integration, Tools and External Services, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 1%

---

# Opslaglocatie en Toewijzing instellen

Laat de opslagplaats en de afbeeldingsmogelijkheden voor de Afhandeling van de Opslag toe door a [ afstandsleverancier ](https://experienceleague.adobe.com/nl/docs/commerce-admin/inventory/configuration/distance-priority-algorithm) te vormen om naar kleinhandelsopslagplaatsen te zoeken.

**Vereisten**

Tijdens het configuratieproces geeft u een Google API-sleutel op voor het Google Maps-platform. Als u geen hebt, [ produceert één van het platform van Kaarten van Google ](https://experienceleague.adobe.com/nl/docs/commerce-admin/inventory/configuration/distance-priority-algorithm#configure-google-maps).

Om de afstandsleverancier te vormen:

1. Voeg in de configuratie **[!UICONTROL Stores > General]** in Beheer de integratie Google Maps toe voor het inhoudstype Kaart.

   - Ga naar **[!UICONTROL Stores > Configuration  > General > Content Management]** .

   - Voeg uw Google API-sleutel toe aan het veld **[!UICONTROL Google Maps API Key]** .

1. Selecteer in de configuratie **[!UICONTROL Stores > Inventory]** in de beheerfunctie de afstandprovider voor Afhandeling opslaan.

   - Ga naar **[!UICONTROL Stores > Configuration > Catalog > Inventory]** .

   - Vouw de sectie **[!UICONTROL Distance Provider for Distance Based SSA]** uit.

   - Plaats de **Leverancier** aan **Kaart van Google**.

1. Configureer instellingen voor de **[!UICONTROL Google Distance Provider]** .

   - Voeg uw **sleutel van Google API** toe.

   - Stel **[!UICONTROL Computation Mode]** in op `Driving` en **[!UICONTROL Value]** op `Distance`
