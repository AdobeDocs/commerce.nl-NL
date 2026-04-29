---
title: '[!DNL SaaS Data Export Guide]'
description: Leer over het gebruiken van de  [!DNL data export]  uitbreiding voor de diensten van Adobe Commerce SaaS die gegevens tussen Adobe Commerce en de verbonden diensten van Commerce synchroniseert.
role: Admin, Developer
exl-id: 8a0067ba-90a4-48a6-8276-208d09abe6fc
source-git-commit: 803e270c5b3119681a6e8c005728a00b3b7875f7
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Hulplijn

[!DNL SaaS data export] synchroniseert gegevens tussen een Adobe Commerce-instantie en verbonden Commerce Services. Wanneer u Live zoeken, productaanbevelingen of de catalogusservice toevoegt aan een Adobe Commerce-installatie, wordt de extensie [!DNL Data export] automatisch geïnstalleerd.

>[!NOTE]
>
>Als u de Adobe Commerce Optimizer-connector installeert, wordt dezelfde extensie Data Export gebruikt om catalogus- en prijsfeeds naar Adobe Commerce Optimizer te verzenden met behulp van het Composable Catalog Data Model (CCDM). Zie de [&#x200B; gids van de Schakelaar van Adobe Commerce Optimizer &#x200B;](../aco-connector/overview.md) voor architectuur en configuratiedetails.

De gegevensuitvoer van SaaS verzamelt en voert diverse types van gegevens uit, die als _worden bedoeld voer_, die specifieke soorten informatie samenvoegen. Afhankelijk van welke Commerce-services worden geïnstalleerd, bevat de SaaS-gegevensexportfeed het volgende:

- **de entiteitvoer van de Catalogus** gezamenlijke productgegevens. Gegevens omvatten producten, productkenmerken, productprijzen, productvariaties, categorieën, categorietoestemmingen en productmachtigingen.
- De **Scopes voeren** gegevens voor klantengroepen, websites, opslag, en opslagmeningen samen.
- De **voer van de Orde van de Verkoop** voegt ordergegevens met inbegrip van hun verwante entiteiten zoals facturen, verzendingen, creditmemo&#39;s, etc. samen.
- De **voer van de multi-Source Inventory** aggregeert gegevens over de punten van de voorraadstatus van de inventaris.

SaaS data export wordt geleverd als een PHP extensie. Deze biedt ondersteuning voor verschillende methoden voor het initiëren en beheren van het proces voor gegevenssynchronisatie.

- **Handmatige synchronisatie van Admin of de bevellijn**

   - Het [&#x200B; dashboard van het Beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard) in Commerce Admin verstrekt een grafische mening van de synchronisatiestatus die productgegevens met succes aan handelsdiensten toont. U kunt het dashboard gebruiken om volledige resynchronisatie (_volledige synchronisatie_) van alle voer uit te voeren. Adobe raadt echter aan om alleen volledige synchronisatie uit te voeren wanneer u Adobe Commerce voor de eerste keer verbindt met een Commerce-service. Zie [&#x200B; Synchronisatieproces &#x200B;](data-synchronization.md).

     {{aco-data-sync-verification}}

   - De [&#x200B; pagina van de Status van de Synchronisatie van het Gegeven van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status) verstrekt inzicht in real time in de gezondheid en de prestaties van de invoer van gegevens die product en categoriegegevens van Commerce aan externe diensten zoals de Aanbevelingen van het Product, Levend Onderzoek, en de Dienst van de Catalogus, of Adobe Commerce Optimizer overbrengen.

   - Het [&#x200B; bevel-lijn van Adobe Commerce hulpmiddel &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI) verstrekt bevelen om specifieke voer te synchroniseren en omvat extra opties om voederverwerking aan te passen.

- **Geautomatiseerde synchronisatie met cron banen**

   - [&#x200B; Gedeeltelijke gegevenssynchronisatie &#x200B;](data-synchronization.md#partial-sync) - de banen van het Gewas brengen een gedeeltelijke gegevenssynchronisatie teweeg wanneer een gebruiker van Commerce Admin een entiteit bijwerkt. Tijdens het exporteren van gegevens worden alleen deze updates naar verbonden Commerce-services verzonden. Het partiële synchronisatieproces is gebaseerd op het MView-mechanisme en vereist geen acties van de Admin-gebruiker of systeemintegrator.

   - [&#x200B; Automatisch opnieuw proberen voor synchronisatiefouten &#x200B;](data-synchronization.md#retry-failed-items-sync) - de banen van de Cron teweegbrengen automatisch opnieuw proberen van het synchronisatieproces wanneer de fouten tijdens het proces van de gegevenssynchronisatie voorkomen.

- **het plannen van de Uitvoer en prestaties**

   - Ontwikkelaars en systeemintegrators kunnen een schatting maken van de tijd die nodig is voor het exporteren van SaaS-gegevens om gegevens tussen Adobe Commerce en verbonden services te synchroniseren. Deze schatting kan helpen bij het plannen van gegevensexportverwerking om verstoring van de site te voorkomen. Zie [&#x200B; schatten gegevensvolume en transmissietijd &#x200B;](estimate-data-volume-sync-time.md).

   - In gevallen waarin de synchronisatie sneller moet verlopen, biedt SaaS-gegevensexport aanpassingsopties om de prestaties van de exportverwerking te verbeteren. Zie [&#x200B; de uitvoerprestaties van gegevens verbeteren &#x200B;](customize-export-processing.md).

- **Spoor en los de activiteiten van de gegevensuitvoer** problemen op - gebruik gegevens-uitvoer en saas-export logboeken om synchronisatiestatus en voederladingen tijdens het synchronisatie en indexeringsproces te herzien. Zie [&#x200B; Registreren en het oplossen van problemen &#x200B;](troubleshooting-logging.md).
