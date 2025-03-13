---
title: feeds synchroniseren met de Commerce CLI
description: Leer hoe te om bevel-lijn interfacebevelen te gebruiken om voer en processen voor  [!DNL data export extension]  voor de diensten van Adobe Commerce te beheren SaaS.
exl-id: 1ebee09e-e647-4205-b90c-d0f9d2cac963
source-git-commit: 086a571b69e8ad76a912c339895409b0037642b9
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# feeds synchroniseren met de Commerce CLI

Met de opdracht `saas:resync` in het `magento/saas-export` -pakket kunt u gegevenssynchronisatie voor Adobe Commerce SaaS-services beheren.

Adobe raadt u niet aan de opdracht `saas:resync` regelmatig te gebruiken. De typische scenario&#39;s voor het gebruiken van het bevel zijn:

- Eerste synchronisatie
- De gegevens van de synchronisatie aan nieuwe gegevensruimte na het veranderen van [ identiteitskaart van de Ruimte van Gegevens SaaS ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas)
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

Wedersynchronisatie van specifieke entiteiten door hun id&#39;s. Ondersteunt feeds `products` , `productAttributes` en `productOverrides` .

Door gebrek, worden de entiteiten gespecificeerd door product SKU. Gebruik `--id-type=ProductID` om product-id&#39;s te gebruiken.

**Voorbeelden:**

```shell
bin/magento saas:resync --feed='<FEED_NAME>' --by-ids='<SKU-1>,<SKU-2>,<SKU-3>'

bin/magento saas:resync --feed='<FEED_NAME>' --by-ids='<ID-1>,<ID-2>,<ID-3>' --id-type='productId'
```

## `--cleanup-feed`

Wist de lijst van de voederindexeerder alvorens gegevens aan SaaS opnieuw te indexeren en te verzenden. Alleen ondersteund voor `products` -, `productOverrides` - en `prices` -feeds.

>[!IMPORTANT]
>
>Alleen gebruiken na schoonmaken van de omgeving. Kan problemen met gegevenssynchronisatie veroorzaken in Commerce Services.

**Voorbeeld:**

```shell
bin/magento saas:resync --feed='<FEED_NAME>' --cleanup-feed
```

## `--continue-resync`

Hervat een onderbroken resync-bewerking. Alleen ondersteund voor `products` -, `productAttributes` - en `productOverrides` -feeds.

**Voorbeeld:**

```shell
bin/magento saas:resync --feed='<FEED_NAME>' --continue-resync
```

## `--dry-run`

Voert het herindexproces van de feed uit zonder dat het aan SaaS wordt voorgelegd of op de voederingstabel wordt opgeslagen. Wordt gebruikt om gegevens te valideren.

Voeg de omgevingsvariabele `EXPORTER_EXTENDED_LOG=1` toe om de lading op te slaan naar `var/log/saas-export.log` .

**Voorbeeld:**

```shell
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed='<FEED_NAME>' --dry-run
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
bin/magento saas:resync --feed='<FEED_NAME>'
```

## `--no-reindex`

Hiermee verzendt u bestaande catalogusgegevens opnieuw naar [!DNL Commerce Services] zonder opnieuw te indexeren. Niet ondersteund voor productgerelateerde feeds.

Het gedrag varieert door [ de uitvoerwijze ](data-synchronization.md#synchronization-modes):

- Oudere modus: hiermee worden alle gegevens opnieuw verzonden zonder dat er wordt afgebroken.
- Modus Direct: optie wordt genegeerd, alleen worden updates/storingen gesynchroniseerd.

**Voorbeeld:**

```shell
bin/magento saas:resync --feed='<FEED_NAME>' --no-reindex
```

## Problemen oplossen

Als u de verwachte gegevens niet ziet in verbonden Commerce Services, kunt u problemen oplossen door de logboeken van fouten bij het exporteren van gegevens te controleren en de opdracht `saas:resync` te gebruiken met omgevingsvariabelen om de gegevens van de payloads en de analyse te bekijken. Zie [ logboeken van het Overzicht en los ](troubleshooting-logging.md) problemen op.
