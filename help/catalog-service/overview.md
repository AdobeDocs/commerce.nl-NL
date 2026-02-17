---
title: '[!DNL Catalog Service]'
description: Versnel uw Adobe Commerce-winkel met  [!DNL Catalog Service]  - een krachtige GraphQL API die de laadtijden van pagina's voor productpagina's, categoriepagina's en zoekresultaten verkort.
role: Admin, Developer
recommendations: noCatalog
exl-id: 525e3ff0-efa6-48c7-9111-d0b00f42957a
source-git-commit: 4f3f8accd653dbee6fec45c065f55ff04b17bd2d
workflow-type: tm+mt
source-wordcount: '1353'
ht-degree: 0%

---

# [!DNL Catalog Service] voor Adobe Commerce

[!DNL Catalog Service] voor Adobe Commerce-extensie verbetert de laadtijden van winkels door geoptimaliseerde, alleen-lezen catalogusgegevens te verschaffen via een speciale GraphQL API. Deze service is specifiek ontworpen om de productgerelateerde paginaervaring te verbeteren, waardoor pagina&#39;s sneller worden geladen en de conversiesnelheden zijn verbeterd.

De rijke mening-modelgegevens die door [!DNL Catalog Service] worden verstrekt omvatten productdetails, attributen, inventaris, en prijzen, die snelle teruggave van product-gerelateerde storefront ervaringen zoals toelaten:

- Productdetailpagina&#39;s
- Productlijst en categoriepagina&#39;s
- Resultaatpagina&#39;s zoeken
- Productcarrousels
- Productvergelijkingspagina&#39;s
- Alle andere pagina&#39;s die productgegevens weergeven, zoals pagina&#39;s met een cart-, volgorde- en wenslijst


## Belangrijkste voordelen en functies

