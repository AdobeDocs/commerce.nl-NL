---
title: '[!DNL Catalog Service] Opmerkingen bij de release'
description: De recentste versieinformatie voor  [!DNL Catalog Service]  voor Adobe Commerce.
feature: Services, Catalog Service, Release Notes
exl-id: 74f2e46a-5592-4857-a6d7-b95b85d8b4cc
source-git-commit: 5dd290a4e10bdbd1f6c96b67ab6c9ba1598705dc
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 0%

---

# [!DNL Catalog Service] Opmerkingen bij de release

In deze releaseopmerkingen worden de meest recente versies van [!DNL Catalog Service] beschreven.
Er wordt ondersteuning geboden voor de belangrijkste uitgebrachte versie. Opmerkingen bij de release voor oudere versies worden ter referentie verschaft.
Updates zijn:

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Nieuwe eigenschappen
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Bevestigingen en verbeteringen
![&#x200B; Bug &#x200B;](../assets/bug.svg) Bekende kwesties

## Huidige hoofdversie

### V1.26 Release

_22 oktober, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) het schema van GraphQL omvat nu het `lastModifiedAt` attribuut in de productinformatie. Deze nauwkeurige tijdstempel helpt klanten ervoor te zorgen dat de sitemaps de meest recente updates aan hun producten nauwkeurig weerspiegelen. Zodoende kunnen zoekprogramma&#39;s zoals Google ook bepalen wanneer opnieuw indexeren nodig is, het crawling-proces optimaliseren en problemen voorkomen die te maken hebben met agressieve datums die het laatst zijn gewijzigd wanneer er geen nauwkeurige informatie beschikbaar is. <!--DATA-6209-->

## Vorige versies

+++ Vorige versies

### V1.23 Release

_Augustus 22, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Repareren &#x200B;](../assets/fix.svg) U kunt productinformatie zonder product met voeten treden (prijzen) gegevens nu terugwinnen. In vorige versies, kwamen deze vragen de volgende fout terug:
`The following sku does not have product override data in the DB: <SKU value>. Make sure data is synced.` <!--DATA-6121-->

### V1.22 Release

