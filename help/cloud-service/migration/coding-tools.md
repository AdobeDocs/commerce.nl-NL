---
title: AI-coderingsgereedschappen voor extensies
description: Leer hoe u de AI-gereedschappen gebruikt om Commerce App Builder-extensies te maken.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
role: Developer
hide: true
hidefromtoc: true
source-git-commit: 5dd290a4e10bdbd1f6c96b67ab6c9ba1598705dc
workflow-type: tm+mt
source-wordcount: '1454'
ht-degree: 0%

---

# AI-coderingsgereedschappen voor extensies

Wanneer u naar [!DNL Adobe Commerce as a Cloud Service] migreert, kunt u de AI-coderingsgereedschappen gebruiken om bestaande [!DNL Adobe Commerce] PHP-extensies om te zetten in [!DNL Adobe Developer App Builder] -extensies. Deze kan ook worden gebruikt om nieuwe [!DNL App Builder] extensies te maken.

Het gebruik van de AI-coderingsgereedschappen biedt de volgende voordelen:

* **Verbeterde ontwikkelingswerkschema**: Geïntegreerde de ontwikkelingshulpmiddelen van Adobe Commerce.
* **op AI-Gerichte hulp**: Contextbewuste codegeneratie en het zuiveren.
* **Commerce-specifieke eigenschappen**: Gespecialiseerde hulpmiddelen voor de ontwikkeling van Adobe Commerce App Builder.
* **Geautomatiseerde werkschema&#39;s**: Gestroomlijnde ontwikkeling en plaatsingsprocessen.

## Vereisten

