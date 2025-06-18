---
title: Elementen beheren
description: Met Productvisa met AEM Assets kunt u media-elementen voor uw winkel beheren.
feature: CMS, Media
source-git-commit: 0e7bdfab3efff7f994c63215f4ac31ed00562628
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---


# Commerce-media-elementen beheren met producthandleidingen

<!--In ACAP-844, this topic was linked to from the Commerce Admin products images and videos when the Assets integration is enabled. If the URL to the topic changes, be sure to add a redirect.-->

U kunt de volgende mediatypen beheren met behulp van productvisuele hulpmiddelen van AEM Assets:

* Productafbeeldingen
* Afbeeldingen van inhoud
* Productvideo&#39;s
* Categorieafbeeldingen

## Productafbeeldingen

Wanneer de integratie van de productvisuele integratie is ingeschakeld, wordt het imagebeheer gecentraliseerd in het Digital Asset Management System (DAM). Adobe Commerce werkt vervolgens als een belangrijk betrokkenheidskanaal, zodat alleen goedgekeurde afbeeldingen van hoge kwaliteit worden gebruikt voor alle winkeliers. Deze instelling verbetert de consistentie van merken, minimaliseert handmatige inspanningen en stroomlijnt de updates van inhoud, zodat handelaren afbeeldingen niet handmatig hoeven te uploaden of te beheren in Adobe Commerce.

### Afbeeldingen van producten weergeven in Adobe Commerce

Productafbeeldingen worden automatisch uit AEM Assets opgehaald op basis van vooraf geconfigureerde overeenkomende regels:

1. Voor _Admin_ sidebar, navigeer aan **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.

1. Selecteer een product.

1. Open de **Beelden en de sectie van Video&#39;s**.

   ![ beeld van het Product ](assets/product-image.png){width="600" zoomable="yes"}

   >[!NOTE]
   >
   > Een bericht wijst erop dat de integratie wordt toegelaten, makend dit a **read-only** sectie aangezien het beeldbeheer in DAM wordt gecentraliseerd.

### Productafbeeldingen beheren in AEM Assets

Om product-verwante beelden te beheren, moeten alle veranderingen direct in **AEM Assets** worden aangebracht. Dit proces is volledig geautomatiseerd, zodat alle wijzigingen worden gesynchroniseerd met Adobe Commerce zonder dat handmatige tussenkomst vereist is.

### Synchronisatie-SLA&#39;s

