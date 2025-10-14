---
title: Prijsboeken
description: Leer hoe te om prijsboeken in  [!DNL Adobe Commerce Optimizer] te beheren.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: a1849830-3d0e-4df9-ab73-380659c3f9dc
source-git-commit: 502d8d21ff052f4ecb212176459b38ce51f85dfc
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Prijsboeken

Met prijzenboeken kunt u productprijzen voor een catalogusbron definiëren voor verschillende klantniveaus en markten. De boeken van de prijs steunen een hiërarchisch model, dat tot drie niveaus van genestelde kindprijsboeken onder elk basisprijzenboek toestaat. Elk prijzenboek kan naar een ouderprijzenboek verwijzen, dat een boomstructuur voor het bepalen van catalogusbronnen vormt.

Het basisprijzenboek definieert de valuta voor zichzelf en al zijn kinderprijzenboeken. De boeken van de kindprijs erven deze munt en kunnen niet het met voeten treden.

Zie de [&#x200B; ontwikkelaarsdocumentatie &#x200B;](https://developer.adobe.com/commerce/services/reference/rest/) leren hoe te om, prijzenboeken voor [!DNL Adobe Commerce Optimizer] tot stand te brengen bij te werken en te schrappen het gebruiken van de Boek API van de Prijs.

## Belangrijkste concepten

| Term | Beschrijving |
|------|-------------|
| **Boek van de Prijs** | Logische groepering die prijzen voor een catalogusbron bepaalt; bijvoorbeeld, specifiek gebied, of klantenrij en wordt gebruikt om productprijzen te beheren. |
| **Boek van de Prijs van de Fallback** | Het bovenste prijzenboek in een hiërarchie. Het heeft geen ouder en is het *slechts* prijsboek dat de munt voor zich en al zijn afstammende prijsboeken bepaalt.<br/><br/> als geen ouder tijdens de verwezenlijking van het prijsboek (door API) wordt bepaald, wordt een nieuw fallback prijzenboek gecreeerd. |
| **Boek van de Prijs van de Ouder** | Een prijzenboek op een hoger niveau waaruit een onderliggend prijzenboek prijzen kan overerven als deze niet expliciet in het kind zijn ingesteld. |
| **de Diepte van de Hiërarchie** | Maximum van drie niveaus (Fallback -> Kind -> Grootkind) <br/><br/> niet afgedwongen bij innametijd. |
| **Valuta** | Uitsluitend gedefinieerd voor de fallback-prijs. Overgenomen door alle kinderprijzenboeken.<br/><br/> als de munt niet tijdens de verwezenlijking van het fallback prijzenboek (door API) wordt gespecificeerd blijft de munt aan USD in gebreke. |
| **Prijs van het Product** | De specifieke prijs die is toegewezen aan een product (SKU) binnen een bepaald prijzenboek. |
| **Kortingen** | Kortingen worden gedefinieerd in de productprijs. Niet overgenomen. |
