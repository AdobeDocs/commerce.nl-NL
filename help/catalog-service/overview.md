---
title: '[!DNL Catalog Service]'
description: '[!DNL Catalog Service] voor Adobe Commerce biedt een manier om de inhoud van de pagina''s met productweergave en de productlijst veel sneller op te halen dan de GraphQL-query''s van de native Adobe Commerce.'
role: Admin, Developer
recommendations: noCatalog
exl-id: 525e3ff0-efa6-48c7-9111-d0b00f42957a
source-git-commit: be1c739f3821a5f1e846b3026088e3a3ff45a60f
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 0%

---

# [!DNL Catalog Service] voor Adobe Commerce

De extensie [!DNL Catalog Service] for Adobe Commerce biedt rijke view-model (alleen-lezen) catalogusgegevens om productgerelateerde winkelervaringen snel en volledig te renderen, waaronder:

* Productdetailpagina&#39;s
* Productlijst en categoriepagina&#39;s
* Resultaatpagina&#39;s zoeken
* Productcarrousels
* Productvergelijkingspagina&#39;s
* Alle andere pagina&#39;s die productgegevens weergeven, zoals pagina&#39;s met een cart-, volgorde- en wenslijst

[!DNL Catalog Service] gebruikt [ GraphQL ](https://graphql.org/) om catalogusgegevens met inbegrip van producten, productattributen, inventaris, en prijzen te verzoeken en te ontvangen. GraphQL is een querytaal die een front-end client gebruikt om te communiceren met de API (Application Programming Interface) die op een back-end zoals Adobe Commerce is gedefinieerd. GraphQL is een veelgebruikte communicatiemethode omdat deze lichtgewichtgericht is en een systeemintegrator de inhoud en volgorde van elke reactie kan opgeven.

Adobe Commerce heeft twee GraphQL-systemen. Het kernGraphQL systeem verstrekt een brede waaier van vragen (lees verrichtingen) en mutaties (schrijf verrichtingen) die een verkoopster toestaan om met vele soorten pagina&#39;s, met inbegrip van product, klantenrekening, kar, controle, en meer in wisselwerking te staan. Nochtans, worden de vragen die productinformatie terugkeren niet geoptimaliseerd voor snelheid. Het GraphQL-systeem voor services kan alleen query&#39;s uitvoeren op producten en gerelateerde informatie. Deze query&#39;s leveren meer op dan vergelijkbare core query&#39;s.

De gegevens beschikbaar aan de Dienst van de Catalogus worden geleverd door de uitbreiding van de Uitvoer van Gegevens SaaS. Deze extensie synchroniseert gegevens tussen de Commerce-toepassing en de aangesloten Commerce Services om ervoor te zorgen dat query&#39;s naar de services die GraphQL API-eindpunten retourneert, de meest recente catalogusgegevens retourneren. Voor informatie over het beheren van en het oplossen van problemenSaaS gegevens de uitvoerverrichtingen, zie de [ Gids van de Uitvoer van Gegevens SaaS ](../data-export/overview.md).

[!DNL Catalog Service] klanten kunnen [ SaaS prijsindexeerder ](../price-index/price-indexing.md) gebruiken, die snellere prijsupdates en synchronisatietijd verstrekt.

## Architectuur

In het volgende diagram worden de twee GraphQL-systemen weergegeven:

![ diagram van de architectuur van de Catalogus ](assets/catalog-service-architecture.png)

In het kernGraphQL systeem, verzendt PWA een verzoek naar de toepassing van Commerce, die elk verzoek ontvangt, verwerkt het, misschien verzendend een verzoek door veelvoudige subsystems, dan keert een antwoord op storefront terug. Deze ronde trip kan leiden tot een trage laadtijd voor de pagina, wat kan leiden tot lagere conversiesnelheden.

[!DNL Catalog Service] is een Gateway van de Diensten Storefront. De dienst heeft toegang tot een afzonderlijk gegevensbestand dat productdetails en verwante informatie, zoals productattributen, varianten, prijzen, en categorieën bevat. De service houdt de database via indexering synchroon met de Adobe Commerce.
Omdat de dienst directe communicatie met de toepassing overslaat, kan het de latentie van de verzoek en reactiecyclus verminderen.

De kern en de dienstGraphQL systemen communiceren niet direct met elkaar. U hebt toegang tot elk systeem via een andere URL en voor aanroepen is andere headerinformatie nodig. De twee GraphQL-systemen zijn ontworpen om samen te worden gebruikt. Het GraphQL-systeem van [!DNL Catalog Service] maakt het basissysteem sterker, zodat producten sneller kunnen worden opgeslagen.

U kunt naar keuze uitvoeren [ API Net voor Adobe Developer App Builder ](https://developer.adobe.com/graphql-mesh-gateway/) om de twee systemen van Adobe Commerce GraphQL met privé en derde APIs en andere softwareinterfaces te integreren gebruikend Adobe Developer. Het netwerk kan worden gevormd om vraag te verzekeren die aan elk eindpunt wordt verpletterd bevat de correcte vergunningsinformatie in de kopballen.

## Architectuurgegevens

In de volgende secties worden enkele verschillen tussen de twee GraphQL-systemen beschreven.

### Schema-beheer

Aangezien Catalog Service als service werkt, hoeven integrators zich niet zorgen te maken over de onderliggende versie van Commerce. De syntaxis van de query&#39;s is voor alle versies hetzelfde. Bovendien is het schema verenigbaar voor alle handelaren. Deze consistentie maakt het gemakkelijker om beste praktijken te vestigen, en verhoogt opnieuw gebruik van storefront widgets beduidend.

### Vereenvoudiging van productsoorten

Het schema vermindert de diversiteit van producttypen tot twee gebruiksgevallen:

* Eenvoudige producten zijn producten die worden gedefinieerd met één prijs en hoeveelheid. De Catalogusservice wijst de eenvoudige, virtuele, downloadbare en cadeau-kaartproducttypen toe aan `simpleProductViews` .

* Complexe producten bestaan uit meerdere eenvoudige producten. De componenten eenvoudige producten kunnen verschillende prijzen hebben. Een complex product kan ook worden bepaald zodat de verkoopster de hoeveelheid componenten eenvoudige producten kan specificeren. De Catalogusservice wijst de configureerbare, bundel- en gegroepeerde producttypen toe aan `complexProductViews` .

Complexe productopties worden verenigd en onderscheiden door hun gedrag, niet door type. Elke optiewaarde vertegenwoordigt een eenvoudig product. Deze optie heeft toegang tot de eenvoudige productkenmerken, inclusief prijs. Wanneer de verkoper alle opties voor een complex product selecteert, wijst de combinatie geselecteerde opties naar een specifiek eenvoudig product. Het eenvoudige product blijft dubbelzinnig totdat de gebruiker een waarde voor alle beschikbare opties selecteert.

#### Kenmerken van de productweergave

Zowel hebben de eenvoudige als de complexe producten klant-bepaalde attributen die op de winkelfront kunnen worden getoond. Deze attributen zijn teruggekeerd als [ ProductViewAttributes ](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/#productviewattribute-type). In Adobe Commerce worden de beschikbare kenmerken gedefinieerd wanneer het product wordt gemaakt. U kunt aanvullende kenmerken toevoegen vanuit de Adobe Commerce-backend of via programmacode. Zie [ de gegevens van de de uitvoervoer van SaaS uitbreiden en aanpassen ](../data-export/extensibility-and-customizations.md).

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

[!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."}

Het installatieproces vereist configuratie van de [ Schakelaar van de Diensten van Commerce ](../landing/saas.md). Wanneer dat is voltooid, is de volgende stap dat een systeemintegrator de storefront-code bijwerkt om de [!DNL Catalog Service] query&#39;s op te nemen. Alle [!DNL Catalog Service] query&#39;s worden gerouteerd naar de GraphQL-gateway. De URL wordt tijdens het instapproces opgegeven.
