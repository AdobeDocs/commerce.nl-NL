---
title: Facturen beheren
description: Leer hoe te om bestaande  [!DNL Live Search]  facetten te beheren.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Facturen beheren

Volg deze instructies om de eigenschappen van bestaande facetten bij te werken of hun presentatie in de winkel te veranderen.

## Prijsfacetgroepen configureren

Verwijs naar [ Montages ](settings.md) om prijsfacetintervallen en groeperingen te vormen.

## facet bewerken

1. Zoek het facet dat u wilt bewerken.
1. Als er vele facetten in de lijst zijn, plaats *Filter door* aan één van het volgende:

   * Vastgezet
   * Dynamisch

   Meer leren, ga naar [ Types van Facet ](facets-type.md).

   ![ de facetten van de Filter ](assets/facets-filter-by-cropped.png)

1. Om de faceteigenschappen uit te geven, klik **Meer** (...) opties.
1. Klik **uitgeven**

   ![ geef opties ](assets/facet-edit-menu.png) uit

1. Voer een van de volgende handelingen uit om het label van het facet te bewerken:

   * Voor a [!DNL Commerce] storefront, geef het [ attributenetiket ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html?lang=nl-NL) uit.
   * Voor een implementatie zonder kop klikt u op de waarde in de eerste kolom en bewerkt u de tekst naar wens.

   ![ geef etiket ](assets/facet-edit-label.png) uit

1. (Alleen Headless) Als u de methode wilt wijzigen die wordt gebruikt om de waarden van facetten te sorteren, klikt u op de waarde in de kolom Type sorteren *en kiest u een van de volgende opties:*

   * Alfabetisch
   * Aantal

   ![ geef telling ](assets/facets-edit-count.png) uit

1. In de **Max kolom van de Waarde**, plaats het maximumaantal (van 0 - 10) van de waarden van de facetfilter in de storefront te tonen.
1. Wanneer volledig, klik **sparen**.

   De wijzigingen worden pas na publicatie in de winkelruimte weergegeven.

## Vastzetten/vastzetten van facet

Het speld verandert kleur wanneer geklikt en wordt gebruikt om de facet aan of *vastgezette Facets* of de *Dynamische sectie van Facetten* te bewegen.

1. Om een facet aan de bovenkant van de *lijst van Filters* vast te zetten, vind de facet in de *Dynamische lijst van Facetten* en klik het grijze speld (![ Vastzetten selecteur ](assets/btn-pin-gray.png)).

   De speld wordt blauw en de facetbewegingen aan de *Vastgezette sectie van Facetten*.

1. Om een facet los te maken, vind het facet in de *Vastgezette lijst van Facetten* en klik het blauwe speld (![ Vastzetten selecteur ](assets/btn-pin-blue.png)).

   De speld verandert grijs en de facetbewegingen aan de *Dynamische sectie van Facetten*.

   ![ Vastgezette en dynamische facetten ](assets/facets-pinned-unpinned.png)

>[!NOTE]
>
>Vastgezette facetvolgorde kan inconsistent zijn als er twee labels met dezelfde naam zijn.

## Vastgezet facet verplaatsen

>[!NOTE]
>
>De volgorde van vastgezette facetten wordt alleen ondersteund in implementaties zonder kop. Gebruik de [!DNL Live Search] PLP-widget als geordende facetten nodig zijn.

U kunt de volgorde van vastgezette facetten wijzigen door de rij naar een andere positie te verplaatsen. De vastgezette facetten hebben a *pictogram van de Beweging ![ (](assets/btn-move.png)) aan het begin van de rij.* In tegenstelling tot vastgezette facetten kunnen dynamische facetten niet worden verplaatst.

1. Vind het facet in de *Vastgezette sectie van Facetten* van de lijst.
1. Gebruik het **pictogram van de Beweging** (![ selecteur van de Beweging ](assets/btn-move.png)) om de rij aan een nieuwe positie in de *Vastgezette sectie van Facetten* te slepen.

   Nadat de veranderingen worden gepubliceerd, verschijnen de opnieuw in orde gebrachte facetten in de opslag *lijst van Filters*.

## Facet verwijderen

1. Vind het facet in de lijst en klik **Meer** (...) opties.
1. Klik **Schrapping**.
1. Wanneer ertoe aangezet om te bevestigen, klik **Facet van de Schrapping**.
Het facet wordt verwijderd uit het winkelcentrum nadat de wijzigingen zijn gepubliceerd.

## Wijzigingen publiceren

1. Om de storefront met uw veranderingen bij te werken, klik **publiceer veranderingen**.
1. Wacht ongeveer 15 minuten totdat de updates in uw winkel worden weergegeven.
