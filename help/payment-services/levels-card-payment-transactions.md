---
title: Verwerking van niveau 2 en niveau 3
description: De verwerkingsniveaus van de betaling van de kaart binnen  [!DNL Payment Services]  transacties.
role: Admin
feature: Payments, Paas, Saas
exl-id: db8993fe-dd6f-48b5-9e7b-69a0f2e08552
source-git-commit: 870c2497a2d6dcfc4066c07f20169fc9040ae81a
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Verwerking van niveau 2 en niveau 3

[!DNL Payment Services] biedt geavanceerde mogelijkheden voor kaartverwerking om handelaren te helpen hun betalingstransacties te optimaliseren en de afwikkelingskosten te verlagen. Er zijn drie niveaus van kaartverwerking beschikbaar, elk met verschillende vereisten van transactiegegevens.

>[!CAUTION]
>
> [&#x200B; Fastlane &#x200B;](payments-options.md#fastlane-button) de orden omvatten Niveau 2/Niveau 3 geen gegevens, lijnpunten, en waardeverdeling.

## Gegevensvereisten per verwerkingsniveau

![&#x200B; het rapport van Transacties &#x200B;](assets/level-processing-details.png){width="500" zoomable="yes"}

[!DNL Payment Services] verzamelt deze gegevens en geeft een gedetailleerde rapportage van uw betalingstransacties.

## Beschikbare verwerkingsniveaus per kaartnetwerk

![&#x200B; de details van de Kaart &#x200B;](assets/cards-details-level-processing.png){width="500" zoomable="yes"}

Zie [&#x200B; betalingsverwerking &#x200B;](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} in de documentatie van de Ontwikkelaar van PayPal voor meer informatie.

### Niveau 1

Niveau 1 is de meest voorkomende, vereist minder informatie en brengt daarom in het algemeen hogere afwikkelingsvergoedingen met zich mee dan transacties die worden verwerkt met gegevens van niveau 2 of niveau 3, die doorgaans verband houden met zakelijke en aankoopkredietkaarten.

### Niveau 2 en niveau 3

[!DNL Payment Services] Merchants on Interchange Plus (IC++) komen in aanmerking voor verwerking op niveau 2/niveau 3 als zij aanvullende transactiedetails leveren aan kaartnetwerken en voldoen aan specifieke kwalificatiecriteria. Deze niveaus zijn met name gunstig voor handelaren die aanzienlijke aankopen of grote hoeveelheden bedrijfskaarten verwerken, aangezien zij tot aanzienlijke kostenbesparingen kunnen leiden. Gedetailleerde gegevens van niveau 2 of niveau 3 kunnen worden geleverd:

* Lagere verwerkingskosten en optimaliseer de totale kosten
* Fraude voorkomen, processorrisico verlagen
* Transactiebeveiliging verbeteren

Zie [&#x200B; wat IC++ is?](https://www.paypal.com/us/brc/article/what-is-interchange-plus-plus){target=_blank} in de documentatie voor ontwikkelaars van PayPal voor meer informatie.

## Betalingstransacties met kaart van niveau 2 en niveau 3 in [!DNL Payment Services]

Om in aanmerking te komen voor verwerking op niveau 2 of niveau 3, moeten handelaren de vorige informatie verzenden, hoewel het de kaartnetwerken zijn die uiteindelijk bepalen welk niveau een transactie in aanmerking komt bij de verwerking ervan.

Zie [&#x200B; Veelgestelde vragen over de verwerking van de Betaling &#x200B;](https://www.paypal.com/us/cshelp/article/ts2278?_ga=1.131773126.875104296.1712843492){target=_blank} in de ontwikkelaarsdocumentatie van PayPal voor meer informatie.

Verwerking op niveau 2 en niveau 3 is standaard uitgeschakeld voor [!DNL Payment Services] -handelaren op archiefniveau.

De verwerking van niveau 2 en niveau 3 zijn beschikbaar als u reeds IC++ tarifering gebruikt. Om deze eigenschap toe te laten kunt u dit via de [&#x200B; bevel-lijn Interface (CLI &#x200B;](configure-cli.md) doen.

>[!IMPORTANT]
>
>Neem contact op met uw accountmanager van [!DNL Payment Services] als u vragen hebt.
