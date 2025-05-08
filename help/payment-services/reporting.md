---
title: Rapportage
description: Gebruik het rapport Transacties om de snelheid van de transactievergunning en transactietrends zichtbaar te maken.
role: User
level: Intermediate
exl-id: dd1d80f9-5983-4181-91aa-971522eb56fa
source-git-commit: 4482c1f93a424c73497b88c707d0ab93a694c957
workflow-type: tm+mt
source-wordcount: '1270'
ht-degree: 0%

---

# Rapportage

[!DNL Payment Services] for [!DNL Adobe Commerce] en [!DNL Magento Open Source] biedt uitgebreide rapportage zodat u een duidelijk overzicht kunt krijgen van de transacties, orders en betalingen in uw winkel.

![ het rapport van Transacties ](assets/transactions-report.png){width="700" zoomable="yes"}

Het Transactierapport biedt inzicht in transactievergunningpercentages en negatieve transactietrends zodat u de gezondheid van uw opslag effectief kunt controleren en om het even welke transactiekwesties op voorhand kunt identificeren en behandelen.

Zie afzonderlijke transacties voor in de winkel geplaatste orders en hun betalingsmethoden, resultaat, responscodes voor betalingen en meer.

De in het transactieverslag verstrekte informatie is uitsluitend bestemd voor commercieel gebruik. Deel deze informatie niet met klanten of andere potentiële fraudeurs. Transactiegegevens kunnen worden gebruikt om beveiligingscontroles te omzeilen of om orders te plaatsen die tot doorbelasting leiden.

U kunt het rapport Transacties downloaden in de .csv-bestandsindeling voor gebruik in bestaande software voor boekhouding of orderbeheer.

