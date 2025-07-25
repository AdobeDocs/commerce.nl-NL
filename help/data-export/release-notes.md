---
title: '[!DNL SaaS Data Export Extension] Opmerkingen bij de release'
description: De recentste versieinformatie voor  [!DNL Data Export Extension]  voor Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 8ae51d3d-8c12-4607-b7e5-985033143a84
source-git-commit: 6876a5fbde2b3292cd788a50d104083cf51109ed
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Opmerkingen bij de release Extension

In deze releaseopmerkingen worden de nieuwste versies van de extensie [!DNL SaaS data export] beschreven. Er wordt ondersteuning geboden voor de belangrijkste uitgebrachte versie. Opmerkingen bij de release voor oudere versies worden ter referentie verschaft.

Updates zijn:

![ Nieuwe ](../assets/new.svg) Nieuwe eigenschappen
![ bevestig ](../assets/fix.svg) Bevestigingen en verbeteringen
![ Bug ](../assets/bug.svg) Bekende kwesties


>[!NOTE]
>
>De de gegevensuitvoeruitbreiding van SaaS is een inzameling van modules die automatisch met Levend Onderzoek, de Aanbevelingen van het Product, en de Dienst van de Catalogus geïnstalleerd is. U kunt de versie controleren die op uw systeem is geïnstalleerd met Composer. In sommige gevallen kunt u de extensie voor het exporteren van gegevens op uw systeem upgraden om oplossingen of nieuwe mogelijkheden op te halen zonder de Commerce Service-versie bij te werken.

## Huidige hoofdversie

## 103.4.7 Release

![ bevestig ](../assets/fix.svg) Verwijderde verouderde lijsten die categorietoestemmingen voor producten opsloeg. <!--MDEE-1065-->

## 103.4.6 Release

![ verbeter ](../assets/fix.svg) downloadbare het productgegevens van de Uitvoer Adobe Commerce gebruikend het `ac_downloadable` attribuut voor gebruik met Adobe Commerce Optimizer. <!--MDEE-1043-->
![ bevestig ](../assets/fix.svg) de Kritieke oplossing van de installatiefout voor versie 2.4.4 van Adobe Commerce. <!--MDEE-1074-->

## 103.4.5 Release

![ de Nieuwe ](../assets/new.svg) Gegevens SaaS de uitvoer steunt nu het het producttype van Adobe Commerce `giftcard`. In de gegevensfeed worden Cadeauproducten geëxporteerd als eenvoudige producten met het type productkenmerk `ac_giftcard` . <!--MDEE-1042-->
![ bevestig ](../assets/fix.svg) Verbeterde fout die van de gegevensuitvoer rapporteert. Logs omvat nu gedetailleerdere foutenmeldingen, met inbegrip van originele technische details om het gemakkelijker te maken om fouten te zuiveren en te vinden. <!--MDEE-1064-->

## 103.4.4 Release

![ Nieuw ](../assets/new.svg) voegde een waarschuwingsbericht toe dat toont wanneer het `cleanup-feed` argument aan het `saas:resync` CLI bevel wordt toegevoegd. De optie `--cleanup-feed` moet voorzichtig worden gebruikt en alleen in specifieke scenario&#39;s, zoals na het opschonen van de omgeving of met de optie `--dry-run` . In andere gevallen kan dit leiden tot gegevensverlies en synchronisatieproblemen. <!--MDEE-1047-->
![ Repareren ](../assets/fix.svg) voegde `x-request-id` van de serverreactie voor betere traceerbaarheid toe. <!--MDEE-1041-->
![ bevestig ](../assets/fix.svg) een kwestie waar de synchronisatiestatus niet voor de volledige voederpartij werd bewaard, die tot onnodige resynchronisatie leidde. <!--MDEE-1049-->
![ bevond het Bevel ](../assets/fix.svg) een kwestie waar alle voer in de voederpartij tijdens synchronisatie werd overgeslagen als één voer een fout bevatte. <!--MDEE-976-->
![ Repareren ](../assets/fix.svg) Toegevoegde steun voor afmetingen in de indexer van categorietoestemmingen. <!--MDEE-654-->

## 103.4.3 Release

