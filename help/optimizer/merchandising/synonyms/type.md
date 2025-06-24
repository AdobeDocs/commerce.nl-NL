---
title: Typen synoniemen
description: Leer over de verschillende types van synoniemen in  [!DNL Adobe Commerce Optimizer].
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 3131cc27a25d1bf958071b973f1d4bf1a68be152
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Typen synoniemen

Met synoniemen in één en twee richtingen wordt de definitie van trefwoorden uitgebreid. Sommige zijn onderling verwisselbaar met het trefwoord, terwijl andere een subset van het trefwoord vertegenwoordigen.

## 2-wegs

Synoniemen in twee richtingen hebben dezelfde betekenis en retourneren dezelfde zoekresultaten. In het volgende voorbeeld is het eerste woord dat vet wordt weergegeven, het trefwoord dat wordt gebruikt in de catalogus, gevolgd door woorden met dezelfde betekenis als het oorspronkelijke trefwoord. U kunt een eenvoudig paar synoniemen in twee richtingen, of een ketting van veelvoudige synoniemen in twee richtingen voor het zelfde sleutelwoord tot stand brengen.

**jasje** ![ bidirectionele selecteur ](../../assets/btn-two-way.png) jas
**broek** ![ 2-wegenkiezer ](../../assets/btn-two-way.png) stapels ![ 2-wegenkiezer ](../../assets/btn-two-way.png) brousers

## Eenweg

Een eenrichtingssynoniem is een subset van een trefwoord, maar heeft een specifiekere betekenis. Capris en shorts zijn bijvoorbeeld broeken, maar niet alle planten zijn capris of korts. Een zoekopdracht naar broek omvat capris en korte broeken. Een zoekopdracht naar korte berichten retourneert echter geen capris.

**sweatshirt** ![ Één-weg selecteur ](../../assets/btn-one-way.png) hoodie
**broek** ![ Eenwegs selecteur ](../../assets/btn-one-way.png) capris ![ Veelvoudige unidirectionele selecteur ](../../assets/btn-multiple-one-way.png) calf-length-broek ![ Veelvoudige unidirectionele selecteur ](../../assets/btn-multiple-one-way.png) peddle handdupers

## Synoniemgedrag van meerdere woorden

Voor synoniemen met meerdere woorden beschouwt [!DNL Adobe Commerce Optimizer] het synoniem als een woordgroep. Bijvoorbeeld, als u een bidirectionele synoniem **het dineren van de lijst van de ruimte** ![ 2-wegenkiezer ](../../assets/btn-two-way.png) **keukenlijst** ![ 2-wegenkiezer ](../../assets/btn-two-way.png) **eetlijst** creeert, dan [!DNL Adobe Commerce Optimizer] onderzoeken over alle gebieden die aan zoekbaar voor het voorkomen van **eetbare kamerlijst** of **worden geplaatst 3&rbrace; keukenlijst** of **eetlijst**.

Als geen synoniem wordt gecreeerd en een verkoopster zoekt naar **keukenlijst**, [!DNL Adobe Commerce Optimizer] zoekt overal de termijnen op de doorzoekbare gebieden, zelfs over verschillende gebieden, bijvoorbeeld **lijst** op het naamgebied en **keuken** in het meta sleutelwoord.

Na het creëren van een synoniem, verandert het onderzoeksgedrag om de nauwkeurige uitdrukking **keukenlijst** te zoeken. Hierdoor kan het aantal resultaten afnemen, omdat alleen producten met de exacte zin worden weergegeven.

Als u de termijnen afzonderlijk wilt worden gezocht zoals voordien, kunt u [ een steunkaartje ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) creëren. Als er voldoende vraag is, overweegt [!DNL Adobe Commerce Optimizer] deze functionaliteit in een toekomstige release aan het product toe te voegen.
