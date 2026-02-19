---
title: '[!DNL Commerce Storefront Catalog Service Release Notes]'
description: De recentste versieinformatie voor  [!DNL Catalog Service]  voor Adobe Commerce.
feature: Services, Catalog Service, Release Notes
exl-id: 74f2e46a-5592-4857-a6d7-b95b85d8b4cc
source-git-commit: 7b05da07d185c5495642037c6ef3b7ff5fcaa8e6
workflow-type: tm+mt
source-wordcount: '2193'
ht-degree: 0%

---

# [!DNL Commerce Storefront Catalog Service] Opmerkingen bij de release

Deze releaseopmerkingen hebben betrekking op de meest recente updates van de Commerce Catalog Service, waaronder:

- {de versies van de Catalogusdienst van de 0} Storefront ****

   - API-schemaverbeteringen voor catalogusservice voor verbeterde gegevensophaling.
   - Verbeteringen op het gebied van beveiliging, prestaties en betrouwbaarheid voor de API voor catalogusservice en de onderliggende infrastructuur.

- **de metapakketversies van de Dienst van de Catalogus**

   - Bijgewerkte afhankelijkheden voor betere prestaties, stabiliteit en compatibiliteit met andere Adobe Commerce-componenten.

Updates worden gecategoriseerd op type:

![ Nieuwe ](../assets/new.svg) Nieuwe eigenschappen
![ bevestig ](../assets/fix.svg) Bevestigingen en verbeteringen
![ Bug ](../assets/bug.svg) Bekende kwesties

De nieuwste versie wordt ondersteund. Opmerkingen bij de release voor oudere versies worden ter referentie opgenomen.

## Catalogusservice Storefront

### release v1.47

_12 Februari, 2025_

