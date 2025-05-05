---
title: feeds synchroniseren met de Commerce CLI
description: Leer hoe te om bevel-lijn interfacebevelen te gebruiken om voer en processen voor  [!DNL data export extension]  voor de diensten van Adobe Commerce te beheren SaaS.
exl-id: 1ebee09e-e647-4205-b90c-d0f9d2cac963
source-git-commit: 8233b2e184c8af293ffc41cb22e085388cf18049
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---

# feeds synchroniseren met de Commerce CLI

Met de opdracht `saas:resync` in het `magento/saas-export` -pakket kunt u gegevenssynchronisatie voor Adobe Commerce SaaS-services beheren.

Adobe raadt u niet aan de opdracht `saas:resync` regelmatig te gebruiken. De typische scenario&#39;s voor het gebruiken van het bevel zijn:

- Eerste synchronisatie
- De gegevens van de synchronisatie aan een nieuwe gegevensruimte na het veranderen van [ identiteitskaart van de Ruimte van Gegevens SaaS ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas)
- Problemen oplossen

Synchronisatiebewerkingen in het `var/log/saas-export.log` -bestand controleren.

## Beginsynchronisatie

>[!NOTE]
>
>De eerste synchronisatie wordt automatisch uitgevoerd wanneer Live zoeken of productaanbevelingen zijn ingeschakeld. Handmatige opdrachten zijn niet nodig.

Wanneer u een `saas:resync` activeert vanaf de opdrachtregel, afhankelijk van de grootte van de catalogus, kan het enkele minuten tot enkele uren duren voordat de gegevens zijn bijgewerkt.

Voor de eerste synchronisatie raadt Adobe aan de opdrachten in de volgende volgorde uit te voeren:

```shell
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions
```

## Synchroniseren met CLI-opdrachten

De opdracht `saas:resync` ondersteunt diverse synchronisatiebewerkingen:

- Gedeeltelijke synchronisatie door SKU
- Onderbroken synoniemen hervatten
- Gegevens valideren zonder te synchroniseren

Alle beschikbare opties weergeven:

```shell
bin/magento saas:resync --help
```

Zie de volgende secties voor opties beschrijvingen met voorbeelden.


>[!NOTE]
>
>Voor geavanceerde opties om uitvoerverwerking te beheren, zie [ uitvoerverwerking ](customize-export-processing.md) aanpassen.

## `--by-ids`

Wedersynchronisatie van specifieke entiteiten door hun id&#39;s. Ondersteunt de feeds `products` , `productAttributes` , `productOverrides` , `inventoryStockStatus` , `prices` , `variants` en `categoryPermissions` .

Wanneer u de optie `--by-ids` gebruikt, geeft u standaard waarden op met behulp van SKU-productwaarden. Als u product-id&#39;s wilt gebruiken, voegt u de optie `--id-type=ProductID` toe.

**Voorbeelden:**

```shell
bin/magento saas:resync --feed products --by-ids='ADB102,ADB111,ADB112'

bin/magento saas:resync --feed= products --by-ids='1,2,3' --id-type='productId'
```


## `--cleanup-feed`

Maak de indexeertabel van de feed schoon voordat u de gegevens opnieuw exporteert en naar SaaS verzendt. Alleen ondersteund voor `products`, `productAttributes`, `productOverrides`, `inventoryStockStatus`, `prices`, `variants` en `categoryPermissions` .

Als de bewerking wordt gebruikt met de optie `--dry-run` , wordt de resync-bewerking tijdens de uitvoering uitgevoerd voor alle items.

>[!IMPORTANT]
>
>Gebruik deze alleen nadat u de omgeving hebt opgeschoond of met de optie `--dry-run` . Als de opschoningsbewerking in andere gevallen wordt gebruikt, kunnen er problemen met gegevensverlies en gegevenssynchronisatie optreden.

**Voorbeeld:**

```shell
bin/magento saas:resync --feed products --cleanup-feed
```

## `--continue-resync`

Hervat een onderbroken resync-bewerking. Alleen ondersteund voor `products` -, `productAttributes` - en `productOverrides` -feeds.

**Voorbeeld:**

```shell
bin/magento saas:resync --feed productAttributes --continue-resync
```

## `--dry-run`

Voert het feed-redex-proces uit zonder de feed naar SaaS te verzenden en zonder op te slaan naar de voedertabel. Deze optie is handig als u problemen met uw gegevensset wilt identificeren.

Voeg de omgevingsvariabele `EXPORTER_EXTENDED_LOG=1` toe om de lading op te slaan naar `var/log/saas-export.log` .

**Voorbeeld:**

```shell
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed products --dry-run
```

### Specifieke feed-items testen

Test specifieke feed-items door de optie `--by-ids` toe te voegen met de uitgebreide logboekverzameling om de gegenereerde lading in het `var/log/saas-export.log` -bestand te zien.

**Voorbeeld:**

```shell
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed products --dry-run --by-ids='ADB102,ADB111,ADB112'
```

### Alle feed-items testen

Standaard bevat de feed die tijdens een `resync --dry-run` -bewerking wordt verzonden alleen nieuwe items of items die niet eerder zijn geëxporteerd. Als u alle items in de te verwerken feed wilt opnemen, gebruikt u de optie `--cleanup-feed` .

**Voorbeeld**

```shell
bin/magento saas:resync --feed products --dry-run --cleanup-feed
```

## `--feed`

Vereist. Hiermee geeft u de te synchroniseren feed-entiteit op.

Beschikbare feeds:

- `categories`
- `categoryPermissions`
- `inventoryStockStatus`
- `orders`
- `prices`
- `products`
- `productAttributes`
- `productOverrides`
- `scopesWebsite`
- `scopesCustomerGroup`
- `variants`

**Voorbeeld:**

```shell
bin/magento saas:resync --feed products
```

## `--no-reindex`

Hiermee verzendt u bestaande catalogusgegevens opnieuw naar [!DNL Commerce Services] zonder opnieuw te indexeren. Niet ondersteund voor productgerelateerde feeds.

Het gedrag varieert door [ de uitvoerwijze ](data-synchronization.md#synchronization-modes):

- Oudere modus: hiermee worden alle gegevens opnieuw verzonden zonder dat er wordt afgebroken.
- Modus Direct: optie wordt genegeerd, alleen worden updates/storingen gesynchroniseerd.

**Voorbeeld:**

```shell
bin/magento saas:resync --feed productAttributes --no-reindex
```

## `--id-type=ProductId`

Standaard worden de entiteiten die worden opgegeven wanneer u de opdracht `saas:resync feed` gebruikt met de optie `--by-ids` , opgegeven door product-SKU. Gebruik de optie `--id-type=ProductId` om entiteiten op product-id op te geven.

```shell
bin/magento saas:resync --feed products --by-ids='1,2,3' --id-type='productId'
```

**Voorbeeld:**

## Problemen oplossen

Als u de verwachte gegevens niet ziet in verbonden Commerce Services, kunt u problemen oplossen door de logboeken van fouten bij het exporteren van gegevens te controleren en de opdracht `saas:resync` te gebruiken met omgevingsvariabelen om de gegevens van de payloads en de analyse te bekijken. Zie [ logboeken van het Overzicht en los ](troubleshooting-logging.md) problemen op.
