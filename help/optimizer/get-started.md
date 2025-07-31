---
title: Aan de slag
description: Leer hoe te beginnen met  [!DNL Adobe Commerce Optimizer].
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: de57d93d-e156-45c1-86aa-de29a8c34bd2
source-git-commit: f1861e890ec661d441b6f2c9b0c0cd54b4c20ece
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 0%

---

# Aan de slag

Deze handleiding begeleidt u bij het instellen van [!DNL Adobe Commerce Optimizer] van het begin tot het einde. Terwijl deze gids alle rollen behandelt, zie de [ documentatie van de ontwikkelaar ](https://developer.adobe.com/commerce/services/optimizer/) voor gedetailleerde ontwikkelaar-specifieke inhoud.

## Vereisten

Voordat u begint, moet u controleren of:

- **de rekening van Adobe Experience Cloud** met [!DNL Adobe Commerce Optimizer] rechten
- **beheerdertoegang van de Organisatie** om instanties tot stand te brengen en gebruikers te beheren
- **GitHub rekening** (voor het laden van steekproefgegevens en storefront ontwikkeling)
- **Basis begrip** van e-commerceconcepten

## Handleiding Snel starten

Voer de volgende essentiële stappen uit om uw [!DNL Adobe Commerce Optimizer] -omgeving actief te maken:

### Stap 1. Een instantie maken

1. Login aan [ Adobe Experience Cloud ](https://experience.adobe.com/).
1. Navigeer aan **Commerce** > **Manager van Commerce Cloud**.
1. Klik **toevoegen Instantie** > **Commerce Optimizer**.

   ![ creeer instantie ](./assets/create-aco-instance.png){width="60%" zoomable="yes"}

1. Instantie-instellingen configureren:
   - **Naam**: Beschrijvende naam (bijvoorbeeld, &quot;Mijn Sandbox van het Bedrijf&quot;)
   - **Beschrijving**: Korte beschrijving van doel
   - **Gebied**: Selecteer uw aangewezen gebied
   - **Type van Milieu**: Begin met a **zandbak** milieu voor het testen

1. Klik **toevoegen Instantie**.

   De Cloud Manager wordt bijgewerkt en bevat nu uw nieuwe exemplaar. Voor details bij de toegang tot van en het beheren van het, zie [ een instantie ](#manage-an-instance) leiden.

>[!NOTE]
>
>Sandbox-exemplaren zijn beperkt tot Noord-Amerika. U kunt het gebied na het maken niet wijzigen.

### Stap 2. Uw omgeving instellen

Nadat u de instantie hebt gemaakt:

1. [ beheer uw instantie ](#manage-an-instance) van de Manager van Commerce Cloud.
1. Opstelling catalogusmeningen en beleid gebruikend de [ gids van de Mening van de Catalogus ](./setup/catalog-view.md).
1. Vorm gebruikerstoegang gebruikend de [ gids van het Beheer van de Gebruiker ](./user-management.md).

### Stap 3. Voorbeeldgegevens toevoegen (optioneel)

Voor het testen en het leren, volg de [ instructies van de Gegevens van de Steekproef van de Lading ](#add-sample-data).

## Op rollen gebaseerde workflows

[!DNL Adobe Commerce Optimizer] de opstelling en het beheer baseren zich op drie zeer belangrijke rollen. Elke rol heeft specifieke taken en verantwoordelijkheden:

![ Werkschema op hoog niveau ](./assets/high-level-workflow.png){zoomable="yes"}

### Beheertaken

Beheerders beheren instanties, gebruikers en organisatorische instellingen.

| Taak | Beschrijving | Koppeling |
|---|---|---|
| **beheert Gebruikers** | Gebruikers, ontwikkelaars en beheerders toevoegen | [ Gebruikersbeheer ](./user-management.md) |
| **creeer Instanties** | Sandbox- en productieomgevingen instellen | [ creeer instantie ](#create-an-instance) |
| **vorm Toegang** | Catalogusweergaven en -beleid instellen | [ de Weergaven van de Catalogus ](./setup/catalog-view.md) |

### Ontwikkelingstaken

De ontwikkelaars behandelen technische implementatie en gegevensintegratie, met inbegrip van de taken van de platformarchitectuur.

| Taak | Beschrijving | Koppeling |
|---|---|---|
| **Toegang Developer Console** | Projecten maken en referenties genereren | [ Developer Console ](https://developer.adobe.com/developer-console/docs/guides/getting-started) |
| **Ingest Gegevens van de Catalogus** | Productgegevens van bestaande systemen importeren | [ Ingestie API van Gegevens ](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/using-the-api/) |
| **Opstellings Storefront** | Edge Delivery Services-storefront configureren | [ Opstelling Storefront ](./storefront.md) |

### Merchandisertaken

Handelaars optimaliseren en personaliseren de boodschapervaring door productontdekking en aanbevelingen. Zij gebruiken ook verkoopgegevens en analyses om strategische besluiten over productplaatsing, tarifering, en promoties op de winkel te nemen.

| Taak | Beschrijving | Koppeling |
|---|---|---|
| **Ontdekking van het Product** | Zoeken en filteren configureren | [ het Merchandising Overzicht ](./merchandising/overview.md) |
| **Aanbevelingen** | Aanbevelingen voor producten met een AI-processor instellen | [ Aanbevelingen van het Product ](./merchandising/recommendations/overview.md) |
| **Prestaties die** volgen | Meting van succes controleren | [ Metriek van het Succes ](./manage-results/success-metrics.md) |

## Een instantie beheren

1. Login aan [ Adobe Experience Cloud ](https://experience.adobe.com/).

1. Commerce Cloud Manager openen:
   - Onder **Snelle toegang**, klik **Commerce**.
   - Bekijk de beschikbare varianten.

1. Toegang tot uw instantie:

   Klik op de instantienaam om de [!DNL Adobe Commerce Optimizer] -toepassing te openen. Binnen de toepassing kunt u tussen verschillende [!DNL Adobe Commerce Optimizer] -instanties schakelen met behulp van de vervolgkeuzelijst boven aan de pagina:

   ![ Schakelaar van de Instantie ](./assets/context-switcher.png){zoomable="yes"}

   Alle weergegeven exemplaren behoren tot dezelfde organisatie. U kunt tussen instanties schakelen om gegevens en montages voor elk te bekijken, zoals tussen zandbak en productiemilieu&#39;s.

1. Instantiedetails ophalen:
   - Klik op het informatiepictogram naast de instantienaam.
   - Neem nota van het eindpunt van GraphQL, het eindpunt van de Dienst van de Catalogus voor gegevensopname, en identiteitskaart van de Instantie (die ook als `tenant ID` wordt bekend).

   ![ Details van de Instantie ](./assets/aco-instance-details.png){width="60%" zoomable="yes"}

   Het eindpunt en instantieidentiteitskaart (huurder ID) details worden vereist om met frontend toepassingen en achterste systemen te integreren. De URL voor toegang tot de toepassing [!DNL Adobe Commerce Optimizer] wordt hier ook gegeven.

   Niet alle Adobe Commerce Optimizer-gebruikers hebben toegang tot Cloud Manager en de instantiedetails. De toegang hangt van de rol en de toestemmingen af die aan de gebruikersrekening worden toegewezen. Als u geen toegang hebt, neemt u contact op met uw organisatiebeheerder om de instantiedetails op te halen.

1. Naam en beschrijving van exemplaar bewerken:
   - Klik **uitgeven** pictogram naast een instantienaam.
   - Werk de naam en beschrijving naar wens bij.
   - Klik **sparen**.

   U kunt de opties voor zoeken en filteren ook gebruiken om snel naar specifieke varianten te zoeken.

## Voorbeeldgegevens toevoegen

Adobe biedt een GitHub-opslagplaats met voorbeeldgegevens en -gereedschappen waarmee u functies van [!DNL Adobe Commerce Optimizer] kunt leren en testen.
De steekproefgegevens zijn gebaseerd op het [ bedrijfscase van het Carvelo ](./use-case/admin-use-case.md) en omvat:

- Productcatalogus met auto-onderdelen
- Meerdere prijzenboeken en prijsscenario&#39;s
- Catalogusweergaven en -beleid voor verschillende dealers
- Volledige voorbeelden van end-to-end workflows

**Laad de steekproefgegevens:**

1. Heb toegang tot de bewaarplaats GitHub:
   - Bezoek de [ Opslag van de Ingestie van de Gegevens van de Catalogus van de Steekproef ](https://github.com/adobe-commerce/aco-sample-catalog-data-ingestion)
   - Volg de installatie-instructies in het README-bestand van de gegevensopslagruimte.

2. Voer de inname uit:
   - Gebruik de beschikbare scripts om voorbeeldgegevens in uw Adobe Commerce Optimizer-testomgeving te laden.
   - Verifieer dat de gegevens in uw [ Synchronisatie van Gegevens ](./setup/data-sync.md) pagina verschijnen.

3. Opruimen (optioneel):

   Verwijder de voorbeeldgegevens met behulp van het script `reset.js` dat is opgenomen in de broncode van de voorbeeld-gegevensloader.

## Volgende stappen

Na voltooiing van de installatie:

1. Opzetten van uw winkelcentrum:
   - Vorm [ Edge Delivery Services storefront ](./storefront.md)
   - Verbinding maken met uw catalogusgegevens

1. Ontdek de draagtas van Carvelo:
   - Volg het [ werkschema van begin tot eind ](./use-case/admin-use-case.md)
   - Praktijken met echte scenario&#39;s

1. Handelsversie configureren:
   - Opstelling [ productontdekking ](./merchandising/overview.md)
   - Creeer [ aanbevelingen ](./merchandising/recommendations/overview.md)

1. Monitorprestaties:
   - De metriek van het spoor [ succes ](./manage-results/success-metrics.md)
   - Analyseer [ onderzoeksprestaties ](./manage-results/search-performance.md)

## Problemen oplossen

### Algemene kwesties

| Probleem | Oplossing |
|---|---|
| **kan geen instantie tot stand brengen** | Controleer of u [!DNL Adobe Commerce Optimizer] rechten en beheerdersmachtigingen hebt. |
| **Instantie verschijnt niet** | Controleer uw Adobe IMS-organisatie en vernieuw de pagina. |
| **heeft geen toegang tot instantie** | Zorg ervoor dat u als gebruiker in de Admin Console wordt toegevoegd. |
| **gegevens van de Steekproef laden niet** | Verifieer uw instantiereferenties en API eindpunten. |

### Hulp vragen

- **Middelen van de Ontwikkelaar**: [ Documentatie van de Ontwikkelaar ](https://developer-stage.adobe.com/commerce/services/composable-catalog/)
- **Bron van de Storefront**: [ Documentatie van Commerce Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL)
- **Steun**: [ de middelen van de Steun van Adobe Commerce ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/overview)
