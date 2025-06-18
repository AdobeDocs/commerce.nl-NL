---
title: '[!DNL Manage the Data Export extension]'
description: Leer hoe te om de  [!DNL Data Export]  uitbreiding te bevorderen en de diensten van de gegevensuitvoer te verwijderen of onbruikbaar te maken die niet worden vereist.
role: Admin, Developer
exl-id: 94702995-d272-47b9-9560-198eee3250a6
source-git-commit: ff5c717dbdd638e114bccc3f6dec26f4be269194
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# De SaaS-extensie voor gegevensexport beheren

De extensie [!DNL data export] voor SaaS-services is een verzameling modules waarmee gegevens kunnen worden verzameld en gesynchroniseerd tussen Adobe Commerce en verbonden Commerce Services.

Specifieke modules zijn opgenomen in de metapakketten voor dergelijke extensies voor Adobe Commerce Services
als [ Levend Onderzoek ](/help/live-search/overview.md), [ Aanbevelingen van het Product ](/help/product-recommendations/overview.md), en [ de Dienst van de Catalogus ](/help/catalog-service/overview.md). Als u deze diensten gebruikt, wordt geen afzonderlijke installatie vereist om de uitbreiding van de Uitvoer van Gegevens toe te laten.

## Functies voor het exporteren van Commerce-gegevens verwijderen of uitschakelen

Als u niet één van de geïnstalleerde modules van de de uitvoer van handelsgegevens nodig hebt, gebruik het `magento:module:disable` bevel CLI om het onbruikbaar te maken.

Bijvoorbeeld, is er a [ Categorieën API ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) die intern de gegevens van de categorietoestemming gebruikt. Als u deze API niet gebruikt, kunt u de gegevensexport uitschakelen voor de feed voor categorietoestemming.

```shell script
bin/magento module:disable Magento_CategoryPermissionDataExporter Magento_SaaSCategoryPermissions
```

### Een module bijwerken naar een specifieke versie

U kunt om het even welke geïnstalleerde modules van de de uitvoer van handelsgegevens bijwerken door Composer te gebruiken. U kunt bijvoorbeeld een module bijwerken naar een opgegeven versie en ook de vereiste afhankelijkheden bijwerken.

1. Log in bij de Commerce-toepassingsserver.

1. Werk de module bij met behulp van Composer vanaf de opdrachtregel:

   ```bash
   composer require magento/module-saas-price:103.3.1 --with-all-dependencies
   ```

Als de Commerce-instantie wordt geïmplementeerd op de Cloud-infrastructuur, werkt u de extensie bij vanuit de cloud-projectmap. Zie [ Verbetering een uitbreiding ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) in _Adobe Commerce op de Gids van de Infrastructuur van de Wolk_.