![ Nieuw ](../assets/new.svg) de API dienst steunt nu het `CategoryProductView` type, toelatend verbeterde meningen en vragen voor producten door categorie. Deze update stelt ontwikkelaars in staat productgegevens op efficiënte wijze op te halen en te filteren op basis van categorie, waardoor ze flexibeler en beter presteren bij gebruik in categorieën. Voor details, zie [ categorieën van de Implementatie op de storefront ](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/categories-storefront-implementation/). Slechts gesteund op de implementaties die van Commerce het [ composable model van catalogusgegevens ](https://developer.adobe.com/commerce/services/optimizer/) gebruiken voor headless storefronts <!--DATA-6949-->

### release v1.46

_December 11, 2025_

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om prestaties en stabiliteit te verbeteren. <!--DATA-6852, DATA-6864-->

### release v1.45

_17 november 2025_

![ Nieuwe ](../assets/new.svg) **het Filtreren van Attributen door Naam** - de `productSearch` vraag van GraphQL steunt nu het filtreren productattributen met het `names` gebied. <!--DATA-6831--> Met dit filter kunt u:

- De lading van de reactielading verminderen door slechts specifieke attributen te verzoeken
- Combineer met het bestaande filter `roles` om te beperken door zichtbaarheidsrol en kenmerknaam
- Voorbeelden:

  **filter door attributennamen slechts**

  ```graphql
  query {
    products(skus: ["SKU-001"]) {
      attributes(names: ["color", "size", "material"]) {
        name
        label
        value
      }
    }
  }
  ```

  **Filter door zowel rollen als namen:**

  ```graphql
  query {
    products(skus: ["SKU-001"]) {
      attributes(roles: ["visible in PDP"], names: ["eco_collection", "new"]) {
        name
        label
        value
        roles
      }
    }
  }
  ```

>[!NOTE]
>
>Als u alle kenmerken wilt ophalen zonder te filteren, laat u het argument `names` weg of geeft u een lege array op.

### release v1.44

_6 November, 2025_

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om prestaties en stabiliteit te verbeteren. <!--DATA-6852, DATA-6864-->

### v1.43-release

_3 November, 2025_

![ Nieuwe ](../assets/new.svg) **Lagen van het Product voor multi-dimensionale product aanpassing** - Toegevoegde steun voor kanaal-specifieke, locale-bewuste inhoudslevering voor de implementaties van Adobe Commerce Optimizer.<!--DATA-6632-->

- Verschillende productinhoud naar verschillende klantensegmenten verzenden
- Landspecifieke aanpassingen toepassen zonder basisgegevens te dupliceren
- Velden overschrijven met laagmaskers beheren
- Ondersteuning voor hoogwaardige, seizoensgebonden en voor mobiele apparaten geoptimaliseerde inhoudlagen

  Lagen worden opgehaald met de bestaande `products` -query, worden op de server toegepast vanuit aanvraagheaders en vereisen geen wijzigingen in het schema. Zie [ de laag van de Catalogus ](https://experienceleague.adobe.com/en/docs/commerce/optimizer/setup/catalog-layer) in de _Gids van Adobe Commerce Optimizer_.

![ Gegroepeerde producten van 0} herstellen {kunnen nu worden gevraagd wanneer de ouder geen tarifering heeft; de kindproducten keren hun eigen zichtbaarheidsrollen terug.](../assets/fix.svg)<!--DATA-6779-->

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om prestaties en stabiliteit te verbeteren. <!--DATA-6721, DATA-6864-->

### release v1.42

_September 8, 2025_

![ Nieuwe ](../assets/new.svg) **Toegevoegde steun van de Prijsstelling van de Rij** aan vraagvolume het tarief:<!--DATA-6643-->

Laagprijs ophalen:

1. Gebruik `products` vraag met uw gewenste SKUs
2. Voor **SimpleProductView**, toegang `price.tiers`
3. Voor **ComplexProductView**, toegang `priceRange.minimum.tiers` en `priceRange.maximum.tiers`
4. Elke laag bevat de verlaagde `tier` prijs en `quantity` voorwaarden
5. Drempelwaarden voor hoeveelheden definiëren met `gte` (groter dan of gelijk aan) en `lt` (kleiner dan)

**Voorbeeld:**

```graphql
query {
  products(skus: ["SKU-001"]) {
    ... on SimpleProductView {
      price {
        regular { amount { value currency } }
        tiers {
          tier { amount { value currency } }
          quantity {
            ... on ProductViewTierRangeCondition { gte lt }
          }
        }
      }
    }
  }
}
```

![ Repareren ](../assets/fix.svg) **prijzen van de Rij die door minimumdefinitieve prijs** worden gefilterd <!--DATA-6643-->

API keert nu slechts rijen terug de waarvan verdisconteerde prijs **lager is dan** de minimumdefinitieve prijs van het product. Hogere niveaus worden weggelaten omdat de minimumeindprijs in plaats daarvan op de winkelruimte van toepassing zou zijn.

Van toepassing op:

- **Eenvoudige producten**: `price.tiers` omvat slechts rijen met `tier.amount.value` &lt; `price.final.amount.value` (minimum definitief).
- **Complexe producten**: `priceRange.minimum.tiers` en `priceRange.maximum.tiers` gebruiken de zelfde regel wanneer het bouwen van de prijswaaier.

### v1.41-release

_2 September, 2025_

![ Repareren ](../assets/fix.svg) **Verbeterde fout behandeling voor ontbrekende prijsinformatie** - wanneer de prijsgegevens nog niet worden ontvangen, keert API `null` voor het prijsgebied in plaats van het werpen van een fout terug, toestaand cliënten om ontbrekende gegevens netjes te behandelen.<!--DATA-6612-->

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om prestaties en stabiliteit te verbeteren.<!--DATA-6671-->

### release v1.40

_30 Juli, 2025_

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om veiligheid, prestaties, en stabiliteit te verbeteren.<!--DATA-6619-->

### release v1.39

_24 Juli, 2025_

![ Nieuw ](../assets/new.svg) **wint aanbevelingen eenheden door eenheididentiteitskaart** - Nieuw eindpunt van GraphQL `recommendationsByUnitIds` terug adviseringseenheden door hun unieke identiteitskaart voor flexibelere, gerichte toegang.

- `unitIds` is vereist (lijst met op te halen recIds).
- Contextparameters (`currentSku`, `cartSkus`, `userViewHistory`, `userPurchaseHistory`, `category`) gedragen zich op dezelfde manier als in de bestaande query voor aanbevelingen.

- **Voorbeeld**

  ```graphql
  query {
    recommendationsByUnitIds(
      unitIds: ["11ee89d1-bfae-4582-a921-2ced44ff6bf7"]
      currentSku: "24-MB01"
      cartSkus: ["24-MB01"]
    ) {
      totalResults
      results {
        unitId
        unitName
        totalProducts
        productsView {
          sku
        }
        pageType
        typeId
        storefrontLabel
        displayOrder
      }
    }
  }
  ```

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om veiligheid, prestaties, en stabiliteit te verbeteren.<!--DATA-6316-->

### release v1.38

_15 juli 2025_

![ Nieuwe ](../assets/new.svg) **de types van het kaartproduct van de Gift** - de Dienst van de Catalogus Storefront steunt nu productattributen als voorwerpen JSON of series, toelatend flexibel beheer van complexe types zoals giftekaarten.<!--DATA-6573-->


### release v1.37

_Juni 20, 2025_

![ Nieuwe ](../assets/new.svg) **Hiërarchische configuratie van het prijzenboek** - nauwkeurige prijswaaiers voor ouder-kind prijzenboeken. De berekeningen respecteren hiërarchie en geërfte regels; vermindert prijsfouten wanneer de veelvoudige prijsboeken met elkaar verbonden zijn. Alleen Adobe Commerce Optimizer. Zie [ de Boeken van de Prijs ](https://experienceleague.adobe.com/en/docs/commerce/optimizer/setup/pricebooks).

![ Nieuwe ](../assets/new.svg) **case-insensitive sleutels** - de zeer belangrijke raadplegingen in vragen zijn nu case-insensitive, verminderend fouten van zeer belangrijke casing. <!--DATA-6494, DCAT-2495-->

### v1.36-release

_Juni 20, 2025_

![ Nieuwe ](../assets/new.svg) **Openbare IO Gebeurtenissen voor de Storefront van de Catalogus** - toegevoegde openbare IO gebeurtenissen voor integratie en observability in real time (CSS en EDS).<!--DATA-6329-->

![ Nieuwe ](../assets/new.svg) **Server-zij het Teruggeven (SSR)** - de Verbeteringen van de Architectuur om SSR voor betere prestaties, SEO, en UX op grote catalogi te steunen.<!--DATA-6278, DATA-6280-->

![ Nieuwe ](../assets/new.svg) **Infrastructuur &amp; Veiligheid** - Nieuwe rollen van AWS, integratie ServiceNow, en pijpleidingen CI/CD voor de gebeurtenisdienst.

![ Nieuwe ](../assets/new.svg) **formaten van de Gebeurtenis &amp; waarneming** - Gestroomlijnde ladingen, verbeterde controle, betere variantgebeurtenisgegevens.<!--DATA-6332, DATA-6402, -->

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om veiligheid, prestaties, en stabiliteit te verbeteren.<!--DATA-6404, DATA-6410, -->

+++ Vorige versies

## v1.35-release

_13 Juni, 2025_

![ Nieuw ](../assets/new.svg) **wint uncached gegevens** - laat de `Magento-Is-Preview` kopbal toe om uncached gegevens van het cataloguseindpunt tot de Dienst van het Onderzoek over te gaan.<!--DATA-6345-->

![ Nieuw ](../assets/new.svg) **Multi-select productopties** - GraphQL API stelt nu bloot of de productopties veelvoudige selecties toestaan (bijvoorbeeld, bundel &quot;kies veelvoudige punten&quot;).<!--DATA-6487-->

![ Nieuwe ](../assets/new.svg) bijgewerkte prijsbevestiging op gegevensinvoer om producten zonder prijzen te steunen.<!--DATA-6098-->

![ Verbeterde fout behandeling voor eenvoudige bundelprijs in Adobe Commerce Optimizer ](../assets/fix.svg) herstellen.<!--DATA-6541-->

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om veiligheid, prestaties, en stabiliteit te verbeteren.<!--DATA-6273, DATA-6485, -->

## v1.34-release

_Maart 23, 2025_

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om veiligheid, prestaties, en stabiliteit te verbeteren.<!--DATA-5732-->

## v1.33-release

_29 April, 2025_

![ verbeter ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen. De infrastructuur steunt nu uiterst grote catalogi (tot ~440 miljoen SKUs) zonder bestaande werklasten te beïnvloeden.

### v1.32-release

_Maart 28, 2025_

![ Attributen van het 0} Repareren {zonder rollen worden niet meer geïndexeerd door gebrek voor de composable catalogus, verbeterend indexerende tijd en verminderend opslag. ](../assets/fix.svg) Verouderd gedrag kan opnieuw worden ingeschakeld via een functiemarkering.

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om veiligheid, prestaties, en stabiliteit te verbeteren. <!--DATA-6348, DATA-6440, DATA-6446, DATA-6641-->

### v1.31-release

_18 Februari, 2025_

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om veiligheid, prestaties, en stabiliteit te verbeteren.<!--DATA-6389, DATA-6367, DATA-6373-->

### release v1.30

_9 December, 2024_

Belangrijke versie: [ composable model van catalogusgegevens ](https://developer.adobe.com/commerce/services/optimizer/) voor hoofdloze storefronts, kopbalbeheer, en de behandeling van productgegevens.

![ Nieuw ](../assets/new.svg) **Composable Model van Gegevens van de Catalogus (CCDM)** - steunt klanten die de composable catalogus voor hoofdloze storefronts gebruiken. Nieuwe eindpunten accepteren Catalogusweergave en Beleid-id&#39;s (compatibel met oudere versies). Configureerbare productdetails en prijzen met ingebouwde paginering.<!--DATA-6018, DATA-6288-->

![ Nieuw ](../assets/new.svg) **Beheer van de Kopbal** - `AC-Locale` anders genoemd aan `AC-Scope-Locale` voor composable catalogus API verrichtingen; koptekstafbeelding en gespecificeerde standaardwaarden.<!--DATA-6303, DATA-6078-->

![ Nieuwe ](../assets/new.svg) **Gegevens van het Product &amp; het Tarief** - Steun voor composable model van catalogusgegevens en betere prijsbehandeling voor configureerbare producten.<!--DATA-6279-->

`CurrencyEnum` bijgewerkt om `NONE` voor productzoekopdrachten te ondersteunen, uitgelijnd op federatielogica. <!--DATA-6285-->

![ herstellen ](../assets/fix.svg) de Infrastructuur &amp; verbeteringen **- systeem-vlakke verbeteringen voor veiligheid, prestaties, en stabiliteit.**

![ de productopties van de Bundel van 0} herstellen {tonen nu slechts toegelaten producten.](../assets/fix.svg)<!--DATA-6347-->

### release v1.29

_9 December, 2024_

![ Nieuw ](../assets/new.svg) **Beeld die in productvragen** opdracht geven - de beelden van het Product in het gebied van GraphQL `images` volgen nu catalogusuitvoer `sortOrder` voor verenigbaar opslag en API gedrag.<!--DATA-6258-->

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om veiligheid, prestaties, en stabiliteit te verbeteren.<!--DATA-6619-->

### release v1.28

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om veiligheid, prestaties, en stabiliteit te verbeteren.<!--DATA-6180, DATA-6230, DATA-6254, DATA-6257-->

### release v1.27

_September 26, 2024_

![ bevestig ](../assets/fix.svg) systeem-niveau en infrastructuurverbeteringen om veiligheid, prestaties, en stabiliteit te verbeteren.<!--DATA-6243-->

### v1.26-release

_22 oktober, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) schema van GraphQL omvat nu `lastModifiedAt` in productinformatie voor nauwkeurige sitemaps en onderzoek-motor het opnieuw indexeren (b.v., Google). <!--DATA-6209-->

### v1.23-release

_Augustus 22, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ de informatie van het 1} Product van de Reparatie ](../assets/fix.svg) kan nu zonder product met voeten treden (prijzen) gegevens worden teruggewonnen. Eerder werden deze query&#39;s geretourneerd: `The following sku does not have product override data in the DB: <SKU value>. Make sure data is synced.` <!--DATA-6121-->

### v1.22-release

_Augustus 13, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Toegevoegde steun om alle varianten door productSKU terug te winnen. Zie de [ Verwijzing van de Dienst API van de Catalogus ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/). <!--DATA-6067-->

### release v1.19

_Mei 23, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer


![ bevestig ](../assets/fix.svg) <!--DATA-5033--> de `InStock` vlag voor optiewaarden respecteert nu het scoped `enabled` status van de productvariant.

![ Bevestig ](../assets/fix.svg) toegevoegde steun voor productprijzen met maximaal 16 cijfers en 4 decimalen. <!--DATA-5888--> Hersynchroniseer van het [ dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard) of [ CLI ](../landing/catalog-sync.md#command-line-interface) om updates toe te passen.

#### Bekende beperkingen

De volgende functies worden nog niet ondersteund:

- De maximumgrootte voor dynamische kenmerklading is 9 MB.
- De productprijs van de groep kan worden berekend aan de hand van eenvoudige productprijzen.
- In een afbeeldingsarray bevat alleen de eerste afbeelding rollen.

Gebruik API Mesh en de Core GraphQL API voor:

- Minimale geadverteerde prijs
- Tier-prijsstelling
- Bundel van producten tegen vaste prijzen

Voor details en voorbeelden, zie [ de Dienst van de Catalogus en het Netwerk van API ](mesh.md).

### release v1.18

_11 april 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Toegevoegde steun voor PHP 8.3.

![ Nieuw ](../assets/new.svg) de [`products` ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) en [`refineProduct` ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/refine-product/) vragen keren nu klantgerichte optiesgegevens voor zowel eenvoudige als complexe producten terug.<!--DATA-5538-->

### release v1.17

_22 Februari, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) [[!DNL Data Management Dashboard] ](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard.html) is nu beschikbaar voor gegevensstromen (de Aanbevelingen van het Product, Levend Onderzoek, de Dienst van de Catalogus). Vereist `catalog-service` metapack v3.1.0+.

### v1.16-release

_13 Februari, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ de Nieuwe ](../assets/new.svg) video&#39;s van het Product worden nu gesteund door de Dienst API van de Catalogus.
![ de uit-van-voorraad opties van 0} herstellen {worden nu getoond in PDP widget.](../assets/fix.svg)

#### Bekende beperkingen

Deze functies worden nog niet ondersteund:

- De maximumgrootte voor dynamische kenmerklading is 9 MB.
- Productprijs per groep. Deze waarde kan worden berekend aan de hand van eenvoudige productprijzen.
- In een afbeeldingsarray bevat alleen de eerste afbeelding rollen.

Gebruik API Mesh en de Core GraphQL API voor:

- Minimale geadverteerde prijs
- [Tier-prijsstelling](mesh.md)

### v1.13-release

_12 oktober 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Dienst van de Catalogus steunt de `inStock` vlag voor productvarianten.
![ Nieuw ](../assets/new.svg) de `urlKey` en `externalId` gebieden zijn toegevoegd aan het schema van GraphQL.
![ Nieuwe ](../assets/new.svg) Downloadbare producten en geschenkkaarten worden nu gesteund.

### v1.12-release

_19 september, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Dienst van de Catalogus gebruikt nu [ Prijs het indexeren SaaS ](../price-index/price-indexing.md).
![ Repareren ](../assets/fix.svg) Deze versie bevat insectenmoeilijke situaties en verbeteringen op de de dienstkant.

### v1.11-release

_18 juli 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Dienst van de Catalogus steunt nu de [`recommendations` ](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) vraag van GraphQL voor de Aanbevelingen van het Product.

### release v1.10

_Juni 27, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) De dienst API van de Catalogus steunt nu `related products`.

