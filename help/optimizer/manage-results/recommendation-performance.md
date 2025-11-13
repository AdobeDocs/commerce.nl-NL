---
title: Prestaties van aanbevelingen
description: De pagina met aanbevelingen geeft insight inzicht in hoe goed je productaanbevelingen presteren.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: 1b77e2ea-412b-4c78-9d38-390bd8fda87e
source-git-commit: 177ebffe0295fdc87b6f4a60473ebfda6bea0f01
workflow-type: tm+mt
source-wordcount: '647'
ht-degree: 0%

---

# Prestaties van aanbevelingen

De pagina van Prestaties van Aanbevelingen toont een lijst van gevormde aanbevelingen samen met zeer belangrijke metriek om u te helpen hun doeltreffendheid evalueren. U kunt de mening vormen om metriek voor de afgelopen dag, week, of maand te tonen. Deze inzichten tonen hoe vaak elke aanbeveling eenheid wordt bekeken of geklikt, die u helpen prestaties beoordelen en kansen voor optimalisering identificeren.

>[!INFO]
>
>Een aanbevelingseenheid is een widget die de geadviseerde product _punten_ bevat.

![ Prestaties van Aanbevelingen ](../assets/rec-performance.png){zoomable="yes"}

## Een rapport weergeven

1. Kies de **bron van de Catalogus**, zoals `en-US` waar uw aanbevelingen van toepassing zijn.

1. Klik op **[!UICONTROL Date Range]** en selecteer een van de volgende bereiken:

   ![ de Waaier van de Datum van Aanbevelingen ](../assets/rec-perf-date-range.png)

   De lijst van de aanbeveling werkt aan vertoningsmetriek voor dat datumwaaier bij.

## Tabel aanpassen

1. In de upper-left hoek, klik het ![ selecteur van de Kolom ](../assets/icon-show-hide-columns.png) pictogram om de lijst aan te passen.

   De zichtbare kolommen hebben een vinkje.

1. Voer in het menu een van de volgende handelingen uit:

   - Als u een verborgen kolom wilt weergeven, klikt u op een kolomnaam zonder vinkje.
   - Als u een zichtbare kolom wilt verbergen, klikt u op een kolomnaam met een vinkje.

   De tabel wordt vernieuwd en bevat alleen de geselecteerde kolommen.

## Details weergeven

1. In de lijst, klik het (![ Meer selecteur ](../assets/btn-more.png)) pictogram naast de aanbeveling die u wilt onderzoeken.

1. Om het statuut van de aanbeveling te veranderen, activeer **** of **** deactivate.

## Aanbevelingen maken of beheren

Leer hoe u [ een nieuwe kunt tot stand brengen of een bestaande ](../merchandising/recommendations/create.md) aanbeveling beheren.

## Workspace-besturingselementen

| Besturing | Beschrijving |
|---|---|
| ![ de Waaier van de Datum ](../assets/rec-perf-date-range.png) | Hiermee bepaalt u het tijdsbereik dat wordt gebruikt voor metrische berekeningen. |
| ![ de selecteur van de Kolom ](../assets/icon-show-hide-columns.png) | Bepaalt de kolommen die in de lijst van Aanbevelingen verschijnen. |
| Aanbeveling maken | Opent [ creëren Nieuwe pagina van de Aanbeveling ](../merchandising/recommendations/create.md). |

## Kolombeschrijvingen

| Kolom | Beschrijving |
|---|---|
| Naam | De naam van de aanbeveling. |
| Pagina | De pagina waar de aanbeveling wordt weergegeven. |
| Type | Het type aanbeveling. |
| Status | De adviesstatus. Opties: Inactief/actief/concept |
| Gemaakt | De datum waarop de aanbeveling is opgesteld. |
| Laatst bewerkt | De datum waarop de aanbeveling voor het laatst is bewerkt. |
| Impressies | Het aantal keren dat een aanbevolen eenheid op een pagina wordt geladen en weergegeven. Een aanbeveling-eenheid die zich onder de voud van de viewport van de browser bevindt, wordt weergegeven op de pagina, zelfs als de gebruiker deze niet bekijkt. In dit geval wordt de weergegeven eenheid geteld als een indruk, maar een weergave wordt alleen geteld als de gebruiker de eenheid in beeld schuift. |
| vImpressions | (Zichtbare indrukkingen) Het aantal aanbevelingen-eenheden dat ten minste één weergave registreert. Als de aanbevolen eenheid bijvoorbeeld twee regels heeft, elk met twee producten, en de laatste twee producten niet door de verkoopster worden gezien, maar de eerste twee, dan zal de activiteit nog steeds als een indruk worden beschouwd. |
| Weergaven | Het aantal aanbevelingen dat wordt weergegeven in de viewport van de browser van de klant. Als de gebruiker de pagina meerdere keren omhoog of omlaag schuift, wordt de gebeurtenis meerdere keren geactiveerd, telkens wanneer de eenheid zichtbaar is. |
| Klikken | De som van het aantal tijden een verkoopster klikt een punt in de aanbeveling eenheid en het aantal tijden de verkoopster **toevoegt aan wortel** knoop in de aanbeveling eenheid |
| Ontvangsten | De inkomsten die voortvloeien uit de aanbeveling voor de huidige periode. |
| LT-inkomsten | (Levensopbrengsten) De levenslange inkomsten die worden voortgebracht door een aanbeveling. |
| Zichtbaarheid | Het percentage aanbevolen eenheden dat zich registreert voor de weergave. |
| CTR | (Doorkliksnelheid) Het percentage eenheidsindrukkingen voor de aanbeveling die een klik registreert. CTR telt alle indrukken zelfs als de eenheid niet de mening van de verkoopster ingaat. Als de eenheid van de aanbeveling niet wordt bekeken, is het onwaarschijnlijk om te worden geklikt. Deze onzichtbare indrukken tellen echter mee voor de CTR-score en verlagen het totale CTR-percentage. |
| vCTR | (Zichtbare Doorkliksnelheid) maateenheden die alleen op zichtbare indrukken (aanbevelingen die daadwerkelijk in het zichtbare gedeelte van het scherm van de klant zijn weergegeven) zijn gebaseerd, zodat u een nauwkeurigere schatting van de betrokkenheid van de klant krijgt. |
