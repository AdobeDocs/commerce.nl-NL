---
title: Productkenmerken dynamisch toevoegen
description: Leer hoe u tijdens het synchronisatieproces van gegevens dynamisch aangepaste productkenmerken kunt toevoegen aan de functie voor het exporteren van gegevens.
role: Admin, Developer
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Productkenmerken dynamisch toevoegen tijdens gegevenssynchronisatie

U kunt productkenmerken uitbreiden zonder ze in Adobe Commerce te registreren door een plug-in te maken om de kenmerken toe te voegen tijdens het proces voor gegevenssynchronisatie.

>[!NOTE]
>
>De beste manier om productkenmerken uit te breiden is hen [ toe te voegen aan Adobe Commerce ](extensibility-and-customizations.md#add-product-attributes-to-adobe-commerce) waar u hen van Commerce kunt vormen en beheren Admin. Voeg deze alleen dynamisch toe als u ze alleen voor Commerce-winkelservices nodig hebt en niet in Adobe Commerce wilt registreren. U hebt ook de optie om douanekenmerken te beheren gebruikend [ API Net met de Dienst van de Catalogus ](../catalog-service/mesh.md) om het schema van GraphQL van de Dienst van de Catalogus uit te breiden.

## Productkenmerken toevoegen

Maak een plug-in die een `customer_attribute` aan de klasse `Magento\CatalogDataExporter\Model\Provider\Product\Attributes` toevoegt.

1. Werk het [ dossier van de de injectieconfiguratie van de gebiedsdeel ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`) bij om de stop te bepalen.

   ```xml
   <type name="Magento\CatalogDataExporter\Model\Provider\Product\Attributes">
     <plugin name="product_customer_attributes" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttribute"/>
   </type>
   ```

1. Maak de insteekmodule.

   ```php
    <?php
    declare(strict_types=1);
   
    namespace Vendor\CatalogDataExporter\Model\Plugin;
   
    use Magento\CatalogDataExporter\Model\Provider\Product\Attributes;
   
    class AddAttribute {
   
         /**
          * @param Attributes $subject
          * @param array $result
          * @param $arguments
          * @return array
          * @throws \Zend_Db_Statement_Exception
          */
         public function afterGet(Attributes $subject, array $result, $arguments): array
         {
              $productIds = \array_column($arguments, 'productId');
   
              foreach ($productIds as $productId) {
                    $result[] = [
                         'productId' => $productId,
                         // "storeViewCode" must be specified for products where the customer attribute value should be set
                         'storeViewCode' => 'default',
                         'attributes' => [
                              // specify the customer attribute code
                              'attributeCode' => 'customer_attribute',
                              // provide single or multiple values for the attribute
                              'value' => [
                                    rand(41,43)
                              ]
                         ]
                    ];
              }
   
              return $result;
         }
    }
   ```

   Nadat u de plug-in hebt toegevoegd, worden de wijzigingen tijdens de volgende geplande synchronisatie gesynchroniseerd met de verbonden winkelservices. Om de updates onmiddellijk te verzenden, gebruik het volgende CLI bevel om het synchronisatieproces manueel te beginnen.

   ```
   bin/magento saas:resync --feed=products
   ```

## Metagegevens van aangepaste productkenmerken declareren

Als u dynamisch een attribuut van het douaneproduct creeert en het voor vertoning, onderzoek, of het filtreren in de diensten van de opslagront wilt gebruiken, voeg de meta-gegevens van de productattributen toe om het storefront gedrag te vormen.

1. Werk het [ dossier van de de configuratieconfiguratie van de gebiedsdeelinjectie ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`) bij om de stop voor de meta-gegevens van het productattribuut te bepalen.

   ```xml
   <type name="\Magento\CatalogDataExporter\Model\Provider\ProductMetadata">
     <plugin name="product_customer_attributes_metadata" type="Vendor\CatalogDataExporter\Model\Plugin\AddAttributeMetadata"/>
   </type>
   ```

1. Maak de plug-in bij de volgende provider `\Magento\CatalogDataExporter\Model\Provider\ProductMetadata` .

   Schakel `ProductAttributeMetadata` in `vendor/magento/module-catalog-data-exporter/etc/et_schema.xml` voor vereiste velden.

   ```php
    <?php
    declare(strict_types=1);
   
    namespace Vendor\CatalogDataExporter\Model\Plugin;
   
    use Magento\CatalogDataExporter\Model\Provider\ProductMetadata;
   
    class AddAttributeMetadata {
   
         /**
          * @param ProductMetadata $subject
          * @param array $result
          * @param $arguments
          * @return array
          * @throws \Zend_Db_Statement_Exception
          */
         public function afterGet(ProductMetadata $subject, array $result, $arguments): array
         {
              $result[] = [
                'id' => '123',
                'storeCode' => 'default',
                'websiteCode' => 'base',
                'storeViewCode' => 'default',
                // specify the customer attribute code - should be the same as used in the products attributes plugin
                'attributeCode' => 'customer_attribute',
                // only product attributes are supported
                'attributeType' => 'catalog_product',
                // specify the data type
                'dataType' => 'int',
                'multi' => false,
                'label' => 'Customer Attribute',
                'frontendInput' => 'select',
                'required' => false,
                'unique' => false,
                'global' => true,
                'visible' => true,
                'searchable' => true,
                'filterable' => true,
                // This value must be set to true to export it to the storefront services
                'visibleInCompareList' => true,
                'visibleInListing' => true,
                'sortable' => true,
                'visibleInSearch' => true,
                'filterableInSearch' => true,
                'searchWeight' => 1.0,
                'usedForRules' => true,
                'boolean' => false,
                'systemAttribute' => false,
                'numeric' => false,
                // specify the list of attribute options
                'attributeOptions' => [
                    'option1',
                    'option2',
                    'option3'
                ]
             ];
   
              return $result;
         }
      }
   ```

   Nadat u de plug-in hebt toegevoegd, worden de wijzigingen tijdens de volgende geplande synchronisatie gesynchroniseerd met de verbonden winkelservices. Om de updates onmiddellijk te verzenden, gebruik het volgende CLI bevel om het synchronisatieproces manueel te beginnen.

   ```
   bin/magento saas:resync --feed=productattributes
   ```
