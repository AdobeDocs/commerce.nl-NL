---
title: Winefront instellen
description: Leer hoe te om het steigermiddel in werking te stellen aan opstelling uw  [!DNL Adobe Commerce as a Cloud Service]  storefront.
feature: Storefront
role: Developer
level: Beginner
exl-id: 02928dc4-1777-483e-b0ee-b04fc813864d
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 6eda2197fde2e88292e58b2bb4fc4759f24da558
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Winefront instellen

Voer de volgende stappen uit om [!DNL Adobe Commerce Storefront] powered by [!DNL Edge Delivery Services] for [!DNL Adobe Commerce as a Cloud Service] (SaaS) in te stellen.

Voor een meer klantgerichte en gedetailleerde analyse, verwijs naar de [ storefront documentatie ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/).

1. Open het [ hulpmiddel van de plaatsschepper ](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator).

1. Selecteer **[!UICONTROL Create New Site (Code & Content)]** .

1. Voer de **[!UICONTROL Github Organization/Username]** in waar u de opslaglocatie voor de voorbeeldcode wilt maken.

1. Voer een **[!UICONTROL Site Name]** in.

1. Op het **[!UICONTROL Commerce GraphQL Endpoint (optional)]** gebied, ga uw [!DNL Adobe Commerce as a Cloud Service] (SaaS) eindpunt van GraphQL in, dat u in de Manager van Commerce Cloud kunt toegang hebben na [ het creëren van uw instantie ](./getting-started.md#create-an-instance).

   Als u [[!DNL API Mesh] ](https://developer.adobe.com/graphql-mesh-gateway/mesh/basic) gebruikt, voert u het [!DNL API Mesh] GraphQL-eindpunt in het **[!UICONTROL Commerce GraphQL Endpoint (optional)]** -veld in. Zie [ een netwerk ](https://developer.adobe.com/graphql-mesh-gateway/mesh/basic/create-mesh) voor meer informatie creëren.

1. Klik op **[!UICONTROL Create Site]**. Volg de instructies op scherm om toegang tot uw bewaarplaats te verlenen GitHub.

Nadat het proces is voltooid, kunt u de winkel op de volgende manieren aanpassen:

* Uw code aanpassen: `https://github.com/<username or org>/<repo name>`
* Uw inhoud bewerken: `https://da.live/#/<username or org>/<repo name>`
* Uw configuratie beheren: `https://da.live/sheet#/<username or org>/<repo name>/configs-stage`
* Een voorvertoning van uw winkel weergeven: `https://main--<repo name>--<username or org>.aem.page/`

## Volgende stappen

Raadpleeg de volgende artikelen voor meer informatie:

* Meer leren over het beheren van en het tonen van inhoud en gegevens in de storefront, zie [ het bijwerken van storefront inhoud ](./use-cases.md#update-storefront-content).
* Voor meer informatie over contextafhankelijke experimenteringseigenschappen, zie [ contextafhankelijke experimentatie ](./use-cases.md#contextual-experimentation).
* Voor meer informatie bij het gebruiken van Generatieve AI om de inhoudsgeneratie van uitstekende kwaliteit te automatiseren, zie [ Variaties ](./use-cases.md#generate-variations) produceren.
* Zie [[!DNL Adobe Commerce Storefront documentation] ](https://experienceleague.adobe.com/developer/commerce/storefront/) voor meer informatie over het bijwerken van de site-inhoud en het integreren met Commerce frontend-componenten en backend-gegevens.
