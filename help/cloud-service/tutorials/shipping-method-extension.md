---
title: Zelfstudie over het verlengen van verzendmethoden
description: Leer hoe u een configureerbare uitbreiding van de verzendmethode voor Adobe Commerce as a Cloud Service maakt met App Builder, de startkit voor het uitchecken en de ontwikkelingstools voor AI.
feature: App Builder, Cloud
role: Developer
level: Intermediate
source-git-commit: e55bc4db196d3d973b981bb2484be950dcd6b7c3
workflow-type: tm+mt
source-wordcount: '1849'
ht-degree: 0%

---

# Zelfstudie over het verlengen van verzendmethoden

Deze zelfstudie begeleidt u door het bouwen van een het verschepen methodeuitbreiding voor [!DNL Adobe Commerce as a Cloud Service] gebruikend [!DNL Adobe App Builder], de [&#x200B; uitcheckstarter uitrusting &#x200B;](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/){target="_blank"}, en AI-bijgewoonde ontwikkelingshulpmiddelen.

De extensie voegt een configureerbare verzendmethode toe aan de kassa waar de tarieven afkomstig zijn van een externe service voor de verzending van mock-verzendkosten. De handelaren vormen de dienst URL, de API sleutel, en het pakhuis (schip-van) adres in Admin UI, en bij controle de tarieven van uitbreidingsverzoeken van die dienst en toont de teruggekeerde opties aan de klant.

Alvorens u begint, voltooi de [&#x200B; eerste vereisten &#x200B;](./tutorial-prerequisites.md).

## Voorwaarden verifiëren {#tutorial-verify-prerequisites}

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

## De mock Shipping Rate API maken

Na de voltooiing van de [&#x200B; eerste vereisten &#x200B;](./tutorial-prerequisites.md), creeer de model verschepende tarieven API, zodat hebt u de dienst URL en API sleutel klaar wanneer u de uitbreiding in [!DNL Commerce Admin] vormt. De extensie roept een externe API voor verzendkosten aan. Voor deze zelfstudie gebruikt u een mock-API waarmee u de flow kunt uitvoeren zonder een echte carrier-account. U zult modelAPI creëren gebruikend [&#x200B; Pijptemam &#x200B;](https://pipedream.com) (vrije vereiste rekening). De mock-API gebruikt een aanvraag-/antwoordcontract dat vergelijkbaar is met de gewone API&#39;s voor werkelijke verzendkosten. Het is dus raadzaam deze extensie later aan te sluiten op een echte provider.

Om de mock API te creëren, download het [&#x200B; mock rates API specificatiedossier &#x200B;](../assets/mock-rates-api-spec.zip), open het, en voeg het `.md` dossier aan uw project (bijvoorbeeld `docs/mock-rates-api-spec.md`) toe.

**Tijd:** het zou ongeveer **5-10 minuten** moeten vergen om mock API tot stand te brengen.

### Een workflow en HTTP-trigger maken

1. Ga naar [&#x200B; pipedream.com &#x200B;](https://pipedream.com) en teken omhoog of login.
1. Klik **Nieuw werkschema** (of **voeg werkschema** toe).
1. Voor de trekker, uitgezochte **HTTP / Webhaak**.
1. In de trekkerconfiguratie, plaats **de Reactie van HTTP** aan **keert een douanerespons van uw werkschema** terug. Dit staat de stap van de Code toe om de mockJSON reactie te verzenden.
1. Pipedream toont een uniek **eindpunt URL van HTTP**, zoals `https://123456.m.pipedream.net`.
1. **Exemplaar dit URL** en gebruik het als **Dienst URL** wanneer het vormen van de uitbreiding in Commerce Admin.

   ![&#x200B; Pipedream werkschema met HTTP/Webhaak trekker en eindpuntURL zichtbaar &#x200B;](../assets/mock-api-trigger.png){width="600" zoomable="yes"}

U te hoeven niet om **Vergunning** op de trekker te vormen; het model API bevestigt de `API-Key` kopbal in de stap van de Code.

### De stap Code toevoegen

1. Klik op het pictogram **+** om een stap toe te voegen.
1. Kies **de code van Node.js van de Looppas** (stap van de Code).
1. **vervangt** de standaardcode met volgende JavaScript.

   ```javascript
   export default defineComponent({
   async run({ steps, $ }) {
      const event = steps.trigger.event;
      const body = event.body ?? {};
      const headers = event.headers ?? {};
      const apiKey = headers["api-key"] ?? body.api_key ?? "";
   
      if (!apiKey || String(apiKey).trim() === "") {
         await $.respond({
         immediate: true,
         status: 401,
         headers: { "Content-Type": "application/json" },
         body: { error: "Missing or invalid API-Key header" },
         });
         return;
      }
   
      const shipment = body.shipment;
      if (!shipment || typeof shipment !== "object") {
         await $.respond({
         immediate: true,
         status: 400,
         headers: { "Content-Type": "application/json" },
         body: { error: "Missing or invalid shipment" },
         });
         return;
      }
   
      const rates = [
         {
         service_code: "mock_standard",
         service_name: "Mock Standard",
         carrier_friendly_name: "Mock Carrier",
         shipping_amount: { amount: 5.99 },
         shipment_cost: 5.99,
         cost: 5.99,
         },
         {
         service_code: "mock_express",
         service_name: "Mock Express",
         carrier_friendly_name: "Mock Carrier",
         shipping_amount: { amount: 12.99 },
         shipment_cost: 12.99,
         cost: 12.99,
         },
      ];
   
      await $.respond({
         immediate: true,
         status: 200,
         headers: { "Content-Type": "application/json" },
         body: { rates },
      });
   },
   });
   ```

1. Klik **opstellen**.

   ![&#x200B; de stap van de Code van de Pijpleiding met mock het manuscript van verschepende tarieven &#x200B;](../assets/mock-api-code-step.png){width="600" zoomable="yes"}

De mock retourneert twee tariefopties (Mock Standard en Mock Express) voor elke geldige aanvraag die een niet-lege `API-Key` header en een `shipment` -object bevat. U configureert de API-sleutel later in de [!DNL Commerce Admin] -zelfstudie. U zult ook het het werkschema URL van de Pijpnaam op het zelfde configuratiescherm specificeren, zo nota van het.

## Uitbreiding

Deze sectie begeleidt u door het ontwikkelen van een het verschepen methodeuitbreiding voor [!DNL Adobe Commerce as a Cloud Service] gebruikend de [&#x200B; uitcheckstarter kit &#x200B;](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/){target="_blank"} en AI-bijgewoonde ontwikkelingshulpmiddelen.

1. Navigeer aan de montages MCP in uw coderende agent. Ga bijvoorbeeld in Cursor naar **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]** . Controleer of de gereedschapsset `commerce-extensibility` zonder fouten is ingeschakeld. Als er fouten optreden, schakelt u de gereedschapset in en uit.

   ![&#x200B; de montages van winde van de Curseur die MCP handel-rekbaarheid toegelaten toolset tonen &#x200B;](../assets/cursor-settings-shipping.png){width="600" zoomable="yes"}

   >[!NOTE]
   >
   >Als u werkt met ontwikkelprogramma&#39;s voor AI, verwacht u natuurlijke variaties in de code en reacties die door de agent worden gegenereerd.
   >
   >Als u om het even welke kwesties met uw code ontmoet, kunt u altijd de agent vragen om u te helpen het zuiveren.

1. Als u documentatie hebt toegevoegd aan de context van de Cursor, maak het onbruikbaar. Navigeer aan [!UICONTROL **Curseur**] > [!UICONTROL **Montages**] > [!UICONTROL **de Montages van de Curseur**] > [!UICONTROL **Indexeren &amp; Dokken**] en schrap om het even welke vermelde documentatie.

   ![&#x200B; Curseur het indexeren en docs montages met lege documentatielijst &#x200B;](../assets/disable-documentation.png){width="600" zoomable="yes"}

1. Geef de agent toegang tot de mock rates API specificatie, zodat kan het de cliënt correct uitvoeren. Als u dit nog niet hebt gedaan, download het [&#x200B; mock rates API specificatiedossier &#x200B;](../assets/mock-rates-api-spec.zip), open het, en voeg het `.md` dossier aan uw project (bijvoorbeeld `docs/mock-rates-api-spec.md`) toe, dan verwijzing dat dossier in uw herinnering.

1. De extensie van de verzendmethode genereren:

   - Van het het praatjevenster van de agent, uitgezochte **wijze van het Plan**, als beschikbaar. Dit verhindert de agent zonder een plan te werk te gaan.
   - Voer de volgende vraag in:

   ```shell-session
   Build an Adobe Commerce extension that adds a shipping method at checkout. The rates come from an external mock shipping rates service: the merchant configures the service's URL and API key in Admin, and at checkout the extension asks that service for rates and shows the returned options to the customer.
   
   External service (mock shipping rates API):
   - The service endpoint URL is configurable by the merchant (for example https://123456.m.pipedream.net).
   - The API is specified in ./docs/mock-rates-api-spec.md.
   
   The merchant must be able to configure the following in the Adobe Commerce Admin UI. Use the Adobe Commerce Admin UI SDK (or equivalent App Builder extensibility options for the Admin) to add a configuration screen where the merchant can set:
   - The service URL (where the extension sends rate requests).
   - An API key the service expects (any non-empty value for the mock). The API key is sensitive data: it must be stored securely and must never appear in logs, error messages, or in the UI in full (e.g. mask in the UI).
   - The warehouse (ship-from) address: name, phone, street, city, state, postal code, country. This is the origin used when requesting rates.
   ```

   >[!NOTE]
   >
   >Als de agent om de documentatie verzoekt te zoeken, sta het toe.

   ![&#x200B; het praatjevenster van de Curseur op de wijze van de Agent met het verschepen van uitbreidingsherinnering ingegaan &#x200B;](../assets/enter-prompt-shipping.png){width="600" zoomable="yes"}

1. Beantwoord de vragen van de agent precies om het te helpen de beste code produceren. Als de agent vraagt welke uitrusting of malplaatje te gebruiken, het aan de [&#x200B; kassa van de controleaanzet &#x200B;](https://developer.adobe.com/commerce/extensibility/starter-kit/checkout/){target="_blank"} met het verschepen domein en Admin UI de uitbreiding van SDK zodat zowel de verschepende webhaak als het koopvaardijconfiguratiescherm worden uitgevoerd.

   De agent kan een `requirements.md` (of gelijkwaardig) dossier tot stand brengen dat als bron van waarheid voor de implementatie dient.

1. Controleer het bestand `requirements.md` (of equivalent) en controleer het abonnement. Als alles correct kijkt, instrueer de agent om zich aan architectuur planning (of **Fase 2**) te bewegen. Bevestig dat:

   - A **verschepen-methodes** actie (of gelijkwaardig) behandelt de webhaak van Commerce en roept externe tarief API.
   - A **verschepen-config** (of gelijkwaardig) actie steunt GET (gelezen config, API zeer gemaskeerde sleutel) en SET (sparen dienst URL, API sleutel, pakhuisadres), met veilig opgeslagen config, bijvoorbeeld in Runtime staat.
   - Admin UI omvat a **Mock die** (of gelijkaardig) lusje met gebieden voor de Dienst URL, API sleutel (wachtwoord/gemaskeerd), en pakhuisadres verscheept.

   ![&#x200B; dossier van Vereisten dat door AI agent met de details van de het verschepen implementatie van de extensie wordt gecreeerd &#x200B;](../assets/requirements-file-shipping.png){width="600" zoomable="yes"}

1. Herzie het architectuurplan wanneer de agent het verstrekt.

   ![&#x200B; AI plan van de agentenimplementatie voor de uitbreiding van de Tarieven van het Mock Verschepende &#x200B;](../assets/implementation-plan-shipping.png){width="600" zoomable="yes"}

1. Geef de agent de opdracht om door te gaan met het genereren van code. De agent zou a **mock** drager aan de het verschepen dragers configuratie moeten toevoegen die Commerce toestaat om de teruggekeerde methodes goed te keuren, en de webhaakmethode `plugin.magento.out_of_process_shipping_methods.api.shipping_rate_repository.get_rates` te gebruiken (webhaaktype **na**, vereiste **Facultatief**).

   De agent genereert de vereiste code en geeft een gedetailleerd overzicht van uw volgende stappen (waaronder het installeren van afhankelijkheden, het registreren van de mock-carrier, het configureren van de Commerce-webhaak en het implementeren).

   ![&#x200B; Samenvatting van geproduceerde code en implementatie voor het verschepen uitbreiding &#x200B;](../assets/code-generation-summary-shipping.png){width="600" zoomable="yes"}

   ![&#x200B; AI agent volgende stappen voor het installeren van, het vormen webhaak, en het opstellen van de verschepende uitbreiding &#x200B;](../assets/next-steps-shipping.png){width="600" zoomable="yes"}

### Opschonen voor implementatie

Verwijder voor het implementeren de code die de toepassing niet nodig heeft. De startkit voor uitchecken kan ongebruikte domeinen (zoals betaling, belasting of gebeurtenissen) en basisstructuur bevatten. Laat de agent de items verwijderen en zorg dat alleen de verzendingen en [!DNL Admin UI] -onderdelen behouden blijven door een melding als:

```shell-session
Proceed with Phase 5 cleanup.
```

De agent produceert een opschoonrapport, verwijdert ongebruikte acties, config, en manuscripten, en werkt het project bij. Voltooi deze stap voordat u deze implementeert.

![&#x200B; AI agentenfase 5 schoonmaakrapport dat verwijderde en gehouden componenten &#x200B;](../assets/cleanup-report-shipping.png){width="600" zoomable="yes"} toont

### De extensie implementeren

1. Na het verifiëren van de geproduceerde code, stel de uitbreiding op gebruikend de volgende herinnering:

   ```shell-session
   Deploy the app.
   ```

   De agent voert een pre-implementatiebeoordeling van gereedheid uit (bijvoorbeeld het controleren van `.env` op `COMMERCE_WEBHOOKS_PUBLIC_KEY` , `COMMERCE_BASE_URL` en OAuth/IMS-variabelen als de Admin UI of Commerce API wordt gebruikt).

   ![&#x200B; AI agent pre-plaatsingsbereidheid en plaatsingsstappen voor de Verzenduitbreiding van het Mock &#x200B;](../assets/pre-deployment-assessment-shipping.png){width="600" zoomable="yes"}

1. Wanneer u met de beoordelingsresultaten vertrouwd bent, instrueer de agent om met plaatsing te werk te gaan. De agent gebruikt toolkit MCP om, automatisch te verifiëren en op te stellen.

   ![&#x200B; MCP toolkit plaatsingsoutput met opgestelde pakketten en webhaak URL voor het verschepen van uitbreiding &#x200B;](../assets/deployment-process-shipping.png){width="600" zoomable="yes"}

### Post-implementatie

Na plaatsing, voltooi de volgende stappen om de mock drager te registreren, webhaak en [!DNL Admin UI] te vormen, en de uitbreiding bij checkout te verifiëren.

1. **Register de mock drager in Commerce** (stel eens in werking na stel op):

   ```bash
   npm run create-shipping-carriers
   ```

   Zorg ervoor dat uw `.env` `COMMERCE_BASE_URL` en een geldige OAuth/IMS-referenties heeft, zodat het script de carrier kan registreren.

1. **vorm de verschepende webhaak in [!DNL Commerce Admin]:**

   - Ga naar **Opslag** > Montages > **Configuratie** > **de Diensten van Adobe** > **Webhooks van Commerce**.
   - Een webhaak toevoegen:
      - **methode Webhaak:** `plugin.magento.out_of_process_shipping_methods.api.shipping_rate_repository.get_rates`
      - **het type van Webhaak:** **na**
      - **URL:** opgesteld **verschepen-methodes** Webactie URL (van opstellen output of [!DNL Adobe Developer Console]).
      - **Vereist:** **Facultatief** - dit staat controle toe om nog te werken als externe API geen tarieven terugkeert.

   ![&#x200B; Commerce Admin webshconfiguratie voor Mock die Tarieven verscheept &#x200B;](../assets/admin-webhook-shipping.png){width="600" zoomable="yes"}

1. **vorm de [!DNL Admin UI SDK] uitbreiding:**

   - In [!DNL Commerce Admin], ga naar **Opslag** > Montages > **Configuratie**.
   - Open {de Diensten van 0} Adobe **>** Admin UI SDK **.**
   - Plaats **toelaten Admin UI SDK** aan **ja** en klik **sparen Config** als het niet reeds wordt toegelaten.
   - Klik **vormen uitbreidingen**, kies de werkruimte uw app aan wordt opgesteld, dan klik **&#x200B;**&#x200B;toepassen. U kunt de **optie van de Douane** ook selecteren en de werkruimtenaam ingaan.
   - Selecteer de [!DNL App Builder] -toepassing in de lijst en sla deze op. Als app niet verschijnt, klik **verfrist registraties** en probeert opnieuw.

   ![&#x200B; Admin UI SDK vormt uitbreidingen modaal met werkruimte en uitbreidingsselectie &#x200B;](../assets/admin-ui-configure-extensions.png){width="600" zoomable="yes"}

1. **vorm de Verzendmethode van het Mock in Adobe Commerce Admin UI:**
   - Open **Apps** en selecteer uw app.
   - Open het **Mock die** tabel (of gelijkwaardig) verscheept.
   - Voer de volgende gegevens in:
      - **de Dienst URL:** de het werkschema URL van het Pipetream u kopieerde (bijvoorbeeld `https://123456.m.pipedream.net`).
      - **API sleutel:** om het even welke niet lege waarde voor het mock, bijvoorbeeld `tutorial-key`.
      - **Warehouse (schip-van) adres:** naam, telefoon, straat, stad, staat, postcode, land.
   - Klik **sparen**. De configuratie wordt opgeslagen in Runtime staat en door de verschepen-methodes actie gebruikt.

   ![&#x200B; Verzendconfiguratie van het Mock met de Dienst URL, API sleutel, en pakhuisadres &#x200B;](../assets/admin-ui-mock-shipping.png){width="600" zoomable="yes"}

1. **verifieer bij controle:** voeg een product aan de kar toe, ga aan controle, en ga een verschepend adres in. U zou de mock die opties verschepen, bijvoorbeeld **StandaardMock** en **Uitdrukkelijke Mock** moeten zien.

   ![&#x200B; pagina die van de Controle Mock Verzendopties van externe tarieven API toont &#x200B;](../assets/checkout-mock-shipping.png){width="600" zoomable="yes"}

### Problemen oplossen

- **Config sparen niet in Admin UI:** als u &quot;Reactie niet geldig &quot;bericht/http&quot;of waarden ziet die na sparen niet bijwerken, controleer runtime activeringslogboeken voor de config actie, gebruikend een bevel gelijkend op het volgende:

  ```bash
  aio app logs --action CustomMenu/shipping-config --limit 20
  ```

  De gemeenschappelijke oorzaken omvatten de gateway die een specifiek reactieformaat (bijvoorbeeld een koordlichaam en `Content-Type: application/json`) of de staatsbibliotheek verwacht die koordwaarden-verzeker de actie config als koord opslaat en het ontleedt wanneer het lezen, en dat de verschepen-methodes actie het zelfde ontleden gebruikt. Herzie de agentenpraatje of de logboeken voor de nauwkeurige oorzaak en moeilijke situatie.

- **&quot;De reactie moet minstens één verrichting bevatten&quot;** (in webhalogboeken): Commerce vereist de verschepende webhaak om minstens één verrichting terug te keren. Vraag de agent om ervoor te zorgen dat de actie voor verzendmethoden nooit een lege bewerkingsarray retourneert (bijvoorbeeld door een fallback-snelheid te retourneren wanneer de externe API geen snelheden retourneert).

- **Geen verschepende tarieven bij controle:** bevestig webhaak URL en de methode correct zijn, wordt de mock drager geregistreerd (`npm run create-shipping-carriers`), en het Verschepende config van het Mock wordt geplaatst in [!DNL Admin UI]. Controleer of de actie bij uitvoering is geregistreerd voor de actie voor verzendmethoden voor API- of validatiefouten. Controleer of de actie ten minste één bewerking retourneert. In [!DNL Commerce] wordt dus niet &quot;De reactie moet ten minste één bewerking bevatten&quot; weergegeven.

### Zelfstudie

Hier volgt een overzicht van de onderwerpen die in deze zelfstudie worden behandeld:

- **Eerste vereisten en opstelling:** het verifiëren van hulpmiddelen en het creëren van de mock verschepende tarief API.
- **agent-gedreven ontwikkeling:** Gebruikend de handel-rekbaarheid toolset om vereisten, een implementatieplan, en code voor de verschepende webhaak en Admin UI te produceren.
- **Fase 5 schoonmaakbeurt:** Verwijderend ongebruikte de domeinen van de controleaanzet en steigers alvorens op te stellen.
- **Plaatsing:** pre-plaatsingsbeoordeling en toolkit MCP opstellen.
- **post-plaatsing configuratie:** registrerend de mock drager, vormend de [!DNL Commerce] webhaak, toelatend de [!DNL Admin UI SDK] uitbreiding, en plaatsend de Scheepvaart van het Mock (de dienst URL, API sleutel, pakhuis) in [!DNL Admin UI].
- **Verificatie:** Bevestigend mock verschepende opties verschijnen bij controle.

### Volgende stappen

Overweeg het volgende voor verdere experimenten met deze zelfstudie:

- Automatiseer installatie na implementatie met een haak die de mock carrier in [!DNL Commerce] registreert en de verschepende webhaak na elke implementatie configureert.
- Wijzig de URL van de service en de API-sleutel in de [!DNL Admin UI] in de richting van de extensie op een API met echte verzendsnelheden.
- Breid [!DNL Admin UI] uit om dragerstatus of testconnectiviteit aan de tariefdienst te tonen.
