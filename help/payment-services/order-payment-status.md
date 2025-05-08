---
title: Betalingsstatusrapport bestelling
description: Gebruik het rapport Betalingsstatus bestellen om de betalingsstatus van uw bestellingen beter te kunnen bekijken en om eventuele problemen op te sporen.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
feature: Payments, Checkout, Orders, Paas, Saas
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '2045'
ht-degree: 0%

---

# Betalingsstatusrapport bestelling

[!DNL Payment Services] voor [!DNL Adobe Commerce] en [!DNL Magento Open Source] biedt u uitvoerige rapportering aan zodat u een duidelijke mening van de 3&rbrace; transacties van uw opslag [&#128279;](reporting.md), orden, en betalingen kunt krijgen.

Er zijn twee beschikbare rapportageweergaven voor de betalingsstatus van bestellingen waarmee u snel de betalingsstatus van uw bestellingen kunt bekijken:

* [&#128279;](#order-payment-status-data-visualization-view)**- Grafiek beschikbaar op het Huis van de Diensten van de Betaling van de Orde dat een visuele vertegenwoordiging van samengevoegde betalingsstatussen per dag van de mening van het het statusrapport van de Betalingsstatus van de Orde is**
* **[de mening van het de statusrapport van de Bestelling van de Bestelling](#order-payment-status-report-view)** - Rapport beschikbaar in de betalingsstatus van de Orde die gedetailleerde betaling toont, gefactureerd, verscheept, teruggave, en geschilstatus voor alle transacties

De weergave van de betalingsstatus van bestellingen helpt u eenvoudig te begrijpen waar een specifieke bestelling zich binnen de bestelling bevindt om de kasstroom te verwerken. Met deze rapporten kunt u snel bestellingen bekijken (op basis van hun betalingsstatus en betalingsdatum) en mogelijke problemen identificeren.

U kunt de betalingsstatussen van de Orde [&#128279;](#download-order-payment-statuses) in een .csv dossierformaat voor gebruik in bestaande boekhouding of de software van het ordebeheer downloaden.

>[!NOTE]
>
>U kunt geen financiële rapporten bekijken als u niet [ hebt geregistreerd en Actieve wijze ](production.md#enable-live-payments) voor [!DNL Payment Services] geactiveerd.

## Weergave voor visualisatie betalingsstatusgegevens bestellen

De weergave voor de visualisatie van betalingsstatusgegevens voor bestellingen is beschikbaar in de Home Betalingsservices. Het is een visuele vertegenwoordiging van de samengevoegde betalingsstatussen per dag van de gedetailleerde tabelvormige [ mening van het het statusrapport van de Bestelling ](#order-payment-status-report-view).

Op _Admin_ sidebar, ga naar **Verkoop** > **de Diensten van de Betaling** > _Orders_ om de gegevens visualisatie [ grafiek van betalingsstatussen ](#statuses-information) te zien.

![ visualisatie van de gegevens van de Uitbetaling in Admin ](assets/orderpayment-dataviz.png){width="800" zoomable="yes"}

Klik **[!UICONTROL View Report]** om aan de gedetailleerde tabelvormige [ mening van het het vooruitbetalingsstatusrapport van de Orde ](#order-payment-status-report-view) te navigeren.

### Tijdskader voor statussen aanpassen

Standaard worden betalingsstatussen van 30 dagen weergegeven.

In de weergave Betalingsstatus bestellen kunt u het tijdpad voor de betalingsstatussen die u wilt bekijken aanpassen door een datumbereik te selecteren:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. De de visualisatiemening van de de betalingsstatus van de Orde is zichtbaar in de _sectie van Orden_.
1. Klik op het selectorfilter **[!UICONTROL Range]** .
1. Kies het toepasselijke datumbereik: 30 dagen, 15 dagen of 7 dagen.
1. Geef de statusinformatie voor de opgegeven datums weer.

### Statusinformatie

De betalingsstatussen voor een geselecteerd datumbereik worden links van de weergave voor betalingsstatus van bestelling weergegeven. De datums voor het geselecteerde datumbereik worden onder aan de weergave weergegeven. Als er op een bepaalde datum geen orders waren, wordt die datum niet weergegeven.

De weergave voor de visualisatie van betalingsstatusgegevens voor bestellingen bevat de volgende informatie.

| Gegevens | Beschrijving |
| ------------ | -------------------- |
| [!UICONTROL Orders] | Mate van bereik voor orders in opgegeven tijdframe; gegevens op de Y-as (links) |
| Datumbereik | Datumbereik voor het opgegeven tijdframe; gegevens op de X-as (onder) |
| Geautoriseerd | Orde is geautoriseerd |
| Opname aangevraagd | Vastleggen aangevraagd voor bestelling |
| Vastleggen bevestigd | Opname van bestelling voltooid |
| Gedeeltelijk vastleggen | Gedeeltelijk vastgelegde bestelling |
| Vastleggen mislukt | Vastleggen van volgorde mislukt |
| Gestemd | Volgorde ongeldig |

## Overzicht van betalingsstatus van bestelling

De weergave van het rapport Betalingsstatus bestellen is beschikbaar in de weergave Home of Payment Services. Het omvat gedetailleerde statussen - betaling, gefactureerd, verscheept, terugbetaling, geschil, en meer-voor alle transacties.

Op _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**&#x200B;om de gedetailleerde lijst van het de statusrapport van de Betalingsstatus van de Orde te zien.

![ de betalingstatustransacties van de Orde in Admin ](assets/orders-report-data.png){width="800" zoomable="yes"}

U kunt deze mening, per de secties in dit onderwerp vormen, om de gegevens het best voor te stellen u wenst te zien.

U kunt [ betalingstransacties van de downloaduitbetaling ](#download-order-payment-statuses) in een .csv dossierformaat voor gebruik in bestaande boekhouding of ordebeheersoftware.

>[!NOTE]
>
>De gegevens in deze tabel worden standaard in aflopende volgorde (`DESC`) gesorteerd met de `TRANS DATE` . De `TRANS DATE` is de datum en het tijdstip waarop de transactie is gestart.

### Updates van de betalingsstatus

Bepaalde betalingsmethoden vereisen een periode om de betaling af te vangen. [!DNL Payment Services] detecteert nu de hangende status van een betalingstransactie in een bestelling door:

* `pending capture` transacties synchroon detecteren
* `pending capture` Transacties asynchroon controleren

>[!NOTE]
>
>Als de status van betalingstransacties in behandeling in een bestelling wordt vastgesteld, worden per ongeluk verzendopdrachten voorkomen als de betaling nog niet is ontvangen. Dit kan gebeuren bij e-check- en PayPal-transacties.

#### Synchrone detectie van opnametransacties in behandeling

Detecteer automatisch vastgelegde transacties in de status `Pending` en voorkom dat orders de status `Processing` invoeren wanneer een dergelijke transactie wordt gedetecteerd.

Tijdens het uitchecken door de klant of wanneer een beheerder een factuur maakt voor een eerder geautoriseerde betaling, detecteert [!DNL Payment Services] automatisch transacties in een `Pending` -status die worden uitgevoerd en wordt de bijbehorende bestellingen naar `Payment Review` -status verplaatst.

#### Asynchrone bewaking van opnametransacties in behandeling

Detecteren wanneer een vastlegtransactie in behandeling de status `Completed` krijgt, zodat handelaren de verwerking van de desbetreffende order kunnen hervatten.

Om ervoor te zorgen dat dit proces naar behoren werkt, moeten handelaren een nieuwe uitsnijdtaak configureren. Zodra de baan wordt gevormd om automatisch te lopen, worden geen andere interventies verwacht van de handelaar.

Zie [ cron banen ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) vormen. Nadat de nieuwe taak is geconfigureerd, wordt deze elke 30 minuten uitgevoerd om updates op te halen voor bestellingen die de status `Payment Review` hebben.

Verkopers kunnen de bijgewerkte betalingsstatus controleren via de rapportweergave voor betalingsstatus van bestelling.

### In het rapport gebruikte gegevens

[!DNL Payment Services] gebruikt bestelgegevens en combineert deze met geaggregeerde betalingsgegevens uit andere bronnen (waaronder PayPal) voor zinvolle en zeer nuttige rapporten.

Bestelgegevens worden geëxporteerd en blijven in de betalingsservice staan. Wanneer u [ verandert of ordestatus ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-status#custom-order-status) toevoegt of [ uitgeeft een opslagmening ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-views#edit-a-store-view), [ opslag ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/setup/store-details#store-information), of websitenaam, dat het gegeven met betalingsgegevens wordt gecombineerd en het rapport van de de betalingsstatus van de Orde wordt bevolkt met gecombineerde info.

Er zijn twee stappen in dit proces:

1. De index wordt veranderd gegeven of `ON SAVE` (telkens als de ordesinfo of opslaginfo wordt veranderd) of `BY SCHEDULE` (op een pre-gevormde kroonprogramma), afhankelijk van hoe het in [ het Beheer van de Index ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) in Admin wordt gevormd.

   Standaard vindt gegevensindexatie plaats `ON SAVE` . Dit houdt in dat wanneer iets verandert in de volgorde, de status van de order, de winkelweergave, de winkel of de website, het opnieuw indexeren onmiddellijk plaatsvindt.

1. De geïndexeerde gegevens worden verzonden naar de betalingsdienst, die vervolgens het rapport over de betalingsstatus van de betalingsopdracht invult.

De enige gegevens die voor rapportagedoeleinden worden geëxporteerd en gesorteerd, zijn gegevens die worden gebruikt in het rapport betreffende de betalingsstatus van de betalingsopdracht.

>[!NOTE]
>
>De gegevens in deze tabel worden standaard in aflopende volgorde (`DESC`) gesorteerd met de `ORDER DATE` . De `ORDER DATE` is de tijdstempel op de datum waarop de bestelling is gemaakt.

#### Gegevens exporteren configureren

Hoewel het opnieuw indexeren standaard plaatsvindt in de modus `ON SAVE` , wordt u aangeraden de index in de modus `BY SCHEDULE` uit te voeren. De `BY SCHEDULE` -index wordt uitgevoerd volgens een uitsnijdschema van één minuut en alle gewijzigde gegevens worden binnen twee minuten na elke gegevenswijziging weergegeven in het statusrapport van uw bestelling. Deze geplande herindexering helpt u om het even welke druk op uw opslag te verminderen, vooral als u een groot volume van inkomende orden hebt, omdat het op een programma gebeurt (niet aangezien elke orde wordt geplaatst).

U kunt de indexwijze veranderen— `ON SAVE` of `BY SCHEDULE`— [ in Admin ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode).

Leren hoe te om de gegevensuitvoer te vormen, zie [ bevel-lijn configuratie ](configure-cli.md#configure-data-export).

### Gegevensbron selecteren

In de mening van het het statusrapport van de Betalingsstatus van de Orde, kunt u de gegevensbron selecteren— **[!UICONTROL Live]** _ of **[!UICONTROL Sandbox]**—waarvoor u rapportresultaten wilt zien.

![ de bronnen van Gegevens selectie ](assets/datasource.png){width="300" zoomable="yes"}

Als _[!UICONTROL Live]_&#x200B;de geselecteerde gegevensbron is, kunt u rapportinformatie voor uw opslag zien die [!DNL Payment Services] in productiemodus gebruiken. Als&#x200B;_[!UICONTROL Sandbox]_ de geselecteerde gegevensbron is, kunt u rapportinformatie voor zandbakwijze zien.

Gegevensbronselecties werken als volgt:

* Als u geen opslagruimten hebt die [!DNL Payment Services] in de live modus gebruiken, wordt de gegevensbronselectie standaard ingesteld op _[!UICONTROL Sandbox]_.
* Als u opslagruimten hebt (een of meerdere) die [!DNL Payment Services] in de live modus gebruiken, wordt de gegevensbronselectie standaard ingesteld op _[!UICONTROL Live]_.
* De uitvoer van het rapport respecteert altijd de gegevensbronselectie.

U kunt als volgt de gegevensbron voor uw [!UICONTROL Order Payment Status] -rapport selecteren:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Orders]** > **[!UICONTROL View Report]**.
1. Klik op het selectorfilter _[!UICONTROL Data source]_&#x200B;en selecteer **[!UICONTROL Live]**&#x200B;of **[!UICONTROL Sandbox]**.

   De rapportresultaten regenereren op basis van de geselecteerde gegevensbron.

### Tijdschema voor datums van bestellingen aanpassen

In de weergave van het rapport Betalingsstatus bestellen kunt u de tijdlijn aanpassen van de statusresultaten die u wilt bekijken door specifieke datums te selecteren. Standaard worden de betalingsstatussen van 30 dagen voor bestellingen weergegeven in het raster.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klik op het filter voor de kalenderkiezer van _[!UICONTROL Order dates]_.
1. Kies het toepasselijke datumbereik.
1. Bekijk de betalingsstatussen voor de bestelling voor de opgegeven datums in het raster.

### Rapportgegevens filteren

In de weergave Betalingsstatusrapport bestellen kunt u de resultaten filteren die u wilt bekijken door filtercriteria te selecteren.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klik op de kiezer **[!UICONTROL Filter]** .
1. Wissel de _opties van de Status van het Betalen_ om rapportresultaten voor slechts geselecteerde status van de ordebetaling te zien.
1. Het rapport van de mening resulteert binnen een waaier van het ordebedrag door a _[!UICONTROL Min Order Amount]_&#x200B;of _ [!UICONTROL Max Order Amount_] in te gaan.
1. Klik op **[!UICONTROL Hide filters]** om het filter te verbergen.

### Kolommen tonen en verbergen

Het rapport Betalingsstatus bestelling toont standaard alle beschikbare kolommen met informatie. U kunt, echter, aanpassen welke kolommen u in uw rapport ziet.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klik het _pictogram van de montages van de Kolom_ (![ pictogram van kolommontages ](assets/column-settings.png){width="20" zoomable="yes"}).
1. Als u wilt aanpassen welke kolommen u in het rapport ziet, schakelt u de kolommen in de lijst in of uit.

   Het rapport Betalingsstatus bestellen toont direct alle wijzigingen die u hebt aangebracht in het menu Kolominstellingen. De kolomvoorkeuren worden opgeslagen en blijven van kracht als u niet in de rapportweergave navigeert.

### Statussen weergeven

De weergave van het rapport Betalingsstatus bestelling bevat uitgebreide informatie over de betalingsstatus van elke bestelling.

Standaard worden de betalingsstatussen van 30 dagen voor bestellingen weergegeven in het raster.

De rol aan de linkerzijde en het recht om [ informatie van de de ordebetaling ](#column-descriptions) te bekijken, met inbegrip van ordedatum, geoorloofde datum, gefactureerd, verscheept, betaal status, en meer.

Het aantal rijen dat wordt geretourneerd in een zoekopdracht of dat wordt weergegeven in de standaardbetalingsstatus van 30 dagen van een bestelling, wordt boven het weergaveraster voor betalingsstatus van bestelling weergegeven naast het filter Kalender voor orderdatums.

#### Betaalstatus

In de statuskolom Betalen wordt de huidige status van een betaling weergegeven. Een betaling van `Capture failed` geeft een status van een rood waarschuwingsbericht weer en een betaling van `Voided` geeft een status van een grijs waarschuwingsbericht weer.

#### Terugbetalingsstatus

In de statuskolom Restitutie wordt de huidige status voor elke restitutie weergegeven. Een betaling van `Capture failed` geeft een status van een rood waarschuwingsbericht weer en een betaling van `Voided` geeft een status van een grijs waarschuwingsbericht weer.

### Rapportgegevens bijwerken

De weergave van het rapport Betalingsstatus bestellen toont een _[!UICONTROL Last updated]_-tijdstempel dat de laatste keer weergeeft dat de rapportgegevens zijn bijgewerkt. Standaard worden de gegevens in het rapport Betalingsstatus van bestelling elke drie uur automatisch vernieuwd.

U kunt ook handmatig afdwingen dat de gegevens in het rapport Betalingsstatus van bestelling worden vernieuwd om de meest actuele rapportgegevens te zien.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Klik _verfrissen zich_ pictogram (![ verfrissen pictogram ](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   De gegevens van het rapport met de betalingsstatus van de bestelling worden vernieuwd, er verschijnt een *[!UICONTROL Update complete]* -bevestiging en de meest recente informatie staat in het raster.

### Geschillen bekijken

Je kunt geschillen over bestellingen van je winkel bekijken en naar het PayPal Resolution Center navigeren om actie te ondernemen vanuit het statusrapport voor bestellingen.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Navigeer naar de map **[!UICONTROL Disputes column]** .
1. Bekijk om het even welke geschillen voor een specifieke orde en zie [ de geschillenstatus ](#order-payment-status-information).
1. De details van het meningsgeschil van het [ Centrum van de Resolutie van PayPal ](https://www.paypal.com/us/cshelp/article/what-is-the-resolution-center-help246) door de verbinding van identiteitskaart van het geschil te klikken die met _PP-D_ begint.
1. Indien nodig passende maatregelen nemen voor het geschil.

   Klik op de kolomkop [!UICONTROL Disputes] als u conflicten met de status wilt sorteren.

### Betalingsstatus van bestellingen downloaden

U kunt een CSV-bestand downloaden met alle statussen die zichtbaar zijn in het weergaveraster voor betalingsstatus van bestelling, of u nu de standaardstatus van 30 dagen bekijkt of een aangepast tijdframe.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Als u statussen voor een timeframe buiten de laatste 30 dagen wilt zien, [ aanpassen de timeframe van de datumwaaier voor uw statussen ](#customize-dates-timeframe).
1. Klik het _pictogram van de Download_ (![ downloadpictogram ](assets/icon-download.png){width="20" zoomable="yes"}).

De betalingsstatus van uw bestelling wordt gedownload in de indeling .csv.

### Kolombeschrijvingen

Betalingsstatusrapporten voor bestellingen bevatten de volgende informatie.

| Kolom | Beschrijving |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Commerce order ID <br> <br> om verwante [ orde info ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/orders){target="_blank"} te zien, klik identiteitskaart |
| [!UICONTROL Order Date] | Tijdstempel van besteldatum |
| [!UICONTROL Authorized Date] | Tijdstempel van betalingsvergunning |
| [!UICONTROL Order Status] | Huidige Commerce [ ordestatus ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-status){target="_blank"} |
| [!UICONTROL Invoiced] | Factuurstatus van bestelling—*[!UICONTROL No]*, *[!UICONTROL Partial]* of *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Verzendstatus van bestelling—*[!UICONTROL No]*, *[!UICONTROL Partial]* of *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Totaalbedrag van de beschikking |
| [!UICONTROL Cur] | Valutatype van order |
| [!UICONTROL Pay Status] | Status van betaling voor een specifieke bestelling |
| [!UICONTROL Paid Amt] | Op bestelling betaald bedrag |
| [!UICONTROL Cur] | Valutatype van het op een bestelling betaalde bedrag |
| [!UICONTROL Refund Status] | Status van een terugbetaling op een bestelling (zoals informatie uit geretourneerde bedragen, RMA&#39;s en kredietmemo&#39;s)—   *[!UICONTROL Requires refund]* , *[!UICONTROL Refund requested]* , *[!UICONTROL Refunded]* , *[!UICONTROL Refund failed]* of *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Totaal terugbetaald bedrag voor een bestelling |
| [!UICONTROL Cur] | Valutatype van het bedrag dat voor een order wordt terugbetaald |
| [!UICONTROL Disputes] | Status van een geschil over een bestelling (informatie uit geschillen en terugbetalingen)—*[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]* of *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | Betalingsmethode gebruikt in Commerce-transactie voor een bestelling |
| [!UICONTROL Website] | Website van waaruit de bestelling is geplaatst |
| [!UICONTROL Store] | Winkel van waaruit de bestelling is geplaatst |
| [!UICONTROL Store View] | Winkelweergave van waaruit de bestelling is geplaatst |
