---
title: Aangepaste automatische matching
description: Leer hoe aangepaste automatische overeenkomsten vooral handig zijn voor handelaren met complexe matching-logica of voor bedrijven die vertrouwen op een systeem van derden dat geen metagegevens in AEM Assets kan invullen.
feature: CMS, Media, Integration
exl-id: e7d5fec0-7ec3-45d1-8be3-1beede86c87d
source-git-commit: 6e8d266aeaec4d47b82b0779dfc3786ccaa7d83a
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 1%

---

# Aangepaste automatische matching

Als de standaard automatische passende strategie (**automatische aanpassing OTB**) niet met uw specifieke bedrijfsvereisten wordt gericht, selecteer de optie van de douanegelijke. Deze optie steunt het gebruik van [&#x200B; Adobe Developer App Builder &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder) om een toepassing van de douanematcher te ontwikkelen die complexe passende logica, of activa behandelt die uit een derdesysteem komen dat meta-gegevens in AEM Assets niet kan bevolken.

## Aangepaste automatische overeenkomsten configureren

1. Navigeer in Commerce Admin naar **[!UICONTROL Store]** > Configuratie > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]** .

1. Selecteer **[!UICONTROL Custom Matcher]** als overeenkomende regel.

1. Wanneer u deze passende regel selecteert, toont Admin extra gebieden om **eindpunten** en noodzakelijke **authentificatieparameters** voor de douane passende logica te vormen.

### workspace.json

Het veld **[!UICONTROL Adobe I/O Workspace Configuration]** biedt een gestroomlijnde manier om uw aangepaste matcher te configureren door het App Builder `workspace.json` -configuratiebestand te importeren.

