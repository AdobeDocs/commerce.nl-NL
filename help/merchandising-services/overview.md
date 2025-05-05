---
title: '[!DNL Merchandising Services] overzicht'
description: Leer hoe  [!DNL Merchandising Services]  voor Adobe Commerce u helpt opstelling uw catalogus om uw bedrijfsmodel en go-to-market strategie aan te passen
recommendations: noCatalog
exl-id: afa7c148-10fb-4161-8bcc-13084f85c42c
source-git-commit: 31270ceac79977b6ecdf8043b0c162031d129de7
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 0%

---

# [!DNL Merchandising Services] overzicht

Een productcatalogus is van essentieel belang voor online winkelervaring, zodat klanten kunnen bladeren, zoeken en aankopen kunnen doen. Voor een efficiënte werking moet een productcatalogus de bedrijfsstructuur van de onderneming nauw weerspiegelen. De ondernemingen moeten vaak producten tegen verschillende prijzen verkopen die op geografische markt, distributiekanaal, klantensegment, en andere variabelen worden gebaseerd. Om dit aan te kunnen, moet een e-commerce-platform een flexibel catalogusgegevensmodel bieden waarmee bedrijven variaties van hun catalogus kunnen produceren die zijn aangepast aan deze scenario&#39;s. Adobe lost deze behoeften op door de Diensten van de Verkoop aan te bieden die door Kanalen en Beleid worden aangedreven. Merchandising Services biedt bouwstenen die handelaren kunnen gebruiken om catalogi op schaal te maken en te beheren. Dit laat ondernemingen toe om catalogi te vormen die zich op hun bedrijfsstructuur en go-to-market strategieën richten.

Op een hoog niveau, met de Diensten van het Merchandising kunt u:

- Gebruik één basiscatalogus voor al uw bedrijfsbehoeften. Schaal uw catalogus snel over nieuwe merken, markten, zaken-eenheden, go-aan-markt kanalen, en klantensegmenten zonder de behoefte aan volledige re-architectuur. Dit elimineert gegevensduplicatie en plaatst uw e-commerceplatform voor hoge operationele efficiency.
- Ontgrendel catalogussynchronisatie en lever de juiste inhoud door uw productcatalogus te ontwerpen die uw bedrijf, inclusief producten, klanten, prijzen en distributie, weerspiegelt.
- Snel catalogusgegevens opnemen en bijwerken en snel de updates leveren aan de winkel voor uw promoties en campagnebehoeften.
- Maak perfecte vuurtorscores met gebruiksklare, bliksemsnelle UI-componenten aangedreven door Edge Delivery Services voor naadloze productnavigatie en aanbevelingen.
- Ga een moderne composable architectuur die de uitbreidingsarchitectuur van Adobe gebruiken ([ App Builder ](https://experienceleague.adobe.com/nl/playlists/commerce-get-started-app-builder-development)) om productgegevens en machtshoofdloze handelsafspraken in te voeren gebruikend Adobe [ API Net ](https://experienceleague.adobe.com/nl/playlists/commerce-get-started-app-builder-and-api-mesh).

>[!INFO]
>
>Om over APIs te leren beschikbaar in het Merchandising van de Diensten die door Kanalen en Beleid worden aangedreven, zie de [ documentatie van de ontwikkelaar ](https://developer-stage.adobe.com/commerce/services/composable-catalog).

## Architectuur

Merchandising Services powered by Channels and Policies is een zeer schaalbaar, flexibel model voor catalogusgegevens dat eenvoudige multibrand, multi-business unit en meertalige gebruiksscenario&#39;s opent. Dit model vervangt het gebruik van het klassieke Adobe Commerce-productbereik (website, winkel, opslag) door nieuwe Merchandising Services-productbereik (kanaal, beleid en landinstelling).

Het volgende diagram verstrekt een mening op hoog niveau van het Kader van de Verkoop.

![[!DNL Merchandising Services] Architectuur ](assets/merchandising-svcs-architecture.png)

Bovenaan in dit diagram worden catalogusgegevens (PIM, ERP, enzovoort) opgenomen in het framework Services voor handelsdoeleinden. Deze catalogusgegevens bevatten SKU&#39;s. Elke SKU bevat werkingsgebieddetails (scène) en productattributen, die aan het nieuwe het productwerkingsgebied van de Diensten van de Verkoop in kaart brengen (kanalen, beleid, en scène).

Wanneer al dit gegeven in het Merchandising kader wordt opgenomen, is het resultaat een nieuwe verenigde basiscatalogus die in de de gegevenspijpleiding van de Dienst van de Catalogus beschikbaar is. In het volgende deel van het diagram ziet u meerdere kanalen. Elk kanaal vertegenwoordigt een bedrijfseenheid. Bijvoorbeeld, *de kleinhandel van Texas*, *de kleinhandel van Texas seizoensgebonden*, etc. Zoals u op het diagram kunt zien, kunnen de scènes, het beleid, en de prijsboeken allen over kanalen worden gedeeld. &#x200B;

Tot slot toont het diagram hoe deze verschillende catalogusgegevens kunnen worden gevonden op verschillende locaties, zoals een Edge Delivery Services-winkel, een markt, een advertentiekanaal, een aangepaste microwinkel enzovoort.

Leren hoe u uw catalogusgegevens in het Merchandising gebruiken van de opname API van catalogusgegevens kunt opnemen en hoe te opstelling uw scènes, beleid, en prijsboeken gebruikend het catalogusbeheer en de regels API, zie de [ documentatie van de ontwikkelaar ](https://developer-stage.adobe.com/commerce/services/composable-catalog/).

Meer over de concepten leren die omhoog de Diensten van de Verkoop vormen, zie de volgende secties.

## Beheer van productcatalogi

Het beheer van productcatalogi omvat twee verschillende aspecten: productgegevens en productcontext. De handelsdiensten eerbiedigen de scheiding van deze taken, die voor elk een onafhankelijk beheer bieden.

- **gegevens van het Product** - Welk product wordt verkocht en tegen welke prijs?
- **context van het Product** - wie verkoopt aan wie en waar?

![[!DNL Merchandising Services] aspects ](assets/merchandising-svcs-parts.png)

### Productgegevens

De productgegevens omvatten de volgende typen:

- **Producten** - Individuele SKUs of inzamelingen van SKUs die fysieke goederen of immateriële diensten met attributen vertegenwoordigen die het product met inbegrip van beschrijving, gewicht, grootte, afmetingen, en meer vertegenwoordigen. De attributen specificeren ook het kanaal en beleidswerkingsgebied voor SKU. De producten kunnen in diverse producttypes zoals eenvoudig, configureerbaar, bundel, bundel van bundels, abonnementen, en meer worden gegroepeerd.
- **Meta-gegevens** - de meta-gegevens van het attribuut van het Product bepaalt en beheert hoe de productattributen op de winkel in productlijsten, detailpagina&#39;s, onderzoeksresultaten, etc. worden getoond. Metagegevens definiëren ook hoe productkenmerken worden gebruikt bij zoeken, sorteren, filteren, zoeken, dikten enzovoort.
- **de boeken en de prijzen van de Prijs** - bepaalt de het verkopen prijzen van producten. In de Diensten van de Verkoop, worden een product SKU en de prijs losgekoppeld, vandaar bent u gemachtigd om veelvoudige prijsboeken voor één enkele SKU te bepalen. Door de prijzen van SKU los te koppelen, kunt u werkingsgebiedspecifieke prijzen over verschillende klantenlijsten, bedrijfseenheden, en geografische gebieden ontgrendelen. U kunt reguliere prijzen en gedisconteerde prijzen definiëren en dit alles op schaal beheren.
- **Assets** - Artefacten verbonden aan producten, zoals beelden, video&#39;s, PDFs of andere dossiertypes (toekomstige roadmap).

### Contextbeheer van producten

Het contextbeheer van producten heeft betrekking op de volgende aspecten:

- **Kanaal** - het kanaal van de Distributie bepaalt de weg die de zaken producten door willen verkopen. Een kanaal is de abstractie op het hoogste niveau die landinstellingen en beleid omvat.
   - Voorbeeld: dealers voor de auto-industrie. Dochterondernemingen voor multibrand-conglomeraten. productielocatie voor leveranciers.
- **Beleid** - de toegangsfilter van Gegevens die u machtigt om de juiste inhoud aan de juiste bestemming te leveren. Met dit concept zijn mogelijkheden voor catalogussynchronisatie mogelijk.
   - Voorbeeld: fysieke winkels, marketingplaatsen, advertentiepijpleidingen (Google, Facebook, Instagram)
- **Reikwijdte** - Vertegenwoordigt de taal (scène) voor catalogi, bijvoorbeeld `en-US`. Het bereik wordt ingesteld op SKU-niveau tijdens het opnemen van catalogusgegevens.

Tijdens het opnemen en bijwerken van productgegevens, bevat SKU de details van werkingsgebied en attributen (de attributenkaart aan kanalen en beleid). Deze bepalen de herkenningstekens van de productcontext waartot SKU behoort:

![[!DNL Merchandising Services] Product-context-id&#39;s ](assets/merchandising-svcs-product-id.png)

In het bovenstaande beeld, verstrekt elke SKU:

- &#x200B;
   - Landinstelling: verplicht &#x200B;
- Productkenmerken
   - De kenmerken van het product worden gebruikt om aan de relevante kanalen en het beleid in kaart te brengen &#x200B;
   - Voorbeeld: als autofabrikant kunt u een kanaal- en beleidscombinatie voor productkenmerken maken: (1) Handelaars (2) Auto merken. &#x200B;
- Prijzen en toegewezen prijsnoteringen
   - Elke SKU kan veelvoudige prijzen hebben die gebruikend veelvoudige prijsboeken worden bepaald.
   - Voorbeeld: je biedt werknemers een lagere normale prijs voor auto-onderdelen met een extra korting van 25%. Je biedt VIP-klanten een hogere normale prijs met een korting van 10%. De de prijsinformatie van productSKU zorgt ervoor dat de juiste prijs voor elk klantensegment wordt getoond.

De kanaal en beleidsdefinities worden gecreeerd gebruikend specifieke APIs:

![[!DNL Merchandising Services] Toewijzing kanaal, beleid en bereik ](assets/merchandising-svcs-scope-map.png)

- **Reikwijdte** (scène) - plaatste op een niveau van SKU tijdens het opnemen van productgegevens. &#x200B;
- **Kanaal** - Begeleiding die gebruikend specifieke APIs wordt gecreeerd. &#x200B;
- **Beleid** - gecreeerde Definitie gebruikend specifieke APIs.

## Belangrijkste kenmerken

| Belangrijkste kenmerken | Voordeel |
|---|---|
| **Directe ingang van catalogusgegevens in de pijpleiding van de opslagdiensten van de catalogusdiensten**: Maak direct uw catalogusgegevens in de pijpleiding van de catalogusdienst voor de browser van de storefront en onderzoekslevenscyclus (de Pagina van de Vertoning van het Product, de Pagina van de Lijst van het Product, de Pagina van de Resultaten van het Onderzoek, etc.) | <ul><li>Dien rechtstreeks catalogusgegevens in de opslagservice-pijplijn in: Catalogusservice, Productdetectie (Live Search) en Productaanbevelingen. Met dit, kunt u catalogusupdates op schaal voor miljoenen SKUs leveren. Dit ontgrendelt tijdgevoelig grootschalig promotiebeheer. </li></ul> |
| **Nieuw gebied van het catalogusproduct**: Het kanaal, het beleid, en het werkingsgebied zijn nieuw productwerkingsgebied dat door de Diensten van de Verkoop wordt geïntroduceerd. Dit productbereik vervangt het bereik van de website-, opslag- en opslagweergave in de laag met winkelservices. [ leer meer ](#product-context-management). | <ul><li>Met het nieuwe bereik ontgrendelt Merchandising Services de mogelijkheid om met gemak en met behulp van één basiscatalogus geschaald uit te breiden naar multigeografie, multi-business unit, multibrand en meertalige gebruiksgevallen.</li><li>Elimineer gegevensredundantie in uw catalogusbeheer.</li></ul> |
| **Schaal aan tientallen miljoenen SKUs** | Catalogusbeheer op schaal ontgrendelen. Hier kunt u meer dan 200 MM SKUs met gemak opnemen en beheren. |
| **typesteun van het Product** | <ul><li>Eenvoudig, configureerbaar</li><li>Bundels en bundels (toekomstig stappenplan)</li><li>Abonnementen en abonnementen (toekomstig stappenplan)</li></ul> |
| **Hoofdloze handel** | <ul><li>Volledige ondersteuning voor headless commerce-implementaties via Catalog Service, Product Discovery (Live Search) en Product Recommendations API&#39;s.</li></ul> |
| **Moderne bliksemsnelle UI componenten** | <ul><li>UI-componentondersteuning voor productzoekopdrachten en productaanbevelingen.</li><li>De UI-componenten zijn uitbreidbaar en flexibel, zodat ze zowel door Adobe Edge Delivery Service als door andere storefront-implementatie kunnen worden gebruikt.</li></ul> |

## Welk type van koopman het meest van de Diensten van de Koophandel profiteert?

De volgende lijst benadrukt gemeenschappelijke uitdagingen verkopers ontmoeten en hoe de Diensten van de Verkoop die door Kanalen en Beleid worden aangedreven hen richt.

| Merchant type | Hoofdletters gebruiken | Opgeloste problemen |
|---|---|---|
| Multibrand conglomeraat | <ul><li>Zij verkopen verschillende merken</li><li>Ze verkopen in verschillende landen</li><li>Ze verkopen in verschillende talen</li></ul> | Gebruik één enkele basis verenigde catalogus en behaal operationele efficiency terwijl het uitbreiden aan verscheidene merken, geographies en talen. |
| Automobiel/fabricageconglomeraat | <ul><li>Hiermee verkoopt u auto- of computeronderdelen. De producten zijn hetzelfde voor alle klanten.</li><li>Verschillende dealers verkopen onderdelen aan klanten</li><li>Elke handelaar heeft zijn eigen prijzen, voorraad en verzendmethoden</li></ul> | Om verschillende scheepvaartintegraties te hebben, zou elke handelaar een afzonderlijke website moeten hebben. Maar afzonderlijke websites dwingen het typische model van catalogusgegevens om de gegevens te dupliceren. Dus als er 3000 dealers in de VS zijn, maakt een handelaar 3000 catalogusexemplaren, ook al wordt dezelfde catalogus door alle dealers gebruikt. Deze gegevensduplicatie heeft invloed op de prestatielimieten. Merchandising Services elimineert gegevensduplicatie. |
| Verpakkings-/logistiekbedrijf | <ul><li>Ze hebben verschillende verzendlocaties</li><li>Zij hebben een verschillende prijs voor elke klant</li><li>Hetzelfde product dat op twee locaties beschikbaar is voor twee klanten heeft 4 mogelijke prijzen</li></ul> | Ondanks het gebruik van klantgroepen om prijzen per klant te dekken, beschikt het typische model van catalogusgegevens niet over de capaciteit om prijs per plaats te beheren. Bovendien willen handelaren unieke zichtbaarheidsregels per locatie/website. Beheer van dergelijke complexe prijs- en zichtbaarheidsregels kan op schaal worden ontgrendeld met Merchandising Services. |

### Hoe verder?

- Samenvatting gegevens in het Merchandising van de Diensten die [ gegeven gebruiken API ](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/using-the-api/).
- Beheer uw catalogus en bepaal de kanalen, het beleid, en het werkingsgebied gebruikend [ catalogusbeheer API ](https://developer-stage.adobe.com/commerce/services/composable-catalog/admin/using-the-api/)
- [ voltooi een leerprogramma ](https://developer-stage.adobe.com/commerce/services/composable-catalog/merchandising-services-use-case/) dat toont hoe een bedrijf met één enkele basiscatalogus de Diensten APIs van de Verkoop kan gebruiken om productgegevens toe te voegen, catalogi te bepalen gebruikend projecties, en de catalogusgegevens voor vertoning in een headless storefront terug te winnen.