* Een coderende agent, zoals [&#x200B; Cursor &#x200B;](https://cursor.com/download) (geadviseerd), [&#x200B; Kopilot van Github &#x200B;](https://github.com/features/copilot), [&#x200B; Google Gemini CLI &#x200B;](https://github.com/google-gemini/gemini-cli), of [&#x200B; Claude Code &#x200B;](https://www.claude.com/product/claude-code)
* [&#x200B; Node.js &#x200B;](https://nodejs.org/en/download): De versie van LTS
* De Manager van het pakket: [&#x200B; npm &#x200B;](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) of [&#x200B; garen &#x200B;](https://classic.yarnpkg.com/lang/en/docs/install/#mac-stable)
* [&#x200B; Git &#x200B;](https://github.com/git-guides/install-git): Voor bewaarplaats het klonen en versiecontrole

## Installatie

1. Installeer de recentste [&#x200B; CLI van Adobe I/O &#x200B;](https://github.com/adobe/aio-cli) globaal:

   ```bash
   npm install -g @adobe/aio-cli
   ```

1. Installeer de [&#x200B; insteekmodule van Adobe I/O CLI Commerce &#x200B;](https://github.com/adobe-commerce/aio-cli-plugin-commerce):

   ```bash
   aio plugins:install https://github.com/adobe-commerce/aio-cli-plugin-commerce
   ```

1. Kloon de de integratiestarterkit van Commerce [&#x200B; &#x200B;](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/create-integration):

   ```bash
   git clone git@github.com:adobe/commerce-integration-starter-kit.git
   ```

1. Navigeer naar de startmap:

   ```bash
   cd commerce-integration-starter-kit
   ```

1. Installeer de Commerce AI-uitbreidbaarheidsprogramma&#39;s met de interactieve instellingsopdracht:

   ```bash
   aio commerce extensibility tools-setup
   ```

Tijdens het installatieproces worden configuratieopties weergegeven. Kies voor de installatielocatie de optie &quot;Huidige map&quot; om de gereedschappen in de huidige werkruimte te installeren:

```terminal
? Where would you like to setup the tools?
❯ Current directory
  New directory
```

Bij het selecteren van de coderingsagent raadt Adobe aan `Cursor` te selecteren voor de beste ontwikkelervaring:

```terminal
? Which coding agent would you like to use?
❯ Cursor
  Copilot
  Gemini CLI
  Claude Code
```

Als Adobe pakketbeheer selecteert, wordt u aangeraden `npm` te gebruiken voor consistentie:

```terminal
? Which package manager would you like to use?
❯ npm
  yarn
```

1. Nadat de coderingsgereedschappen zijn geïnstalleerd, wordt het installatieproces geconfigureerd:

   * Integratie van MCP-servers voor Adobe Commerce-ontwikkeling
   * Cursor IDE-regels voor verbeterde ontwikkelervaring
   * Commerce-specifieke ontwikkelingsinstrumenten en -workflows

   De volgende bestanden worden toegevoegd aan de werkruimte:

   * MCP-configuratie: `.cursor/mcp.json`
   * Map met regels: `.cursor/rules/`

## Configuratie na installatie

1. Begin winde van de Curseur opnieuw om de nieuwe hulpmiddelen MCP en de configuratie te laden.

1. Controleer de installatie door te bevestigen dat de regels aanwezig zijn in de map `.cursor/rules/` .

1. Schakel de MCP-server in:

   * Open de Montages van de Curseur MCP gebruikend **Cmd+Shift+P** (macOS) of **Ctrl+Shift+P** (Vensters en Linux).
   * Type **Mening: Open Montages MCP**
   * Plaats **handel-rekbaarheid MCP Server** in de lijst
   * Wissel de server **AAN** om de coderingshulpmiddelen toe te laten

1. Verifieer de serverstatus - de uitbreidbaarheid MCP van Commerce zou als moeten verschijnen:

   ```terminal
   Status: Connected/Active
   Server: commerce-extensibility
   Configuration: Automatically configured via .cursor/mcp.json
   ```

## Voorbeeldprompt

Met de volgende voorbeeldprompt wordt een extensie gemaakt voor het verzenden van meldingen wanneer een bestelling wordt geplaatst.

```terminal
Implement an Adobe Commerce SaaS extension that will send an ERP notification when a customer places an order. The ERP notification must be sent as a POST HTTP call to <ERP URL> with the following details in the request JSON body:

Order ID -> orderID
Order Total -> total
Customer Email ID -> emailID
Payment Type -> pType
```

## Aanbevolen procedures

Adobe raadt u aan de volgende aanbevolen procedures toe te passen wanneer u de AI-coderingsgereedschappen gebruikt:

### Checklist

Voordat u een ontwikkelingssessie start:

* Controleren op `REQUIREMENTS.md`
* Controleren of MCP-gereedschappen werken
* Huidige fase en doelstellingen evalueren
* Beginnen met voorbeeldcode of basisprojecten

Tijdens de ontwikkeling:

* Vertrouw het vier-fase [&#x200B; protocol &#x200B;](#protocol)
* Implementatieplannen aanvragen voor complexe ontwikkeling
* MCP-gereedschappen gebruiken indien beschikbaar
* Elke functie na implementatie testen
* Eerst lokaal testen, daarna implementeren en opnieuw testen
* Gebruik de coderingsgereedschappen voor testondersteuning
* Vraag om onnodige complexiteit
* Stapsgewijs implementeren voor snellere ontwikkeling

Bij het starten van nieuwe chat:

* Geef de juiste sessieafhandeling op
* Referentiesleutelbestanden met `@`
* Duidelijke doelen voor de sessie instellen
* Op fasen gebaseerde grenzen gebruiken

### Workflow

Wanneer het ontwikkelen met de AI codeerhulpmiddelen, begin met steekproefcode of gesteven projecten. Deze benadering zorgt ervoor dat u op een stevige stichting bouwt eerder dan van niets te beginnen, terwijl ook het optimaliseren van uw AI ontwikkelingswerkschema.

Hierdoor kunt u ook Adobe-sjablonen gebruiken en bouwen op beproefde patronen en architecturen, terwijl u de bestaande mappenstructuren en conventies behoudt.

Raadpleeg de volgende bronnen om aan de slag te gaan:

* [&#x200B; Startuitrusting van de Integratie &#x200B;](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/create-integration)
* [&#x200B; Adobe Commerce starter kit malplaatjes &#x200B;](https://github.com/adobe/adobe-commerce-samples/tree/main/starter-kit)
* [&#x200B; de aanzetmalplaatjes van Adobe I/O Events &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/io-events/getting-started-io-events)
* [&#x200B; de steekproeftoepassingen van App Builder &#x200B;](https://developer.adobe.com/app-builder/docs/resources/sample_apps)

#### Waarom u deze middelen zou moeten gebruiken

* **Bewezen patronen**: De kits van de aanzet embody Adobe beste praktijken en architecturale besluiten
* **Snellere ontwikkeling**: Vermindert tijd besteed aan boilerplate en configuratie
* **Consistentie**: Verzekert uw uitbreiding gevestigde overeenkomsten volgt
* **Handhaving**: Gemakkelijker om te handhaven en bij te werken wanneer het volgen van standaardpatronen
* **Documentatie**: De kits van de aanzet komen met voorbeelden en documentatie
* **Communautaire steun**: Gemakkelijker om hulp te krijgen wanneer het gebruiken van standaardbenaderingen
* **AI contextefficiency**: Gebruik vertrouwde patronen en structuren om met te werken, verminderend de behoefte aan uitgebreide verklaringen en verbeterend de nauwkeurigheid van de codegeneratie
* **Verminderd symbolisch gebruik**: Verwijzing bestaande patronen in plaats van het produceren van alles van kras, die tot efficiëntere gesprekken en minder contextsamenvattingen leiden

### Protocol

Het volgende vierfaseprotocol wordt automatisch afgedwongen door het regelensysteem. De hulpmiddelen zouden dit protocol automatisch moeten volgen wanneer het ontwikkelen van uitbreidingen:

* Fase 1: Analyse en verduidelijking van de eisen
   * Geef volledige antwoorden op de gestelde vragen om de vragen te verduidelijken.
* Fase 2: Architectuurplanning en goedkeuring door de gebruiker
   * Wanneer u een plan presenteert, moet u het zorgvuldig beoordelen voordat u het goedkeurt.
* Fase 3: Opstellen en uitvoeren van code
* Fase 4: Documentatie en validering

### Implementatieplannen aanvragen voor complexe ontwikkeling

Voor complexe ontwikkeling met meerdere runtimeacties, aanraakpunten of integraties, moet u expliciet vragen dat de AI-gereedschappen een gedetailleerd implementatieplan maken. Wanneer u een plan op hoog niveau in [&#x200B; Fase 2 &#x200B;](#protocol) ziet dat veelvoudige componenten impliceert, vraag om een gedetailleerd implementatieplan om het in handelbare taken neer te breken:

```terminal
Create a detailed implementation plan for this complex development.
```

Complexe Adobe Commerce-extensies hebben vaak betrekking op:

* Meerdere runtimeacties
* De configuratie van de gebeurtenis over veelvoudige touchpoints
* Integratie met externe systemen
* Vereisten inzake staatsbeheer
* Testen op meerdere componenten

### MCP-gereedschappen gebruiken

Het hulpmiddel blijft aan hulpmiddelen MCP in gebreke, maar in bepaalde omstandigheden, kan het bevelen CLI in plaats daarvan gebruiken. Als u MCP hulpmiddelgebruik wilt verzekeren, uitdrukkelijk verzoek hen in uw herinnering.

Als u CLI bevelen ziet die en hulpmiddelen MCP in plaats daarvan willen gebruiken, gebruik de volgende herinnering:

```terminal
Use only MCP tools and not CLI commands
```

* MCP-gereedschappen: aio-app-opstellen, aio-app-dev, aio-dev-invoke
* CLI-opdrachten: implementatie van een AIR-app, ontwikkelen van een AIR-app

CLI de bevelen kunnen voor de volgende scenario&#39;s worden gebruikt:

* Complexe implementatiescenario&#39;s
* Fouten opsporen in specifieke problemen
* Wanneer de hulpmiddelen MCP beperkingen hebben
* Eenmalige verrichtingen die niet van integratie MCP profiteren

### Ontwikkeling

Het is belangrijk om onnodige complexiteit die door de AI-gereedschappen wordt veroorzaakt, in twijfel te trekken.

Wanneer overbodige bestanden worden toegevoegd (`validator.js` , `transformer.js` , `sender.js` ) voor eenvoudige alleen-lezen eindpunten, volgt u de volgende aanwijzingen:

```terminal
Why do we need these files for a simple read-only endpoint?
Perform a root cause analysis before adding complexity
Verify if simpler solutions exist
```

### Testen

Gebruik de volgende aanbevolen procedures bij het testen:

#### Elke functie na implementatie testen

Nadat u de ontwikkeling van een functie in uw implementatieplan hebt voltooid, test u deze onmiddellijk. Het vroege testen voorkomt samengestelde kwesties en maakt het zuiveren gemakkelijker.

* Wacht niet tot alle functies zijn voltooid
* Test incrementeel om problemen vroeg op te vangen
* Functionaliteit valideren voordat u naar de volgende functie gaat

#### Eerst lokaal testen

Altijd eerst lokaal testen met het gereedschap `aio-app-dev` . Dit verstrekt direct terugkoppelt en staat voor snellere iteratiecycli, gemakkelijker het zuiveren, en geen plaatsingsoverheadkosten toe.

1. Start de lokale ontwikkelingsserver:

   ```bash
   aio-app-dev
   ```

1. Handelingen lokaal testen:

   ```bash
   aio-dev-invoke action-name --parameters '{"test": "data"}'
   ```

#### Implementeren en opnieuw testen

Implementeer en test lokale tests in de runtimeomgeving als het lokale testen is gelukt. Runtimeomgevingen kunnen een ander gedrag hebben dan lokale ontwikkeling.

1. Distribueren naar runtime:

   ```bash
   aio-app-deploy
   ```

1. Uitgevoerde acties testen

1. Webbrowser of directe HTTP-aanvragen gebruiken

1. Activeringslogboeken controleren voor foutopsporing

#### Gebruik de coderingsgereedschappen voor testondersteuning

Vraag om hulp bij het testen. De hulpmiddelen kunnen met het zuiveren, logboekanalyse, en het creëren van aangewezen testgegevens voor uw specifieke runtime acties helpen.

**runtime van de Test acties**:

```terminal
Help me test the customer-created runtime action running locally
```

**zuivert mislukkingen**:

```terminal
Why did the subscription-updated runtime action activation fail?
```

**Logboeken van de Controle**:

```terminal
Help me check the logs for the last stock-monitoring runtime action invocation
```

**creeer testlading**:

```terminal
Generate test data for this Commerce event
```

```terminal
Create a test payload for the customer_save_after event
```

**vind runtime eindpunten**:

```terminal
What's the URL for this deployed action?
```

**handvatauthentificatie**:

```terminal
How do I authenticate with this external API?
```

**los** problemen op:

```terminal
Help me debug why this action is returning 500 errors
```

### Foutopsporing

Stoppen en beoordelen wanneer dingen fout gaan. Als er problemen optreden:

* Stoppen en beoordelen - Ga niet door in een gebroken toestand
* Logbestanden controleren - Activeringslogboeken gebruiken om problemen op te sporen
* Vereenvoudigen - Complexiteit verwijderen om problemen te isoleren
* Stapsgewijs testen - Eén probleem tegelijk verhelpen
* Valideren - test elke oplossing voordat u verdergaat

### Implementatie

Gebruik de volgende beste praktijken wanneer het opstellen:

#### Stapsgewijs implementeren

Implementeer alleen gewijzigde acties om de ontwikkeling te versnellen. Hierdoor wordt het risico op een onderbreking van de bestaande functionaliteit beperkt en wordt sneller feedback over wijzigingen gegeven. Het vermindert ook het risico van het breken van bestaande functionaliteit.

* Gebruik hulpmiddelen MCP om specifieke acties op te stellen

  ```bash
  aio-app-deploy --actions action-name
  ```

* Afzonderlijke acties implementeren na lokale tests
* Stapsgewijs implementeren en volledige implementatie van toepassingen tijdens de ontwikkeling vermijden

#### Opschonen van runtime

Na grote wijzigingen kunt u de gereedschappen gebruiken om zwevende handelingen op te schonen. De AI-werktuigen kunnen het schoonmaakproces systematisch afhandelen, ze kunnen op efficiënte wijze de zwevende handelingen identificeren, hun status controleren en ze veilig verwijderen zonder handmatige tussenkomst.

```terminal
Help me identify and clean up orphaned runtime actions
```

Vraag de AI-gereedschappen om geïmplementeerde acties weer te geven en ongebruikte acties te identificeren

```terminal
List all deployed actions and identify which ones are no longer needed
```

AI-gereedschappen de zwevende handelingen laten verwijderen met de juiste opdrachten

```terminal
Remove the orphaned actions that are no longer part of the current implementation
```

### Toezicht

Gebruik de volgende aanbevolen procedures voor het controleren van uw toepassing:

#### Controle op contextkwaliteitsindicatoren

* **Goede context**: AI herinnert recente besluiten, verwijzingen correcte dossiers
* **Arme context**: AI vraagt om eerder verstrekte info, herhaalt opgeloste kwesties

#### Snelheid voor spoorontwikkeling

* **Hoge snelheid**: Duidelijke vooruitgang, minimale verduidelijking nodig
* **Lage snelheid**: Herhaalde verklaringen, AI verwarring, langzame vooruitgang

#### Kostenefficiëntie bewaken

Gebruikspatronen voor token bijhouden:

* **Efficiënt**: Laag symbolisch gebruik, weinig contextsamenvattingen
* **Inefficiënt**: Hoog symbolisch gebruik, veelvoudige samenvattingen, herhaald werk

## Wat te vermijden

Gebruik de AI-coderingsgereedschappen om de volgende antipatronen te vermijden:

* **overslaat niet de verklaringsfase** - altijd verzekert Fase 1 vóór implementatie wordt voltooid.
* **slaat het testen na elke eigenschap** niet over - test incrementeel, wacht niet tot alles volledig is.
* **voeg geen ingewikkeldheid zonder de analyse van de worteloorzaak toe** - vraag onnodige dossiertoevoegingen en verzoek behoorlijk onderzoek.
* **verklaart geen succes zonder echte gegevens het testen** - altijd test met daadwerkelijke gegevens, niet enkel randgevallen.
* **vergeet runtime schoonmaakbeurt** niet - schoon altijd orphaned acties na belangrijke veranderingen.