Controle [ de Synchronisatie SLA ](get-started/setup-synchronization.md#synchronization-sla) voor meer informatie over dit onderwerp.

## Afbeeldingen van inhoud

Adobe Commerce verstrekt de Bouwer van de Pagina als systeem van het a **inhoudsbeheer (CMS)** voor verkopers die niet Adobe Experience Manager (AEM) toolset gebruiken. Om inhoudsverwezenlijking te verbeteren, onze integratiehefboomwerkingen [ de Selector van Activa van AEM ](synchronize/asset-selector-integration.md), die marketers toestaan om tot beelden van **direct toegang te hebben en in te bedden DAM**. Hierdoor wordt ervoor gezorgd dat alleen goedgekeurde en kwalitatief hoogstaande afbeeldingen worden gebruikt bij het maken van inhoud, waardoor overbodige opslag in Adobe Commerce overbodig wordt.

### AEM Asset Selector gebruiken in Page Builder

Om de **Selector van Activa van AEM** voor het inbedden van beelden te gebruiken:

1. Navigeer aan om het even welke sectie in **Adobe Commerce Admin** die `content enrichment` gebruikend **Bouwer van de Pagina** steunt.

1. Open [ Bouwer van de Pagina ](https://developer.adobe.com/commerce/frontend-core/page-builder/){target=_blank}.

   Een nieuw Type van Media genoemd **de Activa van AEM** zal beschikbaar zijn.

1. Sleep het mediatype AEM Asset naar een inhoudsblok.

1. Geef desgevraagd de referenties op om toegang te krijgen tot de DAM.

1. Selecteer een afbeelding in de DAM en voeg deze rechtstreeks in de inhoud in.

De vereniging aan het geselecteerde beeld zal in Adobe Commerce als direct URL worden opgeslagen richtend aan **Dynamische Media**, die ervoor zorgen dat:

* Afbeeldingsbestanden hoeven niet in Adobe Commerce te worden opgeslagen.

* Marktdeelnemers werken uitsluitend met goedgekeurde activa van de DAM.

* Inhoud blijft consistent en up-to-date voor alle aanraakpunten van klanten.

## Productvideo&#39;s

Adobe Commerce fungeert als een belangrijk betrokkenheidskanaal voor digitale middelen. Nadat de Visuals van het Product wordt toegelaten, is het videobeheer gecentraliseerd binnen **DAM**, die consistentie, naleving, en geoptimaliseerde levering over handelsafzet verzekeren.

### Productvideo&#39;s beheren

1. Voor _Admin_ sidebar, navigeer aan **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.

1. Selecteer een product.

1. Open de **Beelden en de sectie van Video&#39;s**.

   ![ beeld van het Product ](assets/product-image.png){width="600" zoomable="yes"}

   >[!NOTE]
   >
   > Een bericht wijst erop dat de integratie wordt toegelaten, die tot deze sectie **read-only** maken, aangezien de video&#39;s in AEM Assets worden gecontroleerd.

### Video&#39;s koppelen in AEM Assets

1. Navigeer in AEM Assets naar de video die u aan een product wilt koppelen.

1. Koppel de video aan een of meer producten in Adobe Commerce.

1. De integratie synchroniseert automatisch de koppeling, waarbij de videospeler Dynamic Media rechtstreeks op de storefront wordt weergegeven. Dit elimineert de behoefte aan handelaren om videoplaybackconfiguraties te beheren.

### Alleen API-eerste videoondersteuning

De integratie ondersteunt momenteel video&#39;s via API, waarmee partners via programmacode video&#39;s kunnen ophalen.

>[!WARNING]
>
> Video&#39;s zijn standaard nog niet geïntegreerd in bestaande Adobe Commerce-opslagoplossingen.

Dankzij deze integratie kunnen handelaren eenvoudig productvideo&#39;s op schaalbare en geoptimaliseerde wijze beheren, waarbij ze AEM Assets en Dynamic Media gebruiken voor naadloze levering.

### Synchronisatie-SLA&#39;s

Controle [ de Synchronisatie SLA ](get-started/setup-synchronization.md#synchronization-sla) voor meer informatie over dit onderwerp.

## Categorieafbeeldingen

Adobe Commerce stelt handelaren in staat afbeeldingen te koppelen aan productcategorieën, waardoor een visueel aantrekkelijke winkel ontstaat. De integratiehefboomwerkingen AEM Asset Selector, toelatend marketers om productbeelden direct van het **Digitale systeem van het Beheer van Activa (DAM)** foutloos te selecteren. Dit zorgt ervoor dat alleen goedgekeurde images worden gebruikt en voorkomt dat deze in Adobe Commerce moeten worden opgeslagen, zodat consistentie en efficiëntie in alle servicekanalen behouden blijven.

### AEM Asset Selector gebruiken voor categorieafbeeldingen

Nadat u de [ selecteur van Activa van AEM ](synchronize/asset-selector-integration.md) vormt, kunt u het gebruiken om activa in uw inhoud van cataloguscategorieën toe te voegen.

1. Voor _Admin_ sidebar, navigeer aan **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.

1. Selecteer een categorie die u wilt bijwerken.

1. Breid de ![ selecteur van de Uitbreiding ](../assets/icon-display-expand.png) in de **[!UICONTROL Content]** sectie uit.

1. In de **[!UICONTROL Content]** sectie, bepaal de plaats van het *gebied van het Beeld* verbonden aan de categorie.

   ![ inhoud van de Categorie ](assets/category-asset.png){width="600" zoomable="yes"}

1. Klik op **[!UICONTROL Select from Assets]** om de categorieafbeelding te wijzigen.

   ![ inhoud van de Categorie ](assets/asset-view.png){width="600" zoomable="yes"}

1. Kies een afbeelding in de AEM Asset Selector.

   ![ inhoud van de Categorie ](assets/select-image.png){width="600" zoomable="yes"}

1. Klik op **[!UICONTROL Save]** en ga verder.

   Voor meer informatie over het creëren van een categorie, zie [ de categorieinhoud ](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/categories/create/category-create#step-3-complete-the-category-content) in de **Gids van het Beheer van de Catalogus van Commerce** voltooien.

## Middelen bijwerken

Nadat u middelen in AEM Assets hebt bijgewerkt en goedgekeurd, worden de updates automatisch naar Adobe Commerce verzonden met de functie voor automatische matching van productvisa. Dit proces wordt geactiveerd na goedkeuring van activa. Zorg ervoor dat u het element opnieuw verwerkt voordat u het goedkeurt om ervoor te zorgen dat alle laatste wijzigingen en updates van metagegevens worden opgenomen.

Raadpleeg de volgende documentatie bij AEM Assets voor meer informatie.

* [ het Opverwerken van digitale activa ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/manage/reprocessing)

* [ keur activa ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/approve-assets) goed