>[!NOTE]
>
>U kunt geen financiële rapporten bekijken als u niet [ hebt geregistreerd en Actieve wijze ](production.md#enable-live-payments) voor [!DNL Payment Services] geactiveerd.

## Transactierapportweergave

De weergave van het Transactierapport is beschikbaar in de weergave Transacties van Betalingsdiensten. Het bevat alle beschikbare informatie over transacties voor je winkel(s).

Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**&#x200B;om de gedetailleerde het rapportmening van Transacties in de tabelvorm te zien.

![ het rapportmening van Transacties ](assets/transactions-report-view.png){width="800" zoomable="yes"}

U kunt deze mening, per de secties in dit onderwerp vormen, om de gegevens het best voor te stellen u wenst te zien.

Zie de gekoppelde Commerce-order en PayPal-transactie-id&#39;s, transactiebedragen, betalingsmethode per transactie en meer in dit rapport.

Niet alle betalingsmethoden bieden dezelfde mate van informatie. Met creditcardtransacties worden bijvoorbeeld reacties, AVS- en CCV-codes en de laatste vier cijfers van de kaart in het Transactierapport verschaft. PayPal-betalingsknoppen doen dat niet.

U kunt [ transacties ](#download-transactions) in een .csv dossierformaat voor gebruik in bestaande boekhouding of ordebeheersoftware downloaden.

>[!WARNING]
>
> Het transactierapport bevat geen gegevens die buiten [!DNL Payment Services] zijn vastgelegd.

### Gegevensbron selecteren

In de het rapportmening van Transacties, kunt u de gegevensbron selecteren— **[!UICONTROL Live]** of **[!UICONTROL Sandbox]**—waarvoor u rapportresultaten wilt zien.

![ de bronnen van Gegevens selectie ](assets/datasource.png){width="300" zoomable="yes"}

Als _[!UICONTROL Live]_&#x200B;de geselecteerde gegevensbron is, kunt u rapportinformatie voor uw opslag zien die [!DNL Payment Services] in productiemodus gebruiken. Als&#x200B;_[!UICONTROL Sandbox]_ de geselecteerde gegevensbron is, kunt u rapportinformatie voor uw zandbakwijze zien.

Gegevensbronselecties werken als volgt:

* Als u geen opslagruimten hebt die [!DNL Payment Services] in de productiemodus gebruiken, wordt de gegevensbronselectie standaard ingesteld op _[!UICONTROL Sandbox]_.
* Als u opslagruimten hebt (een of meerdere opslagruimten) die [!DNL Payment Services] in de productiemodus gebruiken, wordt de gegevensbronselectie standaard ingesteld op _[!UICONTROL Live]_.
* De uitvoer van het rapport respecteert altijd de gegevensbronselectie.

U kunt als volgt de gegevensbron voor uw [!UICONTROL Transactions] -rapport selecteren:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klik op **[!UICONTROL Data source]** en selecteer **[!UICONTROL Live]** of **[!UICONTROL Sandbox]** .

   De rapportresultaten regenereren op basis van de geselecteerde gegevensbron.

### Tijdskader voor datums aanpassen

In de weergave van het Transactierapport kunt u de tijdlijn aanpassen van de transacties die u wilt weergeven door specifieke datums te selecteren. Standaard worden 30 dagen transacties in het raster weergegeven.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klik op het filter voor de kalenderkiezer van **[!UICONTROL Transaction dates]** .
1. Kies het toepasselijke datumbereik.
1. Geef de transacties voor de opgegeven datums weer in het raster.

### Rapportgegevens filteren

In de weergave van het Transactierapport kunt u de resultaten filteren die u wilt bekijken door filtercriteria te selecteren.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klik op de kiezer **[!UICONTROL Filter]** .
1. Schakel de optie _[!UICONTROL Transaction Result]_&#x200B;in of uit om alleen de resultaten van geselecteerde ordertransacties te bekijken.
1. Schakel de opties van _[!UICONTROL Payment Method]_&#x200B;in om de rapportresultaten voor het type betaling te bekijken dat voor de transactie wordt gebruikt.
1. Schakel de _[!UICONTROL Payment Detail]_-opties in of uit om aanvullende informatie weer te geven over het gebruikte type betaling, indien beschikbaar.
1. Ga het Min van de Orde van de a __ of _Max Bedrag van de Orde_ in om rapportresultaten binnen die waaier van het ordebedrag te zien.
1. Voer een _[!UICONTROL Order ID]_&#x200B;in om te zoeken naar een specifieke transactie.
1. Introduceer _[!UICONTROL Card Last Four]_&#x200B;om naar een specifieke creditcard of bankpas te zoeken.
1. Voer een _[!UICONTROL Customer ID]_&#x200B;in om alle transacties van een bepaalde klant weer te geven.
1. Voer _[!UICONTROL Customer Email]_&#x200B;in om transacties voor die e-mail te filteren.
1. Klik op **[!UICONTROL Hide filters]** om het filter te verbergen.

### Kolommen tonen en verbergen

Het rapport van Transacties toont alle beschikbare kolommen van informatie door gebrek. U kunt, echter, aanpassen welke kolommen u in uw rapport ziet.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klik het **[!UICONTROL Column settings]** pictogram ![ pictogram van de kolommontages ](assets/column-settings.png){width="20" zoomable="yes"}.
1. Om aan te passen welke kolommen die u in het rapport ziet, controleer of uncheck kolommen in de lijst.

   In het rapport Transacties worden direct alle wijzigingen weergegeven die u hebt aangebracht in het menu Kolominstellingen. De kolomvoorkeuren worden opgeslagen en blijven van kracht als u niet in de rapportweergave navigeert.

### Rapportgegevens bijwerken

De het rapportmening van Transacties toont een _[!UICONTROL Last updated]_&#x200B;timestamp die de laatste tijd toont dat de rapportinformatie werd bijgewerkt. Door gebrek, worden het rapportgegevens van Transacties auto-verfrist om de drie uur.

U kunt ook manueel dwingen verfrist zich van de rapportgegevens om de meest bijgewerkte rapportinformatie te zien.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Klik _verfrissen zich_ pictogram (![ verfrissen pictogram ](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   De gegevens van het Transactierapport worden vernieuwd, er verschijnt een *[!UICONTROL Update complete]* bevestiging en de meest recente informatie staat in het raster.

### Transacties downloaden

U kunt een CSV-bestand downloaden met alle transacties die zichtbaar zijn in het raster van de transactieweergave, of u nu de standaardtransacties van 30 dagen bekijkt of een aangepast tijdframe.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. Als u transacties voor een timeframe buiten de laatste 30 dagen wilt zien, [ aanpassen de timeframe van de datumwaaier voor uw statussen ](#customize-dates-timeframe).
1. Klik het _pictogram van de Download_ ![ download ](assets/icon-download.png){width="20" zoomable="yes"}.

Uw transacties worden gedownload in de indeling .csv.

### Kolombeschrijvingen

Transactierapporten bevatten de volgende informatie.

| Kolom | Beschrijving |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | Commerce orde ID (bevat slechts waarden voor succesvolle transacties en is leeg voor verworpen transacties) <br> <br> om verwante [ orde info ](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/order-management/orders/orders){target="_blank"} te zien, klik identiteitskaart |
| [!UICONTROL PayPal Transaction ID] | Transactie-id verstrekt door de betalingsaanbieder; bevat alleen waarden voor geslaagde transacties en bevat een streepje voor geweigerde transacties. U kunt op deze id klikken om de pagina met PayPal-transactiegegevens te openen. |
| [!UICONTROL Customer ID] | Commerce-klant-id van een bestelling <br> <br> zie [ onderwerp van klantinfo ](https://experienceleague.adobe.com/nl/docs/commerce-admin/customers/customer-accounts/account-create){target="_blank"} voor meer informatie. |
| [!UICONTROL Transaction Date] | Tijdstempel van transactiedatum |
| [!UICONTROL Payment Method] | Soort betaling gebruikt voor de transactie met informatie over merk en type kaart. Zie [ kaarttypes ](https://developer.paypal.com/docs/api/orders/v2/#definition-card_type) voor meer informatie; beschikbaar voor versies 1.6.0 van de Diensten van de Betaling en nieuwer |
| [!UICONTROL Payment Detail] | Bevat aanvullende informatie over het type betaling dat voor de transactie wordt gebruikt, indien beschikbaar. |
| [!UICONTROL Card Last Four] | Laatste vier cijfers van de voor de transactie gebruikte krediet- of debetkaarten |
| [!UICONTROL Result] | Het resultaat van de transactie—*[!UICONTROL OK]* (geslaagde transactie), *[!UICONTROL Rejected by Payment Provider]* (geweigerd door PayPal), *[!UICONTROL Rejected by Bank]* (geweigerd door de bank die de kaart heeft uitgegeven) |
| [!UICONTROL Response Code] | Foutcode die reden voor afwijzing weergeeft van de betalingsaanbieder of de bank. Zie de lijst met mogelijke antwoordcodes en beschrijvingen voor [`Rejected by Bank` status ](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) en [`Rejected by Payment Provider` status ](https://developer.paypal.com/api/rest/reference/orders/v2/errors/) . |
| [!UICONTROL AVS Code] | Adres Verification Service-code; de responsgegevens van de processor voor betalingsverzoeken. Zie [ lijst van mogelijke codes en beschrijvingen ](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) voor meer informatie. |
| [!UICONTROL CVV Code] | De code van de de controlewaarde van de kaart voor krediet en debetkaarten; zie [ lijst van mogelijke codes en beschrijvingen ](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) voor meer informatie. |
| [!UICONTROL Amount] | Volgorde van transactie |
| [!UICONTROL Currency] | Valuta gebruikt voor order in transactie |
| [!UICONTROL Type] | [ de actie van de Betaling ](../payment-services/production.md#set-payment-services-as-payment-method) voor transactie— `Authorize` of `Authorize and Capture` |

### Foutresponscodes

De _kolom van de Code van de Reactie_ toont een specifieke fout of succescode met betrekking tot de transactie. Enkele veelvoorkomende foutcodes die u kunt zien, zijn:

* `PAYMENT_DENIED` - De transactie is door PayPal geweigerd omdat het vermoeden bestond dat er sprake was van fraude.
* `INTERNAL_SERVER_ERROR` - De transactie is door PayPal geweigerd en er is een PayPal-serverfout opgetreden. De transactie kan opnieuw worden geprobeerd.
* `INSTRUMENT_DECLINED` - De klant is door PayPal geweigerd op basis van een geselecteerde betalingsmethode. Transactie kan opnieuw worden uitgevoerd met een andere betalingsmethode.
* `9500` - De transactie is door de gekoppelde bank geweigerd omdat het vermoeden bestond dat het om fraude ging.
* `5120` - De transactie is door de geassocieerde bank geweigerd omdat de klant onvoldoende middelen had voor de betaling.
* `5650` - de transactie werd verworpen door de bijbehorende bank omdat de bank sterke klantenauthentificatie ([ 3DS ](security.md#3ds) vereist).

Gedetailleerde foutresponscodes voor mislukte transacties zijn beschikbaar voor transacties die jonger zijn dan 1 juni 2023. Gedeeltelijke rapportgegevens worden weergegeven voor transacties die vóór 1 juni 2023 hebben plaatsgevonden.
