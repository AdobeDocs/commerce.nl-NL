---
title: Waarneembaarheid voor  [!DNL Adobe Commerce as a Cloud Service]
description: Leer over de observability hulpmiddelen en de telemetriemogelijkheden beschikbaar voor  [!DNL Adobe Commerce as a Cloud Service], met inbegrip van metriek, registreren, en het vinden.
feature: Cloud, Integration
role: Admin, Developer
level: Intermediate
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 3c10ecdea3d06295013c9c6e2d6869afd750a0b9
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# Waarneming

Waarneming is een essentieel aspect van het werken met [!DNL Adobe Commerce as a Cloud Service] . Het omvat de inzameling, verwerking, en visualisatie van telemetriegegevens-met inbegrip van metriek, registreren, en het vinden-zodat u toepassingsgezondheid kunt controleren, prestatieskwesties diagnostiseren, en de betrouwbaarheid van uw handelsplatform en zijn integratie optimaliseren.

## [!DNL Adobe Commerce as a Cloud Service]

### Overzicht van waarneming

Waarnembaarheid geeft u inzicht in de gezondheid en prestaties van uw Adobe Commerce-winkel en alle aangesloten App Builder-toepassingen. Door telemetriegegevens over uw commerciële ecosysteem te verzamelen, kunt u:

* {de metriek van het 0} Spoor **zoals de reactietijden van API, verzoek en foutenpercentages, en middelgebruik om prestaties en steuntendensen in real time te controleren.**
* **centraliseer logboeken** van uw toepassing, infrastructuur, CDN, en integratie in één enkele mening voor snellere het oplossen van problemen.
* **de verzoeken van het spoor** van begin tot eind aangezien zij van front door Commerce en verbonden apps stromen, die u helpen knelpunten en mislukkingen identificeren alvorens zij klanten beïnvloeden.

Samen helpen deze mogelijkheden u om problemen snel te identificeren en op te lossen, prestaties te optimaliseren en een betrouwbare ervaring voor uw klanten te verzekeren. Het [ observability overzicht ](https://developer.adobe.com/commerce/extensibility/observability/) verklaart hoe [!DNL Adobe Commerce as a Cloud Service] OpenTelemetry gebruikt om deze telemetrieinzameling over gebeurtenis, webhooks, en de toepassingen van App Builder te verenigen.

![ de architectuur van de Waarneming ](./assets/observability.png){width="600" zoomable="yes"}

Adobe Commerce biedt via OpenTelemetry ondersteuning voor de volgende hulpmiddelen voor waarneembaarheid:

* Elasticsearch
* Grafana
* Jaeger
* New Relic
* Prometheus
* Splunk
* Zipkin

### Abonnementen configureren

[ vorm observability abonnementen ](https://developer.adobe.com/commerce/extensibility/observability/configuration/) in [!UICONTROL Admin] of door REST API aan routelogboeken, metriek, of sporen aan om het even welk OpenTelemetry-compatibel eindpunt. Elk abonnement richt zich op specifieke componenten (webhooks, gebeurtenis of [!UICONTROL Admin UI SDK]).

### REST API voor waarneming

De [ observability REST API ](https://developer.adobe.com/commerce/extensibility/observability/api/) verstrekt eindpunten die tot stand brengen, terugwinnen, bijwerken, en de abonnementen van de schrappingswaarneming programmatically. Gebruik deze eindpunten om configuratie over instanties te automatiseren.

## Adobe Developer App Builder

### App Builder-instrumenten

[ voert observability in  [!DNL App Builder] uit ](https://developer.adobe.com/commerce/extensibility/observability/app-builder/) om spoorcontext van Commerce in uw [!DNL App Builder] acties te verspreiden zodat de logboeken en de sporen van beide systemen in uw observatieplatform correleren. Omvat instrumentatie voor op webhaak gebaseerde en op gebeurtenis-gebaseerde integratie.

[!DNL App Builder] verstrekt ook ingebouwde hulpmiddelen voor [ het beheren van toepassingslogboeken ](https://developer.adobe.com/app-builder/docs/guides/app_builder_guides/application_logging/logging), met inbegrip van toegang CLI en Developer Console, en logboek het door:sturen aan externe oplossingen zoals Splunk, Azure, en New Relic.

### Telemetriebibliotheek

De [`@adobe/aio-lib-telemetry` ](https://github.com/adobe/aio-lib-telemetry/blob/main/docs/usage.md) -bibliotheek is wat App Builder-handelingen gebruiken om met OpenTelemetry compatibele logbestanden en sporen uit te zenden. Omvat installatie, configuratie, en de opstelling van de uitvoerder.

### Lokale ontwikkeling en tests

[ test lokale uw opstelling van de observatievermogen ](https://developer.adobe.com/commerce/extensibility/observability/local-development/) alvorens op te stellen. Gebruik [!DNL Grafana] voor visualisatie en het doorsturen van tunnels (bijvoorbeeld [!DNL Ngrok] ) om telemetrie te ontvangen van een externe Commerce-instantie op uw ontwikkelingscomputer.

## [!DNL API Mesh]

### API-netregistratie

[ API het registreren van het Net ](https://developer.adobe.com/graphql-mesh-gateway/mesh/advanced/logging/) laat u controleren en zuivert verzoeken die door uw netwerk stromen gebruikend straal IDs. Exporteer logbestanden in bulk of stuur ze door naar platforms zoals [!DNL New Relic] voor gecentraliseerde analyse.

## Storefront

### CDN en Real User Monitoring

[ Echte de Controle van de Volmacht van de Gebruiker (RUM) ](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/content-delivery-network/#proxy-rum-through-the-origin-to-avoid-a-tls-handshake) gegevensinzameling door uw oorsprong CDN om een extra handdruk van TLS te elimineren en prestatiesmeting te verbeteren front-end.

## Video&#39;s over waarneming

De volgende video&#39;s bieden een overzicht op hoog niveau van de aanbiedingen voor waarneembaarheid in [!DNL Adobe Commerce as a Cloud Service] :

* [App Builder-video&#39;s over waarneming](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/observability/overview){target="_blank"}
* [API-netvideo&#39;s](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/extensibility/api-mesh/getting-started-api-mesh){target="_blank"}
