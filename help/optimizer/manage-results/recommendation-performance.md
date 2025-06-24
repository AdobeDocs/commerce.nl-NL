---
title: Prestaties van aanbevelingen
description: De pagina met aanbevelingen geeft insight inzicht in hoe goed je productaanbevelingen presteren.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: f49a86b8793e2d91413acfbc0b922cb94db67362
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---

# Prestaties van aanbevelingen

De pagina van Prestaties van Aanbevelingen toont een lijst van gevormde aanbevelingen samen met zeer belangrijke metriek om u te helpen hun doeltreffendheid evalueren. U kunt de mening vormen om metriek voor de afgelopen dag, week, of maand te tonen. Deze inzichten tonen hoe vaak elke aanbeveling eenheid wordt bekeken of geklikt, die u helpen prestaties beoordelen en kansen voor optimalisering identificeren.

>[!INFO]
>
>Een aanbevelingseenheid is een widget die de geadviseerde product _punten_ bevat.

![ Prestaties van Aanbevelingen ](../assets/rec-performance.png){zoomable="yes"}

## Kies de **mening van de Catalogus**

Selecteer de [ catalogusmening ](../setup/catalog-view.md) waar uw aanbevelingen van toepassing zijn.

![ de Mening van de Catalogus ](../assets/catalog-view.png)

## Een rapport weergeven

Klik op de kalender en voer een van de volgende handelingen uit:

- Als u één datum wilt opgeven, dubbelklikt u op de datum in de kalender.
- Als u een datumbereik wilt opgeven, klikt u op de eerste en laatste datum in de kalender.

>[!NOTE]
>
>Het datumbereik mag niet langer zijn dan één jaar.

## Tabel aanpassen

1. In de upper-left hoek, klik het ![ selecteur van de Kolom ](../assets/icon-show-hide-columns.png) pictogram om de lijst aan te passen.

   De zichtbare kolommen hebben een vinkje.

1. Voer in het menu een van de volgende handelingen uit:

   - Als u een verborgen kolom wilt weergeven, klikt u op een kolomnaam zonder vinkje.
   - Als u een zichtbare kolom wilt verbergen, klikt u op een kolomnaam met een vinkje.

   De tabel wordt vernieuwd en bevat alleen de geselecteerde kolommen.

## Filters instellen

Klik op het filterpictogram om de meetgegevens in de werkruimte met aanbevolen prestaties te filteren.

![ Metriek van de Filter ](../assets/rec-filters.png)

U kunt meerdere waarden configureren voor elk van de filters. Zie de [ lijst hieronder ](#column-descriptions) voor beschrijvingen van elke filter.

## Details weergeven

1. In de lijst, klik het (![ Meer selecteur ](../assets/btn-more.png)) pictogram naast de aanbeveling die u wilt onderzoeken.

1. Om het statuut van de aanbeveling te veranderen, activeer **&#x200B;**&#x200B;of **&#x200B;**&#x200B;deactivate.

## Aanbevelingen maken of beheren

Leer hoe u [ een nieuwe kunt tot stand brengen of een bestaande ](../merchandising/recommendations/create.md) aanbeveling beheren.

## Workspace-besturingselementen

| Besturing | Beschrijving |
|---|---|
| ![ de selecteur van de Kalender ](../assets/icon-calendar.png) | Hiermee bepaalt u het tijdsbereik dat wordt gebruikt voor metrische berekeningen. |
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
