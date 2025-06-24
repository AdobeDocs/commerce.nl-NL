---
title: Catalogusweergave
description: Leer hoe te om catalogusmeningen in  [!DNL Adobe Commerce Optimizer] tot stand te brengen en te beheren.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 553490762ef10e43ccce1654acec59aeb83bb5f9
workflow-type: tm+mt
source-wordcount: '1896'
ht-degree: 0%

---

# Catalogusweergave maken

[ de meningen van de Catalogus ](#catalog-views) helpen u uw kleinhandelsstructuur in zinvolle bedrijfsgroepen bepalen. Een catalogusweergave beïnvloedt de zichtbaarheid van het product door specifieke beleidsregels en filters toe te passen die bepalen welke producten op een winkel worden weergegeven. Dit beleid kan kenmerken zoals merk, model of onderdelencategorie bevatten, zodat alleen relevante producten zichtbaar zijn voor kopers die zijn gebaseerd op de configuratie van de catalogusweergave. Bovendien kunnen catalogusweergaven prijsboeken gebruiken om klantspecifieke prijzen weer te geven en de winkelervaring verder aan te passen. [ leer meer ](#catalog-views) over catalogusmeningen.

In deze sectie, creeert u een catalogusmening, selecteert a [ beleid ](policies.md), en a [ prijsboek ](pricebooks.md).

1. Op het linkermenu, ga naar _opstelling van de Opslag_ en klik **[!UICONTROL Catalog views]**.

1. Klik op **[!UICONTROL Create catalog view]** . &#x200B;

1. Voeg de details van de catalogusweergave toe:

   - **Naam** - ga de naam van de catalogusmening in. Bijvoorbeeld &#39;Celport&#39;. &#x200B;
   - **de bronnen van de Catalogus** - voeg de catalogusbron (scène) toe. Bijvoorbeeld &#39;en-US&#39;. Druk **ga** sleutel in.
   - **Beleid** - gebruik drop-down om het relevante beleid te selecteren. Bijvoorbeeld &#39;Merk&#39;, &#39;Model&#39;. &#x200B;Zorg ervoor u reeds [ een beleid ](policies.md) creeerde.

1. Selecteer het prijzenboek dat u aan de catalogusweergave wilt koppelen. Leer meer over [ prijsboeken ](pricebooks.md).

1. Klik op **[!UICONTROL Add]** om de catalogusweergave te maken met het gekoppelde prijzenboek en het gekoppelde beleid.

   Als de **[!UICONTROL Add]** knoop niet actief is, zorg ervoor dat de catalogusbron behoorlijk wordt toegevoegd door uw curseur op het gebied van de bronnen van de Catalogus te plaatsen en **te drukken gaat** binnen. &#x200B;

De pagina van de catalogusweergaven wordt bijgewerkt om de nieuwe catalogusweergave weer te geven. &#x200B;

Nadat u deze stappen hebt voltooid, is de nieuwe catalogusweergave geconfigureerd voor het weergeven van producten en prijzen op basis van de catalogusbronnen en het beleid dat u hebt geselecteerd.

## Catalogusweergaven

Een productcatalogus is van essentieel belang voor online winkelervaring, zodat klanten kunnen bladeren, zoeken en aankopen kunnen doen. Voor een efficiënte werking moet een productcatalogus de bedrijfsstructuur van de onderneming nauw weerspiegelen. Bedrijven moeten vaak producten tegen verschillende prijzen verkopen op basis van de geografische markt, de weergave van de distributiecatalogus, het klantensegment en andere variabelen. Om dit mogelijk te maken, moet een e-commerceplatform een flexibel catalogusgegevensmodel bieden waarmee bedrijven variaties van hun catalogus kunnen produceren die zijn aangepast aan deze scenario&#39;s. Adobe lost deze behoeften op door Merchandising Services aan te bieden die worden aangedreven door catalogusweergaven en -beleid. Merchandising Services biedt bouwstenen die handelaren kunnen gebruiken om catalogi op schaal te maken en te beheren. Dit laat ondernemingen toe om catalogi te vormen die zich op hun bedrijfsstructuur en go-to-market strategieën richten.

Op een hoog niveau, met de Diensten van het Merchandising kunt u:

- Gebruik één basiscatalogus voor al uw bedrijfsbehoeften. Schaal uw catalogus snel over nieuwe merken, markten, zaken-eenheden, gaan-aan-markt catalogusmeningen, en klantensegmenten zonder de behoefte aan volledige re-architectuur. Dit elimineert gegevensduplicatie en plaatst uw e-commerceplatform voor hoge operationele efficiency.
- Ontgrendel catalogussynchronisatie en lever de juiste inhoud door uw productcatalogus te ontwerpen die uw bedrijf, inclusief producten, klanten, prijzen en distributie, weerspiegelt.
- Snel catalogusgegevens opnemen en bijwerken en snel de updates leveren aan de winkel voor uw promoties en campagnebehoeften.
- Maak perfecte vuurtorscores met gebruiksklare, bliksemsnelle UI-componenten aangedreven door Edge Delivery Services voor naadloze productnavigatie en aanbevelingen.
- Ga een moderne composable architectuur die de uitbreidingsarchitectuur van Adobe gebruiken ([ App Builder ](https://experienceleague.adobe.com/en/playlists/commerce-get-started-app-builder-development)) om productgegevens en machtshoofdloze handelsafspraken in te voeren gebruikend Adobe [ API Net ](https://experienceleague.adobe.com/en/playlists/commerce-get-started-app-builder-and-api-mesh).

>[!INFO]
>
>Om over APIs te leren beschikbaar in het Merchandising van de Diensten die door de meningen en het Beleid van de Catalogus worden aangedreven, zie de [ documentatie van de ontwikkelaar ](https://developer-stage.adobe.com/commerce/services/composable-catalog).

## Architectuur

Merchandising Services aangedreven door catalogusweergaven en -beleid is een zeer schaalbaar, flexibel model voor catalogusgegevens dat eenvoudige multibrand, multi-business unit en meertalige gebruiksscenario&#39;s opent. Dit model vervangt het gebruik van de klassieke bronnen van de Adobe Commerce-productcatalogus (website, winkel, opslagvoorvertoning) door nieuwe bronnen uit de productcatalogus van de Services voor het in de handel brengen (catalogusweergave, beleid en landinstelling).

Het volgende diagram verstrekt een mening op hoog niveau van het Kader van de Verkoop.

![[!DNL Merchandising Services] Architectuur ](../assets/merchandising-svcs-architecture.png)

Bovenaan in dit diagram worden catalogusgegevens (PIM, ERP, enzovoort) opgenomen in het framework Services voor handelsdoeleinden. Deze catalogusgegevens bevatten SKU&#39;s. Elke SKU bevat de details van de catalogusbron (scène) en productattributen, die aan de nieuwe het productcatalogusbronnen van de Diensten van de Verkoop (catalogusmeningen, beleid, en scène) in kaart brengen.

Wanneer al dit gegeven in het Merchandising kader wordt opgenomen, is het resultaat een nieuwe verenigde basiscatalogus die in de de gegevenspijpleiding van de Dienst van de Catalogus beschikbaar is. In het volgende gedeelte van het diagram ziet u meerdere catalogusweergaven. Elke catalogusweergave vertegenwoordigt een bedrijfseenheid. Bijvoorbeeld, *de kleinhandel van Texas*, *de kleinhandel van Texas seizoensgebonden*, etc. Aangezien u kunt zien dat van het diagram, de scènes, het beleid, en de prijsboeken allen over catalogusmeningen kunnen worden gedeeld. &#x200B;

Tot slot toont het diagram hoe deze verschillende catalogusgegevens kunnen worden gevonden op verschillende locaties, zoals een Edge Delivery Services-winkel, een markt, een advertentiecatalogusweergave, een aangepaste microwinkel enzovoort.

Leren hoe u uw catalogusgegevens in het Merchandising gebruiken van de opname API van catalogusgegevens kunt opnemen en hoe te opstelling uw scènes, beleid, en prijsboeken gebruikend het catalogusbeheer en de regels API, zie de [ documentatie van de ontwikkelaar ](https://developer-stage.adobe.com/commerce/services/composable-catalog/).

Meer over de concepten leren die omhoog de Diensten van de Verkoop vormen, zie de volgende secties.

## Beheer van productcatalogi

Het beheer van productcatalogi omvat twee verschillende aspecten: productgegevens en productcontext. De handelsdiensten eerbiedigen de scheiding van deze taken, die voor elk een onafhankelijk beheer bieden.

- **gegevens van het Product** - Welk product wordt verkocht en tegen welke prijs?
- **context van het Product** - wie verkoopt aan wie en waar?

![[!DNL Merchandising Services] aspects ](../assets/merchandising-svcs-parts.png)

### Productgegevens

De productgegevens omvatten de volgende typen:

- **Producten** - Individuele SKUs of inzamelingen van SKUs die fysieke goederen of immateriële diensten met attributen vertegenwoordigen die het product met inbegrip van beschrijving, gewicht, grootte, afmetingen, en meer vertegenwoordigen. De attributen specificeren ook de catalogusmening en de bronnen van de beleidscatalogus voor SKU. De producten kunnen in diverse producttypes zoals eenvoudig, configureerbaar, bundel, bundel van bundels, abonnementen, en meer worden gegroepeerd.
- **Meta-gegevens** - de meta-gegevens van het attribuut van het Product bepaalt en beheert hoe de productattributen op de winkel in productlijsten, detailpagina&#39;s, onderzoeksresultaten, etc. worden getoond. Metagegevens definiëren ook hoe productkenmerken worden gebruikt bij zoeken, sorteren, filteren, zoeken, dikten enzovoort.
- **de boeken en de prijzen van de Prijs** - bepaalt de het verkopen prijzen van producten. In de Diensten van de Verkoop, worden een product SKU en de prijs losgekoppeld, vandaar bent u gemachtigd om veelvoudige prijsboeken voor één enkele SKU te bepalen. Door de prijzen van SKU te ontkoppelen, kunt u catalogusspecifieke prijzen over verschillende klanten, bedrijfseenheden, en geografische gebieden ontgrendelen. U kunt reguliere prijzen en gedisconteerde prijzen definiëren en dit alles op schaal beheren.
- **Assets** - Artefacten verbonden aan producten, zoals beelden, video&#39;s, PDFs of andere dossiertypes (toekomstige roadmap).

### Contextbeheer van producten

Het contextbeheer van producten heeft betrekking op de volgende aspecten:

- **catalogusmening** - de catalogusmening van de Distributie bepaalt de weg die de zaken producten door willen verkopen. Een catalogusweergave is de abstractie op het hoogste niveau waarbij landinstellingen en beleid worden ingekapseld.
   - Voorbeeld: dealers voor de auto-industrie. Dochterondernemingen voor multibrand-conglomeraten. productielocatie voor leveranciers.
- **Beleid** - de toegangsfilter van Gegevens die u machtigt om de juiste inhoud aan de juiste bestemming te leveren. Met dit concept zijn mogelijkheden voor catalogussynchronisatie mogelijk.
   - Voorbeeld: fysieke winkels, marketingplaatsen, advertentiepijpleidingen (Google, Facebook, Instagram)
- **catalogusbron** - Vertegenwoordigt de taal (scène) voor catalogi, bijvoorbeeld `en-US`. de catalogusbron wordt geplaatst op SKU niveau tijdens de opname van catalogusgegevens.

Tijdens het invoeren en bijwerken van productgegevens, bevat SKU de details van catalogusbronnen en attributen (de attributenkaart aan catalogusmeningen en beleid). Deze bepalen de herkenningstekens van de productcontext waartot SKU behoort:

![[!DNL Merchandising Services] Product-context-id&#39;s ](../assets/merchandising-svcs-product-id.png)

In het bovenstaande beeld, verstrekt elke SKU:

- &#x200B; van catalogusbron
   - Landinstelling: verplicht &#x200B;
- Productkenmerken
   - De kenmerken van het product worden gebruikt om aan de relevante catalogusmeningen en het beleid in kaart te brengen &#x200B;
   - Voorbeeld: als autofabrikant kunt u een catalogusweergave en beleidscombinatie voor productkenmerken maken: (1) Handelaars (2) Auto-merken. &#x200B;
- Prijzen en toegewezen prijsnoteringen
   - Elke SKU kan veelvoudige prijzen hebben die gebruikend veelvoudige prijsboeken worden bepaald.
   - Voorbeeld: je biedt werknemers een lagere normale prijs voor auto-onderdelen met een extra korting van 25%. Je biedt VIP-klanten een hogere normale prijs met een korting van 10%. De de prijsinformatie van productSKU zorgt ervoor dat de juiste prijs voor elk klantensegment wordt getoond.

De catalogusweergave en beleidsdefinities worden gemaakt met behulp van specifieke API&#39;s:

![[!DNL Merchandising Services] catalogusweergave, Beleid en toewijzing van catalogusbron ](../assets/merchandising-svcs-scope-map.png)

- **catalogusbron** (scène) - die op een niveau van SKU tijdens de opname van productgegevens wordt geplaatst. &#x200B;
- **catalogusmening** - gecreeerde Definitie gebruikend specifieke APIs. &#x200B;
- **Beleid** - gecreeerde Definitie gebruikend specifieke APIs.

## Belangrijkste kenmerken

| Belangrijkste kenmerken | Voordeel |
|---|---|
| **Directe ingang van catalogusgegevens in de pijpleiding van de opslagdiensten van de catalogusdiensten**: Maak direct uw catalogusgegevens in de pijpleiding van de catalogusdienst voor de browser van de storefront en onderzoekslevenscyclus (de Pagina van de Vertoning van het Product, de Pagina van de Lijst van het Product, de Pagina van de Resultaten van het Onderzoek, etc.) | <ul><li>Dien direct catalogusgegevens in de storefront dienstpijpleiding in die bevoegdheden: de Dienst van de Catalogus, de Ontdekking van het Product, en Aanbevelingen. Met dit, kunt u catalogusupdates op schaal voor miljoenen SKUs leveren. Dit ontgrendelt tijdgevoelig grootschalig promotiebeheer. </li></ul> |
| **Nieuwe catalogusbronnen van het catalogusproduct**: de catalogusmening, het beleid, en de catalogusbron zijn nieuwe die bronnen van de productcatalogus door de Diensten van de Verkoop worden geïntroduceerd. Deze productcatalogusbronnen vervangen de website-, opslag- en opslagcatalogusbronnen in de laag met opslagservices. [ leer meer ](#product-context-management). | <ul><li>Met de nieuwe catalogusbronnen ontgrendelt Merchandising Services de mogelijkheid om met gemak geschaald uit te breiden naar multigeografie, multi-business unit, multi-brand en meertalige gebruiksgevallen met behulp van één basiscatalogus.</li><li>Elimineer gegevensredundantie in uw catalogusbeheer.</li></ul> |
| **Schaal aan tientallen miljoenen SKUs** | Catalogusbeheer op schaal ontgrendelen. Hier kunt u meer dan 200 MM SKUs met gemak opnemen en beheren. |
| **typesteun van het Product** | <ul><li>Eenvoudig, configureerbaar</li><li>Bundels en bundels (toekomstig stappenplan)</li><li>Abonnementen en abonnementen (toekomstig stappenplan)</li></ul> |
| **Hoofdloze handel** | <ul><li>Volledige ondersteuning voor headless commerce-implementaties via Catalog Service, Product Discovery en Recommendations API&#39;s.</li></ul> |
| **Moderne bliksemsnelle UI componenten** | <ul><li>UI-componentondersteuning voor het zoeken naar producten en aanbevelingen.</li><li>De UI-componenten zijn uitbreidbaar en flexibel, zodat ze zowel door Adobe Edge Delivery Service als door andere storefront-implementatie kunnen worden gebruikt.</li></ul> |

## Welk type van koopman het meest van de Diensten van de Koophandel profiteert?

De volgende lijst benadrukt gemeenschappelijke uitdagingen verkopers ontmoeten en hoe de Diensten van de Verkoop die door de meningen en het Beleid van de Catalogus worden aangedreven hen richt.

| Merchant type | Hoofdletters gebruiken | Opgeloste problemen |
|---|---|---|
| Multibrand conglomeraat | <ul><li>Zij verkopen verschillende merken</li><li>Ze verkopen in verschillende landen</li><li>Ze verkopen in verschillende talen</li></ul> | Gebruik één enkele basis verenigde catalogus en behaal operationele efficiency terwijl het uitbreiden aan verscheidene merken, geographies en talen. |
| Automobiel/fabricageconglomeraat | <ul><li>Hiermee verkoopt u auto- of computeronderdelen. De producten zijn hetzelfde voor alle klanten.</li><li>Verschillende dealers verkopen onderdelen aan klanten</li><li>Elke handelaar heeft zijn eigen prijzen, voorraad en verzendmethoden</li></ul> | Om verschillende scheepvaartintegraties te hebben, zou elke handelaar een afzonderlijke website moeten hebben. Maar afzonderlijke websites dwingen het typische model van catalogusgegevens om de gegevens te dupliceren. Dus als er 3000 dealers in de VS zijn, maakt een handelaar 3000 catalogusexemplaren, ook al wordt dezelfde catalogus door alle dealers gebruikt. Deze gegevensduplicatie heeft invloed op de prestatielimieten. Merchandising Services elimineert gegevensduplicatie. |
| Verpakkings-/logistiekbedrijf | <ul><li>Ze hebben verschillende verzendlocaties</li><li>Zij hebben een verschillende prijs voor elke klant</li><li>Hetzelfde product dat op twee locaties beschikbaar is voor twee klanten heeft 4 mogelijke prijzen</li></ul> | Ondanks het gebruik van klantgroepen om prijzen per klant te dekken, beschikt het typische model van catalogusgegevens niet over de capaciteit om prijs per plaats te beheren. Bovendien willen handelaren unieke zichtbaarheidsregels per locatie/website. Beheer van dergelijke complexe prijs- en zichtbaarheidsregels kan op schaal worden ontgrendeld met Merchandising Services. |
