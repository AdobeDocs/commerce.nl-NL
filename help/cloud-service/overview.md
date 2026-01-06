---
title: '[!DNL Adobe Commerce as a Cloud Service] overzicht'
description: Leer over de belangrijkste eigenschappen en de voordelen van  [!DNL Adobe Commerce as a Cloud Service].
feature: App Builder, GraphQL, Integration, Saas
role: Admin, Developer, User, Leader
level: Beginner
exl-id: 1b7e2731-4a10-4c2b-9bfc-8945729ed523
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 3fe22d47b6fd6cf1077cbd4644ffad08f55826ca
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 0%

---


# [!DNL Adobe Commerce as a Cloud Service] overzicht

[!DNL Adobe Commerce as a Cloud Service] biedt flexibiliteit, schaalbaarheid en efficiëntie door bedrijven in staat te stellen digitale bewerkingen te leveren en snel te schalen en tegelijk de innovatie te versnellen. Adobe-cloudinfrastructuur past automatisch bronnen aan om te voldoen aan de piekvereisten voor verkeer, bestellingen en catalogusbeheer.

In de volgende tabel worden de producten gemarkeerd die van kracht zijn [!DNL Adobe Commerce as a Cloud Service] :

<table style="table-layout:auto">
  <tr>
    <td align="left">
      <img src="../assets/icon-checkmark-circle-outline.svg" alt="vinkje" align="center"> <strong> Commerce Storefront </strong>
    </td>
    <td align="left">
      Naar de klant gerichte interface waar klanten door producten bladeren en producten kopen
    </td>
  </tr>
  <tr>
    <td align="left">
      <img src="../assets/icon-checkmark-circle-outline.svg" alt="vinkje" align="center"> <strong> Merchandising Services </strong>
    </td>
    <td align="left">
      De diensten van de steun die productcatalogi, tarifering, en inventaris beheren
    </td>
  </tr>
  <tr>
    <td align="left">
      <img src="../assets/icon-checkmark-circle-outline.svg" alt="vinkje" align="center"> <strong> Visuals van het Product </strong>
    </td>
    <td align="left">
      Digitaal middelenbeheer voor productafbeeldingen en media
    </td>
  </tr>
  <tr>
    <td align="left">
      <img src="../assets/icon-checkmark-circle-outline.svg" alt="vinkje" align="center"> <strong> Platform van de Ontwikkelaar </strong>
    </td>
    <td align="left">
      Core development tools and APIs for building custom functionaliteit
    </td>
  </tr>
</table>

## Architectuur

Bekijk de volgende video voor een korte inleiding op de [!DNL Adobe Commerce as a Cloud Service] -architectuur. Diagrammen die de architectuur illustreren worden verstrekt onder de video.

