---
title: Zelfstudie over productherzieningen
description: Leer hoe u een productrelevaluatie en de extensie Vragen en antwoorden voor Adobe Commerce as a Cloud Service bouwt met App Builder-, Edge Delivery Services- en AI-tools voor ontwikkeling.
solution: Commerce
feature: App Builder, Cloud
feature-set: Commerce
role: Developer
level: Intermediate
type: Tutorial
hide: true
hidefromtoc: true
source-git-commit: 9c76bae29c05909406a40ca03a2b3d242db05f3f
workflow-type: tm+mt
source-wordcount: '2470'
ht-degree: 0%

---

# Zelfstudie over productoverzichten

Deze zelfstudie begeleidt u door het maken van een extensie waarmee klanten inhoud (vragen en antwoorden) voor productrevisie en vragen kunnen indienen voor winkels met een [!DNL Adobe Commerce as a Cloud Service] backend-functie met behulp van [!DNL Adobe App Builder] - en AI-hulpmiddelen voor ontwikkeling. De extensie biedt REST API-eindpunten voor kopers om de inhoud van productrevisie en vragen en antwoorden (vragen en antwoorden) weer te geven en te verzenden, en deze weer te geven op de pagina met productdetails (PDP).

U bouwt twee delen:

- **de uitbreiding van App Builder** — Een REACTIE API met GET en POST verrichtingen om productoverzicht en inhoud Q&amp;A met bevestiging, paginering, en persistentie in `aio-lib-state` tot stand te brengen en te bekijken.
- **integratie van de Storefront** — een blok van het productoverzicht op PDP die revisies en Q&amp;A, met vormen voor kopers toont om revisies, vragen, en antwoorden voor te leggen.

>[!NOTE]
>
>AI-agentia zijn niet deterministisch. De vragen, vragen en resultaten in deze zelfstudie zijn voorbeelden. Uw agent kan verschillende vragen, vereisten, of architectuurvoorstellen veroorzaken. Gebruik de voorbeelden in deze zelfstudie om de agent naar een vergelijkbaar resultaat te sturen.