![ bevestig ](../assets/fix.svg) een kwestie opgelost waar de producten tijdens het proces van de gegevensuitvoer wegens ontbrekende attributen EAV werden overgeslagen. <!--MDEE-970-->

## 103.4.2 Release

![ bevestig ](../assets/fix.svg) toevoegde de capaciteit om entiteitlading in `saas-export.log` te verzamelen wanneer het runnen van de testresynchronisatie gebruikend het `saas:resync --dry-run` bevel met de `EXPORTER_EXTENDED_LOG=1` omgevingsvariabele. <!--MDEE-1023-->

## 103.4.1 Release

![ bevestig ](../assets/fix.svg) een prefix aan QueryXml geheim voorgeheugensleutels toevoegde om noemende conflicten met andere modules te verhinderen. <!--MDEE-1019-->

## 103.4.0 Release

![ Repareren ](../assets/fix.svg) het product treedt voer met voeten verzendt niet meer toestemmingen als het product niet aan een categorie wordt toegewezen.<!--MDEE-449-->

## 103.3.21 Release

![ Toegevoegde functionaliteit van 0&rbrace; Repareren ](../assets/new.svg), `products`, en `productOverrides` voer gedeeltelijk synchroniseert dat op een gespecificeerde lijst van productSKUs wordt gebaseerd. `productAttributes` Gebruik de nieuwe functionaliteit door de optie `--by-ids` aan de opdracht resync CLI toe te voegen: <!--MDEE-606-->

```shell
bin/magento saas:resync --feed=<FEED_NAME> --by-ids='<SKU1>,<SKU2>,<SKU3>
```

![ bevestig ](../assets/fix.svg) Verminderde potentiële verenigbaarheidskwesties met PHP 8.4 door verouderde functionaliteit te richten. <!--MDEE-1002-->

## 103.3.20 Release

![ Vaste ontraceerbare ](../assets/fix.svg) fouten in `BulkException` door overseinen voor fouten te verbeteren met betrekking tot de mislukkingen van de uitvoerkring van de Gegevens van de Catalogus.`cron.log`<!--MDEE-966-->
![ bevestig ](../assets/fix.svg) Verbeterde prestaties van het product re-synchronisatieproces op instanties met een hoog aantal opslagmeningen. <!--MDEE-974-->

## 103.3.19 Release

![ bevestig ](../assets/fix.svg) de uitbreiding van de gegevensuitvoer werkte bij om voer rekbaarheid te verbeteren. <!--MDEE-936-->
![ bevestig ](../assets/fix.svg) de bewerker van de gegevensuitvoer verifieert nu de indexeerstatus vóór een volledige resync om onbedoeld gegevensverlies in de voederingslijst te vermijden.

## 103.3.18 Release

![ het Staging updates van 0&rbrace; herstellen &lbrace;voor product en categorieentiteiten wordt nu correct teweeggebracht op de gegevensupdates van de Uitvoer van Gegevens.](../assets/fix.svg)<!--MDEE-963-->

## 103.3.17 Release

![ Toegevoegde verenigbaarheid voor PHP 8.4 herstellen ](../assets/fix.svg). <!--MDEE-941-->

## 103.3.16 Release

![ de waarden van de Optie van 0&rbrace; herstellen &lbrace;kunnen leeg voor configureerbare producten voor veelvoudige opslagmeningen zijn. ](../assets/fix.svg)<!--MDEE-926-->

## 103.3.15 Release

![ bevestig ](../assets/fix.svg) verzekerde stabiele verrichting van integratietests op oudere configuraties. <!--MDEE-869-->
![ herstellen ](../assets/fix.svg) Einde verspreidend onnodige attributenopties. <!--MDEE-882-->
![ bevestig ](../assets/fix.svg) het foutenbericht dat naar het logboek van de gegevensuitvoer wordt verzonden wanneer de gegevensrangschikking ontbreekt. <!--MDEE-913-->
![ bevestig ](../assets/fix.svg) verbeterde de betrouwbaarheid van eenvoudige productupdates met extra testdekking. <!--MDEE-886-->

## 103.3.14 Release

![ bevestig ](../assets/fix.svg) de exporter indexer handhaaft nu de correcte status voor afhankelijke indexen. Eerder, waren deze indexen verkeerd ongeldig en vereiste extra controles en bevestiging die het indexeren prestaties vertraagden. <!--MDEE-866-->

