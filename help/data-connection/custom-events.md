---
title: Aangepaste gebeurtenissen maken
description: Leer hoe u aangepaste gebeurtenissen maakt om uw Adobe Commerce-gegevens te koppelen aan andere Adobe DX-producten.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: db782c0a-8f13-4076-9b17-4c5bf98e9d01
source-git-commit: 25d796da49406216f26d12e3b1be01902dfe9302
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Aangepaste gebeurtenissen maken

U kunt het [ gebeurtenisplatform ](events.md) uitbreiden door uw eigen storefront gebeurtenissen te creëren om gegevens te verzamelen uniek aan uw industrie. Wanneer u creeert en een douanegebeurtenis vormt, wordt het verzonden naar de [ Collector van de Gebeurtenissen van Adobe Commerce ](https://github.com/adobe/commerce-events/tree/main/packages/storefront-events-collector).

## Aangepaste gebeurtenissen afhandelen

Aangepaste gebeurtenissen worden alleen ondersteund voor de Adobe Experience Platform. Aangepaste gegevens worden niet doorgestuurd naar Adobe Commerce-dashboards en metrieke trackers.

Voor elke `custom` -gebeurtenis:

- Voegt `identityMap` met `ECID` toe als primaire identiteit
- Omvat `email` in `identityMap` als secundaire identiteit _als_ `personalEmail.address` in de gebeurtenis wordt geplaatst
- Hiermee wordt de volledige gebeurtenis binnen een `xdm` -object geprononceerd voordat deze naar de Edge wordt doorgestuurd

Voorbeeld:

Aangepaste gebeurtenis gepubliceerd via Adobe Commerce Events SDK:

```javascript
mse.publish.custom({
    commerce: {
        saveForLaters: {
            value: 1,
        },
    },
});
```

In Experience Platform Edge:

```javascript
{
  xdm: {
    identityMap: {
      ECID: [
        {
          id: 'ecid1234',
          primary: true
        }
      ],
      email: [
        {
          id: "runs@safari.ke",
          primary: false
        }
      ]
    },
    commerce: {
        saveForLaters: {
            value: 1
        }
    }
  }
}
```

>[!NOTE]
>
> Het gebruik van aangepaste gebeurtenissen kan invloed hebben op standaard Adobe Analytics-rapporten.

## Overschrijvingen van gebeurtenissen afhandelen (aangepaste kenmerken)

Voor elke gebeurtenis die met een `customContext` is ingesteld, overschrijft of breidt de verzamelaar de velden in de gebeurtenislading van de velden in de `custom context` . Het gebruik van overschrijvingen is mogelijk wanneer een ontwikkelaar contexten die door andere delen van de pagina zijn ingesteld, opnieuw wil gebruiken en uitbreiden in gebeurtenissen die al worden ondersteund.

Overschrijvingen van gebeurtenissen zijn alleen van toepassing wanneer u deze naar Experience Platform doorstuurt. Ze worden niet toegepast op analytische gebeurtenissen van Adobe Commerce en Sensei. De Collector van de Gebeurtenissen van Adobe Commerce [ README ](https://github.com/adobe/commerce-events/blob/e34bcfc0deca8d5ac1f9310fc1ee4c1becf4ffbb/packages/storefront-events-collector/README.md) verstrekt extra info.

>[!NOTE]
>
>Wanneer u `productListItems` uitbreidt met aangepaste kenmerken in Experience Platform-gebeurtenisladingen, dient u producten overeen te laten komen met gebruik van SKU. Deze vereiste geldt niet voor `product-page-view` -gebeurtenissen.

### Gebruik

```javascript
const mse = window.magentoStorefrontEvents;

mse.publish.productPageView(customCtx);
```

### Voorbeeld 1 - toevoegen `productCategories`

```javascript
magentoStorefrontEvents.publish.productPageView({
    productListItems: [
        {
            productCategories: [
                {
                    categoryID: "cat_15",
                    categoryName: "summer pants",
                    categoryPath: "pants/mens/summer",
                },
            ],
        },
    ],
});
```

### Voorbeeld 2 - aangepaste context toevoegen vóór publicatie van gebeurtenis

```javascript
const mse = window.magentoStorefrontEvents;

mse.context.setCustom({
  productListItems: [
    {
      productCategories: [
        {
          categoryID: "cat_15",
          categoryName: "summer pants",
          categoryPath: "pants/mens/summer",
        },
      ],
    },
  ],
});

mse.publish.productPageView();
```

### Voorbeeld 3 - de douanecontext die in de uitgever wordt geplaatst beschrijft de douanecontext eerder in de Laag van Gegevens van de Cliënt van Adobe wordt geplaatst.

In dit voorbeeld, zal de `pageView` gebeurtenis **Naam van de Pagina van de Douane 2** op het `web.webPageDetails.name` gebied hebben.

```javascript
const mse = window.magentoStorefrontEvents;

mse.context.setCustom({
  web: {
    webPageDetails: {
      name: 'Custom Page Name 1'
    },
  },
});

mse.publish.pageView({
  web: {
    webPageDetails: {
      name: 'Custom Page Name 2'
    },
  },
});
```

### Voorbeeld 4 - aangepaste context toevoegen aan `productListItems` met gebeurtenissen met meerdere producten

```javascript
const mse = window.magentoStorefrontEvents;

mse.context.setCustom({
  productListItems: [
    {
      SKU: "24-WB01", //Match SKU to override correct product in event payload
      productCategory: "Hand Bag", //Custom attribute added to event payload
      name: "Strive Handbag (CustomName)" //Override existing attribute with custom value in event payload
    },
    {
      SKU: "24-MB04",
      productCategory: "Backpack Bag",
      name: "Strive Backpack (CustomName)"
    },
  ],
});

mse.publish.shoppingCartView();
```

>[!NOTE]
>
> Het overschrijven van gebeurtenissen met aangepaste kenmerken kan van invloed zijn op standaard Adobe Analytics-rapporten.