### release v1.7

_12 april 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Dienst van de Catalogus ontruimt nu geschrapte productvarianten.
![ verbeter ](../assets/fix.svg) scalability van de Infrastructuur en prestatiesverbeteringen.

### v1.6-release

_Maart 28, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Toegevoegde stalen aan de [`products` ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) vraag.
![ Nieuw ](../assets/new.svg) voegde de capaciteit toe om `entityId` te krijgen gebruikend [ API Net ](mesh.md).

### v1.5-release

_Maart 6, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Toegevoegde [`categories` ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) functionaliteit van GraphQL.
![ verbeter ](../assets/fix.svg) Verbeterde prestaties en API scalability.

### release v1.4

_7 Februari, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![ Nieuwe ](../assets/new.svg) Gepubliceerde catalogus-dienst metapakket om installatiestappen te vereenvoudigen.
![ bevestig ](../assets/fix.svg) API scalability en prestatiesverbeteringen.

### v1.3-release

_Januari 17, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![ Nieuw ](../assets/new.svg) Vereenvoudigde en verbeterde de onboarding ervaring.
![ Nieuwe ](../assets/new.svg) de nieuwe eindpunten van de klantenzandbak zijn beschikbaar voor preproductie het testen.
![ Nieuwe ](../assets/new.svg) Steun die voor virtuele producten wordt toegevoegd.
![ bevestig ](../assets/fix.svg) API scalability en prestatiesverbeteringen.

