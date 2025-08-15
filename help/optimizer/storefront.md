---
title: Winefront instellen
description: Leer hoe te opstelling uw  [!DNL Adobe Commerce Optimizer]  storefront.
role: Developer
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: 2b4c9e98-a30c-4a33-b356-556de5bd721a
source-git-commit: 475706df971e75091ee72e89d64088fa56aec4dd
workflow-type: tm+mt
source-wordcount: '1858'
ht-degree: 0%

---

# Winefront instellen

Dit leerprogramma verstrekt gedetailleerde instructies voor vestiging en het gebruiken van [ Adobe Commerce Storefront die door Edge Delivery Services ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/) wordt aangedreven om een uitvoerbare, scalable, en veilige Commerce storefront tot stand te brengen die door gegevens van uw [!DNL Adobe Commerce Optimizer] instantie wordt aangedreven.


>[!TIP]
>
>Snel het installatieproces van de winkel volgen door met het gereedschap Sitemaker de opslagplaats en de omgeving van de auteur van het document in te stellen
>&#x200B;>automatisch. Vervolgens kunt u deze instructies gebruiken om te begrijpen hoe de winkel is gemaakt en om meer te weten te komen over de componenten waarover u beschikt.

## Vereisten

* Zorg ervoor dat u een rekening GitHub (github.com) hebt die bewaarplaatsen kan tot stand brengen en voor lokale ontwikkeling gevormd.

* Leer over de concepten en het werkschema om Commerce storefronts op de Diensten van de Levering van de Rand van Adobe te ontwikkelen door het [ Overzicht ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started) in de documentatie van de Storefront van Adobe Commerce te herzien.
* De ontwikkelomgeving instellen


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

   * **malplaatje van de Bewaarplaats** - `hlxsites/aem-boilerplate-commerce` (gebrek).
   * **Eigenaar** - Uw organisatie of (vereiste) rekening.
   * **Naam van de Bewaarplaats** - een unieke naam voor uw nieuwe (vereiste) repo.
   * **Beschrijving** - een korte beschrijving van uw (facultatieve) reactie.
   * **Openbaar of Privé** - Adobe adviseert openbaar (gebrek).

1. Selecteer **creeer bewaarplaats**.

   Na enkele minuten wordt de nieuwe opslagplaats geopend.

   Negeer om het even welke berichten van het trekkingsverzoek die in het GitHub gebruikersinterface worden getoond.

### Stap 2: De storefront boilerplate bijwerken

U hebt de volgende informatie nodig om de storefront boilerplate-code bij te werken:

* **GitHub bewaarplaats URL van Stap 2** - `github.com/{ORG}/{SITE}`

   * `{ORG}` is de organisatienaam of gebruikersnaam voor de repository

   * `{SITE}` is de naam van uw opslagplaats

* **omslag URL van de Inhoud van Stap 1** - `https://drive.google.com/drive/folders/{YOUR_FOLDER_ID}`

  `{YOUR_FOLDER_ID}` is de id van de map die u hebt gemaakt met de voorbeeldinhoudsgegevens.

#### De gegevensopslagruimte koppelen aan de omgeving van de auteur van het document

