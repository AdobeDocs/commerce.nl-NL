---
title: Installatie
description: Installeer  [!DNL Store Fulfillment solution]  voor een Adobe Commerce storefront gebruikend Composer voor PHP.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Installatie

Voltooi de eerste installatie van de extensie [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] in een niet-productieomgeving met de uitvoering van de wachtrij en het in cache plaatsen geconfigureerd voor de verwerking van uitzonderingen. Zorg ervoor dat uw ontwikkelomgeving ontwikkeltools bevat voor de beste werkwijzen voor het werken en onderhouden van uw Adobe Commerce-instantie.

>[!TIP]
>
>Bevorder de uitbreiding van de Afhandeling van de Opslag voor Adobe Commerce op gebouw door de [ verbeteringsinstructies ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html) in de _Gids van de Verbetering van Adobe Commerce_ te volgen. Voor Adobe Commerce op wolkeninfrastructuur, zie [ bevorderen een uitbreiding ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/extensions.html#upgrade-an-extension) in *Commerce op de Gids van de Infrastructuur van de Wolk*.

## Vereisten

Herzie de [ vereisten ](solution-requirements.md) voor de oplossing van de Afhandeling van de Opslag en verzamel vereiste informatie alvorens u installeert of bevordert de [!DNL Store Fulfillment] uitbreiding voor Adobe Commerce.

Als u een pre-versie of bètaversie van de Store Fulfillment for Adobe Commerce-extensie hebt geïnstalleerd, gebruikt u de volgende opdracht om deze te verwijderen voordat u de huidige versie installeert.

```bash
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Installatievereisten

- **Toegang tot de Opslag die door het softwarearchief van de Technologieën van Commerce van het Spoor (.zip- dossier)** wordt ontvangen - tijdens het onboarding en enablement proces, werk met uw Manager van de Rekening om toegang tot het installatiedossier voor de uitbreiding van de Afhandeling van de Opslag te krijgen.

- **de rekeningsinformatie van Adobe Commerce** - Installerend de [!DNL Store Fulfillment] oplossing vereist a [[!DNL Commerce]  rekening ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/commerce-account/commerce-account-create){target="_blank"} . U hebt een account-id en gebruikersgegevens nodig met de toegang tot het [!DNL Adobe Commerce] -project door Eigenaar of Beheerder.

- Voor [!DNL Adobe Commerce] in projecten met cloudinfrastructuur moeten softwareinstallatieprogramma&#39;s beheerderstoegang tot het Cloud-project hebben. Zie [ gebruikerstoegang beheren ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/project/user-access).

- **Ervaring gebruikend Composer en[!DNL Commerce CLI]** - zie [ Algemene Installatie CLI ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions){target="_blank"}  voor informatie over het gebruiken van deze hulpmiddelen om uitbreidingen op het [!DNL Adobe Commerce] platform te installeren en te beheren.

- **Ervaring die derdeuitbreidingen op Adobe Commerce** installeert - voor verwijzing, zie de documentatie van Adobe Commerce.

   - [ installeer een uitbreiding voor een Adobe Commerce op de instantie van de wolkeninfrastructuur ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#install-an-extension).

   - [ installeer een uitbreiding voor een Adobe Commerce op-gebouw instantie ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions).

### Stap 1: De extensiesbundel downloaden

Volg de instructies van uw accountvertegenwoordigers om het archiefbestand te downloaden dat de Composer-pakketten bevat voor het installeren van de extensie Store Fulfillment Services.

### Stap 2: Extensieartefacten extraheren naar uw toepassing

Extraheer het archiefdossier dat de integratiebundel bevat om de uitbreiding van de Diensten van de Afhandeling van de Opslag te installeren.

1. Maak een doelmap voor de geëxtraheerde bestanden.

   - Ga vanaf de opdrachtregel naar de hoofdmap van het webserverdocument.

   - Maak een map `artifacts` .

1. Extraheer het archiefbestand naar de nieuwe map.

1. Controleer of de bestanden zijn uitgepakt door de bestandenlijst te bekijken.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### Stap 3: Uw app configureren met Composer

Gebruik Composer om de bronmap voor de installatie te configureren en de extensie Services voor winkelvervulling te installeren.

1. Configureer de bronopslagplaats voor de Composer-installatie.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Voeg de uitbreiding van de Diensten van de Afhandeling van de Opslag aan `composer.json` toe.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>Voor betere prestaties op Adobe Commerce op-gebouwinstanties, kunt u [ de autoload configuratie ](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader) bijwerken: `composer dump-autoload --optimize`

### Stap 4: Upgrade het databaseschema en de gegevens

Voltooi de installatie met behulp van `bin/magento setup:upgrade` om het databaseschema en de gegevens bij te werken met de wijzigingen ter ondersteuning van de oplossing Store Fulfillment.

>[!NOTE]
>
>Voor Adobe Commerce-infrastructuurprojecten in de cloud hoeft u de extensie niet te registreren. Wijs in plaats daarvan de codewijzigingen toe vanaf de vorige stap en duw deze naar uw omgevingsvertakking. De opdrachten voor het bijwerken van het databaseschema en de gegevens worden automatisch uitgevoerd tijdens het proces voor het bouwen en implementeren van de cloud.

### Stap 5: De installatie voltooien

1. Registreer de extensie met Adobe Commerce met de opdracht `setup:upgrade` Magento CLI.

   ```bash
   bin/magento setup:upgrade
   ```

1. Compileer het [!DNL Commerce] -project opnieuw als daarom wordt gevraagd.

   ```bash
   bin/magento setup:di:compile
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:clean
   ```

1. Onderhoudsmodus uitschakelen.

   ```bash
   bin/magento maintenance:disable
   ```

### Stap 6: De installatie controleren

Verifieer bij de Adobe Commerce-server of de modules voor de extensie Store Fulfillment Services zijn geïnstalleerd en ingeschakeld.

1. Log in bij de server.

   Voor installaties op Adobe Commerce op wolkeninfrastructuur, [ gebruik SSH aan login aan het verre milieu ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/secure-connections#ssh).

1. Verifieer dat de modules van de Diensten van de Afhandeling van de Opslag worden toegelaten.

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   De uitvoer moet de volgende modules bevatten:

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### Aanvullende stappen

Indien nodig, gebruik de [ opstelling :static-content: ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises){target="_blank"}  CLI bevel opstelt om statische meningsdossiers aan uw productiemilieu op te stellen.

```bash
php bin/magento setup:static-content:deploy -f
```

De optie `-f` is vereist als u een leeg thema gebruikt.

>[!NOTE]
>
>Voor meer informatie, zie de [ Statische inhoud beste praktijken in Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/development/static-content-deployment.html) artikel in het Centrum van de Hulp van Adobe Commerce opstelt.


