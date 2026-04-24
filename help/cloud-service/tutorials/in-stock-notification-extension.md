---
title: Zelfstudie voor het aanmelden van bestanden
description: Leer hoe u een extensie voor meldingen in voorraad maakt voor Adobe Commerce as a Cloud Service met de ontwikkelingsprogramma's App Builder, Edge Delivery Services en AI.
solution: Commerce
feature: App Builder, Cloud
feature-set: Commerce
role: Developer
level: Intermediate
type: Tutorial
hide: true
hidefromtoc: true
source-git-commit: ba445bf33ec9334c853245fce125af12cd244367
workflow-type: tm+mt
source-wordcount: '2693'
ht-degree: 0%

---

# Zelfstudie voor het verlengen van meldingen in voorraad

Deze zelfstudie begeleidt u bij het maken van een extensie voor meldingen in voorraad voor [!DNL Adobe Commerce as a Cloud Service] gebruik van [!DNL Adobe App Builder] - en AI-ontwikkelingsprogramma&#39;s. Met de uitbreiding kunnen kopers zich abonneren op producten uit de voorraad en een melding ontvangen wanneer het product weer in voorraad is.

U bouwt twee delen:

- **uitbreiding van App Builder** — Een REST API voor het beheren van uit-van-voorraad abonnementen (creeer, lees, schrapping) met gebeurtenis-gedreven en geplande achterstandsopsporing.
- **integratie Storefront** — Een abonnementvorm op de pagina van het productdetail (PDP) die verschijnt slechts wanneer het geselecteerde product of de variant uit voorraad zijn.

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

