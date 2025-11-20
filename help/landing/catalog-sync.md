---
title: Catalogus synchroniseren
description: Leer hoe te om productgegevens van de  [!DNL Commerce]  server naar  [!DNL Commerce Services] uit te voeren.
feature: Catalog Management, Data Import/Export, Catalog Service
exl-id: 99f96b93-b036-490c-8c57-40463a0de365
source-git-commit: ae672ed3f2693e2f14e8c7f379e59ef117a34fc3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# Catalogus synchroniseren

>[!NOTE]
>
> Het dashboard voor catalogussynchronisatie is nu het gegevensbeheerdashboard. Dit vernieuwde dashboard ondersteunt nu [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md) v6.0.0+, [[!DNL Live Search]](../live-search/overview.md) v4.1.0+ en [[!DNL Catalog Service]](../catalog-service/overview.md) v1.17+. Klanten kunnen het gegevensbeheerdashboard ophalen door de nieuwste versie van een van deze services bij te werken. Lees meer over het in de [ documentatie van het Dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard.html). Dit huidige onderwerp blijft voor die gebruikers die nog moeten bevorderen en nog het dashboard van de Synchronisatie van de Catalogus hebben.

Adobe Commerce gebruikt indexen om catalogusgegevens in tabellen te compileren. Het proces wordt automatisch teweeggebracht door [ gebeurtenissen ](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) zoals een verandering in een productprijs of inventarisniveau.

De service Catalog Sync verplaatst productgegevens van een [!DNL Adobe Commerce] -instantie naar het [!DNL Commerce Services] -platform op permanente basis om de gegevens up-to-date te houden. [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) vereist bijvoorbeeld de huidige catalogusinformatie om aanbevelingen met juiste namen, prijzen en beschikbaarheid correct te retourneren. Gebruik het _dashboard van de Synchronisatie van de Catalogus 0} {om het synchronisatieproces of de bevel-lijn interface waar te nemen en te beheren om een catalogussynchronisatie teweeg te brengen en productgegevens voor consumptie door_ opnieuw te indexeren. [!DNL Commerce Services] Zie [ bevel-lijn de Verwijzing van de Interface ](../data-export/data-export-cli-commands.md) in de _3} Gids van de Uitvoer van Gegevens SaaS {._

## Het dashboard Catalog Sync openen

Om tot het dashboard van de Synchronisatie van de Catalogus toegang te hebben, selecteer **Systeem** Overdracht van Gegevens _>_ Synchronisatie van de Catalogus **.**

Met het **dashboard van de Synchronisatie van de Catalogus** kunt u:

- Bekijk de synchronisatiestatus (**Bezig**, **Succes**, **Ontbroken**)
- Het totale aantal gesynchroniseerde producten weergeven
- Gesynchroniseerde producten zoeken om hun huidige status weer te geven
- Catalogus zoeken op naam, SKU, enz.
- Gesynchroniseerde productgegevens weergeven in JSON om een synchronisatieverschil te diagnosticeren
- Het synchronisatieproces opnieuw starten

### Laatste synchronisatie

Meldt de synchronisatiestatus van:

- **Succes** - Toont de datum en de tijd dat de synchronisatie en het aantal bijgewerkte producten succesvol was
- **Ontbroken** - Toont de datum en de tijd dat de synchronisatie werd geprobeerd
- **Bezig** - Toont de datum en de tijd van laatste succesvolle synchronisatie

Het synchronisatieproces van de catalogus wordt automatisch om het uur uitgevoerd. Als u verwachte producten op de winkel niet ziet, of als de producten recente veranderingen niet weerspiegelen u aanbracht, kunt u [ kwesties van de catalogussynchronisatie ](#resolvesync) oplossen.

### Gesynchroniseerde producten

Hiermee geeft u het totale aantal producten weer dat is gesynchroniseerd vanuit de catalogus van [!DNL Commerce] . Na de eerste synchronisatie moeten alleen gewijzigde producten worden gesynchroniseerd.

## Resync {#resync}

Als u een resync van uw catalogus moet in werking stellen alvorens de per uur geplande synchronisatie voorkomt, kunt u een resync dwingen.

>[!NOTE]
>
> Dwingend een resync teweegbrengt een resync van uw volledige productcatalogus, die lading op hardwaremiddelen kan verhogen.

1. Van het _dashboard van de Synchronisatie van de Catalogus 0} {, uitgezochte_ Montages **.**

   De _pagina van de Montages van de Synchronisatie van de Catalogus_ verschijnt.

1. In de _sectie van Gegevens_ opnieuw synchroniseren, klik [!UICONTROL Resync].

   [!DNL Commerce] synchroniseert uw catalogus tijdens het volgende geplande synchronisatievenster. Afhankelijk van de grootte van de catalogus kan deze bewerking lang duren.

## Gesynchroniseerde catalogusproducten

De **Gesynchroniseerde catalogusproducten** lijst toont de volgende informatie.

| Veld | Beschrijving |
|---|---|
| ID | Unieke identificatiecode van het product |
| Naam | Storefront-naam van het product |
| Type | Identificeert het producttype, zoals eenvoudig, configureerbaar, of downloadbaar |
| Laatst geëxporteerd | De datum waarop het product voor het laatst is geëxporteerd uit uw catalogus |
| Laatst gewijzigd | Datum waarop het product voor het laatst is gewijzigd in uw catalogus |
| SKU | Geeft de voorraadeenheid voor het product weer |
| Prijs | Prijs van het product |
| Zichtbaarheid | De zichtbaarheidsinstelling van een product zoals gedefinieerd in de catalogus van [!DNL Commerce] |

## Synchronisatieproblemen met catalogi oplossen {#resolvesync}

Zie [ Logboeken en het oplossen van problemen ](../data-export/troubleshooting-logging.md#troubleshooting) in de _Gids van de Uitvoer van Gegevens SaaS_.
