---
title: Wat is  [!DNL Live Search]?
description: '[!DNL Live Search] van Adobe Commerce biedt een snelle, relevante en intuïtieve zoekervaring.'
recommendations: noCatalog
exl-id: 15399216-6a96-4d0b-bbc1-293190cb9e14
source-git-commit: 1548b7e11249febc2cd8682581616619f80c052f
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 1%

---

# Wat is [!DNL Live Search]?

[!DNL Live Search] is een functie die de standaardzoekmogelijkheden in Adobe Commerce vervangt. Wanneer de functie [!DNL Live Search] is ingeschakeld en geconfigureerd, wordt het standaardzoektekstveld vervangen door het tekstveld [!DNL Live Search] . [!DNL Live Search] bevat ook de widget pagina met productlijsten (Product Listing Page, PLP). Deze widget biedt robuuste filtermogelijkheden voor het bladeren in zoekresultaten.

Met [!DNL Live Search] kunt u:

- Creëer zinvolle zoekervaringen om kopers te helpen bij het vinden van wat ze willen, zo weinig mogelijk.
- Profiteer van dynamische facettering op basis van AI en herrangschikking van zoekresultaten als reactie op winkelgedrag tijdens een sessie.
- Gebruik een eenvoudige SaaS-service die eenvoudige updates biedt en in uw licentie is opgenomen, waardoor de totale eigendomskosten dalen.
- Zorg voor technische oplossingen door GraphQL API, flexibiliteit zonder kop, API-sandboxomgevingen en ultrasnelle SaaS in te schakelen.

>[!IMPORTANT]
>
>Adobe Commerce biedt opties voor het zoeken naar sites. Vóór implementatie, herzie de [ Grenzen en 1} informatie van Grens {om ervoor te zorgen dat ](boundaries-limits.md) geschikt voor uw bedrijfsbehoeften is.[!DNL Live Search]

## Architectuur

De kant van Adobe Commerce van de architectuur omvat het ontvangen van het onderzoek *Admin*, het synchroniseren van catalogusgegevens, en het runnen van de vraagdienst. Nadat [!DNL Live Search] is geïnstalleerd en geconfigureerd, wordt Adobe Commerce gestart met het delen van zoek- en catalogusgegevens met SaaS-services. Op dit punt, kunnen de gebruikers Admin opstelling, aanpassen en onderzoek [ facetten ](facets.md), [ synoniemen ](synonyms.md) beheren, en [ merchandising regels ](category-merch.md).

![ de Levende Stroom van Gegevens van het Onderzoek ](assets/ls-cs-data-flow.png)

## Snelle rondleiding

Met de focus op snelheid, relevantie en gebruiksgemak is [!DNL Live Search] een gamewisselaar voor zowel kopers als handelaren. Bekijk de volgende video en bekijk een snelle rondleiding van [!DNL Live Search] vanuit de winkel.

