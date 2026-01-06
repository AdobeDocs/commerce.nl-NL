---
title: Voorwaarden voor de zelfstudie over de uitbreiding van classificaties
description: Leer de eerste vereisten voor het laboratorium van de classificatieuitbreiding.
feature: App Builder, Cloud
role: Developer
level: Intermediate
hide: true
hidefromtoc: true
source-git-commit: 4ca909c2f8f95fbc404ce6a745d769958b2c01f4
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Voorwaarden voor de extensie van beoordelingen (Beta)

>[!NOTE]
>
>De AI-gereedschappen die in deze zelfstudie worden gebruikt, bevinden zich momenteel in Beta en kunnen bugs of andere problemen bevatten.

Deze pagina maakt een lijst van de eerste vereisten en opstellingsstappen voor [!DNL Adobe Commerce as a Cloud Service] leerprogramma&#39;s, zoals het [ leerprogramma van de classificatieuitbreiding ](./ratings-extension.md).

## Adobe Commerce as a Cloud Service-voorwaarden

* De [!DNL Adobe I/O CLI] installeren

  ```bash
  npm install -g @adobe/aio-cli
  ```

* Installeer [ Adobe I/O CLI Commerce ](https://github.com/adobe-commerce/aio-cli-plugin-commerce), [ Adobe I/O CLI Runtime ](https://github.com/adobe/aio-cli-plugin-runtime), en [ App Builder CLI ](https://github.com/adobe/aio-cli-plugin-app-dev) stoppen:

  ```bash
  aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce @adobe/aio-cli-plugin-app-dev @adobe/aio-cli-plugin-runtime
  ```

* Download AI-bijgewoonde winde, zoals [ Cursor ](https://cursor.com/download) (geadviseerd), andere IDEs, zoals de Code van Claude, Gemini CLI, of Copilot wordt ook gesteund, maar kon wijzigingen in de herinneringen en andere stappen in het leerprogramma vereisen.

### Adobe Developer Console-voorwaarden

1. Navigeer aan [ Adobe Developer Console ](https://developer.adobe.com/console){target="_blank"}.
1. Meld u aan met uw e-mail en wachtwoord.

#### Een nieuw project maken

1. Navigeer aan [ Adobe Developer Console ](https://developer.adobe.com/).
1. Klik [!UICONTROL **creeer project van een malplaatje**].
1. Selecteer het [!UICONTROL **App Builder**] malplaatje.
1. Ga Titel van het a [!UICONTROL **Project**] in en [!UICONTROL **App Naam**].
1. Controleer of het selectievakje **[!UICONTROL Include Runtime]** is gemarkeerd.

   ![ Adobe Developer Console project verwezenlijking met het geselecteerde malplaatje van App Builder ](../assets/app-builder-template.png){width="600" zoomable="yes"}

1. Klik [!UICONTROL **sparen**].

#### API&#39;s toevoegen aan de werkruimte

1. Klik de [!UICONTROL **werkruimte van het Stadium**] en herhaal dan de volgende stappen voor elke API.

   ![ werkruimte van het Stadium met Add de optie van de Dienst voor APIs ](../assets/add-apis-workspace.png){width="600" zoomable="yes"}

1. Klik [!UICONTROL **toevoegen de Dienst**] en selecteren [!UICONTROL **API**].

1. Selecteer een van de volgende API&#39;s. U moet dit proces voor elke API herhalen die hieronder wordt vermeld:

   * [!UICONTROL **filter van de Diensten van 0} Adobe {:**]
      * [!UICONTROL **I/O Beheer API**]
      * [!UICONTROL **I/O Gebeurtenissen**] API
   * [!UICONTROL **Experience Cloud**] filter:
      * [!UICONTROL **Adobe I/O Events voor Adobe Commerce**] API

1. Klik [!UICONTROL **daarna**].

1. Klik [!UICONTROL **sparen gevormde API**].

1. Herhaal de vorige stappen totdat alle API&#39;s zijn toegevoegd aan de werkruimte.

   ![ Workspace die alle vereiste met succes toegevoegde APIs tonen ](../assets/apis-added.png){width="600" zoomable="yes"}

### De Adobe I/O CLI configureren

1. Wis om het even welke bestaande configuratie:

   ```bash
   aio config clear
   ```

   Meld u aan met [!DNL Adobe I/O CLI] :

   ```bash
   aio auth login -f
   ```

1. Selecteer uw organisatie, project, en werkruimte, gebruikend elk van de volgende bevelen:

   ```bash
   aio console org select
   ```

   ```bash
   aio console project select
   ```

   ```bash
   aio console workspace select
   ```

   ![ Eind die Adobe I/O CLI organisatieproject en werkruimteselectie tonen ](../assets/cli-configuration.png){width="600" zoomable="yes"}

### De integratiestartkit klonen

Clone the Commerce integration starter kit repository and prepare your project:

```bash
git clone https://github.com/adobe/commerce-integration-starter-kit.git extension
cd extension
```

![ Eind output die het bevel van de kloonkloon voor de de integratiestarterkit van Commerce tonen ](../assets/clone-starter-kit.png){width="600" zoomable="yes"}

### Een .env-bestand maken

Maak uw configuratiebestand voor de omgeving:

```bash
cp env.dist .env
```

Open het bestand `.env` in een teksteditor en voeg de volgende OAuth-referenties toe:

```shell-session
OAUTH_CLIENT_ID=
OAUTH_CLIENT_SECRET=
OAUTH_TECHNICAL_ACCOUNT_ID=
OAUTH_TECHNICAL_ACCOUNT_EMAIL=
OAUTH_ORG_ID=
```

U kunt deze waarden van de **[!UICONTROL Credential details]** pagina in [ Developer Console ](https://developer.adobe.com/) kopiëren door het **[!UICONTROL OAuth Server-to-Server]** lusje op uw werkruimte te klikken.

![ OAuth Server-aan-Server geloofsbrieven pagina in Adobe Developer Console ](../assets/oauth-credentials.png){width="600" zoomable="yes"}

#### De Commerce-configuratie toevoegen

Voeg de volgende Commerce-instantiedetails toe aan uw `.env` -bestand:

```shell-session
COMMERCE_BASE_URL=
COMMERCE_GRAPHQL_ENDPOINT=
```

U kunt als volgt de volgende waarden vinden:

1. Navigeer aan [ instanties van de Dienst van Commerce Cloud ](https://experience.adobe.com/#/@commerce/commerce/cloud-service/instances).
1. Klik op het informatiepictogram naast de instantie.
1. Kopieer het REST-eindpunt als `COMMERCE_BASE_URL` .
1. Kopieer het GraphQL-eindpunt als `COMMERCE_GRAPHQL_ENDPOINT` .

#### Gebeurtenisvoorvoegsel instellen

Stel een tijdelijke waarde in voor het voorvoegsel van de gebeurtenis:

```shell-session
EVENT_PREFIX=test
```

### Configuratie van werkruimte downloaden

Voer de volgende opdracht uit om het configuratiebestand van de werkruimte te downloaden:

```bash
aio console workspace download workspace.json
```

Kopieer het configuratiebestand van de werkruimte naar de map `scripts` :

```bash
cp workspace.json scripts/
```

### Lokale werkruimte verbinden met externe werkruimte

Koppel uw lokale project aan de externe werkruimte:

```bash
aio app use workspace.json -m
```

![ Eind die succesvolle werkruimteverbinding tonen met het bevel van het de toepassingsgebruik van de lucht ](../assets/connect-workspace.png){width="600" zoomable="yes"}

### Uitbreidbare AI-gereedschappen installeren

Werk het bestand met cursorregels en de MCP-configuratie bij om het `commerce-extensibility-tools` -pakket op te nemen.

1. Stel de ontwikkelprogramma&#39;s voor AI-toepassingen in de map `extension` in met behulp van de volgende opdrachten:

   ```bash
   cd extension
   ```

   ```bash
   aio commerce extensibility tools-setup
   ```

   ![ Eind die AI de output van het bevel van de de opstellingsbevelopstelling van uitbreidingshulpmiddelen tonen ](../assets/install-ai-tools.png){width="600" zoomable="yes"}
<!--
## Storefront prerequisites

The following items are required to complete the [storefront](./ratings-extension.md#connect-to-the-storefront) section of [this tutorial](./ratings-extension.md) and see the product ratings in your store.

* Install [!DNL Node.js] (version `22.x.x`) and npm (`9.0.0` or higher). Verify your installation:

   ```bash
   node --version
   npm --version
   ```

* Install [Git](https://git-scm.com) (Optional) - Required only if [cloning the repository directly](#option-a-clone-the-repository-recommended)(recommended), not needed if you [download the zip file](#option-b-download-the-zip-file). Verify your installation:

  ```bash
  git --version
  ```

* Bash shell
  * macOS/Linux: No installation required
  * Windows: Use [Git Bash](https://git-scm.com/install) or [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install)

* [Google Chrome](https://www.google.com/chrome/) - Required for testing the storefront

### Get the project files

You can obtain the project files using one of the following methods:

#### Option A: Clone the repository (recommended)

If you have [!DNL Git] installed, open your terminal and clone the repository:

```bash
git clone --branch agentic-dev https://github.com/hlxsites/aem-boilerplate-commerce.git storefront
cd storefront
```

#### Option B: Download the zip file

If you do not have [!DNL Git] installed:

1. Download the project zip file from: [https://github.com/hlxsites/aem-boilerplate-commerce/archive/refs/heads/agentic-dev.zip](https://github.com/hlxsites/aem-boilerplate-commerce/archive/refs/heads/agentic-dev.zip)
1. Extract the zip file to a folder on your machine.
1. Open your terminal and navigate into the unzipped folder:

   ```bash
   cd path/to/aem-boilerplate-commerce-agentic-dev
   ```

### Install root dependencies

Install the main project dependencies:

```bash
npm install
```

This will install all the necessary packages for the storefront application.

### Install MCP server dependencies

Navigate to the MCP server directory and install its dependencies:

```bash
cd mcp-server
npm install
cd ..
```

### Configure environment variables

The MCP server requires certain environment variables to connect to the RAG service.

Create an `.env` file in the `mcp-server` directory:

```bash
cd mcp-server
cp env.example .env
```

Edit the `.env` file and add the following values:

```env
RAG_MODE=worker
WORKER_RAG_URL=
```

### Enable MCP in Cursor

The Model Context Protocol (MCP) server provides AI agents with access to [!DNL Adobe Commerce] Storefront documentation.

#### Open Cursor MCP settings

![Open Cursor MCP Settings](../assets/cursor-mcp-settings.png){width="600" zoomable="yes"}

1. Open [!DNL Cursor].
1. Navigate to **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]**.

#### Enable and configure MCP features

The project includes an MCP configuration file at `.cursor/mcp.json`. This file should already be configured to use the local MCP server.

Verify the MCP configuration:

1. Ensure the "commerce-documentation-rag" server is listed and enabled

The configuration should look similar to this:

![MCP Configuration](../assets/mcp-configuration.png){width="600" zoomable="yes"}

>[!NOTE]
>
>The `start-mcp.sh` script will automatically load the environment variables from your `.env` file in the `mcp-server` directory.

#### Restart Cursor

After enabling MCP and configuring the server:

1. Quit [!DNL Cursor] completely.
1. Reopen [!DNL Cursor] and open the `aem-boilerplate-commerce` project.

#### Verify MCP connection

Check that the MCP server is running correctly:

1. Open a new chat in [!DNL Cursor].
1. Look for an indicator showing the MCP server is connected. This indicator is typically located in the chat interface.
1. Try entering a prompt like the following:

   ```shell-session
   Search the storefront docs for information about slots
   ```

If the MCP server is working, you should see relevant documentation results.

![MCP Connection Verified](../assets/mcp-connection-verified.png){width="600" zoomable="yes"}

If this works, you are ready to continue with the [tutorial](./ratings-extension.md).
 -->
