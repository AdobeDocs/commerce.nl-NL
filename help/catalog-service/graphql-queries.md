---
title: '[!DNL Retrieve catalog data with GraphQL]'
description: Gebruik GraphQL-query's om de catalogusgegevens op te halen en Commerce-ervaringen te stimuleren.
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
exl-id: 49bbdb3b-bbe9-4777-8ea7-3bd25ae53889
source-git-commit: ff5c717dbdd638e114bccc3f6dec26f4be269194
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Catalogusgegevens ophalen met GraphQL {#graphql-queries}

Met GraphQL-query&#39;s kunt u producten, prijzen en andere gegevens ophalen uit de Adobe Commerce Catalog SaaS-gegevensruimte en deze gebruiken om Commerce-ervaringen sneller te renderen dan met de native Adobe Commerce GraphQL-query&#39;s.

De Catalogusservice biedt de volgende query&#39;s:

| Query | Beschrijving | Gebruik |
|-------|-------------|-------|
| `categories` | Retourneert categoriegegevens. Als het invoerobject van de substructuur is opgegeven, retourneert de query details over subcategorieën. | Nuttig om de navigatie van de storefront en categoriepagina&#39;s terug te geven. [ zie voorbeeld.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) |
| `products` | Retourneert details over de SKU&#39;s die zijn opgegeven als invoer. | Wordt voornamelijk gebruikt om inhoud weer te geven op productdetails en productvergelijkingspagina&#39;s. [ zie voorbeeld.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) |
| `productSearch` | Retourneert een lijst met producten die voldoen aan de zoekcriteria. | Nuttig voor het weergeven van zoekresultaten en pagina&#39;s met productlijsten op basis van zoekgegevens. [ zie voorbeeld.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) |
| `refineProduct` | Verkort de resultaten van een productvraag tegen een complex product wordt in werking gesteld om een specifieke informatie over een productvariant terug te keren. | Nuttig voor het weergeven van bijgewerkte productdetailpagina&#39;s wanneer de kopers een productoptie selecteren. [ zie voorbeeld.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/refine-product/) |
| `variants` | Geeft details over alle variaties van een product. | Nuttig voor het weergeven van variantafbeeldingen op productdetails of pagina&#39;s zonder meerdere API-aanvragen in te dienen. [ zie voorbeeld.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/product-variants/) |

Zie de [ Gids van de Dienst API van de Catalogus ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/) voor meer informatie over het gebruiken van deze vragen
