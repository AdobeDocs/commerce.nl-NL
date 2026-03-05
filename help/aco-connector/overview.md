---
title: Adobe Commerce Optimizer Connector
description: Leer hoe u uw gegevens van uw Commerce-cloud of -project op locatie kunt verbinden met Adobe Commerce Optimizer
feature: Personalization, Integration, Configuration
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."
source-git-commit: 11bb5df2488a017065db44504f35612fe54e284c
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Adobe Commerce Optimizer Connector

De Adobe Commerce Optimizer-connector is de integratiebrug die catalogus- en prijsgegevens synchroniseert tussen een Adobe Commerce op cloudinfrastructuur of implementatie op locatie en [!DNL Adobe Commerce Optimizer] . Door gegevens naar Adobe Commerce Optimizer te synchroniseren, beschikt u over functies zoals dynamische AI-zoekopdrachten, aanbevelingen, optimalisatie van sites en snel ladende headless-winkels, waaronder Adobe Commerce-winkeliers op Edge Delivery Services, en real-time prestatieanalyses.

## Architectuur en ervaring

De Adobe Commerce Optimizer Connector werkt door Commerce-websites in kaart te brengen en weergaven op te slaan naar een Commerce Optimizer-project, zoals in de volgende afbeelding wordt getoond:

![&#x200B; het in kaart brengen van de gegevens van Commerce aan Adobe Commerce Optimizer &#x200B;](./assets/storeview-to-catalogview-mapping.png){width="700" zoomable="yes"}

Wanneer gegevens van Commerce naar Commerce Optimizer worden geëxporteerd:

* Weergaven in Commerce-winkel worden toegewezen aan catalogusbronnen
* Websites worden toegewezen aan prijsboeken

De bijbehorende catalogus- en prijsgegevens worden geëxporteerd en later gebruikt om catalogusweergaven te maken en eventueel beleidsregels te definiëren om de catalogus- en prijsgegevens te filteren voor specifieke gevallen van zakelijk gebruik.

Wanneer de schakelaar wordt toegelaten, kunt u ook handelsregels voor productontdekking en regels voor aanbevelingen vormen en beheren gebruikend [[!DNL Adobe Commerce Optimizer]  Merchandising hulpmiddelen &#x200B;](../optimizer/overview.md#quick-tour) De instantie van Adobe Commerce wordt de gegevensbron voor catalogus en prijsgegevens. Wanneer de gegevens in Commerce worden bijgewerkt, worden de updates gesynchroniseerd met de [!DNL Adobe Commerce Optimizer] -instantie.

## Workflows

De connector schakelt verschillende belangrijke workflows in:

* **de catalogusgegevens van Commerce van de uitvoer naar[!DNL Adobe Commerce Optimizer]** - prijs en prijsboekgegevens worden uitgevoerd op het website en klantengroepsniveau. Gegevens van product- en productkenmerken worden geëxporteerd op `store view` niveau. Standaard is het synchroniseren van catalogusgegevens ingeschakeld voor alle Commerce-bereiken (websites en winkelweergaven).

  Als u deze workflow wilt inschakelen, installeert u de extensie `adobe-commerce/commerce-data-export-aco-adapter` PHP, controleert u de configuratie van de exportfunctie en schakelt u vervolgens de integratie tussen Commerce en Commerce Optimizer in via Commerce Admin. Voor gedetailleerde instructies, zie [&#x200B; Begonnen &#x200B;](#get-started) worden.

* **Wijs de Commerce-website toe en sla weergavegegevens op waarnaar u wilt exporteren[!DNL Adobe Commerce Optimizer]**

  Pas desgewenst de exportinstellingen aan om alleen gegevens voor bepaalde websites te synchroniseren of om weergaven op te slaan. U kunt bijvoorbeeld catalogusgegevens exporteren voor slechts één winkelweergave die u voor een specifiek geval wilt gebruiken, zoals het optimaliseren van de zoek- en ontdekkingservaring voor een bepaalde markt of regio.

* **het Merchandising de regelconfiguratie en beheer**

  Wanneer de Connector is ingeschakeld, worden de regels voor het verhandelen van producten voor productdetectie en -aanbevelingen gedefinieerd en beheerd vanuit de [!DNL Adobe Commerce Optimizer] -gebruikersinterface, niet vanuit de [!UICONTROL Live Search] - en [!UICONTROL Product Recommendations] -pagina&#39;s in Commerce Admin.

* **stel uw Opslag van Commerce op Edge Delivery Services** op

  Nadat u de integratie met [!DNL Adobe Commerce Optimizer] hebt ingesteld, kunt u een Commerce Storefront op Edge Delivery Services implementeren. Dit biedt ultrasnelle prestaties, schaalbaarheid, naadloze creatie van inhoud en geïntegreerde personalisatie met behulp van een composable, API-gestuurde architectuur.

Voor details op hoe te opstelling de integratie en deze werkschema&#39;s toelaten, zie [&#x200B; Begonnen krijgen &#x200B;](get-started.md).
