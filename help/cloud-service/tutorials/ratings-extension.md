---
title: Zelfstudie over het verlengen van beoordelingen
description: Leer hoe u een productrating-extensie maakt voor Adobe Commerce as a Cloud Service met App Builder en AI-hulpmiddelen voor ontwikkeling.
role: Developer
hide: true
hidefromtoc: true
source-git-commit: d0b9fd3ebbf0c88abbbf12821c5c4825ffcf10f0
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Zelfstudie over het verlengen van beoordelingen (Beta)

>[!NOTE]
>
>De AI-gereedschappen die in deze zelfstudie worden gebruikt, bevinden zich momenteel in Beta en kunnen bugs of andere problemen bevatten.

Deze zelfstudie begeleidt u bij het maken van een productrating-extensie voor [!DNL Adobe Commerce as a Cloud Service] gebruik van [!DNL Adobe App Builder] - en AI-ontwikkelingsprogramma&#39;s.

Alvorens u begint, voltooi de [ eerste vereisten ](./tutorial-prerequisites.md).

## Voorwaarden verifiëren

Controleer of de volgende voorwaarden zijn geïnstalleerd:

```bash
# Check Node.js version (should be 22.x.x)
node --version

# Check npm version (should be 9.0.0 or higher)
npm --version

# Check Git installation
git --version

# Check Bash shell installation
bash --version
```

Als om het even welke voorafgaande bevelen niet de verwachte resultaten terugkeren, zie de [ eerste vereisten ](tutorial-prerequisites.md) voor begeleiding.

## Uitbreiding

Deze sectie begeleidt u door het proces om een classificatieuitbreiding voor Adobe Commerce as a Cloud Service te ontwikkelen gebruikend de hulp van AI ontwikkelingshulpmiddelen.

1. Navigeer naar **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]** en controleer of de gereedschapset `commerce-extensibility` zonder fouten is ingeschakeld. Als er fouten optreden, schakelt u de gereedschapset in en uit.

   ![ montages van de Curseur ](../assets/cursor-settings.png){width="600" zoomable="yes"}

   >[!NOTE]
   >
   >Als u werkt met ontwikkelprogramma&#39;s voor AI-toepassingen, zijn er natuurlijke variaties in de code en de reacties die door de agent worden gegenereerd.
   >Als u om het even welke kwesties met uw code ontmoet, kunt u altijd de agent vragen om u te helpen het zuiveren.

1. Als u documentatie hebt toegevoegd aan de context van de Cursor, maak het onbruikbaar:

   - Navigeer aan [!UICONTROL **Curseur**] > [!UICONTROL **Montages**] > [!UICONTROL **de Montages van de Curseur**] > [!UICONTROL **Indexeren &amp; Dokken**] en schrap om het even welke vermelde documentatie.

   ![ maak documentatie ](../assets/disable-documentation.png){width="600" zoomable="yes"} onbruikbaar

1. Code genereren voor een extensie voor productbeoordelingen:
   - Van Curseur het curseurpraatje windiow, uitgezochte **wijze van de Agent**.
   - Voer de volgende vraag in:

   ```plain
   Implement an Adobe Commerce as a Cloud Service extension to handle Product Ratings.
   
   Implement a REST API to handle GET ratings requests.
   
   GET requests will have to support the following query parameters:
   
   sku -> product SKU
   ```

   >[!NOTE]
   >
   >Als de agent om de documentatie verzoekt te zoeken, sta het toe.

1. Beantwoord de vragen van de agent precies om het te helpen de beste code produceren.

   ![ ga herinnering in Curseur ](../assets/enter-prompt.png){width="600" zoomable="yes"} binnen

   ![ de Agent vraagt het verduidelijken vragen ](../assets/agent-questions.png){width="600" zoomable="yes"}

