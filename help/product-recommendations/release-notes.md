---
title: '[!DNL Product Recommendations] Opmerkingen bij de release'
description: De recentste versieinformatie voor  [!DNL Product Recommendations]  van Adobe Commerce.
feature: Services, Recommendations, Release Notes
exl-id: 37404605-5b62-4c71-90d1-4f09e6105c4b
source-git-commit: 30cbe1ed54dd8a1149afe9f5f77b1b6f543b277e
workflow-type: tm+mt
source-wordcount: '1878'
ht-degree: 0%

---

# [!DNL Product Recommendations] Opmerkingen bij de release

De releaseopmerkingen bevatten updates voor de volgende [!DNL Product Recommendations] -modules:

* [!DNL Product Recommendations] metapack: `magento/product-recommendations`
* Ondersteuning voor Page Builder in de module [!DNL Product Recommendations] (optioneel): `magento/module-page-builder-product-recommendations`
* Ondersteuning voor het aanbevolen type visuele gelijkenis voor de module [!DNL Product Recommendations] (optioneel): `magento/module-visual-product-recommendations`

Er is ondersteuning voor de nieuwste versie. Opmerkingen bij de release voor oudere versies worden ter referentie verschaft.
De opmerkingen bij de release omvatten:

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Nieuwe eigenschappen
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Bevestigingen en verbeteringen
![&#x200B; Bug &#x200B;](../assets/bug.svg) Bekende kwesties

Zie de ontwikkelaardocumentatie [&#x200B; over productsteun &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) leren.

## Gehoste service-updates

Deze nota&#39;s beschrijven updates of bekende kwesties die buiten een versioned versie of verbeteringen aan de ontvangen dienst werden gepubliceerd of ontdekt.

_19 November, 2025_

![&#x200B; Nieuw &#x200B;](../assets/new.svg) u kunt tot 50 actieve aanbevelingen eenheden voor elk paginatype nu tot stand brengen. Voorheen was de limiet vijf.

_1 Oktober, 2025_

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde nieuwe genoemde sleutel van de gegevensopslag `ds-logged-in` voor klant het programma geopende gegevens.

_Januari 31, 2025_

![&#x200B; Nieuw &#x200B;](../assets/new.svg) is er een nieuw beleid van het gegevensbehoud voor ongevraagde catalogusgegevens in uw testende milieu. [&#x200B; leer meer &#x200B;](overview.md#catalog-data-retention-policy).

_Juni 28, 2024_

![&#x200B; Bug &#x200B;](../assets/bug.svg) Producten die aan het karretje van a [!DNL Product Recommendations] eenheid op de kartpagina worden toegevoegd worden niet verwijderd uit de lijst van geadviseerde producten wanneer de kartpagina opnieuw laadt.
![&#x200B; de Producten van de Bug &#x200B;](../assets/bug.svg) die van het karretje worden verwijderd blijven in de `cartSkus` serie bestaan tot de kartpagina herlaadt.

_18 juli 2023_

![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Product Recommendations] heeft nu een GraphQL [`recommendations` &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) vraag.

_25 April, 2023_

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) [!DNL Product Recommendations] klanten kunnen uit [&#x200B; prijs nu voordeel halen SaaS indexerend &#x200B;](../price-index/price-indexing.md).

## Huidige hoofdversie

### 6.5.0 magento/productaanbevelingen

_3 November, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) verbeterde hoe de eenheden van de productaanbeveling op verschillende milieu&#39;s interactie aangaan.

### Vorige versies

### 6.4.0 magento/productaanbevelingen

_17 September, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; bevor &#x200B;](../assets/fix.svg) een periodiek probleem op waar de eenheden van de productaanbeveling als gevolg van een fout van JavaScript zouden verdwijnen wanneer de lokale opslaggegevens niet beschikbaar waren. Deze correctie zorgt ervoor dat PREX geen fouten meer veroorzaakt als `ds-view-history-time-decay` ontbreekt in lokale opslag.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) werkte CDN URLS voor `recommendations-sdk` aan het `adobe.io` domein bij.

### 6.3.0 van magento/productaanbevelingen

_5 September, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde steun aan vertoningsmetriek voor [&#x200B; PageBuilder aanbeveling eenheden &#x200B;](page-builder.md) die in niet standaard opslagmeningen binnen de [&#x200B; werkruimte van de Aanbevelingen van het Product &#x200B;](workspace.md) worden gecreeerd.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Aanbevelingen van het Product respecteert nu volledig [&#x200B; wijze van de koekjesbeperking &#x200B;](setting-cookie.md) door gegevensinzameling en opslag in koekjes/lokale opslag te verhinderen wanneer de beperkingen worden toegelaten.

### 6.2.1. van magento/productaanbevelingen

_14 juli 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) aangebrachte verbeteringen aan het [&#x200B; voorproefaanbevelingen &#x200B;](./create.md#preview-recommendations) paneel.

### 6.2.0 van magento/productaanbevelingen

_4 April, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) werkte CDN URLs voor `recommendations-admin-ui` aan het `adobe.io` domein bij.

### 6.1.0 van magento/productaanbevelingen

_Maart 11, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde PHP 8.4 steun.

### 6.0.3 van de aanbevelingen voor magento/product

_6 November, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; beval &#x200B;](../assets/fix.svg) een kwestie vast waar de [&#x200B; categoriefilter &#x200B;](filters.md#category) categorieën omvatte die niet tot de huidige storeview behoorden.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een gebiedsdeelkwestie in het `magento/product-recommendations` metapakket.

### 6.0.2 van magento/productaanbevelingen

_Mei 9, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; beval &#x200B;](../assets/fix.svg) een kwestie waar het klikken van de **[!DNL Add to Cart]** knoop op een eenvoudig product binnen een eenheid van de Aanbevelingen van het Product de verkoopster aan de homepage eerder dan het blijven op de huidige pagina opnieuw richtte.
![&#x200B; Bug &#x200B;](../assets/bug.svg) Er is een bevestigingsfout die door het `referenceBlock` element in het `ProductRecommendations Layout` dossier van XML wordt veroorzaakt.

### 6.0.1 van magento/productaanbevelingen

_Maart 19, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde PHP 8.3 steun.

### 6.0.0 van magento/product-recommendations

_22 Februari, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Catalog Sync Dashboard] is nu [[!DNL Data Management Dashboard] &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard). Dit vernieuwde dashboard biedt inzichten in gegevensstromen voor [!DNL Product Recommendations] , [!DNL Live Search] en [!DNL Catalog Service] .
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie die controlefouten voor [!DNL Product Recommendations] veroorzaakte.

+++5.0.0 en eerdere

### 5.0.1 van magento/productaanbevelingen

_15 September, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde nieuwe modules om de [&#x200B; Indexer van de Prijs van de Zas &#x200B;](../price-index/price-indexing.md) te steunen.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde nieuwe modules van de gegevensuitvoer om het uitvoeren van meer producttypes met inbegrip van gebundelde producten en giftekaarten te steunen.
![&#x200B; Repareer &#x200B;](../assets/fix.svg) de lijstgrootte van de Producten en de feeds van de Prijs zijn zeer verminderd. Tabellen `catalog_data_exporter_products` en `catalog_data_exporter_product_prices` moeten aanzienlijk worden verkleind.

#### Bekende beperkingen

* De waarde `websiteCode` wordt onjuist geretourneerd als deze een onderstrepingsteken (_) bevat.

### 5.0.0 van magento/productaanbevelingen

_Maart 20.2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) Bijgewerkt [!DNL Product Recommendations] om Adobe Commerce 2.4.6 te steunen.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) Dit is een belangrijke versieversie. [&#x200B; geeft &#x200B;](install-configure.md#update) het wortel `composer.json` dossier voor uw project uit.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Product Recommendations] steunt nu volledige [&#x200B; Inventory management &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) mogelijkheden in Commerce (vroeger weet als Voorraad Multi-Source, of MSI). Om volledige steun toe te laten, moet u [&#x200B; de gebiedsdeelmodule &#x200B;](install-configure.md#update) aan versie 102.2.0+ bijwerken.`commerce-data-export`

### 4.0.1 van magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Repareren &#x200B;](../assets/fix.svg) vroeger, [!DNL Product Recommendations] zou een fout tonen wanneer de vertoningsmunt aan een niet-standaardmunt werd geschakeld. Wisselen naar andere valuta werkt nu goed.

### 4.0.0 van magento/product-recommendations

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde [&#x200B; gereedheidsindicatoren &#x200B;](create.md) om u te helpen de opleidingsvooruitgang van elk aanbevelingstype visualiseren.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) Dit is een belangrijke versieversie. [&#x200B; geeft &#x200B;](install-configure.md#update) het wortel `composer.json` dossier voor uw project uit. Deze versie vereist u ook om twee API sleutels te verstrekken wanneer het installeren en het vormen [!DNL Product Recommendations]: [&#x200B; een productiesleutel en een zandbaksleutel &#x200B;](../landing/saas.md).

#### Bekende beperkingen

* De waarde `websiteCode` wordt onjuist geretourneerd als deze een onderstrepingsteken (_) bevat.

### 3.3.7 van de aanbevelingen van magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde PHP 8.1 steun
![&#x200B; Nieuw &#x200B;](../assets/new.svg) Verbeterde beeldresizing zodat het rangschikken van beelden consistenter in het malplaatje van de verwijzingsvertoning wordt behandeld

### 3.3.6 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Geoptimaliseerde [!DNL Product Recommendations] metapakket door de gebiedsdelen uitdrukkelijk op te geven

### 3.3.5 van de aanbevelingen van magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde [&#x200B; B2B steun &#x200B;](onboarding.md#b2bsupport) in [!DNL Product Recommendations]
![&#x200B; Nieuw &#x200B;](../assets/new.svg) Toegevoegde nieuwe voer aan [&#x200B; gegevens van de synchronisatiecatalogus &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/user-guides/data-services/catalog-sync) aan de Diensten van Commerce via de bevellijn

### 3.3.3 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) Toegevoegde nieuwe [&#x200B; aanbevelingen types &#x200B;](type.md): Omzetting (mening aan kar), Omzetting (mening aan aankoop), en onlangs bekeken. Deze nieuwe aanbevelingen zijn beschikbaar in `magento/product-recommendations` module 3.2.2 en later.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie waar de Firewall van de Toepassing van het Web van Fastly (WAF) verkeerd een koekje blokkeerde
![&#x200B; Repareren &#x200B;](../assets/fix.svg) Vaste kwestie waar de producten die aan de niet-standaard Mening van de Opslag werden toegewezen niet in het _paneel van de Voorproef van het Product van Aanbevelingen_ werden getoond wanneer het creëren van een aanbeveling voor die specifieke Mening van de Opslag
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Vaste kwestie waar bepaalde namen van de aanbeveling eenheid in de Bouwer van de Pagina de aanbeveling eenheid om op de storefront te tonen verhinderden

### 3.3.2. van magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Vaste ontbrekende gebiedsdeel van 0&rbrace; herstellen &lbrace;voor B2B steun](../assets/fix.svg)

### 3.3.1. van magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde steun voor de prijsstelling van de klantengroep B2B. Wanneer u a [&#x200B; prijsfilter &#x200B;](filters.md) op een aanbevelingseenheid plaatst, zien de klanten B2B die het programma worden geopend de prijsstelling van de klantengroep die voor de getoonde producten wordt geplaatst.

### 3.3.0 van magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde steun voor de Laag van Gegevens van de Cliënt van Adobe om gedragsgegevensinzameling over de eigenschappen en de diensten van Adobe Commerce te standaardiseren. Zie [&#x200B; readme &#x200B;](https://github.com/adobe/commerce-events/blob/main/packages/storefront-events-collector/README.md) om meer te leren.

### 3.2.6 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) een modale fout van JavaScript
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie waar de Firewall van de Toepassing van het Web van Fastly (WAF) verkeerd een koekje blokkeerde

### 3.2.5 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) anders genoemd de Diensten van Magento aan [&#x200B; de Diensten van Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/user-guides/integration-services/saas) en betere bruikbaarheid in Admin

### 3.2.4 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) &quot;Onbekwaam om configureerbare gegevens van productopties&quot;fout terug te winnen wanneer het indexeren van productkenmerken

### 3.2.3 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) &quot;Onbekwaam om configureerbare gegevens van productopties&quot;fout tijdens de Synchronisatie van de Catalogus terug te winnen
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie waar de opslagcode niet correct werd geplaatst wanneer u &quot;toevoegde opslagcode aan URL&quot;configuratie
![&#x200B; Repareren &#x200B;](../assets/fix.svg) Verbeterde opsporing van de configuratieveranderingen van het Comité Admin om ervoor te zorgen dat deze veranderingen in de gegevens van de Synchronisatie van de Catalogus worden weerspiegeld

### 3.2.2. van magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) voegde de capaciteit toe aan [&#x200B; resultaten van de voorproefaanbeveling &#x200B;](create.md) in aanmaaktijd. Hiervoor moet u mogelijk de module bijwerken naar de meest recente versie.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) voegde de capaciteit toe om [&#x200B; &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/user-guides/data-services/catalog-sync) het proces van de catalogussynchronisatie van Admin te controleren en te beheren.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) toegevoegde filters [&#128279;](filters.md) om te controleren welke producten in aanbevelingen worden getoond.

![&#x200B; Nieuw &#x200B;](../assets/new.svg) voegde het [&#x200B; Visuele gelijkenis &#x200B;](type.md#visualsim) aanbevelingen type toe.

### 1.2.1 van magento/module-page-builder-product-recommendations for Page Builder

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde steun voor 3.2.0+ versie van de `magento/product-recommendations` module

### 3.1.0 van magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) voegde de capaciteit aan [&#x200B; opnieuw toe &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/user-guides/data-services/catalog-sync) uw catalogus aan diensten SaaS via bevellijn.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde steun voor prefixen van de gegevensbestandlijst
![&#x200B; Repareren &#x200B;](../assets/fix.svg) Verwijderde PHP 7.1 steun

### 3.0.8 van magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Repareren &#x200B;](../assets/fix.svg) Vaste een kwestie waar de gebeurtenissen voor gegevensinzameling werden verzonden alvorens de module werd gevormd, veroorzakend ongeldig verkeer

### 3.0.6 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) **(Beta)** omvat steun voor nieuw [&#x200B; Visuele gelijkenis &#x200B;](type.md#visualsim) type van aanbeveling.

### 1.0.0 van magento/module-visual-product-recommendations

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) **(Beta)** [&#x200B; Visuele gelijkenis &#x200B;](type.md#visualsim). Met het _Visuele gelijkenis_ aanbevelingen type, kunt u een aanbeveling eenheid aan uw pagina van het productdetail opstellen die producten toont die visueel gelijkaardig aan het product zijn dat wordt bekeken.

### 3.0.5 van magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) &quot;Onbekwaam om de gegevens van productopties&quot;fout terug te winnen die tijdens catalogusuitvoer kon voorkomen.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) het muntsymbool in de _3&rbrace; kolom van de Opbrengst &lbrace;op het_ dashboard wijst nu correct op de gevormde basismunt._[!DNL Product Recommendations]_

### 3.0.4 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Toegevoegde steun van 0&rbrace; Repareren voor Adobe Commerce 2.4.0](../assets/fix.svg)

### 3.0.3 van de aanbevelingen van magento/product

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) Verbeterde symboolimplementatie in storefront malplaatje

### 1.0.4 van magento/module-page-builder-product-recommendations for Page Builder

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde naam van de Aanbeveling van het Product wanneer het uitgeven van het inhoudstype van de Bouwer van de Pagina

### 3.0.2 magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) voegde een statuskolom op het net toe wanneer het selecteren van de eenheden van de Aanbeveling in de Bouwer van de Pagina
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie met onjuiste protocollen http/https in product en beeld URLs

### 3.0.1 van magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

Dit is een belangrijke versie. [&#x200B; geeft &#x200B;](install-configure.md#update) het wortel composer.json- dossier van uw project uit.

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Vetch [!DNL Product Recommendations] van afwisselende Gegevensruimten SaaS. Hierdoor kunt u [!DNL Product Recommendations] die in uw productomgeving is berekend, gebruiken in andere, niet-productieomgevingen. [&#x200B; het schakelen van de Spaties van Gegevens SaaS &#x200B;](settings.md) beschrijft verder deze eigenschap.

![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie waar de controle voor shoppers werd belemmerd gebruikend de Oorsprong van het Blok
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie die externe toe:voegen-aan-kart gebeurtenissen verzendt

### 1.0.3 van magento/module-page-builder-product-recommendations for Page Builder

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) steun van de Bouwer van de Pagina. Met de integratie van de Bouwer van de Pagina, kunt u de eenheden van de Aanbeveling nauwkeurig en korrelig in om het even welke willekeurige plaats op de Bouwer van de Pagina-geschreven inhoud plaatsen. U kunt ook zelf de koppen en aanbevelingen opmaken. Ga naar [&#x200B; Bouwer van de Pagina &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) voor meer informatie.

### 2.0.0 van magento/productaanbevelingen

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Algemene beschikbaarheidsversie!

+++

## Documentatie

Meer informatie over [!DNL Product Recommendations] en [!DNL Product Recommendations] ontwikkeling:

* [Gebruikershandleiding](overview.md)
* [&#x200B; Documentatie van de Ontwikkelaar &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/developer/development-overview)
