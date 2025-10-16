---
title: Typen aanbevelingen
description: Leer meer over de aanbevelingen die u op verschillende pagina's op uw site kunt implementeren.
exl-id: bbb290b0-b50b-43d9-bf71-1813298d5f39
source-git-commit: 67d0b98f3a9317c0db944a176fd99375091a3970
workflow-type: tm+mt
source-wordcount: '1991'
ht-degree: 0%

---

# Typen aanbevelingen

Adobe Commerce biedt een groot aantal aanbevelingen die u op verschillende pagina&#39;s op uw site kunt implementeren. Alle aanbevelingstypen zijn gebaseerd op gegevens. Ze worden aangedreven door gedragsgegevens, productkenmerkgegevens en meetgegevens. Ter referentie worden de aanbevolen typen als volgt gegroepeerd:

- [Gepersonaliseerd](#personalized)
- [Crosssells en up-sells](#crossup)
- [Populariteit](#popularity)
- [Krachtig](#highperf)

Als beste praktijk, adviseert Adobe de volgende richtlijnen wanneer het gebruiken van aanbevelingen:

- Diversifieer uw aanbevelingen types. Klanten negeren de aanbevelingen als ze steeds weer dezelfde producten voorstellen.

- Implementeer niet dezelfde aanbevelingen op de pagina met winkelwagentjes en de pagina met bevestiging van bestellingen. U kunt overwegen `Most Added to Cart` te gebruiken voor de pagina met het winkelwagentje en `Bought This, Bought That` voor de pagina met bevestiging van de bestelling.

- Houd uw site netjes. Implementeer niet meer dan drie aanbevolen eenheden op dezelfde pagina.

- Als uw winkel kleding verkoopt, kan de `More like this` aanbeveling genderspecifieke producten voorstellen die niet overeenkomen met het geslacht van het product dat wordt weergegeven. Overweeg dit soort aanbevelingen alleen te gebruiken voor niet-kledingcategorieën.

>[!NOTE]
>
>Voor meer informatie over de gebeurtenissen die in dit artikel worden beschreven, zie [&#x200B; storefront gebeurtenissen &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#product-recommendations) in de ontwikkelaarsdocumentatie.

## Gegevensvereisten en gedrag

De Aanbevelingen van het product is een gegeven-gedreven systeem dat zich op gedragsgegevens baseert die uit uw winkel worden verzameld. De kwaliteit en kwantiteit van aanbevelingen zijn afhankelijk van de hoeveelheid beschikbare gebeurtenisgegevens.

>[!IMPORTANT]
>
>De meeste soorten aanbevelingen vereisen voldoende gedragsgegevens (zoals productmeningen, toe:voegen-aan-kart acties, en aankopen) om zinvolle resultaten te produceren. Het systeem heeft doorgaans meerdere dagen actieve verkoopactiviteiten nodig om nauwkeurige aanbevelingen te kunnen maken. Zie [&#x200B; gereedheidsindicatoren &#x200B;](create.md#readiness-indicators) leren hoe de hulp van het plaatsverkeer om de diverse aanbevelingstypes te bevolken.

### Wat gebeurt er met ontoereikende gegevens?

Wanneer er niet genoeg gebeurtenisgegevens zijn om aanbevelingen te produceren, kan het systeem:

- Retourneer lege resultaten voor de aanbevolen eenheid.
- De trekker [&#x200B; reserveaanbevelingen &#x200B;](events.md#backup-recommendations), zoals het tonen van `Most viewed` producten wanneer de gepersonaliseerde aanbevelingen nog niet beschikbaar zijn.
- Vertoning minder producten dan [&#x200B; gevormd &#x200B;](create.md) in de aanbeveling eenheid.

## Gepersonaliseerd {#personalized}

Deze aanbevelingen typen producten op basis van de gedragsgeschiedenis van de specifieke klant op uw site aan. Bijvoorbeeld, als een verkoopster eerder naar een jasje doorzocht of een jasje op uw plaats kocht, nemen deze aanbevelingen hoofdzakelijk op waar zij weggingen en adviseren andere jasjes of gelijkaardige producten.

>[!NOTE]
>
>Persoonlijke aanbevelingen vereisen dat kopers een bekende gedragsgeschiedenis hebben. De nieuwe bezoekers of de kopers zonder voldoende interactiegeschiedenis zullen [&#x200B; reserveaanbevelingen &#x200B;](events.md#backup-recommendations) zien, zoals de Meeste bekeken producten tot zij genoeg gedragssignalen op uw plaats produceren.

| Type | Beschrijving |
|---|---|
| Aanbevolen voor u | Aanbevolen producten op basis van het huidige en vorige onsite gedrag van elke klant. Hier worden zeer relevante aanbevelingen weergegeven op basis van de bladeren- en aankoopgeschiedenis van de klant. Dit soort aanbevelingen is effectief op de homepage waar de meeste klanten hun reis op een plaats beginnen. Voor nieuwe kopers op uw site die geen signaal hebben gegenereerd om hun ervaring aan te passen, toont Adobe Commerce producten op basis van het meest bekeken aanbevolen type. Wanneer de verkoopster begint te communiceren met de producten op de site, worden de aanbevolen producten echter in real-time aangepast aan hun gedrag.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/><br/>**Voorgestelde etiketten:**<br/> - enkel voor u <br/> - geadviseerd voor u <br/> - Geïnspireerd door uw het winkelen tendensen |
| Onlangs bekeken | De producten van vertoningen onlangs bekeken door de verkoopster, die op browser geschiedenis wordt gebaseerd. Verwijderde producten worden door de aanbevolen eenheid verwijderd. De aanbevolen eenheid wordt niet weergegeven als er geen browsergeschiedenis is of als er onvoldoende geschiedenis is wanneer filterregels worden toegepast. Als de resultaten minder producten bevatten dan worden gevormd, toont de aanbeveling eenheid slechts de teruggekeerde producten.<br/><br/>**waar gebruikt:**<br/> - Homepage <br/> - Categorie <br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - onlangs bekeken <br/> - neem een andere blik |

## Crosssells en up-sells {#crossup}

Deze soorten aanbevelingen zijn sociaal-veilig, zodat kopers kunnen vinden wat anderen leuk vonden of door producten gestuurd om ze te helpen andere, vergelijkbare producten te vinden. De aanbevolen producten vormen vaak een aanvulling op het geselecteerde product.

>[!NOTE]
>
>&quot;bekeken dit, bekeken dat&quot;, &quot;bekeken dit, kocht dat&quot;, en &quot;kocht dit, kocht dat&quot;de aanbevelingstypes niet een eenvoudig-voorvalmetrisch maar eerder een verfijnd samenwerkings-filtrerend algoritme gebruiken dat *interessante gelijkenissen* zoekt die niet naar populaire producten worden scheefgetrokken. De gegevens die worden gebruikt om deze aanbevelingen te informeren zijn gebaseerd op het geaggregeerde gedrag van de verkoper dat uit veelvoudige zittingen op uw plaats wordt afgeleid. De gegevens zijn niet gebaseerd op verkoopgedrag dat is afgeleid van één exemplaar tijdens de sessie op uw site. Deze aanbevelingen helpen klanten die aangrenzende producten vinden die niet duidelijk aan paar met het momenteel bekeken product zouden kunnen zijn.
>
>Deze soorten aanbevelingen vereisen substantiële gegevens over productoverschrijdende interactie om zinvolle correlaties te identificeren. Winkels met een beperkte diversiteit aan productcatalogi of een laag verkeer kunnen minder aanbevelingen zien totdat voldoende gedragspatronen optreden.

| Type | Beschrijving |
|---|---|
| Bekeken dit, gezien dat | Aanbevolen producten die kopers vaker onevenredig weergeven met het product dat momenteel wordt weergegeven.<br/><br/>**waar gebruikt:**<br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Klanten die dit product ook bekeken (PDP) bekeken |
| Bekijk dit, kocht dat | Aanbevolen producten die kopers vaker onevenredig kunnen kopen nadat ze het huidige product hebben bekeken. Dit type helpt kopers te helpen producten te ontdekken die ze anders niet hadden opgemerkt.<br/><br/>**waar gebruikt:**<br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Klanten die dit uiteindelijk bekeken <br/> - Klanten kochten <br/> - wat anderen kopen na het bekijken van dit product? |
| Dit gekocht | Aanbevolen producten die kopers vaker onevenredig veel kopen bij het product dat momenteel wordt weergegeven. Bij dit type worden zeer relevante producten weergegeven die kopers aan hun winkelwagen kunnen toevoegen door samen te voegen wat andere kopers met het huidige product hebben gekocht.<br/><br/>**waar gebruikt:**<br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - krijg alles dat u nodig hebt <br/> - vergeet niet deze <br/> - vaak samen gekocht |
| Meer als dit | Aanbevelt producten die op gelijkaardige meta-gegevens zoals naam, beschrijving, categorietoewijzing, en attributen worden gebaseerd. Door de kenmerken te evalueren voor de producten die worden weergegeven, beveelt dit type vergelijkbare producten in dezelfde categorie aan. Als een winkelier bijvoorbeeld door yoga-mats bladert, wordt u aangeraden andere producten uit de apparatencategorie te gebruiken. Omdat in dit soort aanbevelingen geen onderscheid wordt gemaakt tussen genders, wordt het niet aanbevolen voor kleding, mode of andere geslachtsspecifieke verticalen.<br/><br/>**waar gebruikt:**<br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Meer producten zoals dit <br/> - Gelijkaardig aan dit |
| [&#x200B; Visuele gelijkenis &#x200B;](#visualsim) | Hiermee kunt u vergelijkbare producten aanbevelen als het product dat u bekijkt. Dit soort aanbevelingen is vooral handig als afbeeldingen en visuele aspecten van producten belangrijk zijn voor de boodschappenervaring. |

## Populariteit {#popularity}

Deze aanbevelingen typen producten aan die het populairst of het trending binnen de laatste zeven dagen zijn.

>[!NOTE]
>
>Op populariteit-gebaseerde aanbevelingen vereisen voldoende gebeurtenisgegevens van uw storefront. Als uw winkel nieuw is of weinig verkeer heeft, kunnen deze aanbevelingen beperkte resultaten of geen resultaten opleveren totdat er voldoende gedragsgegevens zijn verzameld. Controleer uw [&#x200B; indicator van de gegevensbereidheid &#x200B;](workspace.md) om optimale prestaties te verzekeren.

| Type | Beschrijving |
|---|---|
| Meest bekeken | Aanbevolen producten die het meest werden bekeken door het aantal sessies te tellen waarop een weergaveactie in de laatste zeven dagen plaatsvond.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**stelde etiketten voor:**<br/> - het populairste <br/> - het Trending <br/> - Bevolkt nu <br/> - Onlangs populaire <br/> - de Populaire producten die door dit product (PDP) worden geïnspireerd <br/> - Topverkopers |
| Meest aangeschaft | Aanbevolen producten die het meest worden aangeschaft door kopers in de afgelopen zeven dagen.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**stelde etiketten voor:**<br/> - het populairste <br/> - het Trending <br/> - Bevolkt nu <br/> - Onlangs populaire <br/> - de Populaire producten die door dit product (PDP) worden geïnspireerd <br/> - Topverkopers |
| Meest toegevoegd aan winkelwagentje | Aanbevolen producten die in de afgelopen zeven dagen het vaakst door kopers aan winkelwagentjes worden toegevoegd. Dit soort aanbevelingen kan op alle pagina&#39;s worden gebruikt.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**stelde etiketten voor:**<br/> - het populairste <br/> - het Trending <br/> - Bevolkt nu <br/> - Onlangs populaire <br/> - de Populaire producten die door dit product (PDP) worden geïnspireerd <br/> - Topverkopers |
| Trend | Aanbevolen producten op basis van de recente dynamiek van de populariteit van een product op uw site.<br/><br/> Adobe Sensei voegt het doorbladeren en koopgegevens over uw plaats samen om te bepalen en te rangschikken welke producten het meest recent met uw kopers populair zijn. Omdat Trending de recente productdynamiek analyseert, is het een efficiënt advisetype voor catalogi die een hoge omzet hebben. Als uw catalogus statisch is, is deze wellicht minder handig, tenzij de winkelpatronen van uw publiek sterk variëren.<br/><br/> wanneer gebruikt op de homepage, beveelt het Trending producten aan die onlangs over de volledige plaats populair zijn. Trending geeft geen producten weer die altijd populair zijn, maar producten die onlangs populair zijn geworden. Als u bijvoorbeeld een campagne voor het in de handel brengen van e-mail hebt om bepaalde producten te promoten, vergroot de populariteit van de e-mail de kans dat de geprezen producten als trending worden ingedeeld.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Trending <br/> - nu Trending <br/> - onlangs trending <br/> - Hete producten <br/> - het Trending verwante producten (PDP) |

## Hoge prestaties {#highperf}

In deze aanbevolen typen worden producten aanbevolen die de beste prestaties leveren op basis van succescriteria zoals &#39;add-to-cart&#39; of conversiesnelheden.

>[!NOTE]
>
>De goed presterende aanbevelingen typen baseren zich op omzettingsgegevens (aankopen en toe:voegen-aan-kart acties). Nieuwe opslagplaatsen of opslagplaatsen met een laag omzettingsvolume moeten mogelijk gegevens verzamelen over 7-14 dagen voordat deze aanbevelingen effectief worden.

| Type | Beschrijving |
|---|---|
| Omzetten van aankoop bekijken | Aanbevolen producten met de hoogste weergave-naar-aankoop conversiesnelheid. Van alle winkelsessies die een productweergave registreerden, wat is het percentage dat uiteindelijk een aankoop door de winkelier registreerde.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Top verkopers <br/> - Populaire producten <br/> - u zou in geinteresseerd kunnen zijn |
| Omzetten naar winkelwagentje | Hiermee worden producten met de hoogste conversiesnelheid voor weergave naar winkelwagentje aanbevolen. Van alle winkelzittingen die een productmening registreerden, wat is het aandeel dat uiteindelijk registreerde en aan karretje toevoegde door de verkoopster.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Belangrijkste verkopers <br/> - Populaire producten <br/> - u zou in geinteresseerd kunnen zijn |
| Meest aangeschaft | Deze aanbeveling wordt vaak &#39;&#39;Top Sellers&#39;&#39; genoemd en telt het aantal sessies waarvoor een plaatsordeactie is uitgevoerd in de laatste zeven dagen. Dit soort aanbevelingen kan op alle pagina&#39;s worden gebruikt.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**stelde etiketten voor:**<br/> - het populairste <br/> - het Trending <br/> - Bevolkt nu <br/> - Onlangs populaire <br/> - de Populaire producten die door dit product (PDP) worden geïnspireerd <br/> - Topverkopers |
| Meest toegevoegd aan winkelwagentje | Aanbevolen producten die in de afgelopen zeven dagen het vaakst door kopers aan winkelwagentjes worden toegevoegd. Dit soort aanbevelingen kan op alle pagina&#39;s worden gebruikt.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**stelde etiketten voor:**<br/> - het populairste <br/> - het Trending <br/> - Bevolkt nu <br/> - Onlangs populaire <br/> - de Populaire producten die door dit product (PDP) worden geïnspireerd <br/> - Topverkopers |

## Visuele gelijkenis {#visualsim}

Het _Visuele gelijkenis_ aanbevelingen type adviseert gelijkaardige het kijken producten aan het product dat wordt bekeken. Dit soort aanbevelingen is vooral handig wanneer afbeeldingen en visuele aspecten van de producten belangrijke onderdelen zijn van de boodschappenervaring.

### Hoe werkt het

Het _Visuele gelijkenis_ aanbevelingen type biedt aanbevelingen voor andere producten in uw catalogus aan die een visuele gelijkenis met de beelden hebben die momenteel worden bekeken. Visuele gelijkenis omvat aspecten zoals:

- Kleur
- Vorm
- Grootte
- Structuur
- Materiaal
- Stijl

Adobe Sensei gebruikt AI om de beelden in uw catalogus te verwerken en te analyseren en attributen te bouwen die worden gebruikt om visuele gelijkenissen te bepalen.

>[!NOTE]
>
> Als u dit type aanbevelingen test in een niet-productieomgeving, moet u ervoor zorgen dat de URL&#39;s van de afbeelding openbaar toegankelijk zijn.

>[!NOTE]
>
> Productafbeeldingen moeten momenteel 10 MB of minder groot zijn.

Omdat dit aanbevelingen type niet op de meeste catalogi van toepassing is, wordt het niet toegelaten door gebrek. U moet dit aanbevelingstype uitdrukkelijk toelaten.

### Aanbevolen type voor visuele gelijkenis inschakelen

>[!NOTE]
>
> Het _Visuele gelijkenis_ aanbevelingen type is beschikbaar wanneer u [&#x200B; &#x200B;](install-configure.md) het als facultatieve module installeert.

1. Op _Admin_ sidebar, ga **de Marketing** > _Bevorderingen_ > **Aanbevelingen van het Product** om het _dashboard van de Aanbevelingen van het Product_ te tonen.

1. Klik **Montages** (tandwielpictogram) om de _pagina van Montages_ te tonen.

1. In de _Visuele sectie van Aanbevelingen_, selecteer **toelaten Visuele Aanbevelingen**.

1. Klik **sparen veranderingen** wanneer u wordt gebeëindigd.

   [&#x200B; creeer Nieuwe Aanbeveling &#x200B;](create.md) pagina toont nu **Visuele gelijkenis** als verkiesbaar aanbevelingstype wanneer het paginatype **Detail van het Product** is.

Nadat u visuele aanbevelingen hebt ingeschakeld, start Adobe Sensei de afbeeldingsverwerking. Hoe lang dit duurt, is afhankelijk van de grootte van de catalogus.

### Indien gebruikt

- Productdetails

### Voorgestelde winkellabels

- U kunt ook
- We hebben andere producten gevonden die je wellicht aanspreken
- Geïnspireerd door deze stijl

### Voorbeeld

Het volgende beeld toont de pagina van het productdetail voor het _Controle van de Klamber_:

![&#x200B; Klambercontrole &#x200B;](assets/visual-sim-pdp.png)

Het volgende toont de _Visuele gelijkenis_ aanbevelingseenheid voor _Controle van de Klamber_:

![&#x200B; Visuele gelijkenis eenheid &#x200B;](assets/visual-sim-unit.png)
