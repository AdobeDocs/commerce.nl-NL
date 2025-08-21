---
title: Aan de slag met  [!DNL Live Search]
description: Leer de systeemvereisten en installatiestappen voor  [!DNL Live Search]  van Adobe Commerce.
role: Admin, Developer
exl-id: 45b985f1-9afb-4a07-93e8-f2fe231c5400
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."
source-git-commit: 1548b7e11249febc2cd8682581616619f80c052f
workflow-type: tm+mt
source-wordcount: '3151'
ht-degree: 0%

---

# Instellen voor succes met [!DNL Live Search]

Adobe Commerce [!DNL Live Search] en [[!DNL Catalog Service]](../catalog-service/guide-overview.md) werken samen om een krachtige, relevante en intuïtieve zoekoplossing te bieden, zodat uw klanten snel precies kunnen vinden wat ze nodig hebben. [!DNL Catalog Service] bevat met name de catalogusgegevens die u wilt gebruiken voor SaaS-services, zoals [!DNL Live Search] .

Dit artikel bevat stapsgewijze instructies voor het implementeren van [!DNL Live Search] met [!DNL Catalog Service] .

## Publiek

Dit artikel is bedoeld voor de ontwikkelaar of systeemintegrator in uw team die verantwoordelijk is voor de installatie en configuratie van uw Adobe Commerce-exemplaar.

## Vereisten

