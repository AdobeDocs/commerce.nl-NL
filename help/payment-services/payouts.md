---
title: Uitbetalingsrapport
description: Gebruik het rapport Uitbetalingen voor volledige transparantie met betrekking tot het bedrag van de betaling, het verwerkte volume en gedetailleerde rapportage over het transactieniveau voor financiële afstemming.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
feature: Payments, Checkout, Paas, Saas
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '1303'
ht-degree: 0%

---

# Uitbetalingsrapport

[!DNL Payment Services] for [!DNL Adobe Commerce] en [!DNL Magento Open Source] biedt uitgebreide rapportage zodat u een duidelijk overzicht kunt krijgen van de transacties, orders en betalingen in uw winkel.

Er zijn twee beschikbare meningen van de het rapportering van Uitbetalingen om u toe te laten om diepgaande informatie over al uw uitbetalingen te zien:

* [&#128279;](#payouts-data-visualization-view)**- Grafiek beschikbaar op het Huis van de Diensten van de Betaling dat een visuele vertegenwoordiging van samengevoegde bedragen per dag van de het rapportmening van Uitbetalingen is**
* **[het rapportmening van Uitbetalingen](#payouts-report-view)** - Rapport beschikbaar in Uitbetalingen die gedetailleerde uitbetalingsinformatie voor alle transacties toont

In de weergave Uitbetalingen worden uitgebreide uitbetalingsgegevens in één oogopslag weergegeven, zodat u volledig transparant kunt zijn over het bedrag van de betaling, het verwerkte volume en gedetailleerde rapportage over het transactieniveau voor financiële afstemming.

U kunt [&#x200B; betalingstransacties van de downloaduitbetaling &#x200B;](#download-transactions) in een .csv dossierformaat voor gebruik in bestaande boekhouding of ordebeheersoftware.

>[!NOTE]
>
>De rapporten van uitbetalingen tonen slechts orden die worden gevangen (betalingsactie wordt geplaatst aan [`Authorize and Capture` &#x200B;](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html?lang=nl-NL#set-payment-services-as-payment-method)) - of [&#x200B; duidelijk als `Invoiced` &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice).

## Weergave gegevensvisualisatie uitbetaling

De weergave voor de visualisatie van betalingsgegevens is beschikbaar in de startpagina van Betalingsservices. Het is een visuele vertegenwoordiging van de samengevoegde bedragen per dag van de gedetailleerde tabelvormige [&#x200B; mening van het rapport van Uitkeringen &#x200B;](#payouts-report-view).

Op _Admin_ sidebar, ga naar **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** om de grafiek van de gegevensvisualisatie van kredieten tegenover debits en de bewegende gemiddelden in tijd te zien.

![&#x200B; visualisatie van de gegevens van de Uitbetaling in Admin &#x200B;](assets/payouts-report.png){width="800" zoomable="yes"}

Klik **[!UICONTROL View Report]** om aan de gedetailleerde in tabelvorm [&#x200B; mening van het het rapport van Uitbetalingen &#x200B;](#payouts-report-view) te navigeren.

### Tijdschema voor transacties aanpassen

Standaard worden 30 dagen transacties weergegeven.

In de visualisatieweergave voor betalingsgegevens kunt u het tijdkader voor de uitbetalingstransacties die u wilt bekijken aanpassen door een datumbereik te selecteren:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. De weergave van de gegevensvisualisatie van Uitbetalingen is zichtbaar in de sectie Uitbetalingen.
1. Klik op het selectorfilter **[!UICONTROL Range]** .
1. Kies het toepasselijke datumbereik: 30 dagen, 15 dagen of 7 dagen.
1. Bekijk de transactiegegevens voor de opgegeven datums.

### Transactiegegevens

De transactiebedragen voor een geselecteerd datumbereik worden links van de weergave Betalingsgegevens weergegeven. De datums voor het geselecteerde datumbereik worden onder aan de weergave weergegeven. Als er op een bepaalde datum geen uitbetalingen zijn gedaan, wordt die datum niet weergegeven.

De weergave voor de visualisatie van betalingsgegevens bevat de volgende informatie.

| Gegevens | Beschrijving |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | Mate van bereik voor transacties in opgegeven tijdkader; gegevens op de Y-as (links) |
| Datumbereik | Datumbereik voor het opgegeven tijdframe; gegevens op de X-as (onder) |
| Krediet | Betalingen voor het opgegeven tijdsbestek |
| Debet | Debiteringen (terugbetalingen) voor het opgegeven tijdsbestek |
| Gemiddeld verplaatsen | Weergave van de gemiddelde uitbetaling voor elke datum in het opgegeven tijdsbestek |
| Netto voor bereik | Netto uitbetalingsbedrag voor het opgegeven tijdkader (bereik) |

## Weergave uitbetalingsrapport

De weergave van het betalingsrapport is beschikbaar in de weergave Uitbetalingen van betalingsservices. Deze bevat alle beschikbare informatie over de betalingen voor je winkel(s).

Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**&#x200B;om de gedetailleerde lijst van Uitbetalingen te zien rapportmening.

![&#x200B; de transacties van de Uitbetaling in Admin &#x200B;](assets/payouts-report-new.png){width="800" zoomable="yes"}

U kunt deze mening, per de secties in dit onderwerp vormen, om de gegevens het best voor te stellen u wenst te zien.

Zie gekoppelde Commerce-order- en transactie-id&#39;s, transactiebedragen, betalingsmethode per transactie en meer in dit rapport.

U kunt [&#x200B; betalingstransacties van de downloaduitbetaling &#x200B;](#download-transactions) in een .csv dossierformaat voor gebruik in bestaande boekhouding of ordebeheersoftware.

>[!NOTE]
>
>De gegevens in deze tabel worden standaard in aflopende volgorde (`DESC`) gesorteerd met de `TRANS DATE` . De `TRANS DATE` is de datum en het tijdstip waarop de transactie is gestart.

### Gegevensbron selecteren

In de het rapportmening van Uitbetalingen, kunt u de gegevensbron selecteren— **[!UICONTROL Live]** of **[!UICONTROL Sandbox]**—waarvoor u rapportresultaten wilt zien.

![&#x200B; de bronnen van Gegevens selectie &#x200B;](assets/datasource.png){width="300" zoomable="yes"}

Als _[!UICONTROL Live]_&#x200B;de geselecteerde gegevensbron is, kunt u rapportinformatie voor opslag in productiemodus zien. Als&#x200B;_[!UICONTROL Sandbox]_ de geselecteerde gegevensbron is, kunt u de opslag van rapportinformatie op zandbakwijze zien.

Gegevensbronselecties werken als volgt:

* Als u geen opslagruimten hebt die zich in de live modus bevinden, wordt de gegevensbronselectie standaard ingesteld op _[!UICONTROL Sandbox]_.
* Als u een of meerdere opslagruimten hebt in de live modus, wordt de gegevensbronselectie standaard ingesteld op _[!UICONTROL Live]_.
* De uitvoer van het rapport respecteert altijd de gegevensbronselectie.

U kunt als volgt de gegevensbron selecteren voor het rapport Betalingsstatus bestelling:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. Klik op **[!UICONTROL Data source]** en selecteer **[!UICONTROL Live]** of **[!UICONTROL Sandbox]** .

   De rapportresultaten regenereren op basis van de geselecteerde gegevensbron.

### Transacties weergeven

Standaard worden 30 dagen transacties weergegeven.

Het aantal rijen dat wordt geretourneerd in een zoekopdracht of dat wordt weergegeven in de standaard 30 dagen aan transacties, wordt boven het weergaveraster Uitbetalingen weergegeven naast het filter voor de kalenderkiezer voor Transactiedata.

De rol aan de linkerzijde en het recht om [&#x200B; informatie voor elke uitbetalingstransactie &#x200B;](#column-descriptions) in het dagelijkse rapport, met inbegrip van transactiedatum, referentie identiteitskaart, factuuraantal, en de details van de betalingsmethode te bekijken.

#### Tijdschema voor transacties aanpassen

In de weergave van het rapport Uitbetalingen kunt u het tijdpad voor de uitbetalingstransacties die u wilt bekijken aanpassen door specifieke datums in te voeren of een datumbereik te selecteren in de datumkiezer:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. Klik op het filter voor de kalenderkiezer van _[!UICONTROL Transaction dates]_.
1. Kies het toepasselijke datumbereik.
1. Bekijk de uitbetalingsstatussen in het raster voor de opgegeven datums.

### Kolommen tonen en verbergen

In de weergave van het rapport Uitbetalingen worden standaard de meeste beschikbare kolommen met informatie weergegeven. U kunt echter aanpassen welke kolommen u in het rapport ziet.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. Klik het _pictogram van de montages van de Kolom_ (![&#x200B; pictogram van kolommontages &#x200B;](assets/column-settings.png){width="20" zoomable="yes"}).
1. Als u wilt aanpassen welke kolommen u in het rapport ziet, schakelt u de kolommen in de lijst in of uit.

   In de weergave van het rapport Uitbetalingen worden direct alle wijzigingen weergegeven die u hebt aangebracht in het menu Kolominstellingen. De kolomvoorkeuren worden opgeslagen en blijven van kracht als u niet in de rapportweergave navigeert.

### Transacties downloaden

U kunt een CSV-bestand downloaden dat alle transacties bevat die zichtbaar zijn in het raster van de weergave Uitbetalingen.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Payouts]_>**[!UICONTROL View Report]**.
1. [&#x200B; pas timeframe van de datumwaaier voor uw transacties &#x200B;](#customize-transactions-timeframe) aan.
1. Klik het _pictogram van de Download_ (![&#x200B; het pictogram van de Download &#x200B;](assets/icon-download.png){width="20" zoomable="yes"}).

Uw uitbetalingstransacties worden gedownload in de CSV-indeling.

### Kolombeschrijvingen

Uitbetalingsrapporten bevatten de volgende informatie.

| Kolom | Beschrijving |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Betalingsaanbieder |
| [!UICONTROL Provider trans] | Transactie-id |
| [!UICONTROL Trans date] | Datum en tijdstip waarop de transactie is gestart |
| [!UICONTROL Type] | Transactietype—*[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br> zie [&#x200B; de types van Transactie &#x200B;](#transaction-types) voor meer informatie. |
| [!UICONTROL Status] | Huidige status van de transactie—*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | De code van de transactie die of Krediet (*CR*) of Debit (*DR.*) wijst |
| [!UICONTROL Reference ID] | Oorspronkelijke transactie-id waarvoor deze gebeurtenis verband houdt |
| [!UICONTROL Invoice] | Factuur-id (één per bestelling) van de transactie |
| [!UICONTROL Commerce order] | Commerce-order-id <br> <br> om verwante [&#x200B; orde info &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/order-management/orders/orders) te zien, klik identiteitskaart |
| [!UICONTROL Commerce trans] | Commerce-transactie-id |
| [!UICONTROL Pay method] | Het type van creditcard—*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]* - en bijbehorende kaartleverancier (zoals *Visa* of *MasterCard*) |
| [!UICONTROL TRANS AMT] | Bedrag van de transactie |
| [!UICONTROL CUR] | Valuta-eenheid voor transactiebedrag |
| [!UICONTROL PENDING] | Nog uit te betalen bedrag |
| [!UICONTROL CUR] | Valuta-eenheid voor het uitstaande bedrag |
| [!UICONTROL SELLER AMT] | Bedrag van aan of van een klant overgedragen middelen <br> <br> de middelen die zich van de verkopersrekening bewegen tonen een streepje (-) prefix. |
| [!UICONTROL CUR] | Valuta-eenheid voor het bedrag van de verkoper |
| [!UICONTROL PARTNER FEE] | Partner-kosten verbonden aan de transactie <br> <br> Middelen die zich uit de rekening van de partnervergoeding bewegen tonen een streepje (-) prefix. |
| [!UICONTROL CUR] | Valuta-eenheid voor partnergeld |
| [!UICONTROL PROV FEES] | Aan de transactie gekoppelde kosten <br> <br> de middelen die zich van de de vergoedingsrekening van de leverancier bewegen tonen een streepje (-) prefix. |
| [!UICONTROL CUR] | Valuta-eenheid voor leveranciersvergoeding |
| [!UICONTROL FEE %] | Percentage van het transactiebedrag dat als vergoeding in rekening wordt gebracht |
| [!UICONTROL FIXED FEE] | Vaste kosten provider |
| [!UICONTROL CHBK FEE] | Restitutiekosten voor de transactie <br> <br> het streepje van A (-) prefix wijst erop dat de terugkeringsvergoeding werd teruggedraaid. |
| [!UICONTROL CUR] | Valuta-eenheid voor terugboekingsvergoeding |
| [!UICONTROL HOLD AMT] | In de wachtstand gezet of uit de wachtstand gezet bedrag <br> <br> de streepjesprefix van A (-) wijst erop dat de middelen van de greep worden vrijgegeven. |
| [!UICONTROL CUR] | Valuta-eenheid voor het bedrag van de reserve |
| [!UICONTROL RECOUP AMT] | Bedrag dat van de terugvorderingsaccount is teruggeboekt <br> <br> de middelen die zich uit de terugwinningsrekening bewegen tonen een streepje (-) prefix. |
| [!UICONTROL CUR] | Valuta-eenheid voor het terugvorderingsbedrag |

### Transactietypen

Deze transactietypen kunnen in de uitbetalingstransacties worden vermeld.

| Rapport | Beschrijving |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Geld verplaatst tussen koper en verkoper voor een bestelling |
| [!UICONTROL AUTH] | Vergunningverlening en annulering van transacties |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | Terugboekingskosten en terugboekingskosten |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | Partner-kosten, betalings- en terugboekingstransacties |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | Winsten van bank- of verliesrekeningen |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
