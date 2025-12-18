---
title: Documentatie-RAG-service
description: Leer hoe u de zoekservice voor documentatie van AI kunt gebruiken voor Adobe Commerce-ontwikkeling.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
role: Developer
hide: true
hidefromtoc: true
source-git-commit: 28396828516645abec3b42a2c6874afe9134dfb8
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---

# Documentatie RAG-service (Beta)

>[!NOTE]
>
>De documentatie-RAG-service bevindt zich momenteel in Beta en de ervaring kan worden gewijzigd.

De documentatie-RAG-service (Retrieval-Augmented Generation) biedt semantische zoekmogelijkheden van AI in alle relevante documentatie van Adobe Commerce en App Builder.

Deze RAG verstrekt een interface van winde voor het stellen van vragen over Adobe Commerce en kan u adviseren over beste praktijken voor het ontwikkelen van toepassingen en andere migratietaken.

De dienst van RAG maakt deel uit van de [&#x200B; de rekbaarheidshulpmiddelen van Commerce &#x200B;](./coding-tools.md) MCP (ModelProtocol van de Context) server, die met Cursor en andere MCP-compatibele AI medewerkers integreert.

## Beschikbare documentatie

De volgende lijst beschrijft welke documentatie momenteel door de dienst van RAG wordt geïndexeerd, en de sleutelwoorden u kunt gebruiken om het zoeken van de bijbehorende index teweeg te brengen. De bijgevoegde documentatie zal verder worden uitgebreid naarmate we de RAG-dienst ontwikkelen.

| Categorie | Index | Inhoud inbegrepen | Trefwoorden |
|-------|---------|---------|------------------------|
| [&#x200B; Storefront &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL) | commerce-storefront-doc | Edge Delivery Services, drop-ins, storefront componenten | winkel, drop-in, EDS, productaanbieding, kassa |
| [&#x200B; Uitbreidbaarheid &#x200B;](https://developer.adobe.com/commerce/extensibility/) | handel-rekbaarheid-documenten | Webhaken, gebeurtenissen, extensies, integratie | webhaak, gebeurtenis, extensie, API-net, GraphQL |
| [&#x200B; Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/cloud-service/overview) | commerce-core-docs | Core Commerce (catalogus, klanten, bestellingen) | catalogus, product, klant, bestelling, voorraad |
| [&#x200B; App Builder &#x200B;](https://developer.adobe.com/app-builder/docs/intro_and_overview/) | app-builder-docs | App Builder, handelingen bij uitvoering, UI-extensies | app builder, runtime actie, React Spectrum |

Voor meer informatie over indexselectie, verwijs naar [&#x200B; Automatische indexselectie &#x200B;](#automatic-index-selection-recommended) en [&#x200B; Expliciete indexselectie &#x200B;](#explicit-index-selection).

Voor gedetailleerde informatie over de documentatie inbegrepen in elke index, verwijs naar [&#x200B; ingebedde bronlijst &#x200B;](https://github.com/adobe-commerce/azure-commerce-documentation-agent/blob/develop/docs/INGESTED_SOURCES.md).

## Veiligheid en privacy

* **IMS authentificatie** - Alle API vraag gebruikt de tokens van Adobe IMS OAuth2.
* **Geen gegevensopslag** - de server MCP slaat geen geloofsbrieven of gegevens op.
* **Lokale uitvoering** - alle hulpmiddelen lopen plaatselijk op uw machine.
* **Veilige mededeling** - het onderzoek van de Documentatie gebruikt HTTPS met symbolische bevestiging.

Het productieeindpunt wordt beschermd door [&#x200B; Azure Voorste Door &#x200B;](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview), die de volgende bescherming omvat:

* Web Application Firewall (WAF) met Microsoft Default RuleSet 2.1 en Bot Manager RuleSet 1.0
* Geoblokkering voor door de VS verboden gebieden (Cuba, Iran, Noord-Korea, Syrië, Krim, Luhansk, Donetsk)
* DoS-beveiliging aan de rand
* API-beheerbackend vergrendeld om alleen verkeer van de voordeur te accepteren

Voor verschillende veiligheidseisen, kunt u een douaneeindpunt gebruiken. Zie [&#x200B; Eigen Voorste eindpunt van de Deur van de Douane &#x200B;](#custom-front-door-endpoint) voor meer informatie.

## Vereisten

Controleer voordat u gaat installeren of:

* [&#x200B; Node.js &#x200B;](https://nodejs.org/en/download){target="_blank"} 18+ (Aanbevolen LTS)
* [&#x200B; winde van de Curseur &#x200B;](https://cursor.com/download){target="_blank"} (geadviseerd) of een andere MCP-compatibele winde

  >[!NOTE]
  >
  >Terwijl andere MCP-compatibele IDEs wordt gesteund, is de Cursor geadviseerde winde voor de beste ervaring. Als u een andere winde gebruikt, zult u de herinneringen en andere stappen in de documentatie moeten wijzigen om met uw geselecteerde winde te werken.

## Installatie

1. Installeer [&#x200B; CLI van Adobe I/O &#x200B;](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) globaal:

   ```bash
   npm install -g @adobe/aio-cli
   ```

1. Verifiëren met Adobe IMS:

   ```bash
   aio auth login
   ```

1. Clone the Commerce rekability tools repository and navigate to the directory:

   ```bash
   git clone https://github.com/adobe-commerce/commerce-extensibility-tools.git
   cd commerce-extensibility-tools
   ```

1. Afhankelijkheden installeren:

   ```bash
   npm install
   ```

1. Maak of werk `.cursor/mcp.json` bij in uw Commerce-projectmap (niet globaal) om de `commerce-extensibility-tools` MCP-server op te nemen:

   ```json
   {
     "mcpServers": {
       "commerce-extensibility-tools": {
         "command": "node",
         "args": [
           "/<your-project-directory>/commerce-extensibility-tools/index.js"
         ],
         "env": {
           "NODE_ENV": "production"
         }
       }
     }
   }
   ```

   Vervang `<your-project-directory>` door het werkelijke pad waar u de opslagplaats hebt gekloond.

   >[!NOTE]
   >
   >Op Vensters, als u kwesties met het verstrekken van de weg aan uw projectfolder ontmoet, verwijs naar [&#x200B; de kwesties van de Weg oplossen van problemen &#x200B;](#path-issues-windows).

1. Start de IDE van de cursor opnieuw om de MCP-server te laden.

1. Controleer de installatie door de AI-assistent te vragen:

   ```shell-session
   Can you show me the available Adobe Commerce tools?
   ```

## Gebruik

Zodra geïnstalleerd, kunt u de indexen [&#x200B; automatisch roepen &#x200B;](#automatic-index-selection-recommended) of [&#x200B; uitdrukkelijk &#x200B;](#explicit-index-selection). U kunt ook [`/search-commerce-docs` bevel &#x200B;](#command-based-search) gebruiken.

>[!NOTE]
>
>De RAG-service retourneert de vijf belangrijkste resultaten.

### Automatische indexselectie (aanbevolen)

Door vragen te stellen over de natuurlijke taal van uw Commerce-project, zoekt het programma automatisch naar de juiste documentatieindex en verstrekt het relevante informatie:

>[!BEGINSHADEBOX]

Met de volgende prompt wordt automatisch de `commerce-storefront-docs` -index geselecteerd:

```shell-session
"How do I use Edge Delivery Services drop-ins for product listing?"
```

Met de volgende prompt wordt automatisch de `commerce-extensibility-docs` -index geselecteerd:

```shell-session
"How do I create a webhook in Adobe Commerce?"
```

Met de volgende prompt wordt automatisch de `commerce-core-docs` -index geselecteerd:

```shell-session
"How to configure product catalog settings?"
```

Met de volgende prompt wordt automatisch de `app-builder-docs` -index geselecteerd:

```shell-session
"What are App Builder runtime action best practices?"
```

>[!ENDSHADEBOX]

### Expliciete indexselectie

U kunt ook de index opgeven die u wilt gebruiken in de vraag.

```shell-session
Search commerce-storefront-docs for authentication drop-in
```

```shell-session
Using app-builder-docs, how do I deploy runtime actions?
```

### Op opdrachten gebaseerde zoekopdracht

Als u er zeker van wilt zijn dat de RAG-service wordt gebruikt, kunt u de opdracht `/search-commerce-docs` Cursor handmatig aanroepen om de documentatie met uw vraag te doorzoeken:

```shell-session
/search-commerce-docs "How do I subscribe to Commerce events?"
```

## Aangepast eindpunt voorzijde

Door gebrek, gebruikt het documentonderzoek het productie [&#x200B; Azure Front Door &#x200B;](https://learn.microsoft.com/en-us/azure/frontdoor/front-door-overview) eindpunt met de bescherming van WAF. Voor test- of ontwikkelingsdoeleinden kunt u dit overschrijven met de omgevingsvariabele `FRONT_DOOR_URL` .

Om een douaneeindpunt te gebruiken, voeg het aan uw Configuratie van de Curseur MCP toe:

```json
{
  "mcpServers": {
    "commerce-extensibility-tools": {
      "command": "node",
      "args": ["/<your-project-directory>/commerce-extensibility-tools/index.js"],
      "env": {
        "NODE_ENV": "production",
        "FRONT_DOOR_URL": "https://<custom-endpoint>.azurefd.net"
      }
    }
  }
}
```

>[!NOTE]
>
>De meeste ontwikkelaars moeten het standaardeindpunt van de productie gebruiken en hoeven de variabele `FRONT_DOOR_URL` niet in te stellen.

## Problemen oplossen

De volgende secties verstrekken het oplossen van problemenuiteinden voor gemeenschappelijke kwesties u kon ontmoeten wanneer het gebruiken van de documentatieRAG dienst.

### Verificatiefouten

Voor het zoeken naar documentatie is Adobe IMS-verificatie vereist. Als u verificatiefouten tegenkomt, gebruikt u de volgende stappen om het probleem op te lossen en op te lossen.

1. Controleren of u bent aangemeld:

   ```bash
   aio where
   ```

1. Controleer of u de IMS-token kunt zien:

   ```bash
   aio auth login --bare
   ```

1. Als de authentificatiefouten voortduren, probeer het programma openen en terug in:

   ```bash
   aio auth logout
   aio auth login
   ```

### MCP-server wordt niet geladen

Als de server MCP verbindt, of uw agent zegt het niet met RAG kan verbinden, gebruik de volgende stappen om de kwestie problemen op te lossen en op te lossen.

1. Open de Montages van de Curseur gebruikend **Cmd,** (macOS) of **CTRL,** (Vensters en Linux).

1. Zoek naar &quot;MCP&quot;en verifieer dat `commerce-extensibility-tools` vermeld en toegelaten is.

1. Controleer op foutberichten in het MCP-instellingenvenster.

1. Controleer of het bestand `mcp.json` bestaat in uw project:

   ```bash
   cat .cursor/mcp.json
   ```

1. Controleer of het pad juist en absoluut is:

   ```bash
   ls -la /<your-project-directory>/commerce-extensibility-tools/index.js
   ```

### Gereedschap niet gevonden

1. Sluit de cursor en open deze opnieuw.

1. Controleer de MCP serverlogboeken in de ontwikkelaarsconsole van de Cursor door **Cmd+Shift+P** (macOS) of **Ctrl+Shift+P** (Vensters/Linux) te gebruiken en het zoeken naar &quot;Ontwikkelaar: Open Omslag van Logs&quot;.

1. Controleer de installatie:

   ```bash
   cd commerce-extensibility-tools
   npm install
   node index.js
   ```

   De server moet zonder fouten starten.

### Padproblemen (Windows)

In Windows gebruikt u slashes `/` of backslashes met escape-teken `\\` :

```json
{
  "args": ["C:/Users/yourname/projects/commerce-extensibility-tools/index.js"]
}
```

```json
{
  "args": ["C:\\Users\\yourname\\projects\\commerce-extensibility-tools\\index.js"]
}
```

## Aanvullende bronnen

* [&#x200B; de ontwikkelaarsdocumentatie van Adobe Commerce &#x200B;](https://developer.adobe.com/commerce/docs/){target="_blank"}
* [&#x200B; documentatie van App Builder &#x200B;](https://developer.adobe.com/app-builder/docs/){target="_blank"}
* [&#x200B; ModelContext Protocol &#x200B;](https://modelcontextprotocol.io/){target="_blank"}
* [&#x200B; IDE van de Curseur &#x200B;](https://cursor.sh/docs){target="_blank"}
