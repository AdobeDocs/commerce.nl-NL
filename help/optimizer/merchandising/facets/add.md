---
title: Facturen maken en beheren
description: Leer hoe te om facetten in  [!DNL Adobe Commerce Optimizer] toe te voegen en te beheren.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: d6b7ff1f-a9b8-4fb8-8bd3-b3596695045c
source-git-commit: c6725fc524e9d239ccc0f16701e92ad5d2fc7729
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Facturen maken en beheren

Alle filterbare productkenmerken kunnen als facet worden gebruikt. Facetten helpen klanten producten in uw winkel te filteren en gemakkelijker te vinden. Dit artikel verklaart hoe te om, facetten in uw storefront toe te voegen te beheren en te vormen.

![ creeer een Facet ](../../assets/create-facet.png)

## Een facet maken

1. In het linkerspoor, uitgezochte _Merchandising_ > **Facets** dan klik **tot facetten**.
1. In *creeer facetten* lijst, heeft elk beschikbaar attribuut een afzonderlijke ![ toevoegen knoop ](../../assets/btn-add.png). Voer een van de volgende handelingen uit:

   - In de *attributen van Facetten* lijst, kies de productattributen die u als facet wilt gebruiken en **klikken voegt** toe.
   - Om een specifiek productattribuut te vinden, ga de eerste paar karakters van de attributennaam in het *vakje van het Onderzoek* in. Dan, klik **toevoegen**.

   Het facet wordt toegevoegd aan de bodem van de *Dynamische facetten* lijst en *publiceert veranderingen* knoop wordt beschikbaar.

1. Als het facet u wilt toevoegen niet kan worden gevonden, gebruik [ Meta-gegevens API ](https://developer.adobe.com/commerce/services/reference/rest/#tag/Metadata) om de `filterable` parameter te plaatsen:

   `"filterable": true`

   De volgende keer dat de catalogus wordt gesynchroniseerd met [!DNL Adobe Commerce Optimizer], wordt het facet beschikbaar in de winkel. Als de facet niet beschikbaar na twee uren is, zie [ gegevenssynchronisatie ](../../setup/data-sync.md).

## Eigenschappen van facetten bewerken (optioneel)

1. Zoek het facet dat u wilt bewerken.
1. Klik (![ meer selecteur ](../../assets/btn-more.png)) meer selecteur.
1. Voor het menu, geeft de klik **** uit. Pas vervolgens de volgende eigenschappen naar wens aan:

   - Label - Voer het facetlabel in dat u wilt gebruiken.
   - Type sorteren - Kies een van de volgende opties:
      - Alfabetisch - facetten worden alfabetisch gesorteerd
      - Aantal - Sorteert facetten die op het aantal gevonden gelijken worden gebaseerd
   - Max. waarde - Voer het maximale aantal facetwaarden in dat in de winkelruimte wordt weergegeven. Geldige vermeldingen: 0 - 100; Standaard: 8.

1. Wanneer volledig, klik **sparen**.

## Velden vastzetten

Het speld verandert kleur wanneer geklikt en wordt gebruikt om de facet aan of *vastgezette Facets* of de *Dynamische sectie van Facetten* te bewegen.

1. Om een facet aan de bovenkant van de *lijst van Filters* vast te zetten, vind de facet in de *Dynamische lijst van Facetten* en klik het grijze speld (![ Vastzetten selecteur ](../../assets/btn-pin-gray.png)).

   De speld wordt blauw en de facetbewegingen aan de *Vastgezette sectie van Facetten*.

1. Om een facet los te maken, vind het facet in de *Vastgezette lijst van Facetten* en klik het blauwe speld (![ Vastzetten selecteur ](../../assets/btn-pin-blue.png)).

   De speld verandert grijs en de facetbewegingen aan de *Dynamische sectie van Facetten*.

>[!NOTE]
>
>Vastgezette facetvolgorde kan inconsistent zijn als er twee labels met dezelfde naam zijn.

## Elementen verwijderen

1. Vind de facet in de lijst en klik (![ Meer selecteur ](../../assets/btn-more.png)) meer selecteur.
1. Klik **Schrapping**.
1. Wanneer ertoe aangezet om te bevestigen, klik **Facet van de Schrapping**.
Het facet wordt verwijderd uit het winkelcentrum nadat de wijzigingen zijn gepubliceerd.

## Wijzigingen publiceren

1. Klik op **[!UICONTROL Publish]** om de storefront bij te werken met uw wijzigingen.
1. Wacht ongeveer 15 minuten totdat de updates in uw winkel worden weergegeven.

## Aanvullende informatie

- Om prijsfacetintervallen en groeperingen te vormen, zie [ Montages ](../../settings.md).
- Leer meer over de [ types ](type.md) van facetten.