### v1.1-release

_18 November, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![ Nieuwe ](../assets/new.svg) Dienst van de Catalogus steunt nu Adobe [ API Net ](https://developer.adobe.com/graphql-mesh-gateway/).
![ bevestig ](../assets/fix.svg) Verbeterde API scalability en algemene prestaties.

### v1.0-release

_4 Oktober, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![ Nieuwe ](../assets/new.svg) Steun voor gebundelde en gegroepeerde producten.
![ Nieuwe ](../assets/new.svg) Toegevoegde B2B zichtoverschrijvingen. De producten zijn nu doorzoekbaar en kunnen aan de kar voor specifieke klantengroepen worden toegevoegd.
![ de Dienst van 0} Repareren {is nu stabieler en heeft betere prestaties.](../assets/fix.svg)

### 0.3-release - Beta+

_12 September, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![ Nieuwe ](../assets/new.svg) Veranderlijke beelden: teruggekeerde productbeelden gebaseerd op geselecteerde opties.
![ Nieuwe ](../assets/new.svg) de rollen van de Prijs: slechts leden van specifieke klantengroepen kunnen productprijzen zien.
![ bevestig ](../assets/fix.svg) Verbeterde stabiliteit en prestaties van de dienst.
![ Nieuwe ](../assets/new.svg) Updates worden ontvangen wanneer de producten van de catalogus worden geschrapt.

### Beta Release

_9 augustus, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.x en nieuwer

![ Nieuw ](../assets/new.svg) de vragen `products` en `refineProduct` keren de volgende gegevens terug:

- Vooraf gedefinieerde (systeem)productkenmerken.
- Dynamische productkenmerken en filter deze op rol (pagina met productweergave/productlijst).
- Productopties.
- Productafbeeldingen en filteren op rol (PDP/PLP).
- Een specifieke prijs voor eenvoudige producten en prijsbereiken voor configureerbare producten.
- Prijzen en prijsbereiken van de klantengroep. Ze retourneren een fallback-standaardprijs voor kopers zonder een klantengroep.
- Producttypen die gebruikmaken van klantspecifieke B2B-prijzen.

+++

## Metapakket Catalog Service

Updates aan het PHP metapakket van de Dienst van de Catalogus (`magento/catalog-service`).

- Voor Adobe Commerce as a Cloud Service-klanten wordt de nieuwste versie geïnstalleerd in uw omgeving.

- Voor Adobe Commerce op cloud-systemen op locatie raadt Adobe aan om Composer te gebruiken om het pakket met catalogusservices in uw cloud-omgevingen bij te werken met de nieuwste versie.

### v3.3.0-release

_14 oktober 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) **verbetering van de Diensten van Gegevens** - `magento/data-services` gebiedsdeel dat aan ^8.0.0 wordt bijgewerkt. Controleer het gebruik van de omgeving en de aangepaste API voor Data Services voor 8.x-compatibiliteit voordat u een upgrade uitvoert.
ea
![ Nieuwe ](../assets/new.svg) Bijgewerkte versie en meta-gegevens voor de 3.3.0 versie.

