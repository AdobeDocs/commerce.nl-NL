---
title: '[!DNL Live Search] Aanbevolen werkwijzen'
description: Leer de beste praktijken voor het uitvoeren van  [!DNL Live Search]  in uw opslag.
role: Admin, Developer
exl-id: f7700339-fb13-42fe-a249-17cd4ba36e1b
source-git-commit: c3d431a6536c3c5528b9aee45f03b0b94b4ea64e
workflow-type: tm+mt
source-wordcount: '2892'
ht-degree: 0%

---

# Aanbevolen procedures

Dit artikel helpt handelaren hun zoekfunctionaliteit voor sites te verbeteren en zorgt voor een naadloze en efficiënte verkoopervaring die de conversiesnelheden maximaliseert. Door de beschreven strategieën te volgen leert u hoe u geavanceerde zoekfuncties kunt implementeren en uw zoekfunctie voortdurend kunt verfijnen voor optimale prestaties met Adobe Commerce [!DNL Live Search] .

Er zijn verschillende belangrijke factoren die de relevantie en doeltreffendheid van de zoekresultaten bepalen:

- Goed gestructureerde productgegevens zorgen ervoor dat de onderzoeksalgoritmen producten aan vragen effectief kunnen aanpassen. Lage kwaliteit van productgegevens leidt tot weinig relevante zoekresultaten. Om het succes van uw koopwaar direct te beïnvloeden strategie:
   - Stel de juiste kenmerken in als doorzoekbaar met het corresponderende gewicht.
   - Zorg ervoor dat de gegevens binnen die kenmerken relevant zijn.
- Een goed ontworpen zoekervaring bouwt vertrouwen op bij klanten en stelt het vertrouwen in dat ze kunnen vinden wat ze nodig hebben.
- De regels van het onderzoek zijn kritiek aangezien zij de zichtbaarheid van bepaalde producten kunnen verhogen die op populariteit, nieuwe aankomst, promotiecriteria of een andere handelsstrategie worden gebaseerd om aan uw bedrijfsvereisten te voldoen.
- Met gefaciliteerde navigatie kunnen kopers hun zoekopdracht verfijnen en snel relevante resultaten behalen.

Om [!DNL Live Search] te beheren, ga **Marketing** > *SEO &amp; Onderzoek* > **[!DNL Live Search]** in Adobe [!DNL Commerce] Admin. 

## Uw zoekfunctionaliteit optimaliseren

In deze sectie leert u hoe u de zoekfunctionaliteit kunt optimaliseren door functies zoals automatisch aanvullen te gebruiken om real-time suggesties te bieden, zoals type, synoniemen en spelling van kopers, zodat kopers producten kunnen zoeken, zelfs als ze andere woorden gebruiken, en facetten waarmee kopers zoekresultaten kunnen beperken.

### Automatisch aanvullen

Automatisch aanvullen, ook wel &#39;type-ahead&#39; of &#39;auto-suggestie&#39; genoemd, is een interactieve zoekfunctie die dynamisch suggesties weergeeft aan kopers die hun zoektermen invoeren. Op deze manier kunnen kopers snel en gemakkelijk producten vinden door real-time suggesties te bieden op basis van hun input.

Met de widget [!DNL Live Search] [[!DNL popover]](storefront-popover.md) kunt u via automatische zoekopties veelgebruikte producten voorstellen. Als elk teken door de verkoper wordt getypt, wordt de pop-up bijgewerkt met de voorgestelde producten en miniatuurafbeeldingen van de bovenste zoekresultaten.

[!DNL Live Search] geeft resultaten wanneer de gebruiker twee tekens heeft getypt. Voor een gedeeltelijke overeenkomst, is het maximumaantal karakters per woord 20. Het aantal karakters in een &quot;onderzoek aangezien u&quot;vraag typt is niet configureerbaar.

