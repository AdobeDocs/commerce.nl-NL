---
title: Adobe Commerce Optimizer Connector voor Commerce
description: Leer hoe u uw gegevens van uw Commerce-cloud of -project op locatie kunt verbinden met Adobe Commerce Optimizer
feature: Personalization, Integration, Configuration
hidefromtoc: true
hide: true
source-git-commit: 5d0cfb2c389bf11f89815e7d1fbc2861a6b48962
workflow-type: tm+mt
source-wordcount: '1530'
ht-degree: 0%

---


# Overzicht

De Adobe Commerce-connector is de integratiebrug die catalogusgegevens en prijsgegevens synchroniseert tussen een bestaande Adobe Commerce Cloud op cloud- of on-premisse implementatie en het Adobe Commerce Optimizer-model met composable catalogusgegevens. Dit maakt functies mogelijk zoals dynamische AI-zoekopdrachten, aanbevelingen, snelle koploze winkels, waaronder Adobe Commerce-winkeliers op Edge Delivery Services, en realtime prestatieanalyses.

>[!NOTE]
>
>Deze documentatie beschrijft een product in vroege-toegangsontwikkeling en weerspiegelt niet alle functionaliteit voorgenomen voor algemene beschikbaarheid.

## Architectuur en ervaring

Adobe Commerce Connector werkt door Commerce `website/store/storeview` catalogushiërarchie toe te wijzen aan Adobe Commerce Optimizer `channel/policy/source` gegevensmodel.

