---
title: Merchandising Rules Workspace
description: Leer je weg rond de werkruimte Regels voor het veranderen van objecten.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is op Adobe Commerce as a Cloud Service en  [!DNL Adobe Commerce Optimizer]  slechts projecten (Adobe-Beheerde infrastructuur SaaS) van toepassing."
exl-id: 3deac529-731d-44b9-87f3-3c9cb36e28e7
source-git-commit: 9cb231055df45bbfcff3303c6e1c257c883cb852
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 0%

---

# Merchandising Rules Workspace

De *Merchandising Regels* werkruimte maakt een lijst van de huidige selectie van regels en hun status, en verleent toegang tot hulpmiddelen u regels moet creëren en beheren. U kunt werkingsgebiedregels aan alle [ catalogusmeningen ](../../setup/catalog-view.md) (globaal) of aan één enkele catalogusmening. Zie [ Uitgezochte catalogusmening ](#select-catalog-view) voor hoe te door catalogusmening filtreren en regels per catalogusmening creëren. Vanuit de werkruimte kunt u:

- Zoeken naar regels
- Regeldetails weergeven
- Regels activeren/deactiveren
- Regels verwijderen
- Toegang tot de regeleditor

![ Merchandising Rules Workspace ](../../assets/rules-workspace.png)

## Kolommen tonen/verbergen

1. In de hoger-juiste hoek, klik **tonen/verbergen** ![ selecteur van de Kolom ](../../assets/btn-show-hide-columns.png) kolommen.

1. Voer in het menu een van de volgende handelingen uit:

   - Als u een verborgen kolom wilt weergeven, klikt u op een kolomnaam zonder vinkje.
   - Als u een zichtbare kolom wilt verbergen, klikt u op een kolomnaam met een vinkje.

## Regels filteren op status

1. Als uw winkel veel regels heeft, kunt u de regels filteren op status om de lijst te verkorten. Standaard worden in de lijst Regels alle regels weergegeven.

1. Om van slechts regels met een specifieke status het plaatsen, plaats **Status** aan één van het volgende:

   - Alles
   - Actief
   - Inactief
   - Gepland
   - Concept

   U kunt ook filtreren door **Voorwaarden**, **datum van het Begin**, **einddatum**, en **laatst bijgewerkt**.

## Details weergeven

In het deelvenster Details worden de naam, de status, de voorwaarden en gebeurtenissen van de regel, de begin- en einddatum, de beschrijving en de datum die het laatst is bewerkt weergegeven. Regels kunnen worden ingeschakeld, bewerkt en verwijderd in het deelvenster Details.

1. Op de *Merchandising regels* werkruimte, vind de regel in het net dat u wilt bekijken en klikken (![ Meer selecteur ](../../assets/btn-more.png)) pictogram.

   U kunt een van de volgende handelingen uitvoeren in het menu:

   - Regel bewerken
   - Regel verwijderen
   - Regel in-/uitschakelen

## Kolombeschrijvingen

| Kolom | Beschrijving |
|--- |--- |
| Naam | De naam van de regel. |
| Laatst bijgewerkt | De datum waarop de regel voor het laatst is bijgewerkt. |
| Begindatum | De begindatum van een geplande regel. |
| Einddatum | De einddatum van een geplande regel. |
| Status | De status met kleurcodes geeft de huidige status van de regel aan. Gebruik het besturingselement Status boven het raster om regels op status te filteren. Waarden:<br /> Al status - Toont alle regels ongeacht status.<br /> Actief (blauw) - toont slechts actieve regels.<br /> Gepland (Oranje) - toont slechts geplande regels.<br /> Inactief (grijs) - toont slechts inactieve regels. |

## Besturingselementen

| Besturing | Beschrijving |
|--- |--- |
| Regel toevoegen | Opent de [ regelredacteur ](add.md). |
| Catalogusweergave | Hiermee filtert u de tabel op regels die van toepassing zijn op de geselecteerde catalogusweergave. Stelt ook het werkingsgebied in wanneer u [ een regel ](add.md) creeert. Opties: *Alle meningen* of een specifieke [ catalogusmening ](../../setup/catalog-view.md). Zie [ Uitgezochte catalogusmening ](#select-catalog-view). |
| Status | Hiermee filtert u de lijst met regels op status. Opties: Alle, Actief, Inactief, Gepland |
| ![ de selecteur van de Kolom ](../../assets/btn-show-hide-columns.png) | Hiermee geeft u de kolommen op die zichtbaar zijn in het raster. Opties: Laatst bijgewerkt, Begindatum, Einddatum, Status |
| Zoeken | Zoekt naar een regel op volledige naam of gedeeltelijke gelijke. |
| ![ Meer selecteur ](../../assets/btn-more.png) | Toont een menu van meer acties die op de geselecteerde regel kunnen worden toegepast. Opties: bewerken, details weergeven, verwijderen |

## Regeldetails

| Veld | Beschrijving |
|--- |--- |
| Status | De huidige status van de regel. |
| Voorwaarden | De onderzoeksvraag die de voorwaarden verbonden aan de regel beschrijft. |
| Begindatum | De datum waarop de regel van kracht wordt, indien gepland. |
| Einddatum | De datum de regel verloopt, indien gepland. |
| Beschrijving | Een korte beschrijving van de regel. |
| Laatst bijgewerkt | De datum en de tijd de regel het laatst werd bijgewerkt. |
| Ingeschakeld | Een besturingselement dat de status van de regel wijzigt. Opties: Ingeschakeld/Uitgeschakeld |

## Catalogusweergave selecteren

>[!IMPORTANT]
>
>Deze functie is momenteel in bèta.

De kiezer **[!UICONTROL Catalog view]** op de pagina Regels voor handelswijziging doet twee dingen:

1. **Filters de lijst** - toont slechts regels (en hun details) die op de geselecteerde catalogusmening van toepassing zijn.
1. **plaatst het werkingsgebied voor nieuwe regels** - wanneer u [ een regel ](add.md) creeert, wordt de geselecteerde catalogusmening gebruikt als werkingsgebied van de regel. De opties zijn *Alle meningen* of een specifieke [ catalogusmening ](../../setup/catalog-view.md).

   - **Alle meningen** - de regel is op alle catalogusmeningen van toepassing. Het gedrag van Zoeken en rangschikken is hetzelfde voor elke winkel die de catalogus gebruikt.
   - **de mening van de Catalogus** - de regel is slechts op de geselecteerde catalogusmening (bijvoorbeeld, één opslag, gebied, handelaar, of merk) van toepassing. Gebruik deze optie wanneer verschillende catalogusweergaven andere logica voor het verhandelen vereisen.

Voor details bij het creëren van een regel en het plaatsen van zijn werkingsgebied, zie [ regels ](add.md) creëren en beheren.

### Waarom een regel per catalogusweergave maken?

Maak regels per catalogusweergave wanneer verschillende winkels, regio&#39;s of merken een ander zoek- en classificatiegedrag nodig hebben. Voorbeelden:

- **Dealer of distributienetwerken** - elke handelaar heeft zijn eigen catalogusmening; u wilt verschillende vastgezette, gebooste, of begraven producten per handelaar.
- **Multi-region** - de afzonderlijke catalogusmeningen voor EU, de V.S., of andere gebieden met gebied-specifieke handelsregels.
- **Multi-brand** - Elk merk heeft zijn eigen catalogusmening en u wilt merkspecifieke regels (bijvoorbeeld, verschillende standaardrangschikking of bevorderde producten per merk).

De gegevens van het gedrag die [ intelligente rangschikking ](add.md#intelligent-ranking) (zoals het meest bekeken, het meeste gekochte, trending) bevoegdheden {worden berekend per catalogusmening door gebrek. Regels die gebruikmaken van intelligente rangschikking weerspiegelen daarom het gedrag van de winkelier van die catalogusweergave. Als uw account een groot aantal catalogusweergaven bevat, kan het systeem gedragsgegevens globaal samenvoegen om de prestaties te behouden. In dat geval kan de rangschikking meer worden beïnvloed door catalogusweergaven met veel verkeer en kan de relevantie voor weergaven met minder verkeer worden verminderd. Zie [ Beperkingen en grenzen ](../../boundaries-limits.md) voor huidige grenzen.

### Een regel instellen per catalogusweergave

1. Voor de *Merchandising Regels* werkruimte, gebruik **[!UICONTROL Catalog view]** dropdown om de catalogusmening te selecteren waar de regel zou moeten van toepassing zijn.
1. Klik op **[!UICONTROL Create rule]**.

   De regel die u maakt, valt binnen het bereik van de geselecteerde catalogusweergave.
1. Bouw uw regel in de [ regelredacteur ](add.md).

   Definieer in de editor voorwaarden, gebeurtenissen en details. De regel geldt alleen voor zoekresultaten in die catalogusweergave.

U kunt de catalogusweergave (het bereik) van een regel niet wijzigen nadat u deze hebt gemaakt. Als u een vergelijkbare logica wilt toepassen op een andere catalogusweergave, maakt u een nieuwe regel en selecteert u die catalogusweergave voordat u deze maakt.