- **Snellere paginaladingen**: Geoptimaliseerde vragen voor tot 10X snellere de terugwinning van catalogusgegevens in vergelijking met het kernsysteem van GraphQL
- **Verbeterde omzettingspercentages**: De snellere ladingtijden leiden tot betere gebruikerservaring
- **Vereenvoudigde producttypes**: Het verenigde schema dat op eenvoudige en complexe producttypes wordt gebaseerd vermindert ingewikkeldheid voor ontwikkelaars
- **Verbeterde prijsprecisie**: Steun voor 16 cijferwaarden met 4 decimalen
- **Ontkoppelde architectuur**: Het afzonderlijke systeem van GraphQL voor catalogusgegevens verzekert hoge prestaties zonder de verrichtingen van kernCommerce te beïnvloeden
- **Real-time gegevenssynchronisatie**: De dienst van de Catalogus wordt gehouden synchroon met de toepassing van Adobe Commerce door de uitbreiding van de Uitvoer van Gegevens SaaS, die ervoor zorgt dat de vragen de huidigste catalogusgegevens terugkeren
- **Dashboard van het Beheer van Gegevens**: De verrichtingen van de gegevenssynchronisatie van de interface van Adobe Commerce Admin controleren en beheren
- **API de integratie van het Net**: Naar keuze integreren met [ API Net voor Adobe Developer App Builder ](https://developer.adobe.com/graphql-mesh-gateway/) om de systemen van Adobe Commerce GraphQL met andere interne en derde APIs te combineren om het schema van GraphQL van de Dienst van de Catalogus uit te breiden en douanegegevens of functionaliteit toe te voegen


## Overzicht van architectuur

>[!NOTE]
>
>Als u uw catalogus gebruikend de composable catalogus met Adobe Commerce Optimizer, of de Schakelaar van Adobe Commerce Optimizer uitvoert, zie de [ Gids van Adobe Commerce Optimizer ](../optimizer/overview.md#architecture) en de Gids van de Ontwikkelaar van de Diensten van de Merchandising.

[!DNL Catalog Service] gebruikt [ GraphQL ](https://graphql.org/) om catalogusgegevens met inbegrip van producten, productattributen, inventaris, en prijzen te verzoeken en te ontvangen. GraphQL is een querytaal die een front-end client gebruikt om te communiceren met de API (Application Programming Interface) die op een back-end zoals Adobe Commerce is gedefinieerd. GraphQL is een veelgebruikte communicatiemethode omdat deze lichtgewichtgericht is en een systeemintegrator de inhoud en volgorde van elke reactie kan opgeven.

Adobe Commerce biedt twee GraphQL-systemen voor verschillende doeleinden:

### Core GraphQL System

- **Doel**: Volledig-gekenmerkte API voor alle verrichtingen van Commerce
- **Mogelijkheden**: Vragen (lees) en mutaties (schrijf) voor producten, klanten, kar, controle, en meer
- **Beperking**: De vragen van het product worden niet geoptimaliseerd voor snelheid
- **geval van het Gebruik**: De algemene verrichtingen van Commerce en schrijven verrichtingen

### Catalogusservice GraphQL-systeem

- **Doel**: De krachtige vragen van de productcatalogus slechts
- **Mogelijkheden**: Read-only vragen voor producten, attributen, inventaris, en prijzen
- **Voordeel**: Aanzienlijk sneller dan kernsysteem voor productgegevens
- **Geval van het Gebruik**: De productervaringen van de Storefront waar de snelheid kritiek is

De gegevens beschikbaar aan de Dienst van de Catalogus worden geleverd door de uitbreiding van de Uitvoer van Gegevens SaaS. Deze extensie synchroniseert gegevens tussen de Commerce-toepassing en de aangesloten Commerce Services om ervoor te zorgen dat query&#39;s naar de services die GraphQL API-eindpunten retourneert, de meest recente catalogusgegevens retourneren. Voor informatie over het beheren van en het oplossen van problemenSaaS gegevens de uitvoerverrichtingen, zie de [ Gids van de Uitvoer van Gegevens SaaS ](../data-export/overview.md).

[!DNL Catalog Service] klanten kunnen [ SaaS prijsindexeerder ](../price-index/price-indexing.md) gebruiken, die snellere prijsupdates en synchronisatietijd verstrekt.

## Architectuurgegevens

In het volgende diagram worden de architecturale verschillen tussen het GraphQL-kernsysteem en het GraphQL-systeem van Catalog Service weergegeven, waarbij wordt getoond hoe ze samenwerken om de prestaties van winkels te optimaliseren:

![ diagram van de architectuur van de Catalogus ](assets/catalog-service-architecture.png)

### De werking van de systemen

**Systeem van de Kern GraphQL (Traditionele Benadering):**
De Progressieve Web App (PWA) verzendt verzoeken rechtstreeks naar de toepassing van Commerce, die elk verzoek door veelvoudige subsystemen alvorens een reactie terugkeert verwerkt. Deze stap voor ronde reizen in meerdere stappen kan leiden tot een trage laadtijd van de pagina, wat kan leiden tot lagere conversiesnelheden.

**de Dienst van de Catalogus (Geoptimaliseerde Benadering):**
De Dienst van de Catalogus doet dienst als Gateway van de Diensten Storefront die tot een specifieke, geoptimaliseerde gegevensbestand toegang heeft die productdetails, attributen, varianten, prijzen, en categorieën bevatten. De service zorgt voor synchronisatie met Adobe Commerce via automatische indexering, waarbij de traditionele aanvraagresponscyclus wordt overgeslagen om de latentie aanzienlijk te verminderen.

De kern en de dienstGraphQL systemen communiceren niet direct met elkaar. U hebt toegang tot elk systeem via een andere URL en voor aanroepen is andere headerinformatie nodig. De twee GraphQL-systemen zijn ontworpen om samen te worden gebruikt. Het GraphQL-systeem van [!DNL Catalog Service] maakt het basissysteem sterker, zodat producten sneller kunnen worden opgeslagen.

U kunt naar keuze uitvoeren [ API Net voor Adobe Developer App Builder ](https://developer.adobe.com/graphql-mesh-gateway/) om de twee systemen van Adobe Commerce GraphQL met privé en derde APIs en andere softwareinterfaces te integreren gebruikend Adobe Developer. Het netwerk kan worden gevormd om vraag te verzekeren die aan elk eindpunt wordt verpletterd bevat de correcte vergunningsinformatie in de kopballen.

## Architectuurgegevens

In de volgende secties worden enkele verschillen tussen de twee GraphQL-systemen beschreven.

### Schema-beheer

Aangezien Catalog Service als service werkt, hoeven integrators zich niet zorgen te maken over de onderliggende versie van Commerce. De syntaxis van de query&#39;s is voor alle versies hetzelfde. Bovendien is het schema verenigbaar voor alle handelaren. Deze consistentie maakt het gemakkelijker om beste praktijken te vestigen, en verhoogt opnieuw gebruik van storefront widgets beduidend.

### Vereenvoudiging van productsoorten

Het schema vermindert de diversiteit van producttypen tot twee gebruiksgevallen:

- **Eenvoudige producten** - de Dienst van de Catalogus brengt de eenvoudige, virtuele, downloadbare, en de producttypes van cadeaukaart van Adobe Commerce aan `simpleProductViews` in kaart. Dit type heeft:
   - Eén enkele vaste prijs en hoeveelheid
   - Een reguliere prijs (vóór kortingen) en eindprijs (na kortingen)
   - Ondersteuning voor productkenmerken, zoals kleur, grootte en andere kenmerken

- **Complexe producten** - de Dienst van de Catalogus brengt de configureerbare Adobe Commerce, bundel, en gegroepeerde producttypes aan `complexProductViews` in kaart. De complexe producten zijn inzamelingen van veelvoudige eenvoudige producten die samen kunnen worden gevormd of worden gebundeld.
   - Elk onderdeel van een eenvoudig product kan een eigen prijs hebben.
   - Klanten kunnen de hoeveelheden voor afzonderlijke producten opgeven.
   - Productopties (zoals grootte, kleur, materiaal) zijn verenigd en werken op dezelfde manier, ongeacht het producttype. Elke optie wijst naar een specifiek eenvoudig product met zijn eigen kenmerken en prijs. Het eindproduct blijft ongedefinieerd totdat de gebruiker alle vereiste opties selecteert.

#### Kenmerken van de productweergave

Zowel hebben de eenvoudige als de complexe producten klant-bepaalde attributen die op de winkelfront kunnen worden getoond. Deze attributen zijn teruggekeerd als [ ProductViewAttributes ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/#productviewattribute-type). In Adobe Commerce worden de beschikbare kenmerken gedefinieerd wanneer het product wordt gemaakt. U kunt aanvullende kenmerken toevoegen vanuit de Adobe Commerce-backend of via programmacode. Zie [ de gegevens van de de uitvoervoer van SaaS uitbreiden en aanpassen ](../data-export/extensibility-and-customizations.md).

>[!TIP]
>
>In plaats van het toevoegen van gegevenstypes aan de Commerce achterkant, kunt u [ API Net met de Dienst van de Catalogus gebruiken ](mesh.md) om het schema van GraphQL van de Dienst van de Catalogus uit te breiden om gegevens toe te voegen of bestaande catalogusgegevens te vormen om nieuwe functionaliteit toe te laten.

### Prijzen

Eenvoudige producten vertegenwoordigen de basisverkoopeenheid die een prijs heeft. [!DNL Catalog Service] berekent de normale prijs vóór kortingen en de uiteindelijke prijs na kortingen. Prijsberekeningen kunnen vaste productbelastingen bevatten. Ze sluiten gepersonaliseerde promoties uit.

Een complex product heeft geen vaste prijs. In plaats daarvan retourneert de Catalogusservice de prijzen van gekoppelde voorbeelden. Een handelaar kan bijvoorbeeld in eerste instantie dezelfde prijzen toewijzen aan alle varianten van een configureerbaar product. Als bepaalde grootten of kleuren niet populair zijn, kan de handelaar de prijzen van die varianten verlagen. De prijs van het complexe (configureerbare) product vertoont dus eerst een prijsbereik, dat de prijs van zowel standaard- als niet-populaire varianten weerspiegelt. Nadat de winkelier een waarde voor alle beschikbare opties heeft geselecteerd, toont de winkel één enkele prijs.

De Catalogusdienst verzekert nauwkeurige prijsupdates en berekeningen door prijzen met grote waarden (tot 16 cijfers) en hoge decimale precisie (tot 4 decimalen) te steunen.

>[!NOTE]
>
> De klanten van Commerce met [!DNL Catalog Service] kunnen uit snellere prijsveranderingen en synchronisatietijd op hun websites met [ SaaS prijsindexer ](../price-index/price-indexing.md) voordeel halen.

## Implementatie

Het implementatieproces omvat:

1. [!BADGE  PaaS slechts ]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."} **[installeert en vormt de Dienst van de Catalogus](installation.md)** - installeert en vormt de uitbreiding van de Dienst van de Catalogus en opstelling de verbinding SaaS gebruikend [!DNL Commerce Services Connector].
2. **de storefrontcode van de Update**: Integreer de vragen van GraphQL van de Dienst van de Catalogus in uw frontend.
3. **vragen van de Route**: Alle vragen van de Dienst van de Catalogus gaan door de gateway van GraphQL (URL die tijdens onboarding wordt verstrekt)
4. **Monitor en los gegevenssynchronisatie** problemen op: Verifieer betere prestaties en monitorresultaten