>[!VIDEO](https://video.tv.adobe.com/v/3443232?learn=on)

Dit diagram illustreert de gegevensstroom tussen [!DNL Adobe Commerce as a Cloud Service] en alle oplossingen van Adobe Experience Cloud.

![ het stroomdiagram dat van Gegevens [!DNL Adobe Commerce as a Cloud Service] integratie met [!DNL Adobe Experience Cloud] oplossingen ](./assets/data-flow.svg){zoomable="yes"} toont

## Commerce Storefront

Gebruik Adobe [[!DNL Commerce Storefront] ](https://experienceleague.adobe.com/developer/commerce/storefront) aangedreven door [!DNL Edge Delivery Services] om in enkele minuten rijke ervaringen op te doen met eenvoudige, op documenten gebaseerde ontwerpen of visuele bewerkingen met [!DNL Storefront Builder] .

[!DNL Commerce Storefront] heeft een volledig ontkoppelde architectuur die alle Merchandising Services en gegevens via een GraphQL API-laag biedt. Deze architectuur staat teams toe om hun frontends onafhankelijk van de Stichting van Commerce te ontwikkelen, die de behendigheid verstrekt om nieuwe aanraakpunten met nieuwe technologieën te bouwen en te testen.

>[!NOTE]
>
>[!DNL Adobe Commerce as a Cloud Service] biedt geen ondersteuning voor Luma-storefronts. Als u van Adobe Commerce op Wolk of op-gebouw migreert, zie [ bestaande storefronts ](https://experienceleague.adobe.com/developer/commerce/storefront/discovery/#existing-storefronts) voor begeleiding bij het overgaan.

## Handelsbemiddeling en betalingsdiensten

Adobe biedt een uitgebreide reeks intelligente, composable merchandising-services waarmee u uw belangrijkste bedrijfsdoelen kunt ondersteunen. Deze services bieden ook API&#39;s die essentieel zijn voor het optimaliseren van prestaties op schaal.

- [ Levend Onderzoek ](../live-search/overview.md) - lever slimmere, snellere en relevante resultaten voor kopers met dit AI-Gerichte onderzoekshulpmiddel.
- [ Aanbevelingen van het Product ](../optimizer/merchandising/recommendations/overview.md) - voeg op AI-Gebaseerde aanbevelingen toe die op verkoopgedrag, populaire tendensen, productgelijkenis, en meer worden gebaseerd.
- [ de Dienst van de Catalogus ](../catalog-service/guide-overview.md) - geef uw klanten een geoptimaliseerde productervaring terwijl het opvoeren van prestaties, verbeterend scalability, en verhogend omzettingen.
- [ - De klantentevredenheid van de 1} Aandrijving van de Betaling van de Diensten van de 1} - aandrijving door diverse betalingsmethodes, met inbegrip van rentevrije betalingstermijnen aan te bieden, en één enkele mening in betalingsverwerking, orden, en facturen.](../payment-services/guide-overview.md)

## [!DNL Product Visuals powered by AEM Assets]

Product Visuals helpt het beheer van bedrijfsmiddelen te vereenvoudigen met behulp van een DAM-systeem (Digital Asset Management) dat kan worden geïntegreerd met Adobe Experience Manager voor het beheer van rich media-inhoud.

De integratie zorgt ervoor dat digitale elementen, zoals productafbeeldingen of marketinginhoud, dynamisch worden gekoppeld aan de juiste handelsentiteiten, waaronder producten en categorieën in Adobe Commerce, op basis van SKU of andere sleutelkenmerken.

[!DNL Product Visuals] is in [!DNL Adobe Commerce as a Cloud Service] offline beschikbaar en biedt enkele mogelijkheden van [!DNL AEM Assets] .

De native functies in [!DNL Adobe Commerce as a Cloud Service] bieden ook elementaire hulpmiddelen voor middelenbeheer voor het opslaan en beheren van digitale elementen.

Controleer de [ de integratie van AEM Assets ](../aem-assets-integration/overview.md) gids om meer over te leren hoe te om [!DNL Product Visuals powered by AEM Assets] met [!DNL Adobe Commerce as a Cloud Service] te integreren.

### [!DNL Product Visuals] of [!DNL AEM Assets]

Met de volgende vergelijking kunt u de beste optie selecteren voor uw inhoud die supply chain nodig heeft:

<table>
  <tr>
    <td align="left">
      <strong>[!DNL Product Visuals powered by AEM Assets]</strong>
      <ul>
        <li>Geïntegreerde, geautomatiseerde productimage en video Digital Asset Manager (DAM)</li>
        <li>Afbeeldingen vergroten, verkleinen, uitsnijden en omzetten</li>
        <li>Hoge snelheid voor het afspelen van afbeeldingen en video</li>
        <li>Afbeeldingsindelingen, -formaten en -kwaliteit optimaliseren op basis van de mogelijkheden van de clientbrowser</li>
        <li>Toegang tot Adobe Express en Adobe Firefly</li>
        <li>Gebruiksbeperkingen voor de capaciteit voor het leveren van beelden/video en gebruikerstoegang</li>
        <li>Geïntegreerde middelenkiezer</li>
      </ul>
    </td>
    <td align="center">
      <br><br><br><br><br><br><br><br><br><br><br>
      <img src="../assets/icon-double-chevron-right.svg" alt="chevron" width="100">
    </td>
    <td align="left">
      <strong> AEM Assets </strong>
      <ul>
        <li>Alle mogelijkheden van producthandleidingen</li>
        <li>Digital Asset Manager (DAM) voor volledige marketing</li>
        <li>Onbeperkte gebruikers (betaal per gebruiker)</li>
        <li>Onbeperkte levering van afbeeldingen en video</li>
        <li>Geavanceerde functionaliteit voor middelenbeheer:</li>
        <ul>
          <li>360° centrifuges en interactieve viewers</li>
          <li>Ondersteuning voor 3D-modellen en overweldigende inhoud</li>
          <li>PDF-ondersteuning</li>
          <li>Slim uitsnijden met AI-voeding</li>
          <li>Dynamische afbeeldingssjablonen</li>
          <li>Slimme tags toepassen</li>
          <li>Tracering en analyse van de prestaties van bedrijfsmiddelen</li>
        </ul>
      </ul>
    </td>
  </tr>
    <tr>
    <td align="center" colspan="3">
      <strong> Adobe-branded integratie is beschikbaar voor gemakkelijke migratie tussen dienstenaanbod.</strong>
    </td>
  </tr>
</table>

## Developer Platform

Adobe biedt ontwikkelaars uitgebreide uitbreidingspunten en tools om toepassingen te maken die Commerce Foundation-mogelijkheden uitbreiden en integreren met systemen van derden (zoals CRM&#39;s, ERP&#39;s en PIM&#39;s). Met deze gereedschappen worden de totale eigendomskosten van het platform als volgt verminderd:

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

[!DNL Commerce Foundation] biedt een veilig geautomatiseerd hostplatform en functies voor zelfbediening voor het beheer van uw Commerce-toepassing in een cloud-native omgeving.

Belangrijkste kenmerken zijn:

- Vereenvoudigd aan boord
- Naadloze upgrades
- Integraties van derden

### Vereenvoudigd aan boord

Start sandbox- en productieinstanties binnen enkele minuten met de zelfbedieningsportal van [!UICONTROL Commerce Cloud Manager] . Alles wat u nodig hebt, inclusief Merchandising Services, een Commerce-instantie zonder kop en [!DNL App Builder] , wordt automatisch geconfigureerd en geïntegreerd met uw instanties.

Zie [ Begonnen worden ](getting-started.md) om te leren hoe te om de instanties van Commerce tot stand te brengen en te beheren.

### Naadloze upgrades

Toegang tot de nieuwste functies en verbeteringen zonder dat u handmatig hoeft te upgraden. Door de voortdurende levering van nieuwe functies en updates is het niet nodig om handmatig te patchen, zodat u altijd toegang hebt tot de nieuwste mogelijkheden tegen lage totale eigendomskosten.

Bij het gebruikelijke upgradeproces voor Adobe Commerce op Cloud ging het om het maken van back-ups, het klonen van instanties, het uitvoeren van compatibiliteitsgereedschappen en het oplossen van codeconflicten. Dat is niet meer nodig met [!DNL Adobe Commerce as a Cloud Service] . Adobe stuurt u meldingen in de app wanneer nieuwe functies en beveiligingsupdates zijn uitgebracht. U hebt een periode van 30 dagen om de nieuwe mogelijkheden in uw zandbakinstanties te evalueren alvorens de updates automatisch op uw productiemilieu&#39;s worden toegepast.

>[!NOTE]
>
>Adobe garandeert achterwaartse compatibiliteit voor alle updates. Dit betekent dat wanneer de updates worden toegepast, zij bestaande functionaliteit of aanpassingen niet zullen breken die aan het [ API-eerste rekbaarheids ](https://developer.adobe.com/commerce/extensibility/) model houden.

### Integraties van derden

De ontwikkelaars kunnen uitvoerige [ GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/) en [ REST APIs ](https://developer.adobe.com/commerce/webapi/rest/) gebruiken om [!DNL Commerce Foundation] met derdesystemen te integreren en de mogelijkheden van Commerce uit te breiden.

<!-- ## Experience Cloud integration

[!DNL Adobe Commerce as a Cloud Service] integrates with all Experience Cloud solutions to deliver [personalized commerce experiences at scale](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

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
