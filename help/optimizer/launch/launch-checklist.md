---
title: Checklist starten
description: Leer hoe te om configuratie, storefront, SEO, CDN, integratie, veiligheid, analyses, en het testen voor  [!DNL Adobe Commerce Optimizer]  productie te bevestigen.
solution: Commerce
feature: Integration, Storefront, Search, Catalog Management, Personalization
feature-set: Commerce
role: Admin, Developer
level: Intermediate
topic: Administration
recommendations: noCatalog
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is op Adobe Commerce as a Cloud Service en  [!DNL Adobe Commerce Optimizer]  slechts projecten (Adobe-Beheerde infrastructuur SaaS) van toepassing."
source-git-commit: 37b8b8a334ca11daacfd3da03b0441e77329e2e1
workflow-type: tm+mt
source-wordcount: '1940'
ht-degree: 0%

---


# Checklist starten

Gebruik deze checklist om te verifiëren dat uw productie [!DNL Adobe Commerce Optimizer] project wordt gevormd, getest, en klaar voor lancering. Werk door elke sectie met uw team en volg voltooiing in uw eigen projectplan of tracker. Voor productmogelijkheden en UI gebieden die hieronder van verwijzingen worden voorzien, zie de [[!DNL Adobe Commerce Optimizer]  documentatie &#x200B;](../overview.md).

## Hoofdletters en architectuur gebruiken {#use-case}

Gebruik deze controlelijst wanneer u een B2C-ervaring levert die [!DNL Adobe Commerce Optimizer] en Edge Delivery Services (EDS) combineert met een bestaande Adobe Commerce op Cloud-instantie.

Uw oplossing omvat typisch deze componenten:

- **wolk** - Adobe Commerce op Cloud beheert catalogusgegevens, klanten, activa, en koopstromen (controle, ordebeheer, het verschepen, etc.).
- **Optimizer** - [!DNL Adobe Commerce Optimizer] levert merchandising ervaringen.
- **Storefront** - Adobe Commerce Storefront op Edge Delivery Services verstrekt UI.
- **de diensten van de Derde** - Betaling, verschepen, en belastingleveranciers.
- **App Builder** - Uitbreidbaarheid.
- **API Net** - verzoek verpletterend.

## Adobe Commerce verifiëren op Cloud {#verify-cloud}

Bevestig dat uw Adobe Commerce op Cloud-omgeving gereed is voor productie.

▢ De instantie van de Wolk is [&#x200B; provisioned &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/start/new-project).
▢ Testgegevens en dummygegevens worden uit de instantie verwijderd.
▢ Productiegegevens worden op de instantie geladen.
▢ u kent het [&#x200B; eindpunt van GraphQL &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/).
▢ de instantie voldoet aan [&#x200B; klaar-voor-lancerings &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/launch/checklist) vereisten.

## Commerce Optimizer-exemplaar verifiëren {#verify-optimizer}

Controleer of de productie-instantie van [!DNL Adobe Commerce Optimizer] correct is ingesteld.

▢ De productie-instantie is actief. Zie [&#x200B; begonnen worden &#x200B;](../get-started.md) voor hoe u het voorziet.
▢ De instantie bevindt zich in het juiste gebied.
▢ Het omgevingstype is Production.
▢ U kent de organisatie-id, client-id, invoer-URL en Commerce Optimizer-URL. Zie [&#x200B; begonnen worden &#x200B;](../get-started.md).
▢ De geconfigureerde limieten en grenzen komen overeen met de waarden die zijn bevestigd door uw Adobe Customer Technical Advisor (CTA).
▢ Testartefacten en dummygegevens zijn uit de instantie verwijderd.

## Opslagsite verifiëren {#verify-storefront-site}

Bevestig dat uw Edge Delivery Services-winkelsite bestaat en dat de toegang beperkt is.

▢ De storefront-site bestaat. Zie [&#x200B; een storefront &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/?lang=nl-NL) creëren.
▢ U kent de sitenaam.
▢ slechts hebben de gemachtigde mensen [&#x200B; toestemming om &#x200B;](https://tools.aem.live/tools/user-admin/index.html) te publiceren.
▢ slechts hebben de gemachtigde mensen [&#x200B; toestemming aan auteur &#x200B;](https://docs.da.live/administrators/guides/permissions).

## Integratie van Cloud en Optimizer controleren {#cloud-optimizer-integration}

Controleer of Adobe Commerce op Cloud en [!DNL Adobe Commerce Optimizer] gegevens correct uitwisselen.

### Op Adobe Commerce

Voltooi deze controles in uw Cloud-project.

▢ De schakelaar van Commerce Optimizer wordt [&#x200B; geïnstalleerd en gevormd &#x200B;](../../aco-connector/get-started.md).
▢ De opdracht `aco:conf:show` CLI bevestigt de verbinding met de productie-Commerce Optimizer-instantie. De organisatie-id, de client-id, de invoer-URL en de Commerce Optimizer-URL komen overeen met de productie.
▢ het werkingsgebied van de Synchronisatie in [&#x200B; configuratie van de Uitvoer &#x200B;](../../aco-connector/get-started.md) past uw vereisten aan.
▢ [&#x200B; de status van de het voedersynchronisatie van Gegevens &#x200B;](../../aco-connector/get-started.md) bevestigt gegevensuitvoer van de instantie van de Wolk.

### In Commerce Optimizer

Voltooi deze controles in [!DNL Adobe Commerce Optimizer] UI.

▢ het [&#x200B; dashboard van de gegevenssynchronisatie &#x200B;](../setup/data-sync.md) toont ontvangen gegevens. Er worden producten, prijzen en kenmerken weergegeven voor Catalogusservice, Productdetectie en Aanbevelingen.
▢ {de boeken van 1} Prijs [&#128279;](../setup/pricebooks.md) worden auto-gecreeerd van klantengroepen op Wolk.

▢ [&#x200B; de meningen van de Catalogus &#x200B;](../setup/catalog-view.md) bestaan en u kent hun IDs.
▢ [&#x200B; Beleid &#x200B;](../setup/policies.md) bestaat en u kent hun IDs.
▢ [&#x200B; Facets &#x200B;](../merchandising/facets/overview.md) worden gevormd.
▢ [&#x200B; Synoniemen &#x200B;](../merchandising/synonyms/overview.md) worden gevormd.
▢ [&#x200B; Merchandising de regels &#x200B;](../merchandising/rules/overview.md) worden gevormd.
▢ [&#x200B; de facetten van de Prijs en onderzoekstaal &#x200B;](../settings.md) passen uw vereisten aan wanneer u die eigenschappen gebruikt.
▢ [&#x200B; de aanbevelingen van het Product &#x200B;](../merchandising/recommendations/create.md) bestaan en gedraagt zich zoals verwacht in voorproef.
▢ {de prestatiegegevens van 1} Onderzoek [&#x200B; verschijnt in &#x200B;](../manage-results/search-performance.md) Admin *.*
▢ {de prestatiegegevens van 1} Aanbevelingen [&#x200B; verschijnen in &#x200B;](../manage-results/recommendation-performance.md) Admin *.*

## Integratie van winkel en cloud controleren {#storefront-cloud-integration}

Bevestig dat de storefront van het correcte eindpunt van Adobe Commerce GraphQL leest.

### Op Adobe Commerce

▢ de verenigbaarheidspakketten van de Storefront zijn [&#x200B; geïnstalleerd &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/storefront-compatibility/install/?lang=nl-NL).

### In de winkel

▢ storefront `commerce-core-endpoint` het plaatsen richt aan uw [&#x200B; eindpunt van GraphQL van de Wolk &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/commerce-configuration/?lang=nl-NL).
▢ Als u API-net gebruikt als een proxy voor Cloud GraphQL, verwijst `commerce-core-endpoint` naar het eindpunt van het API-net in plaats van naar het eindpunt van Cloud GraphQL.

## Integratie van storefront en Optimizer controleren {#storefront-optimizer-integration}

Bevestig Commerce Optimizer-instellingen in de storefront-configuratie.

▢ Uw storefront gebruikt de correcte [&#x200B; montages van Commerce Optimizer &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/commerce-configuration/?lang=nl-NL).
▢ `adobe-commerce-optimizer` is `true`
▢ `commerce-endpoint` verwijst naar het Commerce Optimizer GraphQL-eindpunt van de productie of naar het API-neteindpunt wanneer u API-net gebruikt.
▢ `headers.cs.AC-view-ID` bevat de catalogusweergave-id van uw Commerce Optimizer-instantie voor productie.

## Services van derden op de cloud controleren {#third-party-services}

Bevestig integraties die op uw systeem van de gastheerhandel (niet in [!DNL Adobe Commerce Optimizer]) lopen.

▢ **Betalingen:** de gateway van de betaling is levend en getest (Stripe, PayPal, Adyen, etc.).
▢ **die:** verschepen API verbindingen werken (UPS, FedEx, etc.).
▢ **Verschepend:** het platform van de Afhandeling wordt verbonden en getest (bijvoorbeeld, ShipStation).
▢ **Belasting:** de integratie van de belastingberekening wordt bevestigd (Avalara, TaxJar, etc.).
▢ **Belasting:** de software van de Boekhouding synchroniseert de werken (QuickBooks, etc.).
▢ **Overzicht:** PIM, ERP, of de integratie van het inventarisbeheer wordt getest en synchroniseert.
▢ **Architectuur:** het systeem van de gastheerhandel behandelt betaling, het verschepen, de belasting, en inventaris (niet [!DNL Adobe Commerce Optimizer]).
▢ **Architectuur:** API Net en App Builder blijven synchroon tussen het systeem van de gastheerhandel en [!DNL Adobe Commerce Optimizer].
▢ **E-mail:** de Transactionele werken van de e-maillevering (ordesbevestiging, verschepen, etc.).
▢ **E-mail:** De malplaatjes van de e-mail passen uw merk aan en gebruiken correcte verbindingen.

## App Builder- en API-net verifiëren {#app-builder-mesh}

Bevestig rekbaarheidsconfiguratie voor productie.

### App Builder

▢ De werkruimte voor productie bevat alle vereiste configuraties en services.
▢ De productie-app voert het testen door in verschillende buildscenario&#39;s.
▢ de grenzen en de grenzen van het Product zijn herzien en bevestigd gebaseerd op de [&#x200B; het productbeschrijving van Adobe Developer App Builder &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-developer-app-builder.html){target="_blank"} en [&#x200B; het systeemmontages en beperkingen van App Builder &#x200B;](https://developer.adobe.com/app-builder/docs/guides/runtime_guides/system-settings){target="_blank"}.
▢ De productie-app gebruikt eindpunten voor App Builder-productie.
▢ het paneeluitbreidingen van Admin van de Douane *worden opgesteld aan de werkruimte van de productie.*

### API-net

▢ Configuraties en bronnen zijn klaar voor productie.

### Gebeurtenissen

▢ Adobe I/O Events wordt geconfigureerd en abonnementen worden gecontroleerd.

## Afwerking van de storefront {#finalize-storefront}

Poolse inhoud, SEO, prestaties, veiligheid, en gedrag CDN vóór lancering.

### Inhoud en ontwerpen

Bevestig de ontwerpworkflow en de opslagcomponenten.

▢ De [&#x200B; AEM/EDS go-live controlelijst &#x200B;](https://www.aem.live/docs/go-live-checklist) controle is volledig.
▢ De publicatiebron is een op documenten gebaseerde of Universal Editor (en geconfigureerd).
▢ Inhoud wordt gepubliceerd met behulp van de voorvertoning → publicatiecyclus.
▢ De QA voor inhoud en ontwerp is voltooid op het `.aem.live` -domein.
▢ Een favicon wordt correct geconfigureerd en aangeboden door de site.
▢ da.live en product visuals gebruiken [&#x200B; gevormde &#x200B;](https://docs.da.live/administrators/guides/permissions) specifieke geloofsbrieven.
▢ drop-ins (kar, controle, PDP, PLP, auth, rekening) worden [&#x200B; aangepast &#x200B;](../storefront.md) en getest.
▢ In de Storefront-branding worden CSS-ontwerptokens, -typografie en -kleuren weerspiegeld.

### SEO en indexering

Bevestig meta-gegevens, URLs, en kruipt gedrag.

▢ Metagegevens over documenttitels zijn aanwezig voor belangrijke pagina&#39;s (met name PDP&#39;s en PLP&#39;s). Zie {meta-gegevens van 0} SEO [&#x200B; in de &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/seo/metadata/?lang=nl-NL){target="_blank"} documentatie van Adobe Commerce Storefront _._
▢ PDPs omvat [&#x200B; meta-gegevens en gestructureerde gegevens &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/seo/metadata/?lang=nl-NL){target="_blank"} (bijvoorbeeld, JSON-LD).
▢ De product-URL-indelingen zijn consistent (bijvoorbeeld `domain/product-name` ).
▢ Vanity URLs leidt naar canonieke URLs om.
▢ Het project bevat `robots.txt` . Hiermee kunt u waar nodig indexeren, verwijzingen naar sitemaps en blokken paden die u niet wilt indexeren (bijvoorbeeld `/drafts` ).
▢ [&#x200B; richt &#x200B;](https://www.aem.live/docs/redirects) dossiers omleiden behandelt veranderingen URL van migratie (bijvoorbeeld, na het verwijderen `.html`).
▢ Sitemap bestaat en wordt naar wens naar de Google Search Console verzonden.
▢ Canonieke URL&#39;s retourneren `2xx` status (niet `3xx` of `4xx`).
▢ Meerdere sites bevatten `hreflang` -tags in de sitemap.
▢ Het dekkingsrapport van de Google Search Console is actueel.

### Pre-rendering

Bevestig rendering op de server waar u deze inschakelt.

▢ Voorrendering is ingeschakeld voor sleutelpagina&#39;s. Zie [&#x200B; pre-teruggeven voor AEM &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/aem-prerender/?lang=nl-NL){target="_blank"} in _Adobe Commerce Storefront_ documentatie.
▢ URL&#39;s gebruiken kleine letters, zodat koppelingen niet worden verbroken bij het renderen vóór het renderen.
▢ HTML-bron bevat metagegevens en inhoud van het lichaam die de werking van pre-rendering bevestigen.
▢ Landinstellingen tonen waar van toepassing de juiste vertaalde pagina&#39;s.
▢ De extra prijsverhoging van HTML wordt [&#x200B; gevormd &#x200B;](https://www.aem.live/docs/redirects) zoals nodig.

### Prestaties en toezicht

Bevestig prestatiesbasislijnen en analytische bedrading.

▢ Uw opslag volgt [&#x200B; prestaties beste praktijken &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/performance/?lang=nl-NL){target="_blank"} in de _documentatie van Adobe Commerce Storefront_.
▢ (Optioneel) Google Analytics en Google-tagbeheer zijn geconfigureerd.
▢ [&#x200B; de gebeurtenissen van de Storefront &#x200B;](https://github.com/adobe/commerce-events/tree/main/examples/events/snowplow-debugger) implementatie is geldig en de gegevens verschijnen in uw [!DNL Live Search] en [!DNL Product Recommendations] dashboards in Adobe Commerce *Admin*.
▢ de `environment` analyseparameter in [&#x200B; configuratie van Commerce &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/commerce-configuration/?lang=nl-NL){target="_blank"} is `"Testing"` tijdens ontwikkeling en `"Production"` bij go-live. Zie [&#x200B; instrumentatie van Analytics &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/analytics/instrumentation/?lang=nl-NL){target="_blank"}.
▢ Lighthouse-scores voldoen aan uw doelen (bijvoorbeeld `100` op sleutelpagina&#39;s) op basis van de richtlijnen in dit onderwerp.

### Beveiliging en toegang

Bevestig toestemmingen en geheimen.

▢ De juiste machtigingen zijn geconfigureerd voor DA-inhoud en EDS-sites. Zie [&#x200B; toestemmingen DA.live en &#x200B;](https://da.live/docs/administration/permissions) de opstelling van de Authentificatie voor creatie [&#128279;](https://www.aem.live/docs/authentication-setup-authoring).

▢ De integratie van de productafbeeldingen is voorzien. Zie [&#x200B; het toegangsoverzicht van de Dienst van de Wolk AEM &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/accessing/overview#).
▢ Koppelingen voor het opnieuw instellen van wachtwoorden in e-mailsjablonen komen overeen met de Edge Delivery Services-instellingen. Zie de veelgestelde vragen over de winkel: [&#x200B; wat moet ik doen als de koppelingen van mijn e-mailsjabloon zijn verbroken na het migreren naar Edge Delivery Services of Helix?](https://experienceleague.adobe.com/developer/commerce/storefront/troubleshooting/faq/?lang=nl-NL#what-should-i-do-if-my-email-template-links-are-broken-after-migrating-to-edge-delivery-services-or-helix){target="_blank"}.
▢ Er zijn productiesleutels voor integratie en betalingsproviders.
▢ Domeinen zijn op de lijst met gewenste personen staan en achterste webhaken werken.

### CDN en caching

Bevestig CDN, DNS, en geheim voorgeheugengedrag.

▢ De CDN-configuratie gebruikt het GraphQL-eindpunt voor de productie (`yourproject.com/graphql` ) voor Sidekick-extensies en -scripts (bijvoorbeeld sitemap-generatie en de imageimporter).
▢ wanneer u snel Adobe Commerce gebruikt, is een CDN ontruimingstoken beschikbaar en [&#x200B; de plaatsconfiguratie &#x200B;](https://tools.aem.live/tools/cdn-setup/index.html) omvat `authToken` en `serviceId`.
▢ [&#x200B; CDN configuratie &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/content-delivery-network/?lang=nl-NL){target="_blank"} bevestigt caching en ongeldigmaking.
▢ voor [&#x200B; multi-store montages &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/seo/indexing/?lang=nl-NL#multi-store-setups){target="_blank"}, omvatten de Dienst van de Catalogus en [!DNL Live Search] verzoeken een store-specific geheim voorgeheugenbuster (bijvoorbeeld, een vraagparameter of CDN regel).
▢ De functie voor pushvalidatie werkt van begin tot eind (publiceer een wijziging en controleer deze vervolgens op het productiedomein).
▢ DNS TTL is laag genoeg vóór bedekken.
▢ DNS A en CNAME verslagen zijn correct voor alle domeinen en hostnames.
▢ Het SSL/TLS-certificaat is ingericht en geverifieerd voor het productiedomein.
▢ `www` en apex worden omgeleid.

## Beveiliging en naleving {#security-compliance}

Bevestig beveiligingspositie en compatibiliteitstaken.

▢ **SSL:** Een vertrouwd op SSL/TLS- certificaat wordt geïnstalleerd.
▢ **SSL:** HTTPS wordt afgedwongen plaats-breed.
▢ **Toegang:** Standaard *Admin* wachtwoorden worden veranderd en een sterk wachtwoordbeleid is op zijn plaats. Zie [!DNL Adobe Commerce Optimizer] [&#x200B; Gebruiker en identiteitsbeheer &#x200B;](../user-management.md).
▢ **Toegang:** *Admin* URL is niet het gebrek.
▢ **Toegang:** de authentificatie met twee factoren wordt toegelaten voor alle *Admin* gebruikers.
▢ **Toegang:** Geen inactieve of ongebruikte gebruikers Admin worden geassocieerd met het project.
▢ **Firewall:** de Firewall van de Toepassing van het Web (WAF) wordt gevormd en geverifieerd.
▢ **PCI:** de penetratietests van de Veiligheid op productie (het werkingsgebied PCI) is volledig.
▢ **Scannen:** het Hulpmiddel van het Scannen van de Veiligheid van Adobe wordt geregistreerd en een eerste aftasten is volledig.
▢ **Toegang:** CORS staat slechts goedgekeurde oorsprong toe.
▢ **Naleving:** het [&#x200B; gedeelde verantwoordelijkheidsmodel &#x200B;](../shared-responsibility.md) voor [!DNL Adobe Commerce Optimizer] is bijgewerkt en bepaalt duidelijk Adobe tegenover klantenverantwoordelijkheden.
▢ **Naleving:** het beleid van de Privacy, koekjestoestemming, en GDPR of CCPA vereisten worden geverifieerd.

## Analyse en bewaking {#analytics-monitoring}

Maatregel en basislijnen bevestigen.

▢ **RUM:** de Echte Controle van de Gebruiker (RUM) is van instrumenten voorzien voor pre-en-na vergelijking.
▢ **Analytics:** de gegevensinzameling van Adobe Experience Platform wordt gevormd (als toepasselijk).
▢ **Analytics:** verifieerde dat de markeringen MarTech op productie hostname in brand steken.
▢ **Analytics:** de analyses van de Basislijn zijn gedocumenteerd; de schommelingen van de post-lancering (paginameningen, stuittarief, etc.) worden verwacht.
▢ **Gebeurtenissen:** het volgen van de Omzetting werkt eind aan eind (voeg aan wagentje toe → controle → bevestiging).

## Testen {#testing}

Kwaliteit vóór en na het starten bevestigen.

▢ **Functioneel:** de stromen van de Kern werken eind aan eind: doorblader → onderzoek → filter toevoegen aan wortel → checkout → rekeningsverwezenlijking.
▢ **Functioneel:** De gateways van de betaling keuren echte en testtransacties goed.
▢ **Functioneel:** de plaatsing van de Orde, bevestigingsmail, en het werk van het orde volgen.
▢ **Functioneel:** de verschepende opties en de belastingberekeningen zijn nauwkeurig.
▢ **Functioneel:** Coupons, kortingen, en loyaliteitsprogramma&#39;s gedragen zich zoals verwacht.
▢ **UAT:** het acceptatietesten van de Gebruiker is volledig op het opvoeren en de productie.
▢ **Prestaties:** De lading en de stress testen zijn volledig en Adobe CTA of CSE heeft de resultaten.
▢ **Prestaties:** de ladingstijd van de pagina is minder dan drie seconden op Desktop en mobiel.
▢ **Prestaties:** de cijfers van de Lighthouse ontmoeten doelstellingen op zeer belangrijke pagina&#39;s (bijvoorbeeld, via Inzichten PageSpeed).
▢ **Prestaties:** de Beelden, de manuscripten, en de activa worden geoptimaliseerd.
▢ **Verenigbaarheid:** Chrome, Firefox, Safari, en Edge gedragen zich zoals verwacht.
▢ **Verenigbaarheid:** de Responsieve lay-outs werken aan mobiel, tablet, en Desktop.
▢ **Verenigbaarheid:** de Prestaties zijn aanvaardbaar op 3G, 4G, en WiFi.
▢ **Toegankelijkheid:** een toegankelijkheidscontrole is volledig (WCAG, het schermlezer, toetsenbordnavigatie).
▢ **Functioneel:** een post-lancering 404 controleplan is op zijn plaats.
▢ **UAT:** Een terugdraaiingsplan bestaat en gaat het testen over als de lanceringskwesties voorkomen.

## Dag starten en na starten {#launch-post-launch}

Bevestig communicatie, steun, en follow-uptaken.

▢ **coördinatie van de Lancering:** Adobe heeft uw bevestigde lanceringsdatum; CTA is meegedeeld per e-mail.
▢ **Steun:** P1 hotline aantal wordt geregistreerd: US (+1) 800-497-0335, dan druk 6 voor Commerce.
▢ **Steun:** Uw team wordt getraind om een steunkaartje **te openen alvorens** het roepen van P1 hotline.
▢ **de lancering van het Post:** verifieer de scores van de Lithouse op het productiedomein.
▢ **Post lancering:** de Console van het Onderzoek van Google van de Monitor voor het indexeren en kruipen fouten.
▢ **de lancering van het Post:** Monitor 404 rapporten en voegt omleidingen voor hoog-verkeerserfenis URLs toe.
▢ **Post lancering:** bevestig MarTech en analysegegevens over productie.
▢ **Post lancering:** Vraag uw CTA, CSE, of AM om controle toe te laten high-SLA.
▢ Er bestaat een Disaster Recovery-plan dat de tests doorgeeft.
▢ Er is een proces voor het bijhouden en bijwerken van bouwsteenpakketten en extensiepakketten naar de huidige versies.
