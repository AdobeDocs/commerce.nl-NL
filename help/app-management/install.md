---
title: Installeren en openen  [!DNL App Management]
description: Vereisten en toegangsvereisten voor het gebruiken van Adobe Commerce  [!DNL App Management].
feature: App Builder, Extensibility, Integration
source-git-commit: 86c0945bbb0a562de1b66d420dec2a05d4d81e5f
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Installeren en openen [!DNL App Management]

[!DNL App Management] is beschikbaar in Commerce Admin voor in aanmerking komende Commerce-instanties. De beschikbaarheid is afhankelijk van het implementatietype.

## Beschikbaarheid

Nadat u aan de volgende vereisten hebt voldaan, selecteert u het bijbehorende tabblad voor uw implementatietype hieronder om te zien of [!DNL App Management] installatie vereist of al beschikbaar is voor uw instantie.

## Vereisten

Controleer voordat u een app gaat koppelen het volgende:

| Vereiste | Beschrijving |
|-------------|-------------|
| **toegang Admin** | Commerce Admin met [!DNL App Management] -machtigingen |
| **Gedistribueerde app** | App Builder-toepassing geïmplementeerd op uw organisatie en klaar voor verbinding |
| **Toegang van de Organisatie** | Toegang tot de Adobe-organisatie waar de app wordt geïmplementeerd |

>[!BEGINTABS]

>[!TAB  Adobe Commerce as a Cloud Service ]

[!DNL App Management] is automatisch beschikbaar op [!DNL Adobe Commerce as a Cloud Service] . Er is geen installatie vereist. [ laat het in Admin ](#access-app-management) toe en begin associërende apps.

>[!TAB  Adobe Commerce op Wolk (PaaS) en op-gebouw ]

* **Adobe Commerce 2.4.8 en later** - [!DNL App Management] is automatisch inbegrepen. Er is geen installatie vereist.

* **Adobe Commerce 2.4.5 aan 2.4.7** - installeer [!DNL Admin UI SDK] (die [!DNL App Management] omvat) gebruikend Composer:

  ```bash
  composer require "magento/commerce-backend-sdk": ">=3.3"
  ```

  Voer vervolgens uit:

  ```bash
  composer update
  bin/magento setup:upgrade
  bin/magento indexer:reindex
  bin/magento cache:clean
  ```

Zie [ installeren of bijwerken Adobe Commerce Admin UI SDK ](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/installation/){target="_blank"} voor meer informatie.

>[!ENDTABS]

## Toegang [!DNL App Management]

1. Meld u aan bij de Commerce-beheerder.

1. Ga naar **[!UICONTROL Apps]** > **[!UICONTROL App Management]**.

De weergave [!DNL App Management] wordt weergegeven. Hier kunt u App Builder-toepassingen koppelen, configureren en beheren.

## App Builder-toepassingen installeren

Als u een App Builder app van Adobe Exchange (bijvoorbeeld, een pre-gebouwde integratie of markt app) moet installeren, zie [ App Builder apps van Adobe Exchange installeren ](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/install-app-builder-app){target="_blank"} voor geleidelijke instructies.

Nadat een app wordt geïnstalleerd en opgesteld, gebruik [!DNL App Management] om het [ met uw instantie van Commerce ](manage-app.md#associate-an-app) te associëren en zijn montages te vormen.

## Commerce-websites en -apps

Sommige toepassingen van App Builder gebruiken [ webhooks van Adobe Commerce ](https://developer.adobe.com/commerce/extensibility/webhooks/) zodat Commerce uw app over HTTP kan roepen wanneer bepaalde gebeurtenissen (bijvoorbeeld, nadat een product wordt bewaard) voorkomen. Webhaak eindpunten en abonnementlogica worden bepaald door de **app ontwikkelaar** wanneer de toepassing wordt gebouwd en opgesteld; de opslagbeheerders vormen niet afzonderlijk webhooks in het Beheer van de App.

Nadat u [ app ](https://experienceleague.adobe.com/en/docs/commerce/app-management/manage-app/manage-app) met uw instantie van Commerce associeert en om het even welke opstellingsinstructies van app voltooit, volgt het webhaakgedrag de implementatie van app.

Als [!DNL App Management] het validatieeindpunt van de app niet kan activeren (de URL is bijvoorbeeld niet bereikbaar of het antwoord voldoet niet aan de vereisten), ziet u mogelijk een fout die lijkt op het volgende in het [!DNL App Management] -dashboard:

![ fout van de Bevestiging Webhaak ](assets/webhook-validation-error.png){width="600" zoomable="yes"}

Het werk met de **app ontwikkelaar** om de webshconfiguratie of plaatsing te verbeteren zodat kan de bevestiging slagen.

**ontwikkelaars van de app**. Om webhaakabonnementen en managerreacties van App Builder uit te voeren, zie [ Webhooks ](https://developer.adobe.com/commerce/extensibility/app-management/installation/webhooks/) in de de ontwikkelaarsdocumentatie van Commerce Vermogen en [`@adobe/aio-commerce-lib-webhooks` ](https://github.com/adobe/aio-commerce-sdk/tree/main/packages/aio-commerce-lib-webhooks) pakket op GitHub.