1. Kloont de opslagplaats naar uw lokale computer.

   ```bash
   git clone https://github.com/{ORG}/{SITE}.git
   ```

   Als u fouten wanneer het klonen van de bewaarplaats ontmoet, zie [ het klonen fouten ](https://docs.github.com/en/repositories/creating-and-managing-repositories/troubleshooting-cloning-errors) in de documentatie van GitHub problemen oplossen.

1. Open de repository in uw terminal of IDE.

1. Maak uw configuratiebestand door het bestand `default-fstab.yaml` naar `fstab.yaml` te kopiëren.

   ```bash
   cp default-fstab.yaml fstab.yaml
   ```

1. Werk het montagepunt in het storefront configuratiedossier bij om aan uw inhoud URL te richten.

   1. Open het {[ configuratiedossier 0} fstab.yaml.](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/#vocabulary)

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

1. Maak een nieuwe map `tools/sidekick` .

   ```shell
   mkdir tools/sidekick
   ```

1. Kopieer het `demo-sidekick.json` -bestand in de hoofdmap naar de `tools/sidekick` -map en wijzig de naam in `config.json` .

   ```shell
   cp demo-sidekick.json tools/sidekick/config.json
   ```

1. Pas de Sidekick-configuratie voor uw site aan.

   Bewerk het `tools/sidekick/` -bestand vanuit de map `config.json` .

   +++Sidekick-configuratiebestand

   ```json
   {
     "project": "My Project",
     "editUrlLabel": "Document Authoring",
     "editUrlPattern": "https://da.live/edit#/{{org}}/{{site}}{{pathname}}"
   }
   ```

1. Werk de `url` zeer belangrijke waarden met de waarden voor uw bewaarplaats GitHub bij.

   * Vervang de `{{ORG}}` -tekenreeks door de organisatie of gebruikersnaam voor de gegevensopslagruimte.

   * Vervang de `{{SITE}}` -tekenreeks door de naam van de gegevensopslagruimte.

   * De variabele `pathname` wordt gevuld door het systeem.

   +++Voorbeeld van bijgewerkt configuratiebestand

   Als uw GitHub-opslagplaats `aco-storefront` heet en uw organisatie `early-adopter` is, zou de bijgewerkte URL er als volgt moeten uitzien:

   ```json
   {
     "project": "My Project",
     "editUrlLabel": "Document Authoring",
     "editUrlPattern": "https://da.live/edit#/aco-storefront/early-adopter{{pathname}}"
   }
   ```

   +++

1. Sla het bestand op.

### Stap 3: Wijzigingen implementeren

Als u de aangepaste storefront boilerplate-code wilt gebruiken, overschrijft u de code in de `main` -vertakking met uw updates.

1. Leg de bestanden die u hebt bijgewerkt vast en sla deze op in uw editor of IDE.

   ```bash
   git add .
   ```

1. Controleer of u de twee bijgewerkte bestanden vastlegt.

   ```bash
   git status
   On branch main
   Your branch is up to date with 'origin/main'.
   
   Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        new file:   fstab1.yaml
        modified:   tools/sidekick/config.json
   ```

1. Leg de wijzigingen vast.

   ```bash
   git commit -m "Update storefront boilerplate for Adobe Commerce Optimizer"
   ```

1. Pas de wijzigingen toe.

   ```bash
   git push
   ```

### Stap 5: Voeg de AEM Code Sync-app toe

Verbind uw opslagplaats met de Edge Delivery Service door de AEM Code Sync GitHub-app toe te voegen aan uw opslagplaats.

>[!IMPORTANT]
>
>Sluit de app Codesynchronisatie pas aan nadat u de bijgewerkte bouwsteencode hebt geüpload naar de hoofdvertakking van uw GitHub-opslagplaats.

1. Open de [ app van de Synchronisatie van de Code van AEM ](https://github.com/apps/aem-code-sync) configuratiepagina.

1. Selecteer **vormen**, dan met de **organisatie** voor authentiek verklaren of **rekening** die de bewaarplaats bevat u creeerde.

1. Van de vorm, kies **slechts uitgezochte bewaarplaatsen**, en selecteer dan de bewaarplaats u creeerde.

1. Selecteer **installeer** om de app van de Synchronisatie van de Code van AEM aan uw bewaarplaats toe te voegen.

   Er wordt een bericht weergegeven dat de app is geïnstalleerd.

### Stap 6: Inhoud toevoegen

Maak en initialiseer uw winkelinhoud in de ontwerpomgeving van het document die wordt gehost op `https://da.live` met het gereedschap Sitemaker. Met dit gereedschap importeert u de voorbeeldinhoud naar de documentauteur en voltooit u het voorbeeld- en publicatieproces voor de inhoud van alle documenten in de voorbeeldinhoud. De voorbeeldinhoud bevat de paginalay-outs, banners, labels en andere elementen om uw winkelachtergrond te vullen.

1. Open het [ hulpmiddel van de plaatsschepper ](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator)

1. De opslagplaats configureren:

   * Selecteer **[!UICONTROL Use Existing Repository]** .
   * Voer **[!UICONTROL Organization/Username]** in voor uw storefront boilerplate-project.
   * Voer de **[!UICONTROL Repository Name]** in.

1. De invoer, voorproef, en publiceert de inhoud aan het milieu van de Auteur van het Document door **te selecteren leidt plaats**.

   ![[!DNL AEM demo content clone tool]](./assets/storefront-edit-initial-content.png){width="700" zoomable="yes"}

   Nadat de site is gemaakt, kunt u de koppelingen in de secties [!UICONTROL Edit content] en [!UICONTROL View Site] gebruiken om de demo-storefront te verkennen.

   De belangrijkste koppelingen naar uw inhoud en site volgen de volgende indelingen:

   * **omslag van de wortelinhoud**— `https://da.live/#/{ORG}/{SITE}`
   * **voorproef van de Plaats**—   `https://main--{SITE}--{ORG}.aem.page/`
   * **de productie van de Plaats:**— `https:/main--{SITE}--{ORG}.ae.live/`

1. Open de koppeling naar de hoofdinhoudsmap om de inhoud weer te geven.

   ![[!DNL Storefront Document Author environment]](./assets/storefront-document-author-environment.png){width="700" zoomable="yes"}

   >[!TIP]
   >
   >In de zijnavigatie, gebruik [!UICONTROL **leren**] en [!UICONTROL **ontdekken**] verbindingen aan toegang het leren middelen voor het beheren van uw plaats en plaatsinhoud.

### Stap 7: Voorvertoning van demosite

Controleer of zowel de inhoud van het voorbeeld als de gegevens van de Adobe Commerce Optimizer-demo-instantie correct worden weergegeven.

* **inhoud van de Steekproef** wordt gediend van de inhoudsomslag in het milieu van de Auteur van het Document. Dit omvat de paginalay-outs, banners en labels voor uw site.
* **gegevens van de Steekproef** wordt gediend van de [!DNL Adobe Commerce Optimizer] demo instantie. De gegevens omvatten productgegevens met productkenmerken, beelden, productbeschrijvingen, en prijzen bevolkt gebaseerd op de kopbalwaarden die in het archiefrontconfiguratiedossier, `config.json` worden gespecificeerd.

#### Maak verbinding met uw site om voorbeeldinhoud en -gegevens weer te geven

1. Geef uw site weer door naar `https://main--{SITE}--{ORG}.aem.live` te navigeren.

   Vervang `{ORG}` en `{SITE}` door de organisatie en naam van de opslagplaats voor vaste gegevens.

   ![[!DNL ACO storefront site with boilerplate]](./assets/aco-storefront-site-boilerplate.png){width="700" zoomable="yes"}

   Als de pagina een 404 retourneert, controleert u het volgende:

   * [ het montagepoint in uw `fstab.yaml` dossier richt aan de correcte inhoud URL ](#link-the-repository-to-the-document-author-environment): `https://content.da.live/{ORG}/{SITE}/`
   * [ u hebt de app van de Synchronisatie van de Code gevormd om met uw bewaarplaats te verbinden GitHub ](#step-5%3A-add-the-aem-code-sync-app).
   * [ u hebt de inhoud aan het milieu van de Auteur van het Document gepubliceerd gebruikend het de kloonhulpmiddel van de demo inhoud ](#step-6%3A-add-content-documents-for-your-storefront).


1. De voorbeeldcatalogusgegevens weergeven die afkomstig zijn van de standaardinstantie van Commerce Optimizer.

   1. Klik in de winkelkoptekst op het vergrootglas dat u wilt zoeken naar `tires` .

      ![[!DNL View product list page]](./assets/storefront-site-with-aco-data.png){width="675" zoomable="yes"}

   1. De pers **gaat** binnen om de pagina van onderzoeksresultaten te bekijken.

      ![[!DNL View search results page]](./assets/storefront-with-aco-search-results-page.png){width="675" zoomable="yes"}

      De onderdelen van de pagina met zoekresultaten worden gedefinieerd door het inhoudsdocument van `search` . De gegevens van de zoekresultaten worden gevuld op basis van de storefront-configuratie in `config.json` .

   1. Bekijk de pagina met productdetails door een bandenproduct op de pagina te selecteren.

      ![[!DNL View product details page]](./assets/storefront-with-aco-pdp-page.png){width="675" zoomable="yes"}

      De onderdelen van de pagina met productdetails worden gedefinieerd door het `default` -inhoudsdocument in de map `product` .

### Stap 8: Ontwikkelen in uw lokale omgeving

In deze sectie, werkt u de storefrontconfiguratie van uw lokale ontwikkelomgeving bij.

* Werk de storefront configuratie bij om met het eindpunt van GraphQL voor de [!DNL Adobe Commerce Optimizer] instantie te verbinden die Adobe voor u leverde.
* Werk de koptekstwaarden bij om gegevens van uw instantie op te halen.

#### Lokale ontwikkeling starten

1. In uw winde, checkout uw belangrijkste tak, en stel het aan laatste terug begaat op de verre tak.

   ```bash
   git checkout main
   git reset --hard origin/main
   ```

1. Installeer de vereiste afhankelijkheden.

   ```bash
   npm install
   ```

1. Start de lokale ontwikkelingsserver.

   ```bash
   npm start
   ```

   De eerste pagina van de tekstbouwsteenwinkel moet zichtbaar zijn in uw browser op `http://localhost:3000` .

   ![[!DNL Configure github repo to pull all branches from boilerplate repo]](./assets/aco-storefront-local-dev-env.png){width="700" zoomable="yes"}


#### De storefrontconfiguratie bijwerken

Werk het storefront configuratiedossier bij en voorproef de veranderingen in uw lokale ontwikkelomgeving.

1. Werk in uw IDE de storefront configuratie bij om met de [!DNL Adobe Commerce Optimizer] instantie te verbinden die Adobe voor u heeft voorzien.

   1. Open het `config.json` -bestand.

   1. Werk de volgende waarden bij met behulp van het eindpunt voor de instantie [!DNL Adobe Commerce Optimizer] :

      * **`commerce-endpoint`** - Vervang de bestaande waarde door de URL van het eindpunt.

        ```json
        "commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/{tenantId}/graphql"
        ```

      * **`ac-environment-id`** - Vervang de bestaande waarde met huurderidentiteitskaart van uw eindpunt URL.

        ```json
        "ac-environment-id": "{tenantId}"
        ```

   1. Sla het bestand op.

      Als uw lokale voorvertoning correct werkt, worden de updates toegepast op uw lokale winkel.

1. Controleer de site om de resultaten van de configuratiewijziging te bekijken.

   1. Navigeer in de browser naar `http://localhost:3000` en vernieuw de pagina.

   1. Klik in de winkelkoptekst op het vergrootglas dat u wilt zoeken naar `tires` .

      ![ Onderzoek naar banden ](./assets/storefront-header-empty-search-list.png){width="675" zoomable="yes"}

   1. Pers **gaat** binnen om de pagina van de Resultaten van het Onderzoek te tonen.

      ![ Lege onderzoeksresultaten met ongeldige kopbalwaarden ](./assets/storefront-configuration-with-incorrect-headers.png){width="675" zoomable="yes"}

      De zoekopdracht levert geen resultaten op omdat de headerwaarden in het configuratiebestand van de winkel zijn gebaseerd op de standaardinstantie. Nu de configuratie naar de voor u ingerichte [!DNL Adobe Commerce Optimizer] -instantie wijst, zijn deze waarden ongeldig.

### Volgende stappen

Zie [ het gebruiksgeval van begin tot eind van de Beheerder van de Opslag en van de Catalogus ](./use-case/admin-use-case.md) om meer over het beheren van en het tonen van inhoud en gegevens in de storefront te leren.

>[!MORELIKETHIS]
>
> Zie de [ documentatie van Adobe Commerce Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/) om meer over het bijwerken van plaatsinhoud te leren en met Commerce frontend componenten en backend gegevens te integreren.