>[!VIDEO](https://video.tv.adobe.com/v/3418797?learn=on)

Voor een meer diepgaande video over het gebruiken van en het vormen van Levend Onderzoek, zie [ Volledige Demonstratie op  [!DNL Live Search] ](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration) onderwerp.

### Zoeken terwijl u typt

[!DNL Live Search] antwoordt met gesuggereerde producten en een duimnagelbeeld van hoogste onderzoeksresultaten in a [ popover ](storefront-popover.md) als het type van kopers vragen in het [ Onderzoek ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) vakje. De [ paginasvertoningen van het 0} productdetail {wanneer de kopers een gesuggereerd of gekenmerkt product klikken. ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) A _Mening alle_ verbinding in footer van popover toont de pagina van onderzoeksresultaten.

[!DNL Live Search] retourneert de resultaten &quot;search as you type&quot; voor een query van twee of meer tekens. Voor een gedeeltelijke overeenkomst, is het maximumaantal karakters per woord 20. Het aantal karakters in de vraag is niet configureerbaar. De popover bevat de velden `name` , `sku` en `category_ids` .

![ storefront van het Voorbeeld - onderzoek aangezien u ](assets/storefront-search-as-you-type.png) typt

### Alle zoekresultaten weergeven

Om van alle producten een lijst te maken die door &quot;onderzoek aangezien u&quot;vraag typt, klik _Mening allen_ in footer van popover.

![ de storefront van het Voorbeeld - prijsfacetten ](assets/storefront-view-all-search-results.png)

### Hoe [!DNL Live Search] typos verwerkt

Wanneer een zoekopdracht wordt uitgevoerd, voert [!DNL Live Search] een niet-vage zoekopdracht uit die geen rekening houdt met een typos. Als er geen resultaten worden gevonden, voert [!DNL Live Search] een tweede vage zoekopdracht uit waarbij rekening wordt gehouden met kleine typos. De vage zoekopdracht wordt uitgevoerd met een maximale bewerkingsafstand van 1. Deze geeft afstand uit gebruikt het concept [ Levenshtein afstand ](https://en.wikipedia.org/wiki/Levenshtein_distance), en het staat voor drie soorten verrichtingen toe:

| Bewerking | Beschrijving | Voorbeeld |
|---|---|---|
| Invoegen | Een teken toevoegen. | &quot;cat&quot; -> &quot;cart&quot; |
| Verwijderen | Een teken verwijderen. | &quot;kar&quot; -> &quot;kat&quot; |
| Vervanging | Een teken vervangen door een ander teken. | &quot;kar&quot; -> &quot;cast&quot; |

Naast de vage zoeklogica wordt ook rekening gehouden met omzettingen, dat wil zeggen, waarbij twee aangrenzende tekens in een woord worden gewisseld, bijvoorbeeld &#39;the&#39; in plaats van &#39;the&#39;. Deze bewerkingslimieten gelden per woord en niet voor de hele woordgroep.

### Gefilterde zoekopdracht met facetten

Het gefiltreerde onderzoek gebruikt veelvoudige afmetingen van attributenwaarden, of [ facetten ](facets.md), als onderzoekscriteria. De selectie van filters wordt gedefinieerd door de handelaar en verandert afhankelijk van de geretourneerde producten, waarbij de meest gebruikte facetten boven aan de lijst worden vastgezet.

Facets van het gebruik als parameters URL:`http://yourwebsite.com?color=red`, en Levende de filterresultaten van het Onderzoek die op deze attributenwaarden worden gebaseerd.

### Synoniemen

[ Synoniemen ](synonyms.md) breidt het bereik uit en verscherpt de nadruk van vragen door woordshoppers te omvatten zou kunnen gebruiken die van die in de catalogus verschillen. U kunt het synoniem woordenboek perfectioneren om consumenten betrokken te houden en op de weg aan aankoop.

### Handelsregels

Het verhandelen [ regels ](rules.md) vorm de het winkelen ervaring met als-toen verklaringen die logica en gebeurtenissen aan onderzoek toevoegen. U kunt producten eenvoudig verhogen of begraven voor een promotie, seizoen, of een andere periode.

### Ondersteuning voor zoektermen

[!DNL Live Search] steunt Commerce [ herleidt van de onderzoekstermijn ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms). Gebruikers kunnen bijvoorbeeld zoeken naar een term zoals &quot;Verzendkosten&quot; en deze rechtstreeks doorsturen naar de pagina Verzendkosten.

## Componenten Live zoeken

- [!DNL Live Search] [ popover widget ](storefront-popover.md) is de doos die onder het onderzoeksgebied opent dat de onderzoeksresultaten bevat.
- [ Van de Lijst van het Product van de Pagina widget ](plp-styling.md) (PLP) verstrekt een doorzoekbare pagina van de productlijst met facetten en synoniem steun. De widget is geïnstalleerd en ingeschakeld in Live Search 4.0.0+ en vervangt de zoekadapter.
- (**Vervangen**) Adapter van het Onderzoek was de voorloper aan PLP widget en geïnstalleerd met Levend Onderzoek &lt; 4.0.0. Als u een versie van Live zoeken gebruikt die ouder is dan 4.0.0, raadt Commerce u aan een upgrade uit te voeren om de voordelen van de functies van de PLP-widget en toekomstige verbeteringen te kunnen genieten. In de toekomst wordt de zoekadapter alleen bijgewerkt om beveiligingsproblemen te verhelpen.

## [!DNL Live Search] werkruimte

[!DNL Live Search] [ werkruimte ](workspace.md) is het gebied in Admin waar u [!DNL Live Search] eigenschappen zoals synoniemen, facetten, en het Merchandising van de Categorie vormt.

## Gebeurtenissen

[!DNL Live Search] gebruikt [ gebeurtenissen ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#live-search) om [ Intelligente Merchandising ](category-merch.md) en [ prestaties ](performance.md) dashboards te berekenen. Eventing wordt voorzien van standaardimplementaties. Eventing voor hoofdloze winkelcentra moet handmatig worden ingeschakeld.

## Beleid voor het bewaren van catalogusgegevens

Als u gedurende 90 opeenvolgende dagen geen zoekquery naar de catalogusgegevens in uw testomgeving verzendt, worden de catalogusgegevens ingesteld op de slaapstand en worden er geen gegevens geretourneerd voor zoekopdrachten. Dit beleid heeft geen invloed op catalogusgegevens in uw productieomgeving.

Om de catalogusgegevens in uw het testen milieu opnieuw te activeren, [ voorlegt een steunverzoek ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#experience-league-start-page) met de titel: &quot;Reactivate [!DNL Live Search]&quot;en omvat milieu IDs. De catalogusgegevens in de testomgeving moeten binnen een paar uur worden hersteld.
