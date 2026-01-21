---
title: Migreren naar [!DNL Adobe Commerce as a Cloud Service]
description: Leer hoe je kunt migreren naar [!DNL Adobe Commerce as a Cloud Service].
feature: Cloud
exl-id: 9065c92a-f6b2-4464-8ec0-5c549bf78104
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Van toepassing op Adobe Commerce als Cloud Service en alleen Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
role: Developer
level: Intermediate
source-git-commit: af56d52f98a83310b858f82f16693f5323c1b962
workflow-type: tm+mt
source-wordcount: '3016'
ht-degree: 0%

---

# Migreren naar [!DNL Adobe Commerce as a Cloud Service]

[!DNL Adobe Commerce as a Cloud Service] biedt een uitgebreide gids voor ontwikkelaars die overstappen van een bestaande Adobe Commerce PaaS-implementatie naar het nieuwe Adobe Commerce as a Cloud Service (SaaS)-aanbod. Adobe Commerce als Cloud Service vertegenwoordigt een belangrijke verschuiving naar een volledig beheerd, versieloos SaaS-model, dat verbeterde prestaties, schaalbaarheid, vereenvoudigde operaties en nauwere integratie met het bredere [!DNL Adobe Experience Cloud]platform biedt.

>[!NOTE]
>
>Voor meer informatie over migratietools, zie de [Bulk Data Migration Tool](./bulk-data.md).

## De verschuiving begrijpen - PaaS en SaaS vergelijken

**Belangrijke verschillen**

