---
title: Typen factoren
description: '[!DNL Live Search] -facetten zijn dynamisch en verschijnen in de lijst met filters, indien van toepassing.'
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# Typen factoren

[!DNL Live Search] gebruikt een verscheidenheid van facettypes en zij verschijnen in de *lijst van Filters* slechts wanneer relevant. De lijst met beschikbare facetten verandert afhankelijk van de geretourneerde producten. De volgende kenmerken beïnvloeden hun presentatie en gedrag:

* Vastgezette facetten - De meest gebruikte facetten kunnen aan de bovenkant van de lijst worden vastgezet. De resterende facetten worden vermeld in *het type van de Soort* orde na de vastgezette facetten.
* Dynamische facetten - de attributen van het Product die [&#x200B; Adobe Sensei &#x200B;](https://www.adobe.com/sensei.html) het meest relevant voor een productreeks en vraag vindt. De berekening houdt rekening met de attributenmeta-gegevens van de volledige catalogus en bepaalt bij vraagtijd de meest relevante facetten voor de vraag.

  >[!NOTE]
  >
  >Als u merkt dat time-outfouten worden weergegeven in de GraphQL-query nadat u dynamische facetten hebt gemaakt, wijzigt u alle facetten in vastgezet om te zien of dat de prestatieproblemen verhelpt.

* Populaire facetten - Productkenmerken die het vaakst in onderzoeksresultaten aanwezig zijn.
* Prijsfactoren - Retourproducten per prijsklasse. U kunt het aantal selecties en het interval van de prijswaaier op de [*werkruimte van Montages*](settings.md) specificeren.

Bij het opvragen genereert [!DNL Live Search] de zoekresultaten in groepen van dynamische en populaire facetten.

![&#x200B; Facets - Prijs &#x200B;](assets/storefront-search-results-run-price.png)

## Opties voor Storefront en headless

Facetten die voor de [!DNL Commerce] opslag worden teruggegeven worden verwerkt door de onderzoeksadapter, die verzoeken en de resultaten in de opslag teruggeeft. Alle [!DNL Commerce] storefront-facetten worden alfabetisch gesorteerd met opties voor één keuze, ongeacht het invoertype dat aan het overeenkomstige kenmerk is toegewezen. Facetten die beschikbaar zijn in de winkel, worden weergegeven volgens het huidige thema en weerspiegelen eventuele aanpassingen aan de presentatie van gelaagde navigatie.

In tegenstelling, [&#128279;](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) worden de uitvoeringen zonder kop  verwerkt door API en steun extra opties. Koploze facetten kunnen alfabetisch of op aantal worden gesorteerd en kunnen opties voor één of meerdere selecties hebben.

### Facet-labels

Voor [!DNL Commerce] storefronts, wordt het facetetiket bepaald door de [*Eigenschappen van Attributen* &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html?lang=nl-NL). Voor opslag met veelvoudige meningen, kunnen de extra etiketten onder *worden bepaald beheren Etiketten*. Voor hoofdloze implementaties, worden de etiketten uitgegeven van de [&#x200B; facetende werkruimte &#x200B;](faceting-workspace.md).

### Tekst sorteren

Alle facetten die voor de storefront worden weergegeven, worden alfabetisch gesorteerd. Voor implementaties zonder kop kunnen elementen alfabetisch of op aantal worden gesorteerd.

| Tekst sorteren | Beschrijving |
|--- |--- |
| Alfabetisch | In de storefront *lijst van Filters*, worden de facetten alfabetisch gesorteerd. |
| Aantal | (Alleen koptekst) Bij implementaties zonder kop kunnen facetten ook worden gesorteerd op het aantal waarden per facet in de huidige set geretourneerde producten. |
