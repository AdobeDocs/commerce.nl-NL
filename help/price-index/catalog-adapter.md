---
title: Extensie Catalogusadapter
description: Catalogusadapter gebruiken om prijzen te renderen van Commerce Services
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: e42101fa-9c30-482c-a649-44dc35376abb
source-git-commit: 74f6cb64724194651c4eeb538c0c69142b01ac5d
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Catalogusadapter

De `[!DNL Catalog Adapter]` uitbreiding maakt de indexator van de standaardproductprijs inbegrepen in de toepassing van Commerce onbruikbaar en gebruikt prijzen die door de [&#x200B; Dienst van de Catalogus &#x200B;](../catalog-service/overview.md) in plaats daarvan worden verstrekt.

De adapter wordt ontworpen om met de [&#x200B; SaaS gegevensuitvoer &#x200B;](../data-export/overview.md) en de Dienst van Adobe Commerce te werken. De SaaS-gegevensuitvoer is verantwoordelijk voor het indienen van de prijzen en de [!DNL Catalog Adapter] haalt alle prijzen op van de Adobe Commerce Service.

Wanneer u de optie [!DNL Catalog Adapter] inschakelt, worden prijsindexering en bewerkingen op de volgende manieren beïnvloed:

- De prijsindex die in de Adobe Commerce-toepassing is opgenomen, is uitgeschakeld.
- De prijzen worden beheerd gebruikend de SaaS gegevensuitvoer en de [&#x200B; prijsindexeerder SaaS &#x200B;](price-indexing.md).
- Wanneer een klant een product, categorie of andere pagina opent waarop de productprijzen worden weergegeven, worden de prijzen opgehaald van de Adobe Commerce Service.
- De prijzen worden verzonden naar de Dienst van Adobe Commerce door gegevens van de [&#x200B; gegevens te synchroniseren SaaS uitvoeren &#x200B;](../data-export/overview.md).
- Met Afhandeling worden de prijzen dynamisch opnieuw berekend.

U kunt prijsindexering in de toepassing van Commerce opnieuw toelaten door de uitbreiding van de Adapter van de Catalogus te verwijderen of onbruikbaar te maken.

## Vereisten

- Adobe Commerce 2.4.4+
- Voor uw Adobe Commerce-omgeving moet een van de volgende Commerce-services zijn ingeschakeld en geconfigureerd:

   - [Live zoeken](../live-search/install.md)
   - [Aanbevelingen voor producten](../product-recommendations/install-configure.md)
   - [Catalogusservice](../catalog-service/installation.md)

## Installatie

De uitbreiding van de Adapter van de Catalogus is een metapakket Composer dat de volgende modules installeert:

- **Indexer van de Prijs gehandicapt** - Deze module maakt de prijsindex in de toepassing van Commerce onbruikbaar zodat de prijzen via prijsindexering SaaS worden geleverd. De indexeerfunctie van de productprijs in de Commerce-toepassing kan niet worden ingeschakeld wanneer de extensie voor indexering van de SaaS-prijs is geïnstalleerd.
- **de Leverancier van Prijzen** - Deze module verstrekt prijzen voor producten van de Dienst van Adobe Commerce. Het vormt de onderzoeksvraag en verkrijgt de prijzen voor de producten op het front.
- **Adapter van het Onderzoek van de Dienst van de Catalogus** - Deze module brengt prijzen van de toepassing van Adobe Commerce aan de Dienst van Adobe Commerce in antwoord op een verzoek van het productonderzoek over.

## Installatiestappen

>[!BEGINTABS]

>[!TAB  de infrastructuur van de Wolk ]

Gebruik deze methode om [!DNL Catalog Adapter] voor een Commerce Cloud-instantie te installeren.

1. Schakel op uw lokale werkstation de projectmap voor uw Adobe Commerce over het infrastructuurproject voor de cloud in.

   >[!NOTE]
   >
   >Voor informatie over het beheren van het projectmilieu&#39;s van Commerce plaatselijk, zie [&#x200B; het Leiden takken met CLI &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/cli-branches) in _Adobe Commerce op de Gids van de Gebruiker van de Infrastructuur van de Wolk_.

1. Bekijk de omgevingsvertakking voor update met de Adobe Commerce Cloud CLI.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Voeg de module Catalogusadapter toe.

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Pakketafhankelijkheden bijwerken.

   ```bash
   composer update "magento/catalog-adapter"
   ```

1. Wijzigingen in de code voor de bestanden `composer.json` en `composer.lock` doorvoeren en uitvoeren.

1. Voeg de codewijzigingen voor de `composer.json` - en `composer.lock` -bestanden toe, wijs deze toe en duw ze naar de cloudomgeving.

   ```shell
   git add -A
   git commit -m "Add catalog adapter module"
   git push origin <branch-name>
   ```

   Het duwen van de updates aan het wolkenmilieu stelt het [&#x200B; proces van de wolkenplaatsing van Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/process) in werking om de veranderingen toe te passen. Controleer de plaatsingsstatus van [&#x200B; opstellen logboek &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB  op-gebouw ]

Gebruik deze methode om [!DNL Catalog Adapter] voor een instantie op locatie te installeren.

1. Voeg de Adapter van de Catalogus aan uw project toe gebruikend Composer:

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Afhankelijkheden bijwerken en de extensie installeren:

   ```bash
   composer update  "magento/catalog-adapter"
   ```

1. Upgrade Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Cache wissen:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >In sommige gevallen, vooral wanneer het opstellen aan productie, zou u gecompileerde code kunnen willen vermijden omdat het wat tijd kan vergen. Zorg ervoor dat u een back-up van het systeem maakt voordat u wijzigingen aanbrengt.

>[!ENDTABS]


## De Adobe Commerce-productprijsindexator opnieuw inschakelen

Als u toepassingen van derden hebt die op de standaard het productprijsindexer van Adobe Commerce vertrouwen, kunt u het met de volgende bevelen opnieuw toelaten:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer
bin/magento index:reindex catalog_product_price
```

## De indexator van de Prijs van het Product voor Hoofdloze scenario onbruikbaar maken

Als u een Commerce-instantie zonder kop hebt, moet u mogelijk de Adobe Commerce-productprijsindexer uitschakelen om de belasting op uw Adobe Commerce-exemplaar te verminderen. U kunt deze taak voltooien door de module `magento/module-price-indexer-disabler` te installeren:

```bash
composer require magento/module-price-indexer-disabler
```

## Gebruiksscenario&#39;s

Hier volgen enkele veelvoorkomende `[!DNL Catalog Adapter]` scenario&#39;s.

### Geen afhankelijkheid van Adobe Commerce-productprijsindexator

- U bent een Luma- of Adobe Commerce Core GraphQL-handelaar die een vereiste service heeft geïnstalleerd (Live Search, Productaanbevelingen, Catalog Service)
- Geen integratie met extensies van derden die afhankelijk zijn van de Adobe Commerce-productprijsindexer

1. Installeer de [!DNL Catalog Adapter] .

### Met afhankelijkheid van Adobe Commerce product price indexer

- U bent een Luma- of Adobe Commerce Core GraphQL-handelaar die een ondersteunde service heeft geïnstalleerd (Live Search, Productaanbevelingen, Catalog Service)
- U gebruikt een extensie van derden die afhankelijk is van de Adobe Commerce-productprijsindexer

1. Installeer de [!DNL Catalog Adapter] .
1. Schakel de standaardindexeerfunctie voor Adobe Commerce-productprijzen opnieuw in.

### Headless Commerce-instanties

- Een bedrijf met een Commerce-exemplaar zonder kop waarop de vereiste services zijn geïnstalleerd (Live zoeken, Productaanbevelingen, Catalogusservice)
- Geen beroep op de standaard Adobe Commerce-productprijsindexer

1. Installeer de module `magento/module-price-indexer-disabler` vanuit het [!DNL Catalog Adapter] -pakket.
