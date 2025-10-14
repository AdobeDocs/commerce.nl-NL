---
title: Indexeren
description: Leer hoe  [!DNL Live Search]  de eigenschappen van het productattribuut van indexen.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Indexeren

Het [!DNL Live Search] indexeringsproces leest door de catalogus voor productattributen en bouwt een index zodat de producten kunnen worden gezocht, worden gefiltreerd, en snel worden voorgesteld.

Eigenschappen van productkenmerken (metagegevens) bepalen:

* Hoe een attribuut in de catalogus kan worden gebruikt
* De vormgeving en het gedrag van de winkel
* De gegevens die zijn opgenomen in gegevensoverdrachtsbewerkingen

Het bereik van kenmerkmetagegevens is `website/store/store view` .

[!DNL Live Search] API staat een cliënt toe om door om het even welk productattribuut te sorteren dat het [&#x200B; storefront bezit &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/product-attributes/product-attributes) `Use in Search` heeft die aan `Yes` in Adobe Commerce Admin wordt geplaatst. Wanneer deze optie is ingeschakeld, kan `Search Weight` worden ingesteld voor het kenmerk.

[!DNL Live Search] indexeert geen verwijderde producten of producten die zijn ingesteld op `Not Visible Individually` .

>[!NOTE]
>
> De klanten van Commerce met [!DNL Live Search] kunnen uit snellere prijsveranderingen en synchronisatietijd op hun websites met [&#x200B; SaaS prijsindexer &#x200B;](../price-index/price-indexing.md) voordeel halen.

## Indexeringsleiding

De client roept de zoekservice van de storefront aan om (filterbare, sorteerbare) indexmetagegevens op te halen. Slechts doorzoekbare productattributen met het *Gebruik in Gelaagd die bezit van de Navigatie* aan `Filterable (with results)` wordt geplaatst en *Gebruik voor het Sorteren in het Lijst van het Product* aan `Yes` wordt geplaatst kan door de onderzoeksdienst worden geroepen.

Om een dynamische vraag te construeren, moet de onderzoeksdienst weten welke attributen doorzoekbaar en hun [&#x200B; gewicht &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/catalog/search/search-results) zijn. [!DNL Live Search] geeft Adobe Commerce-zoekdikten (1-10, waarbij 10 de hoogste prioriteit heeft). De lijst met gegevens die met de catalogusservice worden gesynchroniseerd en gedeeld, vindt u in het schema, dat wordt gedefinieerd in:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] het indexeren diagram van het cliëntonderzoek &#x200B;](assets/indexing-pipeline.svg)

1. Controleer de handelaar op [!DNL Live Search] machtiging.
1. Winkelweergaven ophalen met wijzigingen in kenmerkmetagegevens.
1. Kenmerken voor indexering opslaan.
1. Indexeer de zoekindex opnieuw.

### Volledige index

Wanneer [!DNL Live Search] tijdens het instappen wordt gevormd en gesynchroniseerd, kan het tot 60 minuten duren om de aanvankelijke index te bouwen. De index van grote catalogi kan langer duren. Het proces begint nadat `cron` de feed heeft verzonden en de bewerking heeft voltooid.

De volgende gebeurtenissen activeren een volledige synchronisatie en de opbouw van de index:

* Onboarding [&#x200B; synchronisatie van catalogusgegevens &#x200B;](install.md#synchronize-catalog-data)
* Wijzigingen in metagegevens voor kenmerken

Als u bijvoorbeeld de eigenschap `Use in Search` van het kenmerk `color` wijzigt van `No` in `Yes` , worden de metagegevens van het kenmerk gewijzigd in `searchable=true` en wordt een volledige synchronisatie en herindex geactiveerd. De volgende kenmerkmetagegevens activeren een volledige synchronisatie en worden opnieuw geordend wanneer ze worden gewijzigd:

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Streaming productupdates

Nadat de aanvankelijke index tijdens [&#x200B; onboarding &#x200B;](install.md#synchronize-catalog-data) wordt gebouwd, worden de volgende stijgende productupdates onophoudelijk gesynchroniseerd en opnieuw bepaald:

* Nieuwe producten toegevoegd aan de catalogus
* Wijzigingen in productkenmerkwaarden

Het toevoegen van een nieuwe staalwaarde aan het kenmerk `color` wordt bijvoorbeeld verwerkt als een streaming productupdate.

Workflow voor gestreamde updates:

1. Bijgewerkte producten worden gesynchroniseerd van de Adobe Commerce-instantie naar de catalogusservice.
1. De indexerende dienst zoekt onophoudelijk productupdates van de catalogusdienst. Bijgewerkte producten worden geïndexeerd wanneer ze in de catalogusservice worden geleverd.
1. Het kan tot 15 minuten duren voordat een productupdate beschikbaar wordt in [!DNL Live Search].

#### Updates die de zichtbaarheid van producten beïnvloeden

Wanneer u updates uitvoert aan [!DNL Live Search] de configuratiemontages van Admin, de configuratiemontages van Adobe Commerce Admin, of updates aan catalogusgegevens, kunt u een vertraging verwachten alvorens die veranderingen op de storefront verschijnen.

In de volgende tabel worden verschillende wijzigingen beschreven. De wachttijd wordt bij benadering bepaald voordat deze in de winkel worden weergegeven.

| Updates | Vertraging tot zichtbaar op de winkel |
|---|---|
| [!DNL Live Search] Wijzigingen in facetten, prijsinstellingen, zoekregels of regels voor het verhandelen van categorieën beheren. | 15-20 minuten. |
| [!DNL Live Search] Wijzigingen in beheer die opnieuw moeten worden gedexeerd: taalinstellingen of synoniemen. | Tot 15 minuten nadat de redexatie is voltooid. |
| Adobe Commerce Admin-wijzigingen waarvoor een volledige redex vereist is: metagegevens voor doorzoekbare, sorteerbare of filterbare kenmerken | Tot 15 minuten nadat de redexatie is voltooid. |
| Incrementele wijzigingen in catalogusgegevens die niet opnieuw hoeven te worden geanalyseerd: productinventaris, prijs, naam, enzovoort. | Tot 15 minuten nadat de Elastic Search-index is bijgewerkt met de meest recente gegevens. |

## Clientzoekopdracht

[!DNL Live Search] API staat een cliënt toe om door om het even welk sorteerbaar productattribuut te sorteren door het [&#x200B; storefront bezit &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/product-attributes/product-attributes) te plaatsen, *Gebruikt voor het sorteren in productlijsten* aan `Yes`. Afhankelijk van het thema, veroorzaakt dit het plaatsen de attributen om als optie in de [&#x200B; Soort door &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/catalog/navigation/navigation) pagineringscontrole op cataloguspagina&#39;s worden omvat. Tot 200 productattributen kunnen door [!DNL Live Search] worden geïndexeerd, met [&#x200B; storefront eigenschappen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/product-attributes/product-attributes) die doorzoekbaar en filterbaar zijn.

De indexmeta-gegevens worden opgeslagen in de indexerende pijpleiding en door de onderzoeksdienst toegankelijk.

![[!DNL Live Search] API-diagram voor indexmetagegevens &#x200B;](assets/index-metadata-api.svg)

### Workflow voor sorteerbare kenmerken

1. De client roept de zoekservice aan.
1. De onderzoeksdienst roept de Dienst van Admin van het Onderzoek.
1. De onderzoeksdienst roept de indexerende pijpleiding.

## Geïndexeerd voor alle producten

De volgorde van de velden in deze lijst geeft de typische volgorde van kolommen in geëxporteerde productgegevens weer.

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

Het volgende gebied wordt geïndexeerd voor alle configureerbare producten:

* `childrenSkus`
