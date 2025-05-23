---
title: Facetten toevoegen
description: Leer hoe te om filterbare productattributen als  [!DNL Live Search]  facetten toe te voegen.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Facetten toevoegen

Alle filterbare productkenmerken kunnen als facet worden gebruikt. Het *voegt facetten* paneel van lijsten de huidige facetten toe en maakt het gemakkelijk om extra productattributen als facetten toe te wijzen. Tijdens dit proces in drie stappen wordt een kenmerk gekozen om als facet te worden gebruikt, worden eigenschappen indien nodig bewerkt en worden de wijzigingen in het winkelcentrum gepubliceerd.

![ voegt Facetten ](assets/facets-add.png) toe

## Stap 1: Een facet toevoegen

1. In Admin, ga naar **Marketing** > SEO &amp; Onderzoek > **[!DNL Live Search]**.
1. Op het *Facetende* lusje, klik **voegt facetten** toe.
1. In *voeg facetten* lijst toe, heeft elk beschikbaar attribuut een afzonderlijke ![ knoop ](assets/btn-add.png) toevoegen. Voer een van de volgende handelingen uit:

   * In de *Facetterende attributen* lijst, kies de productattributen die u als facet wilt gebruiken en **klikken** toevoegt.
   * Om een specifiek productattribuut te vinden, ga de eerste paar karakters van de attributennaam in het *vakje van het Onderzoek* in. Dan, klik **toevoegen**.

     Om prijsfacetintervallen en groeperingen te vormen, verwijs naar [ Montages ](settings.md). Meer leren, ga naar [ Types van Facet ](facets-type.md).
Het facet wordt toegevoegd aan de bodem van de *Dynamische lijst van Facetten* en *publiceert veranderingen* wordt knoop beschikbaar.

1. Als het facet u wilt toevoegen niet kan worden gevonden, ga **> Attributen >** Product **en verifieer dat het attribuut de [ vereiste eigenschappen ](facets.md) heeft om als facet worden gebruikt.** Werk indien nodig de volgende archiefront-eigenschappen van het kenmerk bij:

   * Gebruiken in zoekopdracht - `Yes`
   * Gebruiken in gelaagde navigatie met zoekresultaten - `Yes`
   * Gebruiken in gelaagde navigatie - `Filterable (with results)`

1. Vernieuw de cache wanneer daarom wordt gevraagd.

   De volgende keer dat de catalogus wordt gesynchroniseerd met [!DNL Live Search], wordt het facet beschikbaar in de winkel. Als de facet niet beschikbaar na twee uren is, zie [ catalogusgegevens ](install.md#synchronize-catalog-data) synchroniseren.

## Stap 2: Eigenschappen van facetten bewerken (optioneel)

1. Om de faceteigenschappen uit te geven, klik **Meer** (![ Meer selecteur ](assets/btn-more.png)) opties in de uiterst juiste kolom.
1. Voor het menu, geeft de klik **&#x200B;**&#x200B;uit. Pas vervolgens de volgende eigenschappen naar wens aan.

   * Etiket - ([ Koploze ](facets-type.md) slechts) ga het facetetiket in dat u wilt gebruiken.
   * Sorteertype - Facetten worden alfabetisch gesorteerd voor alle [!DNL Commerce] storefronts. Voor implementaties zonder kop kunnen facetten alfabetisch of op aantal worden gesorteerd. Opties: Alfabetisch, Aantal (alleen zonder kop)
   * Max. waarde - Voer het maximale aantal facetwaarden in dat in de winkelruimte wordt weergegeven. Geldige vermeldingen: 0 - 100; Standaard: 8

1. Wanneer volledig, klik **sparen**.

   ![ geeft Facetten ](assets/facet-edit.png) uit

1. Om de facet aan de bovenkant van de *lijst van Filters* vast te zetten, klik de grijze duw (![ Vastzetten selecteur ](assets/btn-pin-gray.png)).
1. Om de orde van het vastgezette facet te veranderen, klik de **Beweging** (![ de selecteur van de Beweging ](assets/btn-move.png)) pictogram en sleep de rij aan een nieuwe positie in de *Vastgezette sectie van Facetten*.

## Stap 3: Wijzigingen publiceren

1. Wanneer de facet volledig is, klik **publiceer veranderingen**.
1. Wacht tot het facet in de winkel wordt weergegeven.
Als de facet niet beschikbaar na twee uren is, zie [ de uitvoer ](install.md#synchronize-catalog-data) in de installatieinstructies verifiëren.

## Veldomschrijvingen

| Veld | Beschrijving |
|--- |--- |
| Label | ([ Koploze ](facets-type.md) slechts) het [ facetetiket ](facets-type.md) dat in de storefront zichtbaar is kan voor consistentie met uw merk worden uitgegeven. |
| Sorteertype | De methode die aan [ wordt gebruikt soort ](facets-type.md) facetten. Alle [!DNL Commerce] storefronts sorteren alleen alfabetische facetten. Implementaties zonder kop kunnen ook worden gesorteerd op `Count` . Opties:<br /> alfabetisch - sorteert facetten alfabetisch.<br /> Telling - (Hoofdloos slechts) sorteert facetten die op het aantal gevonden gelijken worden gebaseerd. |
| Max. waarde | Het maximumaantal waarden dat in de opslagruimte voor elk facet kan worden getoond. Facetten die een reeks waarden vertegenwoordigen, worden gelijkmatig verdeeld. Geldige vermeldingen: 0 - 100; Standaard: 8 |

### Besturingselementen

| Besturing | Beschrijving |
|--- |--- |
| ![ Vastzetten selecteur ](assets/btn-pin-blue.png) | Punten of unpins een facet aan de bovenkant van de *lijst van Filters*. |
| ![ Meer selecteur ](assets/btn-more.png) | Hiermee geeft u een menu weer met meer acties die op het geselecteerde facet kunnen worden toegepast. Opties: bewerken, verwijderen |
| ![ de selecteur van de Beweging ](assets/btn-move.png) | Gebruik het *pictogram van de Beweging* om een vastgezette facet aan een andere plaats in de *Vastgezette facetten* sectie te slepen. |
