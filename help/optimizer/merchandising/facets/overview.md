---
title: Overzicht van facetten
description: Leer over facetten in  [!DNL Adobe Commerce Optimizer]  en hoe zij onderzoeksresultaten verbeteren.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: cf16626e-8f85-47ca-b973-891b16c31fe3
source-git-commit: ad8fb7d1d7e1ad124647ba84377079dcfbd46a3c
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Facetten

Facets is een methode voor het filteren van hoge prestaties waarbij meerdere dimensies van kenmerkwaarden worden gebruikt als zoekcriteria.

![ Gefilterde onderzoeksresultaten ](../../assets/storefront-search-results-run.png)

Binnen een facet kunnen kopers meerdere opties selecteren, zoals &quot;Standaard&quot; en &quot;Snug&quot; onder &quot;Stijl&quot; en in de zoekresultaten worden alleen die stijlen weergegeven. Op dezelfde manier geldt dat als een winkelier opties selecteert in verschillende facetten, zoals &quot;Standaard&quot; onder &quot;Stijl&quot; en &quot;Binnenshuis&quot; onder &quot;Klimaat&quot;, de zoekresultaten worden bijgewerkt om die geselecteerde stijl en dat geselecteerde klimaat weer te geven.

Elke gedefinieerde facet kan worden gebruikt als een URL-parameter en de resultaten worden gefilterd op basis van de parameterwaarden: `http://yourstore.com?brand=acme&color=red` .

## Facetaggregatie

Facetsamenvoeging wordt als volgt uitgevoerd: als de winkel drie facetten (categorieën, kleur en prijs) heeft en de winkelfilters op alle drie (kleur = blauw, de prijs is van $10.00-50.00, categorieën = `promotions`).

- `categories` aggregatie - aggregeert `categories` en past vervolgens de filters `color` en `price` toe, maar niet het filter `categories` .
- `color` aggregatie - aggregeert `color` en past vervolgens de filters `price` en `categories` toe, maar niet het filter `color` .
- `price` aggregatie - aggregeert `price` en past vervolgens de filters `color` en `categories` toe, maar niet het filter `price` .

## Standaardkenmerkwaarden

De volgende productkenmerken worden standaard gebruikt door [!DNL Adobe Commerce Optimizer] en ingeschakeld.

| Eigenschap | Beschrijving | Kenmerk |
|---|---|---|
| Sorteerbaar | Wordt gebruikt voor sorteren in de productlijst | `price` |
| Doorzoekbaar | Gebruiken in Zoeken | `price` <br />`sku`<br />`name` |

Zie de [ Meta-gegevens API van de Ingestie van Gegevens ](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/#metadata) om meer over productattributen en hun eigenschappen te leren.

## Standaardeigenschappen van niet-systeemkenmerken

In de volgende tabel worden de standaardzoekeigenschappen en filterbare eigenschappen van niet-systeemkenmerken weergegeven. Het plaatsen van het *Gebruik in het 1&rbrace; attributenbezit van het Onderzoek &lbrace;aan* maakt de attributen doorzoekbaar in `Yes`.[!DNL Adobe Commerce Optimizer]

| Kenmerkcode | Doorzoekbaar |
|--- |--- |
| activiteit | Ja |
| attributes_brand | Ja |
| merk | Ja |
| klimaat | Ja |
| halsband | Ja |
| kleur | Ja |
| kosten | Ja |
| eco_collection |
| sekse | Ja |
| fabrikant | Ja |
| materiaal | Ja |
| doel | Ja |
| riem_tassen | Ja |
| style_general | Ja |

## Standaardsysteemkenmerkeigenschappen

In de volgende tabel worden de standaardzoekeigenschappen en filterbare eigenschappen van systeemkenmerken weergegeven.

| Kenmerkcode | Doorzoekbaar |
|--- |--- |
| allow_open_amount | Ja |
| beschrijving | Ja |
| name | Ja |
| prijs | Ja |
| short_description | Ja |
| sku | Ja |
| status | Ja |
| tax_class_id | Ja |
| url_key | Ja |
| gewicht | Ja |
