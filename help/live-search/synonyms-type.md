---
title: Typen synoniemen
description: Één en 2 manier  [!DNL Live Search]  synoniemen breiden de definitie van sleutelwoorden uit.
exl-id: f5522428-c7cc-4627-a09b-d9148918c127
source-git-commit: 81bde302463a70e41318b494565694929703dff9
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Typen synoniemen

Met synoniemen in één en twee richtingen wordt de definitie van trefwoorden uitgebreid. Sommige zijn onderling verwisselbaar met het trefwoord, terwijl andere een subset van het trefwoord vertegenwoordigen.

## 2-wegs

Synoniemen in twee richtingen hebben dezelfde betekenis en retourneren dezelfde zoekresultaten. In het volgende voorbeeld is het eerste woord dat vet wordt weergegeven, het trefwoord dat wordt gebruikt in de catalogus, gevolgd door woorden met dezelfde betekenis als het oorspronkelijke trefwoord. U kunt een eenvoudig paar synoniemen in twee richtingen, of een ketting van veelvoudige synoniemen in twee richtingen voor het zelfde sleutelwoord tot stand brengen.

**jasje** ![&#x200B; bidirectionele selecteur &#x200B;](assets/btn-two-way.png) jas
**broek** ![&#x200B; 2-wegenkiezer &#x200B;](assets/btn-two-way.png) stapels ![&#x200B; 2-wegenkiezer &#x200B;](assets/btn-two-way.png) brousers

## Eenweg

Een eenrichtingssynoniem is een subset van een trefwoord, maar heeft een specifiekere betekenis. Capris en shorts zijn bijvoorbeeld broeken, maar niet alle planten zijn capris of korts. Een zoekopdracht naar broek omvat capris en korte broeken. Een zoekopdracht naar korte berichten retourneert echter geen capris.

**sweatshirt** ![&#x200B; Één-weg selecteur &#x200B;](assets/btn-one-way.png) hoodie
**broek** ![&#x200B; Eenwegs selecteur &#x200B;](assets/btn-one-way.png) capris ![&#x200B; Veelvoudige unidirectionele selecteur &#x200B;](assets/btn-multiple-one-way.png) calf-length-broek ![&#x200B; Veelvoudige unidirectionele selecteur &#x200B;](assets/btn-multiple-one-way.png) peddle handdupers

## Aanbevolen procedures

Houd rekening met de volgende aanbevolen procedures om de meeste van de synoniemen van [!DNL Live Search] te halen.

### &quot;Stop woorden&quot; vermijden

[!DNL Live Search] filtert algemene Engelse &#39;stop words&#39; uit synoniemen, zoals:

a, an, and, are, as, at, be, but, by, for, if, in, is, it, no, not, of, dusdanig, dat, hun, toen, daar, deze, zij, dit, aan, was,

Stopwoorden maken synoniemen niet zinvoller, maar verhogen de hoeveelheid gegevens die moet worden verwerkt.

### Gebruik van enkelvoudig en meervoudig

Het is niet nodig om zowel de enkelvoudige als de meervoudige vorm van een woord als een synoniem te definiëren. Als u een combinatie van enkelvoudige en meervoudige termen in uw catalogus hebt, zoekt u naar de juiste set producten. Als u bijvoorbeeld het woord &quot;pant&quot; in de productnaam gebruikt en een winkel zoekt naar &quot;broek&quot;, wordt de juiste set producten geretourneerd en wordt het woord &quot;pant&quot; voorgesteld als suggestie. In de mode-industrie en soms in de detailhandel wordt de term &quot;pant&quot; vaak gebruikt, hoewel de meervorm &quot;broek&quot; in sommige gebieden vaker wordt gebruikt. (Het woord &quot;pant&quot; verwijst technisch naar het deel van een kledingstuk dat één been bedekt. Daarom hebt u een &quot;broek&quot; nodig om beide benen te bedekken.)

### Consistentie

Zorg ervoor dat de terminologie in de catalogus wordt gebruikt. Houd er rekening mee dat er regionale verschillen in gebruik kunnen zijn, en soms verschillen binnen een bedrijfstak.

## Synoniemgedrag van meerdere woorden

Voor synoniemen met meerdere woorden beschouwt Commerce het synoniem als een woordgroep. Bijvoorbeeld, als u een bidirectionele synoniem **het dineren van de ruimtelijst ![&#x200B; 2-wegenkiezer &#x200B;](assets/btn-two-way.png)** keukenlijst **![&#x200B; 2-wegenkiezer &#x200B;](assets/btn-two-way.png)** eetlijst **creeert, dan zoekt Commerce over alle gebieden die aan het voorkomen van** eetbare ruimtelijst **of** worden geplaatst lijst **of** eetlijst **.**

Als geen synoniem wordt gecreeerd en een verkoopster zoekt naar **keukenlijst**, zoekt Commerce de termijnen overal in de doorzoekbare gebieden, zelfs over verschillende gebieden, bijvoorbeeld **lijst** op het naamgebied en **keuken** in het meta sleutelwoord.

Na het creëren van een synoniem, verandert het onderzoeksgedrag om de nauwkeurige uitdrukking **keukenlijst** te zoeken. Hierdoor kan het aantal resultaten afnemen, omdat alleen producten met de exacte zin worden weergegeven.

Als u de termijnen afzonderlijk wilt worden gezocht zoals voordien, kunt u [&#x200B; een steunkaartje &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) creëren. Als er voldoende vraag is, overweegt Commerce deze functionaliteit in een toekomstige release aan het product toe te voegen.
