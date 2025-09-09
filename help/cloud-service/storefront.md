---
title: Winefront instellen
description: Leer hoe te om het steigereedschap in werking te stellen om uw  [!DNL Adobe Commerce as a Cloud Service]  storefront te opstelling.
role: Developer
exl-id: 02928dc4-1777-483e-b0ee-b04fc813864d
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 408f28bdc20708022c8eca0fbfea4adb17014bf7
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Winefront instellen

Voer de volgende stappen uit om uw Adobe Commerce Storefront met Edge Delivery Services for Adobe Commerce as a Cloud Service (SaaS) in te stellen.

Als u een meer klantgerichte en gedetailleerde analyse wilt, verwijs naar de [ storefront documentatie ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/).

1. Open het [ hulpmiddel van de plaatsschepper ](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator).

1. Selecteer **creeer Nieuwe Plaats (Code &amp; Inhoud)**.

1. Ga de **Organisatie van Github/Gebruikersnaam** in waar u de opslagplaats van de storefrontcode wilt tot stand brengen.

1. Ga de Naam van de a **Plaats** in.

1. Op het **Eindpunt van Commerce GraphQL (facultatief)** gebied, ga uw eindpunt van GraphQL van Adobe Commerce as a Cloud Service (SaaS) in, dat u in de Manager van Commerce Cloud kunt toegang hebben na [ het creëren van uw instantie ](./getting-started.md#create-an-instance).

   Alternatief, als u [ API Net ](https://developer.adobe.com/graphql-mesh-gateway/mesh/basic) gebruikt, ga uw eindpunt van GraphQL van het Netwerk van API in het **(facultatieve) Eindpunt van GraphQL van Commerce** gebied in. Zie [ een netwerk ](https://developer.adobe.com/graphql-mesh-gateway/mesh/basic/create-mesh) voor meer informatie creëren.

1. Klik **creeer Plaats**. Volg de aanwijzingen op het scherm om toegang tot de gegevensopslagruimte van Github te verlenen.

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
* Meer leren over het bijwerken van plaatsinhoud en het integreren met Commerce frontend componenten en achterste gegevens, zie de [ documentatie van de Opslag van Adobe Commerce ](https://experienceleague.adobe.com/developer/commerce/storefront/).
