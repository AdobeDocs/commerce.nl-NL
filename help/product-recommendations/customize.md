---
title: Aanpassen
description: Leer hoe u uw productaanbevelingen kunt aanpassen.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Aanpassen

Wanneer u de module Productaanbevelingen installeert, maakt Adobe Commerce de map `ProductRecommendationsLayout` . Deze map bevat sjabloonbestanden die u kunt aanpassen om de weergave van de aanbevelingen in de winkel te wijzigen. Met name kunt u de volgende sjabloon wijzigen of overschrijven:

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

Voor meer informatie over het wijzigen van malplaatjedossiers, verwijs naar [&#x200B; aanpassing van het Malplaatje &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) in de Voorste Gids van de Ontwikkelaar.

Als u het bestand `recommendations.html` wijzigt, moet u de volgende tags in het bestand behouden om ervoor te zorgen dat Adobe Commerce gegevens over aanbevelingen kan verzamelen van uw winkel:

| Tag | Gebruiken |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | Verzamelt weergavegebeurtenissen. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | Verzamelt klikgebeurtenissen. <br/>**Nota:** als u om het even welke ankermarkeringen toevoegt, moet u deze attributen omvatten. |

Naast het bestand `recommendations.html` bevat de map `ProductRecommendationsLayout` de volgende submappen:

| Map | Doel |
|---|---|
| `layout` | Bevat `*.xml` bestanden voor elk paginatype |
| `templates` | Bevat bestanden die scripts ophalen en renderen |
| `web/js` | Bevat de JavaScript-bestanden die aanbevelingen voor je winkel opvragen en weergeven |
| `web/template` | Bevat de sjabloon voor de module `magento/product-recommendations` |

## Positionering van de aanbevolen eenheid

Wanneer u [&#128279;](create.md) creeert een aanbeveling, specificeert u de [&#x200B; plaats &#x200B;](placement.md) waar het op de pagina verschijnt. Een aanbevolen eenheid kan boven of onder aan de hoofdinhoudscontainer worden geplaatst. U kunt deze plaatsing echter aanpassen. Als u een type van de aanbeveling van de Bouwer van de Pagina adviserende inhoud creeert, gebruik de hulpmiddelen van de Bouwer van de Pagina om de aanbeveling op de pagina te plaatsen. Bewerk voor alle andere paginatypen de `*.xml` -bestanden die worden gegenereerd wanneer de aanbeveling wordt gemaakt.

1. Ga naar de map `layout` :

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   In de volgende tabel worden de XML-bestanden weergegeven die zich in deze map bevinden:

   | Bestandsnaam | Pagina |
   |---|---|
   | `catalog_category_view.xml` | Categorie |
   | `catalog_product_view.xml` | Productdetails |
   | `checkout_cart_index.xml` | Kar |
   | `checkout_onepage_success.xml` | Afhandeling |
   | `cms_index_index.xml` | Home |

   >[!NOTE]
   >
   >De bestandsnamen in de map `layout` kunnen afwijken als uw winkel extensies van derden gebruikt.

1. Wijzig het bestand `catalog_product_view.xml` zodat de aanbevolen eenheid na de productafbeelding op de pagina met productdetails wordt weergegeven. Voordat u dit XML-bestand aanpast, bekijkt u het bestand en begrijpt u welke secties u moet wijzigen:

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   In het bovenstaande fragment geeft het verwijzingsblok `main.content` aan dat de aanbevolen eenheid ergens ten opzichte van dat element wordt geplaatst. Het element `block` ervan bevat het kenmerk `after="-"` , dat aangeeft dat de aanbevolen eenheid op de pagina wordt weergegeven na het blok met de hoofdinhoud.

1. We wijzigen dit bestand door een ander inhoudsblok op te geven.

   Wijzig het verwijzingsblok `name` van `main.content` in `product.info.media` .

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   Deze wijziging leidt ertoe dat uw aanbevolen eenheid wordt weergegeven na de productafbeelding op de pagina met productdetails. Als u de aanbeveling-eenheid vóór `product.info.media` wilt weergeven, wijzigt u het kenmerk `after="-"` in `before="-"` . Het argument `pagePlacement` is een intern argument dat niet mag worden gewijzigd.

Verwijs naar [&#x200B; lay-outoverzicht &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) voor meer informatie over de types van blokken op de pagina.

## Aangepaste productkenmerken

Ontwikkelaars hebben vaak toegang nodig tot aangepaste productkenmerkwaarden in aanbevolen eenheden op winkelcentra, zodat ze visuele behandelingen kunnen toevoegen aan producten die op die kenmerken zijn gebaseerd.

Als uw winkel bijvoorbeeld bepaalde biologische producten verkoopt, hebt u mogelijk een aangepast kenmerk op die producten dat deze aanwijst als `Organic = Yes` . Mogelijk hebt u toegang tot deze kenmerkwaarde op de winkel nodig, zodat u deze producten een speciale visuele behandeling kunt geven wanneer ze in Aanbevelingen worden weergegeven. Op dezelfde manier staat de toegang tot deze waarden van de douaneproductattributen u toe om producten te badge of douanelogica in de presentatielaag van uw plaats te drijven.

![&#x200B; voeg Badge &#x200B;](assets/unit-custom.png) toe

Om ervoor te zorgen is een attribuut van het douaneproduct beschikbaar wanneer u de aanbeveling op de pagina teruggeeft, plaats het `Used in Product Listing` bezit aan `Yes` in de [&#x200B; pagina van de Attributen van het Product &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html?lang=nl-NL) in Admin.

Wanneer deze eigenschap is ingesteld, bevat de JSON-payload een `attributes` -object dat een array van kenmerkcodes en -waarden bevat. Vervolgens kunt u aangepaste opmaakcodes voor winkels toepassen op basis van deze kenmerkwaarden, zoals speciale visuele behandelingen of badges toevoegen zoals eerder vermeld.

>[!NOTE]
>
>Wijzigingen in productkenmerken kunnen maximaal een uur duren voordat ze worden weergegeven in de JSON-payload.
