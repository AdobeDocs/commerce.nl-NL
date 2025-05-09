---
title: Winefront instellen
description: Leer hoe te opstelling uw  [!DNL Adobe Commerce Optimizer]  storefront.
role: Developer
exl-id: 2b4c9e98-a30c-4a33-b356-556de5bd721a
source-git-commit: f1aa8439d6322e5278ab787f5cd096e16b7813a2
workflow-type: tm+mt
source-wordcount: '2150'
ht-degree: 0%

---

# Winefront instellen

>[!NOTE]
>
>Deze documentatie beschrijft een product in vroege-toegangsontwikkeling en weerspiegelt niet alle functionaliteit voorgenomen voor algemene beschikbaarheid.

Dit leerprogramma toont aan hoe te opstelling en gebruik [ Adobe Commerce Storefront die door Edge Delivery Services ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/) wordt aangedreven om een uitvoerbare, scalable, en veilige Commerce storefront tot stand te brengen die door gegevens van uw [!DNL Adobe Commerce Optimizer] instantie wordt aangedreven.


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
>Dit is het installatieproces van [!DNL Adobe Commerce Optimizer] voor de Adobe Commerce Edge Delivery Service Store. De extra middelen om uw [!DNL Adobe Commerce Optimizer] oplossing uit te breiden en aan te passen zijn beschikbaar door [ App Builder voor Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder) en [ API Net voor Adobe Developer App Builder ](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/api-mesh/getting-started-api-mesh). Neem voor toegang tot en gebruiksinformatie contact op met uw Adobe-accountvertegenwoordiger.

#### Sidekick installeren