## 103.3.13 Release

![ bevestig ](../assets/fix.svg) Verbeterde prestaties van het proces van de gegevenssynchronisatie door een lokaal geheime voorgeheugen voor de gegevens van attributenopties toe te voegen.<!--MDEE-864-->

## 103.3.12 Release

![ bevestig ](../assets/fix.svg) een kwestie die synchronisatietijd voor eenvoudige en virtuele producten verhoogde. <!--MDEE-861-->

## 103.3.11 Release

![ Bevestig ](../assets/fix.svg) de dienst van de gegevensuitvoer verzendt nu speciale prijsgegevens voor bundelproducten als percentage, correcterend een vorige kwestie waar het als definitieve prijs werd verzonden. <!--MDEE-854-->
![ bevestig ](../assets/fix.svg) bijgewerkte monoloog implementatie voor verenigbaarheid met Monolog 3. <!--MDEE-858-->

## 103.3.10 Release

![ herstellen ](../assets/fix.svg) Vaste Veelvoudige opslag filtratie voor het voer van de productdouaneopties. <!--MDEE-842-->
![ Repareren ](../assets/fix.svg) Ongeldige voer wordt niet opnieuw voorgelegd tot de het hakwaarde van de voer is veranderd.<!--MDEE-848-->

## 103.3.9 Release

![ Repareren ](../assets/fix.svg) wanneer een entiteit wordt geschrapt, wordt de `deleted` vlag nu verspreid voor het scoping de dienstvoer voor website (`scopesWebsite`) en klantengroep (`scopesCustomerGroup`).<!--MDEE-839-->

## 103.3.8 Release

![ Uitgeschakelde configuratieopties van 0&rbrace; herstellen &lbrace;worden niet meer uitgevoerd als actieve opties.](../assets/fix.svg)<!--MDEE-812-->
![ herstellen ](../assets/fix.svg) de Opties en de waarden worden nu bijgewerkt op een configureerbaar product wanneer de veranderingen in een kindproduct worden aangebracht. <!--MDEE-835-->
![ Nieuw ](../assets/new.svg) voegde de capaciteit toe om de extra gegevens van het systeemattribuut in de voer van productattributen te omvatten.

## 103.3.7 Release

![ bevestig ](../assets/fix.svg) Verwijderde onnodige gebiedsdelen uit de module InventoryDataExporter.
![ Gewijzigde vereiste versies voor inventarismodules inbegrepen in de module CatalogInventoryDataExporter van de Reparatie ](../assets/fix.svg) &lbrace;om Adobe Commerce versie 2.4.4 te steunen.

## 103.3.6 Release

![ bevestig ](../assets/fix.svg) Vaste implocks die tijdens voer opnieuw indexerend op multi-draadwijze voorkwamen. De vragen zijn nu gescheiden in de verrichtingen van het Tussenvoegsel en van de Update.
![ bevestig ](../assets/fix.svg) optimaliseerde de vraag van Prijzen voor grote catalogi met vele websites.
![ Nieuwe ](../assets/new.svg) toegevoegde retry logica om ontbroken transacties opnieuw in werking te stellen wanneer de imlocklocks voorkomt.

## 103.3.5 Release

![ bevestig ](../assets/fix.svg) Vastgestelde gebiedsdeel voor recentste compatibele versie van de gegevensuitvoer voor de gemeenschappelijke module SaaS.

![ verbeter ](../assets/fix.svg) Vervangen `ScopeConfig` instantie met `ServiceConfigInterface` om verschillende de dienstconfiguraties te steunen.

## 103.3.4 Release

![ Toegevoegde steun van 0&rbrace; Repareren voor het controleregistreren van de gegevensoverdracht door een mechanisme toe te voegen om een ](../assets/fix.svg) gebeurtenis te verzenden telkens als het gegeven van de instantie van Commerce aan de dienst van Commerce wordt overgebracht `data_sent_outside`<!--MDEE-785-->

## 103.3.3 Release

![ Nieuwe ](../assets/new.svg) de gegevensuitvoer SaaS nu caches Entiteit-Attributen-Waarde (EAV) attributen voor de vraag van attributenmeta-gegevens.

