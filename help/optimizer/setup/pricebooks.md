---
title: Prijsboeken
description: Leer hoe te om prijsboeken in  [!DNL Adobe Commerce Optimizer] te beheren.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 553490762ef10e43ccce1654acec59aeb83bb5f9
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Prijsboeken

In dit artikel wordt beschreven hoe u prijzenboeken kunt definiëren en toewijzen aan catalogusweergaven met de juiste besturingselementen voor gegevensbeheer.

Zie de [ ontwikkelaarsdocumentatie ](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/api-reference/#tag/Price-Books) leren hoe te om de informatie van het prijsboek van een derdesysteem in [!DNL Adobe Commerce Optimizer] in te voeren gebruikend de Boek API van de Prijs.

Met prijzenboeken kunt u de bronnen van de prijscatalogus bepalen om productprijzen over verschillende klantenniveaus en markten te beheren. De boeken van de prijs steunen een hiërarchisch model, dat tot drie niveaus van genestelde kindprijsboeken onder elk basisprijzenboek toestaat. Elk prijzenboek kan naar een ouderprijzenboek verwijzen, dat een boomstructuur voor het bepalen van catalogusbronnen vormt.

Het basisprijzenboek definieert de valuta voor zichzelf en al zijn kinderprijzenboeken. De boeken van de kindprijs erven deze munt en kunnen niet het met voeten treden.

## Belangrijkste concepten

| Term | Beschrijving |
|------|-------------|
| **Boek van de Prijs** | Logische groepering die de bron van de prijscatalogus bepaalt; bijvoorbeeld, specifiek gebied, of klantenrij en wordt gebruikt om productprijzen te beheren. |
| **Boek van de Prijs van de Fallback** | Het bovenste prijzenboek in een hiërarchie. Het heeft geen ouder en is het *slechts* prijsboek dat de munt voor zich en al zijn afstammende prijsboeken bepaalt.<br/><br/> als geen ouder tijdens de verwezenlijking van het prijsboek (door API) wordt bepaald, wordt een nieuw fallback prijzenboek gecreeerd. |
| **Boek van de Prijs van de Ouder** | Een prijzenboek op een hoger niveau waarvan een onderliggend prijzenboek prijzen kan erven als ze niet expliciet in het kind zijn ingesteld. |
| **de Diepte van de Hiërarchie** | Maximum van 3 niveaus (Fallback → Kind → Grootkind) <br/><br/> niet afgedwongen bij innametijd. |
| **Valuta** | Gedefinieerd alleen voor fallback-prijzenboek. Overgenomen door alle kinderen, prijzenboeken.<br/><br/> als de munt niet tijdens de verwezenlijking van het fallback prijzenboek (door API) wordt gespecificeerd blijft de munt aan USD in gebreke. |
| **Prijs van het Product** | De specifieke prijs die is toegewezen aan een product (SKU) binnen een bepaald prijzenboek. |
| **Kortingen** | Kortingen worden gedefinieerd in de productprijs. Niet overgenomen. |
