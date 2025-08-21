---
title: Implementatieworkflow
description: Leer de stappen om  [!DNL Product Recommendations]  op uw storefront met succes uit te voeren.
exl-id: 4a784d04-8be6-473f-afb3-264af06c850a
source-git-commit: a3e19940e2a3d8a240bb17703cfdd9903df311aa
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Implementatieworkflow

[!DNL Product Recommendations] gebruikt zowel gedragsgegevens als catalogusgegevens:

- Gedrag - Gegevens uit de betrokkenheid van een klant op uw site, zoals productweergaven, aan een winkelwagentje toegevoegde items en aankopen. Adobe Commerce en Adobe Sensei verzamelen geen persoonlijk identificeerbare informatie.

- Catalogus - Productmetagegevens, zoals naam, prijs en beschikbaarheid.

Wanneer u `magento/product-recommendations module` installeert, aggregeert Adobe Sensei de gedrags- en catalogusgegevens en maakt het [!DNL Product Recommendations] voor elk type aanbeveling. De service [!DNL Product Recommendations] implementeert deze aanbevelingen vervolgens in uw winkel. Om u te helpen productaanbevelingen op uw winkel uitvoeren, gebruik het volgende werkschema:

>[!NOTE]
>
> Als uw opslag gebruikend PWA Studio wordt uitgevoerd, verwijs naar de [ documentatie van PWA ](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Als u een douane frontend technologie zoals React of Vue JS gebruikt, leer hoe te [&#128279;](headless.md) integreren [!DNL Product Recommendations] in uw headless opslag.

## Workflow

1. **stelt gegevensinzameling aan productie** op

   Het opstellen [!DNL Product Recommendations] vereist twee belangrijkste [ gegevensbronnen ](type.md): catalogus en gedrag. Omdat productie de enige omgeving is waarin de acties van uw klanten worden vastgelegd en geanalyseerd, moet u zo vroeg mogelijk beginnen met het verzamelen van gegevens over productie. [ Leer ](events.md) hoe Adobe Sensei machine het leren modellen tredt die in hogere kwaliteit aanbevelingen resulteren. Als toegevoegd voordeel, wanneer u gedragsgegevens over productie begint te verzamelen, kunt u [ aanbevelingen ](staging-environment.md#fetch-recommendations-from-production-environment-recommended) halen die op deze productiegegevens worden gebaseerd terwijl het werken in niet-productiemilieu&#39;s. Vervolgens kunt u testen en experimenteren met verschillende aanbevelingen die worden berekend op basis van echte verkoopgegevens die in productie worden verzameld.

   Om gegevensinzameling aan productie op te stellen, moet u [ installeren en vormen ](install-configure.md) module door een [!DNL Product Recommendations] API sleutel [ te verstrekken.](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html)

   >[!TIP]
   >
   > Het implementeren van gegevensverzameling heeft geen invloed op de weergave van de winkel of op de ervaring van kopers. Het creëren van en het opstellen van aanbevelingen veranderen slechts de klantenervaring op uw winkelfront. Zorg ervoor u op uw niet productiemilieu test alvorens aan productie op te stellen. Creëer ook geen aanbevelingen-eenheden totdat u de sjabloon aanpast. Zie de volgende stap.

1. **pas het malplaatje aan om uw stijl aan te passen**

   Uw winkel vertegenwoordigt uw merk, dus zorg ervoor u het malplaatje van productaanbevelingen aanpast om uw plaatsthema aan te passen.

   >[!TIP]
   >
   > Door het malplaatje aan te passen, kunt u uw stijlblad specificeren, beschrijven waar een aanbevelingseenheid op een pagina, etc. verschijnt.

   Zie [&#128279;](https://experienceleague.adobe.com/docs/commerce/product-recommendations/developer/customize.html) aanpassen in de ontwikkelaardocumentatie leren hoe te om deze stap te voltooien.

1. **aanbevelingen van de Test op uw niet-productiemilieu**

   Het is altijd een beste praktijk om een nieuwe technologie op uw niet productiemilieu te testen alvorens u aan productie opstelt. Als u aanbevelingen test voor uw niet-productieomgeving, kunt u met verschillende typen aanbevelingen, positionering en pagina&#39;s spelen. U kunt aanbevelingen trekken die op gedragsgegevens reeds bij productie terwijl het testen in uw niet productieklimaat worden verzameld, zodat de raadsresultaten op het het winkelen gedrag van daadwerkelijke klanten gebaseerd zijn.

   >[!TIP]
   >
   > Zorg ervoor dat de niet-productieomgevingscatalogus grotendeels dezelfde is als de catalogus die u in productie hebt. Door vergelijkbare catalogi te gebruiken, zorgt u ervoor dat de producten die in de aanbevolen eenheden worden geretourneerd, de producten op productie nauwkeurig nabootsen.

   Zie [ gedragsgegevens van 0&rbrace; Vetsen &lbrace;van uw productiemilieu leren hoe te om deze stap te voltooien.](staging-environment.md)

1. **creeer en stel aanbevelingen aan uw productieopslag op**

   Nu u de inzameling van gedragsgegevens in productie hebt opgesteld, het malplaatje van productaanbevelingen, en geteste aanbevelingen gebruikend werkelijk verkoopgedrag hebt gewijzigd, bent u bereid om al code aan productie te bevorderen en [&#128279;](create.md) levende productaanbevelingen tot stand te brengen.
