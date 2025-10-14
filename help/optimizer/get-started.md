---
title: Aan de slag
description: Leer hoe te beginnen met  [!DNL Adobe Commerce Optimizer].
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: de57d93d-e156-45c1-86aa-de29a8c34bd2
source-git-commit: c27b2a8c7dffdcc5d5195cf809d5b475f3e01059
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 0%

---

# Aan de slag

Deze handleiding begeleidt u bij het instellen van [!DNL Adobe Commerce Optimizer] van het begin tot het einde. Terwijl deze gids alle rollen behandelt, zie de [&#x200B; documentatie van de ontwikkelaar &#x200B;](https://developer.adobe.com/commerce/services/optimizer/) voor gedetailleerde ontwikkelaar-specifieke inhoud.

## Vereisten

Voordat u begint, moet u controleren of:

- **de rekening van Adobe Experience Cloud** met [!DNL Adobe Commerce Optimizer] rechten
- **beheerdertoegang van de Organisatie** om instanties tot stand te brengen en gebruikers te beheren
- **GitHub rekening** voor het laden van steekproefgegevens en storefront ontwikkeling
- **Basis begrip** van e-commerceconcepten

## Handleiding voor snel starten

Voer de volgende essentiële stappen uit om uw [!DNL Adobe Commerce Optimizer] -omgeving actief te maken:

### Stap 1. Een instantie maken

1. Login aan [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com/).
1. Navigeer aan **Commerce** > **Manager van Commerce Cloud**.
1. Klik **toevoegen Instantie** > **Commerce Optimizer**.

   ![&#x200B; de Manager van de Wolk van de Handel van Adobe voegt het scherm van de Instantie voor het creëren van een milieu van Commerce Optimizer toe &#x200B;](./assets/create-aco-instance.png){width="60%" zoomable="yes"}

1. Instantie-instellingen configureren:
   - **Naam van de Instantie**: Beschrijvende naam (bijvoorbeeld, &quot;Mijn Sandbox van het Bedrijf&quot;)
   - **Beschrijving**: Korte beschrijving van doel
   - **Type van Milieu**: Begin met a **zandbak** milieu voor het testen
   - **Gebied**: Selecteer uw aangewezen gebied

1. Klik **toevoegen Instantie**.

   De Cloud Manager wordt bijgewerkt en bevat nu uw nieuwe exemplaar. Voor details bij de toegang tot van en het beheren van het, zie [&#x200B; een instantie &#x200B;](#manage-instances) leiden.

>[!NOTE]
>
>U kunt alleen sandboxomgevingen maken in de Noord-Amerikaanse regio. Nadat u een instantie hebt gemaakt, kunt u het gebied niet meer wijzigen.

### Stap 2. Uw omgeving instellen

Nadat u de instantie hebt gemaakt:

1. [&#x200B; beheer uw instantie &#x200B;](#manage-instances) van de Manager van Commerce Cloud.
1. Vorm gebruikerstoegang gebruikend de [&#x200B; Gids van het Beheer van de Gebruiker &#x200B;](./user-management.md).

### Stap 3. Voorbeeldgegevens toevoegen (optioneel)

Voor het testen en het leren, volg de [&#x200B; instructies van de Gegevens van de Steekproef van de Lading &#x200B;](#add-sample-data).

## Op rollen gebaseerde workflows

[!DNL Adobe Commerce Optimizer] de opstelling en het beheer baseren zich op drie zeer belangrijke rollen. Elke rol heeft specifieke taken en verantwoordelijkheden:

![&#x200B; Op rol-gebaseerde werkschema voor de opstelling die van Adobe Commerce Optimizer beheerder, ontwikkelaar, en gebruikerstaken tonen &#x200B;](./assets/high-level-workflow.png){zoomable="yes"}

### Beheertaken

Beheerders beheren instanties, gebruikers en organisatorische instellingen.

| Taak | Beschrijving | Koppeling |
|---|---|---|
| **beheert Gebruikers** | Gebruikers, ontwikkelaars en beheerders toevoegen | [&#x200B; Gebruikersbeheer &#x200B;](./user-management.md) |
| **creeer Instanties** | Sandbox- en productieomgevingen instellen | [&#x200B; creeer instantie &#x200B;](#create-an-instance) |
| **beheert Instanties** | De status controleren, instantienaam en beschrijving bijwerken en sleutel-URL&#39;s ophalen voor toepassing en API-toegang | [&#x200B; beheert Instanties &#x200B;](#manage-instances) |
| **vorm Toegang** | Catalogusweergaven en -beleid instellen | [&#x200B; de Weergaven van de Catalogus &#x200B;](./setup/catalog-view.md) |

### Ontwikkelingstaken

De ontwikkelaars behandelen technische implementatie en gegevensintegratie, met inbegrip van de taken van de platformarchitectuur.

| Taak | Beschrijving | Koppeling |
|---|---|---|
| **Toegang Developer Console** | Projecten maken en referenties genereren | [&#x200B; Developer Console &#x200B;](https://developer.adobe.com/developer-console/docs/guides/getting-started) |
| **Ingest Gegevens van de Catalogus** | Productgegevens van bestaande systemen importeren | [&#x200B; Ingestie API van Gegevens &#x200B;](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/) |
| **Opstelling Storefront** | Edge Delivery Services-storefront configureren | [&#x200B; Opstelling Storefront &#x200B;](./storefront.md) |

### Merchandisertaken

Handelaars optimaliseren en personaliseren de boodschapervaring door productontdekking en aanbevelingen. Zij gebruiken ook verkoopgegevens en analyses om strategische besluiten over productplaatsing, tarifering, en promoties op de winkel te nemen.

| Taak | Beschrijving | Koppeling |
|---|---|---|
| **Ontdekking van het Product** | Zoeken en filteren configureren | [&#x200B; het Merchandising Overzicht &#x200B;](./merchandising/overview.md) |
| **Aanbevelingen** | Aanbevelingen voor producten met een AI-processor instellen | [&#x200B; Aanbevelingen van het Product &#x200B;](./merchandising/recommendations/overview.md) |
| **Prestaties die** volgen | Meting van succes controleren | [&#x200B; Metriek van het Succes &#x200B;](./manage-results/success-metrics.md) |

## Instanties beheren

Exemplaren beheren vanuit Commerce Cloud Manager.

>[!NOTE]
>
>Niet alle Adobe Commerce Optimizer-gebruikers hebben toegang tot Cloud Manager. De toegang hangt van de rol en de toestemmingen af die aan de gebruikersrekening worden toegewezen.

1. Login aan [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com/).

1. Commerce Cloud Manager openen:

   - Onder **Snelle toegang**, klik **Commerce**.
   - Bekijk de beschikbare varianten.

### Zoeken en filteren

Nadat u zich hebt aangemeld, worden op het dashboard alle Commerce-productinstanties weergegeven die in de organisatie beschikbaar zijn.
De kolom Product geeft aan voor welke Commerce-toepassing de instantie is ingericht.

![&#x200B; Dashboard die onderzoek en filteropties voor het productinstanties van de Wolk van de Handel van Adobe tonen &#x200B;](./assets/search-filter-instances.png){zoomable="yes"}

Met de gereedschappen Filter en Zoeken kunt u snel specifieke varianten zoeken op basis van datum, regio, maker, producttype, omgeving of status.

### De toepassing [!DNL Adobe Commerce Optimizer] openen

Zodra de app is geopend, kunt u eenvoudig schakelen tussen omgevingen als sandbox en productie om gegevens en instellingen voor elke omgeving weer te geven zonder terug te keren naar Commerce Cloud Manager.

1. Klik in Commerce Cloud Manager op de instantienaam om de toepassing [!DNL Adobe Commerce Optimizer] te openen.

1. Schakel tussen [!DNL Adobe Commerce Optimizer] -instanties zonder de toepassing te verlaten.

   De instantie drop-down maakt een lijst van alle Optimizer instanties beschikbaar in de organisatie. Selecteer de instantie die u wilt weergeven.

   ![&#x200B; de schakelaardropdown van de Instantie voor het selecteren van de milieu&#39;s van Adobe Commerce Optimizer &#x200B;](./assets/context-switcher.png){zoomable="yes"}

### Instantiedetails ophalen

Bekijk de instantiedetails door op het informatiepictogram naast uw instantienaam te klikken.

![&#x200B; Adobe Commerce Optimizer paneel dat van instantiedetails eindpunten en instantieidentiteitskaart &#x200B;](./assets/aco-instance-details.png){width="60%" zoomable="yes"} toont

Let op de volgende belangrijke informatie:

- **het eindpunt van GraphQL** om de catalogusgegevens van Commerce terug te winnen gebruikend Verkoop API
- **eindpunt van de Dienst van de Catalogus** voor gegevensopname die REST API gebruiken
- **Commerce Optimizer URL** om tot de [!DNL Adobe Commerce Optimizer] toepassing toegang te hebben
- **identiteitskaart van de Instantie**: unieke huurder identiteitskaart die de instantie identificeert

Als u een ontwikkelaar bent, hebt u deze gegevens nodig om uw ontwikkelomgeving in te stellen en verbinding te maken met de API&#39;s van [!DNL Adobe Commerce Optimizer] .

>[!NOTE]
>
>Voor toegang tot de instantiedetails hebt u de noodzakelijke toestemmingen in uw organisatie van Adobe IMS nodig. Neem contact op met de systeembeheerder als u de instantiedetails niet ziet of geen toegang hebt tot de toepassing.

### Instantienaam en beschrijving bewerken

Werk indien nodig de instantienaam en beschrijving bij.

1. Klik **uitgeven** pictogram naast een instantienaam.
1. Werk de **naam van de Instantie** en **Beschrijving** zoals nodig bij.
1. Klik **sparen**.

## Voorbeeldgegevens toevoegen

Adobe biedt een GitHub-opslagplaats met voorbeeldgegevens en -gereedschappen waarmee u functies van [!DNL Adobe Commerce Optimizer] kunt leren en testen.
De steekproefgegevens zijn gebaseerd op het [&#x200B; bedrijfscase van het Carvelo &#x200B;](./use-case/admin-use-case.md) en omvat:

- Productcatalogus met auto-onderdelen
- Meerdere prijzenboeken en prijsscenario&#39;s
- Catalogusweergaven en -beleid voor verschillende dealers
- Volledige voorbeelden van end-to-end workflows

**Laad de steekproefgegevens:**

1. Heb toegang tot de [&#x200B; Ingestie van de Gegevens van de Catalogus van de Steekproef &#x200B;](https://github.com/adobe-commerce/aco-sample-catalog-data-ingestion) bewaarplaats GitHub.

1. Volg de installatie-instructies in het README-bestand van de gegevensopslagruimte om de volgende taken uit te voeren:

   - Uw omgeving instellen
   - Voltooi het proces voor gegevensinvoer
   - Catalogusweergaven en -beleid maken met behulp van voorbeeldgegevens
   - Verifieer de gegevensopname door de gegevens van de Dienst van de Catalogus over de [&#x200B; pagina van de Synchronisatie van 0&rbrace; Gegevens te controleren &lbrace;](./setup/data-sync.md)

## Volgende stappen

Na voltooiing van de installatie:

1. Opzetten van uw winkelcentrum:
   - Vorm [&#x200B; Edge Delivery Services storefront &#x200B;](./storefront.md)
   - Verbinding maken met uw catalogusgegevens

1. Ontdek de draagtas van Carvelo:
   - Volg het [&#x200B; werkschema van begin tot eind &#x200B;](./use-case/admin-use-case.md)
   - Praktijken met echte scenario&#39;s

1. Handelsversie configureren:
   - Opstelling [&#x200B; productontdekking &#x200B;](./merchandising/overview.md)
   - Creeer [&#x200B; aanbevelingen &#x200B;](./merchandising/recommendations/overview.md)

1. Monitorprestaties:
   - De metriek van het spoor [&#x200B; succes &#x200B;](./manage-results/success-metrics.md)
   - Analyseer [&#x200B; onderzoeksprestaties &#x200B;](./manage-results/search-performance.md)

## Problemen oplossen

### Algemene kwesties

| Probleem | Oplossing |
|---|---|
| **kan geen instantie tot stand brengen** | Controleer of u [!DNL Adobe Commerce Optimizer] rechten en beheerdersmachtigingen hebt. |
| **Instantie verschijnt niet** | Controleer uw Adobe IMS-organisatie en vernieuw de pagina. |
| **heeft geen toegang tot instantie** | Zorg ervoor dat u als gebruiker in de Admin Console wordt toegevoegd. |
| **gegevens van de Steekproef laden niet** | Verifieer uw instantiereferenties en API eindpunten. |

### Hulp vragen

- **Middelen van de Ontwikkelaar**: [&#x200B; documentatie van de Ontwikkelaar &#x200B;](https://developer.adobe.com/commerce/services/optimizer/)
- **Bronnen van de Storefront**: [&#x200B; Commerce storefront documentatie &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL)
- **Leerprogramma&#39;s**: [&#x200B; zelfstudies van Commerce Optimizer &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/adobe-commerce-optimizer/overview)
- **Steun**: [&#x200B; de middelen van de Steun van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/overview)
