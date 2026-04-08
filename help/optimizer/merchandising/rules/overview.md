---
title: Merchandising Rules
description: In [!DNL Adobe Commerce Optimizer] worden logica en handelingen voor het maken van zoekresultaten, standaardproductaanbiedingen en categoriepagina's gecombineerd met handelregels.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is op Adobe Commerce as a Cloud Service en  [!DNL Adobe Commerce Optimizer]  slechts projecten (Adobe-Beheerde infrastructuur SaaS) van toepassing."
exl-id: f2a9b5e8-d23d-4855-b424-ca6b40e057df
source-git-commit: 8abc0593c166a2dd861cfb78674918de1d0744de
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---

# Merchandising Rules

De regels van de handel brengen combineren logica met acties om te vormen hoe de producten in **onderzoeksresultaten** verschijnen, op **standaardproductlijsten** (**Alle productlijsten**), en op **categoriepagina&#39;s** ([&#x200B; categorieregels &#x200B;](#category-rules) zijn in bèta). U kunt, producten opvoeren begraven, vastzetten of verbergen en **intelligente rangschikking** toepassen zodat wijzen de lijsten op uw bedrijfsdoelstellingen.

Elk **onderzoeksregel** heeft drie belangrijkste componenten:

- **Voorwaarden** - op vraag-gebaseerde vereisten die een actie teweegbrengen wanneer het onderzoek van de verkoopster past.
- **Gebeurtenissen** - de acties die plaatsvinden wanneer de voorwaarden (handrangschikking en verwante gebeurtenissen) worden voldaan.
- **Details** - de naam van de regel, en facultatieve tijdkader en beschrijving.

**gebruiks** categorieselectie **in plaats van de voorwaarden van de onderzoeksvraag; het intelligente rangschikken en het handboek rangschikken werken de zelfde manier zoals voor onderzoek, met verschillen die in** worden geroepen creëren en leiden Regels [.](add.md)

U kunt veelvoudige voorwaarden en acties voor onderzoeksregels combineren, en om het even welke regel plannen om voor een periode actief te zijn. U kunt a **standaardregel** ook plaatsen (**Alle productlijsten**) die van toepassing is wanneer geen meer specifiek onderzoek of categorieregel van toepassing is.

## Categorievoorschriften {#category-rules}

>[!IMPORTANT]
>
>Categorieregels staan in bèta.

**de regels van de Categorie** orde van het controleproduct op **categoriepagina&#39;s**. U selecteert een of meer categorieën en past vervolgens een intelligente rangschikking (bijvoorbeeld de meest bekeken, trending) en handmatige handelingen toe, zoals vastzetten, opvoeren en begraven. Ze gebruiken geen zoekqueryvoorwaarden. Voor opstellingsstappen, regeltypes, en hoe het rangschikken op categorie tegenover onderzoek van toepassing is, zie [&#x200B; Regels &#x200B;](add.md) creëren en beheren.

## Vereisten

Een eenvoudige **onderzoeksregel** kan één enkele voorwaarde en één enkele gebeurtenis hebben, terwijl een complexe regel tot tien voorwaarden kan hebben die tot 25 gebeurtenissen teweegbrengen. **de regels van de Categorie** volgen de zelfde gebeurtenisgrenzen voor handrangschikking; zij gebruiken vraagvoorwaarden niet.

Regels kunnen:

- Tot tien **voorwaarden** (onderzoeksregels slechts)
- Tot 25 **gebeurtenissen**

Zoektekst kan het volgende bevatten:

- Alfanumerieke tekens (letters en cijfers)
- Hoofdletters of kleine letters. Kapitalisatie wordt genegeerd.

## Logische operatoren

De logische operatoren `AND` en `OR` voegen twee voorwaarden samen en retourneren verschillende resultaten. Alle logische operatoren die in een regel met meerdere voorwaarden worden gebruikt, zijn hetzelfde. Het is niet mogelijk om zowel `AND` als `OR` in dezelfde regel te gebruiken.

