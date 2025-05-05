---
title: Configuratie achtergrondproces
description: Vorm de programma's voor  [!DNL Store Fulfillment]  achtergrondprocessen die in het synchroniseren van gegevens met de uitvoeringsdiensten worden gebruikt.
role: Admin, Developer
level: Intermediate
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Configuratie achtergrondproces

De integratie van de Afhandeling van de Opslag gebruikt achtergrondprocessen en berichtrijen voor optimale prestaties en schaal. Bouw milieu&#39;s voor uw opslag van Adobe Commerce gebruikend [ plaatsingsvariabelen ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#cron_consumers_runner) die [ de looppas van de berichtrij ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework) automatisch beginnen.

De processen van de achtergrond worden beheerd gebruikend de standaardAdobe Commerce [ Geplande functionaliteit van Taken ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/cron). Deze processen zijn de oorzaak van het synchroniseren van orde en de handelaarconfiguratiegegevens met de Webdiensten van de opslagvervulling.

## Geplande taken beheren voor het uitvoeren van een winkel

Ga vanuit Beheer naar **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]** .

Controleer de standaardconfiguratie voor de diensten van de Afhandeling van de Opslag. U kunt deze instellingen aanpassen op basis van het verwerkingsvolume van uw bestelling en de beschikbaarheid van bronnen.