Als om het even welke voorafgaande bevelen niet de verwachte resultaten terugkeren, verwijs naar de [&#x200B; eerste vereisten &#x200B;](./tutorial-prerequisites.md) voor begeleiding.

Controleer ook het volgende:

- U hebt een [!DNL Adobe Commerce as a Cloud Service] -instantie met productgegevens. Zie {de instanties van de Dienst van 0} Commerce Cloud [&#128279;](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview){target="_blank"}.
- Er is een storefront-project verbonden met uw [!DNL Commerce] -instantie. Als u geen hebt, volg de stappen in [&#x200B; creeer een storefront &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/){target="_blank"}.
- De `aem` CLI is geïnstalleerd:

  ```bash
  npm install -g @adobe/aem-cli
  ```

## Uitbreiding

In deze sectie vindt u instructies voor het ontwikkelen van een extensie voor meldingen in voorraad voor [!DNL Adobe Commerce as a Cloud Service] met behulp van ontwikkelingstools voor AI. De extensie biedt een REST API voor abonnementsbeheer en detecteert wanneer producten via Commerce-gebeurtenissen en een geplande controle weer in voorraad worden genomen.

1. Navigeer aan de montages MCP in uw coderende agent.

   Ga bijvoorbeeld in Cursor naar **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]** . Controleer of de gereedschapsset `commerce-extensibility` zonder fouten is ingeschakeld. Als er fouten optreden, schakelt u de gereedschapset in en uit.

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
Implement an Adobe Commerce as a Cloud Service extension to handle out-of-stock notifications for products.

The service should provide REST API endpoints for basic create, read, update, and delete (CRUD) operations on out-of-stock notifications, allowing storefronts to manage notifications for specific product SKUs.

Back-in-stock is detected by an inventory or product event or a scheduled action that checks Commerce API and then calls the REST API to send the notification.

STOP and ask me any clarifying questions you have about the requirements before you do any work.
```

>[!TIP]
>
>Door de agent aan STOP te roepen en vragen te stellen voordat u verdergaat, kunt u de implementatie vroeg in het proces sturen. Dit proces zorgt ervoor dat belangrijke veronderstellingen en ontbrekende vereisten vroegtijdig worden geïdentificeerd en is vereist om de geleide werkstroom in deze zelfstudie in werking te stellen.

### Stap 2: Antwoord de vragen van de agent

De agent keert met een reeks vragen terug het vereist alvorens het kan beginnen een oplossing te vormen. In het volgende voorbeeld worden typische vragen en antwoorden getoond. Uw agent kan verschillende vragen stellen, maar de onderwerpen zijn over het algemeen het zelfde.

**de agentenvragen van het Voorbeeld:**

1. **REST API — gastheer en consumenten** — Zou CRUD REST API deel van deze App Builder app (bijvoorbeeld, Webacties op Adobe I/O Runtime) moeten uitmaken die storefronts roepen? Wie zal het noemen (EDS Storefront, douane/hoofdloze winkel, of allebei)? Hebt u CORS, openbare (niet voor authentiek verklaarde) toegang nodig, of zullen de bezoekers API sleutels, OAuth, of de tokens van Commerce gebruiken?
1. **model van Gegevens** — Wat zou één &quot;bericht&quot;vertegenwoordigen? Klantidentificatie (alleen e-mail of ook klant-id)? Product-id (alleen SKU of SKU + winkelweergave)? Kan de zelfde klant aan zelfde SKU veelvoudige tijden intekenen, of zouden de abonnementen moeten worden gededupliceerd?
1. **achtergrond-in-voorraadopsporing — gebeurtenis vs gepland** — wilt u gebeurtenis-gedreven opsporing (op een inventaris/productgebeurtenis van Commerce), geplande opsporing (een geplande actie die periodiek voorraad controleert), of allebei? Wat zou &quot;het bericht&quot;betekenen (roep een externe webhaak, verzend e-mail, of registreer het)?
1. **Achter-in-voorraad - de bron van Commerce** - hebt u een aangewezen gebeurtenisnaam, of zou het ontwerp welk inventaris/voorraad-bijgewerkte gebeurtenis Commerce verstrekt moeten gebruiken? Voor geplande controles, welke API zou moeten worden gebruikt om voorraadstatus door SKU te krijgen?
1. **persistentie en multi-tenancy** — is `aio-lib-state` de juiste plaats om abonnementen voort te zetten, of hebt u een externe opslag? Moet het ontwerp meerhuurder of enig-huurder veronderstellen?
1. **CRUD semantiek en levenscyclus** — zou &quot;schrappen&quot;abonnement moeten annuleren? Hebt u &quot;update&quot; nodig? Moet het abonnement na verzending van een back-in-stock automatisch worden verwijderd of gemarkeerd als gemeld?
1. **Niet-functioneel** — Om het even welke tariefgrenzen of maximumabonnementen om af te dwingen? Zijn er nalevingsbehoeften (dubbele opt-in, markering van toestemming)?

**antwoorden van het Voorbeeld:**

```shell-session
1. The CRUD REST API should be part of thie App Builder app. It will be called by the EDS Storefront. For this implementation there is no need for API keys or security tokens.
2. For this initial implementation the customer identifier will be the email, product is identified by SKU, customer emails should not be able to subscribe to the same SKU multiple times.
3. Implement both. For now instead of sending the notification, log it so I can audit in the Adobe Developer Console.
4. Research and use what the best event to use that commerce already provides. Research the simplest way to get the stock status by SKU.
5. Use the aio-lib-state. Single tenant for now
6. Delete means cancel subscription. Skip Update, it does not apply for this service. After subscription is sent, it should be marked as notified or removed so it won't send again until the user subscribes again.
7. No limits. Implement minimal compliance requirements.
```

>[!NOTE]
>
>Uw agent kan verschillende vragen stellen. Gebruik deze antwoorden als hulpmiddel om de agent naar hetzelfde functionele resultaat te sturen: een REST API met e-mail- en SKU-abonnementen, gebeurtenisgestuurde en geplande back-in-stock detectie, `aio-lib-state` persistentie en loggebaseerde meldingen.

### Stap 3: Evaluatievereisten en architectuur

De agent produceert vereisten en architectuurdocumenten voor u aan overzicht. Controleer of de vereisten overeenkomen met de antwoorden die u hebt gegeven en of de architectuur van toepassing is op:

- Een REST API-actie voor een abonnement op CRUD (maken, lezen, bijwerken en verwijderen)
- Een gebeurtenisgestuurde back-in-stock-handler die wordt geactiveerd door Commerce-voorraadgebeurtenissen
- Een geplande actie voor het controleren van voorraden als fallback
- Persistentie met `aio-lib-state`

>[!NOTE]
>
>AI-agents zijn niet deterministisch en hun gedrag verschilt afhankelijk van het model en IDE. U kunt een verschillende reeks vragen krijgen die een verschillende reeks vereisten en architectuur produceren. Als zo, probeer om de agent in een richting te sturen zodat de implementatie dicht aanpast wat in dit leerprogramma alvorens te werk te gaan wordt voorgesteld.

### Stap 4: Selecteer een implementatieplan

De agent geeft u de optie om een gedetailleerd implementatieplan te creëren, of een directe implementatie te voltooien.

- Als u een reviewable plan wilt dat u in fasen met meer controle kunt uitvoeren, selecteer de eerste optie.
- Als u wilt dat de agent de volledige implementatie uitvoert met minimale tussenkomst, selecteert u de tweede optie.

### Stap 5: Distribueren, aan boord en abonneren op gebeurtenissen

Nadat de agent de implementatie heeft voltooid, bevat deze de volgende stappen om de app te implementeren, aan boord van de Commerce-instantie en zich te abonneren op gebeurtenissen met behulp van de volgende opdrachten:

1. De extensie implementeren:

   ```bash
   aio app deploy
   ```

1. Voer het instapkaartscript uit om de gebeurtenisprovider te registreren bij Commerce:

   ```bash
   npm run onboard
   ```

1. Abonneren op Commerce-gebeurtenissen:

   ```bash
   npm run commerce-event-subscribe
   ```

1. Valideer het gebeurtenisabonnement.

   Ga naar uw Commerce-instantie en open **[!UICONTROL System]** > **[!UICONTROL Event Subscriptions]** .

   Er moet een gebeurtenisoverzicht worden weergegeven.

   ![&#x200B; Commerce Admin menu die de sectie van het Abonnement van de Gebeurtenis benadrukken &#x200B;](../assets/in-stock-event-subscriptions.png){width="600" zoomable="yes"}

   ![&#x200B; de abonnementlijst van de Gebeurtenis met geregistreerde gebeurtenisingangen &#x200B;](../assets/in-stock-event-table.png){width="600" zoomable="yes"}

### Stap 6: Test de extensie

Vraag de agent om teststappen te verstrekken. Aangezien dit een API-service is, kunt u opdrachtregelinstructies aanvragen:

```shell-session
Give me step by step instructions to test the API service from the command line.
```

Volg de stappen de agent verstrekt. De volgende voorbeelden tonen typische testbevelen.

**abonneert aan een SKU:**

```bash
API_URL="https://<your-runtime-url>/api/v1/web/notify-out-of-stock/api"; curl -X POST "$API_URL" \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","sku":"ADB153"}'
```

De reactie ziet er ongeveer als volgt uit:

```json
{
  "createdAt": "2026-03-06T22:11:00.308Z",
  "email": "test@example.com",
  "id": "b3353bf5-1007-4b10-989d-430892dd4a66",
  "sku": "ADB153"
}
```

**maak een lijst van alle abonnementen:**

```bash
curl -X GET "$API_URL"
```

De reactie retourneert een lijst met alle actieve abonnementen:

```json
{
  "subscriptions": [
    {
      "createdAt": "2026-03-06T22:11:00.308Z",
      "email": "test@example.com",
      "id": "b3353bf5-1007-4b10-989d-430892dd4a66",
      "sku": "ADB153"
    }
  ]
}
```

**Test de rug-in-voorraad stroom:**

1. Bewerk een product waarvoor u een abonnement hebt gemaakt vanuit uw Commerce-exemplaar.
1. Stel de status van de productvoorraad in op **[!UICONTROL Out of Stock]** .
1. Wacht ongeveer één minuut en schakel de voorraadstatus terug naar **[!UICONTROL In Stock]**.

   ![&#x200B; Commerce Admin product geeft pagina uit die de drop-down van de Status van de Voorraad met In Voorraad en uit de opties van de Voorraad &#x200B;](../assets/in-stock-product-stock-status-toggle.png){width="600" zoomable="yes"} toont

1. Wacht ongeveer vijf minuten totdat de gebeurtenis wordt geactiveerd en naar de service wordt verzonden.

1. Navigeer in [!DNL Adobe Developer Console] naar de sectie App Builder-logbestanden.

   ![&#x200B; Adobe Developer Console App Builder logboeken sectie &#x200B;](../assets/in-stock-developer-console-logs.png){width="600" zoomable="yes"}

1. Controleer in de logboeken of er items zijn die bevestigen dat de gebeurtenis is verwerkt en dat het juiste e-mail-SKU-abonnementspaar is geïdentificeerd.

   ![&#x200B; het logboekingangen van App Builder die file-in-voorraad gebeurtenisverwerking &#x200B;](../assets/in-stock-log-entries.png){width="600" zoomable="yes"} tonen

>[!TIP]
>
>U kunt de agent vragen wat in de logboeken te zoeken om de berichtactie te verifiëren met succes werd geregistreerd. U kunt de logboekingangen ook kopiëren en kleven om de agent te hebben de controle doen.

Na de back-in-stock-gebeurtenisprocessen moet het aanvragen van de lijst met abonnementen één keer minder worden geretourneerd, omdat het gemelde abonnement wordt verwijderd.

### Het servicecontract maken

Nu de de dienstimplementatie volledig is, vraag de agent om een de dienstcontract voor het storefront werk tot stand te brengen:

```shell-session
Create an API service contract for the Out of Stock notification service and its endpoints. Ensure that the service contract is clear and detailed enough for a frontend developer to implement the storefront UI integration without needing to ask additional questions about the API. Name this file OUT_OF_STOCK_NOTIFICATION_CONTRACT.md
```

Kopieer dit dossier in uw storefront project zodat kan de storefront agent het van verwijzingen voorzien.

## Verbinding maken met de winkel

Deze sectie begeleidt u door het storefront gedeelte van de uitbreiding van het bericht in voorraad uit te voeren gebruikend [!DNL Edge Delivery Services] en de hulp van AI ontwikkelingshulpmiddelen. U voegt een abonnementsformulier toe aan de pagina met productdetails (PDP) die alleen wordt weergegeven wanneer het geselecteerde product of de geselecteerde variant uit voorraad is.

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
- Het bestand `OUT_OF_STOCK_NOTIFICATION_CONTRACT.md` dat naar het winkelproject is gekopieerd

### Stap 1: De omgeving valideren

Open het `config.json` -bestand en controleer of de waarden voor `commerce-core-endpoint` en `commerce-endpoint` naar het [!DNL Adobe Commerce as a Cloud Service] GraphQL-eindpunt verwijzen.

```json
"commerce-core-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
"commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
```

### Stap 2: Geef de eerste prompt op

Met het de dienstcontract reeds in uw project, vraag de agent om UI in de pagina van productdetails tot stand te brengen. Het gebruik **wijze van het Plan van 0&rbrace; als beschikbaar in uw agent, om de agent te verhinderen zonder een plan te werk te gaan.**

```shell-session
Analyze @OUT_OF_STOCK_NOTIFICATION_CONTRACT.md. Add a form for subscribing to a notification for when a product is back in stock. Place this form on the product details page, underneath the add to cart and wishlist button. The form only displays when a product is out of stock. 

Use the project manager skill to plan this implementation.
```

>[!TIP]
>
>Specifiek het verzoeken om de vaardigheid van de projectmanager te gebruiken brengt het gefaseerde werkschema teweeg dat u de implementatie vroeg in het proces helpt sturen. Dit proces zorgt ervoor dat de belangrijkste veronderstellingen en de ontbrekende vereisten vroegtijdig worden geïdentificeerd en de agent de kans geeft om u van details en vereisten te voorzien u niet zou kunnen denken om in de originele herinnering te voorzien.

### Stap 3: Beantwoord planningsvragen

De agent keert met een reeks vragen terug het moet antwoorden alvorens het kan beginnen een oplossing te vormen. In het volgende voorbeeld worden typische vragen en antwoorden getoond. Uw agent kan verschillende vragen stellen, maar de onderwerpen zijn over het algemeen het zelfde.

**de agentenvragen van het Voorbeeld:**

1. **API basis URL** - hoe zou de opslag de notify-out-of-stock API basis URL moeten krijgen? De opties kunnen een config blok (bijvoorbeeld, een lijst met `out-of-stock-api-base-url`), globale placeholders of milieuvariabelen, of een andere benadering omvatten.
1. **Exemplaar** — Moet de implementatie placeholders voor succes en foutenmeldingen (bijvoorbeeld, voor localisatie) gebruiken, of statische Engelstalig voor deze implementatie gebruiken?
1. **Na succesvol onderteken** — Zou de vorm moeten verbergen en tonen slechts &quot;u wordt ingetekend&quot;(A), de vorm zichtbaar houden maar met een succesbericht boven het (B), of een ander gedrag (C) onbruikbaar maken?
1. **Configurable producten** — Zou het vormzicht op de geselecteerde waarde van de variant `inStock` moeten worden gebaseerd, zodat toont de vorm wanneer de gekozen variant uit voorraad is?

**antwoorden van het Voorbeeld:**

```shell-session
1. Global placeholder with baseurl value of `https://<your-runtime-url>/api/v1/web/notify-out-of-stock/api`
2. Use placeholders with static English fallback
3. B
4. Use selected variant's inStock value
```

>[!NOTE]
>
>Vervang `<your-runtime-url>` door de werkelijke [!DNL Adobe I/O Runtime] URL van uw App Builder-implementatie.
>
>Uw agent kan verschillende vragen stellen. Gebruik deze antwoorden als richtlijn:
>
>- Gebruik een algemene tijdelijke aanduiding voor de basis-URL van de API, zodat deze zonder codewijzigingen kan worden gewijzigd.
>- Gebruik plaatsaanduidingen voor naar de gebruiker gerichte kopieën met statisch Engels als fallback.
>- Na een succesvol abonnement moet u het formulier zichtbaar houden, maar uitschakelen met een succesbericht erboven.
>- Voor configureerbare producten gebruikt u de waarde `inStock` van de geselecteerde variant om de zichtbaarheid van het formulier te regelen.

### Stap 4: Evaluatievereisten en architectuur

De agent werkt het document met vereisten voor u aan overzicht bij. Controleren of:

- Het formulier wordt alleen weergegeven wanneer het product of de geselecteerde variant uit voorraad is.
- Het formulier wordt onder de knoppen Toevoegen aan winkelwagentje en Vraaglijst op de PDP geplaatst.
- De API-integratie gebruikt de basis-URL van een algemene plaatsaanduiding.
- Succesvolle en foutenstatussen worden afgehandeld volgens het contract (201, 409, 400, 503/500).

>[!NOTE]
>
>AI-agents zijn niet deterministisch en hun gedrag verschilt afhankelijk van het model en IDE. U kunt een verschillende reeks vragen krijgen die een verschillende reeks vereisten en architectuur produceren. Als zo, probeer om de agent in een richting te sturen zodat de implementatie dicht aanpast wat in dit leerprogramma alvorens te werk te gaan wordt voorgesteld.

Tijdens **Fase 2 (de Planning van de Architectuur)**, onderzoekt de agent documentatie en uw codebase alvorens een architectuur voor te stellen. Verwacht dat de agent:

- Zoek in [!DNL Commerce] documentatie naar PDP drop-in containers, groeven, en gebeurtenislading.
- Scan de map `blocks` en de map `scripts/initializers/` naar bestaande PDP-gerelateerde code.
- Verken de definities van TypeScript voor beschikbare containers en groefcontextvormen.

De agent stelt dan architectuuropties voor. Herzie het plan en geef de agent op te werk te gaan.

### Stap 5: Selecteer een implementatieplan

De agent geeft u de optie om een gedetailleerd implementatieplan te creëren, of een directe implementatie te voltooien.

- Als u een reviewable plan wilt dat u in fasen met meer controle kunt uitvoeren, selecteer de eerste optie.
- Als u wilt dat de agent de volledige implementatie uitvoert met minimale tussenkomst, selecteert u de tweede optie.

Tijdens **Fase 4 (Implementatie)**, produceert de agent code die op de gekozen architectuur wordt gebaseerd. Afhankelijk van de benadering, gebruikt de agent verscheidene gespecialiseerde vaardigheden:

- **het modelleren van de Inhoud:** als een nieuw blok nodig is, ontwerpt de agent een auteursvriendelijke inhoudsstructuur.
- **de ontwikkeling van het Blok:** de agent leidt tot blokdossiers na [!DNL Edge Delivery Services] overeenkomsten, met inbegrip van de versiefuncties van JavaScript, scoped CSS stijlen, de etiketten van ARIA voor toegankelijkheid, en lading en fout staat behandeling.
- **drop-in aanpassing:** als de architectuur groefaanpassing gebruikt, voert de agent de correcte container in, gebruikt een geverifieerde groef dichtbij de producttitel, en abonneert aan de gebeurtenissen van productgegevens voor huidige SKU.

Bekijk de code die wordt gegenereerd en stel vragen of richt de agent zo nodig om.

### Stap 6: Start de server en test

Nadat de agent de implementatie voltooit, begin de ontwikkelingsserver en test de vorm.

1. Start de lokale ontwikkelingsserver:

   ```bash
   npm run start
   ```

1. Navigeer in een browser naar een productpagina die buiten de voorraad valt. Bijvoorbeeld:

   ```shell-session
   http://localhost:3000/products/<out-of-stock-product-slug>/<sku>
   ```

1. Controleer of het abonnementsformulier wordt weergegeven onder de knoppen Toevoegen aan winkelwagentje en Vraaglijst.

U kunt het manueel testen doen of de agent vragen om zijn browser mogelijkheden te gebruiken om voor u te testen:

```shell-session
Run complete browser testing. Use the following out of stock product 'http://localhost:3000/products/<out-of-stock-product-slug>/<sku>'
```

![&#x200B; de detailpagina die van het Product de rug-in-voorraad meldingsvorm tonen onder toevoegt aan de knoop van het karretje &#x200B;](../assets/in-stock-notification-form.png){width="600" zoomable="yes"}

### Stap 7: Overbodig verwijderen

Nadat u overslaat of het volledige testen, zet de agent u ertoe aan om aan de definitieve **opschoning** fase te werk te gaan. Na bevestiging archiveert de agent alle tijdens de implementatie gemaakte documentatieartefacten.

## Problemen oplossen

Gebruik de volgende tips als u tijdens de zelfstudie problemen ondervindt:

- **API fouten:** gebruik CLI om verzoeken naar API rechtstreeks te verzenden om gedrag te verifiëren. Gebruik bijvoorbeeld `curl` om elk eindpunt onafhankelijk te testen.
- **de fouten van de Agent:** Exemplaar en deeg foutenmeldingen aan een zitting van het agentenpraatje om u te helpen kwesties zuiveren. De agent kan gemeenschappelijke problemen zoals het missen van omgevingsvariabelen of misconfigured acties diagnostiseren.
- **de pijpleiding van de Gebeurtenis:** als de achtergrond-in-voorraad gebeurtenissen niet teweegbrengen, verifieer dat u de onboarding en de stappen van het gebeurtenisabonnement hebt voltooid. Controleer of `workspace.json` zich op de juiste locatie bevindt en of de module Commerce Events is ingeschakeld.
- **de statuslading van het Beeld:** Commerce kan `is_in_stock` als koord (`"1"`) in plaats van Boolean (`true`) verzenden. Als de back-in-stock handler niet activeert, vraagt u de agent om de consumentencode op strikte typevergelijkingen te controleren en deze bij te werken om beide indelingen af te handelen.

## Zelfstudie

Hier volgt een overzicht van de onderwerpen die in deze zelfstudie worden behandeld:

- **de ontwikkeling van de Uitbreiding:** beschrijvend nieuwe functionaliteit aan een agent AI en producerend een werkende REST API met verrichtingen CRUD gebruikend [!DNL App Builder].
- **gebeurtenis-gedreven architectuur:** Vormend de gebeurtenissen van Commerce en een geplande actie om te ontdekken wanneer de producten terug in voorraad komen.
- **Lokale het testen en plaatsing:** het testen van API met `curl` en het opstellen die [!DNL Adobe I/O CLI] gebruiken.
- **de contracten van de Dienst:** Creërend API contracten die achterste uitbreidingen en storefront implementaties overbruggen.
- **Geleidelijke storefront integratie:** Werkend door vereisten, architectuur, en implementatie gebruikend AI-bijgewoonde vaardigheden.
- **drop-in integratie:** Toevoegend een abonnementvorm aan PDP gebruikend [!DNL Adobe Commerce] drop-in containers en groeven.

## Volgende stappen

Gebruik de volgende suggesties om uw service voor meldingen in voorraad uit te breiden:

- **verzend echte berichten:** vervang het op logboek-gebaseerde bericht met de e-maildienst zoals [!DNL Adobe Campaign] of een derdeleverancier.
- **voeg een pagina van het abonnementsbeheer toe:** creeer een storefront pagina waar de kopers hun actieve abonnementen kunnen bekijken en annuleren.
- **steun multi-huurdersplaatsingen:** breid het staatsbeheer uit om veelvoudige huurders van Commerce in één enkele app van App Builder te steunen.
- **voegt tarief het beperken toe:** voer grenzen op abonnement API uit om misbruik te verhinderen.
