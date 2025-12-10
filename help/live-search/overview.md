---
title: Wat is  [!DNL Live Search]?
description: '[!DNL Live Search] van Adobe Commerce biedt een snelle, relevante en intuïtieve zoekervaring.'
recommendations: noCatalog
exl-id: 15399216-6a96-4d0b-bbc1-293190cb9e14
source-git-commit: c6725fc524e9d239ccc0f16701e92ad5d2fc7729
workflow-type: tm+mt
source-wordcount: '925'
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
>Adobe Commerce biedt opties voor het zoeken naar sites. Vóór implementatie, herzie de [&#x200B; Grenzen en 1&rbrace; informatie van Grens &lbrace;om ervoor te zorgen dat &#x200B;](boundaries-limits.md) geschikt voor uw bedrijfsbehoeften is.[!DNL Live Search]

## Architectuur

De kant van Adobe Commerce van de architectuur omvat het ontvangen van het onderzoek *Admin*, het synchroniseren van catalogusgegevens, en het runnen van de vraagdienst. Nadat [!DNL Live Search] is geïnstalleerd en geconfigureerd, wordt Adobe Commerce gestart met het delen van zoek- en catalogusgegevens met SaaS-services. Op dit punt, kunnen de gebruikers Admin opstelling, aanpassen en onderzoek [&#x200B; facetten &#x200B;](facets.md), [&#x200B; synoniemen &#x200B;](synonyms.md) beheren, en [&#x200B; merchandising regels &#x200B;](category-merch.md).

![&#x200B; de Levende Stroom van Gegevens van het Onderzoek &#x200B;](assets/ls-cs-data-flow.png)

## Snelle rondleiding

Met de focus op snelheid, relevantie en gebruiksgemak is [!DNL Live Search] een gamewisselaar voor zowel kopers als handelaren. Bekijk de volgende video en bekijk een snelle rondleiding van [!DNL Live Search] vanuit de winkel.

>[!VIDEO](https://video.tv.adobe.com/v/3418797?learn=on)

Voor een meer diepgaande video over het gebruiken van en het vormen van Levend Onderzoek, zie [&#x200B; Volledige Demonstratie op  [!DNL Live Search] &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration) onderwerp.

### Zoeken terwijl u typt

[!DNL Live Search] antwoordt met gesuggereerde producten en een duimnagelbeeld van hoogste onderzoeksresultaten in a [&#x200B; popover &#x200B;](storefront-popover.md) als het type van kopers vragen in het [&#x200B; Onderzoek &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) vakje. De [&#x200B; paginasvertoningen van het 0&rbrace; productdetail &lbrace;wanneer de kopers een gesuggereerd of gekenmerkt product klikken. &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) A _Mening alle_ verbinding in footer van popover toont de pagina van onderzoeksresultaten.

[!DNL Live Search] retourneert de resultaten &quot;search as you type&quot; voor een query van twee of meer tekens. Voor een gedeeltelijke overeenkomst, is het maximumaantal karakters per woord 20. Het aantal karakters in de vraag is niet configureerbaar. De popover bevat de velden `name` , `sku` en `category_ids` .

![&#x200B; storefront van het Voorbeeld - onderzoek aangezien u &#x200B;](assets/storefront-search-as-you-type.png) typt

### Alle zoekresultaten weergeven

Om van alle producten een lijst te maken die door &quot;onderzoek aangezien u&quot;vraag typt, klik _Mening allen_ in footer van popover.

![&#x200B; de storefront van het Voorbeeld - prijsfacetten &#x200B;](assets/storefront-view-all-search-results.png)

### Hoe [!DNL Live Search] typos verwerkt

Wanneer een zoekopdracht wordt uitgevoerd, voert [!DNL Live Search] een niet-vage zoekopdracht uit die geen rekening houdt met een typos. Als er geen resultaten worden gevonden, voert [!DNL Live Search] een tweede vage zoekopdracht uit waarbij rekening wordt gehouden met kleine typos. De vage zoekopdracht wordt uitgevoerd met een maximale bewerkingsafstand van 1. Deze geeft afstand uit gebruikt het concept [&#x200B; Levenshtein afstand &#x200B;](https://en.wikipedia.org/wiki/Levenshtein_distance), en het staat voor drie soorten verrichtingen toe:

| Bewerking | Beschrijving | Voorbeeld |
|---|---|---|
| Invoegen | Een teken toevoegen. | &quot;cat&quot; -> &quot;cart&quot; |
| Verwijderen | Een teken verwijderen. | &quot;kar&quot; -> &quot;kat&quot; |
| Vervanging | Een teken vervangen door een ander teken. | &quot;kar&quot; -> &quot;cast&quot; |

Naast de vage zoeklogica wordt ook rekening gehouden met omzettingen, dat wil zeggen, waarbij twee aangrenzende tekens in een woord worden gewisseld, bijvoorbeeld &#39;the&#39; in plaats van &#39;the&#39;. Deze bewerkingslimieten gelden per woord en niet voor de hele woordgroep.

### Gefilterde zoekopdracht met facetten

Het gefiltreerde onderzoek gebruikt veelvoudige afmetingen van attributenwaarden, of [&#x200B; facetten &#x200B;](facets.md), als onderzoekscriteria. De selectie van filters wordt gedefinieerd door de handelaar en verandert afhankelijk van de geretourneerde producten, waarbij de meest gebruikte facetten boven aan de lijst worden vastgezet.

Facets van het gebruik als parameters URL:`http://yourwebsite.com?color=red`, en Levende de filterresultaten van het Onderzoek die op deze attributenwaarden worden gebaseerd.

### Synoniemen

[&#x200B; Synoniemen &#x200B;](synonyms.md) breidt het bereik uit en verscherpt de nadruk van vragen door woordshoppers te omvatten zou kunnen gebruiken die van die in de catalogus verschillen. U kunt het synoniem woordenboek perfectioneren om consumenten betrokken te houden en op de weg aan aankoop.

### Handelsregels

Het verhandelen [&#x200B; regels &#x200B;](rules.md) vorm de het winkelen ervaring met als-toen verklaringen die logica en gebeurtenissen aan onderzoek toevoegen. U kunt producten eenvoudig verhogen of begraven voor een promotie, seizoen, of een andere periode.

## Componenten Live zoeken

- [!DNL Live Search] [&#x200B; popover widget &#x200B;](storefront-popover.md) is de doos die onder het onderzoeksgebied opent dat de onderzoeksresultaten bevat.
- [&#x200B; Van de Lijst van het Product van de Pagina widget &#x200B;](plp-styling.md) (PLP) verstrekt een doorzoekbare pagina van de productlijst met facetten en synoniem steun. De widget is geïnstalleerd en ingeschakeld in Live Search 4.0.0+ en vervangt de zoekadapter.
- (**Vervangen**) Adapter van het Onderzoek was de voorloper aan PLP widget en geïnstalleerd met Levend Onderzoek &lt; 4.0.0. Als u een versie van Live zoeken gebruikt die ouder is dan 4.0.0, raadt Commerce u aan een upgrade uit te voeren om de voordelen van de functies van de PLP-widget en toekomstige verbeteringen te kunnen genieten. In de toekomst wordt de zoekadapter alleen bijgewerkt om beveiligingsproblemen te verhelpen.

## [!DNL Live Search] werkruimte

[!DNL Live Search] [&#x200B; werkruimte &#x200B;](workspace.md) is het gebied in Admin waar u [!DNL Live Search] eigenschappen zoals synoniemen, facetten, en het Merchandising van de Categorie vormt.

## Gebeurtenissen

[!DNL Live Search] gebruikt [&#x200B; gebeurtenissen &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#live-search) om [&#x200B; Intelligente Merchandising &#x200B;](category-merch.md) en [&#x200B; prestaties &#x200B;](performance.md) dashboards te berekenen. Eventing wordt voorzien van standaardimplementaties. Eventing voor hoofdloze winkelcentra moet handmatig worden ingeschakeld.

## Beleid voor het bewaren van catalogusgegevens

Als u gedurende 90 opeenvolgende dagen geen zoekquery naar de catalogusgegevens in uw testomgeving verzendt, worden de catalogusgegevens ingesteld op de slaapstand en worden er geen gegevens geretourneerd voor zoekopdrachten. Dit beleid heeft geen invloed op catalogusgegevens in uw productieomgeving.

Om de catalogusgegevens in uw het testen milieu opnieuw te activeren, [&#x200B; voorlegt een steunverzoek &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#experience-league-start-page) met de titel: &quot;Reactivate [!DNL Live Search]&quot;en omvat milieu IDs. De catalogusgegevens in de testomgeving moeten binnen een paar uur worden hersteld.