Alvorens u begint, voltooi de [&#x200B; eerste vereisten &#x200B;](./tutorial-prerequisites.md). Dit leerprogramma gebruikt de **uitrusting van de integratieaanzet**. Controleer of u de toepassing al hebt gekloond en voltooi de stappen die op de pagina met voorwaarden worden beschreven.

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

Als om het even welke voorafgaande bevelen niet de verwachte resultaten terugkeren, zie de [&#x200B; eerste vereisten &#x200B;](./tutorial-prerequisites.md) voor begeleiding.

Controleer ook het volgende:

- U hebt een [!DNL Adobe Commerce as a Cloud Service] -instantie met productgegevens. Zie {de instanties van de Dienst van 0} Commerce Cloud [.](https://experienceleague.adobe.com/nl/docs/commerce/cloud-service/overview){target="_blank"}
- Er is een storefront-project verbonden met uw [!DNL Commerce] -instantie. Als u geen hebt, volg de stappen in [&#x200B; creeer een storefront &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/?lang=nl-NL){target="_blank"}.
- De `aem` CLI is geïnstalleerd:

  ```bash
  npm install -g @adobe/aem-cli
  ```

## Uitbreiding

In deze sectie wordt u door het ontwikkelen van een extensie geleid voor het verzenden en weergeven van productoverzicht en de inhoud van Vragen en antwoorden voor extensies voor winkeliers met een [!DNL Adobe Commerce as a Cloud Service] -backend met behulp van AIR-hulpmiddelen voor ontwikkeling. De extensie biedt een REST API om productrevisie en vraag- en antwoordinhoud te verzenden en weer te geven en op de PDP weer te geven.

1. Navigeer aan de montages MCP in uw coderende agent. Ga bijvoorbeeld in Cursor naar **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]** . Controleer of de gereedschapsset `commerce-extensibility` zonder fouten is ingeschakeld. Als er fouten optreden, schakelt u de gereedschapset in en uit.

   >[!NOTE]
   >
   >Als u werkt met ontwikkelprogramma&#39;s voor AI, verwacht u natuurlijke variaties in de code en reacties die door de agent worden gegenereerd.
   >Als u om het even welke kwesties met uw code ontmoet, vraag de agent om u te helpen het zuiveren.

1. Als u documentatie hebt toegevoegd aan de context van de Cursor, maak het onbruikbaar.

   Navigeer naar **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Indexing & Docs]** en verwijder de vermelde documentatie.

### Stap 1: Geef de eerste prompt op

Vraag de AI-agent om met de implementatie te beginnen. Als u de agent vertelt om te stoppen en vragen te stellen, kunt u de implementatie vroeg sturen.

Ga de volgende herinnering in het de praatjevenster van de agent in:

```shell-session
I want to build an Adobe Commerce as a Cloud Service extension that allows shoppers to submit and view product review and question and answer (Q&A) content that displays on product detail pages (PDP).

## Product Reviews
The application has REST API endpoints that can be called by a storefront to retrieve and submit product reviews for a given SKU.

The GET endpoint accepts the following query parameters:
- sku (string, required): The SKU of the product to fetch reviews for
- limit (integer, optional): The maximum number of reviews to return (default: 10)
- offset (integer, optional): The number of reviews to skip for pagination (default: 0)

The POST endpoint accepts the following JSON body parameters:
- sku (string, required): The SKU of the product to submit a review for
- rating (integer, required): The rating for the product (1-5)
- review (string, optional): The text of the review
- user (string, optional): The name of the user submitting the review

The POST endpoint validates the input and returns appropriate error responses for invalid data. The reviews are stored and associated with the corresponding product SKU.

## Questions and Answers
The application has REST API endpoints that can be called by a storefront to retrieve and submit questions and answers for a given SKU.

The GET endpoint accepts the following query parameters:
- sku (string, required): The SKU of the product to fetch questions and answers for
- limit (integer, optional): The maximum number of questions and answers to return (default: 10)
- offset (integer, optional): The number of questions and answers to skip for pagination (default: 0)

The POST endpoint accepts the following JSON body parameters:
- sku (string, required): The SKU of the product to submit a question or answer for
- type (string, required): The type of submission ("question" or "answer")
- questionId (string, required if type is "answer"): The ID of the question being answered
- content (string, required): The text of the question or answer
- user (string, optional): The name of the user submitting the question or answer

The POST endpoint validates the input and returns appropriate error responses for invalid data. The questions and answers are stored and associated with the corresponding product SKU. Answers are also associated with the corresponding question.

Do not require Adobe IMS authentication for these endpoints. They will be called directly from the storefront.

STOP and ask me any clarifying questions you have about the requirements before you do any work.
```

>[!TIP]
>
>Door de agent aan STOP te vertellen en vragen te stellen voordat u verdergaat, kunt u de implementatie vroeg in het proces sturen. Dit zorgt ervoor dat belangrijke veronderstellingen en ontbrekende vereisten vroegtijdig worden geïdentificeerd en is vereist om de geleide workflow in deze zelfstudie te starten.

### Stap 2: Antwoord de vragen van de agent

De agent keert met een reeks vragen terug het moet antwoorden alvorens het kan beginnen een oplossing te vormen. In het volgende voorbeeld worden typische vragen en antwoorden getoond. Uw agent kan verschillende vragen stellen, maar de onderwerpen zijn over het algemeen het zelfde.

**de agentenvragen van het Voorbeeld:**

1. **REST API — gastheer en consumenten** — Zou CRUD REST API deel van deze App Builder app (Webacties op Adobe I/O Runtime) moeten uitmaken die de storefronts roepen? Wie zal het noemen (EDS Storefront, douane/hoofdloze winkel, of allebei)? Hebt u CORS, openbare (niet voor authentiek verklaarde) toegang nodig, of zullen de bezoekers API sleutels of OAuth gebruiken?
1. **model van Gegevens** - wat zou één &quot;overzicht&quot;of &quot;vraag&quot;vertegenwoordigen? Klantidentificatie (alleen e-mail of ook klant-id)? Product-id (alleen SKU of SKU + winkelweergave)? Kan de zelfde klant veelvoudige overzichten voor zelfde SKU voorleggen?
1. **persistentie** — is `aio-lib-state` de juiste plaats om revisies en Q&amp;A voort te zetten, of hebt u een externe opslag? Moet het ontwerp meerhuurder of enig-huurder veronderstellen?
1. **semantiek van de Paginering** - voor GET van Q&amp;A, is `limit` op vragen slechts (met genestelde antwoorden), of op het totale aantal vragen plus antwoorden van toepassing?

**antwoorden van het Voorbeeld:**

```shell-session
1. The REST API should be part of this App Builder app. It will be called by the EDS Storefront. No authentication — public access for both GET and POST.
2. For reviews: sku, rating (1-5), optional review text, optional user name. For Q&A: sku, type (question or answer), content, optional user. Answers linked to questions via questionId. Allow multiple reviews per SKU from the same user.
3. Use aio-lib-state. Single tenant for now.
4. Pagination by question — limit and offset apply to questions; each question includes its nested answers.
```

>[!NOTE]
>
>Uw agent kan verschillende vragen stellen. Gebruik deze antwoorden als hulpmiddel om de agent naar hetzelfde functionele resultaat te sturen: een openbare REST API met revisies en vragen en antwoorden, `aio-lib-state` persistentie en geen verificatie.

### Stap 3: Evaluatievereisten en architectuur

De agent produceert vereisten en architectuurdocumenten voor u aan overzicht. Controleer of de vereisten overeenkomen met de antwoorden die u hebt gegeven en of de architectuur van toepassing is op:

- Vier webhandelingen: `reviews-get`, `reviews-post`, `qa-get`, `qa-post`
- Permanente toepassing met `aio-lib-state` met toetsen die voldoen aan het toegestane patroon (`[a-zA-Z0-9-_.]` — geen dubbele punten)
- Statuswaarden die zijn opgeslagen als JSON-tekenreeksen (niet als onbewerkte objecten of arrays)
- Zelfstandig pakket — gedeelde code (utils, constanten) in het `product-reviews` -pakket, niet via `../../` -paden die uit de bundel ontsnappen

>[!NOTE]
>
>AI-agents zijn niet deterministisch en hun gedrag verschilt afhankelijk van het model en IDE. U kunt een verschillende reeks vragen krijgen die een verschillende reeks vereisten en architectuur produceren. Als zo, probeer om de agent in de richting te sturen zodat de implementatie dicht aanpast wat in dit leerprogramma alvorens te werk te gaan wordt voorgesteld.

### Stap 4: Selecteer een implementatieplan

De agent geeft u de optie om een gedetailleerd implementatieplan te creëren of een directe implementatie te voltooien.

- Als u een reviewable plan wilt dat u in fasen met meer controle kunt uitvoeren, selecteer de eerste optie.
- Als u wilt dat de agent de volledige implementatie uitvoert met minimale tussenkomst, selecteert u de tweede optie.

### Stap 5: De extensie implementeren

Nadat de agent de implementatie voltooit, stel de uitbreiding op:

```bash
aio app deploy
```

Als de agent `require-adobe-auth: true` aan de acties heeft toegevoegd, vraag het om authentificatie te verwijderen zodat de eindpunten direct van storefront kunnen worden geroepen:

```shell-session
Remove the requirement to provide a valid Adobe IMS access token from all product-reviews actions.
```

Vervolgens opnieuw implementeren:

```bash
aio app deploy
```

### Stap 6: modelgegevens maken en vooraf invullen voor testen

Maak een modelgegevensbestand en gebruik krullen om de API vooraf in te vullen, zodat u een voorbeeldrevisie en Q&amp;A-inhoud hebt voor tests in de CLI en de winkel.

1. Maak een bestand `docs/mock-product-reviews-data.json` (of vergelijkbaar) met voorbeeldgegevens. Bijvoorbeeld:

   ```json
   {
     "reviews": [
       { "sku": "ADB153", "rating": 5, "review": "Great product, highly recommend!", "user": "shopper@example.com" },
       { "sku": "ADB153", "rating": 4, "review": "Good value for money.", "user": "buyer@example.com" }
     ],
     "questions": [
       { "sku": "ADB153", "type": "question", "content": "Does this come in other colors?", "user": "curious@example.com" }
     ]
   }
   ```

1. Gebruik krullen om de gegevens naar uw geïmplementeerde API te verzenden.

   Vervang `<your-runtime-url>` door de werkelijke URL van de App Builder-runtime (bijvoorbeeld `https://1172492-prodreviewqa135-stage.adobeioruntime.net` ):

   ```bash
   API_URL="https://<your-runtime-url>/api/v1/web/product-reviews"
   
   # Submit reviews
   curl -s -X POST "$API_URL/reviews-post" \
     -H "Content-Type: application/json" \
     -d '{"sku":"ADB153","rating":5,"review":"Great product, highly recommend!","user":"shopper@example.com"}'
   
   curl -s -X POST "$API_URL/reviews-post" \
     -H "Content-Type: application/json" \
     -d '{"sku":"ADB153","rating":4,"review":"Good value for money.","user":"buyer@example.com"}'
   
   # Submit a question (save the returned id for the answer)
   curl -s -X POST "$API_URL/qa-post" \
     -H "Content-Type: application/json" \
     -d '{"sku":"ADB153","type":"question","content":"Does this come in other colors?","user":"curious@example.com"}'
   
   # Submit an answer (replace <QUESTION-UUID> with the id from the question response)
   curl -s -X POST "$API_URL/qa-post" \
     -H "Content-Type: application/json" \
     -d '{"sku":"ADB153","type":"answer","questionId":"<QUESTION-UUID>","content":"Yes, it comes in blue and red.","user":"seller@example.com"}'
   ```

1. Verifieer de gegevens met GET-verzoeken:

   ```bash
   curl -s "$API_URL/reviews-get?sku=ADB153"
   curl -s "$API_URL/qa-get?sku=ADB153"
   ```

>[!TIP]
>
>Gebruik SKU `ADB153` voor een product dat zowel revisie- als Vraag- en antwoordinhoud bevat, en `ADB152` voor een product zonder revisies. Deze gegevensconfiguratie laat het testen van zowel bevolkte als lege staten in de storefront toe.

### Stap 7: Test de extensie

Vraag de agent om teststappen te verstrekken, of de krullende voorbeelden van de voorafgaande stap te gebruiken. De volgende voorbeelden tonen typische testbevelen.

**leg een overzicht voor:**

```bash
API_URL="https://<your-runtime-url>/api/v1/web/product-reviews"
curl -s -X POST "$API_URL/reviews-post" \
  -H "Content-Type: application/json" \
  -d '{"sku":"ADB153","rating":5,"review":"Excellent!","user":"test@example.com"}'
```

**de revisies van de Lijst:**

```bash
curl -s "$API_URL/reviews-get?sku=ADB153"
```

**leg een vraag voor:**

```bash
curl -s -X POST "$API_URL/qa-post" \
  -H "Content-Type: application/json" \
  -d '{"sku":"ADB153","type":"question","content":"Is this dishwasher safe?","user":"test@example.com"}'
```

**leg een antwoord** voor (gebruik `id` van de vraagreactie als `questionId`):

```bash
curl -s -X POST "$API_URL/qa-post" \
  -H "Content-Type: application/json" \
  -d '{"sku":"ADB153","type":"answer","questionId":"<QUESTION-UUID>","content":"Yes, it is.","user":"support@example.com"}'
```

### Het servicecontract maken

Nu de de dienstimplementatie volledig is, vraag de agent om een de dienstcontract voor het storefront werk tot stand te brengen:

```shell-session
Create a service contract for the Product Review and Q&A application that defines the API endpoints, request and response formats, and any necessary data models. Ensure that the service contract is clear and detailed enough for a frontend developer to implement the storefront integration without needing to ask additional questions about the API. Name this file PRODUCT_REVIEW_QA_CONTRACT.md
```

Kopieer dit dossier in uw storefront project zodat kan de storefront agent het van verwijzingen voorzien.

## Verbinding maken met de winkel

Deze sectie begeleidt u door het storefront gedeelte van de productrevisies en de uitbreiding van vragen en antwoorden uit te voeren gebruikend [!DNL Edge Delivery Services] en AI-Hulp ontwikkelingshulpmiddelen. U voegt een productrevisieblok toe aan de PDP waarin zowel de revisie- als de vraag- en antwoordinhoud worden weergegeven en waarin kopers nieuwe inhoud kunnen verzenden.

>[!NOTE]
>
>De verstrekte herinneringen zijn beginpunten. Hoewel u hen zonder wijziging kunt gebruiken, denk na hebbend een natuurlijk gesprek met de agent.
>
>Als u werkt met ontwikkelprogramma&#39;s die zijn gebaseerd op AI, zijn er altijd natuurlijke variaties in de code en de reacties die door de agent worden gegenereerd.
>
>Als u om het even welke kwesties met uw code ontmoet, vraag de agent om u te helpen het zuiveren.

### Voorwaarden voor Storefront

Voordat u de storefront-integratie start, moet u controleren of u over het volgende beschikt:

- Een storefront-project dat is verbonden met uw [!DNL Commerce] -instantie
- Commerce storefront AI hulpmiddelen [&#x200B; geïnstalleerd gebruikend CLI &#x200B;](./tutorial-prerequisites.md#install-the-storefront-ai-tools)
- Het bestand `PRODUCT_REVIEW_QA_CONTRACT.md` dat naar het winkelproject is gekopieerd

### Stap 1: De omgeving valideren

Open het `config.json` -bestand en controleer of de waarden voor `commerce-core-endpoint` en `commerce-endpoint` naar het [!DNL Adobe Commerce as a Cloud Service] GraphQL-eindpunt verwijzen.

```json
"commerce-core-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
"commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
```

### Stap 2: Geef de eerste prompt op

Met het de dienstcontract reeds in uw project, vraag de agent om het blok van de productcontrole uit te voeren. Het gebruik **wijze van het Plan van 0&rbrace; als beschikbaar in uw agent, om de agent te verhinderen zonder een plan te werk te gaan.**

```shell-session
Analyze @PRODUCT_REVIEW_QA_CONTRACT.md and build a product review block using the API specified in the contract. The block displays both reviews and Q&A content on the product detail page, with forms for shoppers to submit reviews, questions, and answers. Use the project manager skill to plan this implementation.
```

>[!TIP]
>
>Specifiek het verzoeken om de vaardigheid van de projectmanager te gebruiken brengt het gefaseerde werkschema teweeg dat u de implementatie helpt sturen. Dit zorgt ervoor dat belangrijke veronderstellingen en ontbrekende vereisten vroeg in het proces worden geïdentificeerd.

### Stap 3: Antwoord ter verduidelijking van vragen

De agent keert met een reeks vragen terug het moet antwoorden alvorens het kan beginnen een oplossing te vormen. In het volgende voorbeeld worden typische vragen en antwoorden getoond. Uw agent kan verschillende vragen stellen, maar de onderwerpen zijn over het algemeen het zelfde.

**de agentenvragen van het Voorbeeld:**

1. **API basis URL** - hoe zou de opslag de product-overzichten API basis URL moeten krijgen? De opties kunnen een config blok (bijvoorbeeld, een lijst met `apiBaseUrl`), globale placeholders, of een andere benadering omvatten.
1. **bron SKU** — Moet het blok SKU van de context PDP (huidig product) of van blokconfiguratie lezen?
1. **gedrag van de Vorm** — Na een succesvolle voorlegging, zou de vorm moeten verbergen, een succesbericht tonen, of zichtbaar blijven maar gehandicapt?

**antwoorden van het Voorbeeld:**

```shell-session
1. Block table config with apiBaseUrl (required). Each block instance can point to its own deployment.
2. From block table if set; otherwise use getProductSku() so it works on PDP without authoring a SKU.
3. Show a success message above the form; keep the form visible but disabled.
```

>[!NOTE]
>
>Vervang de tijdelijke aanduiding in de blokconfiguratie door de werkelijke URL van de App Builder-runtime (bijvoorbeeld `https://1172492-prodreviewqa135-stage.adobeioruntime.net` ).
>
>Uw agent kan verschillende vragen stellen. Gebruik deze antwoorden als richtlijn:
>
>- De basis-URL van de API moet afkomstig zijn uit de bloktabel, zodat deze zonder codewijzigingen kan worden gewijzigd.
>- SKU van bloklijst als reeks; anders van het huidige product op PDP.
>- Nadat de verzending is voltooid, geeft u een succesbericht weer en schakelt u het formulier uit.

### Stap 4: Evaluatievereisten en architectuur

De agent werkt het document met vereisten voor u aan overzicht bij. Controleren of:

- In het blok worden revisies (met score, gebruiker, datum, tekst) en vragen en antwoorden (vragen met geneste antwoorden) weergegeven.
- Forms bestaat voor het verzenden van revisies, vragen en antwoorden.
- Paginering wordt ondersteund voor zowel revisie- als Vraag- en antwoordinhoud.
- De API-integratie gebruikt de basis-URL van de bloktabel.
- Succesvolle en foutstatussen worden verwerkt volgens het contract.

>[!NOTE]
>
>AI-agents zijn niet deterministisch en hun gedrag verschilt afhankelijk van het model en IDE. U kunt een verschillende reeks vragen krijgen die een verschillende reeks vereisten en architectuur produceren. Als zo, probeer om de agent in de richting te sturen zodat de implementatie dicht aanpast wat in dit leerprogramma alvorens te werk te gaan wordt voorgesteld.

### Stap 5: Selecteer een implementatieplan

De agent geeft u de optie om een gedetailleerd implementatieplan te creëren, of een directe implementatie te voltooien.

- Als u een reviewable plan wilt dat u in fasen met meer controle kunt uitvoeren, selecteer de eerste optie.
- Als u wilt dat de agent de volledige implementatie uitvoert met minimale tussenkomst, selecteert u de tweede optie.

Tijdens implementatie, leidt de agent tot en wijzigt blokdossiers. Bekijk de code die wordt gegenereerd en stel vragen of richt de agent zo nodig om. Als het blok niet teruggeeft, vraag de agent om de sectiedecoratie en het patroon van de blokontdekking te analyseren — het blokelement moet een direct kind van de sectie zijn zodat kan het kader het vinden.

### Stap 6: Voeg het blok aan de productpagina in Document Authoring toe

Voeg het blok van het productoverzicht aan het malplaatje van de productpagina toe zodat verschijnt het op alle PDPs. Gebruik de Document Authoring service (da.live) om het blok toe te voegen en te configureren.

1. Open uw document auteursdienst, bijvoorbeeld [&#x200B; da.live &#x200B;](https://da.live/)

1. Klik op uw projectruimte, open de **producten** omslag en selecteer **gebrek** (`products/default`).

1. Voeg een nieuwe bloksectie toe.

   In de bloklijst, voeg een rij met de bloknaam **product-overzicht** toe (of de bloknaam uw gemaakte agent).

1. Configureer het blok met de vereiste instellingen:
   - **apiBaseUrl** — Uw runtime URL van App Builder (bijvoorbeeld, `https://<namespace>-<app-name>-stage.adobeioruntime.net`).
   - **SKU** — Verlof leeg om SKU van het huidige product op PDP te gebruiken, of een specifieke SKU in te gaan om revisies voor slechts dat product te tonen.

1. Klik op **[!UICONTROL Publish]** om uw wijzigingen te publiceren.

### Stap 7: Start de server en test

Nadat u het blok aan de productpagina in Document Authoring hebt toegevoegd, start u de ontwikkelingsserver en test u het blok.

1. Start de lokale ontwikkelingsserver:

   ```bash
   npm run start
   ```

1. Navigeer in een browser naar een productpagina met vooraf ingevulde revisies en inhoud voor vragen en antwoorden. Bijvoorbeeld:

   ```shell-session
   http://localhost:3000/products/<product-slug>/ADB153
   ```

1. Controleer of in het productrevisieblok revisies en vraag- en antwoordinhoud worden weergegeven en of de verzendformulieren werken.

U kunt het manueel testen doen of de agent vragen om zijn browser mogelijkheden te gebruiken om voor u te testen:

```shell-session
Run complete browser testing. Use the following product page 'http://localhost:3000/products/<product-slug>/ADB153'
```

### Stap 8: Overbodig verwijderen

Nadat u overslaat of het volledige testen, zet de agent u ertoe aan om aan de definitieve **opschoning** fase te werk te gaan. Na bevestiging archiveert de agent alle tijdens de implementatie gemaakte documentatieartefacten.

## Problemen oplossen

Gebruik de volgende tips als u tijdens de zelfstudie problemen ondervindt.

### Backend (App Builder)

| Symptoom | Oorzaak | Repareren |
|---------|-------|-----|
| GET of POST retourneert 500 &quot;Kan module niet vinden&quot; | De acties voor productoverzichten gebruiken `require("../../utils")` of `require("../../constants")` , die de pakketbundel verlaten. Deze bestanden worden niet opgenomen wanneer het pakket wordt geïmplementeerd. | Maak het pakket voor productherzieningen op zichzelf. Voeg `actions/product-reviews/lib/constants.js` en `actions/product-reviews/lib/utils.js` toe en werk alle vier handelingen bij die u van `../lib/...` wilt vereisen in plaats van `../../` . |
| GET geeft 500 met &quot;key must match pattern&quot; | Statussleutels gebruiken dubbele punten (bijvoorbeeld `reviews:ADB153` ). `aio-lib-state` staat alleen `[a-zA-Z0-9-_.]` toe. | Wijzig voorvoegsels van `reviews:` en `qa:` in `reviews.` en `qa.` . Voeg een `stateKey(prefix, sku)` -hulplijn toe waarmee de SKU wordt ontsmet (vervang ongeldige tekens door `_` ). |
| POST retourneert 500 met &quot;value must be string&quot; | `aio-lib-state` accepteert alleen tekenreekswaarden. De code geeft arrays of objecten door aan `state.put()` . | Serienummering met `JSON.stringify()` bij schrijven en `JSON.parse()` bij lezen. Werk alle vier de handelingen bij. |

{style="table-layout:auto"}

### Storefront (Edge Delivery Services)

| Symptoom | Oorzaak | Repareren |
|---------|-------|-----|
| Blok wordt niet weergegeven op testpagina | Het blokelement is genest binnen een extra `div` , dus na `decorateSections` komt de blokkiezer (`div.section > div > div`) niet overeen. | Maak van het blok een direct onderliggend element van de sectie. Structuur: `section > div.product-review` (of een equivalente blokklasse). Vermijd `section > div > div.product-review` . |
| Ongeldige CSS-tokens | Het blok gebruikt ontwerptokens die niet voorkomen in `styles/styles.css` (bijvoorbeeld `--color-error-100` , `--type-detail-font-size` ). | Vraag de agent om tokens tegen de `styles/styles.css` van het project te bevestigen en ongeldige tokens te vervangen door bestaande (bijvoorbeeld, `--color-alert-*`, `--type-details-caption-*`). |

{style="table-layout:auto"}

## Zelfstudie

Hier volgt een overzicht van de onderwerpen die in deze zelfstudie worden behandeld:

- **de ontwikkeling van de Uitbreiding:** beschrijvend functionaliteit om productoverzicht en inhoud Q&amp;A op een storefront met een achtergrond van Adobe Commerce as a Cloud Service aan een AI agent tot stand te brengen en te bekijken en hoe te om deze functionaliteit uit te voeren door een werkende REST API met vier eindpunten te produceren gebruikend [!DNL App Builder].
- **Persistence:** Gebruikend `aio-lib-state` met correct zeer belangrijk formaat en JSON-Gerialiseerde waarden.
- **gegevens en pre-populatie van het Mock:** Creërend een mock gegevensbestand en gebruikend krullen om API voor CLI en storefront het testen pre-bevolken.
- **de contracten van de Dienst:** Creërend API contracten die achterste uitbreidingen en storefront implementaties overbruggen.
- **Geleidelijke storefront integratie:** Werkend door vereisten, architectuur, en implementatie gebruikend AI-bijgewoonde vaardigheden.
- **blok PDP:** Toevoegend een blok van de productrevisie aan PDP dat revisies en Q&amp;A met voorleggingsvormen en paginering toont.

## Volgende stappen

Gebruik de volgende suggesties om de service voor productreeksen uit te breiden:

- **voeg matiging toe:** voer een moderatiewerkschema voor overzicht en inhoud Q&amp;A uit alvorens het wordt gepubliceerd.
- **voegt authentificatie toe:** vereist dat de kopers worden aangemeld om overzichten of inhoud Q&amp;A voor te leggen, en associeer voorlegging met klantenrekeningen.
- **voeg een pagina van het abonnementenbeheer toe:** creeer een winkelpagina waar de kopers hun overzichten kunnen bekijken en uitgeven.
- **steun multi-huurdersplaatsingen:** breid het staatsbeheer uit om veelvoudige huurders van Commerce in één enkele app van App Builder te steunen.
- **voeg tarief het beperken toe:** voer grenzen op API uit om misbruik te verhinderen.
