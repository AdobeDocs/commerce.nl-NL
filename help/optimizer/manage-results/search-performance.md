---
title: Zoekprestaties
description: De pagina met zoekprestaties biedt insight toegang tot de zoektermen die kopers gebruiken.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: f49a86b8793e2d91413acfbc0b922cb94db67362
workflow-type: tm+mt
source-wordcount: '1737'
ht-degree: 0%

---

# Zoekprestaties

De *prestaties van het Onderzoek* pagina verstrekt insight in de onderzoekstermijnen die de kopers gebruiken. De informatie kan worden gebruikt om tendensen te identificeren, klik-door te verhogen, en de omzettingspercentage te verbeteren. De pagina met zoekprestaties biedt een momentopname van zoekgegevens voor een specifiek datumbereik en bevat de volgende rapporten:

- Unieke zoekopdrachten
- Gemiddelde klikpositie
- Doorklikfrequentie
- Omrekeningskoers
- Resultaatsnelheid nul

![&#128279;](../assets/search-performance.png){zoomable="yes"} prestaties van het 0&rbrace; Onderzoek

>[!IMPORTANT]
>
>Als u geen metriek van onderzoeksprestaties ziet, zorg ervoor de gegevens van de onderzoeksgebeurtenis [ worden verzameld ](../setup/events/overview.md).

## Kies de **mening van de Catalogus**

Selecteer de [ catalogusmening ](../setup/catalog-view.md) om de specifieke resultaten van onderzoeksprestaties te zien.

![ de Mening van de Catalogus ](../assets/catalog-view.png)

## Een rapport weergeven

Klik op de kalender en voer een van de volgende handelingen uit:

- Als u één datum wilt opgeven, dubbelklikt u op de datum in de kalender.
- Als u een datumbereik wilt opgeven, klikt u op de eerste en laatste datum in de kalender.

>[!NOTE]
>
>Het datumbereik mag niet langer zijn dan één jaar.

Klik op **[!UICONTROL Export to CSV]** om een CSV-bestand met uw zoekprestaties te genereren.

## De zoekprestaties verbeteren

In het volgende gedeelte vindt u strategieën waarmee u de zoekfunctionaliteit van uw site kunt verbeteren. Zo beschikt u over een naadloze en efficiënte verkoopervaring die de conversiekoersen maximaliseert.

Er zijn verschillende belangrijke factoren die de relevantie en doeltreffendheid van de zoekresultaten bepalen:

- Goed gestructureerde productgegevens zorgen ervoor dat de onderzoeksalgoritmen producten aan vragen effectief kunnen aanpassen. Lage productgegevens leiden tot minder relevante zoekresultaten. Om het succes van uw koopwaar direct te beïnvloeden strategie:
   - Opstelling de correcte [ attributen zoals doorzoekbaar ](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/api-reference/#tag/Metadata) met hun overeenkomstige gewicht.
   - Zorg ervoor dat de gegevens binnen die kenmerken relevant zijn.
- Een goed ontworpen zoekervaring is een vertrouwensbasis met klanten en geeft het vertrouwen dat ze zullen vinden wat ze nodig hebben.
- De regels van het onderzoek zijn kritiek aangezien zij de zichtbaarheid van bepaalde producten kunnen verhogen die op populariteit, nieuwe aankomst, promotiecriteria of een andere handelsstrategie worden gebaseerd om aan uw bedrijfsvereisten te voldoen.
- Met gefaciliteerde navigatie kunnen kopers hun zoekopdracht verfijnen en snel relevante resultaten behalen.

### Zoekresultaten controleren

Om onderzoeksresultaten met [!DNL Adobe Commerce Optimizer] te optimaliseren, controleer relevante Zeer belangrijke Indicatoren van Prestaties (KPIs) zoals unieke vragen, gemiddelde klikpositie, klikdoorgangstarieven, conversietarief, en nul resultaattarief om te begrijpen hoe de kopers met uw onderzoeksfunctionaliteit interactie aangaan. Op basis van deze gegevens kunt u regelmatig uw zoekregels bijwerken en verfijnen.

- **Unieke Zoekopdrachten** - de telling van verschillende onderzoeksvragen die op uw [!DNL Adobe Commerce Optimizer] plaats worden uitgevoerd. Elke unieke zoekopdracht wordt slechts één keer geteld, zelfs als deze meerdere keren door dezelfde winkelier of door verschillende kopers wordt herhaald. Deze metrische informatie helpt u de diversiteit van onderzoekstermijnen begrijpen die door klanten worden gebruikt en verstrekt inzicht in welke producten of informatiekopers zoeken. Door unieke zoekopdrachten te volgen kunt u:

   - Identificeer populaire onderzoekstendensen en vaak doorzocht punten.
   - Ontdek mogelijke hiaten in uw productcatalogus of inhoud.
   - Optimaliseer uw onderzoeksfunctionaliteit door [ synoniemen ](../merchandising/synonyms/overview.md) toe te voegen, creërend, of het bijwerken [ onderzoeksregels ](../merchandising/rules/overview.md).

- **Gemiddelde klikPositie** - wijst erop dat de gemiddelde positie van onderzoeksresultaten door kopers na het uitvoeren van een onderzoeksvraag op uw plaats klikte. Deze metrisch verstrekt inzicht in de relevantie en de doeltreffendheid van uw onderzoeksresultaten.

  Een lagere gemiddelde klikpositie (dichter aan 1) suggereert dat de kopers relevante resultaten snel vinden, erop wijzend dat uw onderzoeksstrategie efficiënt is. Het helpt u verkoopgedrag te begrijpen en hoe ver zij bereid zijn te scrollen om het gewenste product te vinden. Als de gemiddelde klikpositie hoog is, kan het erop wijzen dat de meest relevante resultaten niet bij de bovenkant verschijnen, die een overzicht en een optimalisering van uw onderzoeksstrategie vereist.

- **klik-door Tarief (CTR)** - Meet het percentage van kopers die op een onderzoeksresultaat na het uitvoeren van een onderzoeksvraag klikken. Een hoge CTR geeft aan dat de zoekresultaten relevant zijn en aantrekkelijk zijn voor kopers, omdat ze op de gevonden resultaten klikken. Het toezicht op CTR kan helpen gebieden voor verbetering identificeren. Lage CTR kan suggereren dat de onderzoeksresultaten niet de gelijke verkoopintentie aanpassen, die een behoefte ertoe aanzetten om onderzoeksregels te verfijnen, productgegevens te verbeteren, of resultaatpresentatie te verbeteren.

- **het tarief van de Omzetting** - wijst op de doeltreffendheid van uw onderzoekseigenschap in het drijven van verkoop en het bereiken van bedrijfsdoelstellingen. Het weerspiegelt de algemene doeltreffendheid van uw zoekfunctionaliteit om aan de behoeften van winkeliers te voldoen en een soepele winkelervaring te vergemakkelijken. Een hoge conversiesnelheid geeft aan dat je zoekresultaten zeer relevant en overtuigend zijn, waardoor kopers hun aankopen kunnen voltooien. Als de omrekeningskoers laag is, kan het kwesties met onderzoeksrelevantie, productbeschikbaarheid, of de algemene reis van winkelbezoekers van onderzoek aan aankoop voorstellen.

- **Nul resultaattarief** - meet het percentage onderzoeksvragen op uw [!DNL Adobe Commerce Optimizer] plaats die geen resultaten terugkeren. Deze maatstaf is van cruciaal belang om te begrijpen hoe vaak de zoekopdrachten van klanten mislukken en kan inzicht verschaffen in mogelijke leemten in uw productcatalogus of zoekinstellingen. Een hoge nulresultatensnelheid kan consumenten frustreren, wat leidt tot een slechte winkelervaring en mogelijk verlies van klanten. Je kunt aangeven naar welke ontbrekende producten of rubrieken in je catalogus kopers zoeken, een overzicht geven en beslissingen nemen over productaanbiedingen.

  U kunt de nulresultatensnelheid verlagen door:

   - Het alternatief van de aanbieding of verwante onderzoekstermijnen, zoals [ synoniemen ](../merchandising/synonyms/overview.md) wanneer geen nauwkeurige gelijken worden gevonden.
   - Controleer regelmatig nulresultaatquery&#39;s om patronen te identificeren en de benodigde aanpassingen aan te brengen in uw productcatalogus en zoekinstellingen.

U kunt deze metrische gegevens gebruiken om uw onderzoeksfunctionaliteit op de volgende manieren te optimaliseren:

- Implementeer regels om populaire producten automatisch hoger te plaatsen in zoekresultaten. Producten waarop vaak is geklikt of die zijn aangeschaft, krijgen voorrang om bovenaan te worden weergegeven. Leer handmatig lijsten met populaire producten voor specifieke zoekopdrachten en controleer of deze items goed worden weergegeven.
- Markeer producten die momenteel trending hebben of onlangs een piek in populariteit hebben gezien. Dit kan met name effectief zijn tijdens seizoensgebonden evenementen, vakanties of promotieperioden. Om dit te bereiken, gebruik de intelligente rangschikking die beter uw gebruiksgeval en bedrijfsbehoefte wanneer vestiging een onderzoeksregel aanpast.
- Wanneer populaire filters of facetten markeren die kopers vaak filteren op bepaalde merken of prijsbereiken, maken ze deze opties prominent door die facetten vast te zetten en ze dienovereenkomstig te sorteren.
- Wanneer een zoekopdracht geen resultaten oplevert, gebruikt u populaire resultaatgegevens om alternatieve producten of verwante categorieën voor te stellen die een grote betrokkenheid van winkels hebben.
- Analyseer populaire zoektermen en productgegevens om belangrijke trefwoorden te identificeren. Optimaliseer uw product doorzoekbare attributen met deze sleutelwoorden om onderzoeksrelevantie te verbeteren.
- Analyseer regelmatig uw resultaatgegevens om veranderende tendensen, verkoopvoorkeur en gedrag te begrijpen, hoogste onderzoekstermijnen te identificeren, en kwesties te ontdekken. Met deze feedbacklus kunt u uw zoekregels en productaanbiedingen voortdurend verfijnen en verbeteren

## Uw zoekfunctionaliteit optimaliseren

Om uw onderzoeksfunctionaliteit te optimaliseren, gebruik [ synoniemen en spelling ](../merchandising/synonyms/overview.md) om ervoor te zorgen dat de consumenten producten vinden zelfs als zij verschillende woorden en [ facetten ](../merchandising/facets/overview.md) gebruiken om consumenten toe te staan om onderzoeksresultaten te beperken.

## De relevantie van zoekresultaten verbeteren

Om de relevantie van het onderzoeksresultaat te verbeteren, voer efficiënte [ onderzoeksregels ](../merchandising/rules/overview.md) uit en gebruik productmeta-gegevens om nauwkeurige en gedetailleerde [ attributen te verzekeren zijn doorzoekbaar ](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/api-reference/#tag/Metadata).

### Afbeeldingen

Zorg ervoor dat de configureerbare producten van het kindproducten beelden met de correcte rollen hebben. Als u bovenliggende of onderliggende producten hebt, heeft het zoekresultaat mogelijk geen afbeeldingen.

>[!NOTE]
>
>Afbeeldingen in zoekresultaten kunnen verschillen, afhankelijk van de zoekterm. Als de zoekterm bepaalt dat een onderliggend product relevanter is, worden afbeeldingen uit het onderliggende product gebruikt in plaats van afbeeldingen uit het bovenliggende product.

### Productmetagegevens gebruiken

Zorg ervoor dat de nauwkeurige en gedetailleerde product [ attributen opstelling zoals doorzoekbaar ](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/api-reference/#tag/Metadata) zijn. SKU-, naam- en categoriekenmerken kunnen standaard worden doorzocht en kunnen niet worden uitgesloten van de zoekopdracht. U bereikt de beste resultaten als u geen spaties gebruikt in uw SKU&#39;s.

Om zoekrelevantie te vergroten, wijst u een gewicht toe aan elk doorzoekbaar kenmerk. Kenmerken met een hogere dikte moeten in de zoekresultaten hoger worden weergegeven. Sorteren op relevantie wordt beïnvloed door meerdere criteria, zoals zoekgewicht. Dit betekent dat kenmerken met een lager zoekgewicht soms nog relevanter kunnen zijn dan kenmerken met een hoger zoekgewicht. Andere criteria kunnen het aantal overeenkomsten in een bepaald kenmerk, de positie van de gevonden zoekterm en de algemene tekststructuur vóór en na een zoekterm bevatten.

Zorg ervoor dat elk product relevante inhoud binnen elk doorzoekbaar kenmerk heeft. Het wordt afgeraden een kenmerk in te stellen als doorzoekbaar als het een grote hoeveelheid inhoud bevat, waardoor de relevantie van zoekresultaten afneemt.

Meer informatie over productkenmerken voor zoekopdrachten:

- [ vastgestelde attributen als doorzoekbaar ](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/api-reference/#tag/Metadata)
- [ Wijs gewicht aan attributen ](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/api-reference/#operation/createProductMetadata) toe

## Veldomschrijvingen

| Opnamegegevens | Beschrijving |
|--- |--- |
| Unieke zoekopdrachten | Het totale aantal unieke zoekopdrachten voor het opgegeven datumbereik. De veelvoudige onderzoeken door de zelfde verkoopster, zelfs als voor de zelfde vraag, worden beschouwd als uniek als voorgelegd meer dan één uur uit elkaar. |
| Doorklikfrequentie | Het percentage zoekopdrachten dat wordt afgesloten met het klikken op een product door de verkoper. De doorklikfrequentie is bijvoorbeeld 50% als de winkel op &quot;broek&quot; en &quot;shirt&quot; zoekt en vervolgens op één resultaat klikt in de &quot;shirt&quot;-zoekopdracht. |
| Omrekeningskoers | Het percentage producten de winkelaankopen tegenover het aantal producten de verkoopster voor de gespecificeerde datumwaaier klikt. De conversiesnelheid van de interactie is bijvoorbeeld 100% als de klant zes producten in de popover weergeeft, op een product klikt en een aankoop doet. <br /><br /> de omzettingssnelheid wordt niet beïnvloed door het aantal meningen van een bepaald product. De omrekeningskoers blijft bijvoorbeeld hetzelfde als de gebruiker van de zoekopdracht op een product klikt. |
| Resultaatsnelheid nul | Het percentage unieke zoekopdrachten dat geen resultaten retourneert voor het opgegeven datumbereik. De nulresultatenfrequentie is bijvoorbeeld 66,67% als de winkel tweemaal zoekt naar &quot;fjjajfjfjf&quot; (zonder resultaten) en naar &quot;broek&quot; (met resultaten). |
| Gem. klikpositie | De relatieve positie van de gemiddelde doorkliksnelheid op basis van unieke zoekopdrachten voor het opgegeven datumbereik. |

| Rapporten | Beschrijving |
|--- |--- |
| Resultaten nul | Maakt een lijst van de onderzoeksvragen die geen resultaten en het aantal tijden terugkeren die tijdens de gespecificeerde datumwaaier worden gebruikt. Rapportlimiet: de hoogste 500 voorwaarden |
| Populaire resultaten | Maakt een lijst van de namen van producten die de meeste meningen tijdens de gespecificeerde datumwaaier ontvingen. De populaire resultaten worden berekend gebaseerd op beelden slechts en worden niet beïnvloed door het aantal geklikte of opbrengst. Rapportlimiet: de hoogste 500 voorwaarden |
| Unieke zoekopdrachten | Hiermee geeft u de unieke zoekquery&#39;s weer die worden gebruikt tijdens het opgegeven datumbereik. De rapportgegevens worden op dezelfde manier berekend als de unieke gegevens van de onderzoeksmomentopname. Als een verkoper de zelfde onderzoeksvraag tweemaal, maar meer dan een uur uit elkaar typt, wordt het onderzoek beschouwd als twee unieke onderzoeken. Rapportlimiet: de hoogste 500 voorwaarden |