### v3.2.0-release

_12 april 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Versie en meta-gegevens die voor 3.2.0 worden bijgewerkt. Geen andere afhankelijkheidswijzigingen.

### v3.1.0-release

_Januari 26, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Toegevoegde nieuwe pakketgebiedsdelen:

- **de gegevensexporteur van de toestemmingsgegevens van de Categorie** (`magento/module-category-permission-data-exporter`) voor het uitvoeren van categorietoestemmingsgegevens die door de catalogusdienst worden gebruikt.
- **Admin van de Synchronisatie van de Catalogus** `magento/module-catalog-sync-admin` voor Admin UI en configuratie met betrekking tot catalogussynchronisatie.

![ Nieuwe ](../assets/new.svg) Bijgewerkte versie en meta-gegevens voor de 3.1.0 versie.

## Gerelateerde documentatie

- Voor projecten die op **Adobe Commerce op wolk, op gebouw, of Adobe Commerce as a Cloud Service worden opgesteld, zie de volgende documentatie:

   - [Catalogusservicehandleiding](overview.md)
   - [ de Verwijzing van GraphQL API van de Dienst van de Catalogus ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/)
   - [ Gids van Admin van Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-admin/)
   - [ de Gids van as a Cloud Service van Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/)
   - [ Adobe Commerce op de Gids van de Wolk ](https://experienceleague.adobe.com/en/docs/commerce-cloud/)

- Voor projecten die **Adobe Commerce Optimizer** gebruiken of **Schakelaar van Adobe Commerce Optimizer**, zie de volgende documentatie:

   - [ Handleiding van de Ontwikkelaar van de Diensten van de Merchandising ](https://developer.adobe.com/commerce/services/optimizer/)
   - [ het Merchandising GraphQL API Verwijzing ](https://developer.adobe.com/commerce/services/reference/graphql/)
   - [Adobe Commerce Optimizer Guide](../optimizer/overview.md)
