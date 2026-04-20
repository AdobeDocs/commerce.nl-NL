---
title: Bestanden toevoegen aan producten
description: Leer hoe te om dossiers zoals PDFs, handboeken, en gegevensbladen aan producten toe te voegen gebruikend dossier-type productattributen in  [!DNL Adobe Commerce as a Cloud Service].
feature: Catalog Management, Products, Integration
role: Admin, Developer
level: Intermediate
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 14c4178338859d55a7391139033d51d1aa6f7678
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# Bestanden toevoegen aan producten

[!DNL Adobe Commerce as a Cloud Service] steunt een &quot;Dossier&quot;[&#x200B; type van de productkenmerkinput &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/product-attributes/attributes-input-types){target="_blank"} dat verkopers toestaat om dossiers-zulke zoals PDFs, handboeken, certificaten, en gegevensbladen rechtstreeks aan producten vast te maken. Bestanden worden opgeslagen in Amazon S3 media-opslag en kunnen worden geopend via de opslagomgeving met GraphQL of via integratie met de REST API.

Er zijn drie manieren om bestanden te uploaden naar productbestandskenmerken:

* [&#x200B; Admin UI &#x200B;](#upload-files-through-the-admin) - uploadt manueel dossiers op het product uitgeeft pagina.
* [&#x200B; REST API &#x200B;](#upload-through-the-rest-api) - upload dossiers door REST API gebruikend S3 presigned URLs.
* [&#x200B; de invoer van het Product &#x200B;](#upload-through-product-import) - de dossiers van de Invoer in bulk door externe URLs in CSV te verstrekken.

## Vereisten

Voordat u bestanden kunt uploaden, moet u een bestandskenmerk maken en dit aan een kenmerkset toewijzen.

* [&#x200B; creeer een dossierattribuut &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create){target="_blank"} - reeks **[!UICONTROL Catalog Input Type for Store Owner]** aan **[!UICONTROL File]**.

* [&#x200B; wijs de attributen aan een attributenreeks &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/product-attributes/create/attribute-sets#create-an-attribute-set){target="_blank"} toe - sleep het nieuwe dossierattribuut in de gewenste groep.

* Vorm toegestane dossiertypes en grootte in de [&#x200B; Configuratie van de Attributen van het Dossier van het Product &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/catalog/product-file-attributes).

## Bestanden uploaden via de beheerder

Nadat u [&#x200B; een dossierattribuut &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create){target="_blank"} creeert en het aan een kenmerkenreeks toewijst, kunt u dossiers van product direct uploaden uitgeeft pagina.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.

1. Open het product dat u wilt bewerken.

1. Zoek het veld voor bestandskenmerken en klik op **[!UICONTROL Upload]** om een bestand te selecteren.

![&#x200B; uploadt dossierknoop in Admin &#x200B;](./assets/upload-file.png){width="600" zoomable="yes"}

1. Klik op **[!UICONTROL Save]**.

U vervangt een bestand door het bestaande bestand te verwijderen en een nieuw bestand te uploaden. Het geüploade bestand wordt opgeslagen in Amazon S3-mediaopslag.

## Uploaden via de REST API

Gebruik de [&#x200B; S3 vooraf ondertekende stroom URL &#x200B;](https://developer.adobe.com/commerce/webapi/rest/saas-integrations/s3-uploads/){target="_blank"} om dossiers programmatically door REST API te uploaden. Dit proces werkt voor productbestandskenmerken op dezelfde manier als voor andere mediatypen, zoals categorieafbeeldingen en kenmerkbestanden van de klant.

Het proces bestaat uit vier stappen:

1. Roep `POST V1/media/initiate-upload` aan met de bestandsnaam en de lus `media_resource_type` for product file attributes.
1. Gebruik de geretourneerde vooraf ondertekende URL om het bestand rechtstreeks naar Amazon S3 te sturen. `PUT`
1. Roep `POST V1/media/finish-upload` aan om de upload te bevestigen.
1. Wijs de teruggekeerde sleutel aan het het dossierattribuut van het product door `PUT /V1/products/{sku}` toe, die de sleutel als [&#x200B; waarde van de douaneattributen &#x200B;](https://developer.adobe.com/commerce/webapi/rest/modules/custom-attributes/) overgaat.

## Uploaden via productimport

U kunt dossiers aan producten in bulk vastmaken gebruikend [&#x200B; invoer API &#x200B;](https://developer.adobe.com/commerce/webapi/rest/modules/import/){target="_blank"} of Admin de invoer UI. De de dossierattributen van het product steunen de invoer van externe URLs slechts, die de zelfde benadering zoals [&#x200B; Methode 2 voor de invoer van het productbeeld &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/import/data-import-product-images#method-2-import-images-from-external-server){target="_blank"} volgt. Commerce downloadt het bestand van de opgegeven URL en slaat het op in S3-mediaopslag.

>[!NOTE]
>
>Het importeren van bestanden vanaf een lokaal serverpad (methode 1) wordt niet ondersteund in [!DNL Adobe Commerce as a Cloud Service] omdat er geen directe toegang tot het bestandssysteem is.

### Geef de URL op in een specifieke kolom

Gebruik de kenmerkcode als CSV-kolomkop en de volledige URL als waarde. Als de kenmerkcode bijvoorbeeld `file_upload` is, ziet de CSV er als volgt uit:

```csv
sku,name,file_upload
ADB112,"My Product",https://example.com/files/manual.pdf
```

### Geef de URL op in `additional_attributes`

U kunt ook het bestandskenmerk in de kolom `additional_attributes` opnemen:

```csv
sku,name,additional_attributes
ADB112,"My Product",file_upload=https://example.com/files/manual.pdf
```

In beide gevallen, moet URL openbaar toegankelijk zijn, en de dossieruitbreiding en de grootte moeten aan de [&#x200B; gevormde beperkingen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/catalog/product-file-attributes){target="_blank"} voldoen.

## Bestanden ophalen via GraphQL

In [!DNL Adobe Commerce as a Cloud Service], dient het [&#x200B; 2&rbrace; eindpunt van GraphQL van de Dienst van de Catalogus productgegevens. &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/){target="_blank"} Bestandskenmerken worden weergegeven in het veld `attributes` op `ProductView` , met de `value` die de volledige openbare URL naar het bestand bevat:

```graphql
{
  products(skus: ["ADB112"]) {
    sku
    name
    attributes(roles: []) {
      name
      label
      value
    }
  }
}
```

De reactie omvat het bestandskenmerk met de openbare URL:

```json
{
  "data": {
    "products": [
      {
        "sku": "ADB112",
        "name": "Example product",
        "attributes": [
          {
            "name": "file",
            "label": "FILE",
            "value": "https://<host>/media/catalog/product_file/manual.pdf",
          }
        ]
      }
    ]
  }
}
```

>[!NOTE]
>
>Voor deze query zijn de headers `Magento-Website-Code` en `Magento-Store-View-Code` vereist. Voor meer informatie, zie de [&#x200B; de productvraag van de Dienst van de Catalogus &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/){target="_blank"}.

## Bestanden ophalen via de REST API

Wanneer het terugwinnen van een product door [&#x200B; REST API &#x200B;](https://developer.adobe.com/commerce/webapi/reference/rest/saas/){target="_blank"} (`GET /V1/products/{sku}`), verschijnen de dossierattributen in `custom_attributes` serie met filename als waarde:

```json
{
  "custom_attributes": [
    {
      "attribute_code": "file_upload",
      "value": "manual_7aa0b2d63f6d3dbf.pdf"
    }
  ]
}
```
