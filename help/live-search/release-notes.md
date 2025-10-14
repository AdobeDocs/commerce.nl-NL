---
title: '[!DNL Live Search] Opmerkingen bij de release'
description: De recentste versieinformatie voor  [!DNL Live Search]  van Adobe Commerce.
feature: Services, Search, Release Notes
exl-id: 099cf79c-968c-4381-b66d-7f6141ad2db3
source-git-commit: 65ee1d4a14d97d5e54602fbdb3b9aa1b464de8df
workflow-type: tm+mt
source-wordcount: '2633'
ht-degree: 0%

---

# [!DNL Live Search] Opmerkingen bij de release

In deze releaseopmerkingen worden de meest recente versies van [!DNL Live Search] beschreven.

Er is ondersteuning voor de nieuwste versie. Opmerkingen bij de release voor oudere versies worden ter referentie verschaft.
Updates zijn:

![ Nieuwe ](../assets/new.svg) Nieuwe eigenschappen
![ bevestig ](../assets/fix.svg) Bevestigingen en verbeteringen
![ Bug ](../assets/bug.svg) Bekende kwesties

## Gehoste service-updates

Deze nota&#39;s beschrijven updates die buiten een versioned versie of verbeteringen aan de ontvangen dienst werden gepubliceerd.

_1 Oktober, 2025_

![ Nieuwe ](../assets/new.svg) Toegevoegde nieuwe genoemde sleutel van de gegevensopslag `ds-logged-in` voor klant het programma geopende gegevens.

_29 April, 2025_

