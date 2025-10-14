---
title: Installatie
description: Leer hoe u  [!DNL Catalog Service] installeert
exl-id: 3f8492c3-f76d-49b7-a201-35deace36a1d
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."
source-git-commit: 1cb6443e79e0e3d813550f9b619b3a0f641cd989
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 0%

---

# Onboarding en installatie

Installeer de Dienst van de Catalogus om productgegevens van een instantie van Commerce te verzoeken en te ontvangen gebruikend de [&#x200B; dienst GraphQL API van de Catalogus &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/). De Catalog Service wordt geleverd als een composer-pakket van de repo.magento.com-opslagplaats.

>[!NOTE]
>
>Als uw Commerce-exemplaar gebruikmaakt van Live zoeken of productaanbevelingen, wordt de Catalogusservice automatisch geïnstalleerd of bijgewerkt wanneer u aan boord bent of een upgrade uitvoert van deze services. Voor details, zie de installatieinstructies voor [&#x200B; Levend Onderzoek &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/live-search/install) en [&#x200B; Aanbevelingen van het Product &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/product-recommendations/getting-started/install-configure).


## Systeemvereisten

**de vereisten van de Software**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2, 8.3, 8.4
- Composer: 2.x

**Ondersteunde platforms**

- Adobe Commerce op cloudinfrastructuur: 2.4.4+
- Adobe Commerce in bedrijven: 2.4.4+

## Eindpunten

[!DNL Catalog Service] heeft twee eindpunten beschikbaar voor instapweigering:

- Sandbox (`https://catalog-service-sandbox.adobe.io/graphql`)—wordt gebruikt voor het testen en valideren voordat u live gaat
- Productie (`https://catalog-service.adobe.io/graphql`) - gebruikt voor levend verkeer voor de handelaren en websites van Commerce

Alle Commerce-testinstanties gebruiken het Sandbox-eindpunt.

Voer alle tests van de Lading op het zandbakeindpunt uit. Alvorens u begint lading het testen, voorlegt a [&#x200B; kaartje van de Steun &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=nl-NL#submit-ticket) zodat het team van de Diensten het extra serververkeer kan voorzien.

## Installatie en configuratie

Om aan de slag te gaan met [!DNL Catalog Service] voor Adobe Commerce, zijn de volgende stappen vereist:

- De extensie Catalog Service installeren (`magento/catalog-service`)
- De service- en gegevensexport configureren
- Toegang tot de service

### De extensie Catalog Service installeren

>[!BEGINSHADEBOX]

**Vereiste**

- Toegang [&#x200B; repo.magento.com &#x200B;](https://repo.magento.com) om de uitbreiding te installeren. Voor zeer belangrijke generatie en het verkrijgen van de noodzakelijke rechten, zie [&#x200B; uw authentificatiesleutels &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) krijgen. Voor wolkeninstallaties, zie [&#x200B; Commerce op de Gids van de Infrastructuur van de Wolk &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/authentication-keys)

- Toegang tot de opdrachtregel van de Adobe Commerce-toepassingsserver.

>[!ENDSHADEBOX]

Installeer de recentste versie van de uitbreiding van de Diensten van de Catalogus (`magento/catalog-service`) op een instantie van Adobe Commerce die Adobe Commerce versie 2.4.4 of later in werking stelt. De dienst van de Catalogus wordt geleverd als composer metapakket van de {[&#x200B; bewaarplaats 0} repo.magento.com.](https://repo.magento.com)

>[!BEGINTABS]

>[!TAB  de infrastructuur van de Wolk ]

Gebruik deze methode om [!DNL Catalog Service] voor een Commerce Cloud-instantie te installeren.

1. Schakel op uw lokale werkstation de projectmap voor uw Adobe Commerce over het infrastructuurproject voor de cloud in.

   >[!NOTE]
   >
   >Voor informatie over het beheren van het projectmilieu&#39;s van Commerce plaatselijk, zie [&#x200B; het Leiden takken met CLI &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/cli-branches) in _Adobe Commerce op de Gids van de Gebruiker van de Infrastructuur van de Wolk_.

1. Bekijk de omgevingsvertakking voor update met de Adobe Commerce Cloud CLI.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Voeg de module Catalogusservice toe.

   ```bash
   composer require magento/catalog-service --no-update
   ```

1. Pakketafhankelijkheden bijwerken.

   ```bash
   composer update "magento/catalog-service"
   ```

1. Voeg de codewijzigingen voor de `composer.json` - en `composer.lock` -bestanden toe, wijs deze toe en duw ze naar de cloudomgeving.

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   Het duwen van de updates aan het wolkenmilieu stelt het [&#x200B; proces van de wolkenplaatsing van Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/process) in werking om de veranderingen toe te passen. Controleer de plaatsingsstatus van [&#x200B; opstellen logboek &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB  op-gebouw ]

Gebruik deze methode om [!DNL Catalog Service] voor een instantie op locatie te installeren.

1. Composer van het gebruik om de module van de Dienst van de Catalogus aan uw project toe te voegen:

   ```bash
   composer require magento/catalog-service --no-update
   ```

1. Afhankelijkheden bijwerken en de extensie installeren:

   ```bash
   composer update  "magento/catalog-service"
   ```

1. Upgrade Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Cache wissen:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >In sommige gevallen, vooral wanneer het opstellen aan productie, zou u gecompileerde code kunnen willen vermijden omdat het wat tijd kan vergen. Zorg ervoor dat u een back-up van het systeem maakt voordat u wijzigingen aanbrengt.

>[!ENDTABS]

### De service- en gegevensexport configureren

Nadat u [!DNL Catalog Service] hebt geïnstalleerd, voert u de volgende taken uit om de catalogusservice te integreren met uw Adobe Commerce-instantie. Deze integratie maakt de gegevenssynchronisatie en communicatie tussen de instantie van Commerce, de Dienst van de Catalogus, en andere ondersteunende diensten mogelijk. De synchronisatie van gegevens wordt behandeld door de [&#x200B; uitbreiding van de Uitvoer van Gegevens SaaS &#x200B;](../data-export/overview.md).

1. Opstelling de [&#x200B; Verbinding van de Diensten van Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/user-guides/integration-services/saas) door de API sleutels te specificeren en een Ruimte van Gegevens te selecteren SaaS.

   Commerce Services Connector-instellingen is een eenmalig proces dat vereist is voor het gebruik van Adobe Commerce-services, zoals Catalog Service, Live Search en Productaanbevelingen. Als u reeds de schakelaar voor een andere dienst hebt gevormd, sla deze stap over.

1. Voer een aanvankelijke gegevenssynchronisatie van het [&#x200B; dashboard van het Beheer van Gegevens uit &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/data-dashboard).

   De eerste synchronisatie kan enkele minuten tot uren duren, afhankelijk van de grootte van de catalogus. U kunt de synchronisatiestatus controleren via het dashboard voor gegevensbeheer. Na de eerste synchronisatie worden de productgegevens van de Catalogus doorlopend geëxporteerd om de services up-to-date te houden.

   >[!NOTE]
   >
   >U kunt de eerste synchronisatie ook starten vanaf de opdrachtregel met behulp van de Commerce CLI. Zie [&#x200B; Aanvankelijke synchronisatie &#x200B;](../data-export/data-export-cli-commands.md#initial-sync) in de _Gids van de Uitvoer van Gegevens SaaS_.

Ga als volgt te werk om te controleren of de catalogus correct wordt geëxporteerd:

- [&#x200B; Bevestig dat de bouwbanen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues) lopen.
- Verifieer dat de indexen van [&#x200B; Admin &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/index-management) lopen of door het bevel van Commerce CLI te gebruiken `bin/magento indexer:info`.
- Controleer of de indexen `Catalog Attributes Feed, Product Feed, Product Overrides Feed` en `Product Variant Feed` op `Update by Schedule` zijn ingesteld.

### Gegevenssynchronisatie controleren en problemen oplossen

Van Commerce Admin, kunt u het synchronisatieproces controleren gebruikend het [&#x200B; Dashboard van het Beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/data-dashboard). Gebruik [&#x200B; CLI van Commerce &#x200B;](../data-export/data-export-cli-commands.md#troubleshooting) en logboeken om het proces te beheren en problemen op te lossen.
