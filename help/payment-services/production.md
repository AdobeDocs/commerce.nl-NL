---
title: Laat  [!DNL Payment Services]  voor Productie toe
description: Voltooi het aan boord gaan proces door  [!DNL Payment Services]  voor productie toe te laten.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
feature: Payments, Checkout, Configuration, Install, Paas, Saas
source-git-commit: 870c2497a2d6dcfc4066c07f20169fc9040ae81a
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 0%

---

# [!DNL Payment Services] inschakelen voor productie

U kunt de dienst in productie zetten en het [&#x200B; onboarding proces &#x200B;](onboard.md) voltooien, per de stappen in dit onderwerp, na u:

* [!BADGE &#x200B; PaaS slechts &#x200B;]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."} [&#x200B; installeer &#x200B;](install.md) de uitbreiding van de Diensten van de Betaling
* [!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."} [&#x200B; vormt en verbindt &#x200B;](connect.md) uw instantie
* [&#x200B; Opstelling &#x200B;](sandbox.md) en [&#x200B; test &#x200B;](test-validate.md) uw zandbak

## [!DNL Payment Services] instellen als betalingsmethode

Nadat u [&#x200B; uw Diensten van Commerce &#x200B;](connect.md#configure-commerce-services) vormt en of [&#x200B; zandbak het testen &#x200B;](sandbox.md#enable-sandbox-testing) of [&#x200B; levende betalingen &#x200B;](#enable-live-payments) toelaat, moet u [!DNL Payment Services] als uw betalingsmethode plaatsen.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klik op **[!UICONTROL Enable Payment Services]**.

   Deze optie is zichtbaar als u [!DNL Payment Services] nog niet hebt geconfigureerd als betalingsmethode voor een of meer van uw websites.

   U wordt geleid aan het montagegebied in de mening van het Huis met de relevante uitgevouwen opties (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), waar u de [!DNL Payment Services] opties als uw [&#x200B; betalingsmethode &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/sales/payment-methods/payment-methods){target="_blank"} kunt toelaten.

1. Stel _[!UICONTROL General Configuration]_&#x200B;in op **[!UICONTROL Enable]**&#x200B;in `Yes` .
1. Stel **[!UICONTROL Payment Action]** voor zowel _[!UICONTROL Credit Card Fields]_&#x200B;als&#x200B;_[!UICONTROL PayPal payment buttons]_ in op een van de volgende opties:

   | Instelling | Beschrijving |
   |---|---|
   | `Authorize` | Hiermee geeft u de aankoop goed en houdt u de middelen in de wacht. De hoeveelheid wordt pas opgevraagd wanneer deze door de handelaar wordt &quot;gevangen&quot;. |
   | `Authorize and Capture` | hecht zijn goedkeuring aan de aankoop en de &quot;opname&quot; van de fondsen door de handelaar. |

   >[!IMPORTANT]
   >
   >[!DNL Payment Services] ondersteunt gedeeltelijke vastleggingen. Een handelaar kan delen van een bestelling gedeeltelijk vastleggen (factureren). U kunt bijvoorbeeld elk item afzonderlijk vastleggen of één item nu en de rest later.

1. Klik op **[!UICONTROL Save]**.
1. Klik op **[!UICONTROL Go to Payment Services]** om terug te gaan naar [!DNL Payment Services] Home.
1. [&#x200B; ontruim uw geheime voorgeheugen &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html?lang=nl-NL).

   Het ontruimen zou na elke configuratieverandering moeten worden gedaan.

Zie [&#x200B; vormen  [!DNL Payment Services]](configure-admin.md) voor meer informatie over het vormen van de Gebieden van de Kaart en PayPal betalingsknopen.

## Volledige merchant aan boord

De volgende stap om je winkels in staat te stellen om live te gaan met betalingsservices is het voltooien van live onboarding.

De Diensten van de betaling verstrekt [**Geavanceerde** (volledig gesteund) en **Standaard** (Uitdrukkelijke Controle) betalingsopties &#x200B;](../payment-services/payments-options.md#standard-vs-advanced-payments-experience) en onboarding stromen, afhankelijk van het land waarin u en uw aangewezen betalingservaring werkt.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klik op **[!UICONTROL Live onboarding]**.

   Deze optie is zichtbaar als u nog niet live on boarding for [!DNL Payment Services] hebt voltooid.

1. In _selecteer uw land_ modaal, selecteer het land waarvan u werkt.

   De Diensten van de betaling verleent volledige steun voor alle betalingsopties in [&#x200B; vijf landen &#x200B;](../payment-services/introduction.md#availability) momenteel. Betalingsdiensten bieden Express Checkout-mogelijkheden (een subset van betalingsopties) voor alle andere landen die in de landenlijst zijn opgenomen.

   Het land u van de lijst kiest zal de betalingsopties bepalen, en op het instappen stroom - [&#x200B; Geavanceerd &#x200B;](#advanced-onboarding) (volledig gesteund) of [&#x200B; Standaard &#x200B;](#standard-onboarding) (Uitdrukkelijke Controle)-beschikbaar aan u.

>[!TIP]
>
> Als u eenmaal een instapkaartoptie hebt gekozen en doorgaat (Standaard of Geavanceerd), moet u het instappen opnieuw voltooien om een upgrade uit te voeren of de oorspronkelijke selectie te verkleinen.

### Geavanceerd instapniveau

Deze instapkaartstroom is beschikbaar voor handelaren in [&#x200B; volledig gesteunde landen &#x200B;](../payment-services/introduction.md#availability).

Nadat het land is geselecteerd:

1. In modaal die verschijnt, uitgezocht **Geavanceerd**.

   Voor de **Standaard** optie, ga aan de [&#x200B; Standaard op het instappen stroom &#x200B;](#standard-onboarding) te werk.

1. Klik **verdergaan**.
1. Ga verder met de PayPal-flow voor de volledig ondersteunde Advanced onboarding-methode, waarbij u uw Paypal-accountgegevens gebruikt (niet uw gegevens van de sandboxaccount) _of_ zich aanmeldt voor een nieuwe Paypal-account.

>[!IMPORTANT]
>
>**Geavanceerd op het instappen** vereist handelaren aan [&#x200B; de betiteling van verzoekbetalingen &#x200B;](#request-payments-entitlement-from-adobe) om levende op het instappen toe te laten.

### Standaard aan boord

Deze Standaard op het instappen stroom is beschikbaar voor handelaren in beschikbare landen waarvoor [&#x200B; slechts de Uitdrukkelijke steun van de Controle &#x200B;](../payment-services/introduction.md#availability) wordt verstrekt.

Nadat het land is geselecteerd:

1. In het _modaal van de Overeenkomst van de Diensten van de Betaling_ dat verschijnt, klik de **overeenkomst van de Diensten van de Betaling** verbinding om de overeenkomst van de Diensten van de Betaling van Adobe Commerce te bekijken.
1. In de _overeenkomst van de Diensten van de Betaling_ modaal, klik **ik keur** goed.
1. Ga verder met de PayPal-flow voor Express Checkout bij het instappen, gebruik uw PayPal-accountgegevens (niet de gegevens van uw sandboxaccount) of meld u aan voor een nieuw PayPal-account.

>[!IMPORTANT]
>
>[&#x200B; het Betalen van Apple en creditcardgebieden &#x200B;](../payment-services/payments-options.md) zijn niet beschikbaar voor **Standaard op het instappen**.

## E-mailadres bevestigen

1. Ga op de zijbalk Beheerder naar **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   De knop _[!UICONTROL Live onboarding]_&#x200B;is niet meer zichtbaar en u ziet een tekstvak &quot;[!UICONTROL Live payments pending]&quot;.

   In dat tekstvak wordt je mogelijk ook gevraagd je e-mailadres bij PayPal te bevestigen om de inboeking te voltooien.

1. Als je wordt gevraagd je e-mailadres te bevestigen, controleer dan je e-mail op het bevestigingsbericht dat je van PayPal hebt ontvangen en klik je om je e-mailadres te bevestigen.
1. Ga op de zijbalk Beheerder naar **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** .
1. Vernieuw het browservenster.

   Wanneer je PayPal-inboarding is goedgekeurd, wordt een melding weergegeven dat je betalingssysteem zich in de sandboxmodus bevindt en geen live betalingen verwerkt.

   >[!IMPORTANT]
   >
   >Als u de toestemming van [!DNL Payment Services] for [!DNL Adobe Commerce] en [!DNL Magento Open Source] voor het verwerken van uw betalingen intrekt (in de instellingen van uw Paypal-account), kunnen bestellingen in uw winkel niet worden verwerkt door [!DNL Payment Services] . Op de homepage van Betalingsdiensten verschijnt een waarschuwing over de ingetrokken toestemming.

## Betalingsrechten aanvragen bij Adobe

Om uw opslag toe te laten om levend te gaan, verzoek betalingsrechten van Adobe (voor [&#x200B; Geavanceerd op instapniveau slechts &#x200B;](#advanced-onboarding)):

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klik op **[!UICONTROL Get Live Payments]** in uw [!DNL Payment Services] startpunt.

   ![&#x200B; Rechten van het Verzoek &#x200B;](assets/request-entitlements.png){width="500" zoomable="yes"}

1. Vul het formulier in.
1. Een lid van het verkoopteam zal contact met u opnemen.

Alternatief, kunt u om betalingsrechten van Adobe bij [&#x200B; zaken.adobe.com verzoeken &#x200B;](https://business.adobe.com/nl/resources/payment-services.html).

>[!IMPORTANT]
>
>**Levend onboarding** is niet toegankelijk tot de betalingsrechten zijn goedgekeurd.

## Prijsniveau configureren

Krijg uw [!DNL Payment Services] _Merchant identiteitskaart_:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klik in de weergave Home op **[!UICONTROL Settings]** . Zie [&#x200B; Huis &#x200B;](payments-home.md) voor meer informatie.
1. Selecteer vereiste _identiteitskaart van de Merchant_ en leg het voor aan uw vertegenwoordiger van de Verkoop, die de correcte tarifering zal vormen.

Zie [&#x200B; Niveau 2 en niveau 3 verwerking &#x200B;](levels-card-payment-transactions.md) voor meer informatie over betalingstransacties.

## Live betalingen inschakelen

A _productie commerciële identiteitskaart_ wordt auto-geproduceerd en bevolkt in de [&#x200B; configuratie &#x200B;](configure-admin.md). Wijzig of wijzig deze id niet.

Live betalingen inschakelen:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klik in het Home op **[!UICONTROL Settings]** rechtsboven op de pagina. Zie [&#x200B; Huis &#x200B;](payments-home.md) voor meer informatie.
1. In de _[!UICONTROL General Configuration]_-sectie ingesteld op **[!UICONTROL Payment mode]**`Production` .
1. Klik op **[!UICONTROL Save]**.
1. [&#x200B; ontruim uw geheime voorgeheugen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/cache-management){target="_blank"}.

   >[!IMPORTANT]
   >
   >Als u de cache niet wist, kunnen klanten tijdens het afrekenen geen PayPal-betalingsopties zien.

Als u teruggaat naar [!DNL Payment Services] Home, wordt het bericht voor de betalingsmodus Sandbox niet meer weergegeven omdat u nu live betalingen verwerkt.

Zie [&#x200B; vormen in Admin &#x200B;](configure-admin.md) voor de opties van de erfenisconfiguratie.

>[!IMPORTANT]
>
>Als u de toestemming van [!DNL Payment Services] voor het verwerken van uw betalingen intrekt (in de instellingen van uw Paypal-account), kunnen bestellingen in uw winkel niet worden verwerkt door [!DNL Payment Services] . Als je de betalingsverwerking opnieuw wilt inschakelen, moet je het instappen opnieuw voltooien. Op de homepage van Betalingsdiensten verschijnt een waarschuwing over de ingetrokken toestemming.

## Test in productie

Het wordt ten zeerste aanbevolen Betalingen in productie te testen, met echte creditcards en banken, voordat u deze functionaliteit aan kopers beschikbaar maakt.

Zie [&#x200B; Testen en bevestigen &#x200B;](test-validate.md) voor meer informatie.
