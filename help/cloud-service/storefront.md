---
title: Winefront instellen
description: Leer hoe te om het steigereedschap in werking te stellen om uw  [!DNL Adobe Commerce as a Cloud Service]  storefront te opstelling.
role: Developer
exl-id: 02928dc4-1777-483e-b0ee-b04fc813864d
source-git-commit: 7f7a674b856090bd02752a9e2ad29475b2b56fcf
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# Winefront instellen

{{accs-early-access}}

In de volgende stappen wordt getoond hoe u snel een Adobe Commerce Storefront kunt instellen die wordt aangedreven door Edge Delivery met de opdracht `aio commerce init` . Met dit proces wordt het volgende ingesteld:

* [ Commerce Storefront die door Edge Delivery Services ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=nl-NL) wordt aangedreven - een uitvoerende, scalable, en veilige opslagplaats die door Adobe Edge Delivery Services wordt aangedreven.
* [ API Net voor Adobe Developer App Builder ](https://developer.adobe.com/graphql-mesh-gateway/mesh/) - een API platform dat ontwikkelaars toestaat om veelvoudige gegevensbronnen in één enkel eindpunt van GraphQL te combineren. API Mesh organiseert de API van derden met Adobe API via één gateway. Één vraag aan het enige eindpunt van GraphQL kan resultaten van veelvoudige bronnen terugkeren.
* [ Adobe Developer Console ](https://developer.adobe.com/developer-console/docs/guides/) - een inzameling van ontwikkelaarshulpmiddelen met toegang tot APIs, gebeurtenissen, runtime functies, en stop- ins, die u kunt gebruiken om projecten voor de toepassingen van Adobe te bouwen.
* [ Adobe I/O Runtime ](https://developer.adobe.com/runtime/docs/) - een serverloze motor voor het opstellen van douanecode die aan gebeurtenissen antwoordt en functies in de wolk uitvoert.

## Vereisten

Voordat u de opdracht `aio commerce init` uitvoert, moet u aan de volgende voorwaarden voldoen:

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

1. Installeer [ CLI van Adobe I/O Runtime ](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

   ```bash
   npm install -g @adobe/aio-cli
   ```

1. Installeer de insteekmodule Adobe I/O API Mesh.

   ```bash
   aio plugins:install @adobe/aio-cli-plugin-api-mesh
   ```

1. Installeer de Adobe I/O Commerce-insteekmodule.

   ```bash
   aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce
   ```

1. Bestaande plug-ins bijwerken.

   ```bash
   aio plugins:update
   ```

1. Log in bij je Adobe Experience Cloud account.

   ```bash
   aio login
   ```

1. Selecteer de IMS-org, het project en de werkruimte. Gebruik de pijlsleutels en druk **binnengaan** om uw selectie te maken. Voor meer informatie over `aio` bevelen, verwijs naar de [ documentatie van Adobe I/O CLI ](https://github.com/adobe/aio-cli-plugin-console?tab=readme-ov-file#commands).

   ```bash
   aio console org select
   ```

   ```bash
   aio console project select
   ```

   ```bash
   aio console workspace select
   ```

1. Als u niet reeds hebt, keur de Termijnen van de Ontwikkelaar van Gebruik in de console van Adobe Developer door aan https://developer.adobe.com/console/home te navigeren en **te klikken Accepteren en verdergaan** goed.

## De opdracht `aio commerce init` uitvoeren

Als u de volgende opdracht uitvoert, wordt een basisstructuur voor uw Commerce-winkel gemaakt. Deze steigers bieden een uitstekende startplaats voor het bouwen en begrijpen van uw winkel. Voor meer informatie over het werken met de storefront, zie de [ documentatie van Adobe Commerce Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL).


1. Voer de opdracht `init` uit:

   ```bash
   aio commerce init
   ```

1. Als u reeds in GitHub wordt geregistreerd, ga `Y` in om tot de repo onder uw gebruikersbenaming te leiden.

1. Voer de naam in van de opslagplaats die u wilt maken.

1. Selecteer een van de volgende opties:

   * **Gebruik de huurder van demo Adobe Commerce** - gebruik een demo huurder.
      * Als u deze optie selecteert, wordt u gevraagd om de AEM Code Sync beide in een browservenster te installeren. U moet de gegevensopslagruimte opgeven die u hebt gemaakt en de beide autoriseren. Ga terug naar de CLI en voer `y` in om de installatie van de AEM Code Sync bot te bevestigen.
   * **kies een beschikbare huurder van Adobe Commerce** - selecteer een bestaande huurder van Commerce in de geselecteerde organisatie.
      * Als u deze optie selecteert, moet u het project en de werkruimte selecteren om een net binnen tot stand te brengen.

   >[!NOTE]
   >
   >Als u de optie `Pick an available API (Mesh -> SaaS)` selecteert, moet u een bestaand project en een bestaande Workspace in de Adobe Developer Console hebben. [ Creërend een templated project ](https://developer.adobe.com/developer-console/docs/guides/projects/projects-template/) en het selecteren van App Builder zal automatisch tot de noodzakelijke werkruimten leiden.

1. Nadat het proces is voltooid, kunt u de winkel op de volgende manieren aanpassen:

   * Uw code aanpassen: `https://github.com/<username or org>/<repo name>`
   * Uw inhoud bewerken: `https://da.live/#/<username or org>/<repo name>`
   * Uw configuratie beheren: `https://da.live/sheet#/<username or org>/<repo name>/configs-stage`
   * Een voorvertoning van uw winkel weergeven: `https://main--<repo name>--<username or org>.aem.page/`
   * Lokaal uitvoeren: `aio commerce:dev`

Om uw storefront aan te passen, verwijs naar de [ documentatie van Adobe Commerce Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL).