1. Gebruik de volgende voorbeeldtekst om de vragen van de agent aan opstellings willekeurig gevormde classificatiegegevens te beantwoorden:

   ```plain
   Yes, this headless extension is for Adobe Commerce as a Cloud Service storefront,
   but we do not need any authentication for the GET API because guest users should be able to use it on the storefront.
   
   This extension will be called directly from the storefront, no async invocation, such as events or webhooks, is required.
   
   Start with just the GET API for now, we will implement other CRUD operations at a later time.
   
   We do not need a DB or storage mechanism right now, just return random ratings data between 1 and 5 and a ratings count between 1 and 1000.
   
   The API should only return the average rating for the product and the total number of ratings.
   We do not need to add tests right now.
   ```

   De agent maakt een `requirements.md` -bestand dat als bron van waarheid voor de implementatie fungeert.

   ![ gecreeerd dossier van Vereisten ](../assets/requirements-file.png){width="600" zoomable="yes"}

1. Controleer het `requirements.md` -bestand en verifieer het plan.

   Als alles correct kijkt, instrueer de agent om zich aan **Fase 2 te bewegen - de Planning van de Architectuur**.
1. Controleer het architectuurplan.
1. Geef de agent de opdracht om door te gaan met het genereren van code.

   De agent produceert de noodzakelijke code en verstrekt een gedetailleerde samenvatting met uw volgende stappen.

   ![ Architectuur planning ](../assets/architecture-planning.png){width="600" zoomable="yes"}

   ![ Overzicht van de generatie van de Code ](../assets/code-generation-summary.png){width="600" zoomable="yes"}

   ![ Volgende stappen ](../assets/next-steps.png){width="600" zoomable="yes"}

### Lokale tests

1. Vraag de agent om u te helpen de code plaatselijk testen.

   ```plain
   Test the ratings API locally on a dev server using cURL.
   ```

1. Volg de instructies van de agent en bevestig dat de API lokaal werkt.

   ![ Lokale het testen ](../assets/local-testing.png){width="600" zoomable="yes"}

   ![ Lokale testende resultaten ](../assets/local-testing-1.png){width="600" zoomable="yes"}

### De extensie implementeren

1. Na het verifiëren van de geproduceerde code, stel de uitbreiding op gebruikend de volgende herinnering:

   ```plain
   Deploy the ratings API.
   ```

   De agent voert een pre-plaatsingsklaar beoordeling uit alvorens op te stellen.

   ![ pre-plaatsingsbeoordeling ](../assets/pre-deployment-assessment.png){width="600" zoomable="yes"}

1. Wanneer u met de beoordelingsresultaten vertrouwd bent, instrueer de agent om met plaatsing te werk te gaan.

   De agent gebruikt toolkit MCP om, automatisch te verifiëren en op te stellen.

   ![ Plaatsing ](../assets/deployment-process.png){width="600" zoomable="yes"}

### Post-implementatie

U kunt de API testen voordat u deze integreert in de winkel. De agent moet de locatie van de nieuwe actie en een teststrategie opgeven.

![ het Testen strategie ](../assets/testing-strategy.png){width="600" zoomable="yes"}

U kunt de API ook handmatig testen met cURL in een terminal:

```bash
curl -s "https://<your-site>.adobeioruntime.net/api/v1/web/ratings/ratings?sku=TEST-SKU-123"
```

![ cURL test ](../assets/curl-test.png){width="600" zoomable="yes"}

### Integreren met Edge Delivery Services

Als u de API voor classificaties wilt integreren met een [!DNL Adobe Commerce] storefront die wordt aangestuurd door [!DNL Edge Delivery Services] , vraagt u de agent een servicecontract te maken met de vereisten voor de API voor classificaties:

```plain
Create a service contract for the ratings api that I can pass on to the storefront agent. Name it RATINGS_API_CONTRACT.md
```

![ contract van de Dienst ](../assets/create-contract.png){width="600" zoomable="yes"}

![ de contractdetails van de Dienst ](../assets/contract.png){width="600" zoomable="yes"}
<!-- 
Return to the terminal and run the following command in the `extension` folder to copy the file to the `storefront` folder:

