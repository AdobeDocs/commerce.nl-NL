---
title: Verwerking van niveau 2 en niveau 3
description: De verwerkingsniveaus van de betaling van de kaart binnen  [!DNL Payment Services]  transacties.
role: Admin
feature: Payments
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# Verwerking van niveau 2 en niveau 3

Er zijn drie niveaus van kaartverwerking beschikbaar door [!DNL Payment Services]:

* Niveau 1 is de meest voorkomende, vereist minder informatie en brengt daarom in het algemeen hogere afwikkelingsvergoedingen met zich mee dan transacties die worden verwerkt met gegevens van niveau 2 of niveau 3, die doorgaans verband houden met zakelijke en aankoopkredietkaarten.

* Met niveau 2 en niveau 3 kunnen [!DNL Payment Services] klanten met een interchange-plus-prijs (IC++) die een groot deel van de aanschafkaart- of bedrijfskaarttransacties accepteren, een lagere verwerkingssnelheid krijgen doordat [!DNL Payment Services] meer informatie over een transactie kan verzenden. Als de transactie in aanmerking komt, volgens de vereisten van het kaartnetwerk, kan de handelaar een lagere verwerkingstarief voor een bepaalde transactie ontvangen.

>[!NOTE]
>
>Prijzen van niveau 2 en niveau 3 gelden alleen voor Visa- en MasterCard-transacties. American Express biedt alleen prijsniveau 2. Detectie biedt geen prijzen van niveau 2 of 3. Zie [ betalingsverwerking ](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank}  in de documentatie van de Ontwikkelaar van PayPal voor meer informatie.

Zie [ wat IC++ is?](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank}  in de documentatie voor ontwikkelaars van PayPal voor meer informatie.

De verwerkingsgegevens van niveau 2 en niveau 3 stellen handelaren in staat hun IC++-prijzen te verlagen als zij aanvullende informatie verstrekken over de aankoop die het processorrisico vermindert en nuttige aspecten biedt:

* Grote klanten betalen minder door deze verwerkingsgegevens op te geven.

* Klanten hebben minder kans op frauduleuze situaties, aangezien de bestellingen meer informatie bevatten.

Nochtans, bepalen de kaartnetwerken, zoals Visa en Mastercard, uiteindelijk of een transactie voor niveau 2 of niveau 3 verwerking in aanmerking komt:

* Gegevens van niveau 2 bevatten aanvullende informatie, zoals het belastingbedrag voor de order of de code van de klant of het inkoopordernummer.

* Gegevens van niveau 3 zijn gedetailleerdere informatie over de verkoop, die helpt in aanmerking te komen voor nog lagere wisselkoersen dan niveau 2. Gegevens van niveau 3 bevatten informatie zoals een beschrijving van het gekochte item, de aangekochte hoeveelheid eenheden, de maateenheid voor de bestelde items en andere specifieke details.

[!DNL Payment Services] verzamelt deze gegevens en geeft een gedetailleerde rapportage van uw betalingstransacties.

## Betalingstransacties met kaart van niveau 2 en niveau 3 in [!DNL Payment Services]

Om in aanmerking te komen voor verwerking op niveau 2 of niveau 3, moeten handelaren de vorige informatie verzenden, hoewel het de kaartnetwerken zijn die uiteindelijk bepalen welk niveau een transactie in aanmerking komt bij de verwerking ervan.

Zie [ Veelgestelde vragen over de verwerking van de Betaling ](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank}  in de ontwikkelaarsdocumentatie van PayPal voor meer informatie.

Verwerking op niveau 2 en niveau 3 is standaard uitgeschakeld voor [!DNL Payment Services] -handelaren op archiefniveau.

De verwerking van niveau 2 en niveau 3 zijn beschikbaar als u reeds IC++ tarifering gebruikt. Om deze eigenschap toe te laten kunt u dit via de [ bevel-lijn Interface (CLI ](configure-cli.md) doen.

>[!IMPORTANT]
>
>Neem contact op met uw accountmanager van [!DNL Payment Services] als u vragen hebt.
