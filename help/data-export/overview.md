---
title: '[!DNL SaaS Data Export Guide]'
description: Leer over het gebruiken van de  [!DNL data export]  uitbreiding voor de diensten van Adobe Commerce SaaS die gegevens tussen Adobe Commerce en de verbonden diensten van Commerce synchroniseert.
role: Admin, Developer
exl-id: 8a0067ba-90a4-48a6-8276-208d09abe6fc
source-git-commit: ae672ed3f2693e2f14e8c7f379e59ef117a34fc3
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Handleiding

[!DNL SaaS data export] synchroniseert gegevens tussen een Adobe Commerce-instantie en verbonden Commerce Services. Wanneer u Live zoeken, productaanbevelingen of de catalogusservice toevoegt aan een Adobe Commerce-installatie, wordt de extensie [!DNL Data export] automatisch geïnstalleerd.

De gegevensuitvoer van SaaS verzamelt en voert diverse types van gegevens uit, die als _worden bedoeld voer_, die specifieke soorten informatie samenvoegen. Afhankelijk van welke Commerce-services worden geïnstalleerd, bevat de SaaS-gegevensexportfeed het volgende:

- **de entiteitvoer van de Catalogus** gezamenlijke productgegevens. Gegevens omvatten producten, productkenmerken, productprijzen, productvariaties, categorieën, categorietoestemmingen en productmachtigingen.
- De **Scopes voeren** gegevens voor klantengroepen, websites, opslag, en opslagmeningen samen.
- De **voer van de Orde van de Verkoop** voegt ordergegevens met inbegrip van hun verwante entiteiten zoals facturen, verzendingen, creditmemo&#39;s, etc. samen.
- De **voer van de multi-Source Inventory** aggregeert gegevens over de punten van de voorraadstatus van de inventaris.

SaaS data export wordt geleverd als een PHP extensie. Deze biedt ondersteuning voor verschillende methoden voor het initiëren en beheren van het proces voor gegevenssynchronisatie.

- **Handmatige synchronisatie van Admin of de bevellijn**

   - Het [ dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard) in Commerce Admin verstrekt een grafische mening van de synchronisatiestatus. U kunt het dashboard gebruiken om volledige resynchronisatie (_volledige synchronisatie_) van alle voer uit te voeren. Adobe raadt echter aan om alleen volledige synchronisatie uit te voeren wanneer u Adobe Commerce voor de eerste keer verbindt met een Commerce-service. Zie [ Synchronisatieproces ](data-synchronization.md).

   - Het [ bevel-lijn van Adobe Commerce hulpmiddel ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI) verstrekt bevelen om specifieke voer te synchroniseren en omvat extra opties om voederverwerking aan te passen.

- **Geautomatiseerde synchronisatie met cron banen**

   - [ Gedeeltelijke gegevenssynchronisatie ](data-synchronization.md#partial-synchronization-with-cron-jobs) - de banen van het Gewas brengen een gedeeltelijke gegevenssynchronisatie teweeg wanneer een gebruiker van Commerce Admin een entiteit bijwerkt. Tijdens het exporteren van gegevens worden alleen deze updates naar verbonden Commerce-services verzonden. Het partiële synchronisatieproces is gebaseerd op het MView-mechanisme en vereist geen acties van de Admin-gebruiker of systeemintegrator.

   - [ Automatisch opnieuw proberen voor synchronisatiefouten ](data-synchronization.md#failed-items-sync-for-error-recovery) - de banen van de Cron teweegbrengen automatisch opnieuw proberen van het synchronisatieproces wanneer de fouten tijdens het proces van de gegevenssynchronisatie voorkomen.

- **het plannen van de Uitvoer en prestaties**

   - Ontwikkelaars en systeemintegrators kunnen een schatting maken van de tijd die nodig is voor het exporteren van SaaS-gegevens om gegevens tussen Adobe Commerce en verbonden services te synchroniseren. Deze schatting kan helpen bij het plannen van gegevensexportverwerking om verstoring van de site te voorkomen. Zie [ schatten gegevensvolume en transmissietijd ](estimate-data-volume-sync-time.md).

   - In gevallen waarin de synchronisatie sneller moet verlopen, biedt SaaS-gegevensexport aanpassingsopties om de prestaties van de exportverwerking te verbeteren. Zie [ de uitvoerprestaties van gegevens verbeteren ](customize-export-processing.md).

- **Spoor en los de activiteiten van de gegevensuitvoer** problemen op - gebruik gegevens-uitvoer en saas-export logboeken om synchronisatiestatus en voederladingen tijdens het synchronisatie en indexeringsproces te herzien. Zie [ Registreren en het oplossen van problemen ](troubleshooting-logging.md).
