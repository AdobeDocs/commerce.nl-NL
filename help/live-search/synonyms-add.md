---
title: Synoniemen toevoegen
description: Voeg  [!DNL Live Search]  synoniemen toe om reactie op onderzoeksverzoeken te verbeteren.
exl-id: 2dc535ea-35a3-45a8-8171-901005223cc9
source-git-commit: 6dcfd0a54e6a6814b7f5708e0c221452b8af4537
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Synoniemen toevoegen

Verhoog de betrokkenheid van klanten door uw eigen gekrulde lijst met [!DNL Live Search] synoniemen toe te voegen. [!DNL Live Search] kan maximaal 200 synoniemen per winkelweergave beheren.

![[!DNL Live Search] synonyms ](assets/synonym-workspace.png)

## Stap 1: Een synoniem toevoegen

1. In Admin, ga naar **Marketing** > SEO &amp; Onderzoek > **[!DNL Live Search]**.
1. Voor veelvoudige opslag, plaats **Reikwijdte** aan de [ opslagmening ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) waar de synoniem montages van toepassing zijn.
1. Klik de **Synoniemen** tabel.
1. Klik **toevoegen synoniemen** knoop.

## Stap 2: De synoniem door type bepalen

Volg de instructies voor het [ type van synoniem ](synonyms-type.md) dat u wilt tot stand brengen.

### Synoniem in twee richtingen

1. Accepteer de standaard **2-weg** optie.

   ![ voeg synoniem in twee richtingen ](assets/synonym-add-two-way.png) toe

1. Ga de **termijn of de uitdrukking 0&rbrace; van het Sleutelwoord &lbrace;in te passen.**
1. Ga de **termijn(en) in van de uitbreiding 0&rbrace; &lbrace;die u als synoniemen voor het sleutelwoord wilt toevoegen.** Scheid meerdere termen met een komma.
In dit voorbeeld is het trefwoord dat moet overeenkomen &#39;broek&#39; en zijn de uitbreidingstermijnen &#39;brousers, slacks&#39;.

   ![ In twee richtingen synoniem voorbeeld ](assets/synonym-add-two-way-example.png)

1. Wanneer volledig, klik **sparen**.
De reeks synoniemen verschijnt in de lijst met een tweerichtingspijl tussen elke termijn die betekent de termijnen onderling verwisselbaar zijn.

   ![ synoniem met twee richtingen ](assets/synonym-two-way.png)

### Eenvoudige synoniem

1. Klik het **unidirectionele** synoniem type.

   ![ voeg eenrichtingssynoniem ](assets/synonym-add-one-way.png) toe

1. Ga het **Sleutelwoord** in en **de voorwaarden van de Uitbreiding**. Scheid meerdere termen met een komma.

   ![ Eenwegs synoniem voorbeeld ](assets/synonym-add-one-way-example.png)

   In dit voorbeeld is het trefwoord &#39;broek&#39; en zijn de eenmalige uitbreidingstermen &#39;capris, peddle-push&#39; elk een subset van &#39;broek&#39;, maar met een specifieke betekenis.

1. Wanneer volledig, klik **sparen**.
De reeks synoniemen verschijnt in de lijst met een eenrichtingspijl die van de uitbreidingstermijnen aan het sleutelwoord richt om erop te wijzen de termijnen subsets van het sleutelwoord zijn. Een plusteken scheidt elke uitbreidingstermijn.

   ![ unidirectionele synoniem ](assets/synonym-one-way.png)

## Stap 3: Wijzigingen publiceren

1. Wanneer uw synoniemen volledig zijn, klik **publiceer veranderingen**.
1. Wacht maximaal twee uur totdat uw updates beschikbaar zijn in de winkel.

## Veldbeschrijvingen

| Veld | Beschrijving |
|--- |--- |
| [ Type ](synonyms.md) | Hiermee wordt bepaald of synoniemen dezelfde betekenis hebben als het trefwoord of een subset van het trefwoord zijn. Opties:<br /> 2-weg (gebrek) - Termen die de zelfde betekenis zoals het sleutelwoord hebben en de zelfde onderzoeksresultaten <br /> in één richting terugkeren - Termen die een ondergroep van het sleutelwoord zijn. Eenwegssynoniemen retourneren een uitgebreidere lijst met specifieke producten. |
| Trefwoord | Een woord dat vaak wordt gekoppeld aan een selectie producten in uw catalogus. |
| Uitbreiding | Aanvullende termen met dezelfde of een vergelijkbare betekenis als het trefwoord. |