Installeer de Sidekick-browserextensie om inhoud te bewerken, voor te vertonen en te publiceren naar de winkel. Zie [ de installatieinstructies van Sidekick ](https://www.aem.live/docs/sidekick#installation).


## Je winkel maken

De winkel die u voor uw [!DNL Adobe Commerce Optimizer] -project maakt, gebruikt een aangepaste versie van de Adobe Commerce op Edge Delivery Services Storefront boilerplate. De bouwsteenplaat is een reeks dossiers en omslagen die een uitgangspunt voor storefront ontwikkeling verstrekken. Dit opstellingsproces is verschillend dan het standaardopstellingsproces voor een [ Adobe Commerce op Edge Delivery Services Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/).

>[!NOTE]
>
>Dit leerprogramma gebruikt macOS, Chrome, en de Code van Visual Studio als ontwikkelomgeving. Deze instelling komt tot uiting in de schermvastleggingen en -instructies. U kunt een verschillend werkend systeem, browser, en coderedacteur gebruiken, maar UI u ziet en de stappen u neemt variëren dienovereenkomstig.

### Workflowoverzicht

Voer de volgende stappen uit om een winkelvoetnoot in te stellen die u met [!DNL Adobe Commerce Optimizer] wilt gebruiken.

1. **[creeer een inhoudsomslag](#step-1-create-a-content-folder)** - creeer een gedeelde inhoudsomslag in de Aandrijving van Google of SharePoint. Deze map bevat de voorbeeldinhoud en elementen voor uw winkel.

1. **[creeer een codebewaarplaats](#step-2-create-a-code-repository)** - creeer een bewaarplaats GitHub van Adobe Commerce + Edge Delivery Services boilerplate malplaatje. Neem alle vertakkingen van de bronopslagplaats op.
1. **[werk storefront boilerplate](#step-3-update-the-storefront-boilerplate)** bij - werk het malplaatje van het douaneboilerplate op de `aco` tak bij om uw inhoudsomslag met de storefront te verbinden.
1. **[upload de bijgewerkte storefront boilerplate code](#step-4-upload-the-updated-boilerplate-code)** - vervang de code op de `main` tak met de bijgewerkte code van de `aco` tak.
1. **[voeg app CodeSync](#step-5-add-the-aem-code-sync-app)** toe - verbind uw bewaarplaats met de Dienst van Edge Delivery. Sluit de toepassing Codesynchronisatie pas aan nadat u de broncode hebt aangepast en de code naar de `main` -vertakking hebt verplaatst.
1. **[Voorproef en publiceer uw inhoud](#step-6-preview-and-publish-your-content)** - gebruik de uitbreiding van Sidekick om de plaatsinhoud van de inhoudsomslag aan de winkel voor te vertonen en te publiceren.
1. **[voorproef uw plaats en meningssteekproefgegevens](#step-7-preview-your-site)** - verbind met uw storefront plaats om de steekproefinhoud en de gegevens van de [!DNL Adobe Commerce Optimizer] demoinstantie te bekijken.
1. **[ontwikkelt de storefront in uw lokale milieu](#step-8-develop-the-storefront-in-your-local-environment)** - installeer de vereiste gebiedsdelen. Start de lokale ontwikkelingsserver en werk de storefront-configuratie bij om verbinding te maken met de [!DNL Adobe Commerce Optimizer] -instantie die Adobe voor u heeft ingericht.
1. **[Volgende stappen](#next-steps)** - leer meer over het beheren van en het tonen van inhoud en gegevens in de storefront.

### Stap 1: Een inhoudsmap maken

Volg de instructies in de Adobe Commerce Storefront-documentatie om een gedeelde inhoudsmap toe te voegen in Google Drive of SharePoint en de voorbeeldinhoud toe te voegen. De voorbeeldinhoud bestaat uit afbeeldingen, tekst en andere elementen waaruit uw site bestaat.

* [ creeer en deel een Aandrijving van Google of de omslag van SharePoint ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/#create-and-share-folder)
* [ Laad de steekproefinhoud ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/#add-sample-content) in uw omslag.

### Stap 2: Een gegevensopslagruimte maken

Creeer een opslagboilerplate codebewaarplaats in GitHub gebruikend het Edge Delivery Services + Adobe Commerce Boilerplate malplaatje.

1. Login aan uw rekening GitHub.

1. Navigeer aan de [ aem-boilerplate-handel ](https://github.com/hlxsites/aem-boilerplate-commerce) bewaarplaats GitHub.

1. Selecteer **Gebruik dit malplaatje**, en selecteer dan **creeer een nieuwe bewaarplaats** van het drop-down menu.

   ![[!DNL Create github repo from storefront boilerplate template]](./assets/storefront-create-github-repo.png){width="700" zoomable="yes"}

   De configuratiepagina van de repository wordt weergegeven.

   ![[!DNL Configure github repo to pull all branches from boilerplate repo]](./assets/storefront-configure-github-repo.png){width="700" zoomable="yes"}

1. Vul het configuratieformulier met de volgende gegevens in:

   * **malplaatje van de Bewaarplaats** - `hlxsites/aem-boilerplate-commerce` (gebrek).
   * **omvat alle takken** - selecteer de optie om alle takken te omvatten.
   * **Eigenaar** - Uw organisatie of (vereiste) rekening.
   * **Naam van de Bewaarplaats** - een unieke naam voor uw nieuwe (vereiste) repo.
   * **Beschrijving** - een korte beschrijving van uw (facultatieve) reactie.
   * **Openbaar of Privé** - Adobe adviseert openbaar (gebrek).

1. Selecteer **creeer bewaarplaats**.

   Na enkele minuten wordt de nieuwe opslagplaats geopend.

   Negeer om het even welke berichten van het trekkingsverzoek die in het GitHub gebruikersinterface worden getoond.

### Stap 3: De storefront boilerplate bijwerken

U hebt de volgende informatie nodig om de storefront boilerplate-code bij te werken:

* **GitHub bewaarplaats URL van Stap 2** - `github.com/{ORG}/{SITE}`

   * `{ORG}` is de organisatienaam of gebruikersnaam voor de repository

   * `{SITE}` is de naam van uw opslagplaats

* **omslag URL van de Inhoud van Stap 1** - `https://drive.google.com/drive/folders/{YOUR_FOLDER_ID}`

  `{YOUR_FOLDER_ID}` is de id van de map die u hebt gemaakt met de voorbeeldinhoudsgegevens.

#### Werk de bouwsteencode bij om met uw inhoudsomslag te verbinden

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

   1. Open het {](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/#vocabulary) configuratiedossier 0} fstab.yaml.[

      ```json
      mountpoints:
       /: {YOUR_MOUNTPOINT_URL}
      
      folders:
       /products/: /products/default
      ```

   1. Vervang `{YOUR_MOUNTPOINT_URL}` door de URL van de inhoudsmap.

      Als u bijvoorbeeld Google Drive gebruikt, moet de bijgewerkte code er als volgt uitzien.

      ```json
       mountpoints:
        /: https://drive.google.com/drive/folders/1HXPWdQT-EK09IxVQV5HBSHN4QCA1a56Y
      ```

   1. Sla het bestand op.

#### De configuratie van de gegevensverbinding controleren

De configuratie van de gegevensverbinding maakt communicatie mogelijk tussen de storefront en de opgegeven [!DNL Adobe Commerce Optimizer] -instantie. Deze verbinding laat catalogusgegevens toe om aan de winkel te stromen en diverse storefront interfaces, met inbegrip van de onderzoekscomponent, productlijst, en de pagina&#39;s van productdetails te bevolken.

Voor de eerste setup van de winkel maakt u verbinding met de standaardinstantie [!DNL Adobe Commerce Optimizer] met voorbeeldgegevens.

```json
{
  "public": {
    "default": {
      "commerce-core-endpoint": "https://www.aemshop.net/graphql",
      "commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/Fwus6kdpvYCmeEdcCX7PZg/graphql",
      "headers": {
        "cs": {
          "ac-channel-id": "9ced53d7-35a6-40c5-830e-8288c00985ad",
          "ac-environment-id": "Fwus6kdpvYCmeEdcCX7PZg",
          "ac-price-book-id": "west_coast_inc",
          "ac-scope-locale": "en-US"
        }
      },
      "analytics": {
        "base-currency-code": "USD",
        "environment": "Production",
        "store-id": 1,
        "store-name": "ACO Demo",
        "store-url": "https://www.aemshop.net",
        "store-view-id": 1,
        "store-view-name": "Default Store View",
        "website-id": 1,
        "website-name": "Main Website"
      }
    }
  }
}
```

In dit bestand geven de volgende sleutelwaarden de [!DNL Adobe Commerce Optimizer] -instantie op waarmee verbinding moet worden gemaakt en bepalen de gegevens die naar de storefront stromen:

* `commerce-endpoint` geeft de instantie aan waarmee verbinding moet worden gemaakt. Deze is ingesteld op het gebruik van de standaardinstantie [!DNL Adobe Commerce Optimizer] . Dit eindpunt wordt gebruikt om catalogusgegevens terug te winnen.
* `ac-environment-id` is de huurder-id voor de instantie [!DNL Adobe Commerce Optimizer] .
* `headers` bepaalt de gegevens die van de instantie naar de storefront stromen.
   * `ac-channel-id` is ingesteld op `west_coast_inc`
   * `ac-price-book-id` is ingesteld op `west_coast_inc`
   * `ac-scope-locale` is ingesteld op `en-US`
   * `ac-price-book-id` is ingesteld op `west_coast_inc`

Met deze waarden stelt u de kanaal-id, de landinstelling en de id van het prijzenboek in om catalogusgegevens naar een specifiek verkoopkanaal te verzenden en filtert u die gegevens op basis van opgegeven waarden voor de landinstelling en het prijzenboek. Later werkt u het eindpunt bij om verbinding te maken met de instantie [!DNL Adobe Commerce Optimizer] die Adobe voor u heeft ingericht, en vervangt u de headerwaarden om de gegevens van die instantie op te halen.

#### De Sidekick-extensie configureren

Voeg de projectconfiguratie voor de uitbreiding van Sidekick toe. Deze configuratie zorgt ervoor dat Sidekick beschikbaar is om inhoud voor uw winkelproject te beheren.

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

   * Vervang de `{ORG}` -tekenreeks door de organisatie of gebruikersnaam voor de gegevensopslagruimte.

   * De `{SITE}` -tekenreeks vervangen door de naam van de gegevensopslagruimte

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

+++

1. Sla het bestand op.

### Stap 4: De bijgewerkte bouwsteencode uploaden

Als u de aangepaste storefront boilerplate-code wilt gebruiken, overschrijft u de code in de `main` -vertakking met uw updates.

1. Leg de bestanden die u hebt bijgewerkt vast en sla deze op in uw editor of IDE.

   ```bash
   git add .
   ```

1. Controleer of u de twee bijgewerkte bestanden vastlegt.

   ```bash
   git status
   On branch aco
   Your branch is up to date with 'origin/aco'.
   
   Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        new file:   fstab1.yaml
        modified:   tools/sidekick/config.json
   ```

1. Leg de wijzigingen in de `aco` -vertakking vast.

   ```bash
   git commit -m "Update storefront boilerplate for Adobe Commerce Optimizer"
   ```

1. Overschrijf de tekstbouwsteen op de `main` -vertakking met de wijzigingen in de `aco` -vertakking.

   ```bash
   git push origin aco:main -f
   ```

### Stap 5: Voeg de AEM Code Sync-app toe

Verbind uw opslagplaats met de Edge Delivery Service door de AEM Code Sync GitHub-app toe te voegen aan uw opslagplaats.

>[!IMPORTANT]
>
>Sluit de app Codesynchronisatie pas aan nadat u de bijgewerkte bouwsteencode hebt geüpload naar de hoofdvertakking van uw GitHub-opslagplaats.

1. Open de [ app van de Synchronisatie van de Code van AEM ](https://github.com/apps/aem-code-sync) configuratiepagina.

1. Selecteer **vormen**, dan met de **organisatie** voor authentiek verklaren of **rekening** die de bewaarplaats bevat u creeerde.

1. Van de vorm, kies **slechts uitgezochte bewaarplaatsen** en selecteer de bewaarplaats u creeerde.

1. Selecteer **installeer** om de app van de Synchronisatie van de Code van AEM aan uw bewaarplaats toe te voegen.

   Er wordt een bericht weergegeven dat de app is geïnstalleerd.

### Stap 6: De inhoud voorvertonen en publiceren

Als u inhoud wilt toevoegen aan uw winkel, bekijkt u een voorvertoning van de inhoud van de winkel en publiceert u deze met de Sidekick-extensie.

1. Open de inhoudsmap in Google Drive of Sharepoint.

1. Schakel Sidekick in door op het Sidekick-pictogram op de browserwerkbalk te klikken.

   ![[!DNL Turn on Sidekick from browser toolbar]](./assets/storefront-enable-sidekick-toolbar.png){width="700" zoomable="yes"}

   Als u niet het pictogram van Sidekick ziet, verifieer dat het de configuratiedossier van Sidekick, `tools/Sidekick/config.json` op de `main` tak van uw bewaarplaats GitHub [ correct ](#configure-the-sidekick-extension) wordt gevormd.

1. Gebruik de werkbalk Sidekick om een voorvertoning van uw inhoud weer te geven en deze te publiceren.

   ![[ Uitgezochte dossiers aan voorproef en te publiceren ]](./assets/storefront-content-preview-publish.png){width="700" zoomable="yes"}

   Selecteer de bestanden in elke map afzonderlijk en gebruik de werkbalk Sidekick om een voorvertoning weer te geven van alle bestanden en deze te publiceren.

   * **Voorproef** - uploadt inhoud aan het opvoeren milieu. De staging-URL&#39;s van de Storefront eindigen met `.aem.page`.

   * **publiceer** - uploadt inhoud aan het productiemilieu. Productie-URL&#39;s eindigen met `aem.live` .

Voor meer informatie, zie de ](https://www.aem.live/docs/sidekick) documentatie van Adobe Experience Manager [ Sidekick.

### Stap 7: Een voorvertoning van uw site weergeven

Controleer of zowel de inhoud van het voorbeeld als de gegevens van de Adobe Commerce Optimizer-demo-instantie correct worden weergegeven.

* **inhoud van de Steekproef** wordt gediend van uw gedeelde inhoudsomslag. Dit omvat de paginalay-outs, banners en andere inhoud die u met Sidekick hebt gepubliceerd.
* **gegevens van de Steekproef** wordt gediend van de [!DNL Adobe Commerce Optimizer] demo instantie. De gegevens omvatten productgegevens met productkenmerken, beelden, productbeschrijvingen, en prijzen bevolkt gebaseerd op de kopbalwaarden die in het archiefrontconfiguratiedossier, `config.json` worden gespecificeerd.


#### Maak verbinding met uw site om voorbeeldinhoud en -gegevens weer te geven

1. Maak verbinding met uw site door naar `https://main--{SITE}--{ORG}.aem.live` te navigeren.

   Vervang `{ORG}` en `{SITE}` door de organisatie en naam van de opslagplaats voor vaste gegevens.

   ![[!DNL ACO storefront site with boilerplate]](./assets/aco-storefront-site-boilerplate.png){width="700" zoomable="yes"}

   Als de pagina een 404 retourneert, controleert u of u de inhoud hebt gepubliceerd met de Sidekick-extensie. Controleer ook of het montagepunt in het bijgewerkte `fstab.yaml` -bestand verwijst naar de inhoudsmap die u hebt gemaakt.

1. De voorbeeldcatalogusgegevens weergeven die afkomstig zijn van de standaardinstantie van Commerce Optimizer.

   1. Zoek naar `tires` om een drop-down lijst van beschikbare bandproducten te zien.

   ![[!DNL Discover Adobe Commerce Optimizer products]](./assets/storefront-site-with-aco-data.png){width="700" zoomable="yes"}

   De zoekcomponent maakt deel uit van de storefront boilerplate-code. De gegevens van de zoekresultaten worden gevuld op basis van de storefront-configuratie in `config.json` .

   1. Pers **gaat** binnen om de pagina van de productlijst te bekijken.

      ![[!DNL View product details page]](./assets/storefront-with-aco-pdp-page.png){width="675" zoomable="yes"}

   1. Bekijk een pagina met productdetails door een bandenproduct op de pagina te selecteren.

      Als je de winkel verkent, merk je op dat sommige componenten niet werken. Als u bijvoorbeeld een product aan het winkelwagentje toevoegt, wordt een fout geretourneerd en werken de onderdelen van het accountbeheer niet. Deze problemen doen zich voor omdat deze componenten niet zijn geconfigureerd om gegevens van een Commerce-backend te ontvangen. De gegevens uit de [!DNL Adobe Commerce Optimizer] -instantie vullen alleen de pagina&#39;s met zoekcomponenten, productlijsten en productdetails in.

   1. Na het verkennen van de storefront, ga met het leerprogramma verder.


### Stap 8: De storefront in uw lokale omgeving ontwikkelen

In deze sectie, werkt u de storefrontconfiguratie van uw lokale ontwikkelomgeving bij.

* Werk de storefront configuratie bij om met het eindpunt van GraphQL voor de [!DNL Adobe Commerce Optimizer] instantie te verbinden die Adobe voor u leverde.
* Werk de koptekstwaarden bij om gegevens van uw instantie op te halen.

#### Lokale ontwikkeling starten

1. In uw winde, controleer de belangrijkste tak van uw GitHub codebewaarplaats.

   ```bash
   git checkout main
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

      De vervolgkeuzelijst wordt niet gevuld.

   1. De pers **gaat** binnen om de pagina van de lijst van het Product te tonen.

      ![ Lege onderzoeksresultaten met ongeldige kopbalwaarden ](./assets/storefront-configuration-with-incorrect-headers.png){width="675" zoomable="yes"}

      De zoekopdracht levert geen resultaten op omdat de headerwaarden in het configuratiebestand van de winkel zijn gebaseerd op de standaardinstantie. Nu de configuratie naar de voor u ingerichte [!DNL Adobe Commerce Optimizer] -instantie wijst, zijn deze waarden ongeldig.

### Volgende stappen

Zie [ het gebruiksgeval van begin tot eind van de Beheerder van de Opslag en van de Catalogus ](./use-case/admin-use-case.md) om meer over het beheren van en het tonen van inhoud en gegevens in de storefront te leren.

>[!MORELIKETHIS]
>
>* [ Adobe Experience Manager storefront documentatie ](https://experienceleague.adobe.com/developer/commerce/storefront/) om meer over het bijwerken van plaatsinhoud te leren en met uw Commerce frontend componenten en backend gegevens te integreren.
></br></br>
>* [ de documentatie van Adobe Commerce Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/) om meer over het bijwerken van plaatsinhoud te leren en met Adobe Commerce frontend componenten en backend gegevens te integreren.
