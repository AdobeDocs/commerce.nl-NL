---
title: '[!DNL Live Search] Opmerkingen bij de release'
description: De recentste versieinformatie voor  [!DNL Live Search]  van Adobe Commerce.
feature: Services, Search, Release Notes
exl-id: 099cf79c-968c-4381-b66d-7f6141ad2db3
source-git-commit: 85753091e3f7708c65cc8465050d03f44add04ae
workflow-type: tm+mt
source-wordcount: '2688'
ht-degree: 0%

---

# [!DNL Live Search] Opmerkingen bij de release

In deze releaseopmerkingen worden de meest recente versies van [!DNL Live Search] beschreven.

Er is ondersteuning voor de nieuwste versie. Opmerkingen bij de release voor oudere versies worden ter referentie verschaft.
Updates zijn:

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Nieuwe eigenschappen
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Bevestigingen en verbeteringen
![&#x200B; Bug &#x200B;](../assets/bug.svg) Bekende kwesties

## Gehoste service-updates

Deze nota&#39;s beschrijven updates die buiten een versioned versie of verbeteringen aan de ontvangen dienst werden gepubliceerd.

_1 Oktober, 2025_

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde nieuwe genoemde sleutel van de gegevensopslag `ds-logged-in` voor klant het programma geopende gegevens.

_29 April, 2025_

![&#x200B; bevond &#x200B;](../assets/fix.svg) Vast een kwestie waar de **Uitvoer naar CSV** rapport over het [**Prestaties**](./performance.md) lusje niet alle gegevens omvatte die in de datumwaaier werden gespecificeerd.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie Vaste waar u a [&#x200B; geen handelende regel &#x200B;](./rules.md) kon bewaren als de filter van de onderzoeksvraag werd gebruikt.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie waar [&#x200B; vastgezette producten &#x200B;](./facets-manage.md#pinunpin-facet) niet vermeld bij de bovenkant van de resultatenpagina waren.

_21 April, 2025_

![&#x200B; beval &#x200B;](../assets/fix.svg) een kwestie met de waaierfilter voor prijzen vast zodat de producten die aan de hogere waaier gelijk zijn niet inbegrepen in de resultaten zijn. Deze verandering richt zich op hoe de prijswaaiers voor facetten worden bepaald.

_3 April, 2025_

![&#x200B; Repareren &#x200B;](../assets/fix.svg) werkte de uitbreiding van de Uitvoer van Gegevens SaaS bij om de &quot;Producten te verwijderen moet aan de wortelcategorie&quot;worden toegewezen [&#x200B; beperking &#x200B;](boundaries-limits.md#b2b-and-category-permissions) voor B2B verkopers. Zie [&#x200B; de uitbreiding van de gegevensuitvoer &#x200B;](../data-export/manage-extension.md) leiden om te leren hoe te om de uitbreiding van de Uitvoer van Gegevens SaaS aan versie 103.4.0+ bij te werken.

_Februari 20, 2025_

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Commerce steunt synoniemen van meerdere woorden. [&#x200B; leer meer &#x200B;](synonyms-type.md#multi-word-synonym-behavior). Ondersteuning voor synoniemen met meerdere woorden is alleen beschikbaar na deze releasedatum van 20 februari. Om het even welke bestaande synoniemen van meerdere woorden vereisen een volledige herdex om te werken, die u kunt verzoeken door [&#x200B; tot een steunkaartje &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) te leiden.

_Januari 31, 2025_

![&#x200B; Nieuw &#x200B;](../assets/new.svg) Er is een nieuw beleid van het gegevensbehoud voor ongevraagde catalogusgegevens in uw het testen milieu. [Meer info](overview.md#catalog-data-retention-policy).

_19 september, 2024_

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) versie van Beta voor de volgende geavanceerde onderzoeksmogelijkheden: gelaagd onderzoek gebruikend `startsWith` en `contains`. [Meer info](workspace.md#layered-search-and-expansion-of-search-types).

_4 September, 2024_

![&#x200B; bevestig &#x200B;](../assets/fix.svg) verhoogde het maximumaantal emmers die [&#x200B; binnen een facet &#x200B;](boundaries-limits.md#facets) aan 100 kunnen zijn teruggekeerd.

_7 Augustus, 2024_

![&#x200B; bevestig &#x200B;](../assets/fix.svg) verhoogde de maximumintervalwaarde, of prijswaaier voor [&#x200B; prijsvermindering &#x200B;](settings.md#price-faceting) van 10.000 tot 40.000.000.

_13 Februari, 2024_

![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Live Search] steunt nu het plaatsen van een standaardregel voor [&#x200B; Merchandising van het Onderzoek &#x200B;](rules.md).

_12 oktober 2023_

![&#x200B; de Nieuwe &#x200B;](../assets/new.svg) beheerders van Commerce kunnen de taal van de index voor [!DNL Live Search] nu specificeren. Zie [&#x200B; Montages &#x200B;](settings.md).
![&#x200B; Repareer &#x200B;](../assets/fix.svg) het lusje van &quot;Regels van het Onderzoek&quot;is anders genoemd aan &quot;Verkoop van het Onderzoek&quot;.

_13 Juni, 2023_

![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie waar sommige karakters zoals citaten of apostroffen rangschikkende kwesties veroorzaakten. Deze problemen worden opgelost door opnieuw te indexeren.

_25 April, 2023_

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) [!DNL Live Search] klanten kunnen uit de nieuwe [&#x200B; SaaS prijsindexeerder &#x200B;](../price-index/price-indexing.md) nu voordeel halen.

### PLP-widget

_2 Februari, 2026_

![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie in PLP versie 2.3.0 waar browser achterknoop niet behoorlijk de pagineringsstaat in PLP widget bijwerkte.

_Mei 22, 2025_

![&#x200B; beval &#x200B;](../assets/fix.svg) een kwestie waar Add aan de knoop van de Kar in het Engels bleef toen de scène in Frans, Duits, Italiaans of Spaans werd veranderd.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie waar Add aan de knoop van de Kar voor uit-van-voorraad producten werd getoond.

_31 Mei, 2024_

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Vrijgegeven versie 2.0.0 van PLP widget, die steun voor de volgende eigenschappen toevoegt:

- Toevoegen aan winkelwagentjes - Alleen beschikbaar voor eenvoudige producten.
- Meerdere afbeeldingen per product - de afbeelding kan veranderen wanneer een andere kleur wordt gekozen voor een configureerbaar product.

_27 oktober, 2023_

![&#x200B; Nieuw &#x200B;](../assets/new.svg) de [!DNL Live Search] PLP widget steunt nu kleurenstalen.

## [!DNL Live Search] 4.6.1

_19 februari, 2026_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) een fout die onder bepaalde voorwaarden met betrekking tot de functionaliteit van de uitbreiding van de Visuele Merchandiser kon voorkomen.

## [!DNL Live Search] 4.6.0

_9 Oktober, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) versie GA voor de volgende geavanceerde onderzoeksmogelijkheden: gelaagd onderzoek gebruikend `startsWith` en `contains`. [&#x200B; leer meer &#x200B;](workspace.md#layered-search-and-expansion-of-search-types).
![&#x200B; Repareer &#x200B;](../assets/fix.svg) het `ProductInterface` voorwerp in de [&#x200B; Levende dienst van het Onderzoek &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) is afgekeurd. Gebruik in plaats hiervan het `ProductView` -object in de catalogusservice.

## [!DNL Live Search] 4.5.0

_5 September, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) Levend Onderzoek respecteert nu volledig [&#x200B; wijze van de koekjesbeperking &#x200B;](install.md#cookies) door gegevensinzameling en opslag in koekjes/lokale opslag te verhinderen wanneer de beperkingen worden toegelaten.

## [!DNL Live Search] 4.4.1

_Augustus 11, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Vaste het diensteindpunt van de catalogusdienst van 0&rbrace; herstellen &lbrace;voor zandbakmilieu&#39;s.](../assets/fix.svg)

## [!DNL Live Search] 4.4.0

_14 juli 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) verhoogde de [&#x200B; prijs groeperende &#x200B;](./settings.md#price-faceting) grens van 50 tot 100.

## [!DNL Live Search] 4.3.0

_Maart 11, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Repareren &#x200B;](../assets/fix.svg) [!DNL Live Search] steunt nu PHP 8.4 voor installaties die Adobe Commerce 2.4.8-beta2 in werking stellen.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie waar de Adapter van het Onderzoek niet compatibel met `psr/http-message:2.0` was.

## [!DNL Live Search] 4.2.3

_13 Februari, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie waar de pagina van het ordendetail het orderaantal, de datum, en de **[!UICONTROL Reorder]** knoop mist.

## [!DNL Live Search] 4.2.2

_6 Januari, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie die een fout met de `categoryList` vraag GraphqL op Adobe Commerce versie 2.4.5 en vroeger veroorzaakte.

## [!DNL Live Search] 4.2.1

_31 Juli, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie waar bepaalde manuscripten niet op de controlepagina laadden.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) een gebiedsdeelversie in het `composer.json` dossier.

## [!DNL Live Search] 4.2.0

_31 Mei, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Bijgewerkte Levende uitbreiding van het Onderzoek om PLP widgets versie 2.0.0 te gebruiken.

## [!DNL Live Search] 4.1.2

_Mei 16, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

### Updates

![&#x200B; bevestig &#x200B;](../assets/fix.svg) de [`productSearch` &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#filtering-by-categories) vraag van GraphQL aan correct filter dat op `categoryPath` en `categoryList` voor categorieën wordt gebaseerd.

## [!DNL Live Search] 4.1.1

_Maart 19, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

### Nieuwe functies

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde taalsteun voor Pools.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Live Search] steunt nu PHP 8.3 voor installaties die Adobe Commerce 2.4.4 in werking stellen.

## [!DNL Live Search] 4.1.0

_22 Februari, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

### Nieuwe functies

![&#x200B; Nieuw &#x200B;](../assets/new.svg) [[!DNL Data Management Dashboard] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard) is nu beschikbaar. Dit vernieuwde dashboard biedt inzichten in gegevensstromen voor [!DNL Product Recommendations] , [!DNL Live Search] en [!DNL Catalog Service] .

### Updates

![&#x200B; bevestig &#x200B;](../assets/fix.svg) een kwestie die een fout veroorzaakte wanneer de gastgebruikers producten aan een kar in niet-gebrek opslagmeningen toevoegden.
![&#x200B; beval &#x200B;](../assets/fix.svg) een kwestie die onderzoekspopover veroorzaakte om het muntsymbool altijd vóór de prijswaarde ongeacht scènemontages te tonen.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Verwijderde onnodige typedefinities voor gehandicapte kernstoppen om verenigbaarheidskwesties op installatie te bevestigen.

## [!DNL Live Search] 4.0.0

_13 November, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

### Nieuwe functies

![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Live Search] steunt nu kleurenstalen in PLP widget.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Live Search] toont nu de categorienaam eerder dan categorieId.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Live Search] steunt nu strikethrough prijzen in PLOP widget.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) introduceerde de &quot;knoop van de Filters van de Huid&quot;om het filterenpaneel te verbergen.


### Updates

![&#x200B; bevestig &#x200B;](../assets/fix.svg) De [!DNL Live Search] PLP widget wordt nu toegelaten door gebrek voor nieuwe installaties.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) de Adapter van het Onderzoek wordt afgekeurd. In de toekomst wordt de zoekadapter alleen bijgewerkt om beveiligingsproblemen te verhelpen.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) opnieuw gevormde CSS stijlen om widgetklassen beter te isoleren.
![&#x200B; Kleine insectenmoeilijke situaties van 0&rbrace; herstellen](../assets/fix.svg)

Nadat u versie 3.1.1 of hoger hebt geïnstalleerd, schakelt u de nieuwe indexen in:

- Diervoeders productprijzen
- Websitegegevensinvoer
- Scopes klant groepeert gegevenstoevoer

Na bevordering, test de bijgewerkte configuratie in QA of het Opvoeren alvorens de veranderingen in productie te duwen.

+++3.1.1 en eerdere

### [!DNL Live Search] 3.1.1

_15 September, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Nieuwe het Merchandising tabel van de Categorie is toegevoegd. Gebruikers kunnen nu intelligente waarderingen en handmatige waarderingen (speld, boost, bury, hide) per categorie toevoegen
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Gebruikers kunnen één enkele categorieregel met intelligente of handboek toevoegen rangschikking
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Gebruikers kunnen Intelligente het Rangschikken regels aan subcategorieën nu toevoegen
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Gedetailleerde informatie wordt verstrekt wanneer het schrappen van subcategorieën met intelligente rangschikking
![&#x200B; Nieuw &#x200B;](../assets/new.svg) voegde de capaciteit toe om regels voor geërfte het rangschikken strategieën te schrappen
![&#x200B; Nieuw &#x200B;](../assets/new.svg) voegde de capaciteit toe om regels voor één enkele categorie te schrappen
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Gebruikers kunnen nu op categorienaam zoeken wanneer het toevoegen van een regel
![&#x200B; Nieuw &#x200B;](../assets/new.svg) met de Mening van de Boom van de Categorie, kunnen de gebruikers nu bekijken welke categorie toegepaste regels heeft.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Voorproef van de Categorie toont slechts de geselecteerde categorie.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) CIF van AEM [&#x200B; Popover widget &#x200B;](https://github.com/adobe/aem-cif-guides-venia/pull/319) en [&#x200B; PLP widget &#x200B;](https://github.com/adobe/aem-cif-guides-venia/pull/320) componenten staan AEM plaatsen toe om uit [!DNL Live Search] voordeel te halen.

#### Updates

![&#x200B; Repareer &#x200B;](../assets/fix.svg) de lijstgrootte van de Producten en de feeds van de Prijs zijn zeer verminderd. Tabellen `catalog_data_exporter_products` en `catalog_data_exporter_product_prices` moeten aanzienlijk worden verkleind.
![&#x200B; Repareren &#x200B;](../assets/fix.svg) het lusje van &quot;Regels&quot;wordt anders genoemd in &quot;de Regels van het Onderzoek&quot;
![&#x200B; Repareren &#x200B;](../assets/fix.svg) wanneer het rangschikken door &quot;trending&quot;, kunt u nu tussen kiezen:
- 3 dagen (standaard)
- 14 dagen
- 30 dagen
![&#x200B; bevestig &#x200B;](../assets/fix.svg) &quot;Gebeurtenissen&quot;(Bost/Pijn/Doordrukken/Verbergen) is anders genoemd aan &quot;Handmatige Rangschikking&quot;
![&#x200B; Repareren &#x200B;](../assets/fix.svg) &quot;het Rangschikken Type&quot;is anders genoemd aan &quot;Intelligente rangschikking&quot;
![&#x200B; bevestig &#x200B;](../assets/fix.svg) kleine insectenmoeilijke situaties

### [!DNL Live Search] 3.1.0

_September 1, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

#### Updates

![&#x200B; Repareer &#x200B;](../assets/fix.svg) het Product van de Lijst widget is bijgewerkt om de [&#x200B; Dienst API van de Catalogus te gebruiken &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/).

### [!DNL Live Search] 3.0.2

_7 Augustus, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

#### Nieuwe functies

![&#x200B; Nieuw &#x200B;](../assets/new.svg) De volgende waarden zijn toegevoegd aan het `storeDetails` voorwerp:

- &quot;Alle producten per pagina toestaan&quot;
- Valuta
- &quot;Producten per pagina op raster Toegestane waarden&quot;
- &quot;Producten per pagina op standaardwaarde van raster&quot;
- Winkeltaal

#### Updates

![&#128279;](../assets/fix.svg) de modules van de Dienst van de Catalogus van 0&rbrace; herstellen &lbrace;zijn toegevoegd aan het metapakket om geavanceerde gegevensherwinning te steunen.

![&#x200B; bevestig &#x200B;](../assets/fix.svg) **Mijn de paginanavigatie van de Rekening** niet meer verdwijnt wanneer het gebruiken van de Van de lijst van het Product widget van de Pagina.

Handelaars moeten de extensieversie van [!DNL Live Search] >= 3.0.2 upgraden om toegang te krijgen tot deze functies.

U wordt aangeraden een upgrade uit te voeren en te testen voordat u naar de productie gaat. Overweeg om de productieomgeving tijdens niet-piekuren te upgraden nadat de resultaten van de testomgeving zijn gecontroleerd.

#### Beperkingen

Google Tag Manager mislukt als u de widget pagina met aanbiedingen van producten voor live zoeken gebruikt. Gebruik de standaardzoekadapter als Google-tagbeheer nodig is.

### [!DNL Live Search] 3.0.1

_Maart 14, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

#### Nieuwe functies

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Kaart van het Punt van het Product in de voorproef van Regels
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) [&#x200B; Van het Product het Van een lijst weergeven widget van de Pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/live-search/live-search-storefront/plp-styling)
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) [&#x200B; Categorie het filtreren opties &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
![&#x200B; Nieuw &#x200B;](../assets/new.svg) voegde de capaciteit toe om te slepen en te laten vallen om de gebeurtenissen van de Speld tot stand te brengen
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Nieuwe Vastzetten acties:
- Vastzetten op steunpunt - Knop Vastzetten om met één klik een vastpingebeurtenis te maken
- Aan bovenkant vastzetten - Plaatst product op de eerste positie
- Vastzetten aan onderzijde - Plaatst het product onder aan de resultaten
- Een gebeurtenis met één klik vrijmaken
![&#x200B; Nieuw &#x200B;](../assets/new.svg) [&#x200B; Intelligente Rangschikking voor regels &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/live-search/live-search-admin/rules/rules-add)
![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Live Search] steunt nu volledige [&#x200B; mogelijkheden van Inventory management &lbrace;in Commerce (vroeger weet als Voorraad Multi-Source, of MSI). &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/inventory/introduction) Om volledige steun toe te laten, moet u [&#x200B; de gebiedsdeelmodule &#x200B;](install.md#update) aan versie 102.2.0+ bijwerken.`commerce-data-export`

#### Updates

![&#x200B; Repareren &#x200B;](../assets/fix.svg) vormt nu automatisch Regels sorteert posities uniek
![&#x200B; Repareren &#x200B;](../assets/fix.svg) Het schrappen van een bestaande gebeurtenis werkt nu voorproef bij
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Regels met geen gebeurtenissen kunnen worden bewaard
![&#x200B; Bevestig &#x200B;](../assets/fix.svg) verwijdert facetfactor &quot;Uitgezochte Type&quot;selecteur
![&#x200B; Repareren &#x200B;](../assets/fix.svg) Toegevoegde nieuwe &quot;het Uitgeven&quot;status voor niet bewaarde regels

#### Oplossingen

![&#x200B; bevestig &#x200B;](../assets/fix.svg) Vaste serverfout wanneer er een onvoltooide gebeurtenis tijdens sparen is
![&#x200B; Vaste correctie &#x200B;](../assets/fix.svg) correct schrappend specifieke gebeurtenis wanneer er veelvoudige gebeurtenissen zijn
![&#x200B; Vaste &#x200B;](../assets/fix.svg) bestaande regelgebeurtenis niet bijwerken wanneer de nieuwe gebeurtenis is toegevoegd
![&#x200B; Vaste Reparatie &#x200B;](../assets/fix.svg) op tweede &quot;geef&quot;klik van details uit, [!DNL Live Search] pagina die herladen vereist
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Synoniemen: Vaste een kwestie wanneer een gebruiker uit input klikte, konden zij niet de nadruk op het gebied terugkeren
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Andere minder belangrijke insectenmoeilijke situaties en prestatiesupdates
![&#x200B; Bug &#x200B;](../assets/bug.svg) - het Rangschikken door &quot;voor u&quot;wordt geadviseerd wordt slechts gesteund binnen Levende widgets van het Onderzoek. Deze functie wordt niet ondersteund met de standaardzoekfunctie voor Luma en PWA.
![&#x200B; Bug &#x200B;](../assets/bug.svg) - de facetten van de prijsattributen van de Douane geven niet correct in Luma terug, maar API behoorlijk filters op hen.

Handelaars moeten de extensieversie van [!DNL Live Search] >= 3.0.1 upgraden om toegang te krijgen tot deze functies.

U wordt aangeraden een upgrade uit te voeren en te testen voordat u naar de productie gaat. Overweeg om de productieomgeving tijdens niet-piekuren te upgraden nadat de resultaten van de testomgeving zijn gecontroleerd.

### [!DNL Live Search] 2.0.5

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Repareren &#x200B;](../assets/fix.svg) - Levend Onderzoek zou een fout werpen wanneer de middelen van SDK niet beschikbaar wegens netwerkkwesties waren. Deze fout is opgelost.

Handelaars moeten de Live Search extensie versie >= 2.0.5 bevorderen om tot deze eigenschappen toegang te hebben.

U wordt aangeraden een upgrade uit te voeren en te testen voordat u naar de productie gaat. Overweeg om de productieomgeving tijdens niet-piekuren te upgraden nadat de resultaten van de testomgeving zijn gecontroleerd.

### [!DNL Live Search] 2.0.4

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) Levend Onderzoek steunt nu het filtreren door de &quot;Vertoning uit Producten van het Voorraad&quot;het plaatsen in admin. Als &#39;Weergave van producten uit voorraad&#39; is ingesteld op false, wordt `inStock = true` toegevoegd aan het filter.
![&#x200B; Repareren &#x200B;](../assets/fix.svg) om prestaties te verbeteren, is het &quot;Suggestions&quot;blok verwijderd uit Live Onderzoek popup. De gegevens worden nog steeds doorgegeven via GraphQL, voor het geval u de functie wilt vervangen.
![&#x200B; Repareren &#x200B;](../assets/fix.svg) `categories` en `categoryPath` hebben `categoryIds` voor categorie het filtreren vervangen. Lees meer in het [&#x200B; productSearch &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) onderwerp.
![&#x200B; Repareren &#x200B;](../assets/fix.svg) eerder, een gebruiker verbonden aan een bedrijf B2B zou een onjuiste Code van de Groep van de Klant ontvangen wanneer het doen van onderzoeken. Live zoeken retourneert nu de juiste waarde.
![&#x200B; Repareren &#x200B;](../assets/fix.svg) eerder, wanneer het zoeken naar een termijn die niet bestaat, zou Levende Onderzoek een fout terugkeren. Die bug is nu opgelost.

Handelaars moeten de extensieversie van [!DNL Live Search] >= 2.0.4 upgraden om toegang te krijgen tot deze functies.

De gebruikers worden geadviseerd om te bevorderen en te testen alvorens aan productie te duwen. Overweeg om de productieomgeving tijdens niet-piekuren te upgraden nadat de resultaten van de testomgeving zijn gecontroleerd.

### [!DNL Live Search] 2.0.3

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) Levend Onderzoek steunt nu eigenschappen B2B door categorietoestemmingen, gedeelde catalogi, en klantgroep-specifieke tarifering te erkennen.

Handelaars moeten de extensieversie van [!DNL Live Search] >= 2.0.3 upgraden om toegang te krijgen tot deze functies.

De gebruikers worden geadviseerd om te bevorderen en te testen alvorens aan productie te duwen. Overweeg om de productieomgeving tijdens niet-piekuren te upgraden nadat de resultaten van de testomgeving zijn gecontroleerd.

### [!DNL Live Search] 2.0

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

Bestaande [!DNL Live Search] -installaties moeten worden bijgewerkt naar [!DNL Live Search] 2.0.0 om te kunnen profiteren van de volgende nieuwe functies, oplossingen en verbeteringen:

![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Live Search] steunt nu PHP 8.1 voor installaties die Adobe Commerce 2.4.4 in werking stellen.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) de `Magento_ElasticsearchCatalogPermissionsGraphQl` module wordt toegevoegd aan de lijst van modules die tijdens de installatie worden onbruikbaar gemaakt.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) Het aantal beschikbare lijnen in [[!DNL storefront popover]](overview.md) kan van *Admin* worden gevormd.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Beta [&#x200B; PWA &#x200B;](https://developer.adobe.com/commerce/pwa-studio/) gesteund voor [!DNL Live Search].
![&#x200B; Nieuw &#x200B;](../assets/new.svg) het [!DNL Live Search] installatieproces wordt bijgewerkt met geavanceerde procesveranderingen.
![&#x200B; herstellen &#x200B;](../assets/fix.svg) [&#x200B; verwijderde verbinding van het Geavanceerd Onderzoek &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/catalog/search/search) &lbrace;van storefront footer.
![&#x200B; Bug &#x200B;](../assets/bug.svg) de volgende productattributen worden niet gesteund door [&#x200B; Commerce GraphQL API &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) wanneer gebruikt met betrekking tot de bètaversie van PWA: `description`, `name`, `short_description`
![&#x200B; Bug &#x200B;](../assets/bug.svg) De bètaversie van PWA voor [!DNL Live Search] steunt [&#x200B; gebeurtenis behandeling &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) niet.

### [!DNL Live Search] 1.3.1

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; herstellen &#x200B;](../assets/fix.svg) [&#x200B; keert de prijsattributen van de Douane niet meer een fout terug wanneer gevormd als a &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/product-attributes/attributes-input-types) facet [&#128279;](facets-add.md).

![&#x200B; bevestig &#x200B;](../assets/fix.svg) Vaste kwestie die een fout veroorzaakte om voor te komen wanneer geen [&#x200B; muntsymbool &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration#step-5-customize-currency-symbols-optional) (`data-currency-symbol`) beschikbaar is.
![&#x200B; Repareren &#x200B;](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) toont nu de [&#x200B; Speciale Prijs &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/products/pricing/product-price-special) (minimumdefinitieve prijs) wanneer beschikbaar.

### [!DNL Live Search] 1.3.0

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) [&#x200B; Prestaties &#x200B;](performance.md) rapporterend dashboard verstrekt insight in onderzoekstermijnen die de kopers gebruiken.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) [!DNL Live Search] [&#x200B; Gebeurtenissen Storefront SDK &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) verleent toegang tot een gemeenschappelijke gegevenslaag met gebeurtenis het publiceren en de abonnementsdiensten, en metriek.
![&#x200B; Repareren &#x200B;](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) heeft een nieuwe `active` klasse voor de `.search-autocomplete` container die zicht controleert.
![&#x200B; Repareren &#x200B;](../assets/fix.svg) in de storefront, wordt de [&#x200B; 3&rbrace; voettekstverbinding van de Termen van het Onderzoek &lbrace;verwijderd en zijn geheim voorgeheugen onbruikbaar gemaakt voor &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/catalog/search/search-terms) installaties.
[!DNL Live Search]
![&#x200B; Bug &#x200B;](../assets/bug.svg) Reparatie voor de handvatten van de Adapter van het Onderzoek dubbele producten.
![&#x200B; Bug &#x200B;](../assets/bug.svg) [!DNL Live Search] steunt [&#x200B; enig-bron &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/inventory/sources/sources-manage) (fysieke) inventarisplaatsen met veelvoudige (virtuele) [&#x200B; voorraden &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/inventory/stocks/stocks-manage). Meerdere inventarisbronnen worden nu niet ondersteund.

### [!DNL Live Search] 1.2.0

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) vertoningen gesuggereerde producten en duimnagelbeelden van hoogste onderzoeksresultaten als kopers typekeuringen in het vakje van het Onderzoek.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Commerce *Admin* zittingsverblijven open tijdens uitgebreide periodes van toetsenbordinactiviteit
![&#x200B; Nieuw &#x200B;](../assets/new.svg) [!DNL Live Search] wordt automatisch toegelaten na onboarding
![&#x200B; Repareren &#x200B;](../assets/fix.svg) Aanvankelijke het indexeren tijd is minder dan een uur
![&#x200B; herstellen &#x200B;](../assets/fix.svg) Incrementele productupdates dichtbij echt - tijd (na installatie en opstelling)
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Geschikte kolommen in Synonym redacteur
![&#x200B; Bevestigen &#x200B;](../assets/fix.svg) [!DNL Live Search] werpt niet meer een fout als de onderzoekscriteria lege waarde van de soortorde bevatten
![&#x200B; Repareren &#x200B;](../assets/fix.svg) het filtreren van de Waaier breekt niet meer als de attributencodes koorden &quot;aan&quot;of &quot;van&quot;bevatten

### [!DNL Live Search] 1.1.0

[!BADGE &#x200B; Ondersteunde &#x200B;]{type="Informative" tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Bug &#x200B;](../assets/bug.svg) de [!DNL Live Search] dienst steunt slechts de [&#x200B; basismunt &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration) van de installatie van Adobe Commerce.
![&#x200B; Bug &#x200B;](../assets/bug.svg) wanneer het toevoegen van een facet, werkt het Diervoer van de Attributen van het Product niet correct bij wanneer reeks aan `Update on Save`. Om dit probleem te vermijden, ga naar [&#x200B; het Beheer van de Index &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/index-management) en plaats de Diersoort van de Attributen van het Product aan `Update by Schedule`.
![&#x200B; Bug &#x200B;](../assets/bug.svg) [!DNL Live Search] synoniemen worden bepaald per opslagmening, maar momenteel opgeslagen per website en geïdentificeerd met een combinatie van `environmentId` en `storeViewCode`. Dit heeft tot gevolg dat alle websites en winkelweergaven in de Adobe Commerce-installatie synoniemen delen. De meest recente reeks synoniemen voor de archiefmening krijgt belangrijkheid.
![&#x200B; Bug &#x200B;](../assets/bug.svg) als een synoniem termijn veelvoudige woorden bevat, wordt elk woord behandeld als afzonderlijk synoniem. Als u bijvoorbeeld &#39;tijdstuk&#39; definieert als een synoniem van &#39;watch&#39;, worden zowel &#39;time&#39; als &#39;piece&#39; beschouwd als synoniemen van &#39;watch&#39;.

+++

## Documentatie

Meer informatie:

- [&#x200B; de Documentatie van de Ontwikkelaar van Adobe Commerce &#x200B;](https://developer.adobe.com/commerce/docs)
- [&#x200B; de Gids van de Gebruiker van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce)
- [[!DNL Live Search]  op Marketplace &#x200B;](https://commercemarketplace.adobe.com/magento-live-search.html)
