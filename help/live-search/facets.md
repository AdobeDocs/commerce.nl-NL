---
title: Facetten
description: '[!DNL Live Search] facetten gebruiken meerdere afmetingen van kenmerkwaarden als zoekcriteria.'
exl-id: d036265e-1868-461d-ab4c-7f469b1c6f5b
source-git-commit: ff5c717dbdd638e114bccc3f6dec26f4be269194
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 0%

---

# Facetten

Faceting is een methode voor het filteren van hoge prestaties waarbij meerdere dimensies van kenmerkwaarden worden gebruikt als zoekcriteria. Het gefactureerde onderzoek is gelijkaardig, maar aanzienlijk &quot;slimmer&quot;dan de standaard [ gelaagde navigatie ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). De lijst van beschikbare filters wordt bepaald door de [ filtreerbare attributen ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) van producten die in de onderzoeksresultaten zijn teruggekeerd.

[!DNL Live Search] gebruikt de query `productSearch` , die faceting en andere gegevens retourneert die specifiek zijn voor [!DNL Live Search] . Zie [`productSearch` query ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) in de ontwikkelaarsdocumentatie voor codevoorbeelden.

![ Gefilterde onderzoeksresultaten ](assets/storefront-search-results-run.png)

Binnen een facet kunnen kopers meerdere opties selecteren, zoals &quot;Standaard&quot; en &quot;Snug&quot; onder &quot;Stijl&quot; en in de zoekresultaten worden alleen die stijlen weergegeven. Op dezelfde manier geldt dat als een winkelier opties selecteert in verschillende facetten, zoals &quot;Standaard&quot; onder &quot;Stijl&quot; en &quot;Binnenshuis&quot; onder &quot;Klimaat&quot;, de zoekresultaten worden bijgewerkt om die geselecteerde stijl en dat geselecteerde klimaat weer te geven.

Elke gedefinieerde facet kan worden gebruikt als een URL-parameter en de resultaten worden gefilterd op basis van de parameterwaarden: `http://yourstore.com?brand=acme&color=red` .

## Faciliteitseisen

De categorie- en productkenmerkvereisten voor facetten zijn vergelijkbaar met de filterbare kenmerken die worden gebruikt voor gelaagde navigatie. Voor elke storefront-eigenschap van een kenmerk moet de waarde &quot;Use in Search Results Layered Navigation&quot; zijn ingesteld op &quot;Yes&quot;.

[!DNL Live Search] ondersteunt maximaal:

* 100 kenmerken geconfigureerd als facetten
* 50 sorteerbare kenmerken
* 200 filterbare kenmerken
* 200 doorzoekbare kenmerken

>[!NOTE]
>
> Als er meer dan 200 filterbare bepaalde eigenschappen zijn, is het niet deterministisch welke 200 eigenlijk zal worden geïndexeerd.

Als u een groot aantal kenmerken hebt om mee te werken, kunt u overwegen kenmerken te combineren tot één &#39;meta-kenmerk&#39;. Schoenen hebben doorgaans bijvoorbeeld een numerieke grootte, terwijl overhemden de gebruikelijke grootte &#39;S/M/L/XL&#39; hebben. Deze twee typen grootten kunnen worden gecombineerd in één doorzoekbaar kenmerk.

| Instelling | Beschrijving |
|--- |--- |
| [ de vertoningsmontages van de Categorie ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | Anker - `Yes` |
| [ eigenschappen van Attributen ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [ het type van Invoer van de Catalogus ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` (widget slechts), `Text swatch` (widget slechts) |
| Eigenschappen van kenmerkarchief | Gebruiken in gelaagde navigatie met zoekresultaten - `Yes` |

## Facetaggregatie

Facetsamenvoeging wordt als volgt uitgevoerd: als de winkel drie facetten (categorieën, kleur en prijs) heeft en de winkelfilters op alle drie (kleur = blauw, de prijs is van $10.00-50.00, categorieën = `promotions`).

* `categories` aggregatie - aggregeert `categories` en past vervolgens de filters `color` en `price` toe, maar niet het filter `categories` .
* `color` aggregatie - aggregeert `color` en past vervolgens de filters `price` en `categories` toe, maar niet het filter `color` .
* `price` aggregatie - aggregeert `price` en past vervolgens de filters `color` en `categories` toe, maar niet het filter `price` .

## Standaardkenmerkwaarden

De volgende productkenmerken hebben [ storefront eigenschappen ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) die door [!DNL Live Search] worden gebruikt en door gebrek worden toegelaten.

| Eigenschap | Storefront, eigenschap | Kenmerk |
|---|---|---|
| Sorteerbaar | Wordt gebruikt voor sorteren in de productlijst | `price` |
| Doorzoekbaar | Gebruiken in Zoeken | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Gebruik in gelaagde navigatie - Filterbaar (met resultaten) | `price`<br />`visibility`<br />`category_name` |

## Standaardeigenschappen van niet-systeemkenmerken

In de volgende tabel worden de standaardzoekeigenschappen en filterbare eigenschappen van niet-systeemkenmerken weergegeven, inclusief de eigenschappen die specifiek zijn voor de Luminantiemonsteringsgegevens. Het plaatsen van het *Gebruik in het 1&rbrace; attributenbezit van het Onderzoek &lbrace;aan `Yes` maakt de attributen doorzoekbaar in zowel [!DNL Live Search] als inheemse Adobe Commerce.*

| Kenmerkcode | Doorzoekbaar | Gebruiken in gelaagde navigatie |
|--- |--- |--- |
| activiteit | Ja | Filterbaar (met resultaten) |
| attributes_brand | Ja | Nee |
| merk | Ja | Nee |
| klimaat | Ja | Filterbaar (met resultaten) |
| halsband | Ja | Filterbaar (met resultaten) |
| kleur | Ja | Filterbaar (met resultaten) |
| kosten | Ja | Nee |
| eco_collection | Ja | Filterbaar (met resultaten) |
| sekse | Ja | Filterbaar (met resultaten) |
| fabrikant | Ja | Filterbaar (met resultaten) |
| materiaal | Ja | Filterbaar (met resultaten) |
| doel | Ja | Filterbaar (met resultaten) |
| riem_tassen | Ja | Filterbaar (met resultaten) |
| style_general | Ja | Filterbaar (met resultaten) |

## Standaardsysteemkenmerkeigenschappen

In de volgende tabel worden de standaardzoekeigenschappen en filterbare eigenschappen van systeemkenmerken weergegeven.

| Kenmerkcode | Doorzoekbaar | Gebruiken in gelaagde navigatie |
|--- |--- |--- |
| allow_open_amount | Ja | Filterbaar (met resultaten) |
| beschrijving | Ja | Nee |
| name | Ja | Nee |
| prijs | Ja | Filterbaar (met resultaten) |
| short_description | Ja | Nee |
| sku | Ja | Nee |
| status | Ja | Nee |
| tax_class_id | Ja | Nee |
| url_key | Ja | Nee |
| gewicht | Ja | Nee |
