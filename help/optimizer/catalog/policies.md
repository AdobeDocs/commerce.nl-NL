---
title: Beleid
description: Leer hoe te om beleid te gebruiken om gegevens binnen een kanaal te filtreren om ervoor te zorgen dat de gegevens naar de juiste bestemming worden verzonden.
hide: true
recommendations: noCatalog
exl-id: 05bbad1a-d612-41a4-9575-543f507089c3
source-git-commit: a731d978aa180633431b0dd9dde5439c286461a2
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# Beleid

>[!NOTE]
>
>Deze documentatie beschrijft een product in vroege-toegangsontwikkeling en weerspiegelt niet alle functionaliteit voorgenomen voor algemene beschikbaarheid.

Het beleid is de filters van de gegevenstoegang bevat binnen kanalen die de gegevens verder verfijnen die aan elk kanaal worden geleverd. Het beleid zorgt ervoor dat de juiste inhoud wordt verzonden naar de juiste bestemming. Bijvoorbeeld fysieke winkels, marketingplaatsen, advertentiepijpleidingen (Google, Facebook, Instagram).

Het beleid is gebaseerd op productkenmerken, zoals merk, model of onderdelencategorie, en wordt gebruikt om de catalogusgegevens aan te passen aan specifieke bedrijfsvereisten. &#x200B;

## Filters

Filters zijn het mechanisme binnen een beleid dat catalogussegmentatie afdwingt. Met filters kunnen bedrijven hun winkelvoorkeuren en kanalen aanpassen aan specifieke productsets op basis van operationele behoeften. U gebruikt criteria zoals productkenmerken, operatoren en waarden om een regel of voorwaarde te definiëren die aangeeft welke producten in een kanaal of winkel zijn opgenomen of uitgesloten.

### Delen van een filter

Een filter bestaat uit de volgende onderdelen:

| Part | Beschrijving | Voorbeeld |
|---|---|---|
| **Attribuut** | The product attribute used for filtering. | `part_category` |
| **Exploitant** | De voorwaarde die op het attribuut wordt toegepast. | `IN`, `EQUALS`, `CONTAINS` |
| **bron van de Waarde** | Geeft aan of de waarden `STATIC` of `TRIGGER` zijn. | `STATIC` [ Leer meer ](#value-source-types) |
| **Waarde** | De specifieke waarden die aan de voorwaarde voldoen. | `brakes, suspension` |

### Voorbeeld

Een filter met het kenmerk `part_category` , een operator van `IN` en values `brakes, suspension` zorgt ervoor dat alleen producten met een kenmerk `part_category` dat de waarde `brake` of `suspension` heeft, door het beleid worden gefilterd en weergegeven.

### Brontypen van waarden

Er zijn twee soorten waardebronnen: **STATISCHE** en **TRIGGER**.

Het beleid met a **bron van de Waarde** van **STATIC** wordt beschouwd als universeel beleid. Met universeel beleid wordt de ervaring van een website als geheel gedefinieerd. Dit betekent dat het kanaal dat beleid altijd zal uitvoeren. Met andere woorden, de uitvoering van dat beleid is niet gebaseerd op enige gebruikersinteractie op de storefront.

Het beleid met a **bron van de Waarde** van **TRIGGER** wordt bedoeld als exclusief beleid. Dit betekent dat het kanaal dat beleid slechts zal uitvoeren wanneer de trekker in de kopbal van de API vraag wordt gespecificeerd. Op de winkel betekent dit dat de informatie wordt weergegeven op basis van wat de verkoper selecteert. Bijvoorbeeld, in het volgende beeld, zijn er twee drop-down menu&#39;s: **Merk** en **Model**.

![ Trigger waardebron op storefront ](../assets/policy-trigger.png)

**Merk** en **Model** worden bepaalde trekkers:

- `AC-Policy-Brand`
- `AC-Policy-Model`

Als de verkoopster **Merk** drop-down klikt, bevat de kopbal van de API vraag `AC-Policy-Brand`, die wordt gevormd om producten slechts te tonen specifiek voor het `AC-Policy-Brand` beleid.

## Beleid maken

In deze sectie maakt u een nieuw beleid. Het beleid kan of **STATISCHE** of **TRIGGER** zijn.

### Een STATISCH beleid maken

1. Open in het linkermenu de sectie **[!UICONTROL Catalog]** en klik op **[!UICONTROL Policies]** .

1. Klik op **[!UICONTROL Add Policy]** .

   Er wordt een nieuwe pagina geopend waarin u de beleidsdetails kunt invullen. &#x200B;

1. Voer de naam van het beleid in, bijvoorbeeld &quot;Categorieën van certificaatonderdelen&quot;.

1. Klik op **[!UICONTROL Add Filter]** .

   Er wordt een dialoogvenster geopend waarin u filterdetails kunt toevoegen.

1. Voeg de filterdetails toe. Bijvoorbeeld:

   1. **Attribuut** - ga een attribuut van uw catalogus in. Bijvoorbeeld &quot;part_category&quot;. Deze naam moet exact overeenkomen met de naam van het kenmerk in de catalogus.
   1. **Exploitant** - kies de exploitant. Bijvoorbeeld, **IN**. &#x200B;
   1. **waarde Source** - Uitgezochte **STATIC**. &#x200B;
   1. **Waarde** - ga de waarde(n) binnen de attributen in u eerder specificeerde. Bijvoorbeeld &quot;remmen, ophanging&quot;. &#x200B;Deze namen moeten exact overeenkomen met de namen van de waarden voor het kenmerk dat u eerder hebt opgegeven.

1. Klik op de knop **[!UICONTROL Save]** in het dialoogvenster met filterdetails. &#x200B;

1. Klik de actiepunten (...) naast de filter u creeerde en **selecteert laat** toe. Van hier, kunt u **ook uitgeven**, **** onbruikbaar maken, of **schrappen** de filter.

   De **kolom van de Status** toont een groen pictogram en het woord &quot;Toegelaten&quot;.

1. Klik op **[!UICONTROL Save]** om het nieuwe beleid op te slaan. &#x200B; Als de knoop niet actief is, zorg ervoor dat de beleidsnaam wordt toegevoegd door het potloodpictogram naast **Nieuw Beleid** te klikken.

1. Als u uw nieuwe beleid wilt verifiëren, gaat u terug naar de lijst met beleidsregels door op de pijl Vorige te klikken. &#x200B;Je nieuwe beleid wordt weergegeven.

### Een TRIGGER-beleid maken

1. Open in het linkermenu de sectie **[!UICONTROL Catalog]** en klik op **[!UICONTROL Policies]** .

1. Klik op **[!UICONTROL Add Policy]** .

   Er wordt een nieuwe pagina geopend waarin u de beleidsdetails kunt invullen. &#x200B;

1. Voer de naam van het beleid in, bijvoorbeeld &quot;Categorieën van certificaatonderdelen&quot;.

1. Klik op **[!UICONTROL Add Trigger]** .

   De **details van de Trekker** dialoog verschijnt.

1. Ga een naam voor de trekker, zoals **AC-beleid-merk** in.

1. Selecteer het **type van Vervoer**. **HTTP_HEADER** is momenteel het enige gesteunde type.

1. Klik op **[!UICONTROL Save]** om de trigger op te slaan.

1. Klik op **[!UICONTROL Add Filter]** .

   Er wordt een dialoogvenster geopend waarin u filterdetails kunt toevoegen.

1. Voeg de filterdetails toe. Bijvoorbeeld:

   1. **Attribuut** - ga een attribuut van uw catalogus in. Bijvoorbeeld &quot;part_category&quot;. Deze naam moet exact overeenkomen met de naam van het kenmerk in de catalogus.
   1. **Exploitant** - kies de exploitant. Bijvoorbeeld, **IN**. &#x200B;
   1. **Source van de Waarde** - selecteer **TRIGGER**. &#x200B;
   1. **Waarde** - ga de trekkernaam in u eerder creeerde (**AC-beleid-merk**).

1. Klik op de knop **[!UICONTROL Save]** in het dialoogvenster met filterdetails. &#x200B;

1. Klik de actiepunten (...) naast de filter u creeerde en **selecteert laat** toe. Van hier, kunt u **ook uitgeven**, **** onbruikbaar maken, of **schrappen** de filter.

   De **kolom van de Status** toont een groen pictogram en het woord &quot;Toegelaten&quot;.

1. Klik op **[!UICONTROL Save]** om het nieuwe beleid op te slaan. &#x200B; Als de knoop niet actief is, zorg ervoor dat de beleidsnaam wordt toegevoegd door het potloodpictogram naast **Nieuw Beleid** te klikken.

1. Als u uw nieuwe beleid wilt verifiëren, gaat u terug naar de lijst met beleidsregels door op de pijl Vorige te klikken. &#x200B;Je nieuwe beleid wordt weergegeven.

Door deze stappen te volgen, zal het beleid worden gecreeerd en bereid om aan een kanaal worden verbonden om productzichtbaarheid te controleren.
