---
title: Extensiezelfstudie over levering wordt geschat
description: Leer hoe u een geschatte leverdatum voor Adobe Commerce as a Cloud Service bouwt met App Builder-, Edge Delivery Services- en AI-ontwikkelingsprogramma's.
solution: Commerce
feature: App Builder, Cloud
feature-set: Commerce
role: Developer
level: Intermediate
type: Tutorial
hide: true
hidefromtoc: true
source-git-commit: 3fc8982613df7b1155cdfb08ac4b56de6d1ce4f6
workflow-type: tm+mt
source-wordcount: '3334'
ht-degree: 0%

---

# Zelfstudie over het maken van ramingen voor levering

In deze zelfstudie wordt uitgelegd hoe u een geschatte verlenging voor de leveringsdatum bouwt voor [!DNL Adobe Commerce as a Cloud Service] gebruik maken van [!DNL Adobe App Builder] , [!DNL Edge Delivery Services] en de ontwikkelingstools voor AI-toepassingen. De extensie haalt ramingen van de verzendtijd en de leveringsdatum op van een externe API en geeft deze weer in de hele winkel.

U bouwt twee delen:

- **de uitbreiding van App Builder** — Een backend-voor-frontend (BFF) actie die een externe leveringsschatting API verpakt, een webhaak die verschepende methodes met leveringsdata bij controle verrijkt, en een Admin UI configuratiepagina voor het beheren van montages zonder herplaatsing.
- **integratie van de Storefront** — De schattingen van de leveringsdatum die op de pagina van het productdetail (PDP), de kartpagina, en de controlepagina gebruikend [!DNL Edge Delivery Services] drop-in componenten en een gedeelde cliëntmodule worden getoond.

>[!NOTE]
>
>AI-agentia zijn niet deterministisch. De vragen, vragen en resultaten in deze zelfstudie zijn voorbeelden. Uw agent kan verschillende vragen, vereisten, of architectuurvoorstellen veroorzaken. Gebruik de voorbeelden in deze zelfstudie om de agent naar een vergelijkbaar resultaat te sturen.

