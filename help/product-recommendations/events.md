---
title: Gegevens verzamelen
description: Leer hoe de gebeurtenissen gegevens voor  [!DNL Product Recommendations] verzamelen.
feature: Services, Recommendations, Eventing
exl-id: 0d5317e3-c049-4fcd-a8e4-228668d89386
source-git-commit: 94d2a9911ab10d164d75779d1f310e5bdf2aea74
workflow-type: tm+mt
source-wordcount: '1360'
ht-degree: 0%

---

# Gegevens verzamelen

Wanneer u op SaaS gebaseerde Adobe Commerce-functies zoals [[!DNL Product Recommendations]](install-configure.md) of [[!DNL Live Search]](../live-search/install.md) installeert en configureert, implementeren de modules gedragsgegevensverzameling in uw winkel. Dit mechanisme verzamelt geanonimiseerde gedragsgegevens van uw kopers en machten [!DNL Product Recommendations] . De gebeurtenis `view` wordt bijvoorbeeld gebruikt om het `Viewed this, viewed that` aanbeveling-type te berekenen en de gebeurtenis `place-order` wordt gebruikt om het `Bought this, bought that` aanbeveling-type te berekenen.

>[!NOTE]
>
>Gegevensverzameling ten behoeve van [!DNL Product Recommendations] omvat geen PII (Persoonlijk identificeerbare informatie). Alle gebruikers-id&#39;s, zoals cookie-id&#39;s en IP-adressen, worden strikt geanonimiseerd. Leer [ meer ](https://www.adobe.com/privacy/experience-cloud.html).

## Gezondheidszorgklanten

