---
title: Belastingsklasse, kenmerkset en voorraadkenmerken toevoegen
description: Leer hoe u de gegevens van de productfeed kunt uitbreiden met kenmerken voor belastingclassificatie, kenmerkset en geavanceerde voorraadinstellingen
role: Admin, Developer
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/
source-git-commit: dd8f518028c9f2025606e6620fc20156fceac9ce
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Belastingsklasse, kenmerkset en voorraadkenmerken toevoegen

De module Adobe Commerce Extra productkenmerken breidt de invoer van productgegevens uit. Het bevat aanvullende productkenmerken van Adobe Commerce-productconfiguraties:

* [ Belastingclassificatie ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/taxes/tax-class)
* [ Reeks van Attributen ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/create/attribute-sets)
* [ Overzicht ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/product-options#advanced-product-options)

Nadat de module is geïnstalleerd, werkt deze automatisch. De aanvullende kenmerken worden tijdens productsynchronisatie vastgelegd en geëxporteerd. Geen extra configuratie wordt vereist.

## Belangrijkste voordelen

* **Automatische verhoging**: Verrijkt productvoer met belastingklasse, kenmerkreeks, en inventarisattributen
* **Naadloze integratie**: Verstrekt essentiële context voor externe systemen en de diensten
* **Nul configuratie**: De werken onmiddellijk na installatie
* **updates in real time**: Synchroniseert automatisch met productveranderingen

## Functies en geëxporteerde kenmerken

De module voegt drie extra kenmerken toe aan uw bestaande productgegevensfeeds:

* `ac_tax_class`
* `ac_attribute_set`
* `ac_inventory`

### &#x200B;1. Informatie over belastingklassen (`ac_tax_class`)

**Doel**: Verstrekt de informatie van de belastingclassificatie voor elk product

**Formaat van Gegevens**: De waarde van het koord die de naam van de belastingklasse bevatten

**output van het Voorbeeld**:

```json
{
  "attributes": [
    {
      "code": "ac_tax_class",
      "values": ["Taxable Goods"]
    }
  ]
}
```

**gevallen van het Gebruik**:

Wanneer u gegevens van belastingklassen exporteert naar de catalogusservices van Commerce, worden deze gegevens beschikbaar voor toepassingen die ondersteuning bieden voor:

* Rapportering over belastingnaleving
* Integratie met externe diensten voor belastingberekening
* Productcategorie voor boekhoudsystemen

### &#x200B;2. Informatie over kenmerkensets (`ac_attribute_set`)

**Doel**: Identificeert welke kenmerkreeks aan elk product wordt toegewezen

**Formaat van Gegevens**: De waarde van het koord die de naam van de attributenreeks bevatten

**output van het Voorbeeld**:

```json
{
  "attributes": [
    {
      "code": "ac_attribute_set",
      "values": [
        "Default"
      ]
    }
  ]
}
```

**gevallen van het Gebruik**:

Wanneer u kenmerksetgegevens exporteert naar de catalogusservices van Commerce, worden geavanceerde functies voor productbeheer in externe systemen ingeschakeld. Deze functies zijn onder andere:

* Identificatie productsjabloon
* Catalogusbeheer en -organisatie
* Integratie van systemen van derden die kenmerksetcontext vereisen

### &#x200B;3. Geavanceerde inventarisgegevens (`ac_inventory`)

**Doel**: Verstrekt voorraadbeheermontages voor elk product

**Formaat van Gegevens**: JSON-Gecodeerde koord die inventarisconfiguratie bevatten

**Included gebieden**:

* `manageStock` (boolean): Of voorraadbeheer is ingeschakeld
* `cartMinQty` (drijvende komma): minimumhoeveelheid toegestaan in winkelwagentje
* `cartMaxQty` (drijvende komma): maximumhoeveelheid toegestaan in winkelwagentje
* `backorders` (tekenreeks): Backorder-beleid. De waarde is een van de volgende:
   * `"no"`: geen achterorden toegestaan
   * `"allow"`: hoeveelheid kleiner dan 0 toestaan
   * `"allow_notify"`: hoeveelheid groter dan 0 toestaan en klant op de hoogte stellen
* `enableQtyIncrements` (boolean): Of toename van aantal is ingeschakeld
* `qtyIncrements` (zwevend): Vereiste waarde voor verhogen van hoeveelheid

**output van het Voorbeeld**:

```json
{
  "attributes": [
    {
      "code": "ac_inventory",
      "values": [
        "{\"manageStock\":true,\"cartMinQty\":2,\"cartMaxQty\":42,\"backorders\":\"no\",\"enableQtyIncrements\":false,\"qtyIncrements\":2}"
      ]
    }
  ]
}
```

**gevallen van het Gebruik**:

Wanneer u inventarisgegevens exporteert naar de catalogusservices van Commerce, zijn er geavanceerde functies voor voorraadbeheer beschikbaar in externe systemen. Deze functies zijn onder andere:

* Inventory management-systeemintegratie
* Regels voor het valideren van winkelwagentjes
* Optimalisatie van het bestelproces
* Klantervaring aanpassen

## Verbetering van gegevensuitvoer

De extra module van de Attributen van het Product verbetert de bestaande productvoer. De nieuwe kenmerkgegevens worden automatisch geïntegreerd.

* **Diervoeders van Producten** (`products`): Verbeterd met de drie extra attributen

   * Hiermee voegt u de kenmerken `ac_tax_class` , `ac_attribute_set` en `ac_inventory` toe aan elke productrecord
   * De oorspronkelijke productgegevens ongewijzigd laten
   * Onderhoudt achterwaartse compatibiliteit met bestaande diervoederconsumenten

* **van de Attributen van het Product van 0} Diervoed**: Verbeterd met attributenmeta-gegevens voor de nieuwe attributen`productAttributes`

   * Metagegevens voor de drie nieuwe kenmerken in de `productAttributes` feed worden automatisch geregistreerd
   * Verstrekt attributenconfiguratiedetails (gegevenstypes, zichtbaarheidsmontages, etc.)
   * Helpt externe systemen het nieuwe kenmerkenschema te begrijpen