```bash
cp RATINGS_API_CONTRACT.md ../storefront
``` -->

### Volgende stappen

Nu u het bevoegdheids-API-contract hebt, kunt u beginnen met het bouwen van het storefront-gedeelte (frontend) van de bevoegdheidsuitbreiding.

<!-- 
## Connect to the storefront

This section teaches you how to implement real storefront features and communicate effectively with AI agents when working with [!DNL Adobe Commerce] dropins and [!DNL Edge Delivery Services].

>[!NOTE]
>
>The prompts provided are starting points. Although you can use them without modification, consider having a natural conversation with the agent.
>
>When working with AI-assisted development tools, there are always natural variations in the code and responses generated by the agent.
>
>If you encounter any issues with your code, ask the agent to help you debug it.

### Ratings stars and review count implementation

1. Navigate to the `storefront` folder:

   ```bash
   cd storefront
   ```

1. Open the storefront folder in a new Cursor window.

    Alternatively, if you have the [Cursor CLI](https://cursor.com/docs/configuration/shell#installing-cli-commands) installed, open the window by using the following command in your terminal:

   ```bash
   cursor .
   ```

1. Start the local development server:

   ```bash
   npm run start
   ```

1. In a browser, navigate to the Apparel page:

   ```plain
   http://localhost:3000/apparel
   ```

1. Observe the boilerplate storefront UI layout and note the lack of visual product ratings.

1. Use the following prompt with your agent:

   ```plain
   Implement product ratings in the storefront.

   Add a 5-star rating display with a review count underneath each product name on the product list page, product details page, and product recommendations.

   Use the dropin slot system where available.

   Use @RATINGS_API_CONTRACT.md to understand how to use the ratings API.
   ```

1. Observe the changes in the codebase, and watch the Apparel page for updates.

   You should see the following changes in your development environment and browser:

   * A product rating "component" is automatically created.
   * The component is integrated into product-details, product-list-page, and product-recommendations blocks using [dropin slots](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/customize/slots).
   * Stars display with proper fill proportions based on mock rating values.

![Product Ratings Implementation](../assets/product-ratings-implementation.png){width="600" zoomable="yes"}

## Tutorial recap

Here is a summary of the topics covered in this tutorial:

* **Feature implementation**: How to describe new functionality to an AI agent.
* **Iterative changes**: Making quick modifications to existing code.
* **Complex UI components**: Building interactive features with visual references.
* **Dropin integration**: Working with [!DNL Adobe Commerce] dropin containers and slots.
* **Component reusability**: Creating shared components used across multiple blocks.

## Next steps

For further experimentation with this tutorial, use the following suggestions to further customize your ratings extension, or create your own modifications:

### Change the star colors

Use the following prompt to your agent:

```plain
Change the star fill color to red.
```

**Expected outcome:**

The stars are changed to red.

![Red Star Colors](../assets/red-star-colors.png){width="600" zoomable="yes"}

### Add rating distribution modal

The following steps show how the agent handles complex UI features with visual references.

1. **Before starting:** Save the following mock image and paste it into the chat with your storefront agent.

   ![Rating Distribution Mockup](../assets/rating-distribution-mockup.png){width="600" zoomable="yes"}

1. Follow these steps to create the ratings distribution modal using the reference image as a guide:

   * Update the API to return additional data representing the ratings distribution.
   * Update the API Contract.
   * Update the contact in the storefront codebase.
   * Ask the storefront agent to use the reference image and updated API Contract to add the ratings distribution to the PDP page.

1. Observe the following changes in the codebase, and watch the Apparel page for updates:

   * How the agent interprets the visual mockup
   * Whether it uses appropriate HTML structure for accessibility
   * How it handles the positioning and interaction states

#### Troubleshooting

* If the modal does not appear, check the browser console for errors.
* If positioning is off, ask the agent to fix it using the following format:

   ```plain
   adjust the modal position to be...
   ```

![Rating Distribution Modal](../assets/rating-distribution-modal.png){width="600" zoomable="yes"}
 -->
