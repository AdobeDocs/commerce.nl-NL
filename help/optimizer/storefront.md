---
title: Winefront instellen
description: Leer hoe te opstelling uw  [!DNL Adobe Commerce Optimizer]  storefront.
role: Developer
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 3131cc27a25d1bf958071b973f1d4bf1a68be152
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# Winefront instellen

Dit leerprogramma toont aan hoe te opstelling en gebruik [ Adobe Commerce Storefront die door Edge Delivery Services ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/) wordt aangedreven om een uitvoerbare, scalable, en veilige Commerce storefront tot stand te brengen die door gegevens van uw [!DNL Adobe Commerce Optimizer] instantie wordt aangedreven.


## Vereisten

- Zorg ervoor dat u een rekening GitHub (github.com) hebt die bewaarplaatsen kan tot stand brengen en voor lokale ontwikkeling gevormd.

- Leer over de concepten en het werkschema om Commerce storefronts op de Diensten van de Levering van de Rand van Adobe te ontwikkelen door het [ Overzicht ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started) in de documentatie van de Storefront van Adobe Commerce te herzien.
- De ontwikkelomgeving instellen


### De ontwikkelomgeving instellen

Installeer Node.js en de Sidekick browser extensie die nodig is om uw [!DNL Adobe Commerce Optimizer] winkel op Edge Delivery Services te ontwikkelen en te testen.

#### Node.js installeren

Installeer Node Version Manager (NVM) en de vereiste Node.js-versie (22.13.1 LTS).

