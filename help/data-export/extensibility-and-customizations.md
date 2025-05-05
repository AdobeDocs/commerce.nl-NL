---
title: SaaS-gegevens voor het exporteren van gegevens uitbreiden en aanpassen
description: Leer hoe te om de  [!DNL SaaS Data Export]  voedergegevens uit te breiden en aan te passen.
role: Admin, Developer
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# SaaS-gegevens voor het exporteren van gegevens uitbreiden en aanpassen

De extensie [!DNL Commerce Data Export] biedt een manier om gegevens uit de [!DNL Commerce] -toepassing te exporteren naar Commerce Services, zoals Live zoeken, Catalog Service en Productaanbevelingen. Indien nodig, kunt u de voedergegevens uitbreiden en aanpassen om extra attributengegevens op te nemen of de verzamelde gegevens te wijzigen.

Na het toevoegen van attributengegevens, is het toegankelijk van het [ attributengebied ](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#productviewattribute-type) in het schema van GraphQL voor storefront de dienst.

>[!NOTE]
>
>Het toevoegen of wijzigen van voedergegevens kan prestaties en verwerkingslogica op de Commerce achterkant beïnvloeden. Test aangepaste code voordat u gaat samenvoegen tot productie. In plaats van gegevens toe te voegen aan de achterkant, gebruikt u API Mesh om het GraphQL-schema van de Catalogusservice uit te breiden. Voor configuratiedetails, zie [ de Dienst van de Catalogus en API Net ](../catalog-service/mesh.md).

## Gegevens van systeemkenmerken uitbreiden in de productfeed

De diervoeders bevatten standaardsysteemkenmerken die vereist zijn voor de verwerking van producten of die algemeen door de consument worden gebruikt. U kunt extra systeemkenmerken in de productfeed opnemen door deze aan de feed toe te voegen.

Om deze taak te voltooien, werk de `magento/catalog-data-exporter` module bij om de extra systeemattributen aan het [ dossier van de de configuratieconfiguratie van de gebiedsdeelinjectie ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) toe te voegen (`di.xml`).

Voeg de attributen aan de vraag van het Attribuut van het Product (`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`) toe.

**Voorbeeld**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```

## Productkenmerken toevoegen aan Adobe Commerce

De ontwikkelaars kunnen productattributen toevoegen die van het [ gebied van productkenmerken ](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#output-fields) toegankelijk zijn door één van de volgende methodes te gebruiken:

- Voeg het kenmerk toe aan Adobe Commerce voor opname in de `products` -voedergegevens die zijn geëxporteerd naar Commerce-winkelservices.
- Voeg het kenmerk dynamisch toe tijdens de feed-synchronisatie met een plug-in.

### Kenmerk toevoegen aan Adobe Commerce

U kunt een productkenmerk toevoegen vanuit Commerce Admin of via een aangepaste PHP-module het kenmerk definiëren en Adobe Commerce bijwerken. Dit is de eenvoudigste methode voor het toevoegen van een productkenmerk, omdat u het kenmerk en alle vereiste metagegevens kunt toevoegen. Het nieuwe attribuut en zijn meta-gegevenseigenschappen worden uitgevoerd naar de diensten SaaS automatisch tijdens de volgende geplande synchronisatie.

#### Het productkenmerk maken via de beheerfunctie

1. In Commerce Admin maakt u het kenmerk op basis van de configuratiepagina voor productkenmerken ([!UICONTROL Stores] > *[!UICONTROL Attributes]* > [!UICONTROL Product] ).

1. Voeg het kenmerk desgewenst toe aan een kenmerkset.

Zie [ productattributen ](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create) in de *Gids van Admin van Adobe Commerce* creëren.

#### Creeer programmatically de productattributen

Voeg via programmacode een productkenmerk toe door een gegevenspatch te maken die `DataPatchInterface` implementeert en instantieer een kopie van de klasse `EavSetup Factory` binnen de constructor om de kenmerkopties te configureren.

Wanneer u de kenmerkopties definieert, zijn alle kenmerkparameters behalve `type` , `label` en `input` optioneel. Definieer de volgende aanvullende opties en eventuele andere opties die afwijken van de standaardinstellingen.

- Zorg ervoor dat de eigenschap wordt geëxporteerd naar storefront-services tijdens gegevenssynchronisatie door `user_defined` = `1` in te stellen
- Stel `used_in_product_listing` = `1` in om ervoor te zorgen dat het kenmerk toegankelijk is binnen de databasequery van de productlijst.

Voor informatie over het creëren van gegevenspatches, zie [ gegevens en schemapatches ontwikkelen ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) in de *Gids van de Ontwikkelaar PHP*.

### Het kenmerk product dynamisch toevoegen

Voor details over het creëren van productkenmerken dynamisch zonder nieuwe Attributen te introduceren Eav, zie [ attributen dynamisch ](add-attribute-dynamically.md) toevoegen.