Alvorens u begint, voltooi de [&#x200B; eerste vereisten &#x200B;](./tutorial-prerequisites.md). Dit leerprogramma gebruikt de **uitcheckstarter uitrusting**. Controleer of u de toepassing al hebt gekloond en voltooi de stappen die op de pagina met voorwaarden worden beschreven.

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

- U hebt een [!DNL Adobe Commerce as a Cloud Service] -instantie met productgegevens. Zie {de instanties van de Dienst van 0} Commerce Cloud [.](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview){target="_blank"}
- Er is een storefront-project verbonden met uw [!DNL Commerce] -instantie. Als u geen hebt, volg de stappen in [&#x200B; creeer een storefront &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/){target="_blank"}.
- De `aem` CLI is geïnstalleerd:

  ```bash
  npm install -g @adobe/aem-cli
  ```

- U hebt a **winkelrekening** — een geregistreerde klant in [!DNL Commerce] met een bewaard standaard verschepend adres. De schattingen van de levering op PDP en de pagina&#39;s van de Kaart worden slechts getoond aan login kopers. Bij Afhandeling worden schattingen weergegeven voor alle kopers, ongeacht de verificatiestatus.

>[!IMPORTANT]
>
>Dit leerprogramma gebruikt het **Uitchecken van de Aanzet van de Controle** (niet de Uitrusting van de Aanzet van de Integratie). Met de Uitchecken Starter Kit kunt u op webhaak gebaseerde berekeningen maken voor betalingen, verzendkosten, belastingen en gebeurtenissen. Zorg ervoor dat u de uitcheckkit loslaat.

## De mock-delivery-schatting-API instellen

De extensie roept een externe API voor een schatting van de levering aan om schattingen van verzenddatum en -tijd te verkrijgen. Voor deze zelfstudie gebruikt u een mock-API, zodat u de volledige flow zonder een echte carrier-account kunt uitvoeren. Er zijn twee opties beschikbaar:

- **Optie A: Het werkschema van de Pijpnaam** — Vrije rij, snelle opstelling, maar heeft maandelijkse oproepingsgrenzen.
- **Optie B: De Runtime van App Builder actie** — Geen externe gebiedsdeel, die tijdens de stappen van de achterste ontwikkelingsontwikkeling wordt gecreeerd.

>[!TIP]
>
>Tijdens ontwikkeling, kunt u met Pipedream (Optie A) beginnen en op een Runtime actie (Optie B) schakelen als u het vrije-rij aanroepingsquotum bereikt. Beide opties implementeren hetzelfde API-contract.

### API-specificatie

De mock-API accepteert een POST-aanvraag en retourneert ramingen voor de leveringsdatum met de vervoerder, doorvoerdagen, afkaptijd en een beste schatting.

**het lichaam van het Verzoek** (alle gebieden facultatief voor het mock):

```json
{
  "origin": { "country_code": "US", "postal_code": "90210", "city": "Beverly Hills" },
  "destination": { "country_code": "US", "postal_code": "10001", "city": "New York" },
  "ship_date": "2026-03-10",
  "carriers": ["standard", "express"],
  "service_levels": ["standard", "express"]
}
```

**Reactie (200 OK):**

```json
{
  "estimates": [
    {
      "carrier_code": "standard",
      "service_code": "ground",
      "delivery_date": "2026-03-14",
      "safe_delivery_date": "2026-03-15",
      "transit_days": 4,
      "cutoff_datetime_utc": "2026-03-10T17:00:00.000Z"
    },
    {
      "carrier_code": "express",
      "service_code": "2day",
      "delivery_date": "2026-03-12",
      "safe_delivery_date": "2026-03-12",
      "transit_days": 2,
      "cutoff_datetime_utc": "2026-03-10T12:00:00.000Z"
    }
  ],
  "best_estimation": { "carrier_code": "express", "delivery_date": "2026-03-12", "transit_days": 2 }
}
```

**reacties van de Fout:** 401 (het ontbreken/ongeldige API sleutel), 400 (ongeldig `ship_date` formaat), 503 (gesimuleerde onderbreking).

### De mock instellen

>[!BEGINTABS]

>[!TAB  Pipedream werkschema ]

De optie Pipedream gebruikt tokenauthentificatie van de Drager en keurt een verzoek van de POST aan de werkschemaprempel URL goed.

| Item | Beschrijving |
|------|-------------|
| Basis-URL | De volledige URL voor trigger van de Pipedream-workflow (bijvoorbeeld `https://<id>.m.pipedream.net`) |
| Auth | `Authorization: Bearer <API_KEY>` |
| Methode | POST |

{style="table-layout:auto"}

**creeer het werkschema:**

1. Creeer een nieuw werkschema in [&#x200B; Pipedream &#x200B;](https://pipedream.com){target="_blank"} (**[!UICONTROL Workflows]** > **[!UICONTROL New Workflow]**).

1. Voeg een **HTTP/Webhaak** trekker toe die voor POST wordt gevormd. Pipedream wijst een webhaak-URL toe.

1. Voeg de stap van de code van Node.js van de a **Looppas** toe en kleef de volgende managercode:

   ```javascript
   const DEFAULT_CARRIERS = [
     { carrier_code: "standard", service_code: "ground", transit_days: 4 },
     { carrier_code: "express", service_code: "2day", transit_days: 2 },
     { carrier_code: "priority", service_code: "overnight", transit_days: 1 },
   ];
   
   const ISO_DATE = /^\d{4}-\d{2}-\d{2}$/;
   
   function parseShipDate(shipDate) {
     if (shipDate == null || typeof shipDate !== "string") return null;
     if (!ISO_DATE.test(shipDate)) return null;
     const d = new Date(shipDate + "T12:00:00.000Z");
     if (Number.isNaN(d.getTime())) return null;
     return shipDate;
   }
   
   function addBusinessDays(isoDate, days) {
     const d = new Date(isoDate + "T12:00:00.000Z");
     let added = 0;
     while (added < days) {
       d.setUTCDate(d.getUTCDate() + 1);
       const dow = d.getUTCDay();
       if (dow !== 0 && dow !== 6) added += 1;
     }
     return d.toISOString().slice(0, 10);
   }
   
   function cutoffUtc(isoDate, hour = 17) {
     return `${isoDate}T${String(hour).padStart(2, "0")}:00:00.000Z`;
   }
   
   function getBearerToken(headers) {
     const auth = headers?.Authorization ?? headers?.authorization ?? "";
     if (typeof auth !== "string" || !auth.startsWith("Bearer ")) return null;
     return auth.slice(7).trim() || null;
   }
   
   function handleDeliveryEstimate(body) {
     const shipDate = parseShipDate(body?.ship_date);
     const baseDate = shipDate ?? new Date().toISOString().slice(0, 10);
     let carriers = DEFAULT_CARRIERS;
     if (Array.isArray(body?.carriers) && body.carriers.length > 0) {
       const set = new Set(body.carriers.map((c) => String(c).toLowerCase()));
       carriers = DEFAULT_CARRIERS.filter((c) => set.has(c.carrier_code.toLowerCase()));
     }
     if (Array.isArray(body?.service_levels) && body.service_levels.length > 0) {
       const set = new Set(body.service_levels.map((s) => String(s).toLowerCase()));
       carriers = carriers.filter(
         (c) => set.has(c.service_code.toLowerCase()) || set.has(c.carrier_code.toLowerCase())
       );
     }
     if (carriers.length === 0) {
       return { status: 200, body: { estimates: [], best_estimation: null } };
     }
     const estimates = carriers.map((c) => {
       const delivery_date = addBusinessDays(baseDate, c.transit_days);
       const safe_delivery_date = addBusinessDays(baseDate, c.transit_days + 1);
       const cutoff_datetime_utc = cutoffUtc(baseDate, 17 - c.transit_days);
       return {
         carrier_code: c.carrier_code,
         service_code: c.service_code,
         delivery_date,
         safe_delivery_date,
         transit_days: c.transit_days,
         cutoff_datetime_utc,
       };
     });
     return { status: 200, body: { estimates, best_estimation: estimates[0] } };
   }
   
   export default defineComponent({
     async run({ steps, $ }) {
       const event = steps.trigger?.event ?? steps.trigger ?? {};
       const body = event.body ?? {};
       const headers = event.headers ?? {};
       const auth = getBearerToken(headers);
       const expectedKey =
         (typeof process.env.MOCK_API_KEY === "string" && process.env.MOCK_API_KEY.trim()) || null;
       if (expectedKey && (!auth || auth !== expectedKey)) {
         await $.respond({
           immediate: true,
           status: 401,
           headers: { "Content-Type": "application/json" },
           body: { error: "unauthorized", message: "Missing or invalid API key." },
         });
         return;
       }
       if (body?.ship_date != null && !parseShipDate(body.ship_date)) {
         await $.respond({
           immediate: true,
           status: 400,
           headers: { "Content-Type": "application/json" },
           body: { error: "bad_request", message: "Invalid ship_date; use YYYY-MM-DD." },
         });
         return;
       }
       const { status, body: responseBody } = handleDeliveryEstimate(body);
       await $.respond({
         immediate: true,
         status,
         headers: { "Content-Type": "application/json" },
         body: responseBody,
       });
     },
   });
   ```

1. (Optioneel) Voeg een omgevingsvariabele `MOCK_API_KEY` toe in de workflowinstellingen om de tokenauth van de gebruiker af te dwingen. Indien niet ingesteld, wordt een verzoek geaccepteerd.

1. Implementeer de workflow.

   Uw eindpunt is de URL van de webhaaktrigger.

**Test het mock:**

```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer mock-api-key" \
  -d '{"destination": {"country_code": "US", "postal_code": "10001"}}' \
  "https://<your-endpoint>.m.pipedream.net"
```

>[!TAB  Runtime van App Builder actie ]

De handelingsoptie App Builder Runtime implementeert het mock als Runtime actie binnen het zelfde [!DNL App Builder] project. Deze aanpak heeft geen externe afhankelijkheid en geen oproepingsquota.

Vraag de agent om de mock actie tot stand te brengen:

```shell-session
Add a new runtime action to this project that implements the API in @docs/PIPEDREAM_API_SPEC.md
- Add it to a separate package
- Use the code in docs/pipedream as inspiration
```

De agent maakt `actions/mock-delivery-api/index.js` met hetzelfde API-contract als de optie Pipedream. Na het opstellen, is het eindpunt:

```shell-session
https://<namespace>.adobeioruntime.net/api/v1/web/mock-delivery-api/delivery-estimate
```

Verificatie wordt gevalideerd tegen een `MOCK_API_KEY` omgevingsvariabele in `.env` .

>[!ENDTABS]

## Uitbreiding

Deze sectie begeleidt u door het ontwikkelen van de [!DNL App Builder] backend voor de levering schat uitbreiding. De achtergrond biedt drie acties:

| Actie | Type | Doel |
|--------|------|---------|
| `delivery-estimates` | Zelfstandige webactie | BFF voor opslag — PDP en kart roepen dit voor leveringsdata |
| `shipping-methods` | Handeling WebHaak | Verhoogt de verzendkosten met leveringsdatums in `additional_data` bij afrekenen |
| `delivery-estimates-config` | Achterstallige beheeractie | CRUD voor configuratie opgeslagen in `aio-lib-state` |

{style="table-layout:auto"}

1. Van de montages MCP in uw coderingsagenten, verifieer dat toolset `commerce-extensibility` zonder fouten wordt toegelaten.

   Ga bijvoorbeeld in Cursor naar **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Tools & MCP]** .

   Als er fouten optreden, schakelt u de gereedschapset in en uit.

   >[!NOTE]
   >
   >Als u werkt met ontwikkelprogramma&#39;s voor AI, verwacht u natuurlijke variaties in de code en reacties die door de agent worden gegenereerd.
   >Als u om het even welke kwesties met uw code ontmoet, vraag de agent om u te helpen het zuiveren.

1. Als u documentatie hebt toegevoegd aan de context van de Cursor, maak het onbruikbaar.

   Navigeer naar **[!UICONTROL Cursor]** > **[!UICONTROL Settings]** > **[!UICONTROL Cursor Settings]** > **[!UICONTROL Indexing & Docs]** en verwijder de vermelde documentatie.

### Stap 1: Geef de eerste prompt op

Geef de agent de externe API specificatie voor context en vraag het om te beginnen. Als u de agent vertelt om te stoppen en vragen te stellen, kunt u de implementatie vroeg sturen.

Ga de volgende herinnering in het de praatjevenster van de agent in:

```shell-session
I want to build an Adobe App Builder extension that extends the checkout with shipping date and time estimates taken from an external API described in @docs/API_SPEC.md.
Delivery dates for a product will be shown in the product details page and on the cart page.
Implement this feature by using the skills in this workspace for backend code, and a separate workspace with storefront skills. For this extension, focus on the backend skills and create an API_SPEC to hand work over to the storefront skills.

STOP and ask me clarifying questions about the requirements before you do any work.
```

>[!TIP]
>
>Verwijzen van het externe API specificatiedossier (`@docs/API_SPEC.md`) in de herinnering geeft de agent concrete context over het derde API contract. De agent gebruikt dit om de actie BFF, de gedeelde cliënt van HTTP, en de configuratiegebieden van Admin UI te ontwerpen. Door de agent aan STOP te roepen en vragen te stellen, wordt de geleide workflow geactiveerd en kunt u de implementatie vroeg sturen.

### Stap 2: Antwoord de vragen van de agent

De agent keert met een reeks het verduidelijken vragen terug die onderwerpen zoals doelmilieu (PaaS vs SaaS), werkingsgebied (standalone actie BFF, webhaakverrijking, of allebei), oorsprong adresbron, caching strategie, en testvoorkeur behandelen. In het volgende voorbeeld worden typische vragen en antwoorden getoond. Uw agent kan verschillende vragen stellen, maar de onderwerpen zijn over het algemeen het zelfde.

**de agentenvragen van het Voorbeeld:**

1. **milieu van het Doel** — bouwt u voor PaaS (op-gebouw) of SaaS (Adobe Commerce as a Cloud Service)?
2. **Reikwijdte** — Moet dit een standalone actie BFF (storefront roept het direct), webhaakverrijking (breid verschepende methodes bij controle uit), of allebei zijn?
3. **configureerbaarheid Admin** - zouden de montages zoals API URL, API sleutel, en oorsprongadres via Commerce Admin configureerbaar moeten zijn, of in `.env` worden opgeslagen?
4. **adres van de Oorsprong** — Waar komt het schip-van (pakhuis) adres uit? Moet het een statische configuratie of dynamisch worden opgelost?
5. **Caching** — Moeten de leveringsramingen op de serverzijde in het voorgeheugen ondergebracht worden om vraag aan externe API te verminderen? Zo ja, welke TTL?

**antwoorden van het Voorbeeld:**

```shell-session
Clarifications:
1. Let's build for SaaS
2. Let's do this:
(A) Can the PDP/cart call the 3rd party API directly — or are there any benefits of wrapping this call with a runtime action?
(B) Let's use the shipping-methods webhook
3. Let's use a Single-page application (SPA) that uses the Admin UI SDK to integrate with the admin. Since we are adding this config screen, let's make anything else that makes sense configurable to avoid redeployments when changing settings
4. Static configuration — origin address should be configurable in the Admin UI (e.g. warehouse address)
5. Yes, cache on the server side; suggest a TTL (e.g. 30 minutes) and make it configurable in the Admin UI
```

>[!TIP]
>
>Als de agent wordt gevraagd of de storefront de API van derden rechtstreeks moet aanroepen of door een runtimeactie moet gaan, wordt een nuttige architectuurdiscussie gestart. De agent verklaart de voordelen van het patroon BFF (Backend-for-Frontend): de API sleutel blijft server-kant, CORS wordt behandeld, caching is gecentraliseerd, en u krijgt verkopersabstractie. Door te vragen of de interface voor beheerders configureerbaar is, moet de agent alle instellingen opslaan in `aio-lib-state` in plaats van `.env` , zodat herimplementaties worden voorkomen wanneer de instellingen worden gewijzigd.

>[!NOTE]
>
>Uw agent kan verschillende vragen stellen. Gebruik deze antwoorden als richtlijn om de agent naar het zelfde functionele resultaat te leiden: een actie BFF voor storefront vraag, een verschepende-methodes webhaak voor checkout verrijking, en een Admin UI config pagina die montages in `aio-lib-state` opslaat.

### Stap 3: Evaluatievereisten en architectuur

De agent produceert vereisten en architectuurdocumenten voor u aan overzicht. Controleer of de vereisten overeenkomen met de antwoorden die u hebt gegeven en of de architectuur van toepassing is op:

- A **actie BFF** (`delivery-estimates`) — Een standalone Webactie die de storefront van PDP en kartpagina&#39;s roept. Deze leest configuratie uit `aio-lib-state`, roept de externe schattings-API voor levering aan en retourneert opgemaakte schattingen.
- A **WebHaak actie** (`shipping-methods`) — Verrijkt het verschepen tarieven met leveringsdata in `additional_data` tijdens controle. Gebruikt de `plugin.out_of_process_shipping_methods.api.shipping_rate_repository.get_rates` webshmethode.
- Een **handeling Admin config** (`delivery-estimates-config`) - CRUD voor configuratie (API URL, API sleutel, oorsprongadres, dragers, geheim voorgeheugen TTL) die in `aio-lib-state` wordt opgeslagen.
- **Gedeelde bibliotheken** — Een cliënt van HTTP voor externe API en een config module voor het lezen en het schrijven `aio-lib-state`.

>[!NOTE]
>
>AI-agents zijn niet deterministisch en hun gedrag verschilt afhankelijk van het model en IDE. U kunt een verschillende reeks vragen krijgen die een verschillende reeks vereisten en architectuur produceren. Als zo, probeer om de agent in een richting te sturen zodat de implementatie dicht aanpast wat in dit leerprogramma alvorens te werk te gaan wordt voorgesteld.

### Stap 4: Selecteer een implementatieplan

De agent geeft u de optie om een gedetailleerd implementatieplan te creëren of een directe implementatie te voltooien.

- Als u een reviewable plan wilt dat u in fasen met meer controle kunt uitvoeren, selecteer de eerste optie.
- Als u wilt dat de agent de volledige implementatie uitvoert met minimale tussenkomst, selecteert u de tweede optie.

### Stap 5: opschonen en implementeren

Zodra de agent de implementatie voltooit, gaat het aan schoonmaakbeurt. Aangezien slechts het Verzenddomein in gebruik is, verwijdert de agent ongebruikte steigers:

- Betalingsacties en configuratie (`validate-payment/`, `filter-payment/`, `payment-methods.yaml`)
- Belastinghandelingen en config (`collect-taxes/`, `collect-adjustment-taxes/`, `tax-integrations.yaml`)
- Gebeurtenisacties en configuratie (`commerce-events/`, `3rd-party-events/`, `events.config.yaml`)
- Algemene steigers (`generic/`)
- Admin UI SPA-componenten van andere domeinen (bijvoorbeeld pagina&#39;s en haken die betrekking hebben op belastingen)
- Ongebruikte scripts, testbestanden en omgevingsvariabelen

>[!TIP]
>
>Vraag de agent om Admin UI SPA ook voor overblijvers van andere domeinen te controleren. De pagina Belastingsklassen en de bijbehorende haken zijn mogelijk nog steeds aanwezig in de basisstructuur van de startkit en moeten worden verwijderd.

Na schoonmaak, stel het gebruiken van deze stappen **in deze orde** op:

```bash
# 1. Copy env template and fill in credentials.
cp env.dist .env

# 2. Select your App Builder workspace.
aio app use --merge

# 3. Sync OAuth credentials from workspace.
npm run sync-oauth-credentials

# 4. Deploy the extension.
aio app deploy

# 5. Register shipping carriers in Commerce.
npm run create-shipping-carriers
```

>[!IMPORTANT]
>
>Sla de stappen niet over of wijzig de volgorde ervan. De stappen 1-3 zijn eerste vereisten aan plaatsing. De opdracht `aio app deploy` mislukt als er geen referenties zijn geconfigureerd.

### Stap 6: Webhaak en Admin UI configureren

Na het opstellen, vorm de verschepende webhaak. De agent kan een manuscript tot stand brengen programmatically om in te tekenen:

```bash
npm run subscribe-webhook
```

Met deze opdracht abonneert u zich op de verzendende webhaak met de volgende instellingen:

| Veld | Waarde |
|-------|-------|
| Methode WebHaak | `plugin.out_of_process_shipping_methods.api.shipping_rate_repository.get_rates` |
| Type webHaak | `after` |
| Vereist | Optioneel (bij fallback wordt standaardverzending toegestaan) |
| Time-out | 5000 ms |

{style="table-layout:auto"}

>[!NOTE]
>
>Voor SaaS, laat de naam van de webhaakmethode `magento.` van de weg vallen. De naam van de webhaak voor PaaS is `plugin.magento.out_of_process_shipping_methods...` en de naam van de webhaak voor SaaS is `plugin.out_of_process_shipping_methods...` .

Configureer vervolgens de interface voor Admin:

1. Laat **Admin UI SDK** toe (**[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Adobe Services]** > **[!UICONTROL Admin UI SDK]** > **[!UICONTROL Enable]** > **[!UICONTROL Yes]**).

1. Configureer extensies door uw [!DNL App Builder] -werkruimte en -extensie te selecteren.

1. Klik op **[!UICONTROL Refresh registrations]**.

1. Navigeer naar **[!UICONTROL Apps]** > **[!UICONTROL Delivery Estimates]** in de zijbalk van [!DNL Admin] .

1. Voltooi de configuratie door de functie in te schakelen en de vereiste instellingen op te geven, waaronder de API-URL en -API-sleutel, het oorspronkelijke adres, standaardcarriers, TTL-cache en toewijzingen van de transportcode.

### Stap 7: Test de extensie

Test de BFF-actie voor de leveringsramingen rechtstreeks:

```bash
curl -s -X POST \
  -H "Content-Type: application/json" \
  -d '{"destination": {"country_code": "US", "postal_code": "10001"}}' \
  "https://<your-runtime-url>/api/v1/web/commerce-checkout-starter-kit/delivery-estimates" | jq .
```

De respons moet er ongeveer als volgt uitzien:

```json
{
  "estimates": [
    {
      "carrier": "standard",
      "service_level": "ground",
      "delivery_date": "2026-03-12",
      "safe_delivery_date": "2026-03-13",
      "transit_days": 4,
      "cutoff_datetime_utc": "2026-03-06T18:00:00Z"
    },
    {
      "carrier": "express",
      "service_level": "2day",
      "delivery_date": "2026-03-10",
      "safe_delivery_date": "2026-03-10",
      "transit_days": 2,
      "cutoff_datetime_utc": "2026-03-06T20:00:00Z"
    }
  ],
  "best_estimation": {
    "carrier": "express",
    "delivery_date": "2026-03-10",
    "transit_days": 2
  }
}
```

### Het servicecontract maken

Nu de backend volledig is, vraag de agent om een de dienstcontract voor het storefront werk tot stand te brengen:

```shell-session
Produce a spec called STOREFRONT_API_SPEC that I can use in the storefront workspace with the corresponding agent. Also give me a prompt that I could use in that workspace.
```

De agent produceert `docs/STOREFRONT_API_SPEC.md` met het volledige BFF eindpuntcontract (verzoek en reactieformaat, voorbeeldlading, fout behandeling) en een klaar-aan-gebruikherinnering voor de storefront werkruimte.

Kopieer dit bestand naar uw winkelproject voordat u de opslagront dev-stappen start.

>[!TIP]
>
>Het hebben van de agent produceert zowel een de dienstcontract **als** een herinnering voor de andere werkruimte verzekert een schone handoff tussen de backend en storefront teams (of agenten). De storefront agent kan onmiddellijk beginnen te werken zonder vragen over API te hoeven stellen.

## Verbinding maken met de winkel

Deze sectie begeleidt u door het storefront gedeelte van de leveringsramingen uit te voeren gebruikend [!DNL Edge Delivery Services] en AI-Hulp ontwikkelingshulpmiddelen. U voegt schattingen voor de leveringsdatum toe aan de PDP-, winkelwagentje- en afhandelingspagina.

>[!NOTE]
>
>De verstrekte herinneringen zijn beginpunten. Hoewel u hen zonder wijziging kunt gebruiken, denk na hebbend een natuurlijk gesprek met de agent.
>
>Als u werkt met ontwikkelprogramma&#39;s die zijn gebaseerd op AI, zijn er altijd natuurlijke variaties in de code en de reacties die door de agent worden gegenereerd.
>
>Als u om het even welke kwesties met uw code ontmoet, vraag de agent om u te helpen het zuiveren.

### Voorwaarden voor Storefront

Alvorens de storefront integratie te beginnen, verifieer dat u het volgende hebt:

- Een storefront-project dat is verbonden met uw [!DNL Commerce] -instantie
- Commerce storefront AI hulpmiddelen [&#x200B; geïnstalleerd gebruikend CLI &#x200B;](./tutorial-prerequisites.md#install-the-storefront-ai-tools)
- Het `STOREFRONT_API_SPEC.md` -bestand is gekopieerd naar de map `docs/` van het storefront-project

### Stap 1: De omgeving valideren

Open het `config.json` -bestand en controleer of de waarden voor `commerce-core-endpoint` en `commerce-endpoint` naar het [!DNL Adobe Commerce as a Cloud Service] GraphQL-eindpunt verwijzen.

```json
"commerce-core-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
"commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/<your-instance-id>/graphql",
```

### Stap 2: Geef de eerste prompt op

Met het de dienstcontract reeds in uw project, vraag de agent om de storefront integratie uit te voeren. Het gebruik **wijze van het Plan van 0&rbrace; als beschikbaar in uw agent, om de agent te verhinderen zonder een plan te werk te gaan.**

```shell-session
I need to implement delivery date estimates on the storefront for an Adobe Commerce (SaaS) store using Edge Delivery Services with storefront drop-ins. The backend is already built and deployed as an App Builder extension.

The full integration contract is in the `docs/STOREFRONT_API_SPEC.md` file— please read it first. It covers two integration points:

PDP and Cart pages — Call the delivery-estimates BFF action (HTTP POST) to fetch estimates for a destination and display the best delivery date.

Checkout shipping step — Delivery dates are already injected into each shipping method's `additional_data` by a webhook. No API call is needed. Just read `additional_data` from the shipping methods and display the delivery date next to each option.

Requirements:
- Show "Get it by [date]" on PDP using best_estimation.delivery_date
- Show a delivery date range on the cart page using delivery_date / safe_delivery_date
- Show delivery dates next to each shipping method at checkout, reading from additional_data
- Show "Order within X hours" countdown using cutoff_datetime_utc where appropriate
- Cache estimates client-side in sessionStorage to avoid redundant calls
- Never block the purchase flow — if estimates are unavailable, hide the UI silently

STOP and ask me any clarifying questions you have about the requirements before you do any work.
```

>[!TIP]
>
>De vraag is gedetailleerd omdat het volledige API contract reeds beschikbaar bij de backend agent is. Door `@docs/STOREFRONT_API_SPEC.md` van verwijzingen te voorzien, kent de agent het nauwkeurige eindpunt URL, verzoek en reactieformaat, en fout behandeling. De expliciete lijst van vereisten verhindert de agent werkingsgebied uit te vinden. Specifiek, teweegbrengt het vragen van planwijze de gefaseerde werkschema teweeg die u helpt de implementatie vroeg sturen.

### Stap 3: Antwoord ter verduidelijking van vragen

De agent keert met vragen over authentificatiewerkingsgebied, controlebenadering, en het stileren terug. In het volgende voorbeeld worden typische vragen en antwoorden getoond.

**de agentenvragen van het Voorbeeld:**

1. **Anonieme vs het programma geopende gebruikers** - zouden de schattingen op PDP en de pagina&#39;s van het Kaart voor alle kopers of slechts voor authentiek verklaarde degenen moeten tonen?
2. **de benadering van de Controle** - De container ShippingMethods drop-in stelt niet `additional_data` bloot, zodat stelt de agent twee opties voor:
   - **Optie A:** Vraag BFF bij controle en DOM-Injecteer leveringsdata (eenvoudiger, verenigbaar met PDP/Kart)
   - **Optie B:** breid het uitcheckfragment van GraphQL via `overrideGQLOperations` uit om `additional_data` te omvatten
3. **het Stijlen** — Emojis vs bestaande ontwerptokens

**antwoorden van het Voorbeeld:**

```shell-session
1. Only for logged-in users — that way we can use the shopper's default shipping address and avoid a zip code input
2. Let's do Option A if feasible
3. Use anything that matches the current styling
```

>[!TIP]
>
>Het weergeven van schattingen alleen voor aangemelde winkels is een pragmatische keuze. De agent kan automatisch het standaardverzendadres van de verkoper gebruiken (via GraphQL), zodat er geen postcode-invoer nodig is. Anonieme kopers op PDP en Cart moeten een postcode invoeren, waardoor wrijving wordt toegevoegd. Bij het afrekenen zien alle kopers de leveringsdatums omdat het verzendadres al is ingevoerd.

>[!NOTE]
>
>Uw agent kan verschillende vragen stellen. Gebruik deze antwoorden als richtlijn:
>
>- Geef alleen schattingen van PDP&#39;s en winkelwagentjes weer voor aangemelde winkels (geen ZIP-code-invoer vereist).
>- Gebruik voor het uitchecken Option A (BFF-aanroep + DOM-injectie) voor het gemak.
>- Bestaande ontwerptokens gebruiken voor opmaak.

### Stap 4: Evaluatievereisten en architectuur

De agent ontwerpt een gedeelde modulearchitectuur. Controleren of het van toepassing is op:

| Component | Doel |
|-----------|---------|
| `scripts/delivery-estimates.js` | Gedeelde module — cliënt BFF, caching (sessionStorage, 30 min TTL), datum het formatteren, tellingslogica, klantenadresraadpleging, dragerafbeelding |
| PDP-integratie | De vertoningen &quot;krijgen het door [ datum ]&quot;met facultatieve afrekening tussen prijs en beschrijving |
| Kart-integratie | Hiermee geeft u het datumbereik (&quot;Thu, Mar 12 - Fri, Mar 13&quot;) in de rechterkolom boven het orderoverzicht weer |
| Integratie van uitchecken | Roept BFF aan wanneer de verzendstap actief is, injecteert DOM leveringsdata via `MutationObserver` |

{style="table-layout:auto"}

Belangrijkste beslissingen bij het ontwerp:

- Alle BFF-aanroepen zijn niet-blokkerend — pagina&#39;s worden eerst gerenderd, schattingen worden asynchroon weergegeven.
- Alle fouten zijn stil — `console.debug` alleen, geen fouten die naar de klant worden gericht.
- `CARRIER_MAP` wijst Commerce carrier codes (DPS, Fedex) toe aan BFF carrier codes (standard, express).
- Dynamisch `import()` houdt de leveringsmodule buiten het kritieke renderingpad.

>[!NOTE]
>
>AI-agents zijn niet deterministisch en hun gedrag verschilt afhankelijk van het model en IDE. U kunt een verschillende reeks vragen krijgen die een verschillende reeks vereisten en architectuur produceren. Als zo, probeer om de agent in een richting te sturen zodat de implementatie dicht aanpast wat in dit leerprogramma alvorens te werk te gaan wordt voorgesteld.

### Stap 5: Selecteer een implementatieplan

De agent geeft u de optie om een gedetailleerd implementatieplan te creëren of een directe implementatie te voltooien.

- Als u een reviewable plan wilt dat u in fasen met meer controle kunt uitvoeren, selecteer de eerste optie.
- Als u wilt dat de agent de volledige implementatie uitvoert met minimale tussenkomst, selecteert u de tweede optie.

Tijdens implementatie, leidt de agent tot en wijzigt de volgende dossiers:

**Nieuw dossier:**

- `scripts/delivery-estimates.js` — Gedeelde module met `fetchDeliveryEstimates()` , `getCustomerShippingAddress()` , `formatDeliveryDate()` , `buildCountdownText()` , `findEstimateForCarrier()`

**Gewijzigde dossiers:**

- `blocks/product-details/product-details.js` + `.css` — Schatting van levering div in de rechterkolom, asynchrone ophaalbewerking na renderen van hoofd
- `blocks/commerce-cart/commerce-cart.js` + `.css` — Aflevering schatting div boven orderoverzicht
- `blocks/commerce-checkout/commerce-checkout.js`, `containers.js`, `.css` — `MutationObserver` gebaseerde DOM-injectie voor labels van verzendmethoden

Bekijk de code die wordt gegenereerd en stel vragen of richt de agent zo nodig om.

### Stap 6: Start de server en test

Nadat de agent de implementatie voltooit, begin de ontwikkelingsserver en test de leveringsramingen.

1. Start de lokale ontwikkelingsserver:

   ```bash
   npm run start
   ```

1. Meld u in een browser aan bij uw winkelaccount.

   Voor schattingen van de levering op PDP en winkelwagentje is een geverifieerde sessie met een opgeslagen standaard verzendadres vereist.

1. Navigeer naar een productpagina en controleer de volgende resultaten:

   | Pagina | Verwacht resultaat | Auth required |
   |------|-----------------|---------------|
   | PDP | &quot;Kies voor donderdag 12 maart&quot; met optionele aftellen | Ja (alleen aangemeld) |
   | Kar | &quot;Geschatte levertijd: Thu, 12 maart - Fri, 13 maart&quot; | Ja (alleen aangemeld) |
   | Afhandeling | &quot;Geschatte levering: donderdag, 12 maart&quot; per verzendmethode | Geen (adres ingevoerd bij afhandeling) |

   {style="table-layout:auto"}

>[!NOTE]
>
>Verzendmethoden zonder overeenkomende drager (bijvoorbeeld Platte snelheid) geven geen schatting weer. Dit is door ontwerp — alleen carriers die zijn toegewezen in `CARRIER_MAP` krijgen leveringsdatums.

U kunt het manueel testen doen of de agent vragen om zijn browser mogelijkheden te gebruiken om voor u te testen:

```shell-session
Run complete browser testing using the following product page 'http://localhost:3000/products/<product-slug>/<sku>'
```

### Stap 7: Overbodig verwijderen

Nadat u overslaat of volledig het testen, zet de agent u ertoe aan te werk te gaan om op te schonen. Na bevestiging archiveert de agent alle tijdens de implementatie geproduceerde documentatieartefacten.

## Problemen oplossen

Gebruik de volgende tips als u tijdens de zelfstudie problemen ondervindt.

### Backend (App Builder)

| Symptoom | Oorzaak | Repareren |
|---------|-------|-----|
| De configuratieactie van Admin UI keert `400 Bad Request` met &quot;Verzoek bepaalt parameters die niet worden toegestaan (gereserveerde eigenschappen)&quot; terug | De frontend haak verzendt `__ow_method` in de aanvraaginstantie. Eigenschappen die zijn voorafgegaan door `__ow_` , worden gereserveerd door OpenWhisk en geweigerd wanneer de handeling is ingesteld op `final: true` . | Verzend een aangepaste eigenschap `method` in plaats van `__ow_method` . De backendactie leest eerst `params.method` en valt dan terug naar `params.__ow_method` (die Runtime automatisch verstrekt). |
| `aio app deploy` mislukt met &quot;maxVersion is required in productDependency&quot; | De CLI-validatie vereist zowel `minVersion` als `maxVersion` in `app.config.yaml` productafhankelijkheden. | Voeg een `maxVersion` -waarde toe aan elk `productDependencies` -item in `app.config.yaml` . |
| Implementatieopdracht mislukt | Credentials niet geconfigureerd vóór implementatie. `.env` , moet de werkruimte worden geselecteerd en moet OAuth-synchronisatie eerst plaatsvinden. | Volg de juiste volgorde: `cp env.dist .env` > `aio app use --merge` > `npm run sync-oauth-credentials` > `aio app deploy` . |

{style="table-layout:auto"}

### Storefront (Edge Delivery Services)

| Symptoom | Oorzaak | Repareren |
|---------|-------|-----|
| PDP leveringsschatting wordt niet weergegeven voor aangemelde winkels | Het PDP-blok initialiseert de `account` drop-in niet, zodat `getCustomerAddress()` ongemerkt mislukt en er geen schatting wordt opgehaald. | Gebruik `CORE_FETCH_GRAPHQL.fetchGraphQl()` rechtstreeks om query&#39;s uit te voeren op winkeladressen in plaats van te vertrouwen op de drop-in-API van de account. Dit werkt op elke pagina. |
| PDP wordt nog steeds niet weergegeven na GraphQL-correctie | Typo in methodenaam: `CORE_FETCH_GRAPHQL.fetch()` is gebruikt in plaats van `CORE_FETCH_GRAPHQL.fetchGraphQl()` . | Gebruik de juiste methodenaam: `fetchGraphQl` (hoofdletter Q, kleine letter l). |
| Leveringsdatums voor afhandeling worden niet weergegeven bij de eerste keer laden | De gebeurtenislistener `checkout/updated` is geregistreerd nadat `checkout/initialized` al was gestart, zodat de initiële gegevens werden overgeslagen. | Voeg een `checkout/initialized` listener met `{ eager: true }` toe om gebeurtenissen die vóór de registratie zijn verzonden, af te vangen. Houd de listener `checkout/updated` voor volgende wijzigingen. |
| Schatting voor levering van winkelwagentje is niet zichtbaar | `block.appendChild(fragment)` verplaatst alle onderliggende elementen uit het fragment, zodat `fragment.querySelector('.cart__delivery-estimate')` null retourneert. | Query uitvoeren vanuit `block` in plaats van `fragment` na de toevoegbewerking. |
| Bij verzending met vaste verzendkosten wordt geen leveringsdatum bij afhandeling weergegeven | Door ontwerp — `CARRIER_MAP` wijst alleen DPS toe aan de standaard en Fedex om uit te drukken. Platte snelheid heeft geen corresponderende drager in de externe API. | Geen bug. Als u schattingen wilt toevoegen voor andere carriers, breidt u de `CARRIER_MAP` in `scripts/delivery-estimates.js` uit en configureert u de carrier in de extensie backend. |

{style="table-layout:auto"}

### Commerce SaaS-sandbox

| Symptoom | Oorzaak | Repareren |
|---------|-------|-----|
| Webhaak retourneert `429 Too Many Requests` | De werkruimte van [!DNL App Builder] is in de foutopsporingsmodus, die strikte tarieflimieten per minuut heeft. [!DNL Commerce] herberekent de verzendkosten regelmatig tijdens het afrekenen, waarbij de quota volledig worden benut. | Stel aan een werkruimte van de Productie op (`aio app use` om, toen `aio app deploy` te schakelen). De werkruimten van de productie hebben zuiveringssnelheidsgrenzen niet. |
| Waarschuwing voor zachte time-out webhaak (>1000 ms) | De actie voor het verzenden van webhaken met verzendmethoden duurde langer dan de zachte time-out van [!DNL Commerce] 1000 ms. | Schakel plaatsing van caching aan de serverzijde agressiever in `aio-lib-state` of verhoog de time-out van de webhaak in [!DNL Commerce Admin] (Commerce Webhooks-configuratie). |

{style="table-layout:auto"}

## Zelfstudie

Hier volgt een overzicht van de onderwerpen die in deze zelfstudie worden behandeld:

- **Mock API opstelling:** Creërend een mock leveringsschatting API gebruikend Pijpmap of een [!DNL App Builder] Runtime actie.
- **patroon BFF:** bouwend een achtergrond-voor-frontend actie die externe API verpakt, geloofsbrieven server-kant houdt, en caching centraliseert.
- **de verrijking van Webhaak:** Uitbreidend de verschepende-methodes webhaak om leveringsdata in elke het verschepen optie bij controle te injecteren.
- **configureerbaarheid Admin UI:** Toevoegend een configuratiepagina gebruikend [!DNL Admin UI SDK] zodat kunnen de verkopers API montages, oorsprongadres, en dragertoewijzingen zonder herplaatsing beheren.
- **de contracten van de Dienst:** Creërend API contracten die achterste uitbreidingen en storefront implementaties overbruggen.
- **integratie van de Storefront:** het Weergeven van leveringsramingen op PDP (&quot;krijg het door&quot;), kart (datumwaaier), en controle (per het verschepen methode) gebruikend een gedeelde cliëntmodule.
- **niet-blokkerende UX:** het verzekeren van leveringsramingen blokkeert nooit de koopstroom — de pagina&#39;s geven eerst terug en de ramingen verschijnen asynchroon.

## Volgende stappen

Gebruik de volgende suggesties om uw service voor geschatte leveringstermen uit te breiden:

- **verbind een echte drager API:** vervang het mock met een levende verschepende API zoals UPS, FedEx, of USPS door de sleutel van de Dienst URL en API in [!DNL Admin UI] te veranderen.
- **de anonieme koper van de Steun:** voeg een postcodeinput op PDP en kartpagina&#39;s toe zodat kunnen de kopers die niet het programma worden geopend leveringsramingen ook zien.
- **breidt dragertoewijzingen uit:** voeg meer dragercodes aan `CARRIER_MAP` toe om leveringsdata voor extra het verschepen methodes te tonen.
- **voeg server-zij caching toe:** voer `aio-lib-state` caching in de actie BFF uit om vraag aan externe API voor herhaalde oorsprong en bestemmingsparen te verminderen.
- **toon ramingen in orde bevestiging:** toon de geschatte leveringsdatum op de pagina van de ordesbevestiging en in transactie e-mails.
