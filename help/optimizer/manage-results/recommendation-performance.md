---
title: Prestaties van aanbevelingen
description: De pagina met aanbevelingen geeft insight inzicht in hoe goed je productaanbevelingen presteren.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is op Adobe Commerce as a Cloud Service en  [!DNL Adobe Commerce Optimizer]  slechts projecten (Adobe-Beheerde infrastructuur SaaS) van toepassing."
exl-id: 1b77e2ea-412b-4c78-9d38-390bd8fda87e
source-git-commit: 9cb231055df45bbfcff3303c6e1c257c883cb852
workflow-type: tm+mt
source-wordcount: '953'
ht-degree: 0%

---

# Prestaties van aanbevelingen

De pagina van Prestaties van Aanbevelingen toont een lijst van gevormde aanbevelingen samen met zeer belangrijke metriek om u te helpen hun doeltreffendheid evalueren. U kunt de mening vormen om metriek voor de afgelopen dag, week, of maand te tonen. Deze inzichten tonen hoe vaak elke aanbeveling eenheid wordt bekeken of geklikt, die u helpen prestaties beoordelen en kansen voor optimalisering identificeren.

>[!INFO]
>
>Een aanbevelingseenheid is een widget die de geadviseerde product _punten_ bevat.

![ Prestaties van Aanbevelingen ](../assets/rec-performance.png){zoomable="yes"}

## Een rapport weergeven

1. Kies de **mening van de Catalogus**, zoals *Alle meningen* waar uw aanbevelingen van toepassing zijn.

   Leer meer over [ catalogusmeningen ](#select-catalog-view) in aanbevelingen.

1. Klik op **[!UICONTROL Date Range]** en selecteer een van de volgende bereiken:

   ![ de Waaier van de Datum van Aanbevelingen ](../assets/rec-perf-date-range.png)

   De lijst van de aanbeveling werkt aan vertoningsmetriek voor dat datumwaaier en catalogusmening bij.

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
| [ mening van de Catalogus ](#select-catalog-view) | Selecteer de catalogusweergave om de tabel te filteren en alleen die aanbevelingen weer te geven die van toepassing zijn op de geselecteerde catalogusweergave. Deze selectie wordt ook gebruikt als catalogusmening wanneer u [ ](../merchandising/recommendations/create.md) tot een nieuwe aanbeveling leidt. De opties zijn *Alle meningen* of een specifieke [ catalogusmening ](../setup/catalog-view.md). |

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

## Catalogusweergave selecteren

>[!IMPORTANT]
>
>Deze functie is momenteel in bèta.

De **[!UICONTROL Catalog view]** selecteur op de **2} pagina van Aanbevelingen {doet twee dingen:**

1. **Filters de lijst** - toont slechts aanbevelingen (en hun metriek) die op de geselecteerde catalogusmening van toepassing zijn.
1. **plaatst het werkingsgebied voor nieuwe aanbevelingen** - wanneer u [ ](../merchandising/recommendations/create.md) een aanbeveling creeert, wordt de geselecteerde catalogusmening gebruikt als werkingsgebied van de eenheid. De opties zijn *Alle meningen* of een specifieke [ catalogusmening ](../setup/catalog-view.md).

   - **Alle meningen** - de aanbeveling is op alle catalogusmeningen van toepassing (productbeschikbaarheid wordt nog gefiltreerd per mening).
   - **de mening van de Catalogus** - de aanbeveling is slechts op de geselecteerde catalogusmening (bijvoorbeeld, één opslag, taal, of merk) van toepassing.

Door een catalogusweergave voor elke aanbeveling op te geven, kunt u:

- Configureer aanbevelingen voor alle (algemene) catalogusweergaven of voor één catalogusweergave.
- De voorproef en filterproducten door catalogusmening op [ creëren ](../merchandising/recommendations/create.md) aanbevelingen pagina.
- Alleen producten weergeven die beschikbaar zijn voor elke winkel.
- Metrische gegevens en storefront gedrag per catalogusweergave weergeven.

### Hoe de catalogusweergave producten filtert

De beschikbaarheid van het product wordt afgedwongen per catalogusmening zelfs voor aanbeveling eenheden onder **Alle meningen** selectie. Dit werkt naast om het even welke [ opneming of uitsluitingsfilters ](../merchandising/recommendations/filters.md) u op de aanbevelingseenheid plaatst.

**Voorbeeld: Aanbeveling met inclusiefilters onder Alle meningsselectie**

- **Alle meningen** aanbeveling omvat SKUs: SKU_ABC, SKU_CDE, SKU_XYZ.
- **Catalogusmening: Kingsbluff** kan SKU_ABC of SKU_CDE niet verkopen. **getoond:** SKU_XYZ plus andere SKUs geldig voor Kingsbluff.
- **de mening van de Catalogus: Arkbridge** kan geen van inbegrepen SKUs verkopen. **getoond:** slechts SKUs die door Arkbridge wordt toegelaten. Als er geen gegevens beschikbaar zijn, wordt de aanbevolen eenheid niet weergegeven op die winkel.
