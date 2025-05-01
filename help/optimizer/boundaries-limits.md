---
title: Grenzen en grenzen
description: Leer over de grenzen en de grenzen voor  [!DNL Adobe Commerce Optimizer]  om ervoor te zorgen het aan de behoeften van uw zaken voldoet.
role: Admin, Developer
source-git-commit: 45a43fe2ada206515c512a04aa6e9072e08844cc
workflow-type: tm+mt
source-wordcount: '335'
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

- Het maximumaantal prijzenboeken is 30.000. Het basisniveau van prijzenboeken mag niet hoger zijn dan 100 en moet de regel volgen waarin (het aantal prijzenboeken) x (het aantal kanalen) kleiner dan of gelijk aan 100 moet zijn.
- De gegarandeerde prijs voor de inname van diervoeder bedraagt 5000 records per minuut.
- Eén prijsnotering mag niet meer dan tien kortingen hebben.
- Het basisaantal prijsupdates per dag is 5.000.000.

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

   - ACO steunt het _Onlangs bekeken_ aanbevelingen type voor EA
   - Er is geen ondersteuning voor de opname of uitsluiting van categorieën of kenmerken.
   - U kunt geen voorvertoning van aanbevelingen weergeven in [!DNL Adobe Commerce Optimizer] .
