---
title: Facetten
description: '[!DNL Live Search] facetten gebruiken meerdere afmetingen van kenmerkwaarden als zoekcriteria.'
exl-id: d036265e-1868-461d-ab4c-7f469b1c6f5b
source-git-commit: 86484d49aa4b79bfe64455dba18b84bcd9073736
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# Facetten

Faceting is een methode voor het filteren van hoge prestaties waarbij meerdere dimensies van kenmerkwaarden worden gebruikt als zoekcriteria. Het gefactureerde onderzoek is gelijkaardig, maar aanzienlijk &quot;slimmer&quot;dan de standaard [&#x200B; gelaagde navigatie &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html?lang=nl-NL). De lijst van beschikbare filters wordt bepaald door de [&#x200B; filtreerbare attributen &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html?lang=nl-NL#filterable-attributes) van producten die in de onderzoeksresultaten zijn teruggekeerd.

[!DNL Live Search] gebruikt de query `productSearch` , die faceting en andere gegevens retourneert die specifiek zijn voor [!DNL Live Search] . Zie [`productSearch` query &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) in de ontwikkelaarsdocumentatie voor codevoorbeelden.

![&#x200B; Gefilterde onderzoeksresultaten &#x200B;](assets/storefront-search-results-run.png)

Binnen een facet kunnen kopers meerdere opties selecteren, zoals &quot;Standaard&quot; en &quot;Snug&quot; onder &quot;Stijl&quot; en in de zoekresultaten worden alleen die stijlen weergegeven. Op dezelfde manier geldt dat als een winkelier opties selecteert in verschillende facetten, zoals &quot;Standaard&quot; onder &quot;Stijl&quot; en &quot;Binnenshuis&quot; onder &quot;Klimaat&quot;, de zoekresultaten worden bijgewerkt om die geselecteerde stijl en dat geselecteerde klimaat weer te geven.

Elke gedefinieerde facet kan worden gebruikt als een URL-parameter en de resultaten worden gefilterd op basis van de parameterwaarden: `http://yourstore.com?brand=acme&color=red` .

## Faciliteitseisen

De categorie- en productkenmerkvereisten voor facetten zijn vergelijkbaar met de filterbare kenmerken die worden gebruikt voor gelaagde navigatie. Voor elke storefront-eigenschap van een kenmerk moet de waarde &quot;Use in Search Results Layered Navigation&quot; zijn ingesteld op &quot;Yes&quot;. U kunt de kenmerkconfiguratie bekijken en bijwerken via het menu [!DNL Stores] > [!DNL Attribute] in Beheer.

>[!NOTE]
>
>Als u een productcategorie als facet definieert, worden in het facet de `url_path` van de categorie en de subcategorie weergegeven.
>
>![&#x200B; facet van de Categorie &#x200B;](assets/facet-category.png)

Zie [&#x200B; grenzen en grenzen &#x200B;](./boundaries-limits.md#facets) om meer over de facetvereisten in [!DNL Live Search] te leren.

Als u een groot aantal kenmerken hebt om mee te werken, kunt u overwegen kenmerken te combineren tot één &#39;meta-kenmerk&#39;. Schoenen hebben doorgaans bijvoorbeeld een numerieke grootte, terwijl overhemden de gebruikelijke grootte &#39;S/M/L/XL&#39; hebben. Deze twee typen grootten kunnen worden gecombineerd in één doorzoekbaar kenmerk.

| Instelling | Beschrijving |
|--- |--- |
| [&#x200B; de vertoningsmontages van de Categorie &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html?lang=nl-NL) | Anker - `Yes` |
| [&#x200B; eigenschappen van Attributen &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html?lang=nl-NL) | [&#x200B; het type van Invoer van de Catalogus &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html?lang=nl-NL) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` (widget slechts), `Text swatch` (widget slechts) |
| Eigenschappen van kenmerkarchief | Gebruiken in gelaagde navigatie met zoekresultaten - `Yes` |

## Facetaggregatie

Facetsamenvoeging wordt als volgt uitgevoerd: als de winkel drie facetten (categorieën, kleur en prijs) heeft en de winkelfilters op alle drie (kleur = blauw, de prijs is van $10.00-50.00, categorieën = `promotions`).

* `categories` aggregatie - aggregeert `categories` en past vervolgens de filters `color` en `price` toe, maar niet het filter `categories` .
* `color` aggregatie - aggregeert `color` en past vervolgens de filters `price` en `categories` toe, maar niet het filter `color` .
* `price` aggregatie - aggregeert `price` en past vervolgens de filters `color` en `categories` toe, maar niet het filter `price` .
