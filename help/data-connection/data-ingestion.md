---
title: Typen Commerce-gegevens
description: Leer de typen gegevens die u kunt verzamelen en naar de Experience Platform kunt verzenden.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Typen Commerce-gegevens

De [ uitbreiding van de Verbinding van Gegevens ](overview.md) verbindt uw gegevens van Commerce met Experience Platform. De gegevens voorgenomen voor gebruik in Experience Platform worden gegroepeerd in twee gedragstypes: tijdreeksgegevens, die tot de **klasse van de Gebeurtenis van de 1&rbrace; van de Ervaring behoren**, en verslaggegevens, die tot de **Individuele klasse van het Profiel** behoren.

Leer meer over [ gegevensgedrag ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) en [ klassen ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) in Experience Platform.

## Gegevens uit tijdreeksen

De gegevens van de tijdreeksen verstrekken een momentopname van het systeem op het tijdstip dat een actie of direct of indirect door een verslagonderwerp werd genomen. Als een winkelier bijvoorbeeld door een product op uw site bladert, voegt u een product toe aan de winkelwagentje, plaatst u een bestelling enzovoort. De reeksgegevens van de tijd worden opgenomen in Experience Platform gebruikend een schema dat de klasse heeft die aan **de Gebeurtenis van de Ervaring** wordt geplaatst.

### Vastgelegde tijdreeksgegevens

Zie [ gedragsgebeurtenissen ](events.md) en [ achterkantoorgebeurtenissen ](events-backoffice.md) om te leren welke gegevens worden gevangen wanneer een gebeurtenis van de tijdreeks wordt geproduceerd.

### Schema nodig om gebeurtenisgegevens voor tijdreeksen in te voeren

Leer hoe te om [ een schema ](update-xdm.md) tot stand te brengen dat gedrags en de gegevens van de de tijdreeksgebeurtenis van het achterkantoor kan opnemen.

## Gegevens opnemen

De gegevens van het verslag verstrekken informatie over de attributen van een onderwerp. Een onderwerp kan een organisatie of een individu zijn. Een winkelier op uw site maakt bijvoorbeeld een account en genereert recordgegevens. Dit gegeven wordt opgenomen in Experience Platform gebruikend een schema dat de klasse heeft die aan **Individueel Profiel** wordt geplaatst. U kunt die verslaggegevens naar het profielbeheer en de segmenteringsdienst van Adobe verzenden: [ Real-Time CDP ](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

### Vastgelegde profielrecordgegevens

Zie [ gegevens van het het profielverslag van de klant ](events-profilerecord.md) leren welke gegevens worden gevangen wanneer een profielverslag wordt geproduceerd.

### Schema nodig voor het invoeren van profielrecordgegevens

Leer hoe te om [ een schema ](profile-data.md) tot stand te brengen dat de gegevens van het profielverslag kan opnemen.