Als u een gezondheidszorgklant bent en u de [ uitbreiding van HIPAA van de Diensten van Gegevens ](../data-connection/hipaa-readiness.md#installation) installeerde, die deel van de [ uitbreiding van de Verbinding van Gegevens ](../data-connection/overview.md) uitmaakt, worden de gegevens van de storefront gebeurtenis die door [!DNL Product Recommendations] worden gebruikt niet meer gevangen. Dit komt doordat gebeurtenisgegevens voor storefront op de client worden gegenereerd. Als u gegevens over storefront-gebeurtenissen wilt blijven vastleggen en verzenden, schakelt u gebeurtenisverzameling opnieuw in voor [!DNL Product Recommendations] . Zie [ algemene configuratie ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/general.html#data-services) om meer te leren.

## Gegevenstypen en gebeurtenissen

Er worden twee soorten gegevens gebruikt in productaanbevelingen:

- **Gedrag** - Gegevens van de overeenkomst van een verkoopster op uw plaats, zoals productmeningen, punten die aan een kar worden toegevoegd, en aankopen.
- **Catalogus** - de meta-gegevens van het Product, zoals naam, prijs, beschikbaarheid, etc.

Wanneer u de module `magento/product-recommendations` installeert, aggregeert Adobe Sensei de gedrags- en catalogusgegevens en worden productaanbevelingen voor elk type aanbeveling gemaakt. De dienst van de Aanbevelingen van het Product stelt dan die aanbevelingen aan uw opslag in de vorm van een widget op die de geadviseerde product _punten_ bevat.

Sommige soorten aanbevelingen gebruiken gedragsgegevens van uw klanten om machine het leren modellen op te leiden om gepersonaliseerde aanbevelingen te bouwen. Andere soorten aanbevelingen gebruiken alleen catalogusgegevens en gebruiken geen gedragsgegevens. Als u snel wilt beginnen met het gebruik van productaanbevelingen op uw site, kunt u de volgende aanbevolen typen gebruiken, alleen voor catalogi:

- `More like this`
- `Visual similarity`

### Koude start

Wanneer kunt u beginnen met het gebruiken van aanbevelingen die gedragsgegevens gebruiken? Het hangt ervan af. Dit wordt bedoeld als _Koud Begin_ probleem.

Het _Koude 1&rbrace; probleem van het Begin van het Begin &lbrace;verwijst naar de tijd het voor een model neemt om te trainen en effectief te worden._ Voor productaanbevelingen betekent dit dat Adobe Sensei moet wachten om voldoende gegevens te verzamelen voor het trainen van zijn modellen voor machinaal leren voordat het aanbevelingen op uw plaats opstelt. Hoe meer gegevens de modellen hebben, des te nauwkeuriger en nuttiger de aanbevelingen zijn. Aangezien de gegevensinzameling op een levende plaats gebeurt, is het best om dit proces vroegtijdig te beginnen door de `magento/production-recommendations` module te installeren en te plaatsen.

De volgende tabel bevat een aantal algemene richtlijnen voor de hoeveelheid tijd die nodig is om voldoende gegevens voor elk type aanbeveling te verzamelen:

| Type aanbeveling | Trainingstijd | Notities |
|---|---|---|
| Gebaseerd op populariteit (`Most viewed`, `Most purchased`, `Most added to cart`) | Varieert | Afhankelijk van het volume van gebeurtenissen - weergaven worden het meest gebruikt en leren dus sneller; voegt dan toe aan winkelwagentje en koopt |
| `Viewed this, viewed that` | Meer training is vereist | De productweergaven zijn aanzienlijk hoog in volume |
| `Viewed this, bought that`, `Bought this, bought that` | De meeste training is vereist | Aankoopgebeurtenissen zijn de meest voorkomende gebeurtenissen op een commercesite, met name in vergelijking met productweergaven |
| `Trending` | Vereist drie dagen gegevens om een basislijn voor populariteit te bepalen | Trending is een maat voor de recente dynamiek in de populariteit van een product in vergelijking met zijn eigen populariteit. De trending score van een product wordt berekend met behulp van een voorgrondset (recente populariteit in 24 uur) en een achtergrondset (basislijn voor populariteit in 72 uur). Als de populariteit van een item binnen een periode van 24 uur aanzienlijk toeneemt ten opzichte van de basislijnpopulariteit, krijgt het item een hoge trendscore. Elk product heeft deze score, en de punten met de hoogste score op elk ogenblik bestaan uit de reeks hoogste trending producten. |

Andere variabelen die van invloed kunnen zijn op de tijd die nodig is om te trainen:

- Hoger verkeersvolume draagt bij aan sneller leren
- Sommige aanbevelingen typen sneller dan andere
- Adobe Commerce berekent de gedragsgegevens elke vier uur opnieuw. Aanbevelingen worden nauwkeuriger naarmate ze langer op uw site worden gebruikt.

Om u te helpen de opleidingsvooruitgang van elk aanbevelingstype visualiseren, [ creeer aanbeveling ](create.md#readiness-indicators) de indicatoren van de paginabereidheid.

Terwijl gegevens worden verzameld op uw livesite en de modellen voor het leren van machines een training zijn, kunt u andere test- en configuratietaken voltooien die nodig zijn om aanbevelingen op te stellen. Tegen de tijd dat u met dit werk wordt gedaan, zullen de modellen genoeg gegevens hebben om nuttige aanbevelingen tot stand te brengen, die u toestaan om hen aan uw winkel op te stellen.

Als uw plaats niet genoeg verkeer (meningen, aankopen, tendensen) voor de meeste product SKUs krijgt, zouden er niet genoeg gegevens kunnen zijn om het het leren proces te voltooien. Hierdoor kan de gereedheidsindicator in de Admin vastzitten. De gereedheidsindicatoren zijn bedoeld om handelaren een ander gegevenspunt te bieden bij het kiezen van het aanbevolen type voor hun winkel. De getallen zijn een leidraad en mogen nooit 100% bedragen. [ Leer meer ](create.md#readiness-indicators) over bereidheid indicatoren.

### Aanbevelingen voor back-up {#backuprecs}

Als de invoergegevens onvoldoende zijn om alle gevraagde aanbevelingen in een eenheid op te nemen, geeft Adobe Commerce back-upaanbevelingen om de aanbevolen eenheden te vullen. Als u bijvoorbeeld het aanbevolen type `Recommended for you` op uw homepage plaatst, heeft een eerste winkelprogramma op uw site niet genoeg gedragsgegevens gegenereerd om op de juiste manier gepersonaliseerde producten te kunnen aanbevelen. In dit geval worden Adobe Commerce-items op basis van het aanbevolen type `Most viewed` aan deze gebruiker doorgegeven.

In het geval van onvoldoende gegevensverzameling worden de volgende aanbevelingen getypt als fallback naar het aanbevolen type `Most viewed` :

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`

### Gebeurtenissen

De [ Verzameling van de Gebeurtenis van Adobe Commerce Storefront ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) maakt een lijst van alle gebeurtenissen die aan uw storefront worden opgesteld. In die lijst staat een subset van gebeurtenissen die specifiek zijn voor [!DNL Product Recommendations] . Deze gebeurtenissen verzamelen gegevens wanneer de klanten met aanbevelingen op de storefront in wisselwerking staan en macht de metriek om te analyseren hoe goed uw aanbevelingen presteren.

| Gebeurtenis | Beschrijving |
| --- | --- |
| `impression-render` | Verzonden wanneer de aanbeveling-eenheid op de pagina wordt weergegeven. Als een pagina twee aanbevelingen-eenheden heeft (gekocht, weergave-weergave), worden twee `impression-render` -gebeurtenissen verzonden. Deze gebeurtenis wordt gebruikt om metrisch voor beelden te volgen. |
| `rec-add-to-cart-click` | De verkoopster klikt **toevoegt aan wortel** knoop voor een punt in de aanbeveling eenheid. |
| `rec-click` | De verkoopster klikt op een product in de aanbevolen eenheid. |
| `view` | Verzonden wanneer de aanbevelingen-eenheid voor ten minste 50 procent zichtbaar wordt, bijvoorbeeld door naar beneden te schuiven. Als een aanbevolen eenheid bijvoorbeeld twee regels heeft, wordt een `view` -gebeurtenis verzonden wanneer één regel plus één pixel van de tweede regel zichtbaar wordt voor de gebruiker. Als de gebruiker de pagina meerdere keren omhoog en omlaag schuift, wordt de gebeurtenis `view` net zo vaak verzonden als de gebruiker de hele aanbevolen eenheid weer op de pagina ziet. |

>[!NOTE]
>
>Metrische gegevens voor productaanbevelingen zijn geoptimaliseerd voor Luma-winkels. Als uw opslag met PWA Studio wordt uitgevoerd, verwijs naar de [ documentatie van PWA ](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Als u een douane frontend technologie zoals React of Vue JS gebruikt, leer hoe te om [ Aanbevelingen van het Product in een headless ](headless.md) milieu te integreren.

#### Vereiste dashboardgebeurtenissen

De volgende gebeurtenissen worden vereist om het [[!DNL Product Recommendations]  dashboard ](workspace.md) te bevolken

| Dashboardkolom | Gebeurtenissen | Veld samenvoegen |
| ---------------- | --------- | ----------- |
| Impressies | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | `unitId` |
| Weergaven | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | `unitId` |
| Klikken | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click` | `unitId` |
| Ontvangsten | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| LT-ontvangsten | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | `unitId`, `sku`, `parentSku` |
| CTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |
| vCTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | `unitId`, `sku`, `parentSku` |

De volgende gebeurtenissen zijn niet specifiek voor productaanbevelingen, maar zijn vereist voor Adobe Sensei om winkelgegevens correct te interpreteren:

- `view`
- `add-to-cart`
- `place-order`

#### Type aanbeveling

In deze tabel worden de gebeurtenissen beschreven die door elk type aanbeveling worden gebruikt.

| Type aanbeveling | Gebeurtenissen | Pagina |
| --- | --- | --- |
| Meest bekeken | `page-view`<br>`product-view` | Productdetailpagina |
| Meest aangekocht | `page-view`<br>`place-order` | Winkelwagentje/Afhandeling |
| Meest toegevoegd aan winkelwagentje | `page-view`<br>`add-to-cart` | De detailpagina van het product <br> product die pagina <br> van de Lijst van de Kar <br> van de Wenslijst van het Product |
| Bekeken dit, gezien dat | `page-view`<br>`product-view` | Productdetailpagina |
| Bekijk dit, kocht dat | Recs product | `page-view`<br>`product-view` | De detailpagina van het product <br> Kar/Controle |
| Dit gekocht | Recs product | `page-view`<br>`product-view` | Productdetailpagina |
| Trend | `page-view`<br>`product-view` | Productdetailpagina |
| Conversie: Weergeven voor aankoop | Recs product | `page-view`<br>`product-view` | Productdetailpagina |
| Conversie: Weergeven voor aankoop | Recs product | `page-view`<br>`place-order` | Winkelwagentje/Afhandeling |
| Omzetten: Weergeven naar winkelwagentje | Recs product | `page-view`<br>`product-view` | Productdetailpagina |
| Omzetten: Weergeven naar winkelwagentje | Recs product | `page-view`<br>`add-to-cart` | De detailpagina van het product <br> van de lijst van het Product pagina <br> Kaart <br> Wislijst |

#### Caveats

- Ad blokkers en privacymontages kunnen gebeurtenissen verhinderen worden gevangen en zouden de overeenkomst en opbrengst [ metriek ](workspace.md#column-descriptions) kunnen veroorzaken om worden onderdrukt. Bovendien kunnen bepaalde gebeurtenissen niet worden verzonden omdat de gebruiker de pagina of het netwerk heeft verlaten.
- [ Headless implementaties ](headless.md) moet het verhinderen uitvoeren om het dashboard van de Aanbevelingen van het Product te aandrijven.
- Voor configureerbare producten gebruiken de Aanbevelingen van het Product het beeld van het ouderproduct in de adviseringseenheid. Als voor het configureerbare product geen afbeelding is opgegeven, is de aanbevolen eenheid leeg voor dat specifieke product.

>[!NOTE]
>
>Als [ de Wijze van de Beperking van het Koekje ](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html?lang=nl-NL) wordt toegelaten, verzamelt Adobe Commerce geen gedragsgegevens tot de verkoopster toestemming geeft om koekjes te gebruiken. Als de modus Cookie-beperking is uitgeschakeld, verzamelt Adobe Commerce standaard gedragsgegevens.
