---
title: Vereisten voor zelfstudie
description: Leer meer over de voorwaarden en de stappen voor het instellen van zelfstudies voor Adobe Commerce as a Cloud Service, waaronder ontwikkelprogramma's voor extensies en winkels.
solution: Commerce
feature: App Builder, Cloud
feature-set: Commerce
role: Developer
level: Intermediate
type: Tutorial
source-git-commit: 1848c9dda4a1976e1bccb4d1f9d5a2e21540fc0b
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---

# Voorwaarden voor zelfstudie

Deze pagina maakt een lijst van de eerste vereisten en opstellingsstappen voor [!DNL Adobe Commerce as a Cloud Service] leerprogramma&#39;s, zoals het [&#x200B; leerprogramma van de classificatieuitbreiding &#x200B;](./ratings-extension.md) en het [&#x200B; verschepen zelfstudie van de methodeuitbreiding &#x200B;](./shipping-method-extension.md).

## Algemene voorwaarden

De volgende gereedschappen zijn vereist voor de ontwikkeling van extensies en winkels in deze zelfstudie.

* [!DNL Node.js] (version `22.x.x` ) en npm ( `9.0.0` of hoger): controleer de installatie met de volgende opdracht:

  ```bash
  node --version
  npm --version
  ```

* Installeer [&#x200B; Git &#x200B;](https://git-scm.com) - verifieer uw installatie:

  ```bash
  git --version
  ```

* Schelp
   * macOS/Linux: geen installatie vereist
   * Vensters: Het gebruik [&#x200B; Bash van de Git &#x200B;](https://git-scm.com/install) of [&#x200B; Subsysteem van Vensters voor Linux (WSL) &#x200B;](https://learn.microsoft.com/en-us/windows/wsl/install)

* Download AI-bijgewoonde winde, zoals [&#x200B; Cursor &#x200B;](https://cursor.com/download) (geadviseerd). Andere IDEs, zoals de Code van Claude, Gemini CLI, of Copilot worden ook gesteund, maar kon wijzigingen in de herinneringen en andere stappen in het leerprogramma vereisen.

## [!DNL Adobe Commerce as a Cloud Service] voorwaarden

* De [!DNL Adobe I/O CLI] installeren

  ```bash
  npm install -g @adobe/aio-cli
  ```

* Installeer [&#x200B; Adobe I/O CLI Commerce &#x200B;](https://github.com/adobe-commerce/aio-cli-plugin-commerce), [&#x200B; Adobe I/O CLI Runtime &#x200B;](https://github.com/adobe/aio-cli-plugin-runtime), en [&#x200B; App Builder CLI &#x200B;](https://github.com/adobe/aio-cli-plugin-app-dev) stoppen:

  ```bash
  aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce @adobe/aio-cli-plugin-app-dev @adobe/aio-cli-plugin-runtime
  ```

### Adobe Developer Console-voorwaarden

Stel een project in de Adobe Developer Console in met de vereiste API&#39;s en referenties.

1. Navigeer aan [&#x200B; Adobe Developer Console &#x200B;](https://developer.adobe.com/console){target="_blank"}.
1. Meld u aan met uw e-mail en wachtwoord.

#### Een nieuw project maken

Maak een App Builder-project in de Adobe Developer Console als host voor uw extensie.

1. Navigeer aan [&#x200B; Adobe Developer Console &#x200B;](https://developer.adobe.com/).
1. Klik op **[!UICONTROL Create project from a template]**.
1. Selecteer de sjabloon **[!UICONTROL App Builder]** .
1. Voer een **[!UICONTROL Project Title]** en **[!UICONTROL App Name]** in.
1. Controleer of het selectievakje **[!UICONTROL Include Runtime]** is gemarkeerd.

   ![&#x200B; Adobe Developer Console project verwezenlijking met het geselecteerde malplaatje van App Builder &#x200B;](../assets/app-builder-template.png){width="600" zoomable="yes"}

1. Klik op **[!UICONTROL Save]**.

#### API&#39;s toevoegen aan de werkruimte

Voeg de vereiste API&#39;s toe aan uw werkruimte van het werkgebied voor gebeurtenisbeheer en Commerce-integratie.

1. Klik op de werkruimte **[!UICONTROL Stage]** en herhaal vervolgens de volgende stappen voor elke API.

   ![&#x200B; werkruimte van het Stadium met Add de optie van de Dienst voor APIs &#x200B;](../assets/add-apis-workspace.png){width="600" zoomable="yes"}

1. Klik op **[!UICONTROL Add Service]** en selecteer **[!UICONTROL API]** .

1. Selecteer een van de volgende API&#39;s. Herhaal dit proces voor elke API hieronder:

   * **[!UICONTROL Adobe Services]** filter:
      * **[!UICONTROL I/O Management API]**
      * **[!UICONTROL I/O Events]** API
   * **[!UICONTROL Experience Cloud]** filter:
      * **[!UICONTROL Adobe I/O Events for Adobe Commerce]** API

1. Klik op **[!UICONTROL Next]**.

1. Klik op **[!UICONTROL Save configured API]**.

1. Herhaal de vorige stappen totdat u alle API&#39;s aan de werkruimte toevoegt.

   ![&#x200B; Workspace die alle vereiste met succes toegevoegde APIs tonen &#x200B;](../assets/apis-added.png){width="600" zoomable="yes"}

### De Adobe I/O CLI configureren

Verbind [!DNL Adobe I/O CLI] met uw organisatie, project, en werkruimte.

1. Wis om het even welke bestaande configuratie:

   ```bash
   aio config clear
   ```

1. Meld u aan met [!DNL Adobe I/O CLI] :

   ```bash
   aio auth login -f
   ```

1. Selecteer uw organisatie, project, en werkruimte gebruikend elk van de volgende bevelen:

   ```bash
   aio console org select
   ```

   ```bash
   aio console project select
   ```

   ```bash
   aio console workspace select
   ```

   ![&#x200B; Eind die Adobe I/O CLI organisatieproject en werkruimteselectie tonen &#x200B;](../assets/cli-configuration.png){width="600" zoomable="yes"}

### De startkits klonen

Kloont een van de volgende Commerce starter kit repositories voor de extensie die u bouwt en bereidt uw project voor:

Integratiestartkit:

```bash
git clone https://github.com/adobe/commerce-integration-starter-kit.git extension
cd extension
```

Uitchecken startkit:

```bash
git clone https://github.com/adobe/commerce-checkout-starter-kit.git extension
cd extension
```

>[!BEGINTABS]

>[!TAB  Startuitrusting van de Integratie ]

### Een .env-bestand maken

Maak uw configuratiebestand voor de omgeving:

```bash
cp env.dist .env
```

Open het bestand `.env` in een teksteditor en voeg de volgende OAuth-referenties toe:

```bash
OAUTH_CLIENT_ID=
OAUTH_CLIENT_SECRET=
OAUTH_TECHNICAL_ACCOUNT_ID=
OAUTH_TECHNICAL_ACCOUNT_EMAIL=
OAUTH_ORG_ID=
```

Kopieer deze waarden van de **[!UICONTROL Credential details]** pagina in [&#x200B; Developer Console &#x200B;](https://developer.adobe.com/) door het **[!UICONTROL OAuth Server-to-Server]** lusje op uw werkruimte te klikken.

![&#x200B; OAuth Server-aan-Server geloofsbrieven pagina in Adobe Developer Console &#x200B;](../assets/oauth-credentials.png){width="600" zoomable="yes"}

#### De Commerce-configuratie toevoegen

Voeg de volgende Commerce-instantiedetails toe aan uw `.env` -bestand:

```bash
COMMERCE_BASE_URL=
COMMERCE_GRAPHQL_ENDPOINT=
```

U kunt als volgt de volgende waarden vinden:

1. Navigeer aan [&#x200B; instanties van de Dienst van Commerce Cloud &#x200B;](https://experience.adobe.com/#/@commerce/commerce/cloud-service/instances).
1. Klik op het informatiepictogram naast de instantie.
1. Kopieer het REST-eindpunt als `COMMERCE_BASE_URL` .
1. Kopieer het GraphQL-eindpunt als `COMMERCE_GRAPHQL_ENDPOINT` .

#### Gebeurtenisvoorvoegsel instellen

Stel een tijdelijke waarde in voor het voorvoegsel van de gebeurtenis:

```bash
EVENT_PREFIX=test
```

### De werkruimteconfiguratie downloaden

Voer de volgende opdracht uit om het configuratiebestand van de werkruimte te downloaden:

```bash
aio console workspace download workspace.json
```

Kopieer het configuratiebestand van de werkruimte naar de map `scripts` :

```bash
cp workspace.json scripts/
```

### De lokale werkruimte verbinden met de externe werkruimte

Koppel uw lokale project aan de externe werkruimte:

```bash
aio app use workspace.json -m
```

![&#x200B; Eind die succesvolle werkruimteverbinding tonen met het bevel van het de toepassingsgebruik van de lucht &#x200B;](../assets/connect-workspace.png){width="600" zoomable="yes"}

>[!TAB  Uitchecken starter kit ]

### Lokale werkruimte verbinden met externe werkruimte

Koppel uw lokale project aan de externe werkruimte. Voer vanuit de hoofdmap van het project (de map `extension` ):

```bash
aio app use --merge
```

Wanneer ertoe aangezet, kies de optie die de organisatie, het project, en de werkruimte gebruikt u selecteerde toen het vormen van Adobe I/O CLI. Hiermee schrijft u de werkruimteconfiguratie naar uw app, zodat deze werkruimte wordt gebruikt bij de implementatie en lokale ontwikkeling.

![&#x200B; Eind die succesvolle werkruimteverbinding tonen met het bevel van het de toepassingsgebruik van de lucht &#x200B;](../assets/connect-workspace.png){width="600" zoomable="yes"}

>[!ENDTABS]

### De uitbreidbaarheidsprogramma&#39;s voor AI installeren

Dit proces leidt tot de configuratie MCP (`.<agent>/mcp.json`), de vaardigheidsfolder (`.<agent>/skills/`), en voegt `AGENTS.md` aan de projectwortel toe. U wordt gevraagd een startkit, coderingsagent en pakketbeheer te kiezen.


1. Stel de ontwikkelprogramma&#39;s voor AI-toepassingen in de map `extension` in met behulp van de volgende opdrachten:

   ```bash
   cd extension
   ```

   ```bash
   aio commerce extensibility tools-setup
   ```

   ![&#x200B; Eind die AI de output van het bevel van de de opstellingsbevelopstelling van uitbreidingshulpmiddelen tonen &#x200B;](../assets/install-ai-tools.png){width="600" zoomable="yes"}

1. Nadat de opstelling voltooit, nieuw begin uw coderingsagent om het toe te staan om de nieuwe hulpmiddelen MCP en vaardigheden te laden. De Commerce App Builder-tools zijn nu beschikbaar in uw omgeving.

   >[!NOTE]
   >
   >Als u een waarschuwing ziet dat er geen vaardigheden zijn gevonden voor de startkit, is er iets fout gegaan, vaak omdat de installatie in een andere map dan waar de startkit is gekloond, is uitgevoerd. Voer `aio commerce extensibility tools-setup` uit vanuit de map `extension` (de hoofdmap van het startkit-project) en selecteer de juiste startkit wanneer hierom wordt gevraagd.

   ![&#x200B; Eind die AI de opstelling van rekbaarheidshulpmiddelen met geselecteerde kweekstarterkit tonen &#x200B;](../assets/tools-setup-checkout.png){width="600" zoomable="yes"}

## Voorwaarden voor Storefront

De volgende punten worden vereist om de [&#x200B; opslag &#x200B;](./ratings-extension.md#connect-to-the-storefront) sectie van de [&#x200B; de uitbreidingsleerprogramma van classificaties &#x200B;](./ratings-extension.md) te voltooien en productratings in uw opslag te tonen.

* [&#x200B; Google Chrome &#x200B;](https://www.google.com/chrome/) - Vereist voor het testen van de storefront

* Een storefront-project dat is verbonden met uw [!DNL Commerce] -instantie. Als u geen storefront project hebt, volg de stappen in [&#x200B; creeer een storefront &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/){target="_blank"}, met inbegrip van de [&#x200B; reactie van de Verbinding aan handelsgegevens &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/#link-repo-to-commerce-data){target="_blank"} sectie.

### De opslagplaats klonen

Open uw terminal en kloon de repository:

```bash
git clone --branch agentic-dev https://github.com/hlxsites/aem-boilerplate-commerce.git storefront
cd storefront
```

### De afhankelijkheden installeren

Installeer de projectafhankelijkheden:

```bash
npm install
```

### De storefront AI-gereedschappen installeren

Stel de ontwikkelprogramma&#39;s voor AI-toepassingen in de map `storefront` in. Voer het volgende bevel van de wortel van uw bouwsteenproject in werking:

```bash
aio commerce extensibility tools-setup
```

Het bevel loopt u door twee herinneringen:

1. **selecteer een starteruitrusting** - kies **AEM Boilerplate Commerce**.

1. **selecteer uw coderingsagent** — kies uw agent van de lijst van gesteunde agenten.

Het bevel installeert het `@adobe-commerce/commerce-extensibility-tools` pakket als dev gebiedsdeel, kopieert de vaardigheidsdossiers in de vaardigheidsfolder van uw agent, en vormt MCP (ModelContext Protocol) zodat kan uw agent tot de hulpmiddelen van het de documentatieonderzoek van Commerce toegang hebben.