![ bevond ](../assets/fix.svg) Vast een kwestie waar de **Uitvoer naar CSV** rapport over het [**Prestaties**](./performance.md) lusje niet alle gegevens omvatte die in de datumwaaier werden gespecificeerd.
![ bevestig ](../assets/fix.svg) een kwestie Vaste waar u a [ geen handelende regel ](./rules.md) kon bewaren als de filter van de onderzoeksvraag werd gebruikt.
![ bevestig ](../assets/fix.svg) een kwestie waar [ vastgezette producten ](./facets-manage.md#pinunpin-facet) niet vermeld bij de bovenkant van de resultatenpagina waren.

_21 April, 2025_

![ beval ](../assets/fix.svg) een kwestie met de waaierfilter voor prijzen vast zodat de producten die aan de hogere waaier gelijk zijn niet inbegrepen in de resultaten zijn. Deze verandering richt zich op hoe de prijswaaiers voor facetten worden bepaald.

_3 April, 2025_

![ Repareren ](../assets/fix.svg) werkte de uitbreiding van de Uitvoer van Gegevens SaaS bij om de &quot;Producten te verwijderen moet aan de wortelcategorie&quot;worden toegewezen [ beperking ](boundaries-limits.md#b2b-and-category-permissions) voor B2B verkopers. Zie [ de uitbreiding van de gegevensuitvoer ](../data-export/manage-extension.md) leiden om te leren hoe te om de uitbreiding van de Uitvoer van Gegevens SaaS aan versie 103.4.0+ bij te werken.

_Februari 20, 2025_

![ Nieuwe ](../assets/new.svg) Commerce steunt synoniemen van meerdere woorden. [ leer meer ](synonyms-type.md#multi-word-synonym-behavior). Ondersteuning voor synoniemen met meerdere woorden is alleen beschikbaar na deze releasedatum van 20 februari. Om het even welke bestaande synoniemen van meerdere woorden vereisen een volledige herdex om te werken, die u kunt verzoeken door [ tot een steunkaartje ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) te leiden.

_Januari 31, 2025_

![ Nieuw ](../assets/new.svg) Er is een nieuw beleid van het gegevensbehoud voor ongevraagde catalogusgegevens in uw het testen milieu. [ leer meer ](overview.md#catalog-data-retention-policy).

_19 september, 2024_

![ Nieuwe ](../assets/new.svg) versie van Beta voor de volgende geavanceerde onderzoeksmogelijkheden: gelaagd onderzoek gebruikend `startsWith` en `contains`. [ leer meer ](workspace.md#layered-search-and-expansion-of-search-types).

_4 September, 2024_

![ bevestig ](../assets/fix.svg) verhoogde het maximumaantal emmers die [ binnen een facet ](boundaries-limits.md#facets) aan 100 kunnen zijn teruggekeerd.

_7 Augustus, 2024_

![ bevestig ](../assets/fix.svg) verhoogde de maximumintervalwaarde, of prijswaaier voor [ prijsvermindering ](settings.md#price-faceting) van 10.000 tot 40.000.000.

_13 Februari, 2024_

![ Nieuw ](../assets/new.svg) [!DNL Live Search] steunt nu het plaatsen van een standaardregel voor [ Merchandising van het Onderzoek ](rules.md).

_12 oktober 2023_

![ de Nieuwe ](../assets/new.svg) beheerders van Commerce kunnen de taal van de index voor [!DNL Live Search] nu specificeren. Zie [ Montages ](settings.md).
![ Repareer ](../assets/fix.svg) het lusje van &quot;Regels van het Onderzoek&quot;is anders genoemd aan &quot;Verkoop van het Onderzoek&quot;.

_13 Juni, 2023_

![ bevestig ](../assets/fix.svg) een kwestie waar sommige karakters zoals citaten of apostroffen rangschikkende kwesties veroorzaakten. Deze problemen worden opgelost door opnieuw te indexeren.

_25 April, 2023_

![ Nieuwe ](../assets/new.svg) [!DNL Live Search] klanten kunnen uit de nieuwe [ SaaS prijsindexeerder ](../price-index/price-indexing.md) nu voordeel halen.

### PLP-widget

_Mei 22, 2025_

![ beval ](../assets/fix.svg) een kwestie waar Add aan de knoop van de Kar in het Engels bleef toen de scène in Frans, Duits, Italiaans of Spaans werd veranderd.
![ bevestig ](../assets/fix.svg) een kwestie waar Add aan de knoop van de Kar voor uit-van-voorraad producten werd getoond.

_31 Mei, 2024_

![ Nieuwe ](../assets/new.svg) Vrijgegeven versie 2.0.0 van PLP widget, die steun voor de volgende eigenschappen toevoegt:

- Toevoegen aan winkelwagentjes - Alleen beschikbaar voor eenvoudige producten.
- Meerdere afbeeldingen per product - de afbeelding kan veranderen wanneer een andere kleur wordt gekozen voor een configureerbaar product.

_27 oktober, 2023_

![ Nieuw ](../assets/new.svg) de [!DNL Live Search] PLP widget steunt nu kleurenstalen.

## [!DNL Live Search] 4.6.0

_9 Oktober, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) versie GA voor de volgende geavanceerde onderzoeksmogelijkheden: gelaagd onderzoek gebruikend `startsWith` en `contains`. [ leer meer ](workspace.md#layered-search-and-expansion-of-search-types).
![ Repareer ](../assets/fix.svg) het `ProductInterface` voorwerp in de [ Levende dienst van het Onderzoek ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) is afgekeurd. Gebruik in plaats hiervan het `ProductView` -object in de catalogusservice.

## [!DNL Live Search] 4.5.0

_5 September, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) Levend Onderzoek respecteert nu volledig [ wijze van de koekjesbeperking ](install.md#cookies) door gegevensinzameling en opslag in koekjes/lokale opslag te verhinderen wanneer de beperkingen worden toegelaten.

## [!DNL Live Search] 4.4.1

_Augustus 11, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Vaste het diensteindpunt van de catalogusdienst van 0} herstellen {voor zandbakmilieu&#39;s.](../assets/fix.svg)

## [!DNL Live Search] 4.4.0

_14 juli 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) verhoogde de [ prijs groeperende ](./settings.md#price-faceting) grens van 50 tot 100.

## [!DNL Live Search] 4.3.0

_Maart 11, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Repareren ](../assets/fix.svg) [!DNL Live Search] steunt nu PHP 8.4 voor installaties die Adobe Commerce 2.4.8-beta2 in werking stellen.
![ bevestig ](../assets/fix.svg) een kwestie waar de Adapter van het Onderzoek niet compatibel met `psr/http-message:2.0` was.

## [!DNL Live Search] 4.2.3

_13 Februari, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ bevestig ](../assets/fix.svg) een kwestie waar de pagina van het ordendetail het orderaantal, de datum, en de **[!UICONTROL Reorder]** knoop mist.

## [!DNL Live Search] 4.2.2

_6 Januari, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ bevestig ](../assets/fix.svg) een kwestie die een fout met de `categoryList` vraag GraphqL op Adobe Commerce versie 2.4.5 en vroeger veroorzaakte.

## [!DNL Live Search] 4.2.1

_31 Juli, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ bevestig ](../assets/fix.svg) een kwestie waar bepaalde manuscripten niet op de controlepagina laadden.
![ bevestig ](../assets/fix.svg) een gebiedsdeelversie in het `composer.json` dossier.

## [!DNL Live Search] 4.2.0

_31 Mei, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Bijgewerkte Levende uitbreiding van het Onderzoek om PLP widgets versie 2.0.0 te gebruiken.

## [!DNL Live Search] 4.1.2

_Mei 16, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

### Updates

![ bevestig ](../assets/fix.svg) de [`productSearch` ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#filtering-by-categories) vraag van GraphQL aan correct filter dat op `categoryPath` en `categoryList` voor categorieën wordt gebaseerd.

## [!DNL Live Search] 4.1.1

_Maart 19, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

### Nieuwe functies

![ Nieuwe ](../assets/new.svg) Toegevoegde taalsteun voor Pools.
![ Nieuw ](../assets/new.svg) [!DNL Live Search] steunt nu PHP 8.3 voor installaties die Adobe Commerce 2.4.4 in werking stellen.

## [!DNL Live Search] 4.1.0

_22 Februari, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

### Nieuwe functies

![ Nieuw ](../assets/new.svg) [[!DNL Data Management Dashboard] ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) is nu beschikbaar. Dit vernieuwde dashboard biedt inzichten in gegevensstromen voor [!DNL Product Recommendations] , [!DNL Live Search] en [!DNL Catalog Service] .

### Updates

![ bevestig ](../assets/fix.svg) een kwestie die een fout veroorzaakte wanneer de gastgebruikers producten aan een kar in niet-gebrek opslagmeningen toevoegden.
![ beval ](../assets/fix.svg) een kwestie die onderzoekspopover veroorzaakte om het muntsymbool altijd vóór de prijswaarde ongeacht scènemontages te tonen.
![ bevestig ](../assets/fix.svg) Verwijderde onnodige typedefinities voor gehandicapte kernstoppen om verenigbaarheidskwesties op installatie te bevestigen.

## [!DNL Live Search] 4.0.0

_13 November, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

### Nieuwe functies

![ Nieuw ](../assets/new.svg) [!DNL Live Search] steunt nu kleurenstalen in PLP widget.
![ Nieuw ](../assets/new.svg) [!DNL Live Search] toont nu de categorienaam eerder dan categorieId.
![ Nieuw ](../assets/new.svg) [!DNL Live Search] steunt nu strikethrough prijzen in PLOP widget.
![ Nieuw ](../assets/new.svg) introduceerde de &quot;knoop van de Filters van de Huid&quot;om het filterenpaneel te verbergen.


### Updates

![ bevestig ](../assets/fix.svg) De [!DNL Live Search] PLP widget wordt nu toegelaten door gebrek voor nieuwe installaties.
![ bevestig ](../assets/fix.svg) de Adapter van het Onderzoek wordt afgekeurd. In de toekomst wordt de zoekadapter alleen bijgewerkt om beveiligingsproblemen te verhelpen.
![ bevestig ](../assets/fix.svg) opnieuw gevormde CSS stijlen om widgetklassen beter te isoleren.
![ Kleine insectenmoeilijke situaties van 0} herstellen](../assets/fix.svg)

Nadat u versie 3.1.1 of hoger hebt geïnstalleerd, schakelt u de nieuwe indexen in:

- Diervoeders productprijzen
- Websitegegevensinvoer
- Scopes klant groepeert gegevenstoevoer

Na bevordering, test de bijgewerkte configuratie in QA of het Opvoeren alvorens de veranderingen in productie te duwen.

+++3.1.1 en eerdere

### [!DNL Live Search] 3.1.1

_15 September, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Nieuwe het Merchandising tabel van de Categorie is toegevoegd. Gebruikers kunnen nu intelligente waarderingen en handmatige waarderingen (speld, boost, bury, hide) per categorie toevoegen
![ Nieuwe ](../assets/new.svg) Gebruikers kunnen één enkele categorieregel met intelligente of handboek toevoegen rangschikking
![ Nieuwe ](../assets/new.svg) Gebruikers kunnen Intelligente het Rangschikken regels aan subcategorieën nu toevoegen
![ Nieuwe ](../assets/new.svg) Gedetailleerde informatie wordt verstrekt wanneer het schrappen van subcategorieën met intelligente rangschikking
![ Nieuw ](../assets/new.svg) voegde de capaciteit toe om regels voor geërfte het rangschikken strategieën te schrappen
![ Nieuw ](../assets/new.svg) voegde de capaciteit toe om regels voor één enkele categorie te schrappen
![ Nieuwe ](../assets/new.svg) Gebruikers kunnen nu op categorienaam zoeken wanneer het toevoegen van een regel
![ Nieuw ](../assets/new.svg) met de Mening van de Boom van de Categorie, kunnen de gebruikers nu bekijken welke categorie toegepaste regels heeft.
![ Nieuwe ](../assets/new.svg) Voorproef van de Categorie toont slechts de geselecteerde categorie.
![ Nieuwe ](../assets/new.svg) CIF van AEM [ Popover widget ](https://github.com/adobe/aem-cif-guides-venia/pull/319) en [ PLP widget ](https://github.com/adobe/aem-cif-guides-venia/pull/320) componenten staan AEM plaatsen toe om uit [!DNL Live Search] voordeel te halen.

#### Updates

![ Repareer ](../assets/fix.svg) de lijstgrootte van de Producten en de feeds van de Prijs zijn zeer verminderd. Tabellen `catalog_data_exporter_products` en `catalog_data_exporter_product_prices` moeten aanzienlijk worden verkleind.
![ Repareren ](../assets/fix.svg) het lusje van &quot;Regels&quot;wordt anders genoemd in &quot;de Regels van het Onderzoek&quot;
![ Repareren ](../assets/fix.svg) wanneer het rangschikken door &quot;trending&quot;, kunt u nu tussen kiezen:
- 3 dagen (standaard)
- 14 dagen
- 30 dagen
![ bevestig ](../assets/fix.svg) &quot;Gebeurtenissen&quot;(Bost/Pijn/Doordrukken/Verbergen) is anders genoemd aan &quot;Handmatige Rangschikking&quot;
![ Repareren ](../assets/fix.svg) &quot;het Rangschikken Type&quot;is anders genoemd aan &quot;Intelligente rangschikking&quot;
![ bevestig ](../assets/fix.svg) kleine insectenmoeilijke situaties

### [!DNL Live Search] 3.1.0

_September 1, 2023_

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

#### Updates

![ Repareer ](../assets/fix.svg) het Product van de Lijst widget is bijgewerkt om de [ Dienst API van de Catalogus te gebruiken ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/).

### [!DNL Live Search] 3.0.2

_7 Augustus, 2023_

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

#### Nieuwe functies

![ Nieuw ](../assets/new.svg) De volgende waarden zijn toegevoegd aan het `storeDetails` voorwerp:

- &quot;Alle producten per pagina toestaan&quot;
- Valuta
- &quot;Producten per pagina op raster Toegestane waarden&quot;
- &quot;Producten per pagina op standaardwaarde van raster&quot;
- Winkeltaal

#### Updates

![ de modules van de Dienst van de Catalogus van 0} herstellen {zijn toegevoegd aan het metapakket om geavanceerde gegevensherwinning te steunen.
](../assets/fix.svg)
![ bevestig ](../assets/fix.svg) **Mijn de paginanavigatie van de Rekening** niet meer verdwijnt wanneer het gebruiken van de Van de lijst van het Product widget van de Pagina.

Handelaars moeten de extensieversie van [!DNL Live Search] >= 3.0.2 upgraden om toegang te krijgen tot deze functies.

U wordt aangeraden een upgrade uit te voeren en te testen voordat u naar de productie gaat. Overweeg om de productieomgeving tijdens niet-piekuren te upgraden nadat de resultaten van de testomgeving zijn gecontroleerd.

#### Beperkingen

Google Tag Manager mislukt als u de widget pagina met aanbiedingen van producten voor live zoeken gebruikt. Gebruik de standaardzoekadapter als Google-tagbeheer nodig is.

### [!DNL Live Search] 3.0.1

_Maart 14, 2023_

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

#### Nieuwe functies

![ Nieuwe ](../assets/new.svg) Kaart van het Punt van het Product in de voorproef van Regels
![ Nieuwe ](../assets/new.svg) [ Van het Product het Van een lijst weergeven widget van de Pagina ](https://experienceleague.adobe.com/en/docs/commerce/live-search/live-search-storefront/plp-styling)
![ Nieuwe ](../assets/new.svg) [ Categorie het filtreren opties ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
![ Nieuw ](../assets/new.svg) voegde de capaciteit toe om te slepen en te laten vallen om de gebeurtenissen van de Speld tot stand te brengen
![ Nieuwe ](../assets/new.svg) Nieuwe Vastzetten acties:
- Vastzetten op steunpunt - Knop Vastzetten om met één klik een vastpingebeurtenis te maken
- Aan bovenkant vastzetten - Plaatst product op de eerste positie
- Vastzetten aan onderzijde - Plaatst het product onder aan de resultaten
- Een gebeurtenis met één klik vrijmaken
![ Nieuw ](../assets/new.svg) [ Intelligente Rangschikking voor regels ](https://experienceleague.adobe.com/en/docs/commerce/live-search/live-search-admin/rules/rules-add)
![ Nieuw ](../assets/new.svg) [!DNL Live Search] steunt nu volledige [ mogelijkheden van Inventory management {in Commerce (vroeger weet als Voorraad Multi-Source, of MSI). ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) Om volledige steun toe te laten, moet u [ de gebiedsdeelmodule ](install.md#update) aan versie 102.2.0+ bijwerken.`commerce-data-export`

#### Updates

![ Repareren ](../assets/fix.svg) vormt nu automatisch Regels sorteert posities uniek
![ Repareren ](../assets/fix.svg) Het schrappen van een bestaande gebeurtenis werkt nu voorproef bij
![ bevestig ](../assets/fix.svg) Regels met geen gebeurtenissen kunnen worden bewaard
![ Bevestig ](../assets/fix.svg) verwijdert facetfactor &quot;Uitgezochte Type&quot;selecteur
![ Repareren ](../assets/fix.svg) Toegevoegde nieuwe &quot;het Uitgeven&quot;status voor niet bewaarde regels

#### Oplossingen

![ bevestig ](../assets/fix.svg) Vaste serverfout wanneer er een onvoltooide gebeurtenis tijdens sparen is
![ Vaste correctie ](../assets/fix.svg) correct schrappend specifieke gebeurtenis wanneer er veelvoudige gebeurtenissen zijn
![ Vaste ](../assets/fix.svg) bestaande regelgebeurtenis niet bijwerken wanneer de nieuwe gebeurtenis is toegevoegd
![ Vaste Reparatie ](../assets/fix.svg) op tweede &quot;geef&quot;klik van details uit, [!DNL Live Search] pagina die herladen vereist
![ bevestig ](../assets/fix.svg) Synoniemen: Vaste een kwestie wanneer een gebruiker uit input klikte, konden zij niet de nadruk op het gebied terugkeren
![ bevestig ](../assets/fix.svg) Andere minder belangrijke insectenmoeilijke situaties en prestatiesupdates
![ Bug ](../assets/bug.svg) - het Rangschikken door &quot;voor u&quot;wordt geadviseerd wordt slechts gesteund binnen Levende widgets van het Onderzoek. Deze functie wordt niet ondersteund met de standaardzoekfunctie voor Luma en PWA.
![ Bug ](../assets/bug.svg) - de facetten van de prijsattributen van de Douane geven niet correct in Luma terug, maar API behoorlijk filters op hen.

Handelaars moeten de extensieversie van [!DNL Live Search] >= 3.0.1 upgraden om toegang te krijgen tot deze functies.

U wordt aangeraden een upgrade uit te voeren en te testen voordat u naar de productie gaat. Overweeg om de productieomgeving tijdens niet-piekuren te upgraden nadat de resultaten van de testomgeving zijn gecontroleerd.

### [!DNL Live Search] 2.0.5

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Repareren ](../assets/fix.svg) - Levend Onderzoek zou een fout werpen wanneer de middelen van SDK niet beschikbaar wegens netwerkkwesties waren. Deze fout is opgelost.

Handelaars moeten de Live Search extensie versie >= 2.0.5 bevorderen om tot deze eigenschappen toegang te hebben.

U wordt aangeraden een upgrade uit te voeren en te testen voordat u naar de productie gaat. Overweeg om de productieomgeving tijdens niet-piekuren te upgraden nadat de resultaten van de testomgeving zijn gecontroleerd.

### [!DNL Live Search] 2.0.4

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) Levend Onderzoek steunt nu het filtreren door de &quot;Vertoning uit Producten van het Voorraad&quot;het plaatsen in admin. Als &#39;Weergave van producten uit voorraad&#39; is ingesteld op false, wordt `inStock = true` toegevoegd aan het filter.
![ Repareren ](../assets/fix.svg) om prestaties te verbeteren, is het &quot;Suggestions&quot;blok verwijderd uit Live Onderzoek popup. De gegevens worden nog steeds doorgegeven via GraphQL, voor het geval u de functie wilt vervangen.
![ Repareren ](../assets/fix.svg) `categories` en `categoryPath` hebben `categoryIds` voor categorie het filtreren vervangen. Lees meer in het [ productSearch ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) onderwerp.
![ Repareren ](../assets/fix.svg) eerder, een gebruiker verbonden aan een bedrijf B2B zou een onjuiste Code van de Groep van de Klant ontvangen wanneer het doen van onderzoeken. Live zoeken retourneert nu de juiste waarde.
![ Repareren ](../assets/fix.svg) eerder, wanneer het zoeken naar een termijn die niet bestaat, zou Levende Onderzoek een fout terugkeren. Die bug is nu opgelost.

Handelaars moeten de extensieversie van [!DNL Live Search] >= 2.0.4 upgraden om toegang te krijgen tot deze functies.

De gebruikers worden geadviseerd om te bevorderen en te testen alvorens aan productie te duwen. Overweeg om de productieomgeving tijdens niet-piekuren te upgraden nadat de resultaten van de testomgeving zijn gecontroleerd.

### [!DNL Live Search] 2.0.3

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) Levend Onderzoek steunt nu eigenschappen B2B door categorietoestemmingen, gedeelde catalogi, en klantgroep-specifieke tarifering te erkennen.

Handelaars moeten de extensieversie van [!DNL Live Search] >= 2.0.3 upgraden om toegang te krijgen tot deze functies.

De gebruikers worden geadviseerd om te bevorderen en te testen alvorens aan productie te duwen. Overweeg om de productieomgeving tijdens niet-piekuren te upgraden nadat de resultaten van de testomgeving zijn gecontroleerd.

### [!DNL Live Search] 2.0

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

Bestaande [!DNL Live Search] -installaties moeten worden bijgewerkt naar [!DNL Live Search] 2.0.0 om te kunnen profiteren van de volgende nieuwe functies, oplossingen en verbeteringen:

![ Nieuw ](../assets/new.svg) [!DNL Live Search] steunt nu PHP 8.1 voor installaties die Adobe Commerce 2.4.4 in werking stellen.
![ Nieuw ](../assets/new.svg) de `Magento_ElasticsearchCatalogPermissionsGraphQl` module wordt toegevoegd aan de lijst van modules die tijdens de installatie worden onbruikbaar gemaakt.
![ Nieuw ](../assets/new.svg) Het aantal beschikbare lijnen in [[!DNL storefront popover]](overview.md) kan van *Admin* worden gevormd.
![ Nieuwe ](../assets/new.svg) Beta [ PWA ](https://developer.adobe.com/commerce/pwa-studio/) gesteund voor [!DNL Live Search].
![ Nieuw ](../assets/new.svg) het [!DNL Live Search] installatieproces wordt bijgewerkt met geavanceerde procesveranderingen.
![ herstellen ](../assets/fix.svg) [ verwijderde verbinding van het Geavanceerd Onderzoek ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) {van storefront footer.
![ Bug ](../assets/bug.svg) de volgende productattributen worden niet gesteund door [ Commerce GraphQL API ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) wanneer gebruikt met betrekking tot de bètaversie van PWA: `description`, `name`, `short_description`
![ Bug ](../assets/bug.svg) De bètaversie van PWA voor [!DNL Live Search] steunt [ gebeurtenis behandeling ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) niet.

### [!DNL Live Search] 1.3.1

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![ herstellen ](../assets/fix.svg) [ keert de prijsattributen van de Douane niet meer een fout terug wanneer gevormd als a ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types) facet [.
](facets-add.md)
![ bevestig ](../assets/fix.svg) Vaste kwestie die een fout veroorzaakte om voor te komen wanneer geen [ muntsymbool ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration#step-5-customize-currency-symbols-optional) (`data-currency-symbol`) beschikbaar is.
![ Repareren ](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) toont nu de [ Speciale Prijs ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) (minimumdefinitieve prijs) wanneer beschikbaar.

### [!DNL Live Search] 1.3.0

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![ Nieuwe ](../assets/new.svg) [ Prestaties ](performance.md) rapporterend dashboard verstrekt insight in onderzoekstermijnen die de kopers gebruiken.
![ Nieuwe ](../assets/new.svg) [!DNL Live Search] [ Gebeurtenissen Storefront SDK ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) verleent toegang tot een gemeenschappelijke gegevenslaag met gebeurtenis het publiceren en de abonnementsdiensten, en metriek.
![ Repareren ](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) heeft een nieuwe `active` klasse voor de `.search-autocomplete` container die zicht controleert.
![ Repareren ](../assets/fix.svg) in de storefront, wordt de [ 3} voettekstverbinding van de Termen van het Onderzoek {verwijderd en zijn geheim voorgeheugen onbruikbaar gemaakt voor ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms) installaties.
[!DNL Live Search]
![ Bug ](../assets/bug.svg) Reparatie voor de handvatten van de Adapter van het Onderzoek dubbele producten.
![ Bug ](../assets/bug.svg) [!DNL Live Search] steunt [ enig-bron ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage) (fysieke) inventarisplaatsen met veelvoudige (virtuele) [ voorraden ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage). Meerdere inventarisbronnen worden nu niet ondersteund.

### [!DNL Live Search] 1.2.0

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![ Nieuwe ](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) vertoningen gesuggereerde producten en duimnagelbeelden van hoogste onderzoeksresultaten als kopers typekeuringen in het vakje van het Onderzoek.
![ Nieuwe ](../assets/new.svg) Commerce *Admin* zittingsverblijven open tijdens uitgebreide periodes van toetsenbordinactiviteit
![ Nieuw ](../assets/new.svg) [!DNL Live Search] wordt automatisch toegelaten na onboarding
![ Repareren ](../assets/fix.svg) Aanvankelijke het indexeren tijd is minder dan een uur
![ herstellen ](../assets/fix.svg) Incrementele productupdates dichtbij echt - tijd (na installatie en opstelling)
![ bevestig ](../assets/fix.svg) Geschikte kolommen in Synonym redacteur
![ Bevestigen ](../assets/fix.svg) [!DNL Live Search] werpt niet meer een fout als de onderzoekscriteria lege waarde van de soortorde bevatten
![ Repareren ](../assets/fix.svg) het filtreren van de Waaier breekt niet meer als de attributencodes koorden &quot;aan&quot;of &quot;van&quot;bevatten

### [!DNL Live Search] 1.1.0

[!BADGE  Ondersteunde ]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![ Bug ](../assets/bug.svg) de [!DNL Live Search] dienst steunt slechts de [ basismunt ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration) van de installatie van Adobe Commerce.
![ Bug ](../assets/bug.svg) wanneer het toevoegen van een facet, werkt het Diervoer van de Attributen van het Product niet correct bij wanneer reeks aan `Update on Save`. Om dit probleem te vermijden, ga naar [ het Beheer van de Index ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) en plaats de Diersoort van de Attributen van het Product aan `Update by Schedule`.
![ Bug ](../assets/bug.svg) [!DNL Live Search] synoniemen worden bepaald per opslagmening, maar momenteel opgeslagen per website en geïdentificeerd met een combinatie van `environmentId` en `storeViewCode`. Dit heeft tot gevolg dat alle websites en winkelweergaven in de Adobe Commerce-installatie synoniemen delen. De meest recente reeks synoniemen voor de archiefmening krijgt belangrijkheid.
![ Bug ](../assets/bug.svg) als een synoniem termijn veelvoudige woorden bevat, wordt elk woord behandeld als afzonderlijk synoniem. Als u bijvoorbeeld &#39;tijdstuk&#39; definieert als een synoniem van &#39;watch&#39;, worden zowel &#39;time&#39; als &#39;piece&#39; beschouwd als synoniemen van &#39;watch&#39;.

+++

## Documentatie

Meer informatie:

- [ de Documentatie van de Ontwikkelaar van Adobe Commerce ](https://developer.adobe.com/commerce/docs)
- [ de Gids van de Gebruiker van Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce)
- [[!DNL Live Search]  op Marketplace ](https://commercemarketplace.adobe.com/magento-live-search.html)