_Augustus 13, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde steun om alle varianten door productSKU terug te winnen. Zie de [&#x200B; Verwijzing van de Dienst API van de Catalogus &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/). <!--DATA-6067-->

### V1.22 Release

_Augustus 13, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde steun om alle varianten door productSKU terug te winnen. Zie de [&#x200B; Verwijzing van de Dienst API van de Catalogus &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/). <!--DATA-6067-->

### V1.19 Release

_Mei 23, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer


![&#x200B; Repareren &#x200B;](../assets/fix.svg) <!--DATA-5033--> De `InStock` vlag voor optiewaarden neemt nu rekening met het scoped `enabled` status van de productvariant.

![&#x200B; Repareren &#x200B;](../assets/fix.svg) <!--DATA-5888--> voegt steun voor productprijzen toe die grote aantallen (tot 16 cijfers) en grotere decimale precisie (tot 4 decimalen) vereisen. Om de updates van de prijsconfiguratie op uw bestaande catalogus toe te passen, hersynchroniseer catalogusgegevens van het [&#x200B; dashboard van het Beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/data-dashboard), of door het [&#x200B; bevel-lijn van Adobe Commerce interface &#x200B;](../landing/catalog-sync.md#command-line-interface) te gebruiken.

#### Bekende beperkingen

De volgende functies worden nog niet ondersteund:

* De maximumgrootte voor dynamische kenmerklading is 9 MB.
* De productprijs van de groep kan worden berekend aan de hand van eenvoudige productprijzen.
* In een afbeeldingsarray bevat alleen de eerste afbeelding rollen.

Los de volgende beperkingen op met behulp van API Mesh en de Core GraphQL API:

* Minimale geadverteerde prijs
* Tier-prijsstelling
* Bundel van producten tegen vaste prijzen

Voor details en voorbeelden, zie [&#x200B; de Dienst van de Catalogus en API Net &#x200B;](mesh.md)

### V1.18 Release

_11 april 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde steun voor PHP 8.3.

![&#x200B; Nieuw &#x200B;](../assets/new.svg) de [`products` &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) en [`refineProduct` &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/refine-product/) vragen keren nu klantgerichte optiesgegevens voor zowel eenvoudige als complexe producten terug.<!--DATA-5538-->

### V1.17 Release

_22 Februari, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) [[!DNL Data Management Dashboard] &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html?lang=nl-NL) is nu beschikbaar. Dit vernieuwde dashboard biedt inzichten in gegevensstromen voor [!DNL Product Recommendations] , [!DNL Live Search] en [!DNL Catalog Service] . Ondersteuning voor deze functie is geïntroduceerd in v3.1.0 van het `catalog-service` -pakket.

### V1.16 Release

_13 Februari, 2024_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; de Nieuwe &#x200B;](../assets/new.svg) video&#39;s van het Product worden nu gesteund door de Dienst API van de Catalogus.
![&#x200B; de uit-van-voorraad opties van 0&rbrace; herstellen &lbrace;worden nu getoond in PDP widget.](../assets/fix.svg)

#### Bekende beperkingen

Deze functies worden nog niet ondersteund:

* De maximumgrootte voor dynamische kenmerklading is 9 MB.
* Productprijs per groep. Deze waarde kan worden berekend aan de hand van eenvoudige productprijzen.
* In een afbeeldingsarray bevat alleen de eerste afbeelding rollen.

De volgende beperkingen kunnen worden opgelost door gebruik te maken van API Mesh en de Core GraphQL API:

* Minimale geadverteerde prijs
* [Tier-prijsstelling](mesh.md)

### V1.13 Release

_12 oktober 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Dienst van de Catalogus steunt de `inStock` vlag voor productvarianten.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) de `urlKey` en `externalId` gebieden zijn toegevoegd aan het schema van GraphQL.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Downloadbare producten en geschenkkaarten worden nu gesteund.

### V1.12 Release

_19 september, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Dienst van de Catalogus gebruikt nu [&#x200B; Prijs het indexeren SaaS &#x200B;](../price-index/price-indexing.md).
![&#x200B; Repareren &#x200B;](../assets/fix.svg) Deze versie bevat insectenmoeilijke situaties en verbeteringen op de de dienstkant.

### V1.11 Release

_18 juli 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Dienst van de Catalogus steunt nu de [`recommendations` &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/recommendations/) vraag van GraphQL voor de Aanbevelingen van het Product.

### V1.10 Release

_Juni 27, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) De dienst API van de Catalogus steunt nu `related products`.

### V1.7-release

_12 april 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Dienst van de Catalogus ontruimt nu geschrapte productvarianten.
![&#x200B; verbeter &#x200B;](../assets/fix.svg) scalability van de Infrastructuur en prestatiesverbeteringen.

### V1.6-release

_Maart 28, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde stalen aan de [`products` &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) vraag.
![&#x200B; Nieuw &#x200B;](../assets/new.svg) voegde de capaciteit toe om `entityId` te krijgen gebruikend [&#x200B; API Net &#x200B;](mesh.md).

### V1.5-release

_Maart 6, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde [`categories` &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) functionaliteit van GraphQL.
![&#x200B; verbeter &#x200B;](../assets/fix.svg) Verbeterde prestaties en API scalability.

### V1.4 Release

_7 Februari, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Gepubliceerde catalogus-dienst metapakket om installatiestappen te vereenvoudigen.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) API scalability en prestatiesverbeteringen.

### V1.3 Release

_Januari 17, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) Vereenvoudigde en verbeterde de onboarding ervaring.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) de nieuwe eindpunten van de klantenzandbak zijn beschikbaar voor preproductie het testen.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Steun die voor virtuele producten wordt toegevoegd.
![&#x200B; bevestig &#x200B;](../assets/fix.svg) API scalability en prestatiesverbeteringen.

### V1.1-release

_18 November, 2022_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Dienst van de Catalogus steunt nu Adobe [&#x200B; API Net &#x200B;](https://developer.adobe.com/graphql-mesh-gateway/).
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Verbeterde API scalability en algemene prestaties.

### V1.0-release

_4 Oktober, 2022_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) steun nu gebundelde en gegroepeerde producten.
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Toegevoegde B2B zichtoverschrijvingen. De producten zijn nu doorzoekbaar en kunnen aan de kar voor specifieke klantengroepen worden toegevoegd.
![&#x200B; de Dienst van 0&rbrace; Repareren &lbrace;is nu stabieler en heeft betere prestaties.](../assets/fix.svg)

### 0.3 Release - Beta+

_12 September, 2022_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Beelden voor variantsteun: de productbeelden zijn teruggekeerd gebaseerd op de geselecteerde opties
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Rollen voor prijssteun: sta slechts leden van specifieke klantengroepen toe om de prijs van producten te zien
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Verbeterde stabiliteit en prestaties van de dienst
![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Updates worden ontvangen wanneer de producten van de catalogus worden geschrapt

### Beta Release

_9 augustus, 2022_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![&#x200B; Nieuw &#x200B;](../assets/new.svg) de vragen `products` en `refineProduct` keren de volgende gegevens terug:

* Vooraf gedefinieerde (systeem)productkenmerken.
* Dynamische productkenmerken en filter deze op rol (pagina met productweergave/productlijst).
* Productopties.
* Productafbeeldingen en filteren op rol (PDP/PLP).
* Een specifieke prijs voor eenvoudige producten en prijsbereiken voor configureerbare producten.
* Prijzen en prijsbereiken van de klantengroep. Ze retourneren een fallback-standaardprijs voor kopers zonder een klantengroep.
* Producttypen die gebruikmaken van klantspecifieke B2B-prijzen.
