---
title: Zelfstudie over het verlengen van beoordelingen
description: Leer hoe u een productrating-extensie maakt voor Adobe Commerce as a Cloud Service met App Builder en AI-hulpmiddelen voor ontwikkeling.
role: Developer
hide: true
hidefromtoc: true
source-git-commit: 453b21f89d2024a8d6927fa082affdd5abb6e5cd
workflow-type: tm+mt
source-wordcount: '1337'
ht-degree: 0%

---

# Adobe Developers Live - werkmap voor het lab in Adobe Commerce

Dit laboratorium begeleidt u door het bouwen van een uitbreiding van productclassificaties voor [!DNL Adobe Commerce as a Cloud Service] gebruikend [!DNL Adobe App Builder] en AI-bijgewoonde ontwikkelingshulpmiddelen.

## Voorwaarden verifiëren

Controleer of de volgende voorwaarden zijn geïnstalleerd:

```bash
# Check Node.js version (should be 22.x.x)
node --version

# Check npm version (should be 9.0.0 or higher)
npm --version

# Check Git
git --version

# Check Bash
bash --version
```

## Aanmelden bij de Adobe Developer Console

1. Navigeer aan [ Adobe Developer Console ](https://developer.adobe.com/console){target="_blank"}.
1. Als u reeds het programma wordt geopend, klik uw profielpictogram in het hoogste recht en klik **Teken uit** knoop.
1. Meld u aan met de e-mailadres en het wachtwoord voor uw licentie voor het laboratorium.
1. Als u wordt ertoe aangezet om een secundair e-mailadres of een telefoonaantal toe te voegen, klik **niet nu**.
1. Wanneer u wordt ertoe aangezet om een organisatieprofiel te selecteren, uitgezochte **Laboratoria van Adobe Commerce**.

   ![ selecteren-organisatie ](./assets/select-org.png){width="600" zoomable="yes"}

1. Als u wordt ertoe aangezet om de voorwaarden goed te keuren, klik de verbinding om de termijnen te lezen, dan klik **Accepteren en verdergaan**.

   ![ goedkeuren-termijnen ](./assets/accept-terms.png){width="600" zoomable="yes"}

## Setup-script uitvoeren

Als de [ eerste vereisten ](#verify-prerequisites) geïnstalleerd zijn, en u hebt binnen aan Adobe Developer Console ondertekend, download en stel het opstellingsmanuscript in werking. Alternatief, kunt u manueel opstelling het manuscript door de [ stappen te volgen van de 1} laboratoriumeerste vereisten.](workbook-prerequisites.md)

1. Clone the repository that contains the setup script:

   ```bash
   git clone https://github.com/adobe-commerce/commerce-adl-2025.git
   ```

   >[!NOTE]
   >
   >Als het manuscript ontbreekt, verwijs naar de [ eerste vereisten ](workbook-prerequisites.md) en ga verder waar het manuscript een fout ontmoette.

1. Navigeer in de gegevensopslagruimte:

   ```bash
   cd commerce-adl-2025
   ```

1. Voer het instellingsscript uit:

   ```bash
   bash adl-setup.sh
   ```

   Terwijl het manuscript loopt, zult u worden ertoe aangezet om uw gebruikersbenaming en wachtwoord in te gaan, die tijdens het laboratorium zullen worden verstrekt. Uw gebruikersnaam weerspiegelt uw locatie en nummer van uw licentie. Als u bijvoorbeeld in San Jose, CA, licentie 123 werkt, is uw gebruikersnaam `sjc-adl-123@adobeeventlab.com` .

   Bovendien, zou u het project moeten selecteren dat aan uw zitplaatsaantal en de **werkruimte van het stadium** beantwoordt. Uw projectnaam geeft uw locatie en nummer van uw licentie aan. Als u bijvoorbeeld in San Jose, CA, licentie 123 werkt, is de projectnaam `SJC ADL 123` .

## Uitbreiding

Deze sectie begeleidt u door het proces om een classificatieuitbreiding voor Adobe Commerce as a Cloud Service te ontwikkelen gebruikend de hulp van AI ontwikkelingshulpmiddelen.

### Uitbreidbare AI-gereedschappen installeren

Stel de ontwikkelprogramma&#39;s voor AI-toepassingen in de map `extension` in:

```bash
cd extension
```

```bash
aio commerce extensibility tools-setup
```

![ installeer AI hulpmiddelen ](./assets/install-ai-tools.png){width="600" zoomable="yes"}

### Cursor openen

>[!NOTE]
>
>Als u werkt met ontwikkelprogramma&#39;s voor AI-toepassingen, zijn er natuurlijke variaties in de code en de reacties die door de agent worden gegenereerd.
>Als u om het even welke kwesties met uw code ontmoet, kunt u altijd de agent vragen om u te helpen het zuiveren.

Open de [!DNL Cursor] toepassing en navigeer aan de `extension` omslag of als u de [ geïnstalleerde Curseur CLI ](https://cursor.com/docs/configuration/shell#installing-cli-commands) hebt, ga het volgende bevel in uw terminal in:

```bash
cursor .
```

![ Open Cursor ](./assets/open-cursor.png){width="600" zoomable="yes"}

Op dit moment worden alle [!DNL Cursor] -regels geïnstalleerd in de map `.cursor/rules` . U kunt hulpmiddelen MCP in de **Montages MCP** in [!DNL Cursor] vinden. Controleer of de gereedschapsset `commerce-extensibility` zonder fouten is ingeschakeld. Als er fouten optreden, schakelt u de gereedschapset in en uit.

![ montages van de Curseur ](./assets/cursor-settings.png){width="600" zoomable="yes"}

Als u om het even welke documentatie hebt die aan de context van Cursor wordt toegevoegd, zult u het moeten onbruikbaar maken. Navigeer aan [!UICONTROL **Curseur**] > [!UICONTROL **Montages**] > [!UICONTROL **de Montages van de Curseur**] > [!UICONTROL **Indexeren &amp; Dokken**] en schrap om het even welke vermelde documentatie.

![ maak documentatie ](./assets/disable-documentation.png){width="600" zoomable="yes"} onbruikbaar

### Codegeneratie

In deze sectie wordt getoond hoe u met behulp van AI-hulpmiddelen code kunt genereren voor een productrating-extensie.

#### Vereisten definiëren

U implementeert een extensie die als API fungeert voor productbeoordelingen. De extensie [!DNL App Builder] reageert met classificatiedetails voor een bepaalde SKU.

**Eerste herinnering:**

Gebruik de volgende prompt in [!DNL Cursor] :

1. Open het chatvenster in Cursor.
1. Selecteer de **wijze van de Agent**.
1. Voer de volgende vraag in:

   ```text
   Implement an Adobe Commerce as a Cloud Service extension to handle Product Ratings.
   Implement a REST API to handle GET ratings requests.
   GET requests will have to support the following query parameters:
   
   sku -> product SKU
   ```

1. Als de agent om de documentatie verzoekt te zoeken, sta het toe.

![ ga herinnering in Curseur ](./assets/enter-prompt.png){width="600" zoomable="yes"} binnen

De agent onderzoekt de vereisten en stelt verduidelijkende vragen. Beantwoord de vragen van de agent precies om het te helpen de beste code produceren.

![ de Agent vraagt het verduidelijken vragen ](./assets/agent-questions.png){width="600" zoomable="yes"}

**herinnering van de Reactie:**

Gebruik het volgende antwoord om de vragen van de agent te beantwoorden:

```text
Yes, this headless extension is for Adobe Commerce as a Cloud Service storefront,
but we do not need any authentication for the GET API because guest users should be able to use it on the storefront.
This extension will be called directly from the storefront,
no async invocation, such as events or webhooks, is required.
Let's start with just the GET API for now,
we will implement other CRUD operations at a later time.
We do not need a DB or storage mechanism right now,
just return random ratings data between 1 and 5 and a ratings count between 1 and 1000.
The API should only return the average rating for the product and the total number of ratings.
We do not need to add tests right now.
```

De agent maakt een `requirements.md` -bestand dat als bron van waarheid voor de implementatie fungeert.

![ gecreeerd dossier van Vereisten ](./assets/requirements-file.png){width="600" zoomable="yes"}

#### Verifieer de vereisten en de planarchitectuur

1. Controleer het `requirements.md` -bestand.
1. Als alles correct kijkt, instrueer de agent om zich aan **Fase 2 te bewegen - de Planning van de Architectuur**.
1. Controleer het architectuurplan.
1. Geef de agent de opdracht om door te gaan met het genereren van code.

![ Architectuur planning ](./assets/architecture-planning.png){width="600" zoomable="yes"}

#### Code genereren

De agent produceert de noodzakelijke code en verstrekt een gedetailleerde samenvatting met uw volgende stappen.

![ Overzicht van de generatie van de Code ](./assets/code-generation-summary.png){width="600" zoomable="yes"}

![ Volgende stappen ](./assets/next-steps.png){width="600" zoomable="yes"}

### Lokale tests

Vraag de agent om u te helpen de code plaatselijk testen.

```text
Test the ratings API locally on a dev server using cURL.
```

Volg de instructies van de agent en bevestig dat de API lokaal werkt.

![ Lokale het testen ](./assets/local-testing.png){width="600" zoomable="yes"}

![ Lokale testende resultaten ](./assets/local-testing-1.png){width="600" zoomable="yes"}

### De extensie implementeren

Nadat u de gegenereerde code hebt geverifieerd, kunt u de extensie implementeren met de volgende prompt:

```text
Deploy the ratings API.
```

#### Evaluatie voorafgaand aan de implementatie

De agent voert een pre-plaatsingsklaar beoordeling uit alvorens op te stellen.

![ pre-plaatsingsbeoordeling ](./assets/pre-deployment-assessment.png){width="600" zoomable="yes"}

#### Implementeren

Wanneer u met de beoordelingsresultaten vertrouwd bent, instrueer de agent om met plaatsing te werk te gaan. De agent gebruikt toolkit MCP om, automatisch te verifiëren en op te stellen.

![ Plaatsing ](./assets/deployment-process.png){width="600" zoomable="yes"}

### De API testen

U kunt de API testen voordat u deze integreert in de winkel.

De agent verstrekt de plaats van de nieuwe actie en een het testen strategie.

![ het Testen strategie ](./assets/testing-strategy.png){width="600" zoomable="yes"}

#### Handmatig testen met cURL

Test de API handmatig met cURL in een terminal:

```bash
curl -s "https://<your-site>.adobeioruntime.net/api/v1/web/ratings/ratings?sku=TEST-SKU-123"
```

![ cURL test ](./assets/curl-test.png){width="600" zoomable="yes"}

### Integreren met Edge Delivery Services

Als u de API voor classificaties wilt integreren met een [!DNL Adobe Commerce] storefront die wordt aangestuurd door [!DNL Edge Delivery Services] , vraagt u de agent een servicecontract te maken met de vereisten voor de API voor classificaties:

```text
Create a service contract for the ratings api that I can pass on to the storefront agent. Name it RATINGS_API_CONTRACT.md
```

![ contract van de Dienst ](./assets/create-contract.png){width="600" zoomable="yes"}

![ de contractdetails van de Dienst ](./assets/contract.png){width="600" zoomable="yes"}

Ga terug naar de terminal en voer de volgende opdracht in de map `extension` uit om het bestand naar de map `storefront` te kopiëren:

```bash
cp RATINGS_API_CONTRACT.md ../storefront
```

## Verbinding maken met de winkel

Deze sectie helpt u bij het implementeren van echte storefront-functies en laat zien hoe u effectief kunt communiceren met AI-agents wanneer u werkt met [!DNL Adobe Commerce] dropins en [!DNL Edge Delivery Services] .

>[!NOTE]
>
>De verstrekte herinneringen zijn uitgangspunt, zou u vrij moeten voelen om een natuurlijk gesprek met de agent te hebben. Als u werkt met ontwikkelprogramma&#39;s voor AI-toepassingen, zijn er natuurlijke variaties in de code en de reacties die door de agent worden gegenereerd.
>
>Als u om het even welke kwesties met uw code ontmoet, kunt u altijd de agent vragen om u te helpen zuivert het.

### Classificatiesterren en aantal revisies implementeren

1. Navigeer naar de map `storefront` :

   ```bash
   cd storefront
   ```

1. Open de opslagmap in een nieuw cursorvenster. Als u de [ geïnstalleerde Curseur CLI ](https://cursor.com/docs/configuration/shell#installing-cli-commands) hebt, ga het volgende bevel in uw terminal in:

   ```bash
   cursor .
   ```

1. Start de lokale ontwikkelingsserver:

   ```bash
   npm run start
   ```

1. Navigeer in een browser naar de pagina Apparel:

   ```text
   http://localhost:3000/apparel
   ```

1. Bekijk de indeling van de boilerplate storefront UI.

1. Gebruik de volgende herinnering met uw agent:

   ```text
   Implement product ratings to the storefront.
   Add a 5-star rating display with a review count underneath each product name on the product list page, product details page, and product recommendations.
   Use the dropin slot system where available.
   
   Use the @RATINGS_API_CONTRACT.md to understand how to use the ratings api.
   ```

   >[!NOTE]
   >
   >Als u wordt ertoe aangezet om de lokale ontwikkelingsserver te beginnen, informeer de agent dat het reeds loopt.

1. Bekijk de wijzigingen in de codebase en bekijk de pagina Apple voor updates.

**Verwachte uitkomst:**

* Er wordt automatisch een productrating &#39;component&#39; gemaakt.
* De component is geïntegreerd in product-details, product-lijst-pagina, en product-aanbevelingen blokken gebruikend Sleuven.
* De sterren worden weergegeven met de juiste vulverhoudingen op basis van de mock-classificatiewaarden.

![ Implementatie van de Classificaties van het Product ](./assets/product-ratings-implementation.png){width="600" zoomable="yes"}

### De sterkleuren wijzigen

Gebruik de volgende herinnering aan uw agent:

```text
Change the star fill color to red.
```

**Verwachte uitkomst:**

De sterren worden rood.

![ Rode Ster Kleuren ](./assets/red-star-colors.png){width="600" zoomable="yes"}

## Storefront-rechthoek

In deze zelfstudie hebben we de volgende onderwerpen behandeld:

* **implementatie van de Eigenschap**: Hoe te om nieuwe functionaliteit aan een AI agent te beschrijven.
* **Iteratieve veranderingen**: Het maken van snelle wijzigingen in bestaande code.
* **Complexe UI componenten**: De bouw van interactieve eigenschappen met visuele verwijzingen.
* **integratie Dropin**: Het werken met [!DNL Adobe Commerce] droppincontainers en groeven.
* **Herbruikbaarheid van de Component**: Creërend gedeelde componenten die over veelvoudige blokken worden gebruikt.

## Volgende stappen

Als de tijd dit toelaat, kunt u uw classificatieuitbreiding verder aanpassen door de volgende eigenschappen toe te voegen:

### Ratingdistributie modaal toevoegen (optioneel)

De volgende stappen tonen hoe de agent complexe eigenschappen UI met visuele verwijzingen behandelt.

1. **alvorens te beginnen:** sparen het volgende modelbeeld en kleef het in het praatje met uw storefront agent.

   ![ Mockup van de Distributie van de Classificatie ](./assets/rating-distribution-mockup.png){width="600" zoomable="yes"}

1. Gebruik de volgende stappen om u door het creëren van de classificatiedistributie modaal te begeleiden die op het verwijzingsbeeld wordt gebaseerd:

   * Werk API bij om extra gegevens terug te keren die de classificatiedistributie vertegenwoordigen.
   * Werk het API-contract bij.
   * Werk de contact in de storefront codebase bij.
   * Vraag de storefront agent om het verwijzingsbeeld en het bijgewerkte contract van API te gebruiken om de classificatiedistributie aan de PDP pagina toe te voegen.

1. Bekijk de volgende wijzigingen in de codebase en bekijk de pagina Apparel voor updates:

   * Hoe de agent het visuele model interpreteert
   * Of de juiste HTML-structuur voor toegankelijkheid wordt gebruikt
   * Hoe de positionering en interactiestatus worden verwerkt

**het Oplossen van problemen:**

* Controleer de browserconsole op fouten als het modaal niet wordt weergegeven.
* Als het plaatsen weg is, kunt u de agent vragen om:

  ```text
  adjust the modal position to be...
  ```

![ Modal van de Distributie van de Classificatie ](./assets/rating-distribution-modal.png){width="600" zoomable="yes"}