* [!BADGE PaaS alleen]{type=Informative url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Van toepassing op Adobe Commerce on Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en alleen on-premises projecten."} **PaaS (Actueel):** Merchant beheert applicatiecode, upgrades, patches en infrastructuurconfiguratie binnen de gehoste omgeving van Adobe. [Gedeelde verantwoordelijkheidsmodel](https://experienceleague.adobe.com/nl/docs/commerce-operations/security-and-compliance/shared-responsibility) voor diensten (MySQL, Elasticsearch en anderen).
* [!BADGE Alleen]{type=Positive url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Van toepassing op Adobe Commerce als Cloud Service en alleen Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."} **SaaS SaaS (Nieuw - [!DNL Adobe Commerce as a Cloud Service])**: Adobe beheert volledig de kernapplicatie, infrastructuur en updates. Handelaren richten zich op maatwerk via uitbreidbaarheidspunten (API&#39;s, App Builder, UI SDK&#39;s). De kernapplicatiecode is vergrendeld.

**Architectonische implicaties**

* **Versieloos platform**: Continue updates betekenen geen grote versie-upgrades meer voor de core.
* **Microservices &amp; API-first**: Diepere afhankelijkheid van API&#39;s voor uitbreidbaarheid en integratie.
* **Standaard headless (optioneel):** Sterke ondersteuning voor losgekoppelde winkelfronts (bijvoorbeeld Commerce Storefront aangedreven door Edge Delivery Services).
* **Edge Delivery Services**: Impact op front-end prestaties en implementatie.

**Nieuwe tools &amp; concepten**

* [Adobe Developer App Builder](https://developer.adobe.com/app-builder/) en [API Mesh voor Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway)
* [Commerce Optimizer](../../optimizer/overview.md)
* [Edge Delivery Services](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL)
* Selfservice-provisioning met de [Commerce Cloud Manager](../getting-started.md#create-an-instance)

## Migratieroutes

[!DNL Adobe Commerce as a Cloud Service] Ondersteunt meerdere migratiepaden, afhankelijk van je tijdlijn, winkel en aanpassingen.

Als alternatief voor een volledige migratie [!DNL Adobe Commerce as a Cloud Service] ondersteunt het een gefaseerde migratie, met gebruik van Commerce Optimizer of een incrementele aanpak.

* **Incrementele migratie**—Deze aanpak omvat het migreren van uw gegevens, aanpassingen en integraties in fasen. Deze aanpak is ideaal voor grote handelaren met veel aanpassingen die hun complexe aanpassingen en data [!DNL Adobe Commerce as a Cloud Service] geleidelijk in hun eigen tempo willen overzetten.

![Incrementele migratie](../assets/incremental.png){width="600" zoomable="yes"}

* **Commerce Optimizer**—Deze aanpak stelt je in staat om iteratief te migreren, door Commerce Optimizer te gebruiken als overgangsfase om complexe aanpassingen en data in je eigen tempo te verplaatsen [!DNL Adobe Commerce as a Cloud Service] . Commerce Optimizer biedt toegang tot merchandisingdiensten die worden aangedreven door catalogusweergaven en -beleid, Commerce Storefront met Edge Delivery, en [!DNL Product Visuals powered by AEM Assets].

![Iteratieve migratie](../assets/optimizer.png){width="600" zoomable="yes"}

* **Volledige migratie**—Deze aanpak houdt in dat alle data, aanpassingen en integraties in één keer worden gemigreerd. Deze aanpak is ideaal voor kleinere handelaren met weinig aanpassingen die snel willen overstappen naar [!DNL Adobe Commerce as a Cloud Service].

De volgende tabel geeft een overzicht van het migratieproces voor verschillende winkelfronts en configuraties:

|                    | LUMA Storefront | PWA Storefront | Commerce Storefront aangedreven door Edge Delivery | Hoofdloos |
|--------------------|----------------------------------------|----------------------------------------|------------------------------------------------------|----------------------------------------|
| Datamigratie | Vereist | Vereist | Vereist | Vereist |
| Storefront | Migreren naar Commerce Storefront met Edge Delivery | Migreren naar Commerce Storefront met Edge Delivery of onderhouden | Geen impact | Geen impact |
| API Mesh | Bouw een nieuw mesh | Bouw een nieuw mesh of herconfigureer bestaande | Bouw een nieuw mesh of herconfigureer bestaande | Bouw een nieuw mesh of herconfigureer bestaande |
| Integraties | Benut integratiestarterkit | Benut integratiestarterkit | Benut integratiestarterkit | Benut integratiestarterkit |
| Aanpassingen | Overstap naar App Builder &amp; API Mesh | Overstap naar App Builder &amp; API Mesh | Overstap naar App Builder &amp; API Mesh | Overstap naar App Builder &amp; API Mesh |
| Assets Management | Migratie vereist bij gebruik van OOTB | Migratie vereist bij gebruik van OOTB | Migratie vereist bij gebruik van OOTB | Migratie vereist bij gebruik van OOTB |
| Uitbreidingen | Migreren naar App Builder | Migreren naar App Builder | Migreren naar App Builder | Migreren naar App Builder |

Zoals aangegeven in de tabel, zullen de mitigaties voor elke migratie bestaan uit:

* **Datamigratie**—Gebruik van meegeleverde [&#128279;](./bulk-data.md) migratietools om data van je bestaande instantie naar te migreren[!DNL Adobe Commerce as a Cloud Service].
* **Storefront**—Bestaande Commerce Storefronts die worden aangedreven door Edge Delivery en headless storefronts vereisen geen mitigatie, maar Luma-storefronts vereisen migratie naar Commerce Storefront powered by Edge Delivery. PWA Studio-winkelfronts kunnen worden gemigreerd naar Commerce Storefront die wordt aangedreven door Edge Delivery of in hun huidige staat wordt onderhouden. Adobe zal accelerators bieden om te helpen bij de migratie van winkelfronts.
* **[API Mesh](https://developer.adobe.com/graphql-mesh-gateway)**—Maak een nieuwe mesh of wijzig de bestaande. Adobe zal vooraf geconfigureerde meshes leveren om dit proces te ondersteunen.
* **Integraties**—Alle integraties moeten gebruikmaken van ofwel de [integratiestarterkit](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/) of de [[!DNL Adobe Commerce as a Cloud Service] REST API.](https://developer.adobe.com/commerce/webapi/reference/rest/saas/)
* **Aanpassingen**—Alle aanpassingen moeten naar App Builder en API Mesh verhuizen.
* **Asset Management**—Al het asset management vereist migratie. Als je al gebruik, [!DNL AEM Assets]is er geen noodzaak om te migreren.
* **Extensies—Alle extensies** in het proces moeten worden nagemaakt als extensies buiten het proces. Tegen het einde van 2025 zal Adobe toegang bieden tot onze populairste extensies om bouwtijden te minimaliseren.

## Migratiefasen

De volgende fasen beschrijven de noodzakelijke stappen en overwegingen voor migratie naar [!DNL Adobe Commerce as a Cloud Service].

### Pre-migratiebeoordeling en planning

Deze fase is van cruciaal belang om risico&#39;s tot een minimum te beperken en een duidelijk migratiepad vast te stellen en problemen te identificeren voordat ze zich voordoen.

**Ontdekking en controle van huidig milieu**

**Codebase analyse:**

* Alle aangepaste modules, thema&#39;s en overschrijvingen identificeren.
* Analyseer de wijzigingen van kerncode en bepaal welke het refactoring als deel van migratie zal vergen.
* Evalueer extensies van derden en bepaal de compatibiliteit met [!DNL Adobe Commerce as a Cloud Service] . Zijn er SaaS-compatibele alternatieven, of moet u aangepaste API-integratie of App Builder-toepassingen maken?
* Identificeer om het even welke verouderde code of functionaliteit die niet zal worden gemigreerd.

**controle van Gegevens:**

* Bepaal de grootte en complexiteit van uw database.
* Ongebruikte gegevens of tabellen identificeren voor opschoning.
* Bekijk bestaande data-import/exportprocessen.

**Integratiebeoordeling:**

* Vermeld alle externe systemen die geïntegreerd zijn met Adobe Commerce (ERP, CRM, PIM, betalingsgateways, verzendproviders, OMS en andere systemen).
* Beoordeel integratiemethoden (API, aangepaste scripts en andere methoden).
* Evalueer compatibiliteit met [!DNL Adobe Commerce as a Cloud Service]&#39;s API-first aanpak en App Builder.

**benchmarks van Prestaties:**

* Huidige Lighthouse-scores, laadtijden van pagina&#39;s en belangrijke prestatie-indicatoren (KPI&#39;s) documenteren, die een basislijn bieden voor het meten van verbeteringen na de migratie.

**de configuratieoverzicht van de Veiligheid:**

* Beoordeel om het even welke regels van douaneWAF, IP lijsten van gewenste personen, en om het even welke andere veiligheidsconfiguraties.

**Definieer de reikwijdte en strategie van migratie:**

* **Gefaseerde versus all-in-once-migratie:** Evalueer de voor- en nadelen van elke aanpak.
* **Identificeer kernbedrijfsprocessen:** Prioriteer functionaliteiten die eerst geïmporteerd moeten worden, zoals:
   * Complexe prijsregels
   * Aangepaste bedrijfsregels die worden toegepast voordat een bestelling officieel wordt geplaatst of verwerkt
   * Complexe belastingberekeningen
   * Adresvalidaties
   * Aangepaste logica wordt geactiveerd nadat een bestelling is geplaatst
* **Hoofdloos versus monolithisch winkelgevel:** Beslissingspunt voor nieuwe winkelontwikkeling of het aanpassen van bestaande winkelpuien.
* **Integratiestrategie:** Bepaal hoe bestaande integraties opnieuw worden geplatformeerd (API Mesh, App Builder, directe API).
* **Datamigratiestrategie:** Bepaal of je van plan bent te migreren met volledige historische data, gedeeltelijke data of geen gemigreerde data.

**Teamgereedheid en training:**

* Maak jezelf vertrouwd met [!DNL Adobe Commerce as a Cloud Service] concepten, ontwikkelworkflows en nieuwe tools.
* Volg praktische trainingen met Adobe App Builder, Edge Delivery Services en [!DNL Adobe Commerce as a Cloud Service] deployment-pipelines.

**Omgevingsopstelling en -provisioning:**

* Provisioneer je [!DNL Adobe Commerce as a Cloud Service] sandbox- en ontwikkelomgevingen met de Commerce Cloud Manager.

### Incrementele migratiefasen

**Strategische refactoring en externalisering**

Deze fase vormt de kern van de migratie, met de nadruk op het aanpassen van je codebase aan het [!DNL Adobe Commerce as a Cloud Service] cloud-native paradigma. Dit houdt in dat nieuwe Adobe-diensten strategisch worden geadopteerd en aangepaste logica uit het kern van het Commerce-platform worden gehaald.

#### &#x200B;1. Migratie van &quot;in-process&quot; aanpassingen en extensies naar App Builder

Dit is een cruciale fase om een &quot;gesloten kern&quot; te bereiken en je oplossing toekomstbestendig te maken, wat centraal staat in de [!DNL Adobe Commerce as a Cloud Service] architectuurfilosofie.

* **Externaliseer complexe logica naar App Builder**: Analyseer bestaande aangepaste modules en extensies van derden binnen je PaaS-codebase. Voor complexe bedrijfslogica, op maat gemaakte integraties of microservices die geen directe, in-process manipulatie van het kern van het Commerce-datamodel vereisen, refactoren en herplatformen deze als serverloze applicaties binnen Adobe Developer App Builder.
* **Maak gebruik van API Mesh**: Voor scenario&#39;s die data van meerdere backendsystemen vereisen (bijvoorbeeld je PaaS Commerce backend, ERP, CRM en aangepaste App Builder-microservices), implementeer een API Mesh-laag binnen App Builder. Dit consolideert uiteenlopende API&#39;s in één presterende GraphQL-endpoint dat door je nieuwe storefront of andere diensten wordt gebruikt, waardoor het ophalen van complexe data vereenvoudigt.
* **Event-driven architecture**: Gebruik Adobe I/O-gebeurtenissen om App Builder-acties te activeren op basis van gebeurtenissen die plaatsvinden in je PaaS-instantie (bijvoorbeeld productupdates, klantregistraties, wijziging van orderstatus) of andere verbonden systemen. Dit bevordert asynchrone communicatie, vermindert nauwe koppeling en verhoogt de systeemveerkracht.

**Voordeel**: Deze stap vermindert de technische schuld die gepaard gaat met diep ingebedde aanpassingen aanzienlijk, versnelt de overgang van je Commerce-instantie aanzienlijk [!DNL Adobe Commerce as a Cloud Service], verbetert de schaalbaarheid en onafhankelijke implementatie van aangepaste logica, en bevordert snellere ontwikkelingscycli voor extensies.

#### &#x200B;2. Adopteer SaaS-gebaseerde Adobe Commerce merchandisingdiensten en integreer catalogusgegevens

Dit is een cruciaal initiële integratiepunt met twee opties voor catalogusgegevensbeheer:

>[!BEGINTABS]

>[!TAB Optie 1 - Bestaande catalogus SaaS-dienst]

**Maak gebruik van bestaande Catalog SaaS-service geïntegreerd met PaaS-backend**

Deze optie dient als overgangsstap, voortbouwend op een bestaande integratie waar uw steun PaaS een bestaand geval van de dienst van Adobe Commerce SaaS met gegevens van de [&#x200B; catalogusdienst &#x200B;](../../catalog-service/guide-overview.md), [&#x200B; levend onderzoek &#x200B;](../../live-search/overview.md), en [&#x200B; productaanbevelingen &#x200B;](../../product-recommendations/overview.md) bevolkt.

* **de gegevenssynchronisatie van de Catalogus**: Verzeker uw instantie van Adobe Commerce PaaS product en catalogusgegevens aan uw bestaande dienst van de Catalogus SaaS van Adobe Commerce blijft synchroniseren. Dit baseert zich typisch op gevestigde schakelaars of modules binnen uw instantie PaaS. De dienst van de Catalogus SaaS blijft de gebiedende bron voor onderzoek en het verhandelen functies, die zijn gegevens uit uw steun PaaS afleiden.
* **API Net voor optimalisering**: Terwijl de hoofdloze opslag (op Edge Delivery Services) en andere diensten gegevens van de dienst van de Catalogus SaaS direct konden verbruiken, adviseert Adobe hoogst gebruikend API Net (binnen App Builder). API Mesh kan APIs van de dienst van Catalog SaaS met andere noodzakelijke APIs van uw backend van PaaS (bijvoorbeeld, voorraadcontroles in real time van het transactionele gegevensbestand of de attributen van het douaneproduct niet volledig die aan de dienst van Catalog SaaS worden herhaald) verenigen in één enkel, presterend GraphQL eindpunt. Dit staat ook voor gecentraliseerde caching, authentificatie, en reactietransformatie toe.
* **Integreer Live Search en productaanbevelingen**: Configureer Live Search en Product Recommendations SaaS-diensten om [catalogusgegevens](https://experienceleague.adobe.com/nl/docs/commerce/live-search/install#configure-the-data) direct van je bestaande Adobe Commerce Catalog SaaS-dienst te importeren, die op zijn beurt wordt gevuld door je PaaS-backend.

**Voordeel**: Dit biedt een snellere weg naar een headless storefront en geavanceerde SaaS-merchandisingfuncties door gebruik te maken van een bestaande en operationele Catalog SaaS-dienst en de integratiepijplijn daarvan met je PaaS-backend. Het blijft echter afhankelijk van de PaaS-backend voor de primaire bron van catalogusgegevens en biedt niet de samenvoegingsmogelijkheden met meerdere bronnen die inherent zijn aan het nieuwe Composable Catalog Data Model. Deze optie is een geldig opstapje naar een volledigere samenstelbare architectuur.

>[!TAB  Optie 2 - het Composable Model van Gegevens van de Catalogus ]

**keur het nieuwe Composable Model van Gegevens van de Catalogus (CCDM) goed**

Dit is de strategische, toekomstbestendige aanpak voor het inzetten van Adobe Commerce Optimizer. CCDM verstrekt een flexibele, scalable, en verenigde catalogusdienst die voor multi-bron gegevenssamenvoeging en dynamische handel wordt ontworpen.

* **Inname van Gegevens en eenmaking**
   * Begin door product en catalogusgegevens van uw bestaande instantie Adobe Commerce PaaS (en/of andere PIM/ERP systemen) in het nieuwe Composable Model van de Gegevens van de Catalogus (CCDM) op te nemen.
   * Wijs bestaande productattributen aan het flexibele schema CCDM in kaart. Prioriteit geven aan kritieke productgegevens voor eerste inname.
   * Stel robuuste gegevenspijpleidingen voor ononderbroken synchronisatie in. Dit kan het volgende inhouden:
      * **gebeurtenis-gedreven** (door App Builder): Gebruik Adobe I/O Events van uw instantie PaaS om openbaar-beschikbare of de toepassingen van de douaneApp Builder van Adobe teweeg te brengen. Deze toepassingen transformeren en duwen gegevensveranderingen (creeer, werk, en schrapping) aan CCDM door zijn APIs bij.
      * **Inname van de Partij**: Voor grote aanvankelijke ladingen of periodieke bulkupdates, gebruiks veilige dossieroverdrachten (bijvoorbeeld, CSV of JSON) aan een opvoerend gebied, dat door de innameservices van Adobe Experience Platform (AEP) in CCDM wordt verwerkt.
      * **Directe API integratie** (met de Orchestratie van App Builder): Voor complexere scenario&#39;s, kan App Builder als orchestratielaag dienst doen, die directe API vraag aan uw steun PaaS maken, die de gegevens transformeert, en het duwt aan CCDM.
* **Catalogusweergave en beleidsdefinitie**: Configureer catalogusweergaven (logische groeperingen voor unieke cataloguspresentatie, zoals winkelweergaven, regio&#39;s en B2B/B2C-segmenten) en definieer beleidsregels (regelsets voor productpresentatie, filtering en merchandising) binnen de CCDM. Dit maakt dynamische controle mogelijk over productassortimenten en weergavelogica per catalogusweergave.
* **Integreer Live Search en productaanbevelingen**: Zodra catalogusgegevens aanwezig zijn in CCDM, integreer dan Adobe&#39;s SaaS-gebaseerde Live Search en Product Recommendation-diensten. Deze maken gebruik van Adobe AI AI en machine learning-modellen voor superieure zoekrelevantie en gepersonaliseerde aanbevelingen, waarbij ze data direct van de CCDM consumeren.

**Voordeel**: Door catalogusbeheer en ontdekking te abstraheren naar CCDM en bijbehorende SaaS-diensten, behaal je verbeterde prestaties, krijg je AI-gedreven merchandisingmogelijkheden, stort je leesoperaties aanzienlijk af van je oude backend en maak je een robuuste &quot;peel-off&quot; van de top-of-funnel-ervaring mogelijk.

>[!ENDTABS]

#### &#x200B;3. Bouw je winkelfront uit met Edge Delivery Services

Met de opgezette merchandisingdatapijplijnen en externaliseerde aanpassingen verschuift de focus naar het bouwen van je high-performance frontend.

* **Aanvankelijke opstelling**: Opstelling uw project gebruikend het Boilerplate van Adobe Commerce Storefront voor Edge Delivery Services. Dit biedt een voorsprong zonder basiskennis die is gebaseerd op moderne webtechnologieën.
* **verbindt met de catalogusdiensten en het Netwerk van API**: Uw Opslag van Commerce zal gegevens hoofdzakelijk door GraphQL APIs verbruiken:
   * **Optie 1**: Vanuit de bestaande Catalog SaaS-dienst (via API Mesh) voor productinformatie en merchandisingregels.
   * **Optie 2**: Van CCDM voor productinformatie en merchandisingregels.
   * Vanuit API Mesh voor georkestreerde data van je legacy backend (PaaS-instantie) of aangepaste App Builder-diensten (bijvoorbeeld realtime inventaris, aangepaste productattributen en loyaliteitspunten).
* **Contentmigratie (AEM Services):** Migreer je bestaande statische content (bijvoorbeeld &quot;Over ons&quot;-pagina&#39;s, blogposts en marketingbanners) naar AEM Services, dat de Commerce Storefront aandrijft. Maak gebruik van de contentauthoringmogelijkheden van AEM en zorg ervoor dat assets geoptimaliseerd zijn voor Edge Delivery Services.
* **Ontwikkel kerncomponenten** van de UI: Bouw kritieke gebruikersinterfacecomponenten uit voor productdetailpagina&#39;s (PDP&#39;s), productlijstpagina&#39;s (PLP&#39;s) en algemene contentpagina&#39;s met behulp van Edge Delivery Services drop-in componenten en aangepaste React/Vue-componenten. Prioriteer kernhandelsstromen.
* **Integratie met bestaande winkelwagen/afreken:** Aanvankelijk zal de Edge Delivery Services-winkel een overdracht organiseren naar je bestaande Adobe Commerce PaaS (of een ander platform van derden) voor winkelwagenbeheer en afrekenen. Dit omvat doorgaans:
   * **Omleiding**: De gebruiker doorleiden naar de native winkelwagen- en afleen-URL&#39;s van het legacy-platform, waarbij de benodigde sessie- en winkelwagenidentificaties worden doorgegeven.
   * **Directe API-interactie** (met App Builder-orkestratie): Het bouwen van aangepaste cartridge- en checkout-UI-componenten binnen Edge Delivery Services die direct interactie hebben met de cartridge en afreken-API&#39;s van je PaaS-backend. Dit houdt vaak in dat App Builder als Backend-for-Frontend (BFF) wordt gebruikt om oproepen naar meerdere backend-diensten te coördineren (bijvoorbeeld PaaS-cartridge, betalingsgateways en verzendcalculators).

**Voordeel**: Levert een razendsnelle, SEO-geoptimaliseerde en zeer flexibele winkelervaring. Deze fase draagt direct bij aan een superieure klantervaring en legt de basis voor toekomstige frontend-innovatie.

#### &#x200B;4. Datamigratie (gefaseerd proces)

Datamigratie is een cruciaal en veelzijdig proces dat gelijktijdig wordt uitgevoerd met refactoring en winkelfrontontwikkeling, waardoor dataconsistentie en integriteit worden gewaarborgd.

* **Schreng en optimaliseer bestaande data**: Voer vóór een grootschalige migratie uitgebreide data-cleansing, deduplicatie en validatie uit op je bestaande PaaS-database. Deze proactieve stap is cruciaal om de overdracht van legacy-dataproblemen te minimaliseren en de kwaliteit van de data in de nieuwe omgeving te waarborgen.

**Bulkmigraties van data**

Bulkmigratie van data houdt in dat je een volledige datadump uit je Adobe Commerce PaaS-instantie neemt, die volledige dataset transformeert en deze in één keer importeert in Adobe Commerce als Cloud Service. Deze methode wordt doorgaans gebruikt voor de initiële populatie van data.

* **Tooling beschikbaarheid**: De specifieke [&#x200B; tooling van de bulkgegevensmigratie &#x200B;](./bulk-data.md) voor klantengebruik voor de bulkgegevensmigraties van eerste-partij Commerce zal door verzoek in Q1 2026 beschikbaar zijn. Als klanten vooraf hulp nodig hebben bij het migreren van bulkgegevens, kan Adobe de gegevensoverdracht namens hen op verzoek vergemakkelijken.

* **Proces**:
   * **Volledige data-export:** Haal een volledige dataset uit je Adobe Commerce PaaS-instantie (bijvoorbeeld producten, categorieën, klantaccounts, historische ordergegevens, statische blokken en paginainhoud).
   * **Datatransformatie**: Pas noodzakelijke transformaties toe om de geëxtraheerde data af te stemmen op de schemavereisten van de nieuwe Adobe Commerce as a Cloud Service-componenten, inclusief het Composable Catalog Data Model (CCDM) indien aangenomen, en alle andere relevante Adobe-diensten of databases. Dit kan aangepaste scripts of gespecialiseerde datamappingtools omvatten.
   * **Initiële import**: Importeer de getransformeerde volledige dataset in de respectievelijke componenten van Adobe Commerce as a Cloud Service. Voor product- en categoriegegevens vult dit de gekozen catalogusdienst (CCDM of bestaande Catalogus SaaS). Voor klant- en ordergegevens vult dit de transactionele backend of bijbehorende diensten in.
   * **Validatie**: Valideer de geïmporteerde data grondig om volledigheid, nauwkeurigheid en consistentie te waarborgen over alle nieuwe systemen.

**Iteratieve datamigraties**

Iteratieve datamigraties richten zich op het synchroniseren van incrementele wijzigingen en delta&#39;s van de bron-PaaS-instantie naar de nieuwe Cloud Service-componenten, waardoor de vernieuwing van data wordt gegarandeerd voorafgaand aan en na de cutover.

* **Beschikbaarheid** van tools: Tools die specifiek zijn ontworpen voor iteratieve datamigraties zullen in 2026 beschikbaar zijn.

* **Proces**:
   * **Delta-identificatie:** Stel mechanismen op om wijzigingen (creaties, updates en verwijderingen) in kritieke datasets in je PaaS-omgeving sinds de laatste synchronisatie te identificeren. Dit kan change data capture (CDC), tijdstempelvergelijkingen of gebeurtenisgebaseerde triggers omvatten.
   * **Ononderbroken synchronisatie**: Voer robuuste mechanismen voor ononderbroken, stijgende gegevenssynchronisatie van uw milieu PaaS aan de nieuwe componenten van Cloud Service (bijvoorbeeld, CCDM en transactionele backend) uit. Dit is van cruciaal belang voor het behoud van de gegevensversheid en het minimaliseren van downtime tijdens het overslaan.
   * **Hefboomwerking gebeurtenissen**: Gebruik Adobe I/O Events waar mogelijk om de acties van App Builder voor real time of bijna updates in real time van uw instantie PaaS aan de nieuwe diensten teweeg te brengen. Bijvoorbeeld, kon een productupdate in PaaS een gebeurtenis teweegbrengen die de overeenkomstige ingang in CCDM bijwerkt.
   * **API-gedreven updates**: Voor gegevens die niet gebeurtenis-gedreven zijn, gebruik geplande API vraag (door App Builder of andere integratieplatforms) om veranderingen van PaaS te trekken en hen aan de nieuwe systemen te duwen.
   * **de behandeling van de Fout en controle**: Voer robuuste fout behandeling, registreren, en controle voor alle iteratieve gegevenspijpleidingen uit om gegevensintegriteit te verzekeren wordt gehandhaafd door het proces.

### Postmigratie en lopende operaties

**DNS cutover &amp; go-live:**

* Plan de DNS-cutover zorgvuldig met minimale uitvaltijd.
* Controleer de gezondheid en prestaties van de site direct na de lancering.

**post-lanceringsverrichtingen:**

**het Ontmantelen milieu van PaaS:**

* Oude PaaS-instanties en gegevens na de validatieperiode veilig archiveren of verwijderen.

**Lopende ontwikkelingswerkschema:**

* Omvat de versieloze aard van [!DNL Adobe Commerce as a Cloud Service], die ononderbroken kleine plaatsingen eerder dan grote verbeteringen heeft.
* Gebruik Cloud Manager voor het beheer van omgevingen en implementaties.
* Gebruik App Builder voor het uitbreiden van functionaliteit zonder dat dit invloed heeft op de kern.

**Controle, prestaties en veiligheid:**

* De prestaties, fouten en beveiligingslogboeken van de site voortdurend controleren.
* Gebruik ingebouwde beveiligingsfuncties van Adobe en volg de beste werkwijzen.

**Opleiding en documentatie:**

* Train nieuwe ontwikkelaars en zakelijke gebruikers op het [!DNL Adobe Commerce as a Cloud Service] -platform en de workflows.
* Houd up-to-date interne documentatie voor aangepaste integraties en processen.
