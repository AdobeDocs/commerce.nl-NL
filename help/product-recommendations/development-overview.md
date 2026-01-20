---
title: Productaanbevelingen Beheerderontwikkeling
description: Een overzicht van de architectuur en de ontwikkelingseigenschappen van de Aanbevelingen van het Product.
exl-id: 5967259e-c531-4fc7-9abd-cc18433fab33
source-git-commit: 458f34c45406db871ec61ff408aa624f163b6ee0
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# Productaanbevelingen Beheerderontwikkeling

De Aanbevelingen van het product zijn een krachtig marketing hulpmiddel u kunt gebruiken om omzettingen te verhogen, opbrengst te verhogen, en winkelbetrokkenheid te stimuleren. De aanbevelingen van het product worden op de winkel in de vorm van eenheden zoals &quot;Klanten die dit product ook bekeken hebben&quot;, &quot;Klanten die dit product ook kochten&quot;, &quot;Aanbevolen voor u&quot;, enzovoort. De Aanbevelingen van het Product van Adobe Commerce worden aangedreven door [&#x200B; Adobe AI &#x200B;](https://business.adobe.com/ai.html), die kunstmatige intelligentie en machine-leert algoritmen gebruikt om een diepe analyse van samengevoegde verkoopgegevens uit te voeren. Deze gegevens, in combinatie met uw Commerce-catalogus, resulteren in zeer boeiende, relevante en persoonlijke ervaringen voor de klant.

>[!NOTE]
>
>Als uw opslag gebruikend PWA Studio wordt uitgevoerd, verwijs naar de [&#x200B; documentatie van PWA &#x200B;](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Als u een douane frontend technologie zoals React of Vue JS gebruikt, verwijs naar de gebruikersgids om te leren hoe te om de Aanbevelingen van het Product in a [&#x200B; te integreren hoofd &#x200B;](headless.md) milieu. De instanties zonder kop moeten gebeurtenis uitvoeren om de werkruimte van de Aanbeveling van het Product te aandrijven.

## Overzicht van architectuur

Op hoog niveau worden Commerce-productaanbevelingen geïmplementeerd als SaaS. De zijde van Commerce omvat storefront, die de de lay-outmalplaatje van de gebeurtenisinzamelaar en van de aanbevelingen, en het achterste eind bevat, dat de Diensten van Gegevens, de module van de Uitvoer SaaS, en Admin UI omvat. Adobe AI-inlichtingendiensten worden gebruikt aan SaaS-zijde.

![&#x200B; het diagram van de de aanbevelingen van het Product architectuur &#x200B;](assets/arch-diag-sensei.svg)

Zodra de aanbevelingen modules worden geïnstalleerd en gevormd, zal uw opslag beginnen het verzamelen van gedragsgegevens. Adobe AI verwerkt deze gedragsgegevens samen met uw catalogusgegevens en berekent productkoppelingen die worden gebruikt door de service met aanbevelingen. Op dit punt, kan de handelaar, producten tot stand brengen leiden en, eenheden van de aanbeveling aan hun winkel direct van Admin UI opstellen.

## Volgende stappen

Lees de volgende onderwerpen om aan de slag te gaan met productaanbevelingen:

- [Productaanbevelingen implementeren](implementation-workflow.md)

- [Productaanbevelingen installeren en configureren](install-configure.md)

- [Aanbevelingen voor producten maken](create.md)
