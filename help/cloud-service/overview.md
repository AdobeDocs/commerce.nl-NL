---
title: '[!DNL Adobe Commerce as a Cloud Service] overzicht'
description: Leer over de belangrijkste eigenschappen en de voordelen van  [!DNL Adobe Commerce as a Cloud Service].
feature: App Builder, GraphQL, Integration, Saas
role: Admin, Architect, Developer, User
exl-id: 1b7e2731-4a10-4c2b-9bfc-8945729ed523
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 7102feff1364b3b5715b4acd7f4cf013fa783eae
workflow-type: tm+mt
source-wordcount: '1165'
ht-degree: 0%

---

# [!DNL Adobe Commerce as a Cloud Service] overzicht

{{accs-early-access}}

[!DNL Adobe Commerce as a Cloud Service] biedt flexibiliteit, schaalbaarheid en efficiëntie door bedrijven in staat te stellen digitale bewerkingen te leveren en snel te schalen en innovatie te versnellen. Adobe-cloudinfrastructuur past automatisch bronnen aan om te voldoen aan de piekvereisten voor verkeer, bestellingen en catalogusbeheer.

In de volgende afbeelding worden de producten gemarkeerd die [!DNL Adobe Commerce as a Cloud Service] van kracht maken:

![[!DNL Adobe Commerce as a Cloud Service] productstapel ](./assets/product-stack.svg){align="center" zoomable="yes"}

>[!BEGINSHADEBOX]

![ info ](assets/Smock_InfoOutline_18_N.svg) als u aan het [!DNL Adobe Commerce as a Cloud Service] vroege toegangsprogramma zou willen deelnemen, voltooi [ deze vorm ](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4WOxhjY2doZPikS2hIbfmL5URFZXTE5TUk9PMUw0OFdOWTBNNlI3UTlNMS4u&amp;route=shorturl).

>[!ENDSHADEBOX]

## Architectuur

Bekijk de volgende video voor een korte inleiding op de [!DNL Adobe Commerce as a Cloud Service] -architectuur. Diagrammen die de architectuur illustreren worden verstrekt onder de video.

