---
title: Installeren en openen  [!DNL App Management]
description: Vereisten en toegangsvereisten voor het gebruiken van Adobe Commerce  [!DNL App Management].
feature: App Builder, Extensibility, Integration
source-git-commit: ab635fecb7b82294bd4a4fd045ed71931e9d265d
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 1%

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

[!DNL App Management] is automatisch beschikbaar op [!DNL Adobe Commerce as a Cloud Service] . Er is geen installatie vereist. [&#x200B; laat het in Admin &#x200B;](#access-app-management) toe en begin associërende apps.

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

Zie [&#x200B; installeren of bijwerken Adobe Commerce Admin UI SDK &#x200B;](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/installation/){target="_blank"} voor meer informatie.

>[!ENDTABS]

## Toegang [!DNL App Management]

1. Meld u aan bij de Commerce-beheerder.

1. Ga naar **[!UICONTROL Apps]** > **[!UICONTROL App Management]**.

De weergave [!DNL App Management] wordt weergegeven. Hier kunt u App Builder-toepassingen koppelen, configureren en beheren.

## App Builder-toepassingen installeren

Als u een App Builder app van Adobe Exchange (bijvoorbeeld, een pre-gebouwde integratie of markt app) moet installeren, zie [&#x200B; App Builder apps van Adobe Exchange installeren &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/install-app-builder-app){target="_blank"} voor geleidelijke instructies.

Nadat een app wordt geïnstalleerd en opgesteld, gebruik [!DNL App Management] om het [&#x200B; met uw instantie van Commerce &#x200B;](manage-app.md#associate-an-app) te associëren en zijn montages te vormen.