Leer meer over [&#x200B; popover &#x200B;](storefront-popover.md) widget.

### Synoniemen en spelfouten

Live zoeken beheert standaard spelfouten. U kunt synoniemen instellen om woorden op te nemen die mogelijk door kopers worden gebruikt die afwijken van de woorden die in uw catalogus zijn opgegeven. Je wilt geen uitverkoop verliezen omdat iemand op zoek is naar een &quot;sofa&quot;, terwijl je product wordt aangeboden als een &quot;bank&quot;. U kunt een brede waaier van onderzoekstermijnen vangen door alle mogelijke woorden in te gaan die de klanten zouden kunnen gebruiken om uw producten te vinden. U kunt synoniemen [&#x200B; plaatsen als één manier of twee manier &#x200B;](synonyms-add.md#step-2-define-the-synonym-by-type) om resultaten te verbeteren.

#### Tips voor het optimaliseren van synoniemen

- Wijs merknamen en afkortingen toe aan hun volledige namen, bijvoorbeeld &quot;HP&quot;aan &quot;Hewlett-Packard&quot;en gemeenschappelijke productbijnamen, bijvoorbeeld &quot;iPhone&quot;aan &quot;Apple iPhone&quot;.
- Inclusief branchespecifieke jargon en termen die consumenten onderling verwisselbaar kunnen gebruiken, bijvoorbeeld &quot;sneakers&quot; en &quot;loopschoenen&quot;.
- Werk regelmatig de synchronisatielijst bij op basis van nieuwe zoektrends, producttoevoegingen en winkelgedrag.
- Test de doeltreffendheid van synoniem in kaart brengen door onderzoeksresultaten en winkelterugkoppelen te analyseren. Verfijn toewijzingen om nauwkeurigheid en relevantie te verbeteren.

Meer informatie over synoniemen:

- [Typen synoniemen](synonyms-type.md)
- [Synoniemen maken](synonyms-add.md)
- [Synoniemen beheren](synonyms-manage.md)
- [Taalondersteuning](settings.md#language)

### Facetten

Filter- en facetfunctionaliteit is een essentieel onderdeel van uw [!DNL Commerce] -site. Deze functie is ontworpen om de verkoopervaring te verbeteren door kopers in staat te stellen zoekresultaten te beperken en efficiënter naar producten te zoeken. Met deze functionaliteit kunnen kopers een uitgebreide lijst met artikelen bekijken door specifieke criteria toe te passen, waardoor het winkelproces sneller, eenvoudiger en tevredener wordt. Door efficiënte, verkoopvriendelijke filters en facetten te implementeren, kunt u klanten helpen precies te vinden wat ze nodig hebben, snel en efficiënt, waardoor uiteindelijk de tevredenheid en de conversietarieven worden verhoogd.

Aan opstelling moet een productattribuut als facet, het de volgende [&#x200B; geplaatste eigenschappen &#x200B;](facets-add.md#step-1-add-a-facet) hebben:

- **[!UICONTROL Use in Search]** -  `Yes`
- **[!UICONTROL Use in Layered Navigation]** -  `Filterable (with results)`
- **[!UICONTROL Use in Search Results Layered Navigation]** -  `Yes`

#### Tips om facetten te optimaliseren

- Bepaal de meest relevante en nuttige attributen voor uw producten, zoals titel, categorie, merk, prijswaaier, kleur, en grootte en plaats hen als [&#x200B; dynamische facetten &#x200B;](facets-type.md). 
- Stel productkenmerken in en sorteer deze op dezelfde manier in uw catalogus en zijn van groot belang voor uw producten om de relevantie en filtermogelijkheden voor uw klanten te verbeteren.
- Zorg ervoor dat facetlabels gemakkelijk te begrijpen zijn en consistent op de hele site worden genoemd. Gebruik bijvoorbeeld Prijsbereik in plaats van Kosten.
- Vermijd overweldigende kopers door het aantal facetten te beperken tot de belangrijkste. Te veel opties kunnen moeheid bij de beslissing veroorzaken. Standaard is [!DNL Live Search] beperkt tot maximaal 100 kenmerken die zijn geconfigureerd als facetten en 30 emmers die binnen elk facet worden geretourneerd. Leer meer over [&#x200B; facetbeperkingen &#x200B;](boundaries-limits.md#facets). 
- Kopers toestaan om meerdere filtercriteria tegelijk te selecteren om de resultaten te verfijnen. Zo kunt u kopers zowel de kleuren &quot;Rood&quot; als &quot;Blauw&quot; laten selecteren.
- Geef het aantal beschikbare producten naast elke facetoptie weer om kopers een idee te geven van de zoekresultaten die ze kunnen verwachten.
- Inklapbare facetsecties implementeren om de interface schoon en beheerbaar te houden, met name op mobiele apparaten.
- Kopers toestaan afzonderlijke facetten of alle geselecteerde filters eenvoudig opnieuw in te stellen om een nieuwe zoekopdracht te starten.

Meer informatie over facetten:

- [Typen facetten](facets-type.md)
- [Elementen toevoegen](facets-add.md)
- [&#x200B; beheert facetten &#x200B;](facets-manage.md) (geef uit, speld een facet, schrap, publiceer)
- [Prijsbeperking](settings.md#price-faceting)

## De relevantie van zoekresultaten verbeteren

In deze sectie wordt besproken hoe u de relevantie van zoekresultaten kunt verbeteren door effectieve zoekregels in te voeren en productmetagegevens te gebruiken om ervoor te zorgen dat nauwkeurige en gedetailleerde kenmerken doorzoekbaar zijn.

### Afbeeldingen

Zorg ervoor dat de configureerbare producten van het kindproducten beelden met de correcte rollen hebben. Als u bovenliggende of onderliggende producten hebt, heeft het zoekresultaat mogelijk geen afbeeldingen.

>[!NOTE]
>
>Afbeeldingen in zoekresultaten kunnen verschillen, afhankelijk van de zoekterm. Als de zoekterm bepaalt dat een onderliggend product relevanter is, worden afbeeldingen uit het onderliggende product gebruikt in plaats van afbeeldingen uit het bovenliggende product.

### Zoekregels

Om uw omzettingspercentage en opbrengst te optimaliseren, moet u efficiënte onderzoeksregels uitvoeren. Pas productrankings aan die op verkoopgegevens, voorraadniveaus, en bevorderingen met [&#x200B; het Merchandising van het Onderzoek &#x200B;](rules.md) worden gebaseerd.

Het is van cruciaal belang om een weloverwogen standaard zoekregel vast te stellen. Uw [&#x200B; standaardregel &#x200B;](rules.md#default-rule) bepaalt hoe de onderzoeksresultaten aanvankelijk worden gesorteerd en aan kopers getoond, die hun algemene ervaring verbeteren en de waarschijnlijkheid van aankoop verhogen. Regelmatige controle en aanpassing van deze regel zorgt ervoor dat deze op effectieve wijze aan de behoeften en bedrijfsdoelstellingen van de winkels blijft voldoen.

#### Tips voor het optimaliseren van zoekregels

- Producten met een hoog verkoopvolume of een recente verkoopactiviteit vastzetten of stimuleren.
- Prioriteit geven aan producten met een hoge score en positieve beoordelingen.
- Zorg ervoor dat de posten in de voorraad hoger worden gerangschikt.
- Geef een lichte prioriteit aan producten met hogere winstmarges zonder de relevantie in gevaar te brengen.
- Markeer producten die te koop zijn of deel uitmaken van speciale promoties.
- Stel zoekregels tijdens promotie- of verkoopperiodes automatisch in door het datumbereik tijdens de promotieperiode te gebruiken.
- Gebruik altijd het deelvenster &#39;Uw regel testen&#39; om te zien hoe uw intelligente waarderingsstrategie de werkelijke zoekresultaten voor verschillende query&#39;s beïnvloedt.
- De onderzoeksresultaten van het dagonderzoek die op individueel verkoopgedrag worden gebaseerd dat [&#x200B; intelligente rangschikking &#x200B;](rules-add.md#intelligent-ranking), zoals &quot;voor u&quot;wordt geadviseerd, &quot;het meest bekeken&quot;etc. gebruikt. Om winkelgedrag aan te passen, moet u ervoor zorgen dat de gebeurtenis correct wordt uitgevoerd. Voor Luminantietransacties is de optie Gebeurtenis beschikbaar buiten de box. Voor hoofdloze of douaneimplementaties, moet u het voorkomen [&#x200B; uitvoeren dat op uw specifieke behoeften wordt gebaseerd. &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/)

Meer informatie over zoekregels:

- [De werkruimte Merchandiing](rules-workspace.md#set-the-scope)
- [Vereisten](rules.md#requirements)
- [Standaardzoekregel](rules.md#default-rule)
- Zoekregels beheren
   - [Maken](rules-add.md)
   - [Bewerken, weergeven, verwijderen](rules-manage.md)
- Dataverzameling
   - [[!DNL Live Search]  gebeurtenissen &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#live-search)
   - [&#x200B; de Collector van de Gebeurtenis van Adobe Commerce &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/reference/event-framework/)
   - [&#x200B; de gebeurtenissen van Commerce GitHub &#x200B;](https://github.com/adobe/commerce-events/tree/main/examples) 

### Metagegevens van producten gebruiken

Zorg ervoor dat de nauwkeurige en gedetailleerde productattributen [&#x200B; opstelling als zoekbaar &#x200B;](workspace.md#set-attributes-as-searchable) zijn. SKU-, naam- en categoriekenmerken kunnen standaard worden doorzocht en kunnen niet worden uitgesloten van de zoekopdracht. U bereikt de beste resultaten als u geen spaties gebruikt in uw SKU&#39;s.

Het kiezen van de kenmerken die u wilt doorzoeken, heeft grote invloed op de zoekkwaliteit. Het doorzoeken van te veel kenmerken kan de relevantie verminderen en onverwachte overeenkomsten tot gevolg hebben, zelfs als het aantal geretourneerde resultaten hierdoor toeneemt. In deze sectie wordt uitgelegd hoe u doorzoekbare kenmerken kunt selecteren om de dekking en relevantie in evenwicht te brengen.

**geadviseerde doorzoekbare attributen:**

- **de naam van het Product** - Hoog intent, beschrijft direct het product.
- **Primaire beschrijving** - de klanten van de beknopte productdetails verwachten om aan te passen.
- **Merk** - de Kopers zoeken vaak door merk.
- **Model aantal/stijl** - Specifieke herkenningstekens met duidelijke bedoeling.
- **Zeer belangrijke eigenschappen** - Belangrijke het onderscheiden kenmerken (bijvoorbeeld, &quot;waterdicht,&quot;draadloos&quot;).
- **Materiaal/Stof** - voor mode en meubilair categorieën.

**vermijd makend deze attributen doorzoekbaar:**

- **Lange beschrijvingen of specificaties** - teveel tekst leidt tot lawaai en onverwachte gelijken.
- **wegen van de Categorie** - kan irrelevante resultaten wegens brede taxonomitermijnen veroorzaken.
- **Interne codes van SKU met gemengde karakters** - creeert valse positieven op gedeeltelijke gelijken.
- **Administratieve gebieden** - Interne nota&#39;s of pakhuiscodes niet relevant voor kopers.
- **de inhoud of het formatteren van HTML markeringen** - de Technische inhoud verbetert geen relevantie.

#### Veelvoorkomende problemen die worden veroorzaakt door onjuiste doorzoekbare kenmerken

Het doorzoeken van verkeerde kenmerken kan de koper frustreren en tot supportescalaties leiden.

| Voorbeeld | Scenario | Aanbeveling |
|---------|----------|----------------|
| **het Afstammen en autocomplete bijwerkingen** | Een handelaar maakt lange productbeschrijvingen doorzoekbaar. Een winkelier zoekt naar &#39;kan&#39; (op zoek naar containers). Als gevolg van stamping en gedeeltelijke overeenkomst worden producten met &quot;kan&quot; als onderdeel van grotere woorden in hun beschrijvingen weergegeven, zoals &quot;American&quot;, &quot;canopy&quot; of &quot;canvas&quot;. Producten die geen verband houden met het intentoppervlak van de winkels, en ze verliezen het vertrouwen in de zoekactie. | Verminder doorzoekbare velden tot kenmerken met een hoge intentie, zoals de productnaam en de primaire beschrijving. Valideer de beste zoektermen om problematische overeenkomsten te identificeren. Gebruik regels voor het wijzigen van zoekopdrachten of omleidingen om bepaalde bekende randgevallen te verwerken. |
| **het Rangschikken door populariteit versterkt lawaaiige aanpassing** | Een handelaar plaatst het rangschikken aan &quot;het Meest Aangeschafte&quot;en omvat categoriewegen en lange beschrijvingen als doorzoekbare attributen. Een winkelier zoekt naar &quot;laptoptas&quot;. De brede overeenkomst retourneert laptoptassen, laptopaccessoires, tassen voor andere doeleinden en laptops zelf. Omdat laptops vaker worden aangeschaft dan laptoptassen, staan ze bovenaan. De verkoopster ziet de rangschikking als onjuist, ook al werkt het systeem zoals geconfigureerd. | Verwijder doorzoekbare ruiskenmerken, zoals categoriepaden. Zodra de gelijke reeks nauwkeuriger is, pas populariteit-gebaseerde het rangschikken strategieën toe. De onderzoeksanalyses van de monitor om vragen te identificeren waar dit patroon voorkomt. |
| **de weg van de Categorie leidt vals positieven** | Een handelaar maakt de volledige categoriepad doorzoekbaar (bijvoorbeeld &quot;Home > Keuken > Toestellen > Kleine Toestellen&quot;). Een winkelier zoekt naar &quot;thuiskantoor&quot;. Producten uit de categorie &quot;Home&quot; komen ook overeen als het keukenartikelen zijn, omdat &quot;home&quot; bestaat in het categoriepad. Keukenapparaten, thuiskleuren en andere niet-verwante producten worden in resultaten weergegeven, waardoor de relevantie afneemt. | Zorg ervoor dat categoriepaden niet doorzoekbaar zijn. Gebruik facetten om te zorgen dat kopers per categorie kunnen filteren. Als het categoriefilteren aan uw onderzoeksstrategie kritiek is, voer het door handelingsregels eerder dan doorzoekbare attributen uit. |

#### Gewicht doorzoekbare kenmerken

Om zoekrelevantie te vergroten, wijst u een gewicht toe aan elk doorzoekbaar kenmerk. Kenmerken met een hogere dikte moeten in de zoekresultaten hoger worden weergegeven. Sorteren op relevantie wordt beïnvloed door meerdere criteria, zoals zoekgewicht. Dit betekent dat kenmerken met een lager zoekgewicht soms nog relevanter kunnen zijn dan kenmerken met een hoger zoekgewicht. Andere criteria kunnen het aantal overeenkomsten in een bepaald kenmerk, de positie van de gevonden zoekterm en de algemene tekststructuur vóór en na een zoekterm bevatten.

**prioriteiten van het gewicht:**

- **Hoogste gewicht (9-10):** de naam van het Product, merk
- **gewicht van Medium (6-8):** Model aantal, primaire beschrijving, zeer belangrijke eigenschappen
- **Lager gewicht (3-5):** Secundaire beschrijvingen, materialen, specificaties

Zorg ervoor dat elk product relevante inhoud binnen elk doorzoekbaar kenmerk heeft. Het wordt afgeraden een kenmerk in te stellen als doorzoekbaar als het een grote hoeveelheid inhoud bevat, waardoor de relevantie van zoekresultaten afneemt.

#### Problemen oplossen

Als de onderzoeksresultaten willekeurig of irrelevant voelen, gebruik deze controlelijst alvorens als productgebrek te escaleren:

1. **van het Overzicht doorzoekbare attributenconfiguratie:**

   - Alle kenmerken weergeven die momenteel zijn ingesteld als doorzoekbaar.
   - Identificeer om het even welke brede of lawaaierige attributen (lange beschrijvingen, categoriepaden, administratieve gebieden).
   - Doorzoekbare status verwijderen uit kenmerken die geen verkoopintentie vertegenwoordigen.

1. **bevestigt vraaggelijken tegen kernattributen:**

   - Test de meest gebruikte zoekopdrachten.
   - Controleer of de resultaten vooral overeenkomen met de naam en het merk van het product in plaats van met de tangentiële tekst.
   - Schakel deze optie in als onverwachte resultaten alleen zwakke overeenkomsten in lange-formulierinhoud delen.

1. **Test met en zonder lawaaierige gebieden:**

   - De doorzoekbare status tijdelijk verwijderen uit het categoriepad en lange beschrijvingsvelden.
   - Herstel probleemvragen om na te gaan of de relevantie verbetert.
   - Als de resultaten verbeteren, permanent uw configuratie.

1. **het merchandising van het gebruik regels voor uitzonderingen:**

   - Voor specifieke bekende vragen die speciale behandeling vereisen, creeer gerichte onderzoeksregels.
   - Probeer randgevallen niet op te lossen door meer kenmerken doorzoekbaar te maken.
   - Gebruik omleidingen voor zoekopdrachten met een merknaam of voor veelgebruikte spelfouten.

1. **Monitor en herhaling:**

   - Gebruik de [&#x200B; werkruimte van Prestaties &#x200B;](performance.md) om nul resultaattarief en klik-door tarieven te volgen.
   - Bekijk de zoekopdrachten van de bovenste zoekopdracht wekelijks om nieuwe patronen te identificeren.
   - Pas doorzoekbare kenmerken en gewichten aan op basis van gegevens, niet op basis van veronderstellingen.

Meer informatie over productkenmerken voor zoekopdrachten:

- [Kenmerken instellen als doorzoekbaar](workspace.md#set-attributes-as-searchable)
- [&#x200B; Wijs gewicht aan attributen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/catalog/search/search-results#weighted-search) toe

## Zoekresultaten controleren

Om onderzoeksresultaten met [!DNL Live Search] te optimaliseren, controleer relevante Zeer belangrijke Indicatoren van Prestaties (KPIs) zoals unieke vragen, gemiddelde klikpositie, klikdoorgangstarieven, conversietarief, en nul resultaattarief om te begrijpen hoe de kopers met uw onderzoeksfunctionaliteit interactie aangaan. Op basis van deze gegevens kunt u regelmatig uw zoekregels bijwerken en verfijnen.

U kunt deze KPIs binnen de [!DNL Live Search] [&#x200B; werkruimte van Prestaties &#x200B;](performance.md) controleren waar u de volgende metriek vindt: 

- **Unieke Zoekopdrachten** - de telling van verschillende onderzoeksvragen die op uw [!DNL Commerce] plaats worden uitgevoerd. Elke unieke zoekopdracht wordt slechts één keer geteld, zelfs als deze meerdere keren door dezelfde winkelier of door verschillende kopers wordt herhaald. Deze metrische informatie helpt u de diversiteit van onderzoekstermijnen begrijpen die door klanten worden gebruikt en verstrekt inzicht in welke producten of informatiekopers zoeken. Door unieke zoekopdrachten te volgen kunt u:

   - Identificeer populaire onderzoekstendensen en vaak doorzocht punten.
   - Ontdek mogelijke hiaten in uw productcatalogus of inhoud.
   - Optimaliseer uw onderzoeksfunctionaliteit door [&#x200B; synoniemen &#x200B;](synonyms.md) toe te voegen, creërend, of het bijwerken onderzoeksregels.

- **Gemiddelde klikPositie** - wijst erop dat de gemiddelde positie van onderzoeksresultaten door kopers na het uitvoeren van een onderzoeksvraag op uw plaats klikte. Deze metrisch verstrekt inzicht in de relevantie en de doeltreffendheid van uw onderzoeksresultaten.

  Een lagere gemiddelde klikpositie (dichter aan 1) suggereert dat de kopers relevante resultaten snel vinden, erop wijzend dat uw onderzoeksstrategie efficiënt is. Het helpt u verkoopgedrag te begrijpen en hoe ver zij bereid zijn te scrollen om het gewenste product te vinden. Als de gemiddelde klikpositie hoog is, kan het erop wijzen dat de meest relevante resultaten niet bij de bovenkant verschijnen, die een overzicht en een optimalisering van uw onderzoeksstrategie vereist.

- **klik-door Tarief (CTR)** - Meet het percentage van kopers die op een onderzoeksresultaat na het uitvoeren van een onderzoeksvraag klikken. Een hoge CTR geeft aan dat de zoekresultaten relevant zijn en aantrekkelijk zijn voor kopers, omdat ze op de gevonden resultaten klikken. Het toezicht op CTR kan helpen gebieden voor verbetering identificeren. Lage CTR kan suggereren dat de onderzoeksresultaten niet de gelijke verkoopintentie aanpassen, die een behoefte ertoe aanzetten om onderzoeksregels te verfijnen, productgegevens te verbeteren, of resultaatpresentatie te verbeteren.

- **Tarief van de Omzetting** - wijst op de doeltreffendheid van uw onderzoekseigenschap in het drijven van verkoop en het bereiken van bedrijfsdoelstellingen. Het weerspiegelt de algemene doeltreffendheid van uw zoekfunctionaliteit om aan de behoeften van winkeliers te voldoen en een soepele winkelervaring te vergemakkelijken. Een hoge conversiesnelheid geeft aan dat je zoekresultaten zeer relevant en overtuigend zijn, waardoor kopers hun aankopen kunnen voltooien. Als de omrekeningskoers laag is, kan het kwesties met onderzoeksrelevantie, productbeschikbaarheid, of de algemene reis van winkelbezoekers van onderzoek aan aankoop voorstellen.

- **Nul Resultaten** - Meet het percentage onderzoeksvragen op uw [!DNL Commerce] plaats die geen resultaten terugkeren. Deze maatstaf is van cruciaal belang om te begrijpen hoe vaak de zoekopdrachten van klanten mislukken en kan inzicht verschaffen in mogelijke leemten in uw productcatalogus of zoekinstellingen. Een hoge nulresultatensnelheid kan consumenten frustreren, wat leidt tot een slechte winkelervaring en mogelijk verlies van klanten. Je kunt aangeven naar welke ontbrekende producten of rubrieken in je catalogus kopers zoeken, een overzicht geven en beslissingen nemen over productaanbiedingen.

  U kunt de nulresultatensnelheid verlagen door:

   - Het alternatief van de aanbieding of verwante onderzoekstermijnen, zoals [&#x200B; synoniemen &#x200B;](synonyms.md) wanneer geen nauwkeurige gelijken worden gevonden.
   - Controleer regelmatig nulresultaatquery&#39;s om patronen te identificeren en de benodigde aanpassingen aan te brengen in uw productcatalogus en zoekinstellingen.

- **Populaire Resultaten** - kan uw onderzoeksresultaten beduidend verbeteren door hen op winkelvoorkeur en gedrag te richten.

U kunt deze metrische gegevens gebruiken om uw onderzoeksfunctionaliteit op de volgende manieren te optimaliseren:

- Implementeer regels om populaire producten automatisch hoger te plaatsen in zoekresultaten. Producten waarop vaak is geklikt of die zijn aangeschaft, krijgen voorrang om bovenaan te worden weergegeven. Leer handmatig lijsten met populaire producten voor specifieke zoekopdrachten en controleer of deze items goed worden weergegeven.
- Markeer producten die momenteel trending hebben of onlangs een piek in populariteit hebben gezien. Dit kan met name effectief zijn tijdens seizoensgebonden evenementen, vakanties of promotieperioden. Om dit te bereiken, gebruik de intelligente rangschikking die beter uw gebruiksgeval en bedrijfsbehoefte wanneer vestiging een onderzoeksregel aanpast.
- Wanneer populaire filters of facetten markeren die kopers vaak filteren op bepaalde merken of prijsbereiken, maken ze deze opties prominent door die facetten vast te zetten en ze dienovereenkomstig te sorteren.
- Wanneer een zoekopdracht geen resultaten oplevert, gebruikt u populaire resultaatgegevens om alternatieve producten of verwante categorieën voor te stellen die een grote betrokkenheid van winkels hebben.
- Analyseer populaire zoektermen en productgegevens om belangrijke trefwoorden te identificeren. Optimaliseer uw product doorzoekbare attributen met deze sleutelwoorden om onderzoeksrelevantie te verbeteren.
- Analyseer regelmatig uw resultaatgegevens om veranderende tendensen, verkoopvoorkeur en gedrag te begrijpen, hoogste onderzoekstermijnen te identificeren, en kwesties te ontdekken. Met deze feedbacklus kunt u uw zoekregels en productaanbiedingen voortdurend verfijnen en verbeteren

Als u de juiste gegevens wilt ophalen in uw [!DNL Live Search] -rapport, moet u ervoor zorgen dat de gebeurtenis correct is geïmplementeerd. Voor Luminantietransacties is de optie Gebeurtenis beschikbaar buiten de box. Voor hoofdloze of douaneimplementaties, moet u het voorkomen [&#x200B; uitvoeren dat op uw specifieke behoeften wordt gebaseerd. &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/)
