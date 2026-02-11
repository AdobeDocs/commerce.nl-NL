---
title: Grenzen en grenzen
description: Leer over de grenzen en de grenzen voor  [!DNL Product Recommendations]  om ervoor te zorgen het aan de behoeften van uw zaken voldoet.
role: Admin, Developer
source-git-commit: 66830c9d950a27269aca1bda0dcc7d0d86f05647
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 0%

---

# Grenzen en grenzen

Controleer de volgende grenzen en grenzen om ervoor te zorgen dat [!DNL Product Recommendations] aan de behoeften van uw zaken voldoet. Het begrip van deze beperkingen helpt u implementatie plannen, filters vormen, en gemeenschappelijke kwesties vermijden.

## Algemeen

- **de types van Product** - de gesteunde producttypes omvatten _eenvoudig_, _configureerbaar_, _virtueel_, _downloadbaar_, en _geschenkkaart_. _Bundel_, _gegroepeerde_, en de types van douaneproduct worden niet gesteund. Als uw catalogus een groot aantal niet gestaafde producttypes bevat, kunt u een lage [&#x200B; bereidheid score &#x200B;](create.md#readiness-indicators) verwachten. Zie [&#x200B; Filter door producttype &#x200B;](filters.md#type).
- **SKUs met ruimten** - SKUs die ruimten bevatten kan aanbevelingsrelevantie verminderen en zou moeten worden vermeden wanneer mogelijk.
- **pagina van het Kart** - de Aanbevelingen van het Product worden niet gesteund op de pagina van het Kart wanneer uw opslag wordt gevormd om de het winkelwagentpagina onmiddellijk na het toevoegen van een product aan de kar [&#x200B; te tonen. &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration) Zie [&#x200B; aanbevelingen &#x200B;](create.md) creëren.
- **de producten van het Kind** - de producten van het Kind van een configureerbaar product (zicht _individueel niet zichtbaar_) worden niet getoond in een aanbeveling eenheid. Alleen het configureerbare (bovenliggende) product kan worden weergegeven. Zie [&#x200B; producten van de Filter &#x200B;](filters.md#product).
- **Gehandicapte of onzichtbare producten** - de Producten die of niet individueel zichtbaar zijn kunnen nooit in aanbevelingen verschijnen en kunnen niet in productfilters worden geselecteerd.
- **Speciale tarifering** - [&#x200B; Speciale prijzen &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) met begin en einddata worden niet gesteund in aanbeveling eenheden. Een product met een speciale prijs kan in aanbevelingen verschijnen, maar de eenheid toont niet de speciale prijs, de begindatum, of de einddatum. Kopers zien de normale prijs (of andere prijsgegevens die door uw catalogus/prijsfeed worden verstrekt) totdat ze de productpagina openen.

## Aanbevelingseenheden

- **Actieve eenheden per paginatype** - u kunt tot 50 actieve aanbevelingseenheden voor elk paginatype (Huis, Categorie, het Detail van het Product, Kar, Bevestiging) tot stand brengen. Het paginatype wordt grijs weergegeven in de aanmaakflow wanneer de limiet is bereikt.
- **Producten per eenheid** - het aantal producten die in een aanbevelingseenheid worden getoond kan van 5 (gebrek) aan een maximum van 20 worden geplaatst.
- **staat van het Ontwerp** - na het bewaren van een aanbeveling als ontwerp, kunt u niet het paginatype of aanbevelingen type voor die eenheid wijzigen. Andere instellingen kunnen worden bewerkt voordat ze worden geactiveerd.

## Filters en voorwaarden

- **Dynamische voorwaarden** - de Dynamische voorwaarden (zoals &quot;producten in de zelfde categorie zoals huidig product&quot;of &quot;relatieve prijswaaier&quot;) zijn beschikbaar op elk paginatype behalve de Homepage. Ze zijn ook niet beschikbaar op pagina&#39;s waar aanbevelingen worden geplaatst bij de Page Builder. Zie [&#x200B; Voorwaarden &#x200B;](filters.md#conditions).

## Voorbeeld- en niet-productieomgevingen

- **onlangs bekeken voorproef** - het _onlangs bekeken_ aanbevelingstype kan niet in Admin worden voorvertoond omdat het gegeven op browser geschiedenis is gebaseerd en niet beschikbaar in de context Admin. is Zie [&#x200B; aanbevelingen van de Voorproef &#x200B;](create.md#preview).
- **Aanbevelingen van een andere gegevensruimte** - wanneer u [&#x200B; aanbevelingen van een verschillende SaaS- gegevensruimte &#x200B;](settings.md) (bijvoorbeeld, productie) in een niet-productieopslag haalt, kunt u de aanbevelingen bekijken maar niet door aan productpagina&#39;s van hen klikken. Dit is door ontwerp voor voorproef en het testen.
- **GraphQL en afwisselende gegevensruimte** - wanneer het gebruiken van de Aanbevelingen van het Product via [&#x200B; GraphQL &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/), is de `alternateEnvironmentId` parameter (die wordt gebruikt om aanbevelingen van een andere gegevensruimte te halen) niet beschikbaar. Gebruik REST API of de Montages Admin om de raadsbron in niet productie te schakelen.

## API en configuratie

- **API sleutels (4.x en hoger)** - u moet openbare en privé API sleutels voor zowel zandbak als productiemilieu&#39;s verstrekken. Als u geen van beide API-sleutels biedt, hebt u geen toegang tot de functie Productaanbevelingen in Admin. De inzameling van gegevens op uw winkel en bestaande aanbevelingen blijven werken. Zie [&#x200B; installeren en vormen &#x200B;](install-configure.md).

## Cookie-beperkingen

- Wanneer [&#x200B; de wijze van de koekjesbeperking &#x200B;](setting-cookie.md) wordt toegelaten en de kopers geen koekjes hebben aanvaard, kunnen bepaalde aanbevelingen die zich op gedragsgegevens baseren niet tonen of kunnen beperkte resultaten tonen.
- De types van aanbeveling die zich niet op gedragsgegevens (bijvoorbeeld, _het meest bekeken_, _Visuele gelijkenis_) baseren blijven werken wanneer de koekjesbeperkingen worden toegelaten.
- Als cookie-beperkingen zijn ingeschakeld, worden gedragsgegevens pas verzameld of opgeslagen in cookies of lokale opslag nadat de winkel hiermee heeft ingestemd.

## Page Builder

- **Metriek en opslagmeningen** - de Metriek voor de aanbevelingen van de Bouwer van de Pagina verschijnt slechts op de standaardarchiefmening in de werkruimte van de Aanbevelingen van het Product. Om de aanbevelingsmetriek van de Bouwer van de Pagina op een niet-standaard opslagmening te zien, moet u [&#x200B; &#x200B;](edit.md) de de aanbevelingseenheid van de Bouwer van de Pagina in die opslagmening openen en uitgeven en het bewaren; de metriek verschijnt dan voor die opslagmening. Zie [&#x200B; integratie van de Bouwer van de Pagina &#x200B;](page-builder.md).

## B2B

- De Aanbevelingen van het product vereert [&#x200B; categorietoestemmingen &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/category-permissions.html), [&#x200B; gedeelde catalogi &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html), en klant groep-specifieke tarifering. Winkelaars zien alleen aanbevelingen voor producten waartoe ze toegang hebben op basis van hun segment- en catalogustoewijzing. Zie [&#x200B; on boarding &#x200B;](onboarding.md).

## Gegevens en gereedheid

- **gedragsgegevens** - Vele aanbevelingstypes vereisen voldoende gegevens van het storefrontgedrag (meningen, toe:voegen-aan-kart, aankopen). Nieuwe opslagplaatsen of winkels met weinig verkeer zien mogelijk beperkte of geen resultaten voor die types tot de adequate gegevens worden verzameld. De indicatoren van de toezicht [&#x200B; bereidheid &#x200B;](create.md#readiness-indicators) in Admin.
- **het Opvoeren zonder productiegegevens** - in een niet productiemilieu zonder gedragsgegevens, het enige aanbevelingstype u kunt testen zonder productie te halen is _meer als dit_, die op catalogus-gebaseerde gelijkenis slechts gebruikt. Zie [&#x200B; het Opvoeren milieu &#x200B;](staging-environment.md).

## Problemen oplossen

Voor hulp met catalogussynchronisatie, aanbevelingen die, of andere gemeenschappelijke kwesties niet tonen, onderzoek de [&#x200B; Kennisbank van Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview) of contacteer [&#x200B; steun &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide).
