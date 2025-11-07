---
title: Voorwaarden voor ADL Commerce-lab
description: Leer de eerste vereisten voor het laboratorium van de classificatieuitbreiding.
role: Developer
hide: true
hidefromtoc: true
source-git-commit: ba4d096bcb99420c029d0b0674fc00f1f1445cea
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Adobe Developers Live - Adobe Commerce-laboratoriumvereisten

Deze pagina maakt een lijst van de eerste vereisten en andere handmatige opstellingsstappen voor het [&#x200B; laboratorium van de classificatieuitbreiding &#x200B;](./workbook.md). Het laboratorium bevat ook een manuscript dat de meeste van deze stappen automatiseert.

## Voorwaarden voor extensies

Voordat u begint, moet u aan de volgende voorwaarden voldoen:

* De [!DNL Adobe I/O CLI] installeren

  ```bash
  npm install -g @adobe/aio-cli
  ```

* De Commerce-insteekmodule installeren

  ```bash
  aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce
  ```

* Download AI-bijgewoonde winde, zoals [&#x200B; Cursor &#x200B;](https://cursor.com/download) (geadviseerd), andere IDEs, zoals de Code van Claude, Gemini CLI, of Copilot wordt ook gesteund, maar kon wijzigingen in de herinneringen en andere stappen in dit leerprogramma vereisen.
<!-- 
### Create a new project on Adobe Developer Console

1. Navigate to [Adobe Developer Console](https://developer.adobe.com/).
1. Click [!UICONTROL **Create project from a template**].
1. Select the [!UICONTROL **App Builder**] template.
1. Enter a [!UICONTROL **Project Title**] and [!UICONTROL **App Name**].
1. Ensure the **[!UICONTROL Include Runtime]** checkbox is marked.

   ![Create project with App Builder template](./assets/app-builder-template.png){width="600" zoomable="yes"}

1. Click **Save**.

### Add APIs to the workspace

1. Click the [!UICONTROL **Stage**] workspace and then repeat the following steps for each API.

   ![APIs added to workspace](./assets/add-apis-workspace.png){width="600" zoomable="yes"}

1. Click [!UICONTROL **Add Service**] and select [!UICONTROL **API**].

1. Select the [!UICONTROL **Adobe Services**] filter and select one of the following APIs:

   * [!UICONTROL **I/O Management API**]
   * [!UICONTROL **I/O Events**]

1. Select the [!UICONTROL **Experience Cloud**] filter and select one of the following APIs:

   * [!UICONTROL **Adobe I/O Events for Adobe Commerce**]

1. Click [!UICONTROL **Next**].

1. Click[!UICONTROL **Save configured API**].

1. Repeat the previous steps until all APIs are added to the workspace.

   ![APIs added to workspace](./assets/apis-added.png){width="600" zoomable="yes"} -->

### AIO CLI configureren

1. Wis de bestaande configuratie:

   ```bash
   aio config clear
   ```

   Meld u aan met de AIO CLI:

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

   ![&#x200B; CLI configuratie &#x200B;](./assets/cli-configuration.png){width="600" zoomable="yes"}

### Kloonintegratiestartkit

Clone the Commerce integration starter kit repository and prepare your project:

```bash
git clone --branch adl https://github.com/adobe/commerce-integration-starter-kit.git extension
cd extension
```

![&#x200B; Kloonstarterkit &#x200B;](./assets/clone-starter-kit.png){width="600" zoomable="yes"}

### Het .env-bestand maken

Maak uw configuratiebestand voor de omgeving:

```bash
cp env.dist .env
```

<!-- Open the `.env` file in a text editor and add the following OAuth credentials:

```text
OAUTH_CLIENT_ID=
OAUTH_CLIENT_SECRET=
OAUTH_TECHNICAL_ACCOUNT_ID=
OAUTH_TECHNICAL_ACCOUNT_EMAIL=
OAUTH_ORG_ID=
```

You can copy these values from the **[!UICONTROL Credential details]** page in [Developer Console](https://developer.adobe.com/) by clicking the **[!UICONTROL OAuth Server-to-Server]** tab on your workspace.

![OAuth credentials](./assets/oauth-credentials.png){width="600" zoomable="yes"}

#### Add the Commerce configuration

Add the following Commerce instance details to your `.env` file:

```text
COMMERCE_BASE_URL=
COMMERCE_GRAPHQL_ENDPOINT=
```

To find these values:

1. Go to [Commerce Cloud Service instances](https://experience.adobe.com/#/@commerce/commerce/cloud-service/instances).
1. Click the information icon next to your assigned seat.
1. Copy the REST endpoint as `COMMERCE_BASE_URL`.
1. Copy the GraphQL Endpoint as `COMMERCE_GRAPHQL_ENDPOINT`.

#### Set event prefix

Set a temporary value for the event prefix:

```text
EVENT_PREFIX=test
```
 -->

### Configuratie van werkruimte downloaden

Voer de volgende opdracht uit om het configuratiebestand van de werkruimte te downloaden:

```bash
aio console workspace download workspace.json
```

### Lokale werkruimte verbinden met externe werkruimte

Koppel uw lokale project aan de externe werkruimte:

```bash
aio app use workspace.json -m
```

![&#x200B; verbind met werkruimte &#x200B;](./assets/connect-workspace.png){width="600" zoomable="yes"}

## Voorwaarden voor Storefront

De volgende punten worden vereist om de [&#x200B; storefront &#x200B;](#connect-to-the-storefront) sectie van dit leerprogramma te voltooien en de productratings in uw opslag te zien.
<!-- 
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
  * Windows: Use [Git Bash](https://git-scm.com/install) or [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install).

* [Google Chrome](https://www.google.com/chrome/) - Required for testing the storefront -->

### De projectbestanden ophalen

U kunt de projectdossiers op één van twee manieren verkrijgen:

<!-- 
#### Option A: Clone the repository (recommended) -->

Als u [!DNL Git] hebt geïnstalleerd, opent u uw terminal en kloont u de repository:

```bash
git clone --branch agentic-dev https://github.com/hlxsites/aem-boilerplate-commerce.git storefront
cd storefront
```

<!-- #### Option B: Download the zip file

If you don't have [!DNL Git] installed:

1. Download the project zip file from: [https://github.com/hlxsites/aem-boilerplate-commerce/archive/refs/heads/agentic-dev.zip](https://github.com/hlxsites/aem-boilerplate-commerce/archive/refs/heads/agentic-dev.zip)
1. Extract the zip file to a folder on your machine.
1. Open your terminal and navigate into the unzipped folder:

   ```bash
   cd path/to/aem-boilerplate-commerce-agentic-dev
   ``` -->

### Hoofdafhankelijkheden installeren

De belangrijkste projectafhankelijkheden installeren:

```bash
npm install
```

Hiermee worden alle vereiste pakketten voor de winkeltoepassing geïnstalleerd.

### MCP-serverafhankelijkheden installeren

Navigeer naar de MCP serverfolder en installeer zijn gebiedsdelen:

```bash
cd mcp-server
npm install
cd ..
```

<!-- ### Configure environment variables

The MCP server requires certain environment variables to connect to the RAG service.

Create a `.env` file in the `mcp-server` directory:

```bash
cd mcp-server
cp env.example .env
```

Edit the `.env` file and add the following values (we'll provide the actual URL during the lab):

```env
RAG_MODE=worker
WORKER_RAG_URL=<provided-during-lab>
```

>[!NOTE]
>
>The actual value for `WORKER_RAG_URL` will be provided by the lab facilitator at the start of the session. -->

### MCP inschakelen in cursor

De MCP-server (Model Context Protocol) biedt AI-agents toegang tot [!DNL Adobe Commerce] Storefront-documentatie.

#### MCP-instellingen voor cursor openen

![&#x200B; Open de Montages van de Curseur MCP &#x200B;](./assets/cursor-mcp-settings.png){width="600" zoomable="yes"}

1. Openen [!DNL Cursor]
1. Ga naar **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]**

#### MCP-functies inschakelen en configureren

Het project omvat een MCP configuratiedossier bij `.cursor/mcp.json`. Dit dossier zou reeds moeten worden gevormd om de lokale server te gebruiken MCP.

Verifieer de configuratie MCP:

1. Verzeker de &quot;handel-documentatie-belemmering&quot;server vermeld en toegelaten is

De configuratie zou gelijkaardig aan dit moeten kijken:

![&#x200B; Configuratie MCP &#x200B;](./assets/mcp-configuration.png){width="600" zoomable="yes"}

>[!NOTE]
>
>Het script van `start-mcp.sh` laadt automatisch de omgevingsvariabelen van het bestand `.env` in de map `mcp-server` .

#### Cursor opnieuw starten

Na het toelaten MCP en het vormen van de server:

1. [!DNL Cursor] volledig afsluiten
1. Open [!DNL Cursor] opnieuw en open het `aem-boilerplate-commerce` -project

#### MCP-verbinding verifiëren

Controleer of de MCP-server correct wordt uitgevoerd:

1. Een nieuwe chat openen in [!DNL Cursor]
1. Zoek een indicator die de server MCP toont wordt aangesloten (gewoonlijk in de praatjinterface)
1. Stel een vraag als: &quot;Zoek in de winkeldocumenten naar informatie over sleuven&quot;

Als de server MCP werkt, zou u relevante documentatieresultaten moeten zien.

![&#x200B; geverifieerde Verbinding MCP &#x200B;](./assets/mcp-connection-verified.png){width="600" zoomable="yes"}

### De ontwikkelingsserver starten

Start de lokale ontwikkelingsserver:

```bash
npm run start
```

De ontwikkelingsserver begint bij `http://localhost:3000` .

Navigeer naar de pagina apparel op `http://localhost:3000/apparel` .

![&#x200B; Server die van de Ontwikkeling &#x200B;](./assets/development-server-running.png){width="600" zoomable="yes"} loopt