1. Installeer Node Version Manager (NVM).

   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
   ```

1. Installeer Node.js en NPM. Voor meer informatie, zie [ Node.js ](https://nodejs.org/en/).

   ```bash
   nvm install 22
   ```

   ```bash
   npm install -g npm
   ```

1. Controleer de installatie.

   ```bash
   npm -v
   ```

>[!TIP]
>
>De extra middelen om uw [!DNL Adobe Commerce Optimizer] oplossing uit te breiden en aan te passen zijn beschikbaar door [ App Builder voor Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder) en [ API Net voor Adobe Developer App Builder ](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/api-mesh/getting-started-api-mesh). Neem voor toegang tot en gebruiksinformatie contact op met uw Adobe-accountvertegenwoordiger.

#### Sidekick installeren

Installeer de Sidekick-browserextensie om inhoud te bewerken, voor te vertonen en te publiceren naar de winkel. Zie [ de installatieinstructies van Sidekick ](https://www.aem.live/docs/sidekick#installation).

## Je winkel maken

De winkel die u voor uw [!DNL Adobe Commerce Optimizer] -project maakt, gebruikt een aangepaste versie van de Adobe Commerce op Edge Delivery Services Storefront boilerplate. De bouwsteenplaat is een reeks dossiers en omslagen die een uitgangspunt voor storefront ontwikkeling verstrekken. Dit opstellingsproces is verschillend dan het standaardopstellingsproces voor een [ Adobe Commerce op Edge Delivery Services Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/).

>[!NOTE]
>
>Dit leerprogramma gebruikt macOS, Chrome, en de Code van Visual Studio als ontwikkelomgeving. Deze instelling komt tot uiting in de schermvastleggingen en -instructies. U kunt een verschillend werkend systeem, browser, en coderedacteur gebruiken, maar UI u ziet en de stappen u neemt variëren dienovereenkomstig.

### Workflowoverzicht

Voer de volgende stappen uit om een winkelvoetnoot in te stellen die u met [!DNL Adobe Commerce Optimizer] wilt gebruiken.

1. **[creeer een codebewaarplaats](#step-1-create-site-code-repository)** - creeer een bewaarplaats GitHub van Adobe Commerce + Edge Delivery Services boilerplate malplaatje. Neem alle vertakkingen van de bronopslagplaats op.
1. **[werk storefront boilerplate](#step-2-update-the-storefront-boilerplate)** bij - werk het malplaatje van het douaneboilerplate op de `aco` tak bij om uw inhoudsomslag met de storefront te verbinden.
1. **[stel veranderingen](#step-3-deploy-changes)** op - vervang de code op de `main` tak met de bijgewerkte code van de `aco` tak.
1. **[voeg app CodeSync](#step-5-add-the-aem-code-sync-app)** toe - verbind uw bewaarplaats met de Dienst van Edge Delivery. Sluit de toepassing Codesynchronisatie pas aan nadat u de broncode hebt aangepast en de code naar de `main` -vertakking hebt geduwd.
1. **[voeg inhoud](#step-6-add-content)** toe - gebruik het kloonhulpmiddel van de demo inhoud om uw storefront inhoud in het milieu van de Auteur van het Document tot stand te brengen en te initialiseren dat op `https://da.live` wordt ontvangen.
1. **[de demoplaats van de voorproef](#step-7-preview-demo-site)** - verbind met uw storefront plaats om de steekproefinhoud en de gegevens van de [!DNL Adobe Commerce Optimizer] demoinstantie te bekijken.
1. **[ontwikkelt zich in uw lokale milieu](#step-8-develop-in-your-local-environment)** - installeer de vereiste gebiedsdelen. Start de lokale ontwikkelingsserver en werk de storefront-configuratie bij om verbinding te maken met de [!DNL Adobe Commerce Optimizer] -instantie die Adobe voor u heeft ingericht.
1. **[Volgende stappen](#next-steps)** - leer meer over het beheren van en het tonen van inhoud en gegevens in de storefront.


### Stap 1: Een gegevensopslagruimte voor sitecode maken

Creeer een bewaarplaats GitHub voor de plaats boilerplate code voor uw storefront gebruikend het Edge Delivery Services + Adobe Commerce Boilerplate malplaatje.

1. Login aan uw rekening GitHub.

1. Navigeer aan de [ aem-boilerplate-handel ](https://github.com/hlxsites/aem-boilerplate-commerce) bewaarplaats GitHub.

1. Selecteer **Gebruik dit malplaatje**, en selecteer dan **creeer een nieuwe bewaarplaats** van het drop-down menu.

   ![[!DNL Create github repo from storefront boilerplate template]](./assets/storefront-create-github-repo.png){width="700" zoomable="yes"}

   De configuratiepagina van de repository wordt weergegeven.

   ![[!DNL Configure github repo to pull all branches from boilerplate repo]](./assets/storefront-configure-github-repo.png){width="700" zoomable="yes"}

1. Vul het configuratieformulier met de volgende gegevens in:

   - **malplaatje van de Bewaarplaats** - `hlxsites/aem-boilerplate-commerce` (gebrek).
   - **omvat alle takken** - selecteer de optie om alle takken te omvatten.
   - **Eigenaar** - Uw organisatie of (vereiste) rekening.
   - **Naam van de Bewaarplaats** - een unieke naam voor uw nieuwe (vereiste) repo.
   - **Beschrijving** - een korte beschrijving van uw (facultatieve) reactie.
   - **Openbaar of Privé** - Adobe adviseert openbaar (gebrek).

1. Selecteer **creeer bewaarplaats**.

   Na enkele minuten wordt de nieuwe opslagplaats geopend.

   Negeer om het even welke berichten van het trekkingsverzoek die in het GitHub gebruikersinterface worden getoond.

### Stap 2: De storefront boilerplate bijwerken

U hebt de volgende informatie nodig om de storefront boilerplate-code bij te werken:

- **GitHub bewaarplaats URL van Stap 2** - `github.com/{ORG}/{SITE}`
   - `{ORG}` is de organisatienaam of gebruikersnaam voor de repository
   - `{SITE}` is de naam van uw opslagplaats
- **omslag URL van de Inhoud van Stap 1** - `https://drive.google.com/drive/folders/{YOUR_FOLDER_ID}`
   - `{YOUR_FOLDER_ID}` is de id van de map die u hebt gemaakt met de voorbeeldinhoudsgegevens.

#### De gegevensopslagruimte koppelen aan de omgeving van de auteur van het document

1. Kloont de opslagplaats naar uw lokale computer.

   ```bash
   git clone https://github.com/{ORG}/{SITE}.git
   ```

   Als u fouten wanneer het klonen van de bewaarplaats ontmoet, zie [ het klonen fouten ](https://docs.github.com/en/repositories/creating-and-managing-repositories/troubleshooting-cloning-errors) in de documentatie van GitHub problemen oplossen.

1. Open de repository in uw terminal of IDE.

1. De vertakking `aco` uitchecken

   ```bash
   git checkout aco
   ```

1. Maak uw configuratiebestand door het bestand `default-fstab.yaml` naar `fstab.yaml` te kopiëren.

   ```bash
   cp default-fstab.yaml fstab.yaml
   ```

1. Werk het montagepunt in het storefront configuratiedossier bij om aan uw inhoud URL te richten.

   1. Open het {[&#128279;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/#vocabulary) configuratiedossier 0} fstab.yaml.

      ```yaml
      mountpoints:
        /:
          url: https://content.da.live/{org}/{site}/
          type: markup
      
      folders:
       /products/: /products/default
      ```

   1. Vervang de tekenreeksen `{ORG}` en `{SITE}` door de waarden voor de gegevensopslagplaats GitHub die u voor uw boilerplate code creeerde.

      De bijgewerkte code moet er bijvoorbeeld zo uitzien.

      ```yaml
      mountpoints:
        /:
          url: https://content.da.live/owner-name/aco-storefront/
          type: markup
      ```

   1. Sla het bestand op.

#### De Sidekick-extensie configureren

1. Voeg de projectconfiguratie voor de uitbreiding van Sidekick toe. Deze configuratie zorgt ervoor dat Sidekick beschikbaar is om inhoud voor uw winkelproject te beheren.

>[!NOTE]
>
>Zorg ervoor dat u de [ uitbreiding van Sidekick ](https://www.aem.live/docs/sidekick#installation) in uw browser hebt geïnstalleerd.

1. Open het `tools/sidekick/config.json` -bestand.

   +++Sidekick-configuratiebestand

   ```json
   {
     "project": "Boilerplate",
     "plugins": [
       {
         "id": "cif",
         "title": "Commerce",
         "environments": [
           "edit"
         ],
         "url": "https://main--{SITE}--{ORG}.aem.live/tools/picker/dist/index.html",
         "isPalette": true,
         "paletteRect": "top: 54px; left: 5px; bottom: 5px; width: 300px; height: calc(100% - 59px); border-radius: var(--hlx-sk-button-border-radius); overflow: hidden; resize: horizontal;"
       },
       {
         "id": "personalisation",
         "title": "Personalisation",
         "environments": [
           "edit"
         ],
         "url": "https://main--{SITE}--{ORG}.aem.live/tools/segments/dist/index.html",
         "isPalette": true,
         "paletteRect": "top: 54px; left: 5px; bottom: 5px; width: 300px; height: calc(100% - 59px); border-radius: var(--hlx-sk-button-border-radius); overflow: hidden; resize: horizontal;"
       }
     ]
   }
   ```

   Zie de [ documentatie van de Bibliotheek van Sidekick ](https://www.aem.live/docs/sidekick-library) voor meer informatie.

   +++

1. Werk de `url` zeer belangrijke waarden met de waarden voor uw bewaarplaats GitHub bij.

   - Vervang de `{ORG}` -tekenreeks door de organisatie of gebruikersnaam voor de gegevensopslagruimte.

   - De `{SITE}` -tekenreeks vervangen door de naam van de gegevensopslagruimte

   +++Voorbeeld van bijgewerkt configuratiebestand

   Als uw GitHub-opslagplaats `aco-storefront` heet en uw organisatie `early-adopter` is, zou de bijgewerkte URL er als volgt moeten uitzien:

   ```json
   {
     "project": "Boilerplate",
     "plugins": [
       {
         "id": "cif",
         "title": "Commerce",
         "environments": [
           "edit"
         ],
         "url": "https://main--aco-storefront--early-adopter.aem.live/tools/picker/dist/index.html",
         "isPalette": true,
         "paletteRect": "top: 54px; left: 5px; bottom: 5px; width: 300px; height: calc(100% - 59px); border-radius: var(--hlx-sk-button-border-radius); overflow: hidden; resize: horizontal;"
       },
       {
         "id": "personalisation",
         "title": "Personalisation",
         "environments": [
           "edit"
         ],
         "url": "https://main--aco-storefront--early-adopter.aem.live/tools/segments/dist/index.html",
         "isPalette": true,
         "paletteRect": "top: 54px; left: 5px; bottom: 5px; width: 300px; height: calc(100% - 59px); border-radius: var(--hlx-sk-button-border-radius); overflow: hidden; resize: horizontal;"
       }
     ]
   }
   ```
