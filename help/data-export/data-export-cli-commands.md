---
title: Opdrachtregelinterface SaaS-gegevens exporteren
description: Leer hoe te om bevel-lijn interfacebevelen te gebruiken om voer en processen voor  [!DNL data export extension]  voor de diensten van Adobe Commerce te beheren SaaS.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Opdracht-lijn Interfaceverwijzing SaaS-gegevens exporteren

De ontwikkelaars en de systeembeheerders kunnen synchronisatieverrichtingen voor SaaS- gegevensuitvoer beheren gebruikend het [ bevel-lijn van Adobe Commerce hulpmiddel ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI). De opdracht `saas:resync` wordt opgenomen in het pakket `magento/saas-export` .

Adobe raadt u niet aan de opdracht `saas:resync` regelmatig te gebruiken. De typische scenario&#39;s voor het gebruiken van het bevel zijn:

- De eerste synchronisatie
- [ identiteitskaart van de Ruimte van Gegevens SaaS ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) werd veranderd, en u moet gegevens aan de nieuwe gegevensruimte synchroniseren.
- Problemen oplossen

## Beginsynchronisatie

>[!NOTE]
>Als u Live zoeken of productaanbevelingen gebruikt, hoeft u de eerste synchronisatie niet uit te voeren. Het proces wordt automatisch gestart nadat u de service hebt verbonden met uw Commerce-instantie.

Wanneer u een `saas:resync` activeert vanaf de opdrachtregel, afhankelijk van de grootte van de catalogus, kan het enkele minuten tot enkele uren duren voordat de gegevens zijn bijgewerkt.

Voor de eerste synchronisatie raadt Adobe aan de opdrachten in de volgende volgorde uit te voeren:

```bash
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

## Voorbeelden van opdrachten

Alvorens `saas:resync` bevelen te gebruiken, herzie de [ optiedecbeschrijvingen ](#command-options).

- Voer een volledige resync voor een entiteitvoer uit.

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  Feeds die al zijn geëxporteerd, worden niet opnieuw gesynchroniseerd.

- De opgegeven feed- en opschoongegevens volledig opnieuw synchroniseren

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  Alleen gebruiken na het uitvoeren van een [!DNL Data Space ID Cleanup] -bewerking.

- Voor directe exportfeeds verzendt u alle gegevens opnieuw naar verbonden Commerce-services zonder de indexgegevens in de voedertabel af te kappen

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- Beschikbare opdrachten en opties weergeven met beschrijvingen.

  ```
  bin/magento saas:resync --help
  ```

## Opdrachtopties

De volgende opties zijn beschikbaar voor het beheer van `saas:resync` -bewerkingen.

>[!NOTE]
>
>De opdracht `saas:resync` ondersteunt ook geavanceerde opties om opdrachten voor het exporteren van gegevens te verbeteren door de batch te vergroten en verwerking met meerdere threads toe te voegen. Zie [ uitvoerverwerking ](customize-export-processing.md) aanpassen.

### `feed`

Met deze optie wordt opgegeven welke feed-entiteit opnieuw moet worden gesynchroniseerd, zoals `products` .

De waarde van de optie `feed` kan elk van de beschikbare feeds voor entiteiten bevatten:

- `products`: invoer van productgegevens
- `productAttributes`: gegevenstoevoer voor productkenmerken
- `categories`: gegevensfeed voor categorieën
- `variants`: configureerbare gegevenstoevoer voor productvariaties
- `prices`: invoer van productprijsgegevens
- `categoryPermissions`: gegevenstoevoer voor machtigingen voor categorieën
- `productOverrides`: invoer van gegevens voor productmachtigingen
- `inventoryStockStatus`: invoer van voorraadstatusgegevens
- `scopesWebsite`: websites met gegevensfeed voor weergaven van winkels en winkels
- `scopesCustomerGroup`: gegevenstoevoer voor klantgroepen
- `orders`: gegevensfeed voor verkooporders

Afhankelijk van welke [ de Diensten van Commerce ](../landing/saas.md) geïnstalleerd zijn, zou u een verschillende reeks voer kunnen hebben beschikbaar voor het `saas:resync` bevel.

### `no-reindex`

Met deze optie worden de bestaande catalogusgegevens opnieuw naar [!DNL Commerce Services] verzonden zonder opnieuw te worden gekoppeld. Als deze optie niet is opgegeven, voert de opdracht een volledige redex uit voordat gegevens worden gesynchroniseerd.

Het gedrag van deze optie hangt af van of het voer in [ erfenis of directe de uitvoerwijze ](data-synchronization.md#synchronization-modes) wordt uitgevoerd

- Voor verouderde exportfeeds worden de geïndexeerde gegevens in de feeds-tabel niet afgebroken tijdens het synchronisatieproces. In plaats daarvan worden alle gegevens opnieuw naar de Adobe Commerce-service verzonden.
- Voor directe exportfeeds wordt deze optie genegeerd als deze wordt opgegeven. Voor deze feeds wordt de index niet afgekapt door het resync-proces en worden alleen updates of items die eerder zijn mislukt, opnieuw gesynchroniseerd.

### `cleanup`

Met deze optie wordt de tabel met indexitems voor een synchronisatie gewist. Wanneer gespecificeerd, voert de gegevensuitvoer SaaS een volledige resync voor het gespecificeerde voer uit en schoont omhoog alle bestaande gegevens in de voederlijst.

Adobe raadt u aan deze opdracht alleen te gebruiken nadat u de bewerking [!DNL Data Space ID Cleanup] hebt uitgevoerd.

>[!WARNING]
>
>**gebruik regelmatig deze optie niet**. Er kunnen problemen met gegevenssynchronisatie optreden in Adobe Commerce Services. De instructie `delete product event` wordt bijvoorbeeld niet doorgegeven aan de Adobe Commerce-service als de optie `cleanup` wordt gebruikt.

## Problemen oplossen

Als u de verwachte gegevens niet ziet in verbonden Commerce Services, kunt u problemen oplossen door de logboeken van fouten bij het exporteren van gegevens te controleren en de opdracht `saas:resync` te gebruiken met omgevingsvariabelen om de gegevens van de payloads en de analyse te bekijken. Zie [ logboeken van het Overzicht en los ](troubleshooting-logging.md) problemen op.
