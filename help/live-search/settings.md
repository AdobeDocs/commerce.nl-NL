---
title: Instellingen
description: Vorm montages voor de  [!DNL Live Search]  dienst.
exl-id: 6387a365-7e23-4023-95ac-27908164d81c
source-git-commit: 70ff444afbe7ddf41e966e479e03975a02f4e10f
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Instellingen

Gebruik de *werkruimte van Montages* om de waaiers en de intervallen van het prijsfacet en de standaardtaal voor de index te vormen.

Prijsfacetten geven het aantal prijsgroepen aan en de verdeling van de prijswaarden tussen deze groepen.

De taalinstelling vertelt de [!DNL Live Search] -service welke taal moet worden verwacht bij het schrijven van de index.

![ Montages ](assets/settings.png)

## Prijsbeperking

U kunt het aantal groepen voor het prijsbereik opgeven en aangeven hoe de prijswaarden eronder worden verdeeld. Elke prijsklasse overlapt de vorige groep met één. Vijf groepen met een interval van 20 maken bijvoorbeeld de volgende prijsbereiken: 0-20, 20-40, 40-60, 60-80 en >80. Als de catalogus niet genoeg producten bevat om alle gedefinieerde bereiken te vullen, wordt de weergave van de beschikbare groepen dienovereenkomstig aangepast. Bijvoorbeeld: 0-20, 60-80, >80.

1. In Admin, ga **Marketing** > *SEO &amp; Onderzoek* > **[!DNL Live Search]**.
1. Op de **1&rbrace; werkruimte van Montages &lbrace;onder** Vergemakkelijking van de Prijs *, doe het volgende:*
   * Ga het **Aantal selecties** in, of prijsgroeperingen om beschikbaar te zijn. Met [!DNL Live Search] 4.4.0 kunt u maximaal 100 prijsgroepen definiëren. Eerdere versies maakten 50 prijsgroepen mogelijk.
   * Ga de **waarde van het Interval**, of prijswaaier voor elke groep in. De maximumwaarde is 40.000.000.
1. Klik **sparen**.

   Het duurt ongeveer 15 minuten voordat de bijgewerkte instellingen beschikbaar zijn in de winkel.

### Veldomschrijvingen

| Veld | Beschrijving |
|--- |--- |
| Aantal selecties | Hiermee geeft u het aantal groepen voor prijsbereik op dat als zoekfilters in de winkel kan worden gebruikt. Standaardwaarde: 8, maximale waarde: 100 (vanaf [!DNL Live Search] 4.4.0) |
| Interval, waarde | Hiermee geeft u het prijsinterval voor elke groep op. Vijf selecties met een intervalwaarde van 20 maken bijvoorbeeld vijf groepen van 0-20, 20-40, 40-60, 60-80 en >80. Standaardwaarde: 5, Maximumwaarde: 40.000.000 |

## Taal

Met de taalinstelling weet [!DNL Live Search] welke taal moet worden verwacht bij het lezen van de catalogus en het schrijven van de index.

Talen hebben verschillende sets regels voor grammatica: hoe woorden worden gescheiden, werkwoordtactieken en woordformulieren, bijvoorbeeld.
Het plaatsen van de Taal zorgt ervoor dat de correcte reeks regels op het indexerende mechanisme worden toegepast.

Stel de taalinstelling in op de primaire taal van de catalogus. Wanneer u de taal van de index wijzigt, kan het 5 tot 60 minuten duren om de wijziging in de winkelruimte weer te geven, afhankelijk van de grootte en de complexiteit van de catalogus.

| Taal | Code |
|----|----|
| Arabisch | ar |
| Armeens | hy |
| Baskisch | eu |
| Bengali | bn |
| Braziliaans | pt-br |
| Bulgaars | bg |
| Catalaans | ca |
| Chinees (vereenvoudigd) | zh-cn |
| Chinees (traditioneel) | zh-tw |
| Tsjechisch | cs |
| Deens | da |
| Nederlands | nl |
| Engels | en |
| Ests | et |
| Fins | fi |
| Frans | fr |
| Galicisch | gl |
| Duits | de |
| Grieks | el |
| Hindi | hi |
| Hongaars | hu |
| Indonesische | id |
| Iers | ga |
| Italiaans | het |
| Japans (Katakana) | ja |
| Koreaans | ko |
| Lets | lv |
| Litouws | lt |
| Noors | nee |
| Perzisch | fa |
| Portugees | pt |
| Roemeens | ro |
| Russisch | ru |
| Sorani | ku |
| Spaans | es |
| Zweeds | sv |
| Turks | tr |
| Thai | th |
