---
title: Grenzen en grenzen
description: Leer over de grenzen en de grenzen voor  [!DNL Live Search]  om ervoor te zorgen het aan de behoeften van uw zaken voldoet.
role: Admin, Developer
exl-id: 28b8d98f-0784-4c4d-b382-81c01838e0de
source-git-commit: 90441950a71e4b25462a89f0cb7352fd8086ed6e
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---

# Grenzen en grenzen

Adobe Commerce biedt opties voor het zoeken naar sites. Controleer de volgende grenzen en grenzen om ervoor te zorgen dat [!DNL Live Search] en [!DNL Catalog Service] aan de behoeften van uw zaken voldoen. Als u geavanceerde onderzoeksmogelijkheden zoals inhoudsonderzoek nodig hebt, breng-uw-eigen-algoritme (BYOA), of op attribuut-gebaseerde handel, overweeg een derdezoekoplossing.

## Algemeen

- De [ Geavanceerde module van het Onderzoek ](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/catalog/search/search) wordt onbruikbaar gemaakt wanneer [!DNL Live Search] wordt geïnstalleerd, en de Geavanceerde verbinding van het Onderzoek in storefront wordt verwijderd.
- [ het Tarief van de Rij ](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/products/pricing/product-price-tier) wordt niet gesteund op het [!DNL Live Search] gebied en de Widget van de Pagina van het Product van de Lijst.
- Productprijzen omvatten btw, maar [!DNL Live Search] kan de btw niet als een afzonderlijke waarde weergeven.
- Zoeken naar inhoud (CMS-pagina&#39;s en -blokken) wordt niet ondersteund.
- Het maximumaantal resultaten dat kan worden gepagineerd, is 10.000. Om ervoor te zorgen dat kopers geen diepe paginering hoeven te gebruiken wanneer een categorie of zoekresultaat een groot aantal producten bevat, moet u zinvolle manieren bieden om producten te filteren.
- Er geldt een harde limiet van 1 MB per kenmerk, inclusief beschrijving en aangepaste kenmerken.
- De zoekadapter ondersteunt geen productkenmerken die zijn gemaakt met een aangepast bronmodel en die als facetten worden gebruikt. Om deze functionaliteit te steunen, moet u het [ product gebruiken dat van de Pagina Widget ](plp-styling.md) van de Pagina een lijst maakt.
- Aangepaste producttypen worden niet ondersteund.
- Aangepaste kenmerken die via programmacode met `"is_user_defined": false` zijn gemaakt, worden niet ondersteund.
- U kunt resultaten filtreren gebruikend &quot;begint met&quot;of &quot;bevat&quot;voorwaarden met sommige beperkingen zoals die in de [ ontwikkelaarsdocumentatie ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#limitations) worden beschreven.
- U kunt prestatiemetriek slechts volgen binnen het laatste jaar.
- Als een zoekquery meerdere woorden bevat, worden deze door de lege ruimte tussen de woorden als aparte zoektermen behandeld. Het gebruik [ synoniemen ](./synonyms.md) als u voor multiword onderzoeksvragen wilt rekenschap geven.

## Indexeren

- [!DNL Live Search] [ indexen ](indexing.md) tot een totaal van 450 productattributen per archiefmening. Deze worden als volgt verdeeld:
   - 50 sorteerbare kenmerken
   - 200 filterbare kenmerken
   - 200 doorzoekbare kenmerken
- [!DNL Live Search] indexeert alleen producten uit de Adobe Commerce-database.
- CMS-pagina&#39;s worden niet geïndexeerd.
- SKU-, naam- en categoriekenmerken kunnen standaard worden doorzocht en kunnen niet worden uitgesloten van de zoekopdracht. Zorg ervoor dat u de toewijzing van de producten uit de categorieën ongedaan maakt als ze niet in die categorieën mogen voorkomen.

## Facetten

- Van de reeks bepaalde filterbare attributen, kunt u tot 100 attributen als facetten vormen.
- Binnen een facet kunnen maximaal 100 emmers worden geretourneerd. Als u meer dan 100 emmers moet terugkeren, [ creeer een steunkaartje ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) zodat kan Adobe het prestatieseffect analyseren en bepalen als het haalbaar is om deze grens voor uw milieu te verhogen.
- Dynamische facetten kunnen prestatieproblemen veroorzaken in grote indexen en indexen met hoge rangorde. Als u dynamische facetten hebt gemaakt en u merkt dat de prestaties achteruitgaan of dat de pagina niet wordt geladen met time-outfouten, kunt u proberen uw facetten te wijzigen in vastgezet om te bepalen of dat het prestatieprobleem verhelpt.
- De voorraadstatus (`quantity_and_stock_status`) wordt niet ondersteund als facet. U kunt `inStock: 'true'` gebruiken om te filteren uit aandelenproducten. Dit wordt vanuit het vak in de module `LiveSearchAdapter` ondersteund wanneer &quot;Display out of stock products&quot; is ingesteld op &quot;True&quot; in [!DNL Commerce] Admin.
- Datumtypekenmerken worden niet als facet ondersteund.
- Wijzigingen die worden aangebracht in de metagegevens van het kenmerk nadat dat kenmerk als een facet is toegevoegd, worden niet doorgevoerd in het facet.
- U kunt maximaal 50 sorteerbare kenmerken en 200 doorzoekbare kenmerken hebben.

## Query

- [!DNL Live Search] gebruikt een uniek [ eindpunt van GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) voor vragen om eigenschappen zoals dynamisch facetten en onderzoek-als-u-type te steunen. Hoewel gelijkaardig aan [ GraphQL API ](https://developer.adobe.com/commerce/webapi/graphql/), zijn er een paar verschillen en sommige gebieden kunnen niet volledig compatibel zijn.
- Het maximumaantal resultaten dat in een onderzoeksvraag kan worden teruggekeerd is 10.000.
- Het maximale aantal resultaten per pagina is 500.
- Het is niet mogelijk om resultaten te filteren met behulp van een datumtype-kenmerk.

## Zoeken in merchandising

- Het maximumaantal onderzoek handelend [ regels ](rules.md) per archiefmening is 50.
- Het maximumaantal voorwaarden per regel is 10.
- Het maximumaantal gebeurtenissen per regel is 25.
- Regels en handmatig gerangschikte producten worden toegepast op de zoekresultaten wanneer de standaardsorteervolgorde &quot;Sorteren op: meest relevant&quot; is geselecteerd. Als een winkelier de sorteervolgorde verandert in een sorteervolgorde op naam of prijs, zijn de regels en handmatige waarderingen niet meer van kracht.
- Om onvoorspelbare resultaten in gepagineerde reacties te voorkomen, zou het aantal vastgezette producten niet de gevraagde paginagrootte moeten overschrijden.

## Synoniemen

- [!DNL Live Search] kan tot 200 [ synoniemen ](synonyms.md) per archiefmening beheren.

## Categorie verhandelen

- U kunt één regel per categorie maken voor elke winkelweergave.
- Het maximumaantal voorwaarden per regel is 10.
- Het maximumaantal gebeurtenissen per regel is 25.
- Regels worden toegepast wanneer een specifieke categorie op de winkel wordt geopend en er voor die categorie een regel bestaat. Voor de Regels van de Verkoop van de Categorie, is de standaardsoortorde &quot;Soort door: Positie&quot;. Als een winkelier de sorteervolgorde wijzigt, worden alle verborgen, vastgezette en begraven producten niet meer gesorteerd.

## B2B- en categoriemachtigingen

- Producten worden niet weergegeven als deze niet worden toegevoegd aan een standaard gedeelde catalogus.
- Om klantengroepen te beperken die [ categorietoestemmingen ](https://experienceleague.adobe.com/nl/docs/commerce-admin/catalog/categories/category-permissions) gebruiken:
   - De producten moeten aan de wortelcategorie worden toegewezen. (**Nota:** u kunt deze beperking verwijderen door de uitbreiding van de Uitvoer van Gegevens SaaS aan versie 103.4.0+ bij te werken. Zie [ de uitbreiding van de gegevensuitvoer beheren ](../data-export/manage-extension.md).
   - Aan de klantengroep &quot;Niet aangemeld&quot; moeten de machtigingen &quot;Toestaan&quot; worden toegekend.
   - Om producten tot de &quot;niet Gelogde&quot;klantengroep te beperken, ga naar elke categorie en plaats toestemming voor elke [ klantengroep ](https://experienceleague.adobe.com/nl/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage).
- Ondersteuning van de buitenverpakking voor B2B met de PLP-widget op PWA Studio wordt momenteel niet ondersteund. Nochtans, kunt u [ gebruiken API ](install.md#pwa-support) om deze functionaliteit uit te voeren.
- De facetten van de categorie in [!DNL Live Search] zouden categorieën kunnen tonen die niet aan een specifieke [ klantengroep ](https://experienceleague.adobe.com/nl/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage) kunnen tonen.
- [!DNL Live Search] kan maximaal 1.000 klantengroepen ondersteunen.

## [!DNL Storefront popover]

- [[!DNL popover]](storefront-popover.md) is beschikbaar slechts voor opslag die het ** thema Luma, of een aangepast thema gebruiken dat op *Luma* gebaseerd is. De bakkrummen op de pagina van onderzoeksresultaten zullen niet *Luma* stileren.
- [!DNL popover] steunt niet het *Lege* thema.
- [!DNL popover] wordt niet ondersteund op het formulier Snelle volgorde.
- Schijflijsten en productvergelijkingen worden niet ondersteund.
- Het valutasymbool voor de Peruviaanse sol (PEN) wordt niet ondersteund.

## Problemen oplossen

Raadpleeg de volgende artikelen in de knowledgebase voor hulp bij het oplossen van enkele veelvoorkomende problemen in [!DNL Live Search] :

- [[!DNL Live Search]  niet gesynchroniseerde catalogus ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync)
- [[!DNL Live Search]  dashboard en het rangschikken van het onderzoeksresultaat is onjuist ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-dashboard-ranking-incorrect)
- [[!DNL Live Search]  vertoningen uit-van-voorraad producten ongeacht de montages van de voorraadstatus in Admin ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-displays-out-of-stock-products)
- [[!DNL Live Search]  worden de facetten niet alfabetisch gesorteerd ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-facets-not-sorted)

Als u extra hulp nodig hebt, contacteer [ steun ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).
