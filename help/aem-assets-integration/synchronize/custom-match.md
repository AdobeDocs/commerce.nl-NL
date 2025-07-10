---
title: Aangepaste automatische matching
description: Leer hoe aangepaste automatische overeenkomsten vooral handig zijn voor handelaren met complexe matching-logica of voor bedrijven die vertrouwen op een systeem van derden dat geen metagegevens in AEM Assets kan invullen.
feature: CMS, Media, Integration
exl-id: e7d5fec0-7ec3-45d1-8be3-1beede86c87d
source-git-commit: 7639422b237ad04cada366c541c041bc146ce085
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Aangepaste automatische matching

Als de standaard automatische passende strategie (**automatische aanpassing OTB**) niet met uw specifieke bedrijfsvereisten wordt gericht, selecteer de optie van de douanegelijke. Deze optie steunt het gebruik van [ Adobe Developer App Builder ](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder) om een toepassing van de douanematcher te ontwikkelen die complexe passende logica, of activa behandelt die uit een derdesysteem komen dat meta-gegevens in AEM Assets niet kan bevolken.

## Aangepaste automatische overeenkomsten configureren

1. Navigeer in Commerce Admin naar **[!UICONTROL Store]** > Configuratie > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]** .

1. Selecteer **[!UICONTROL Custom Matcher]** als overeenkomende regel.

1. Wanneer u deze passende regel selecteert, toont Admin extra gebieden om **eindpunten** en noodzakelijke **authentificatieparameters** voor de douane passende logica te vormen.

## Eindpunten voor aangepaste matcher-API

Wanneer u een toepassing van de douanematcher gebruikend [ App Builder ](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder){target=_blank} bouwt, moet de toepassing de volgende eindpunten blootstellen:

* **activa van App Builder aan productURL** eindpunt
* **het product van App Builder aan activaURL** eindpunt

### App Builder-element naar URL-eindpunt van product

Dit eindpunt wint de lijst van SKUs verbonden aan een bepaald activa terug:

#### Voorbeeldgebruik

```bash
const { Core } = require('@adobe/aio-sdk')
 
async function main (params) {
    // return the products that map to the assetId
    return {
        statusCode: 200,
        body: {
          asset_id: "urn:aaid:aem:1aa1d4a0-18b8-40a7-a228-e0ab588deee1",
          product_matches: [
            {
              product_sku: "SKU1",
              asset_roles: ["thumbnail"],
              asset_position: [1]
            }
          ]
        }
   }
}
 
exports.main = main
```

**Verzoek**

```bash
GET https://your-app-builder-url/api/v1/web/app-builder-external-rule/asset-to-product
```

| Parameter | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `assetId` | String | Vertegenwoordigt de bijgewerkte element-id |

**Reactie**

```bash
{
  "asset_id": "{ASSET_ID}",
  "product_matches": [
    {
      "product_sku": "{PRODUCT_SKU_1}",
      "asset_roles": ["thumbnail","image"]
    },
    {
      "product_sku": "{PRODUCT_SKU_2}",
      "asset_roles": ["thumbnail"]
    }
  ]
}
```

### App Builder-product naar URL-eindpunt van element

Dit eindpunt wint de lijst van activa verbonden aan bepaalde SKU terug:

#### Voorbeeldgebruik

```bash
const { Core } = require('@adobe/aio-sdk')
 
async function main (params) {
    // return asset matches for a product
    return {
        statusCode: 200,
        body: {
          product_sku: params.productSku, //SKU-1
          asset_matches: [
            {
              asset_id: "urn:aaid:aem:1aa1d4a0-18b8-40a7-a228-e0ab588deee1",
              asset_roles: ["thumbnail","image"]
            }
          ]
        }
      }
}
 
exports.main = main
```

**Verzoek**

```bash
GET https://your-app-builder-url/api/v1/web/app-builder-external-rule/product-to-asset
```

| Parameter | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `productSKU` | String | Vertegenwoordigt het bijgewerkte product SKU |

**Reactie**

```bash
{
  "product_sku": "{PRODUCT_SKU}",
  "asset_matches": [
    {
      "asset_id": "{ASSET_ID_1}",
      "asset_roles": ["thumbnail","image"]
    },
    {
      "asset_id": "{ASSET_ID_2}",
      "asset_roles": ["thumbnail"]
    }
  ]
}
```

>[!TIP]
>
> In de `asset_roles` sleutel, gebruik gesteunde [ Commerce activa rollen ](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/products/digital-assets/product-image#image-roles) zoals `thumbnail`, `image`, `small_image`, en `swatch_image`.