- [ Adobe Commerce ](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP 8.1, 8.2 of 8.3
- [!DNL Composer]
- Snijtaken en indexeerders uitvoeren

>[!IMPORTANT]
>
>Alvorens [!DNL Live Search] uit te voeren, zie de [ Grenzen en 2} sectie van Beperkingen {om ervoor te zorgen dat ](boundaries-limits.md) uw bedrijfsbehoeften past.[!DNL Live Search]

## Belangrijke updates

- Vanaf [!DNL Live Search] 3.0.2 wordt de extensie [!DNL Catalog Service] gebundeld met de installatie.

- Vanwege de Elasticsearch 7-aankondiging aan het einde van de service voor augustus 2023 raadt Adobe alle Adobe Commerce-klanten aan naar de OpenSearch 2.x-zoekmachine te migreren. Voor informatie over het migreren van uw onderzoeksmotor tijdens een productverbetering, zie [ Migrerend aan OpenSearch ](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) in de _Gids van de Verbetering_.

## Ondersteunde platforms

- Adobe Commerce on Cloud (ECE) : 2.4.4+
- Adobe Commerce on-prem (EE) : 2.4.4+

## Workflowoverzicht

Op een hoog niveau is het vereist dat u: [!DNL Live Search]

1. [ installeer ](#1-install-the-live-search-extension) de [!DNL Live Search] uitbreiding
1. [ vorm ](#2-configure-api-keys) de API sleutels
1. [ Synchroniseer ](#3-sync-your-catalog-data) uw catalogusgegevens
1. [ verifieer ](#4-verify-that-the-data-was-exported) dat de catalogusgegevens werden uitgevoerd
1. [ vorm ](#5-configure-the-data) de gegevens
1. [ Test ](#6-test-the-connection) de verbinding
1. [ verifieer ](#7-validate-events-are-capturing-data) dat de gebeurtenissen gegevens vangen
1. [ pas ](#8-customize-for-your-storefront) uw storefront aan

## &#x200B;1. Installeer de extensie [!DNL Live Search]

[!DNL Live Search] is geïnstalleerd als uitbreiding van [ Adobe Marketplace ](https://commercemarketplace.adobe.com/magento-live-search.html) door [ Composer ](https://getcomposer.org/). Nadat u [!DNL Live Search] hebt geïnstalleerd en geconfigureerd, begint Adobe [!DNL Commerce] met het delen van zoek- en catalogusgegevens met SaaS-services. Op dit punt, *Admin* kunnen de gebruikers opstelling, aanpassen, en onderzoeksfacetten, synoniemen, en handelswijzigingsregels beheren.

>[!BEGINTABS]

>[!TAB  Nieuwe instantie van Commerce ]

Volg deze instructies als u [!DNL Live Search] op een nieuw Commerce-exemplaar installeert.

1. Bevestig dat [ gewassenbanen ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) en [ indexeerders ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) lopen.

1. Gebruik Composer om de module Live zoeken toe te voegen aan uw project:

   ```bash
   composer require magento/live-search --no-update
   ```

1. Afhankelijkheden bijwerken en de extensie installeren:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

1. Schakel [!DNL OpenSearch] en de bijbehorende modules tijdelijk uit en installeer [!DNL Live Search] .

   ```bash
   bin/magento module:disable Magento_ Magento_Elasticsearch8 Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   [!DNL Elasticsearch] blijft zoekverzoeken van de winkel beheren terwijl de [!DNL Live Search] -service catalogusgegevens en indexproducten op de achtergrond synchroniseert.

1. Installeer de updates.

   ```bash
   bin/magento setup:upgrade
   ```

1. Verifieer dat de volgende [ indexeerders ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) aan &quot;Update door Programma&quot;worden geplaatst:

   - Productfeed
   - Diervoeders voor productvarianten
   - Feed voor cataloguskenmerken
   - Diervoeders productprijzen
   - Websitegegevensfeed
   - Scopes Klantengroepen Gegevensfeed
   - Diervoeders voor categorieën
   - Diervoeders voor categorierechten

Na het verifiëren van de indexen, is de volgende stap de API sleutels [ te vormen ](#2-configure-api-keys).

>[!TAB  Bestaande instantie van Commerce ]

Volg deze instructies als u [!DNL Live Search] op een bestaande Commerce-instantie installeert.

1. Bevestig dat [ gewassenbanen ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) en [ indexeerders ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) lopen.

1. Gebruik Composer om de module Live zoeken toe te voegen aan uw project:

   ```bash
   composer require magento/live-search --no-update
   ```

1. Afhankelijkheden bijwerken en de extensie installeren:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

1. Schakel de [!DNL Live Search] -modules uit die de zoekresultaten van de winkel dienen.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing
   ```

   [!DNL Elasticsearch] blijft zoekverzoeken van de winkel beheren terwijl de [!DNL Live Search] -service catalogusgegevens en indexproducten op de achtergrond synchroniseert.

1. Installeer de updates.

   ```bash
   bin/magento setup:upgrade
   ```

1. Verifieer dat de volgende [ indexeerders ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) aan &quot;Update door Programma&quot;worden geplaatst:

   - Productfeed
   - Diervoeders voor productvarianten
   - Feed voor cataloguskenmerken
   - Diervoeders productprijzen
   - Websitegegevensfeed
   - Scopes Klantengroepen Gegevensfeed
   - Diervoeders voor categorieën
   - Diervoeders voor categorierechten

1. Schakel de extensie [!DNL Live Search] in en schakel [!DNL OpenSearch] uit (de modules Magento Elasticsearch en OpenSearch).

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing
   ```

   ```
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_Elasticsearch8 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   >[!NOTE]
   >
   >De opdracht Uitschakelen bevat een lijst met Commerce-modules die OpenSearch ondersteunen. Als er geen module is geïnstalleerd op uw Commerce-instantie, wordt een `module does not exist` -fout weergegeven.

1. Installeer de updates.

   ```bash
   bin/magento setup:upgrade
   ```

Na het verifiëren van de indexen, is de volgende stap de API sleutels [ te vormen ](#2-configure-api-keys).

>[!ENDTABS]

### De bètaversie van [!DNL Live Search] installeren

>[!IMPORTANT]
>
>De volgende functie is in bèta. Om aan bèta deel te nemen, verzend een e-mailverzoek naar [ handel-opslag-diensten ](mailto:commerce-storefront-services@adobe.com).

Deze bèta steunt drie nieuwe mogelijkheden in [`productSearch` vraag ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/):

- **Gelaagd onderzoek** - Onderzoek binnen een andere onderzoekscontext - met dit vermogen, kunt u tot twee lagen van onderzoek naar uw onderzoeksvragen ondernemen. Bijvoorbeeld:

   - **Laag 1 onderzoek** - Onderzoek naar &quot;motor&quot;op &quot;product_attribute_1
   - **Laag 2 onderzoek** - Onderzoek naar &quot;deelaantal 123&quot;op &quot;product_attribute_2&quot;. In dit voorbeeld wordt gezocht naar &quot;part number 123&quot; in de resultaten naar &quot;motor&quot;.

  Gelaagde zoekopdracht is beschikbaar voor zowel `startsWith` zoekindexatie als `contains` zoekindex, zoals hieronder wordt beschreven:

- **startWith onderzoeksindexatie** - Onderzoek gebruikend `startsWith` indexatie. Met deze nieuwe functie is het mogelijk:

   - Zoeken naar producten waarbij de kenmerkwaarde begint met een bepaalde tekenreeks.
   - Het vormen van &quot;beëindigt met&quot;onderzoek zodat kunnen de kopers naar producten zoeken waar de attributenwaarde met een bepaalde koord beëindigt. Om &quot;beëindigt met&quot;onderzoek toe te laten, moet het productattribuut in omgekeerde worden opgenomen, en de API vraag zou ook een omgekeerde koord moeten zijn.

- **bevat onderzoeksindexatie** - Onderzoek een attribuut gebruikend bevat indexatie. Met deze nieuwe functie is het mogelijk:

   - Zoeken naar een query binnen een grotere tekenreeks. Als een winkel bijvoorbeeld het productnummer &quot;PE-123&quot; zoekt in de tekenreeks &quot;HAPE-123&quot;.

     >[!NOTE]
     >
     >Dit onderzoekstype is verschillend van het bestaande [ uitdrukkingsonderzoek ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#phrase), dat een autocomplete onderzoek uitvoert. Als de waarde van het kenmerk van het product bijvoorbeeld &quot;outdoorbroek&quot; is, retourneert een zoekopdracht met woordgroepen een reactie voor &quot;out pan&quot;, maar wordt geen reactie voor &quot;of ants&quot; geretourneerd. A contains search, echter, retourneert wel een reactie op ‘or ants’.

Deze nieuwe voorwaarden verbeteren het het filtreren van de onderzoeksvraag mechanisme om onderzoeksresultaten te raffineren. Deze nieuwe voorwaarden hebben geen invloed op de hoofdzoekquery.

U kunt deze nieuwe voorwaarden implementeren op de pagina met zoekresultaten. U kunt bijvoorbeeld een nieuwe sectie toevoegen op de pagina waar de gebruiker de zoekresultaten verder kan verfijnen. Je kunt kopers toestaan specifieke productkenmerken te selecteren, zoals &#39;Fabrikant&#39;, &#39;Onderdeelnummer&#39; en &#39;Beschrijving&#39;. Daarna zoeken ze binnen die kenmerken met behulp van de `contains` - of `startsWith` -voorwaarden. Zie de gids Admin voor een lijst van doorzoekbare [ attributen ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types).

1. Om bèta te installeren, voeg de volgende gebiedsdeel aan uw project toe:

   ```bash
   composer require magento/module-live-search-search-types:"^1.0.0-beta1"
   ```

1. Leg de wijzigingen in uw `composer.json` - en `composer.lock` -bestanden vast en duw deze in uw cloudproject. [ leer meer ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension).

   Deze bètaversie voegt selectievakjes **[!UICONTROL Search types]** voor **[!UICONTROL Autocomplete]** , **[!UICONTROL Contains]** en **[!UICONTROL Starts with]** in Admin toe. Het werkt ook de [`productSearch` ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#filtering-using-search-capability) GraphQL API bij om deze nieuwe onderzoeksmogelijkheden te omvatten.

1. In Admin, [ plaats een productattribuut ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes-add#step-5-describe-the-storefront-properties) om het onderzoeksvermogen voor dat attribuut te zoeken en te specificeren, zoals **Bevat** (gebrek) of **Begint met**. U kunt een maximum van zes attributen specificeren die voor **worden toegelaten bevat** en zes attributen die voor **worden toegelaten begint met**. Voor bèta moet u er rekening mee houden dat de beheerder deze beperking niet afdwingt, maar dat deze wel wordt afgedwongen in API-zoekopdrachten.

   ![ specificeer onderzoeksvermogen ](./assets/search-filters-admin.png)

1. Zie de [ ontwikkelaardocumentatie ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#filtering-using-search-capability) leren hoe te om uw [!DNL Live Search] API vraag bij te werken gebruikend de nieuwe `contains` en `startsWith` onderzoeksmogelijkheden.

### Veldomschrijvingen

| Veld | Beschrijving |
|--- |--- |
| `Autocomplete` | Deze optie is standaard ingeschakeld en kan niet worden gewijzigd. Met `Autocomplete`, kunt u `contains` in de [ onderzoeksfilter ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#filtering) gebruiken. Hier retourneert de zoekquery in `contains` een zoekreactie van het type Automatisch aanvullen. Adobe raadt u aan dit type zoekopdracht te gebruiken voor beschrijvingsvelden die meestal meer dan 50 tekens bevatten. |
| `Contains` | Hiermee wordt een zoekopdracht met de tekst in een tekenreeks ingeschakeld in plaats van een automatische zoekopdracht. Gebruik `contains` in de [ onderzoeksfilter ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#filtering-using-search-capability). Verwijs naar de [ Beperkingen ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#limitations) voor meer informatie. |
| `Starts with` | Vraagt tekenreeksen aan die met een bepaalde waarde beginnen. Gebruik `startsWith` in de [ onderzoeksfilter ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#filtering-using-search-capability). |

## &#x200B;2. API-sleutels configureren

De Adobe Commerce API-sleutel en de bijbehorende persoonlijke sleutel zijn vereist om [!DNL Live Search] te verbinden met een installatie van Adobe Commerce. De API-sleutel wordt gegenereerd en onderhouden in de account van de [!DNL Commerce] -licentienemer, die deze kan delen met de ontwikkelaar of de systeemintegrator. De ontwikkelaar kan vervolgens de SaaS-gegevensruimten maken en beheren namens de licentiehouder. Als u al een set API-sleutels hebt, hoeft u deze niet opnieuw te genereren.

Leer hoe te om uw API sleutels in het [ 1} artikel van de Schakelaar van de Diensten van Commerce te vormen.](../landing/saas.md)

## &#x200B;3. Synchroniseer uw catalogusgegevens

[!DNL Live Search] verplaatst catalogusgegevens naar de Adobe-SaaS-infrastructuur. De gegevens worden geïndexeerd en de zoekresultaten worden vanuit deze index rechtstreeks aan de winkel geleverd. Afhankelijk van de grootte en complexiteit kan het indexeren 30 minuten tot een paar uur duren.

Voer de volgende opdrachten in deze volgorde uit om te beginnen met de eerste synchronisatie van uw catalogusgegevens naar SaaS-services:

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions
```

Wanneer u deze opdrachten uitvoert, begint de eerste synchronisatie van de catalogusgegevens met de SaaS-services.

>[!WARNING]
>
>Zoeken en bladeren door categorieën zijn niet beschikbaar tijdens synchroniseren. Afhankelijk van de grootte van de catalogus kan het proces meer dan 1 uur duren.

### Synchronisatievoortgang controleren

Gebruik het [ dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) om synchronisatievooruitgang te controleren. Dit dashboard biedt waardevolle inzichten in de beschikbaarheid van productgegevens in uw winkel, zodat deze direct aan klanten kunnen worden weergegeven.

![ Dashboard van het Beheer van Gegevens ](assets/data-management-dashboard.png)

U kunt synchronisatiebevelen ook in werking stellen en het synchronisatieproces problemen oplossen gebruikend [ Commerce CLI ](../data-export/data-export-cli-commands.md#troubleshooting) en de logboeken van de gegevensuitvoer.

#### Updates voor toekomstige producten

Na de eerste synchronisatie kan het tot 15 minuten duren voordat de incrementele productupdates beschikbaar komen voor het zoeken naar een winkel. Om meer te leren, zie {de Updates van het Product van 0} Streaming [ in de Indexerende documentatie.](indexing.md)

## &#x200B;4. Controleer of de gegevens zijn geëxporteerd

Als u wilt controleren of uw catalogusgegevens uit Adobe Commerce zijn geëxporteerd en met [!DNL Live Search] zijn gesynchroniseerd, hebt u een aantal opties:

- Zoek naar ingangen in de volgende lijsten:

   - `cde_products_feed`
   - `cde_product_attributes_feed`

  >[!NOTE]
  >
  >Als u een `table does not exist` -fout krijgt, zoekt u naar items in de tabellen `catalog_data_exporter_products` en `catalog_data_exporter_product_attributes` . Deze tabelnamen worden gebruikt in eerdere [!DNL Live Search] versies dan 4.2.1.

- Gebruik [ playground van GraphQL ](https://experienceleague.adobe.com/en/docs/commerce/live-search/live-search-admin/graphql) met de standaardvraag (zie [ verwijzing van GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) voor meer details) om het volgende te verifiëren:

   - Het aantal geretourneerde producten ligt dicht bij wat u voor de winkelweergave verwacht.
   - Facetten worden geretourneerd.

Voor extra hulp, zie [[!DNL Live Search]  niet gesynchroniseerde catalogus ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) in de Kennisbank van de Steun.

## &#x200B;5. Vorm de gegevens

Als u uw productgegevens correct configureert, bent u verzekerd van goede zoekresultaten voor uw klanten. In deze sectie schakelt u de widgets voor productlijsten in en wijst u categorieën toe.

### Widgets voor productaanbiedingen inschakelen

Wanneer u [!DNL Live Search] 4.0.0+ installeert, zijn de widgets voor productlijsten standaard ingeschakeld. Wanneer widgets zijn ingeschakeld, wordt een andere UI-component gebruikt voor de zoekresultaten en bladeren in categorieën door pagina&#39;s met productlijsten. Deze component UI doet directe vraag aan de [ Dienst API van de Catalogus ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/), die in snellere reactietijden resulteert.

Als u een [!DNL Live Search] -versie hebt die ouder is dan 4.0.0+, moet u de widget Productaanbieding handmatig inschakelen.

1. Van *Admin*, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Selecteer onder **[!UICONTROL Live Search]** de optie **[!UICONTROL Storefront Features]** .
1. Stel **[!UICONTROL Enable Product Listing Widgets]** in op `Yes` .

   ![ laat het Lijst van het Product toe Widgets ](assets/ls-admin-enable-widget.png)

Wanneer u deze configuratie wijzigt, verschijnt het bericht `Page cache is invalidated` . U moet de Magento Cache leegmaken om de wijziging op te slaan.

1. Heb toegang tot de [ pagina van het Beheer van het Geheime voorgeheugen ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) door één van het volgende te doen:

   - Klik op de koppeling **[!UICONTROL Cache Management]** in het bericht boven de werkruimte.
   - Voor _Admin_ sidebar, ga **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. Selecteer de **Configuratie** [!UICONTROL Cache Type] en klik **[!UICONTROL Flush Magento Cache]**.

   Wijzigingen in de winkel worden direct na het leegmaken van de cache aangebracht.

### Categorieën toewijzen

De producten die in [!DNL Live Search] zijn teruggekeerd moeten aan a [ worden toegewezen categorie ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). In Luma worden producten bijvoorbeeld ingedeeld in categorieën zoals &quot;Mannen&quot;, &quot;Vrouwen&quot; en &quot;Luma&quot;. Subcategorieën worden ook ingesteld voor Tops, Bottoms en Watches. Deze categorietoewijzingen verbeteren de granulariteit bij het filteren.

## &#x200B;6. Test de verbinding

Met uw catalogusgegevens nu in SaaS, test om ervoor te zorgen de productgegevens in de volgende scenario&#39;s zijn teruggekeerd:

- Het vak [!UICONTROL Search] retourneert de juiste resultaten
- Met bladeren door categorie worden de resultaten correct geretourneerd
- Factoren zijn als filters beschikbaar op pagina&#39;s met zoekresultaten

Als alles correct werkt, wordt [!DNL Live Search] geïnstalleerd, aangesloten en klaar te gebruiken.

Als u problemen tegenkomt in de winkel, controleert u het bestand `var/log/system.log` op API-communicatiefouten of -fouten aan de kant van de service.

Als u [!DNL Live Search] wilt toestaan via een firewall, voegt u `commerce.adobe.io` toe aan de lijst van gewenste personen.

## &#x200B;7. Controleer of gebeurtenissen gegevens vastleggen

Zorg ervoor dat de storefront-gebeurtenissen die op uw site zijn geïmplementeerd, werken. Deze controle is vooral belangrijk voor implementatie zonder kop.

- Herzie de [ gebeurtenissen ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#live-search) die voor [!DNL Live Search] worden vereist.
- Zorg ervoor dat het [ Levende dashboard van het Onderzoek ](performance.md) gegevens van uw niet-productiemilieu(s) toont.
- [ verifieer gebeurtenisinzameling ](../product-recommendations/verify.md). Terwijl deze pagina in de [!DNL Product Recommendations] -handleiding staat, zijn de verificatiestappen ook op [!DNL Live Search] van toepassing.

## &#x200B;8. Aanpassen voor je winkel

U hebt de extensie [!DNL Live Search] geïnstalleerd, gesynchroniseerd, gevalideerd en geconfigureerd. De volgende stap is ervoor te zorgen dat de [!DNL Live Search] widgets in overeenstemming zijn met het uiterlijk van uw winkel.

U kunt de popover- en PLP-widgets opmaken door desgewenst aangepaste CSS-regels te definiëren. Zie [ het Stijlen Popover Elementen ](storefront-popover.md#styling-popover-example) en [ product die pagina widget ](plp-styling.md#styling-example) van de lijst voorzien.

Als u de functionaliteit van de widgets wilt uitbreiden, is de broncode voor elke widget beschikbaar in een openbare reactie.
In dit scenario, kunt u JavaScript voor uw eigen behoeften aanpassen en dan uw douanecode ontvangen op uw CDN. Dit aangepaste script communiceert met de service [!DNL Live Search] en retourneert de resultaten zoals normaal, zodat u de functionaliteit van de widget kunt beheren.

- [ PLP widget repo ](https://github.com/adobe/storefront-product-listing-page)
- [ de bar van het Onderzoek repo ](https://github.com/adobe/storefront-search-as-you-type)

## [!DNL Live Search] bijwerken

Controleer voordat u [!DNL Live Search] bijwerkt de versie van [!DNL Live Search] die met Composer is geïnstalleerd.

```bash
composer show magento/module-live-search | grep version
```

Voer de volgende handelingen uit vanaf de opdrachtregel om [!DNL Live Search] bij te werken:

```bash
composer update magento/live-search --with-dependencies
```

Als u een update wilt uitvoeren naar een belangrijke versie zoals 3.1.1 en 4.0.0, bewerkt u het hoofdbestand [!DNL Composer] `.json` van het project als volgt:

1. Als de momenteel geïnstalleerde `magento/live-search` versie `3.1.1` of lager is en u een upgrade uitvoert naar versie `4.0.0` of hoger, voert u de volgende opdracht uit vóór de upgrade:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Voer de volgende opdracht uit voor informatie over de momenteel geïnstalleerde versie van `magento/live-search` :

   ```bash
   composer show magento/live-search
   ```

1. Open het hoofdbestand `composer.json` en zoek naar `magento/live-search` .

1. Werk in de sectie `require` het versienummer als volgt bij:

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. Opslaan `composer.json` . Voer vervolgens de volgende handelingen uit vanaf de opdrachtregel:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## [!DNL Live Search] verwijderen

Om [!DNL Live Search] te desinstalleren, verwijs naar [ modules van de Desinstallatie ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] pakketten

De extensie [!DNL Live Search] bestaat uit de volgende pakketten:

| Pakket | Beschrijving |
|--- |--- |
| `module-live-search` | Staat verkopers toe om hun onderzoeksmontages voor facetting, synoniemen, vraagregels, etc. te vormen, en verleent toegang tot read-only GraphQL playground om vragen van *te testen Admin*. |
| `module-live-search-adapter` | Routes onderzoeksverzoeken van de storefront aan de [!DNL Live Search] dienst en geeft de resultaten in de storefront terug. <br /> - de doorblader van de Categorie - Routes verzoekt van de storefront [ hoogste navigatie ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) aan de onderzoeksdienst.<br /> - Globale onderzoek - Routes verzoekt van het [ snelle onderzoek ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) gebied aan de [!DNL Live Search] dienst. Het snelzoekveld bevindt zich in de rechterbovenhoek van de winkelpagina. |
| `module-live-search-storefront-popover` | De pop-up &#39;&#39;Zoeken terwijl u typt&#39;&#39; vervangt de standaard snelle zoekopdracht en retourneert gegevens en miniaturen van de bovenste zoekresultaten. |

## [!DNL Live Search] afhankelijkheden

Het [!DNL Composer] -pakket voor het installeren van de extensie [!DNL Live Search] bevat de volgende moduleafhankelijkheden.

- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`

## Geavanceerde concepten

De volgende secties bieden geavanceerdere onderwerpen wanneer u [!DNL Live Search] en [!DNL Catalog Service] gebruikt.

### Endpoint

[!DNL Live Search] communiceert via het eindpunt op `https://catalog-service.adobe.io/graphql` .

Aangezien [!DNL Live Search] geen toegang heeft tot de volledige productdatabase, hebben de [!DNL Live Search] GraphQL en Commerce core GraphQL API&#39;s geen volledige pariteit.

Adobe raadt aan de SaaS APIs rechtstreeks aan te roepen — met name het eindpunt van de Catalogusservice.

- Verhoog de prestaties en verlaag de processorbelasting door het Commerce-database/Graphql-proces te omzeilen
- Haal voordeel uit de [!DNL Catalog Service] -federatie om [!DNL Live Search] , [!DNL Catalog Service] en [!DNL Product Recommendations] vanaf één eindpunt aan te roepen.

In sommige gevallen is het beter om [!DNL Catalog Service] op te roepen voor productdetails en vergelijkbare gevallen. Zie [ refineProduct ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/refine-product/) voor meer informatie.

Als u een aangepaste implementatie zonder kop hebt, checkt u de [!DNL Live Search] referentie-implementaties uit:

- [ PLP widget ](https://github.com/adobe/storefront-product-listing-page)
- [[!DNL Live Search]  gebied ](https://github.com/adobe/storefront-search-as-you-type)

Automatische verzameling van gegevens over gebruikersinteractie werkt niet standaard als u de standaardcomponenten niet gebruikt, zoals Zoekadapter, Luminagewidgets of AEM CIF-widgets. Adobe Sensei gebruikt deze verzamelde gegevens voor intelligent winkelen en het volgen van prestaties. Om deze kwestie op te lossen, moet u een douaneoplossing ontwikkelen om deze gegevensinzameling op een krantenloze manier uit te voeren.

De meest recente versie van [!DNL Live Search] gebruikt [!DNL Catalog Service] al.

### Taalondersteuning

[!DNL Live Search] -widgets ondersteunen de volgende talen:

|  |  |  |  |
|--- |--- |--- |--- |
| Taal | Regio | Taalcode | Magento-landinstelling |
| Bulgaars | Bulgarije | bg_BG | bg_BG |
| Catalaans | Spanje | ca_ES | ca_ES |
| Tsjechisch | Tsjechië | cs_CZ | cs_CZ |
| Deens | Denemarken | da_DK | da_DK |
| Duits | Duitsland | de_DE | de_DE |
| Grieks | Griekenland | el_GR | el_GR |
| Engels | Verenigd Koninkrijk | en_GB | en_GB |
| Engels | Verenigde Staten | nl_NL | nl_NL |
| Spaans | Spanje | es_ES | es_ES |
| Ests | Estland | et_EE | et_EE |
| Baskisch | Spanje | eu_ES | eu_ES |
| Perzisch | Iran | fa_IR | fa_IR |
| Fins | Finland | fi_FI | fi_FI |
| Frans | Frankrijk | fr_FR | fr_FR |
| Galicisch | Spanje | gl_ES | gl_ES |
| Hindi | India | hi_IN | hi_IN |
| Hongaars | Hongarije | hu_HU | hu_HU |
| Indonesische | Indonesië | id_ID | id_ID |
| Italiaans | Italië | it_IT | it_IT |
| Koreaans | Zuid-Korea | ko_KR | ko_KR |
| Litouws | Litouwen | lt_LT | lt_LT |
| Lets | Letland | lv_LV | lv_LV |
| Noors | Norway Bokmal | nb_NO | nb_NO |
| Nederlands | Nederland | nl_NL | nl_NL |
| Pools | Polen | pl_PL | pl_PL |
| Portugees | Brazilië | pt_BR | pt_BR |
| Portugees | Portugal | pt_PT | pt_PT |
| Roemeens | Roemenië | ro_RO | ro_RO |
| Russisch | Rusland | ru_RU | ru_RU |
| Zweeds | Zweden | sv_SE | sv_SE |
| Thai | Thailand | th_TH | th_TH |
| Turks | Turkije | tr_TR | tr_TR |
| Chinees | China | zh_CN | zh_Hans_CN |
| Chinees | Taiwan | zh_TW | zh_Hant_TW |

Als de widget detecteert dat de taalinstelling voor Commerce Admin overeenkomt met een ondersteunde taal, wordt deze taal standaard gebruikt. Anders is de widget standaard ingesteld op Engels. In de beheerfunctie wordt de taalinstelling geconfigureerd door te navigeren naar _[!UICONTROL Stores]_> [!UICONTROL Settings] >_[!UICONTROL Configuration]_ > _[!UICONTROL General]_> [!UICONTROL Country Options] .

Admins kan de taal van de [ onderzoeksindex ](settings.md#language) ook plaatsen, helpen betere onderzoeksresultaten verzekeren.

### Widget-codeopslagplaats

De code voor de productpagina widget en de [!DNL Live Search] veld widget is beschikbaar voor downloaden via GitHub.

Ontwikkelaars die toegang hebben tot de code, kunnen de werking en het uiterlijk van de code volledig aanpassen. Ze hosten de code op hun eigen servers, maar gebruiken toch de [!DNL Live Search] -service.

- [ PLP widget ](https://github.com/adobe/storefront-product-listing-page)
- [ bar van het Onderzoek ](https://github.com/adobe/storefront-search-as-you-type)

### Extensie Gegevens

Nadat [!DNL Live Search] is ingeschakeld, synchroniseert de extensie Gegevens exporteren Commerce-gegevens tussen de Commerce-toepassing en [!DNL Live Search] . Dit proces zorgt ervoor dat de meest recente Commerce-gegevens beschikbaar zijn in de winkel. In Admin, kunt u synchronisatiestatus controleren gebruikend het dashboard van het Beheer van Gegevens. U kunt het gegevensexportproces beheren en problemen oplossen met de Commerce CLI en de logboeken. Voor details, zie de [ Gids van de Uitvoer van Gegevens ](../data-export/overview.md).

### Inventory management

[!DNL Live Search] steunt [ Inventory management ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) mogelijkheden in Commerce (weet vroeger als Voorraad Multi-Source, of MSI). Om volledige steun toe te laten, moet u [ de gebiedsdeelmodule ](install.md#updating-live-search) aan versie 102.2.0+ bijwerken.`commerce-data-export`

[!DNL Live Search] retourneert een Booleaanse waarde die aangeeft of een product beschikbaar is in Inventory management, maar die geen informatie bevat over de bron die de voorraad heeft.

### Prijsindexering

[!DNL Live Search] klanten kunnen [ SaaS prijsindexeerder ](../price-index/price-indexing.md) gebruiken, die snellere de updates van de prijsverandering en synchronisatietijd verstrekt.

### Prijsondersteuning

[!DNL Live Search] -widgets ondersteunen de meeste, maar niet alle, door Adobe Commerce ondersteunde prijstypen.

Momenteel worden de basisprijzen ondersteund. Geavanceerde prijzen die niet worden ondersteund zijn:

- Kosten
- Minimale geadverteerde prijs

Kijk naar [ API Net ](../catalog-service/mesh.md) voor complexere prijsberekeningen.

Het prijsformaat steunt de scèneconfiguratie die binnen de instantie van Commerce plaatst: *Slaat* > Montages > *Configuratie* > Algemeen > *Algemene* > Lokale Opties > Scène op.

### Ondersteuning voor headless Storefront

U kunt desgewenst de module `module-data-services-graphql` installeren die de bestaande GraphQL-dekking van de toepassing uitbreidt, zodat deze velden bevat die vereist zijn voor het verzamelen van gedragsgegevens van de winkel.

```bash
composer require magento/module-data-services-graphql
```

Deze module voegt extra contexten aan de vragen van GraphQL toe:

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### B2B-ondersteuning

[!DNL Live Search] steunt [ functionaliteit B2B ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/guide-overview) met extra [ beperkingen ](boundaries-limits.md#b2b-and-category-permissions).

### PWA-ondersteuning

[!DNL Live Search] werkt met PWA Studio, maar gebruikers zien mogelijk kleine verschillen ten opzichte van andere Commerce-implementaties. De basisfunctionaliteit zoals zoeken en pagina met productlijsten werkt in Venia, maar sommige permutaties van Graphql werken mogelijk niet correct. Er kunnen ook prestatieverschillen zijn.

- De huidige PWA-implementatie van [!DNL Live Search] vereist meer verwerkingstijd om zoekresultaten te retourneren dan [!DNL Live Search] met de native Commerce-winkel.
- [!DNL Live Search] in PWA steunt [ gebeurtenis behandeling ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) niet. Het resultaat is dat zoekrapporten en intelligente koopwaar niet werken op PWA-winkelpagina&#39;s.
- Wanneer het gebruiken van [ PWA Studio ](https://developer.adobe.com/commerce/pwa-studio/), steunt GraphQL niet direct het filtreren op `description`, `name`, `short_description`, maar deze gebieden kunnen met een meer algemene filter zijn teruggekeerd.

Als u [!DNL Live Search] wilt gebruiken met PWA Studio, moeten integrators ook:

1. Installeer [ livessearch-storefront-utils ](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Stel de waarde `environmentId` in het `storeDetails` -object in.

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### Cookies

[!DNL Live Search] verzamelt gegevens over gebruikersinteractie als onderdeel van de basisfunctionaliteit en cookies worden gebruikt om deze gegevens op te slaan. Wanneer de gebruiker om het even welke gebruikersinformatie verzamelt, moet de gebruiker ermee instemmen om koekjes op te slaan. [!DNL Live Search] en [!DNL Product Recommendations] delen de gegevensstroom en dus hetzelfde cookiemechanisme. Lees meer over het in [ de Beperkingen van de Koekjescookie ](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/developer/setting-cookie).
