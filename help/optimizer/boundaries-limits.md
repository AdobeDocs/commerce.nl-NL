---
title: Grenzen en grenzen
description: Leer over de grenzen en de grenzen voor  [!DNL Adobe Commerce Optimizer]  om ervoor te zorgen het aan de behoeften van uw zaken voldoet.
role: Admin, Developer
exl-id: 58d94da9-8d48-4513-8b6a-8e8c7c27a2a5
source-git-commit: 149b87fc822e5d07eed36f3d6a38c80e7b493214
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---

# Grenzen en grenzen

>[!NOTE]
>
>Deze documentatie beschrijft de grenzen en de grenzen voor vroege-toegangsontwikkeling en weerspiegelt niet alle functionaliteit voorgenomen voor algemene beschikbaarheid.

Hieronder vindt u grenzen en beperkingen voor Adobe Commerce Optimizer.

## Catalogus

- De gegarandeerde catalogusopname bedraagt: 1000 producten per minuut en 5000 prijzen per minuut
- Het basisaantal productupdates per dag is 1.000.000.
- Het totale aantal SKU&#39;s dat in één instantie is toegestaan, is 250.000. 
- Het maximumaantal scènes is 50.
- Het aantal varianten per product is 10.000.
- De productgrootte mag niet groter zijn dan 200 kB.

## Prijzen

- Het maximumaantal prijzenboeken is 1.000.

## Zoeken en opslaan

- Het aantal producten dat één enkel onderzoeksverzoek kan terugkeren is 100.
- Het maximumaantal filterbare kenmerken is 200
- Het maximumaantal doorzoekbare kenmerken is 200
- Het maximumaantal sorteerbare kenmerken is 50
- Het maximumaantal facetten is 100. Alle facetten moeten filterbare attributen zijn.
- Het maximumaantal opties dat één facetcat retourneert, is 100. Dit kan per ondersteuningsverzoek worden verhoogd.

## Kanalen en beleid

- Het maximumaantal kanalen per huurder is 1000.
- Het maximumaantal beleid dat aan één kanaal wordt toegewezen is 10.
- Het maximumaantal kenmerkwaarden dat in een beleid wordt gebruikt, is 100. 

## Productdetectie en aanbevelingen

- Voor productdetectie worden op kenmerken gebaseerde merchandising en prijsinstellingen niet ondersteund.
- Voor aanbevelingen:

   - [!DNL Adobe Commerce Optimizer] steunt het _onlangs Bekeken_ aanbevelingstype voor vroege toegang.
   - Er is geen ondersteuning voor de opname of uitsluiting van categorieën of kenmerken.
   - U kunt geen voorvertoning van aanbevelingen weergeven in [!DNL Adobe Commerce Optimizer] .
