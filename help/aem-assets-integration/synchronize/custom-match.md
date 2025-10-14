---
title: Aangepaste automatische matching
description: Leer hoe aangepaste automatische overeenkomsten vooral handig zijn voor handelaren met complexe matching-logica of voor bedrijven die vertrouwen op een systeem van derden dat geen metagegevens in AEM Assets kan invullen.
feature: CMS, Media, Integration
exl-id: e7d5fec0-7ec3-45d1-8be3-1beede86c87d
source-git-commit: ee1dd902a883e5653a9fb8764fac708975c37091
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Aangepaste automatische matching

Als de standaard automatische passende strategie (**automatische aanpassing OTB**) niet met uw specifieke bedrijfsvereisten wordt gericht, selecteer de optie van de douanegelijke. Deze optie steunt het gebruik van [&#x200B; Adobe Developer App Builder &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder) om een toepassing van de douanematcher te ontwikkelen die complexe passende logica, of activa behandelt die uit een derdesysteem komen dat meta-gegevens in AEM Assets niet kan bevolken.

## Aangepaste automatische overeenkomsten configureren

1. Navigeer in Commerce Admin naar **[!UICONTROL Store]** > Configuratie > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]** .

1. Selecteer **[!UICONTROL Custom Matcher]** als overeenkomende regel.

1. Wanneer u deze passende regel selecteert, toont Admin extra gebieden om **eindpunten** en noodzakelijke **authentificatieparameters** voor de douane passende logica te vormen.

## Eindpunten voor aangepaste matcher-API

Wanneer u een toepassing van de douanematcher gebruikend [&#x200B; App Builder &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder){target=_blank} bouwt, moet de toepassing de volgende eindpunten blootstellen:

* **activa van App Builder aan productURL** eindpunt
* **het product van App Builder aan activaURL** eindpunt

### App Builder-element naar URL-eindpunt van product

Dit eindpunt wint de lijst van SKUs verbonden aan een bepaald activa terug:

#### Voorbeeldgebruik

```bash
const { Core } = require('@adobe/aio-sdk')

async function main(params) {

    // Build your own matching logic here to return the products that map to the assetId
    // var productMatches = [];
    // params.assetId
    // params.eventData.assetMetadata['commerce:isCommerce']
    // params.eventData.assetMetadata['commerce:skus'][i]
    // params.eventData.assetMetadata['commerce:roles']
    // params.eventData.assetMetadata['commerce:positions'][i]
    // ...
    // End of your matching logic

    return {
        statusCode: 500,
        body: {
            asset_id: params.assetId,
            product_matches: [
                {
                    product_sku: "<YOUR-SKU-HERE>",
                    asset_roles: ["thumbnail", "image", "swatch_image", "small_image"],
                    asset_position: 1
                }
            ]
        }
    };
}

exports.main = main;
```

**Verzoek**

```bash
POST https://your-app-builder-url/api/v1/web/app-builder-external-rule/asset-to-product
```

| Parameter | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `assetId` | String | Vertegenwoordigt de bijgewerkte element-id. |
| `eventData` | String | Retourneert de gegevenslading die aan de element-id is gekoppeld. |

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

async function main(params) {
    // return asset matches for a product
    // Build your own matching logic here to return the assets that map to the productSku
    // var assetMatches = [];
    // params.productSku
    // ...
    // End of your matching logic

    return {
        statusCode: 500,
        body: {
            product_sku: params.productSku,
            asset_matches: [
                {
                    asset_id: "<YOUR-ASSET-ID-HERE>", // urn:aaid:aem:1aa1d5i2-17h8-40a7-a228-e3ur588deee1
                    asset_roles: ["thumbnail", "image", "swatch_image", "small_image"],
                    asset_format: "image", // can be "image" or "video"
                    asset_position: 1
                }
            ]
        }
    };
}

exports.main = main;
```

**Verzoek**

```bash
POST https://your-app-builder-url/api/v1/web/app-builder-external-rule/product-to-asset
```

| Parameter | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `productSKU` | String | Vertegenwoordigt de bijgewerkte product SKU. |
| `eventData` | String | Keert de gegevensuitlading verbonden aan het Product SKU terug. |

**Reactie**

```bash
{
  "product_sku": "{PRODUCT_SKU}",
  "asset_matches": [
    {
      "asset_id": "{ASSET_ID_1}",
      "asset_roles": ["thumbnail","image"],
      "asset_position": 1,
      "asset_format": image
    },
    {
      "asset_id": "{ASSET_ID_2}",
      "asset_roles": ["thumbnail"]
      "asset_position": 2,
      "asset_format": image     
    }
  ]
}
```

| Parameter | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `productSKU` | String | Vertegenwoordigt de bijgewerkte product SKU. |
| `asset_matches` | String | Retourneert alle elementen die aan een specifieke product-SKU zijn gekoppeld. |

De parameter `asset_matches` bevat de volgende kenmerken:

| Kenmerk | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `asset_id` | String | Vertegenwoordigt de bijgewerkte element-id. |
| `asset_roles` | String | Retourneert alle beschikbare elementrollen. Gebruikt gesteunde [&#x200B; Commerce activa rollen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/products/digital-assets/product-image#image-roles) als `thumbnail`, `image`, `small_image`, en `swatch_image`. |
| `asset_format` | String | Geeft de beschikbare indelingen voor het element. Mogelijke waarden zijn `image` en `video` . |
| `asset_position` | String | Hiermee geeft u de positie van het element weer. |