![ bevestig ](../assets/fix.svg) een kwestie waar het `InventoryStockStatus` voer niet werd bewaard bij opnieuw proberen als het product werd geschrapt.

## 103.3.2 Release

![ bevestig ](../assets/fix.svg) een kwestie waar het `modifiedAt` gebied van verwijderde entiteitsvoer mist.

## 103.3.1 Release

![ bevestig ](../assets/fix.svg) een kwestie die een `Invalid Template File` bericht veroorzaakte om tijdens productvoer te verschijnen die opnieuw indexeert wanneer de Bouwer van de Pagina wordt geïnstalleerd.

## 103.3.0 Release

![ Nieuwe ](../assets/new.svg) Gemigreerde directe de voederlijsten van de uitvoer aan de verenigde structuur:
`id` , `source_entity_id` , `feed_id` , `modified_at` , `is_deleted` , `status` , `feed_data` , `feed_hash` , `errors`

![ Nieuwe ](../assets/new.svg) Gemigreerde catalogus en inventarisvoer aan de directe uitvoeroplossing.

![ Nieuw ](../assets/new.svg) anders genoemd directe voer voer voer schaafbanen aan `*_feed_resend_failed_items`.

![ Nieuw ](../assets/new.svg) hernoemde directe de uitvoervoer, indexeermening IDs, en veranderingslogboeklijsten.
- voederlijsten (en indexeermening IDs):
   - `catalog_data_exporter_products` -> `cde_products_feed`
   - `catalog_data_exporter_product_attributes` -> `cde_product_attributes_feed`
   - `catalog_data_exporter_categories` -> `cde_categories_feed`
   - `catalog_data_exporter_product_prices` -> `cde_product_prices_feed`
   - `catalog_data_exporter_product_variants` -> `cde_product_variants_feed`
   - `inventory_data_exporter_stock_status` -> `inventory_data_exporter_stock_status_feed`
- wijzigen, logtabelnamen - volgt hetzelfde naamgevingspatroon als de voedertabellen, maar als u de namen van logtabellen wijzigt, wordt een achtervoegsel `_cl` toegevoegd.  Bijvoorbeeld `catalog_data_exporter_products_cl` -> `cde-products_feed_cl`
Als u aangepaste code hebt die naar een van deze entiteiten verwijst, werkt u de verwijzingen bij met de nieuwe namen om ervoor te zorgen dat de code correct blijft functioneren.

![ Repareer ](../assets/fix.svg) gebied van de Reeks `modified_at` &lbrace;in voedergegevens slechts voor voer dat het vereist.

![ verbeter ](../assets/fix.svg) wijzig de `productAttributes` vraag om slechts productattributen terug te winnen.

## 103.2.6 Release

![ bevestig ](../assets/fix.svg) een kwestie die voer verhinderde opnieuw te worden gefixeerd wanneer de lijsten een prefix hebben.

## 103.2.5 Release

![ bevestig ](../assets/fix.svg) optimaliseerde de vraag van de Prijs.

## 103.2.4 Release

![ bevestig ](../assets/fix.svg) onjuiste status van de Voorraad die voor een product werd getoond wanneer Commerce Inventory management wordt toegelaten.

## 103.2.3 Release

![ bevestig ](../assets/fix.svg) Vaste prijs van websiteniveau.
![ Toegevoegde mutex van 0&rbrace; herstellen &lbrace;voor alle voer dat wordt verwerkt.](../assets/fix.svg)


## 103.2.2 Release

![ verbeter ](../assets/fix.svg) Verbeterde feeds batchstrategie voor grote catalogi. De batchtabel is nu gevuld met een beperkt aantal id&#39;s om het geheugengebruik te verminderen.

![ Elimineerde harde gebiedsdeel van CommerceInventoryDataExporter aan modules MSI.](../assets/fix.svg)

![ Verbeterde ](../assets/fix.svg) logboeken van 0&rbrace; herstellen &lbrace;om meer informatie te verzamelen en door verschillende het uitvoeren stadia te organiseren.`commerce-data-exporter`

## 103.2.1 Release

- Uitgebrachte bijgewerkte versie.

## 103.2.0 Release

- Multithread-gegevenssync voor producten en prijzen toegevoegd.