>[!VIDEO](https://video.tv.adobe.com/v/3443273?learn=on&captions=dut)

Dit diagram illustreert de gegevensstroom tussen [!DNL Adobe Commerce as a Cloud Service] en alle oplossingen van Adobe Experience Cloud.

![[!DNL Adobe Commerce as a Cloud Service] architectuurdiagram ](./assets/data-flow.svg){zoomable="yes"}

## Commerce Storefront

Het gebruik Adobe [ Commerce Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront?lang=nl-NL) aangedreven door Edge Delivery Services om rijke ervaringen in notulen met eenvoudige document-gebaseerde creatie of visuele het uitgeven met de Bouwer van de Storefront tot stand te brengen.

Commerce Storefront heeft een volledig ontkoppelde architectuur die alle Merchandising Services en gegevens biedt via een GraphQL API-laag. Deze architectuur staat teams toe om hun frontends onafhankelijk van de Stichting van Commerce te ontwikkelen, die de behendigheid verstrekt om nieuwe aanraakpunten met nieuwe technologieën te bouwen en te testen.

>[!NOTE]
>
>[!DNL Adobe Commerce as a Cloud Service] biedt geen ondersteuning voor Luma-storefronts. Als u van Adobe Commerce op Wolk of op-gebouw migreert, zie [ bestaande storefronts ](https://experienceleague.adobe.com/developer/commerce/storefront/discovery/?lang=nl-NL#existing-storefronts) voor begeleiding bij het overgaan.

## Handelsbemiddeling en betalingsdiensten

Adobe biedt een uitgebreide reeks intelligente, composable merchandising-services waarmee u uw belangrijkste bedrijfsdoelen kunt ondersteunen. Deze services bieden ook API&#39;s die essentieel zijn voor het optimaliseren van prestaties op schaal.

- [ Levend Onderzoek ](../live-search/overview.md) - lever slimmere, snellere en relevante resultaten voor kopers met dit AI-Gerichte onderzoekshulpmiddel.
- [ Aanbevelingen van het Product ](../product-recommendations/overview.md) - voeg op AI-Gebaseerde aanbevelingen toe die op verkoopgedrag, populaire tendensen, productgelijkenis, en meer worden gebaseerd.
- [ Merchandising de Diensten die door Kanalen en Beleid ](../optimizer/catalog/overview.md) worden aangedreven - beheer grote en complexe productcatalogi met flexibele gegevens modellering om hoogst presterende, flexibele handelscatalogi te leveren die met bedrijfsstructuur en go-aan-markt strategieën worden gericht. Gebruik met [ Commerce Optimizer ](../optimizer/overview.md) om catalogusprestaties te optimaliseren en omzettingspercentages te verbeteren.
- [&#128279;](../payment-services/guide-overview.md) - De klantentevredenheid van de 1&rbrace; Aandrijving van de Betaling van de Diensten van de 1&rbrace; - aandrijving door diverse betalingsmethodes, met inbegrip van rentevrije betalingstermijnen aan te bieden, en één enkele mening in betalingsverwerking, orden, en facturen.

## Productvisa

Vereenvoudig het beheer van bedrijfsmiddelen met behulp van een robuust DAM-systeem (Digital Asset Management) dat kan worden geïntegreerd met Adobe Experience Manager voor het beheer van rich media-inhoud. De native functies in [!DNL Adobe Commerce as a Cloud Service] bieden ook elementaire hulpmiddelen voor middelenbeheer voor het opslaan en beheren van digitale elementen.

Zie [ activabeheer ](https://experienceleague.adobe.com/nl/docs/commerce-admin/content-design/aem-asset-management/aem-assets-integration) om meer te leren.

## Developer Platform

Adobe biedt ontwikkelaars uitgebreide uitbreidingspunten en tools voor het maken van toepassingen die Commerce Foundation-mogelijkheden uitbreiden en integreren met systemen van derden (zoals CRM&#39;s, ERPS en PIMS). Met deze gereedschappen worden de totale eigendomskosten van het platform als volgt verminderd:

- **Scalability** - De toepassingen kunnen afzonderlijk van de kernsoftware worden geschraapt, die voor grotere efficiency en vereenvoudigde verbeteringen toestaat.
- **Isolatie** - een geïsoleerd milieu betekent dat de ontwikkelaars hun uitbreidingen bij hun discretie kunnen bevorderen of wijzigen zonder op een kernversie te vertrouwen.
- **Technologische onafhankelijkheid** - de Ontwikkelaars kunnen kiezen welke technologiestapels en coderende talen die hun behoeften passen.

>[!TIP]
>
>De leverancier-gebouwde apps zijn ook beschikbaar voor installatie op [ Adobe Exchange ](https://exchange.adobe.com/).

Adobe biedt de volgende ontwikkelaarsgereedschappen voor het maken van integratie- en aanpassingsprocessen:

- [**API Net voor Adobe Developer App Builder** ](https://developer.adobe.com/graphql-mesh-gateway/) - coördineer en combineer veelvoudige API, GraphQL, REST, en andere bronnen in één enkel, queryable eindpunt van GraphQL.
- [**App Builder** ](https://developer.adobe.com/app-builder/docs/overview/) - bouw en stel veilige en scalable Webtoepassingen op die de functionaliteit van Commerce uitbreiden en met derdeoplossingen integreren.
- [**Gebeurtenissen** ](https://developer.adobe.com/commerce/extensibility/events/) - de trekkers van de douanegebeurtenis van het Gebruik om met andere verlengbare ontwikkelingshulpmiddelen in wisselwerking te staan.
- [**Webhooks** ](https://developer.adobe.com/commerce/extensibility/webhooks/) - Gebruik webhooks om interactie tussen Commerce en derdesystemen automatisch teweeg te brengen.
- [**Admin UI SDK** ](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) - pas en verbeter Commerce Admin met nieuwe pagina&#39;s en eigenschappen voor uw handelaren aan.
- [**Uitrusting van de Aanzet van de Integratie** ](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/) - versnelt uw achterbureauintegratie met verwijzingsintegratie, op het instappen van manuscripten, en een gestandaardiseerde architectuur.

## Commerce Foundation

Commerce Foundation biedt een veilig geautomatiseerd hostplatform en functies voor zelfbediening voor het beheer van uw Commerce-toepassing in een cloud-native omgeving.

Belangrijkste kenmerken zijn:

- Vereenvoudigd aan boord
- Naadloze upgrades
- Integraties van derden

### Vereenvoudigd aan boord

Start sandbox- en productieinstanties binnen enkele minuten met de zelfbedieningsportal van [!UICONTROL Commerce Cloud Manager] . Alles wat u nodig hebt, inclusief Merchandising Services, een Commerce-instantie zonder kop en App Builder, wordt automatisch geconfigureerd en geïntegreerd met uw instanties.

Zie [ Begonnen worden ](getting-started.md) om te leren hoe te om de instanties van Commerce tot stand te brengen en te beheren.

### Naadloze upgrades

Toegang tot de nieuwste functies en verbeteringen zonder dat u handmatig hoeft te upgraden. Door de voortdurende levering van nieuwe functies en updates is het niet nodig om handmatig te patchen, zodat u altijd toegang hebt tot de nieuwste mogelijkheden tegen lage totale eigendomskosten.

Bij het gebruikelijke upgradeproces voor Adobe Commerce op Cloud ging het om het maken van back-ups, het klonen van instanties, het uitvoeren van compatibiliteitsgereedschappen en het oplossen van codeconflicten. Dat is niet meer nodig met [!DNL Adobe Commerce as a Cloud Service] . Adobe stuurt u meldingen in de app wanneer nieuwe functies en beveiligingsupdates zijn uitgebracht. U hebt een periode van 30 dagen om de nieuwe mogelijkheden in uw zandbakinstanties te evalueren alvorens de updates automatisch op uw productiemilieu&#39;s worden toegepast.

>[!NOTE]
>
>Adobe garandeert achterwaartse compatibiliteit voor alle updates. Dit betekent dat wanneer de updates worden toegepast, zij bestaande functionaliteit of aanpassingen niet zullen breken die aan het [ API-eerste rekbaarheids ](https://developer.adobe.com/commerce/extensibility/) model houden.

### Integraties van derden

De ontwikkelaars kunnen uitvoerige [ GraphQL en REST APIs ](https://developer.adobe.com/commerce/services/cloud/guides/) gebruiken om de Stichting van Commerce met derdesystemen te integreren en de mogelijkheden van Commerce uit te breiden.

<!-- ## Experience Cloud integration

[!DNL Adobe Commerce as a Cloud Service] integrates with all Experience Cloud solutions to deliver [personalized commerce experiences at scale](https://experienceleague.adobe.com/nl/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Data Connection](../data-connection/overview.md) unlocks insights about your shoppers' buying behavior so that you can create personalized shopping experiences across all channels with other Adobe Digital Experience products. -->

## Voordelen

In de volgende secties vindt u informatie over de voordelen die [!DNL Adobe Commerce as a Cloud Service] biedt voor bedrijven en IT-managers.

### Zakelijke leiders

- **de opbrengst van de Vergroting**: De organische verkeer van de aandrijving met een krachtige storefront die SEO versterkt. Maak persoonlijke ervaringen die conversie met rijke gegevens stimuleren.
- **de verrichtingen van de Schaal**: De auto-schrapende diensten voldoen aan de piekeisen van uw zaken met 99.9% beschikbaarheid. Meerdere merken en regio&#39;s implementeren en B2B en B2C ondersteunen vanuit één instantie. Ondersteuning voor grote en complexe productcatalogi met flexibele gegevensmodellen.
- **Merchandiser van de Verhoging productiviteit**: De aangedreven AI diensten van het gebruik om omzetting te verbeteren. Experimenteer native, rechtstreeks in de winkel. Beheer de storefront-ervaring om in enkele minuten rijke ervaringen te creëren met eenvoudige documenten of een visuele editor.
- **Lagere totale kosten van eigendom (TCO) en versnelt innovatie**: altijd de bijgewerkte diensten geven u onmiddellijk toegang tot nieuwe eigenschappen. Activeer nieuwe mogelijkheden door toepassingen eenvoudig van de markt te installeren. Maak middelen vrij van vervelend onderhoud om zich te concentreren op het bouwen van nieuwe mogelijkheden.

### Toonaangevende functies op het gebied van informatietechnologie

- **Snelle levering**: Krijg snel begonnen met zelfbediening levering in notulen. Alle services zijn vooraf geconfigureerd om naadloos samen te werken en sneller aan de slag te gaan. Stel sandboxen in voor experimenteren met ontwikkelaars.
- **Lage kosten van eigendom**: Geen meer verbeteringen met altijd bijgewerkte diensten. Blijf veilig en voldoet aan de nieuwste beveiligingspatches die automatisch op u zijn toegepast. Automatisch schalen om te voldoen aan de meest veeleisende werklasten.
- **Krachtige storefront**: Creeer rijke ervaringen in notulen met eenvoudig document-gebaseerd auteursrecht of een visuele redacteur. Gebruik door AI aangedreven verkoopservices om de conversie te verbeteren. Native experimenteren in de storefront.
- **Snellere innovatie**: Maak middelen van vervelend onderhoud vrij om zich op de bouw van nieuwe mogelijkheden te concentreren die bedrijfswaarde leveren. Gebruik uitgebreide uitbreidbaarheid en op standaarden gebaseerde technologieën (JavaScript, HTML, CSS en low-code tools) om verschillende ervaringen op te bouwen. Installeer apps van derden met een klik om nieuwe mogelijkheden aan uw handelsplatform toe te voegen.
