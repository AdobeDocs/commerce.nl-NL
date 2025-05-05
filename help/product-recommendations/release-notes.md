---
title: '[!DNL Product Recommendations] Opmerkingen bij de release'
description: De recentste versieinformatie voor  [!DNL Product Recommendations]  van Adobe Commerce.
feature: Services, Recommendations, Release Notes
exl-id: 37404605-5b62-4c71-90d1-4f09e6105c4b
source-git-commit: ea7618805596ac4100f5080efe32793feea001df
workflow-type: tm+mt
source-wordcount: '1460'
ht-degree: 0%

---

# [!DNL Product Recommendations] Opmerkingen bij de release

De releaseopmerkingen bevatten updates voor de volgende [!DNL Product Recommendations] -modules:

* [!DNL Product Recommendations] metapack: `magento/product-recommendations`
* Ondersteuning voor Page Builder in de module [!DNL Product Recommendations] (optioneel): `magento/module-page-builder-product-recommendations`
* Ondersteuning voor het aanbevolen type visuele gelijkenis voor de module [!DNL Product Recommendations] (optioneel): `magento/module-visual-product-recommendations`

Er wordt ondersteuning geboden voor de belangrijkste uitgebrachte versie. Opmerkingen bij de release voor oudere versies worden ter referentie verschaft.
De opmerkingen bij de release omvatten:

![ Nieuwe ](../assets/new.svg) Nieuwe eigenschappen
![ bevestig ](../assets/fix.svg) Bevestigingen en verbeteringen
![ Bug ](../assets/bug.svg) Bekende kwesties

Zie de ontwikkelaardocumentatie [ over productsteun ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) leren.

## Gehoste service-updates

Deze nota&#39;s beschrijven updates of bekende kwesties die buiten een versioned versie of verbeteringen aan de ontvangen dienst werden gepubliceerd of ontdekt.

_Januari 31, 2025_

![ Nieuw ](../assets/new.svg) is er een nieuw beleid van het gegevensbehoud voor ongevraagde catalogusgegevens in uw testende milieu. [ leer meer ](overview.md#catalog-data-retention-policy).

_Juni 28, 2024_

![ Bug ](../assets/bug.svg) Producten die aan het karretje van a [!DNL Product Recommendations] eenheid op de kartpagina worden toegevoegd worden niet verwijderd uit de lijst van geadviseerde producten wanneer de kartpagina opnieuw laadt.
![ de Producten van de Bug ](../assets/bug.svg) die van het karretje worden verwijderd blijven in de `cartSkus` serie bestaan tot de kartpagina herlaadt.

_18 juli 2023_

![ Nieuw ](../assets/new.svg) [!DNL Product Recommendations] heeft nu een GraphQL [`recommendations` ](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) vraag.

_25 April, 2023_

![ Nieuwe ](../assets/new.svg) [!DNL Product Recommendations] klanten kunnen uit [ prijs nu voordeel halen SaaS indexerend ](../price-index/price-indexing.md).

## Huidige hoofdversie

### 6.2.0 van magento/productaanbevelingen

_4 April, 2025_

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuw ](../assets/new.svg) werkte CDN URLs voor `recommendations-admin-ui` aan het `adobe.io` domein bij.

### Vorige versies

### 6.1.0 van magento/productaanbevelingen

_Maart 11, 2025_

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Toegevoegde PHP 8.4 steun.

### 6.0.3 van de aanbevelingen voor magento/product

_6 November, 2024_

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ beval ](../assets/fix.svg) een kwestie vast waar de [ categoriefilter ](filters.md#category) categorieën omvatte die niet tot de huidige storeview behoorden.
![ bevestig ](../assets/fix.svg) een gebiedsdeelkwestie in het `magento/product-recommendations` metapakket.

### 6.0.2 van magento/productaanbevelingen

_Mei 9, 2024_

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ beval ](../assets/fix.svg) een kwestie waar het klikken van de **[!DNL Add to Cart]** knoop op een eenvoudig product binnen een eenheid van de Aanbevelingen van het Product de verkoopster aan de homepage eerder dan het blijven op de huidige pagina opnieuw richtte.
![ Bug ](../assets/bug.svg) Er is een bevestigingsfout die door het `referenceBlock` element in het `ProductRecommendations Layout` dossier van XML wordt veroorzaakt.