In plaats van het vormen van en het beheren van de Diensten van Commerce (Levende Onderzoek en Aanbevelingen van het Product) van Commerce Admin, gebruikt u [&#x200B; de hulpmiddelen van de Verkoop van Adobe Commerce Optimizer &#x200B;](../optimizer/merchandising/overview.md) om productontdekking (Levende Onderzoek) en aanbevelingen (de Regelconfiguratie van de Aanbevelingen van het Product) te beheren.  Het Adobe Commerce-exemplaar wordt de gegevensoorsprong voor catalogus- en prijsgegevens. Wanneer de gegevens in Commerce worden bijgewerkt, worden de updates gesynchroniseerd met het Adobe Commerce Optimizer-exemplaar.

## Workflows

De connector schakelt verschillende belangrijke workflows in:

* **de catalogusgegevens van Commerce van de Uitvoer naar Adobe Commerce Optimizer** - prijs en de gegevens van het prijsboek worden uitgevoerd op het `website` niveau. Gegevens van product- en productkenmerken worden geëxporteerd op `store view` niveau. Standaard is het synchroniseren van catalogusgegevens ingeschakeld voor alle Commerce-bereiken (websites en winkelweergaven).

  Als u deze workflow wilt inschakelen, gebruikt u Composer om de `adobe-commerce/commerce-data-export-aco-adapter` PHP-extensie te installeren en geeft u vervolgens de IMS-referenties op om de verbinding tussen het Commerce-project te verifiëren.

* **Kaart de gegevens van Commerce `website/store/storeview` om naar Adobe Commerce Optimizer** uit te voeren

  U kunt de Adobe Commerce Optimizer-exportinstellingen aanpassen om alleen gegevens te exporteren voor een bepaald bereik door de exportconfiguratie van het winkelraster in Admin (**[!UICONTROL Stores]** -> [!UICONTROL Settings] -> **[!UICONTROL All Stores]** ) bij te werken.

* **het Merchandising de regelconfiguratie en beheer**

  Wanneer de Connector is ingeschakeld, worden de regels voor het verhandelen van producten voor productdetectie en -aanbevelingen gedefinieerd en beheerd vanuit de gebruikersinterface van Adobe Commerce Optimizer, niet vanaf de pagina&#39;s [!UICONTROL Live Search] en [!UICONTROL Product Recommendations] in Commerce Admin.

* **stel uw Opslag van Commerce op Edge Delivery Services** op

  Nadat u de integratie met Adobe Commerce Optimizer hebt ingesteld, kunt u een Commerce Storefront instellen en implementeren op Edge Delivery-services voor ultrasnelle prestaties, schaalbaarheid, naadloze creatie van inhoud, geïntegreerde personalisatie en lagere operationele kosten met behulp van de composable, API-gestuurde architectuur en modulaire componenten die beschikbaar zijn in Adobe Commerce Optimizer.

## Vereisten voor het gebruik van de integratie

* Adobe Commerce 2.4.5+

   * PHP 8.1, 8.2, 8.3 of 8.4
   * Composer 2.x

* Adobe Commerce Optimizer-licentie met een geleverde sandbox-instantie.

* Toegang tot [&#x200B; repo.magento.com &#x200B;](https://repo.magento.com) om het metapakket van de Verbinding van Commerce te downloaden gebruikend Composer.

* Admin toegang tot een [&#x200B; zandbakinstantie van Adobe Commerce Optimizer &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/adobe-commerce-optimizer/create-first-instance).

De Adobe Commerce-gebruiker die de integratie configureert, moet beschikken over:

* Beheerderstoegang tot de Adobe Commerce Admin.

* [&#x200B; de lijntoegang van het Bevel tot de de toepassingsserver van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/project/user-access).

* De toegang van de ontwikkelaar tot de [&#x200B; IMS Organisatie &#x200B;](https://experienceleague.adobe.com/nl/docs/core-services/interface/administration/organizations?) waar het project van Adobe Commerce Optimizer provisioned is.

## Aan de slag

1. **Opstelling de Integratie**

   1. [&#x200B; installeer het pakket van de Schakelaar van Commerce &#x200B;](#install-the-commerce-connector-package).

   1. [De vereiste waarden ophalen voor het configureren van de Commerce Optimizer-verbinding](#get-required-values-for-configuring-the-commerce-optimizer-connection)

   1. [&#x200B; laat de integratie van Adobe Commerce Optimizer &#x200B;](#enable-the-adobe-commerce-optimizer-integration) toe.

   1. [&#x200B; verifieer dat de gegevenssynchronisatie &#x200B;](#verify-that-the-data-sync-is-working) werkt.

   1. [&#x200B; pas de configuratie van de gegevensuitvoer &#x200B;](#customize-commerce-data-export-configuration) (facultatief) aan.

1. **[vormen de opslag van Adobe Commerce Optimizer](#configure-adobe-commerce-optimizer-stores)**

1. **[opstelling een Opslag van Commerce op Edge Delivery Services](#set-up-a-commerce-storefront-on-edge-delivery-services)**

## Het Commerce-connectorpakket installeren

De Adobe Commerce Connector Composer-metapakket is beschikbaar voor alle Commerce-handelaren met een actieve licentie voor Adobe Commerce Optimizer.

### Installatiestappen

1. Voeg de module `adobe-commerce/commerce-data-export-aco-adapter` toe met behulp van Composer:

```shell
 composer require adobe-commerce/commerce-data-export-aco-adapter
```

1. Implementeer de wijzigingen in uw Adobe Commerce-testomgeving.

Nadat uw wijzigingen zijn geïmplementeerd, is de optie Commerce Optimizer Optimizer beschikbaar in het menu Commerce Admin.

>[!NOTE]
>
>Raadpleeg de volgende handleidingen voor gedetailleerde installatie-instructies voor extensies:
>
>[&#x200B; installeer uitbreiding op Adobe Commerce op de Infrastructuur van de Wolk &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure-store/extensions)
>
>[&#x200B; installeer uitbreiding Adobe Commerce op-gebouw &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/extensions)

## Vereiste waarden ophalen voor het configureren van de Commerce Optimizer-verbinding

### API-referenties ophalen

>[!NOTE]
>
>Als u al een App Builder Developer-project hebt in de IMS-organisatie waar uw Commerce Optimizer-instantie is geïmplementeerd, kunt u de vereiste API-referenties en organisatie-id ophalen van de OAUTH-server-naar-server-referenties in dat project.

Maak een nieuw ontwikkelaarsproject in de Adobe Developer-console voor het ophalen van API-referenties om de integratie tussen Commerce- en Commerce Optimizer-instanties te configureren. Voor instructies, zie [&#x200B; een project van App Builder &#x200B;](https://developer.adobe.com/commerce/extensibility/events/project-setup/) in de ontwikkelaarsdocumentatie creëren.

Nadat u het project creeert, sparen de volgende waarden van de server-aan-Server geloofsbrieven pagina OAUTH:

* **identiteitskaart van de Organisatie** (`org_id`)

* **IMS `client_id` en`client_secret`**

### Adobe Commerce Optimizer-instantiedetails ophalen

Sla de volgende waarden op uit uw Adobe Commerce Optimizer-instantiedetails.

* **Instance ID—**&#x200B;The unique identifier for your Adobe Commerce Optimizer instance. Ook bekend als huurder-id.

  Haal de instantie-id op van de URL om toegang te krijgen tot uw Adobe Commerce Optimizer-instantie. In de URL `https://na1-sandbox.admin.commerce.adobe.com/1234567890abcdef` is de instantie-id bijvoorbeeld `1234567890abcdef` .

* **Region—**&#x200B;The region where your Adobe Commerce Optimizer sandbox instance is hosted.

  Haal het gebied op van de Adobe Commerce Optimizer URL. In de URL `https://na1-sandbox.admin.commerce.adobe.com/1234567890abcdef` is het gebied bijvoorbeeld `na1` .

## Integratie met Adobe Commerce Optimizer inschakelen

>[!IMPORTANT]
>
>De verwerking van de gegevenssynchronisatie begint aangezien u het configuratiebevel in werking stelt. Standaard is het synchroniseren van catalogusgegevens ingeschakeld voor alle Commerce-bereiken (websites en winkelweergaven). Afhankelijk van de grootte van de catalogus kan het synchronisatieproces van de gegevens vele uren in beslag nemen.

Met behulp van de API-referenties en de instantiedetails die u in de vorige stappen hebt verzameld, kunt u nu de integratie tussen uw Commerce- en Adobe Commerce Optimizer-instanties configureren.

1. Selecteer in Commerce Admin **[!UICONTROL Adobe Commerce Optimizer]** om de configuratiepagina met instructies weer te geven.

   ![&#x200B; de configuratiepagina van Adobe Commerce Optimizer &#x200B;](../assets/aco-connector-config-page.png)

1. Van de bevellijn, [&#x200B; gebruik SSH &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/develop/secure-connections) om met het opvoeren van Commerce milieu te verbinden.

1. Voer het volgende Commerce CLI bevel in werking om de integratie te vormen, die de placeholder waarden met de waarden voor uw project van Commerce Optimizer vervangt:

```terminal
bin/magento aco:config:init --org_id=<<your_org_id>> --tenant_id=<<your_tenant_id>> --client_id=<<your_client_id>> --client_secret=<<your_client_secret>> --region=<<na1>> --type=sandbox
```

1. Controleer de verbinding door terug te keren naar Commerce Admin en de optie [!UICONTROL Adobe Commerce Optimizer] te selecteren.

   Als u op deze optie klikt, wordt de gebruikersinterface van Adobe Commerce Optimizer op een nieuw tabblad geopend.

## Controleren of de gegevenssync werkt

U kunt de gegevenssynchronisatie zowel in Commerce Admin als in Commerce Optimizer controleren.

* De **[pagina van de Status van de Synchronisatie van het Gegeven van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/data-sync/data-feed-sync-status.md)** toont de vooruitgang van de synchronisatie van catalogusgegevens van Commerce aan Adobe Commerce Optimizer.

* De **[[!UICONTROL Data Sync]pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/optimizer/setup/data-sync)** in Adobe Commerce Optimizer toont de catalogusgegevens die van uw instantie van Commerce worden overgebracht.

1. Controleer of de catalogusgegevens van Commerce naar Commerce Optimizer stromen:

   Open vanuit Commerce Admin de pagina [!UICONTROL Data Feed Sync Status] door [!UICONTROL System] **&#x200B; > [!UICONTROL Data Transfer] > &#x200B;** [!UICONTROL Data Feed Sync Status]** te selecteren.

   ![&#x200B; de pagina van de Status van de Synchronisatie van het Gegeven van Gegevens met de status van het voederpunt rapporterend &#x200B;](./assets/data-feed-sync-status.png)

   Als de gegevenssynchronisatie is gestart, worden records verzonden in de feed-gegevens. U kunt synchronisatieproblemen ook weergeven en oplossen door de details voor elke feed weer te geven.

1. Controleer of Adobe Commerce Optimizer de catalogusgegevens ontvangt:

   Selecteer in het menu Commerce Optimizer de optie **[!UICONTROL Data Sync]** om de pagina Gegevenssynchronisatie te openen.

   ![&#x200B; de Synchronisatie van Gegevens &#x200B;](./assets/data-sync.png)

### Problemen oplossen

Als de gegevenssynchronisatie niet is gestart, controleert u of de catalogusindexen geldig zijn. Als de indexen ongeldig zijn, voert u de volgende opdracht van de Commerce CLI uit om de catalogusgegevens opnieuw te indexeren:

```terminal
bin/magento indexer:reindex" catalog indexer re-index CLI command to start PaaS to ACO catalog data synchronization.
```

## Commerce-configuratie voor gegevensexport aanpassen

U kunt de Adobe Commerce Optimizer-exportinstellingen aanpassen om alleen gegevens te exporteren voor een bepaald bereik door de exportconfiguratie van het winkelraster in Admin (**[!UICONTROL Stores]** -> [!UICONTROL Settings] -> **[!UICONTROL All Stores]** ) bij te werken.

* Als u de exporter-instelling op `website` uitschakelt, worden de prijzen en de prijsboekgegevens niet meer naar Adobe Commerce Optimizer geëxporteerd.

* Als u de exporter-instelling op `storeview` uitschakelt, wordt het exporteren van producten en productkenmerken naar Adobe Commerce Optimizer gestopt.

Wanneer de configuratie wordt gewijzigd, worden de corresponderende indexen ongeldig gemaakt om het opnieuw exporteren van de betrokken entiteiten te activeren.

## Adobe Commerce Optimizer-winkels configureren

Adobe Commerce Optimizer-winkels configureren door catalogusweergaven en -beleid te maken. &#x200B; Zie [&#x200B; Creërend de Weergaven van de Catalogus &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/optimizer/setup/catalog-view) in de Gids van Adobe Commerce Optimizer.

Prijsboeken worden automatisch aangemaakt door Adobe Commerce-klantengroepen.

## Commerce Storefront instellen op Edge Delivery Services

In deze sectie vindt u een overzicht op hoog niveau van de stappen die nodig zijn om de Commerce-winkel in te stellen. De gedetailleerde informatie is beschikbaar in [ Adobe Commerce Storefront ] (https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL) documentatieplaats.

1. De kloon en stelt het bouwwerk van Adobe Commerce Storefront aan EDS op gebruikend het [&#x200B; hulpmiddel van de Maker van de Plaats &#x200B;](https://da.live/app/adobe-commerce/storefront-tools/tools/site-creator/site-creator).

1. [&#x200B; opstelling een lokale ontwikkelomgeving &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/create-storefront/?lang=nl-NL#set-up-local-environment).

1. [&#x200B; installeer het pakket van de Verenigbaarheid van de Opslag van GraphQL &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/storefront-compatibility/install/?lang=nl-NL). &#x200B;

1. [&#x200B; vorm de kopballen van CORS voor de instantie van Commerce in wolkenmilieu &#x200B;](#configure-cors-headers-for-commerce-instance).

1. [&#x200B; verbind de opslag met de gegevensbronnen van Commerce &#x200B;](#connect-the-storefront-to-commerce-data-sources).

### CORS-headers configureren voor Commerce-instantie

Als u wilt toestaan dat GraphQL-aanvragen vanuit een Edge Delivery Services-winkel (EDS) naar Adobe Commerce kunnen komen in een cloud- of een omgeving in een bedrijf, gebruikt u een van de volgende opties om specifieke koppen voor het delen van bronnen van kruisoorsprong (Cross-Origin Resource Sharing, CORS) toe te voegen aan de eindpunten van Adobe Commerce GraphQL. &#x200B;

1. Voeg de koppen voor het delen van bronnen tussen verschillende bronnen (CORS) toe aan de eindpunten van Adobe Commerce GraphQL. &#x200B;

   **Optie 1: Voer een PHP douanemodule voor de stichting van Adobe Commerce uit om kopballen CORS te kunnen toevoegen. &#x200B;**

   **Optie 2: Installeer een graycore/magento2-cors van de 3de gemeenschapsmodule &#x200B;** - zie [&#x200B; opstelling CORS &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/cors-setup/?lang=nl-NL) in de *Adobe Commerce Storefront* documentatie.

1. Voeg de volgende CORS-variabelen toe aan het Commerce-configuratiebestand voor de cloud-instantie `app.yaml` :

   * `CONFIG__DEFAULT__WEB__GRAPHQL__CORS_ALLOWED_HEADERS: *`
   * `CONFIG__DEFAULT__WEB__GRAPHQL__CORS_ALLOWED_ORIGINS: *`

### De opslagruimte verbinden met Commerce-gegevensbronnen

In de bewaarplaats GitHub voor de Stortefront boilerplate-code, werk het storefront configuratiedossier, `config.json` met de volgende parameters bij:

* `"commerce-core-endpoint": "Commerce cloud instance GraphQL endpoint"`

* `"commerce-endpoint": "Commerce Optimizer instance GraphQL endpoint"` - krijg deze waarde van de [&#x200B; pagina van de instantiedetails van Commerce Optimizer &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/optimizer/get-started#get-instance-details) &#x200B;

* `"AC-Environment-Id": "Customer organization ID"` - krijg deze waarde van het [&#x200B; de wolkenproject van Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/project/overview#project-overview)

* `"AC-View-ID": "Catalog view ID in Commerce Optimizer Admin"` - Deze waarde wordt opgehaald uit de Adobe Commerce Optimizer Admin.

* `"AC-Price-Book-ID": "base::b6589fc6ab0dc82cf12099d1c2d40ab994e8410c"` — Haal deze waarde op bij Adobe Commerce Optimizer Admin. &#x200B;

* `"AC-Source-Locale": "Catalog source – Store View code from Commerce cloud instance"`

Voor meer informatie, zie {de configuratie van 0} Storefront [&#x200B; in de &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/commerce-configuration/?lang=nl-NL) Adobe Commerce Storefront *documentatie.*