### Operatoren afstemmen

De operatoren Match `All` en `Any` bepalen de logische operator die wordt gebruikt om meerdere voorwaarden in de regel samen te voegen en kunnen worden gebruikt om de bestaande operator te wijzigen.

- `All` - Gebruikt de logische operator `AND` om meerdere voorwaarden te verbinden. Een regel die de operator `All` Match gebruikt, kan slechts één voorwaarde `Search query is` hebben.
- `Any` - Gebruikt de logische operator `OR` om meerdere voorwaarden te verbinden.

Wanneer het samenstellen van een complexe regel, kan het helpen om het met inspringing uit te schrijven om de voorwaarden, bijbehorende gebeurtenissen, en productnamen of SKUs te beschrijven die nodig zijn om de resultaten terug te keren u wilt bereiken. Vervolgens bouwt u de regel en test u het resultaat.

## Standaardregel

U kunt een standaardregel (**plaatsen Alle productlijsten**) die van toepassing is wanneer geen onderzoekstermijn wordt verstrekt, of geen andere onderzoeksregel kan worden toegepast. Als u de standaardregel aan &quot;het Meest Aangeschafte&quot;plaatst, dan vragen gebrek aan dat rangschikkende type tenzij vervangen door een specifiekere onderzoekstermijn. Er kan geen zoekterm voor de standaardregel worden ingesteld. **de regels van de Categorie** zijn afzonderlijk: zij zijn slechts op de categorieën van toepassing u selecteert en vervangen niet de standaardlijstregel.

## Volgorde van prioriteit met meerdere regels

Het volgende is op **onderzoeksregels** van toepassing en hoe zij voor een bepaald onderzoek in wisselwerking staan. **de regels van de Categorie** zijn van toepassing per categorie; zie [&#x200B; tot regels leiden en leiden &#x200B;](add.md#category-rules) voor hoe zij naast onderzoek en standaardregels passen.

Er wordt slechts één zoekregel tegelijk toegepast op een zoekterm.
Als meerdere regels van toepassing blijken te zijn op een zoekfrase, worden al deze regels toegepast. Als er een botsing tussen twee regels is— `rule 1` die sku1 opvoert maar `rule 2` het zelfde SKU-toen verbergt de onlangs toegepaste regel (`rule 2`) neemt belangrijkheid.

- Regels worden geordend met de tijdstempel &#39;Laatst gewijzigd&#39;. De regel die het laatst is gewijzigd, wordt eerst toegepast en daarna oudere regels in tijdstempelvolgorde.
- De voorwaarde `query is` heeft voorrang op andere voorwaarden. Als een nieuwere regel een voorwaarde `query contains` bevat, maar een oudere regel een voorwaarde `query is` heeft, wordt de regel `query is` toegepast.

### Storefront-aanvragen

Als een actieve regel met een voorwaarde `query is` overeenkomt met de zoekuitdrukking, wordt deze toegepast. Als er meerdere overeenkomende regels met een voorwaarde `query is` zijn, wordt de laatst bijgewerkte actieve regel toegepast.
Anders wordt de laatst bijgewerkte actieve regel toegepast.

### Voorvertoningsverzoeken

Aanvraag in [!DNL Adobe Commerce Optimizer] werkt iets anders. Bij het voorvertonen van [!DNL Adobe Commerce Optimizer] worden alle regels toegepast, inclusief de regels die zijn verlopen en gepland.

- Als de regel waarvan een voorvertoning wordt weergegeven een voorwaarde `query is` heeft, wordt deze toegepast.
- Als de regel waarvan een voorvertoning wordt weergegeven geen voorwaarde `query is` heeft en er een volgende actieve, overeenkomende regel met een voorwaarde `query is` wordt gevonden, wordt de regel `query is` toegepast.
- Als de regel waarvan een voorvertoning wordt weergegeven geen voorwaarde `query is` heeft en er geen andere regel met een voorwaarde `query is` wordt gevonden, wordt de regel toegepast die wordt voorvertoond.
