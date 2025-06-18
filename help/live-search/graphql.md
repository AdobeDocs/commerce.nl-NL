---
title: GraphQL
description: De  [!DNL Live Search]  werkruimte van GraphQL laat u vragen met uw levende gegevens bouwen.
exl-id: d32edf42-1fb0-40f9-89e5-798b39521b77
source-git-commit: ff5c717dbdd638e114bccc3f6dec26f4be269194
workflow-type: tm+mt
source-wordcount: '39'
ht-degree: 0%

---

# GraphQL

De *werkruimte van GraphQL* staat beheerders toe om de vragen van GraphQL te bouwen en te testen gebruikend hun eigen gegevens.

Deze werkruimte steunt [`productSearch` ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) en [`attributeMetadata` ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/attribute-metadata/) vragen.

![ de werkruimte van GraphQL ](assets/graphql.png)

```graphql
query productSearch {
  productSearch(phrase: "a306") {
    total_count
    items {
      product {
        sku
        name
      }
    }
    facets {
      title
    }
  }
}
```

Variabelen:

```json
{
  "Magento-Environment-Id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "Magento-Website-Code": "base",
  "Magento-Store-Code": "base",
  "Magento-Store-View-Code": "default",
  "X-Api-Key": "search_gql"
}
```
