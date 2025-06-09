---
title: Migreren naar  [!DNL Adobe Commerce as a Cloud Service]
description: Leer hoe te aan  [!DNL Adobe Commerce as a Cloud Service] migreren.
exl-id: 9065c92a-f6b2-4464-8ec0-5c549bf78104
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
role: Architect
source-git-commit: 395def94181016b12a00ce675bb15ef6c8f10309
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 0%

---

# Migreren naar [!DNL Adobe Commerce as a Cloud Service]

{{accs-early-access}}

[!DNL Adobe Commerce as a Cloud Service] biedt de meeste configuratie uit het vak. Als u echter migreert vanaf een bestaande Adobe Commerce op Cloud of op locatie, moet u verschillende migratiehandelingen uitvoeren, afhankelijk van uw specifieke configuratie.

## Migratiepaden

[!DNL Adobe Commerce as a Cloud Service] ondersteunt meerdere migratiepaden, afhankelijk van uw tijdlijn, voorgrond en aanpassingen.

Als alternatief voor een volledige migratie biedt [!DNL Adobe Commerce as a Cloud Service] ondersteuning voor een gefaseerde migratie, waarbij gebruik wordt gemaakt van Commerce Optimizer of een incrementele aanpak.

* **Incrementele Migratie** - Deze benadering impliceert het migreren van uw gegevens, aanpassingen, en integratie in stadia. Deze benadering is ideaal voor grote handelaren met veel aanpassingen die hun complexe aanpassingen en gegevens geleidelijk in hun eigen tempo naar [!DNL Adobe Commerce as a Cloud Service] willen overbrengen.

![ stijgende migratie ](./assets/incremental.png){width="600" zoomable="yes"}

* **Commerce Optimizer** - Deze benadering staat u toe om zich herhalend te migreren, door Commerce Optimizer als overgangsfase te gebruiken om complexe aanpassingen en gegevens aan [!DNL Adobe Commerce as a Cloud Service] bij uw eigen tempo te bewegen. Commerce Optimizer biedt toegang tot Merchandising Services via Catalog Channels and Policies, Commerce Storefront van Edge Delivery en Product Visuals van AEM Assets.

![ iteratieve migratie ](./assets/optimizer.png){width="600" zoomable="yes"}

* **Volledige Migratie** - Deze benadering impliceert het migreren van alle gegevens, aanpassingen, en integratie in één keer. Deze benadering is ideaal voor kleinere handelaren met weinig aanpassingen die snel willen overschakelen op [!DNL Adobe Commerce as a Cloud Service] .

In de volgende tabel vindt u een overzicht van het migratieproces voor verschillende winkeliers en configuraties:

|                    | LUMA Storefront | PWA Storefront | Commerce Storefront met Edge Delivery | Koploos |
|--------------------|----------------------------------------|----------------------------------------|------------------------------------------------------|----------------------------------------|
| Gegevensmigratie | Vereist | Vereist | Vereist | Vereist |
| Storefront | Migreren naar Commerce Storefront met Edge Delivery | Migreren naar Commerce Storefront met Edge Delivery of Onderhouden | Geen effect | Geen effect |
| API-net | Nieuw net maken | Nieuw net maken of bestaand net opnieuw configureren | Nieuw net maken of bestaand net opnieuw configureren | Nieuw net maken of bestaand net opnieuw configureren |
| Integraties | Hefboomwerking integratie startkit | Hefboomwerking integratie startkit | Hefboomwerking integratie startkit | Hefboomwerking integratie startkit |
| Aanpassingen | Verplaatsen naar App Builder en API-net | Verplaatsen naar App Builder en API-net | Verplaatsen naar App Builder en API-net | Verplaatsen naar App Builder en API-net |
| Assets Management | Migratie vereist bij gebruik van OOTB | Migratie vereist bij gebruik van OOTB | Migratie vereist bij gebruik van OOTB | Migratie vereist bij gebruik van OOTB |
| Extensies | Migreren naar App Builder | Migreren naar App Builder | Migreren naar App Builder | Migreren naar App Builder |

Zoals aangegeven in de tabel, bestaan de verzachtende omstandigheden voor elke migratie uit:

* **Migratie van Gegevens** - Gebruikend verstrekt migratiehulpmiddel om gegevens van uw bestaande instantie aan [!DNL Adobe Commerce as a Cloud Service] te migreren.
* **Storefront** - Bestaande EDS en hoofdloze storefronts vereisen geen matiging, maar de opslag LUMA vereist migrerend aan de Opslag van Commerce aangedreven door Edge Delivery. PWA Studio-winkeliers kunnen worden gemigreerd naar Commerce Storefront, aangedreven door Edge Delivery, of in hun huidige staat worden onderhouden. Adobe zal versnellers leveren om hulp te bieden bij het migreren van winkeliers.
* **[API Net ](https://developer.adobe.com/graphql-mesh-gateway)** - creeer een nieuw net of wijzig bestaande. Adobe zal vooraf geconfigureerde netten beschikbaar stellen als hulp bij dit proces.
* **Integraties** - Alle integraties moeten hefboomwerking of de [ de startuitrusting van de integratieaanzet ](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/) of [[!DNL Adobe Commerce as a Cloud Service]  REST API ](https://developer.adobe.com/commerce/services/reference/cloud-service/core-admin/).
* **Aanpassingen** - Alle aanpassingen moeten zich aan het Net van App Builder en API bewegen.
* **het Beheer van Assets** - Al activa beheer vereist migratie. Als u AEM Assets al gebruikt, is migratie niet nodig.
* **Uitbreidingen** - om het even welke in-proces uitbreidingen moeten als uit-van-procesuitbreidingen worden opnieuw gemaakt. Eind 2025 biedt Adobe toegang tot onze populairste extensies om de ontwikkeltijden te minimaliseren.

## Migratiefasen

Bij het migreren van uw huidige Adobe Commerce-instantie naar een nieuwe [!DNL Adobe Commerce as a Cloud Service] -instantie gaat het vooral om de volgende fasen:

* **[Bereidheid](#readiness-phase)** - begin door te bepalen als uw plaatsing klaar is om aan ACCS te worden bewogen. In deze fase moet u zich ook vertrouwd maken met de wijzigingen die ACCS heeft aangebracht. &#x200B;
* **[Implementatie](#implementation-phase)** - daarna, klaar uw code, opslag, uitbreidingen, en integratie voor migratie. Om de overgang te verlichten, staat Adobe voor zowel [ korte termijn als lange termijn iteratieve benaderingen ](#migration-paths) toe. &#x200B;
* **[gaan-Levend](#go-live-phase)** - test en bevestig alles op zijn plaats is, dan de gegevensmigratie uitvoeren.
* **[post gaan-Levend](#post-go-live-phase)** - in samenwerking met Adobe, controleer voor kwesties en verbetert prestaties zoals nodig nadat de migratie volledig is.

### Gereedheidsfase

1. Begin met het evalueren van de architectuur, het uitbreidbaarheidsframework en de opslagmogelijkheden van [!DNL Adobe Commerce as a Cloud Service] :

   * [ Adobe Commerce op de Architectuur van de Diensten van de Wolk ](./overview.md) - herzie de platformarchitectuur en hoe het van uw huidige instantie van Adobe Commerce verschilt.
   * [ het Kader van de Rekbaarheid van Adobe Commerce ](https://developer.adobe.com/commerce/extensibility/) - identificeer hoe u uw huidige aanpassingen wilt overgaan.
   * [ Commerce Storefront aangedreven door Edge Delivery ](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL) - herzie de geadviseerde storefront oplossing.

1. Controleer de compatibiliteit van uw aanpassingen:

   * Identificeer uw huidige douanemodules en derdesintegratie.
   * Evalueer aanpassingen die opnieuw moeten worden geïmplementeerd met App Builder.
   * Wijs uw huidige aanpassingen toe aan hun equivalente App Builder-extensies.

1. Bevestig uw winkelvereisten en zorg ervoor dat deze zijn afgestemd op de Adobe Edge-leveringsmogelijkheden.

1. Controleer de huidige integratie van derden en bevestig de API-compatibiliteit met het [!DNL Adobe Commerce as a Cloud Service] -platform.

### Implementatiefase

In de volgende stappen wordt het ontwikkelings- en uitvoeringsproces van de migratie beschreven:

1. Creeer een nieuwe [!DNL Adobe Commerce as a Cloud Service] instantie in de [ Manager van Commerce Cloud ](./getting-started.md#create-an-instance).

1. Installeer de vereiste apps en aanpassingen. [!DNL Adobe Commerce as a Cloud Service] heeft toegang tot onze populairste apps. Als u aanvullende apps of aanpassingen nodig hebt, kunt u deze opnieuw implementeren met App Builder.

1. Stel een van de volgende op GraphQL gebaseerde winkeliers in:

   * [ creeer een Commerce storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=nl-NL)
   * [ Gebruik PWA Studio om een douane op GraphQL-Gebaseerde opslag tot stand te brengen ](https://developer.adobe.com/commerce/pwa-studio/)

1. Uw gegevens migreren van uw vorige Commerce-instantie naar ACCS:

   * Native Adobe Commerce-gegevens migreren met behulp van gereedschappen voor gegevensmigratie.
   * Extensies en aanpassingen van derden migreren
   * Configuratie- en integratiegegevens migreren:
      * De configuraties van het Net van de overdracht API, de derdediensten, en systeemintegratie die de [ Uitrusting van de Aanzet van de Integratie van Adobe Commerce gebruiken ](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/).

### GoLive-fase

Voordat u de nieuwe [!DNL Adobe Commerce as a Cloud Service] -instantie start, valideert en test met een sandboxomgeving:

* **Functioneel het Testen** - verzeker gemigreerde gegevens, storefront functionaliteit, en het aanpassingswerk foutloos.

* **het Testen van Prestaties** - evalueer de snelheid en scalability van uw opslag om optimale prestaties globaal te verzekeren.

* **Controle van de Veiligheid** - herzie veiligheidsmaatregelen, met inbegrip van API toegangscontrole en om het even welke potentiële kwetsbaarheid.

Nadat u de nieuwe sandbox-instantie [!DNL Adobe Commerce as a Cloud Service] hebt gevalideerd en getest, kunt u de productie-instantie starten.

### Post Go Live-fase

Voer na Go Live de volgende activiteiten uit:

1. Live follow-up

   * Richt verkeer aan het nieuwe platform en monitorprestaties opnieuw.
   * Schakel uw oude Adobe Commerce-exemplaar uit.

1. Controle na de introductie

   * Gebruik bewakingstools om stabiele bewerkingen te garanderen en om eventuele problemen na het opstarten aan te pakken.
