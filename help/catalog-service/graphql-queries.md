---
title: '[!DNL Retrieve catalog data with GraphQL]'
description: Gebruik GraphQL-query's om de catalogusgegevens op te halen en Commerce-ervaringen te stimuleren.
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
exl-id: 49bbdb3b-bbe9-4777-8ea7-3bd25ae53889
source-git-commit: a4c3a24deb77a9aadc7954b46d171b4d4edea6ba
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Catalogusgegevens ophalen met GraphQL {#graphql-queries}

Met GraphQL-query&#39;s kunt u producten, prijzen en andere gegevens ophalen uit de Adobe Commerce Catalog SaaS-gegevensruimte en deze gebruiken om Commerce-ervaringen sneller te renderen dan met de native Adobe Commerce GraphQL-query&#39;s.

{{aco-merchandising-services}}

De Catalogusservice biedt de volgende query&#39;s:

| Query | Beschrijving | Gebruik |
|-------|-------------|-------|
| `categories` | Retourneert categoriegegevens. Als het invoerobject van de substructuur is opgegeven, retourneert de query details over subcategorieën. | Nuttig om de navigatie van de storefront en categoriepagina&#39;s terug te geven. [&#x200B; zie voorbeeld.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) |
| `products` | Retourneert details over de SKU&#39;s die zijn opgegeven als invoer. | Wordt voornamelijk gebruikt om inhoud weer te geven op productdetails en productvergelijkingspagina&#39;s. [&#x200B; zie voorbeeld.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) |
| `productSearch` | Retourneert een lijst met producten die voldoen aan de zoekcriteria. | Nuttig voor het weergeven van zoekresultaten en pagina&#39;s met productlijsten op basis van zoekgegevens. [&#x200B; zie voorbeeld.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) |
| `refineProduct` | Verkort de resultaten van een productvraag tegen een complex product wordt in werking gesteld om een specifieke informatie over een productvariant terug te keren. | Nuttig voor het weergeven van bijgewerkte productdetailpagina&#39;s wanneer de kopers een productoptie selecteren. [&#x200B; zie voorbeeld.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/refine-product/) |
| `variants` | Geeft details over alle variaties van een product. | Nuttig voor het weergeven van variantafbeeldingen op productdetails of pagina&#39;s zonder meerdere API-aanvragen in te dienen. [&#x200B; zie voorbeeld.](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/product-variants/) |

Zie {de Diensten GraphQL van 0} Storefront [&#x200B; voor meer informatie over het gebruiken van deze vragen.](https://developer.adobe.com/commerce/webapi/graphql/schema/storefront-services/)
