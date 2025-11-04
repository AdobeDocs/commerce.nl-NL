---
title: Gegevens verzamelen
description: Leer hoe de gebeurtenissen gegevens voor  [!DNL Product Recommendations] verzamelen.
feature: Services, Recommendations, Eventing
exl-id: 0d5317e3-c049-4fcd-a8e4-228668d89386
source-git-commit: d770d4d99802f7ecf6e395518dfc9aeaac9aa130
workflow-type: tm+mt
source-wordcount: '980'
ht-degree: 0%

---

# Gegevens verzamelen

Wanneer u [[!DNL Product Recommendations]](install-configure.md) installeert en vormt, stelt de module gedragsgegevensinzameling aan uw storefront op. Dit mechanisme verzamelt geanonimiseerde gedragsgegevens van uw kopers en machten [!DNL Product Recommendations] . De gebeurtenis `view` wordt bijvoorbeeld gebruikt om het `Viewed this, viewed that` aanbeveling-type te berekenen en de gebeurtenis `place-order` wordt gebruikt om het `Bought this, bought that` aanbeveling-type te berekenen.

Zie de [&#x200B; ontwikkelaardocumentatie &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#product-recommendations) om meer over de gedragsgegevens te leren de [!DNL Product Recommendations] gebeurtenissen verzamelen.

>[!NOTE]
>
>Gegevensverzameling ten behoeve van [!DNL Product Recommendations] omvat geen PII (Persoonlijk identificeerbare informatie). Alle gebruikers-id&#39;s, zoals cookie-id&#39;s en IP-adressen, worden strikt geanonimiseerd. Leer [&#x200B; meer &#x200B;](https://www.adobe.com/privacy/experience-cloud.html).

## Gezondheidszorgklanten

Als u een gezondheidszorgklant bent en u de [&#x200B; uitbreiding van HIPAA van de Diensten van Gegevens &#x200B;](../data-connection/hipaa-readiness.md#installation) installeerde, die deel van de [&#x200B; uitbreiding van de Verbinding van Gegevens &#x200B;](../data-connection/overview.md) uitmaakt, worden de gegevens van de storefront gebeurtenis die door [!DNL Product Recommendations] worden gebruikt niet meer gevangen. Dit komt doordat gebeurtenisgegevens voor storefront op de client worden gegenereerd. Als u wilt doorgaan met het vastleggen en verzenden van gegevens over storefront-gebeurtenissen, schakelt u gebeurtenisverzameling opnieuw in voor [!DNL Product Recommendations] . Zie [&#x200B; algemene configuratie &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/general#data-services) om meer te leren.

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

Om u te helpen de opleidingsvooruitgang van elk aanbevelingstype visualiseren, [&#x200B; creeer aanbeveling &#x200B;](create.md#readiness-indicators) de indicatoren van de paginabereidheid.

Terwijl gegevens worden verzameld op uw livesite en de modellen voor het leren van machines een training zijn, kunt u andere test- en configuratietaken voltooien die nodig zijn om aanbevelingen op te stellen. Tegen de tijd dat u met dit werk wordt gedaan, zullen de modellen genoeg gegevens hebben om nuttige aanbevelingen tot stand te brengen, die u toestaan om hen aan uw winkel op te stellen.

Als uw plaats niet genoeg verkeer (meningen, aankopen, tendensen) voor de meeste product SKUs krijgt, zouden er niet genoeg gegevens kunnen zijn om het het leren proces te voltooien. Hierdoor kan de gereedheidsindicator in de Admin vastzitten. De gereedheidsindicatoren zijn bedoeld om handelaren een ander gegevenspunt te bieden bij het kiezen van het aanbevolen type voor hun winkel. De getallen zijn een leidraad en mogen nooit 100% bedragen. [&#x200B; Leer meer &#x200B;](create.md#readiness-indicators) over bereidheid indicatoren.

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

#### Caveats

- Ad blokkers en privacymontages kunnen gebeurtenissen verhinderen worden gevangen en zouden de overeenkomst en opbrengst [&#x200B; metriek &#x200B;](workspace.md#column-descriptions) kunnen veroorzaken om worden onderdrukt. Bovendien kunnen bepaalde gebeurtenissen niet worden verzonden omdat de gebruiker de pagina of het netwerk heeft verlaten.
- [&#x200B; Headless implementaties &#x200B;](headless.md) moet het verhinderen uitvoeren om het dashboard van de Aanbevelingen van het Product te aandrijven.
- Voor configureerbare producten gebruiken de Aanbevelingen van het Product het beeld van het ouderproduct in de adviseringseenheid. Als voor het configureerbare product geen afbeelding is opgegeven, is de aanbevolen eenheid leeg voor dat specifieke product.

>[!NOTE]
>
>Als [&#x200B; de Wijze van de Beperking van het Koekje &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) wordt toegelaten, verzamelt Adobe Commerce geen gedragsgegevens tot de verkoopster toestemming geeft om koekjes te gebruiken. Als de modus Cookie-beperking is uitgeschakeld, verzamelt Adobe Commerce standaard gedragsgegevens.