### 6.0.1 van magento/productaanbevelingen

_Maart 19, 2024_

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Toegevoegde PHP 8.3 steun.

### 6.0.0 van magento/product-recommendations

_22 Februari, 2024_

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuw ](../assets/new.svg) [!DNL Catalog Sync Dashboard] is nu [[!DNL Data Management Dashboard] ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Dit vernieuwde dashboard biedt inzichten in gegevensstromen voor [!DNL Product Recommendations] , [!DNL Live Search] en [!DNL Catalog Service] .
![ bevestig ](../assets/fix.svg) een kwestie die controlefouten voor [!DNL Product Recommendations] veroorzaakte.

+++5.0.0 en eerder

### 5.0.1 van magento/productaanbevelingen

_15 September, 2023_

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Toegevoegde nieuwe modules om de [ Indexer van de Prijs van de Zas ](../price-index/price-indexing.md) te steunen.
![ Nieuwe ](../assets/new.svg) Toegevoegde nieuwe modules van de gegevensuitvoer om het uitvoeren van meer producttypes met inbegrip van gebundelde producten en giftekaarten te steunen.
![ Repareer ](../assets/fix.svg) de lijstgrootte van de Producten en de feeds van de Prijs zijn zeer verminderd. Tabellen `catalog_data_exporter_products` en `catalog_data_exporter_product_prices` moeten aanzienlijk worden verkleind.

#### Bekende beperkingen

* De waarde `websiteCode` wordt onjuist geretourneerd als deze een onderstrepingsteken (_) bevat.

### 5.0.0 van magento/productaanbevelingen

_Maart 20.2023_

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuw ](../assets/new.svg) Bijgewerkt [!DNL Product Recommendations] om Adobe Commerce 2.4.6 te steunen.
![ Nieuw ](../assets/new.svg) Dit is een belangrijke versieversie. [ geeft ](install-configure.md#update) het wortel `composer.json` dossier voor uw project uit.
![ Nieuw ](../assets/new.svg) [!DNL Product Recommendations] steunt nu volledige [ Inventory management ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) mogelijkheden in Commerce (vroeger weet als Voorraad Multi-Source, of MSI). Om volledige steun toe te laten, moet u [&#128279;](install-configure.md#update) de gebiedsdeelmodule `commerce-data-export` aan versie 102.2.0+ bijwerken.

### 4.0.1 van magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Repareren ](../assets/fix.svg) vroeger, [!DNL Product Recommendations] zou een fout tonen wanneer de vertoningsmunt aan een niet-standaardmunt werd geschakeld. Wisselen naar andere valuta werkt nu goed.

### 4.0.0 van magento/product-recommendations

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Toegevoegde [ gereedheidsindicatoren ](create.md) om u te helpen de opleidingsvooruitgang van elk aanbevelingstype visualiseren.
![ Nieuw ](../assets/new.svg) Dit is een belangrijke versieversie. [ geeft ](install-configure.md#update) het wortel `composer.json` dossier voor uw project uit. Deze versie vereist u ook om twee API sleutels te verstrekken wanneer het installeren en het vormen [!DNL Product Recommendations]: [ een productiesleutel en een zandbaksleutel ](../landing/saas.md).

#### Bekende beperkingen

* De waarde `websiteCode` wordt onjuist geretourneerd als deze een onderstrepingsteken (_) bevat.

### 3.3.7 van de aanbevelingen van magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Toegevoegde PHP 8.1 steun
![ Nieuw ](../assets/new.svg) Verbeterde beeldresizing zodat het rangschikken van beelden consistenter in het malplaatje van de verwijzingsvertoning wordt behandeld

### 3.3.6 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Geoptimaliseerde [!DNL Product Recommendations] metapakket door de gebiedsdelen uitdrukkelijk op te geven

### 3.3.5 van de aanbevelingen van magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Toegevoegde [ B2B steun ](onboarding.md#b2bsupport) in [!DNL Product Recommendations]
![ Nieuw ](../assets/new.svg) Toegevoegde nieuwe voer aan [ gegevens van de synchronisatiecatalogus ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/data-services/catalog-sync) aan de Diensten van Commerce via de bevellijn

### 3.3.3 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuw ](../assets/new.svg) Toegevoegde nieuwe [ aanbevelingen types ](type.md): Omzetting (mening aan kar), Omzetting (mening aan aankoop), en onlangs bekeken. Deze nieuwe aanbevelingen zijn beschikbaar in `magento/product-recommendations` module 3.2.2 en later.
![ bevestig ](../assets/fix.svg) een kwestie waar de Firewall van de Toepassing van het Web van Fastly (WAF) verkeerd een koekje blokkeerde
![ Repareren ](../assets/fix.svg) Vaste kwestie waar de producten die aan de niet-standaard Mening van de Opslag werden toegewezen niet in het _paneel van de Voorproef van het Product van Aanbevelingen_ werden getoond wanneer het creëren van een aanbeveling voor die specifieke Mening van de Opslag
![ bevestig ](../assets/fix.svg) Vaste kwestie waar bepaalde namen van de aanbeveling eenheid in de Bouwer van de Pagina de aanbeveling eenheid om op de storefront te tonen verhinderden

### 3.3.2. van magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![&#128279;](../assets/fix.svg) Vaste ontbrekende gebiedsdeel van 0&rbrace; herstellen &lbrace;voor B2B steun

### 3.3.1. van magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Toegevoegde steun voor de prijsstelling van de klantengroep B2B. Wanneer u a [ prijsfilter ](filters.md) op een aanbevelingseenheid plaatst, zien de klanten B2B die het programma worden geopend de prijsstelling van de klantengroep die voor de getoonde producten wordt geplaatst.

### 3.3.0 van magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Toegevoegde steun voor de Laag van Gegevens van de Cliënt van Adobe om gedragsgegevensinzameling over de eigenschappen en de diensten van Adobe Commerce te standaardiseren. Zie [ readme ](https://github.com/adobe/commerce-events/blob/main/packages/storefront-events-collector/README.md) om meer te leren.

### 3.2.6 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ bevestig ](../assets/fix.svg) een modale fout van JavaScript
![ bevestig ](../assets/fix.svg) een kwestie waar de Firewall van de Toepassing van het Web van Fastly (WAF) verkeerd een koekje blokkeerde

### 3.2.5 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuw ](../assets/new.svg) anders genoemd de Diensten van Magento aan [ de Diensten van Commerce ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/integration-services/saas) en betere bruikbaarheid in Admin

### 3.2.4 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ bevestig ](../assets/fix.svg) &quot;Onbekwaam om configureerbare gegevens van productopties&quot;fout terug te winnen wanneer het indexeren van productkenmerken

### 3.2.3 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ bevestig ](../assets/fix.svg) &quot;Onbekwaam om configureerbare gegevens van productopties&quot;fout tijdens de Synchronisatie van de Catalogus terug te winnen
![ bevestig ](../assets/fix.svg) een kwestie waar de opslagcode niet correct werd geplaatst wanneer u &quot;toevoegde opslagcode aan URL&quot;configuratie
![ Repareren ](../assets/fix.svg) Verbeterde opsporing van de configuratieveranderingen van het Comité Admin om ervoor te zorgen dat deze veranderingen in de gegevens van de Synchronisatie van de Catalogus worden weerspiegeld

### 3.2.2. van magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuw ](../assets/new.svg) voegde de capaciteit toe aan [ resultaten van de voorproefaanbeveling ](create.md) in aanmaaktijd. Hiervoor moet u mogelijk de module bijwerken naar de meest recente versie.
![ Nieuw ](../assets/new.svg) voegde de capaciteit toe om [&#128279;](https://experienceleague.adobe.com/en/docs/commerce/user-guides/data-services/catalog-sync) het proces van de catalogussynchronisatie van Admin te controleren en te beheren.
 Nieuwe [ toegevoegde filters ](filters.md) om te controleren welke producten in aanbevelingen worden getoond.
![&#128279;](../assets/new.svg)
![ Nieuw ](../assets/new.svg) voegde het [ Visuele gelijkenis ](type.md#visualsim) aanbevelingen type toe.

### 1.2.1 van magento/module-page-builder-product-recommendations for Page Builder

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Toegevoegde steun voor 3.2.0+ versie van de `magento/product-recommendations` module

### 3.1.0 van magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuw ](../assets/new.svg) voegde de capaciteit aan [ opnieuw toe ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/data-services/catalog-sync) uw catalogus aan diensten SaaS via bevellijn.
![ Nieuwe ](../assets/new.svg) Toegevoegde steun voor prefixen van de gegevensbestandlijst
![ Repareren ](../assets/fix.svg) Verwijderde PHP 7.1 steun

### 3.0.8 van magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Repareren ](../assets/fix.svg) Vaste een kwestie waar de gebeurtenissen voor gegevensinzameling werden verzonden alvorens de module werd gevormd, veroorzakend ongeldig verkeer

### 3.0.6 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuw ](../assets/new.svg) **(Beta)** omvat steun voor nieuw [ Visuele gelijkenis ](type.md#visualsim) type van aanbeveling.

### 1.0.0 van magento/module-visual-product-recommendations

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) **(Beta)** [ Visuele gelijkenis ](type.md#visualsim). Met het _Visuele gelijkenis_ aanbevelingen type, kunt u een aanbeveling eenheid aan uw pagina van het productdetail opstellen die producten toont die visueel gelijkaardig aan het product zijn dat wordt bekeken.

### 3.0.5 van magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ bevestig ](../assets/fix.svg) &quot;Onbekwaam om de gegevens van productopties&quot;fout terug te winnen die tijdens catalogusuitvoer kon voorkomen.
![ bevestig ](../assets/fix.svg) het muntsymbool in de _3&rbrace; kolom van de Opbrengst &lbrace;op het&#x200B;_[!DNL Product Recommendations]_ dashboard wijst nu correct op de gevormde basismunt._

### 3.0.4 van de aanbevelingen inzake magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![&#128279;](../assets/fix.svg) Toegevoegde steun van 0&rbrace; Repareren voor Adobe Commerce 2.4.0

### 3.0.3 van de aanbevelingen van magento/product

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ bevestig ](../assets/fix.svg) Verbeterde symboolimplementatie in storefront malplaatje

### 1.0.4 van magento/module-page-builder-product-recommendations for Page Builder

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Toegevoegde naam van de Aanbeveling van het Product wanneer het uitgeven van het inhoudstype van de Bouwer van de Pagina

### 3.0.2 magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuw ](../assets/new.svg) voegde een statuskolom op het net toe wanneer het selecteren van de eenheden van de Aanbeveling in de Bouwer van de Pagina
![ bevestig ](../assets/fix.svg) een kwestie met onjuiste protocollen http/https in product en beeld URLs

### 3.0.1 van magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

Dit is een belangrijke versie. [ geeft ](install-configure.md#update) het wortel composer.json- dossier van uw project uit.

![ Nieuwe ](../assets/new.svg) Vetch [!DNL Product Recommendations] van afwisselende Gegevensruimten SaaS. Hierdoor kunt u [!DNL Product Recommendations] die in uw productomgeving is berekend, gebruiken in andere, niet-productieomgevingen. [ het schakelen van de Spaties van Gegevens SaaS ](settings.md) beschrijft verder deze eigenschap.

![ bevestig ](../assets/fix.svg) een kwestie waar de controle voor shoppers werd belemmerd gebruikend de Oorsprong van het Blok
![ bevestig ](../assets/fix.svg) een kwestie die externe toe:voegen-aan-kart gebeurtenissen verzendt

### 1.0.3 van magento/module-page-builder-product-recommendations for Page Builder

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) steun van de Bouwer van de Pagina. Met de integratie van de Bouwer van de Pagina, kunt u de eenheden van de Aanbeveling nauwkeurig en korrelig in om het even welke willekeurige plaats op de Bouwer van de Pagina-geschreven inhoud plaatsen. U kunt ook zelf de koppen en aanbevelingen opmaken. Ga naar [ Bouwer van de Pagina ](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) voor meer informatie.

### 2.0.0 van magento/productaanbevelingen

[!BADGE &#x200B; Gesteund &#x200B;]{type=Informative tooltip="Ondersteund"}

![ Nieuwe ](../assets/new.svg) Algemene beschikbaarheidsversie!

+++

## Documentatie

Meer informatie over [!DNL Product Recommendations] en [!DNL Product Recommendations] ontwikkeling:

* [Gebruikershandleiding](overview.md)
* [ Documentatie van de Ontwikkelaar ](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/developer/development-overview)
