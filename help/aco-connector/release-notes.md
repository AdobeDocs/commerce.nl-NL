---
title: '[!DNL Adobe Commerce Optimizer Connector] Opmerkingen bij de release'
description: De recentste versieinformatie voor  [!DNL Adobe Commerce Optimizer Connector]  voor Adobe Commerce.
feature: Services, Catalog Service, Release Notes
source-git-commit: 205fca38b379f94027a965b58826ffd922577f61
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Opmerkingen bij de release Adobe Commerce Optimizer Connector

Deze releaseopmerkingen beschrijven alle releases voor de [!DNL Adobe Commerce Optimizer Connector] en bevatten:

![ Nieuwe ](../assets/new.svg) Nieuwe eigenschappen
![ Vaste kwestie ](../assets/fix.svg) Oplossingen en verbeteringen
![ Bekende kwestie ](../assets/bug.svg) Bekende kwesties

## Versies van 2026

### 1.0.12 Release

_2 April, 2026_

![ Nieuwe ](../assets/new.svg) **Toegevoegde steun voor het voer van Categorieën in `saas:resync` bevel **-u kan nu gemakkelijk uw recentste categoriegegevens verfrissen en bekijken gebruikend het `saas:resync` CLI bevel:

```terminal
bin/magento saas:resync --feed=categories
```

_Maart 10, 2026_

![ Vaste kwestie ](../assets/fix.svg) Vaste een verenigbaarheidskwestie die toegang tot de de configuratiepagina van de Verbinding van de Diensten van Commerce van de menu&#39;s van het Systeem en van de Configuratie van Commerce blokkeerde Admin wanneer de Schakelaar van Adobe Commerce Optimizer op een instantie van Commerce wordt geïnstalleerd.  Nu hebt u toegang tot de configuratiepagina Commerce Services Connector wanneer beide extensies zijn geïnstalleerd. <!--MDEE-1322-->


### Versie v1.0.10

_Maart 09, 2026_

![ Repareren ](../assets/fix.svg) als u tot de pagina van de Status van de Synchronisatie van het Gegeven toegang hebt alvorens de configuratie van de Schakelaar te voltooien, wordt u nu automatisch opnieuw gericht aan de de configuratiepagina van de Schakelaar. Deze geleide stroom zorgt ervoor dat de opstelling van de Schakelaar wordt voltooid en helpt fouten verhinderen die door ontbrekende configuratiemontages worden veroorzaakt die in ontbroken of onvolledige statuspunten konden resulteren.<!--MDEE-1296-->

### Versie v1.0.9

_Maart 01, 2026_

Algemene beschikbaarheidsversie van de Schakelaar van Adobe Commerce Optimizer.

>[!NOTE]
>
>Als u hebt deelgenomen aan het Beta-programma voor de Adobe Commerce Optimizer-connector en een eerdere versie van de extensie hebt geïnstalleerd, voert u een upgrade uit naar de algemene beschikbaarheidsversie om de nieuwste updates te ontvangen.

