---
title: Inventory management Source Transfer
description: Vorm voorraden voor  [!DNL Store Fulfillment solution]  met Adobe Commerce Inventory management. Stel een nieuwe voorraad- en overdrachtvoorraad in op basis van de standaardvoorraad, zodat u deze kunt toewijzen aan bronnen die zijn geconfigureerd om de opslagcapaciteit die door de oplossing Afhandeling van winkel wordt vereist, in te schakelen.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Inventory management Source Transfer

De [!DNL Store Fulfillment] -oplossing gebruikt native Adobe Commerce Inventory management. Standaard wijst de configuratie van [!DNL Commerce] alle webinhoud toe aan de standaardvoorraad, waaraan geen aanvullende bronnen kunnen worden toegewezen. Omdat aan een website slechts één voorraad kan worden toegewezen, moet een handelaar een nieuwe voorraad vormen en naar keuze hun standaardbroninventaris overbrengen naar een bron die aan het aangewezen werkingsgebied wordt toegewezen. Vervolgens kan de bron worden toegewezen aan het nieuwe bestand.

>[!IMPORTANT]
>
>Handelaars moeten de standaardbron voor alle producten handhaven inbegrepen in groep en bundelproducttypes. Deze producten hebben een voorraadhoeveelheid nodig die voldoet aan de minimumdrempel voor hoeveelheid in voorraadartikelen en die een voorraadstatus van [!UICONTROL In Stock] bevat.

Deze configuratieveranderingen helpen u drie dingen verwezenlijken:

1. [ voorraad van de Overdracht aan bron ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/inventory-transfer) om inventaris van het standaardvoorraad/de bron aan het nieuwe voorraad/de bron te bewegen.

1. [ Bulk wijst bronnen ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/bulk-assignment) toe om de nieuwe bronnen voor al uw producten toe te voegen.

1. [ Volledige bulkupdates voor productattributen ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update) om de `Allow Store Pickup` en `Allow Home Delivery` attributen aan bestaande producten toe te voegen. Wanneer de oplossing wordt geïnstalleerd, hebben de attributen de optimale *standaard* waarden. Nochtans, worden deze attributen niet toegepast op bestaande producten tot u het bulk updaContes proces voltooit.

De voorraad wordt afgetrokken van de geselecteerde bron (detailhandel of e-commerce-entrepot). De bronnen die als e-commerce pakhuizen worden gebruikt moeten aan het zelfde dossier worden toegewezen zoals de opslagbestelplaats en voorrang gegeven vóór de detailhandelsplaatsen. Voor extra informatie, zie [ het Prioriseren van Bronnen voor een Beeld ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-prioritize-sources).

Raadpleeg de gebruikersdocumentatie van Adobe Commerce voor meer informatie over het beheer van voorraden, voorraden en bronnen:

- [ het Leiden Inventaris ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction)

- [ het Leiden de Hoeveelheden van de Inventaris ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/quantities/quantities-manage)

- [ Beherend Voorraad ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage)

- [ het Leiden Bronnen ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage)

- [ Prioritaire Bronnen voor een Voorraad ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-prioritize-sources)

- [ Bulk Updates voor de Attributen van het Product ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update)


>[!IMPORTANT]
>
>Het wijzigen van de configuratie voor inventarisatie en voorraadbronnen kan ook downstreamgevolgen hebben voor geïntegreerde systemen. Zorg ervoor dat u begrijpt hoe de wijzigingen in de configuratie van de inventaris deze systemen beïnvloeden.