U kunt het `workspace.json` dossier van [&#x200B; Adobe Developer Console &#x200B;](https://developer.adobe.com/console) downloaden. Het bestand bevat alle gegevens en configuratiegegevens voor uw App Builder-werkruimte.

+++Voorbeeld `workspace.json`

```json
{
  "project": {
    "id": "project_id",
    "name": "project_name",
    "title": "title_name",
    "org": {
      "id": "id",
      "name": "Organization_name",
      "ims_org_id": "ims_id"
    },
    "workspace": {
      "id": "workspace_id",
      "name": "workspace_name_id",
      "title": "workspace_title_id",
      "action_url": "https://action_url.net",
      "app_url": "https://app_url.net",
      "details": {
        "credentials": [
          {
            "id": "credential_id",
            "name": "credential_name_id",
            "integration_type": "oauth_server_to_server",
            "oauth_server_to_server": {
              "client_id": "client_id",
              "client_secrets": ["secret"],
              "technical_account_email": "xx@technical_account_email.com",
              "technical_account_id": "technical_account_id",
              "scopes": [
                "AdobeID",
                "openid",
                "read_organizations",
                "additional_info.projectedProductContext",
                "additional_info.roles",
                "adobeio_api",
                "read_client_secret",
                "manage_client_secrets"
              ]
            }
          }
        ],
        "services": [
          {
            "code": "AdobeIOManagementAPISDK",
            "name": "I/O Management API"
          }
        ],
        "runtime": {
          "namespaces": [
            {
              "name": "namespace_name",
              "auth": "example_auth"
            }
          ]
        },
        "events": {
          "registrations": []
        },
        "mesh": {}
      }
    }
  }
}
```

+++

1. Sleep het `workspace.json` -bestand van uw App Builder-project naar het veld **[!UICONTROL Adobe I/O Workspace Configuration]** . U kunt ook klikken om te bladeren en het bestand te selecteren.

![&#x200B; Configuratie van Workspace &#x200B;](../assets/workspace-configuration.png){width="600" zoomable="yes"}

1. Het systeem automatisch:

   * Valideert de JSON-structuur
   * Extraheert en vult OAuth-referenties
   * Beschikbare runtimeacties voor de werkruimte ophalen
   * Hiermee vult u de vervolgkeuzemogelijkheden in voor de velden **[!UICONTROL Product to Asset URL]** en **[!UICONTROL Asset to Product URL]** .

1. Selecteer de juiste runtimeacties in de vervolgkeuzemenu&#39;s voor elke flow.

1. Klik op **[!UICONTROL Save Config]**.

## Eindpunten voor aangepaste matcher-API

Wanneer u een toepassing van de douanematcher gebruikend [&#x200B; App Builder &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder){target=_blank} bouwt, moet de toepassing de volgende eindpunten blootstellen:

* **activa van App Builder aan productURL** eindpunt
* **het product van App Builder aan activaURL** eindpunt

### App Builder-element naar URL-eindpunt van product

Dit eindpunt wint de lijst van SKUs verbonden aan een bepaald activa terug:

#### Voorbeeldgebruik

```javascript
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

    // Set skip to true if the mapping hasn't changed
    const skipSync = false;

    return {
        statusCode: 200,
        body: {
            asset_id: params.assetId,
            product_matches: [
                {
                    product_sku: "<YOUR-SKU-HERE>",
                    asset_roles: ["thumbnail", "image", "swatch_image", "small_image"],
                    asset_position: 1
                }
            ],
            skip: skipSync
        }
    };
}

exports.main = main;
```

**Verzoek**

```text
POST https://your-app-builder-url/api/v1/web/app-builder-external-rule/asset-to-product
```

| Parameter | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `assetId` | String | Vertegenwoordigt de bijgewerkte element-id. |
| `eventData` | String | Retourneert de gegevenslading die aan de element-id is gekoppeld. |

**Reactie**

```json
{
  "asset_id": "{ASSET_ID}",
  "product_matches": [
    {
      "product_sku": "{PRODUCT_SKU_1}",
      "asset_roles": ["thumbnail", "image"]
    },
    {
      "product_sku": "{PRODUCT_SKU_2}",
      "asset_roles": ["thumbnail"]
    }
  ],
  "skip": false
}
```

| Parameter | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `asset_id` | String | De element-id die overeenkomt. |
| `product_matches` | Array | Lijst met producten die aan het element zijn gekoppeld. |
| `skip` | Boolean | (Optioneel) In `true` slaat de regelengine de synchronisatie voor dit element over (geen update voor producttoewijzing). Wanneer `false` wordt uitgevoerd of weggelaten, wordt de normale verwerking uitgevoerd. Zie [&#x200B; synchronisatieverwerking &#x200B;](#skip-sync-processing) overslaan. |

### App Builder-product naar URL-eindpunt van element

Dit eindpunt wint de lijst van activa verbonden aan bepaalde SKU terug:

#### Voorbeeldgebruik

```javascript
const { Core } = require('@adobe/aio-sdk')

async function main(params) {
    // return asset matches for a product
    // Build your own matching logic here to return the assets that map to the productSku
    // var assetMatches = [];
    // params.productSku
    // ...
    // End of your matching logic

    // Set skip to true if the mapping hasn't changed
    const skipSync = false;

    return {
        statusCode: 200,
        body: {
            product_sku: params.productSku,
            asset_matches: [
                {
                    asset_id: "<YOUR-ASSET-ID-HERE>", // urn:aaid:aem:1aa1d5i2-17h8-40a7-a228-e3ur588deee1
                    asset_roles: ["thumbnail", "image", "swatch_image", "small_image"],
                    asset_format: "image", // can be "image" or "video"
                    asset_position: 1
                }
            ],
            skip: skipSync
        }
    };
}

exports.main = main;
```

**Verzoek**

```text
POST https://your-app-builder-url/api/v1/web/app-builder-external-rule/product-to-asset
```

| Parameter | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `productSKU` | String | Vertegenwoordigt de bijgewerkte product SKU. |
| `eventData` | String | Keert de gegevensuitlading verbonden aan het Product SKU terug. |

**Reactie**

```json
{
  "product_sku": "{PRODUCT_SKU}",
  "asset_matches": [
    {
      "asset_id": "{ASSET_ID_1}",
      "asset_roles": ["thumbnail", "image"],
      "asset_position": 1,
      "asset_format": "image"
    },
    {
      "asset_id": "{ASSET_ID_2}",
      "asset_roles": ["thumbnail"],
      "asset_position": 2,
      "asset_format": "image"
    }
  ],
  "skip": false
}
```

| Parameter | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `product_sku` | String | Het product-SKU dat wordt aangepast. |
| `asset_matches` | Array | Lijst met elementen die aan het product zijn gekoppeld. |
| `skip` | Boolean | (Optioneel) Wanneer `true` , slaat de regelengine de synchronisatie voor dit product over (geen update voor middelentoewijzing). Wanneer `false` wordt uitgevoerd of weggelaten, wordt de normale verwerking uitgevoerd. Zie [&#x200B; synchronisatieverwerking &#x200B;](#skip-sync-processing) overslaan. |

De parameter `asset_matches` bevat de volgende kenmerken:

| Kenmerk | Gegevenstype | Beschrijving |
| --- | --- | --- |
| `asset_id` | String | De element-id. |
| `asset_roles` | Array | Elementrollen. Gebruikt gesteunde [&#x200B; Commerce activa rollen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/products/digital-assets/product-image#image-roles) als `thumbnail`, `image`, `small_image`, en `swatch_image`. |
| `asset_format` | String | De indeling van het element. Mogelijke waarden zijn `image` en `video` . |
| `asset_position` | Getal | De positie van het element in de productgalerie. |

## Synchronisatieverwerking overslaan

Met de parameter `skip` kan uw aangepaste matcher de synchronisatie-verwerking voor specifieke elementen of producten omzeilen.

Wanneer uw App Builder-toepassing `"skip": true` retourneert in de reactie, verzendt de regelengine geen API-aanvragen voor dat middel of product naar Commerce. Deze optimalisatie vermindert onnodige API-aanroepen en verbetert de prestaties.
