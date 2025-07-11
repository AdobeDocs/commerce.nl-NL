---
title: Typen aanbevelingen
description: Leer meer over de aanbevelingen die u op verschillende pagina's op uw site kunt implementeren.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 3020386cd051b4453ed6b90d2c694a5bb31dfb24
workflow-type: tm+mt
source-wordcount: '1295'
ht-degree: 0%

---

# Typen aanbevelingen

Adobe Commerce Optimizer biedt een groot aantal aanbevelingen die u op verschillende pagina&#39;s op uw site kunt implementeren. Alle aanbevelingstypen zijn gebaseerd op gegevens. Ze worden aangedreven door gedragsgegevens, productkenmerkgegevens en meetgegevens. Ter referentie worden de aanbevolen typen als volgt gegroepeerd:

- [Gepersonaliseerd](#personalized)
- [Crosssells en up-sells](#crossup)
- [Populariteit](#popularity)
- [Krachtig](#highperf)

>[!NOTE]
>
>Voor meer informatie over de gebeurtenissen die in dit artikel worden beschreven, zie [ gebeurtenissen ](../../setup/events/overview.md).

## Gepersonaliseerd {#personalized}

Deze aanbevelingen typen producten op basis van de gedragsgeschiedenis van de specifieke klant op uw site aan. Bijvoorbeeld, als een verkoopster eerder naar een jasje doorzocht of een jasje op uw plaats kocht, nemen deze aanbevelingen hoofdzakelijk op waar zij weggingen en adviseren andere jasjes of gelijkaardige producten.

| Type | Beschrijving |
|---|---|
| Aanbevolen voor u | Aanbevolen producten op basis van het huidige en vorige onsite gedrag van elke klant. Hier worden zeer relevante aanbevelingen weergegeven op basis van de bladeren- en aankoopgeschiedenis van de klant. Dit soort aanbevelingen is effectief op de homepage waar de meeste klanten hun reis op een plaats beginnen. Voor nieuwe kopers op uw site die geen signaal hebben gegenereerd om hun ervaring aan te passen, toont Adobe Commerce producten op basis van het meest bekeken aanbevolen type. Wanneer de verkoopster begint te communiceren met de producten op de site, worden de aanbevolen producten echter in real-time aangepast aan hun gedrag.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/><br/>**Voorgestelde etiketten:**<br/> - enkel voor u <br/> - geadviseerd voor u <br/> - Geïnspireerd door uw het winkelen tendensen |
| Onlangs bekeken | De producten van vertoningen onlangs bekeken door de verkoopster, die op browser geschiedenis wordt gebaseerd. Verwijderde producten worden door de aanbevolen eenheid verwijderd. De aanbevolen eenheid wordt niet weergegeven als er geen browsergeschiedenis is of als er onvoldoende geschiedenis is wanneer filterregels worden toegepast. Als de resultaten minder producten bevatten dan worden gevormd, toont de aanbeveling eenheid slechts de teruggekeerde producten.<br/><br/>**waar gebruikt:**<br/> - Homepage <br/> - Categorie <br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - onlangs bekeken <br/> - neem een andere blik |

## Crosssells en up-sells {#crossup}

Deze soorten aanbevelingen zijn sociaal-veilig, zodat kopers kunnen vinden wat anderen leuk vonden of door producten gestuurd om ze te helpen andere, vergelijkbare producten te vinden. De aanbevolen producten vormen vaak een aanvulling op het geselecteerde product.

>[!NOTE]
>
>&quot;bekeken dit, bekeken dat&quot;, &quot;bekeken dit, kocht dat&quot;, en &quot;kocht dit, kocht dat&quot;de aanbevelingstypes niet een eenvoudig-voorvalmetrisch maar eerder een verfijnd samenwerkings-filtrerend algoritme gebruiken dat *interessante gelijkenissen* zoekt die niet naar populaire producten worden scheefgetrokken. De gegevens die worden gebruikt om deze aanbevelingen te informeren zijn gebaseerd op het geaggregeerde gedrag van de verkoper dat uit veelvoudige zittingen op uw plaats wordt afgeleid. De gegevens zijn niet gebaseerd op verkoopgedrag dat is afgeleid van één exemplaar tijdens de sessie op uw site. Deze aanbevelingen helpen klanten die aangrenzende producten vinden die niet duidelijk aan paar met het momenteel bekeken product zouden kunnen zijn.

| Type | Beschrijving |
|---|---|
| Bekeken dit, gezien dat | Aanbevolen producten die kopers vaker onevenredig weergeven met het product dat momenteel wordt weergegeven.<br/><br/>**waar gebruikt:**<br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Klanten die dit product ook bekeken (PDP) bekeken |
| Bekijk dit, kocht dat | Aanbevolen producten die kopers vaker onevenredig kunnen kopen nadat ze het huidige product hebben bekeken. Dit type helpt kopers te helpen producten te ontdekken die ze anders niet hadden opgemerkt.<br/><br/>**waar gebruikt:**<br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Klanten die dit uiteindelijk bekeken <br/> - Klanten kochten <br/> - wat anderen kopen na het bekijken van dit product? |
| Dit gekocht | Aanbevolen producten die kopers vaker onevenredig veel kopen bij het product dat momenteel wordt weergegeven. Bij dit type worden zeer relevante producten weergegeven die kopers aan hun winkelwagen kunnen toevoegen door samen te voegen wat andere kopers met het huidige product hebben gekocht.<br/><br/>**waar gebruikt:**<br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - krijg alles dat u nodig hebt <br/> - vergeet niet deze <br/> - vaak samen gekocht |
| Meer als dit | Aanbevelt producten die op gelijkaardige meta-gegevens zoals naam, beschrijving, categorietoewijzing, en attributen worden gebaseerd. Door de kenmerken te evalueren voor de producten die worden weergegeven, beveelt dit type vergelijkbare producten in dezelfde categorie aan. Als een winkelier bijvoorbeeld door yoga-mats bladert, wordt u aangeraden andere producten uit de apparatencategorie te gebruiken. Omdat in dit soort aanbevelingen geen onderscheid wordt gemaakt tussen genders, wordt het niet aanbevolen voor kleding, mode of andere geslachtsspecifieke verticalen.<br/><br/>**waar gebruikt:**<br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Meer producten zoals dit <br/> - Gelijkaardig aan dit |

## Populariteit {#popularity}

Deze aanbevelingen typen producten aan die het populairst of het trending binnen de laatste zeven dagen zijn.

| Type | Beschrijving |
|---|---|
| Meest bekeken | Aanbevolen producten die het meest werden bekeken door het aantal sessies te tellen waarop een weergaveactie in de laatste zeven dagen plaatsvond.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**stelde etiketten voor:**<br/> - het populairste <br/> - het Trending <br/> - Bevolkt nu <br/> - Onlangs populaire <br/> - de Populaire producten die door dit product (PDP) worden geïnspireerd <br/> - Topverkopers |
| Meest aangeschaft | Aanbevolen producten die het meest worden aangeschaft door kopers in de afgelopen zeven dagen.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**stelde etiketten voor:**<br/> - het populairste <br/> - het Trending <br/> - Bevolkt nu <br/> - Onlangs populaire <br/> - de Populaire producten die door dit product (PDP) worden geïnspireerd <br/> - Topverkopers |
| Meest toegevoegd aan winkelwagentje | Aanbevolen producten die in de afgelopen zeven dagen het vaakst door kopers aan winkelwagentjes worden toegevoegd. Dit soort aanbevelingen kan op alle pagina&#39;s worden gebruikt.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**stelde etiketten voor:**<br/> - het populairste <br/> - het Trending <br/> - Bevolkt nu <br/> - Onlangs populaire <br/> - de Populaire producten die door dit product (PDP) worden geïnspireerd <br/> - Topverkopers |
| Trend | Aanbevolen producten op basis van de recente dynamiek van de populariteit van een product op uw site.<br/><br/> Adobe Sensei voegt het doorbladeren en koopgegevens over uw plaats samen om te bepalen en te rangschikken welke producten het meest recent met uw kopers populair zijn. Omdat Trending de recente productdynamiek analyseert, is het een efficiënt advisetype voor catalogi die een hoge omzet hebben. Als uw catalogus statisch is, is deze wellicht minder handig, tenzij de winkelpatronen van uw publiek sterk variëren.<br/><br/> wanneer gebruikt op de homepage, beveelt het Trending producten aan die onlangs over de volledige plaats populair zijn. Trending geeft geen producten weer die altijd populair zijn, maar producten die onlangs populair zijn geworden. Als u bijvoorbeeld een campagne voor het in de handel brengen van e-mail hebt om bepaalde producten te promoten, vergroot de populariteit van de e-mail de kans dat de geprezen producten als trending worden ingedeeld.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Trending <br/> - nu Trending <br/> - onlangs trending <br/> - Hete producten <br/> - het Trending verwante producten (PDP) |

## Hoge prestaties {#highperf}

In deze aanbevolen typen worden producten aanbevolen die de beste prestaties leveren op basis van succescriteria zoals &#39;add-to-cart&#39; of conversiesnelheden.

| Type | Beschrijving |
|---|---|
| Omzetten van aankoop bekijken | Aanbevolen producten met de hoogste weergave-naar-aankoop conversiesnelheid. Van alle winkelsessies die een productweergave registreerden, wat is het percentage dat uiteindelijk een aankoop door de winkelier registreerde.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Top verkopers <br/> - Populaire producten <br/> - u zou in geinteresseerd kunnen zijn |
| Omzetten naar winkelwagentje | Hiermee worden producten met de hoogste conversiesnelheid voor weergave naar winkelwagentje aanbevolen. Van alle winkelzittingen die een productmening registreerden, wat is het aandeel dat uiteindelijk registreerde en aan karretje toevoegde door de verkoopster.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kar <br/> - Bevestiging <br/><br/>**Voorgestelde etiketten:**<br/> - Belangrijkste verkopers <br/> - Populaire producten <br/> - u zou in geinteresseerd kunnen zijn |
| Meest aangeschaft | Deze aanbeveling wordt vaak &#39;&#39;Top Sellers&#39;&#39; genoemd en telt het aantal sessies waarvoor een plaatsordeactie is uitgevoerd in de laatste zeven dagen. Dit soort aanbevelingen kan op alle pagina&#39;s worden gebruikt.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**stelde etiketten voor:**<br/> - het populairste <br/> - het Trending <br/> - Bevolkt nu <br/> - Onlangs populaire <br/> - de Populaire producten die door dit product (PDP) worden geïnspireerd <br/> - Topverkopers |
| Meest toegevoegd aan winkelwagentje | Aanbevolen producten die in de afgelopen zeven dagen het vaakst door kopers aan winkelwagentjes worden toegevoegd. Dit soort aanbevelingen kan op alle pagina&#39;s worden gebruikt.<br/><br/>**waar gebruikt:**<br/> - de pagina van het Huis <br/> - Categorie <br/> - het detail van het Product <br/> - Kaart <br/> - Bevestiging <br/><br/>**stelde etiketten voor:**<br/> - het populairste <br/> - het Trending <br/> - Bevolkt nu <br/> - Onlangs populaire <br/> - de Populaire producten die door dit product (PDP) worden geïnspireerd <br/> - Topverkopers |