## De extensie installeren

**Vereisten**

* PHP 8.1, 8.2, 8.3 of 8.4
* Adobe Commerce 2.4.4+
* [ de uitbreiding van de Uitvoer van Gegevens van Adobe Commerce ](manage-extension.md#update-a-module-to-a-specific-version), versie 103.4.11 of later
* Toegang tot [ repo.magento.com ](https://repo.magento.com)

  Om sleutels te produceren en de noodzakelijke rechten te verkrijgen, zie [ uw authentificatiesleutels ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) krijgen. Voor wolkeninstallaties, zie [ Commerce op de Gids van de Infrastructuur van de Wolk ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Toegang tot de opdrachtregel van de Adobe Commerce-toepassingsserver.

### Installatiestappen

Voeg de module `adobe-commerce/module-extra-product-attributes` toe met behulp van Composer:

```shell
composer require adobe-commerce/module-extra-product-attributes
```

Raadpleeg de volgende handleidingen voor gedetailleerde installatiestappen:

* [ installeer uitbreiding op Adobe Commerce op de Infrastructuur van de Wolk ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure-store/extensions)
* [ installeer uitbreiding Adobe Commerce op-gebouw ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/extensions)

## Productgegevens synchroniseren

Na herplaatsing, voert de instantie van Adobe Commerce automatisch de extra gegevens tijdens productsynchronisatie uit. U kunt de `resync` CLI bevelen ook gebruiken om onmiddellijk te synchroniseren.

```shell
# Resync the products feed (includes the new attributes)
bin/magento saas:resync --feed=products
```

```shell
# Resync the product attributes feed (includes new attribute metadata)
bin/magento saas:resync --feed=productAttributes
```

## Problemen oplossen

**Producten ontbrekende extra attributen:**

* Controleren of de module correct is geïnstalleerd en ingeschakeld
* Voer de resync-opdrachten uit om de productgegevens te vernieuwen
* Controleren of producten geldige belastingklasse- en kenmerksettoewijzingen hebben

**de gegevens van de Inventaris verschijnen onjuist:**

* Controleren of de inventarisinstellingen correct zijn geconfigureerd in de beheerder
* Controleren op overschrijvingen van specifieke inventarissen voor websites
* Verifieer dat de [ module van Inventory management ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) correct werkt

Voor verdere details, zie de [ Gids van Inventory management ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) in de *Commerciële Documentatie van Adobe Commerce*.

**de bedenkingen van Prestaties:**

* De exportprocesprestaties na installatie controleren
* Overweeg het plannen van resyncs tijdens lage verkeersperioden

### Logboekregistratie en foutopsporing

De module registreert uitvoerfouten en waarschuwingen aan het standaard het registrerensysteem van Commerce. Als er problemen optreden tijdens de productsynchronisatie, controleert u de logbestanden voor het exporteren van gegevens.

Voor details, zie [ logboeken van het Overzicht en los ](troubleshooting-logging.md) problemen op.

