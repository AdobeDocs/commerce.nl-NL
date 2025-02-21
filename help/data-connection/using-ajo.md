---
title: Adobe Journey Optimizer gebruiken om een afgebroken winkelwagentje te verzenden
description: Leer hoe u Adobe Journey Optimizer kunt gebruiken om een verlaten winkelwagentje-e-mail te verzenden.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 0%

---

# Adobe Journey Optimizer gebruiken om een e-mailbericht voor verlaten winkelwagentje te verzenden

Leer hoe u een persoonlijke e-mail of melding voor opnieuw contact kunt verzenden als een winkelwagentje of browsersessie is verlaten. In dit artikel gebruikt u gegevens die zijn gegenereerd van klanten die een aantal producten en categorieën hebben weergegeven, die een product gebruiken of tijd op een pagina hebben doorgebracht.

## Welke gegevens moet ik overwegen te gebruiken?

Bouw een verlaten karretje, doorblader e-mail, of bericht gebruikend gegevens van opslag en achterkantoorgebeurtenissen.

| Gegevenstypen | Storefront-gegevens (gedragsgebeurtenissen) | Back Office-gegevens (server-side gebeurtenissen) |
|---|---|---|
| **Definitie** | Klik of acties die klanten op uw site uitvoeren. | Informatie over de levenscyclus en details van elke bestelling (verleden en huidig). |
| **Gebeurtenissen die door Adobe Commerce** worden gevangen | [ pageView ](https://experienceleague.adobe.com/en/docs/commerce/data-connection/event-forwarding/events#pageview) <br>[ productPageView ](https://experienceleague.adobe.com/en/docs/commerce/data-connection/event-forwarding/events) <br>[ addToCart ](https://experienceleague.adobe.com/en/docs/commerce/data-connection/event-forwarding/events#addtocart) <br>[ openCart ](https://experienceleague.adobe.com/en/docs/commerce/data-connection/event-forwarding/events#opencart) <br>[ startCheckout ](https://experienceleague.adobe.com/en/docs/commerce/data-connection/event-forwarding/events#startcheckout) <br>[ completeCheckout ](https://experienceleague.adobe.com/en/docs/commerce/data-connection/event-forwarding/events#completecheckout) | [ orderPlaced ](https://experienceleague.adobe.com/en/docs/commerce/data-connection/event-forwarding/events-backoffice#orderplaced) <br>[ de geschiedenis van de Orde ](https://experienceleague.adobe.com/en/docs/commerce/data-connection/fundamentals/connect-data#send-historical-order-data) |

### Wat hebben andere klanten bereikt?

Adobe [!DNL Commerce]-klanten hebben aanzienlijke zakelijke effecten bereikt door persoonlijke beëindigingscampagnes te implementeren met Adobe [!DNL Commerce] , Adobe [!DNL Journey Optimizer] en Adobe [!DNL Real-Time CDP] .

Een wereldwijde, multibrand-kledinghandelaar bereikte:

- 1.9x conversie bij klikken vanuit nieuwe campagnes
- 57% verhoging van de inkomsten uit wegvluchten in het buitenland
- 41% stijging van de conversiecijfers van herplaatsingscampagnes
- Meer dan 1000 nieuwe kopers per week ingeschakeld

Een wereldwijd drankenbedrijf bereikte:

- 36% e-mailopeningstarieven voor nieuwe taken
- 21% toename van klikdoorslag
- 8,5% verhoging van de omrekeningskoers
- 89% van de opnieuw gestarte gepensioneerden zet zich om

## Laten we beginnen

In dit specifieke geval is het maken van een verlaten e-mailbericht met een winkelwagentje aan de hand van gegevens uit uw [!DNL Commerce] -exemplaar en het verzenden ervan naar Adobe [!DNL Journey Optimizer] .

### Wat is Adobe Journey Optimizer?

[ Adobe Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) helpt u de handelservaring voor uw kopers personaliseren. U kunt Journey Optimizer bijvoorbeeld gebruiken om geplande marketingcampagnes te maken en te leveren, zoals wekelijkse promoties voor een detailhandel, of een verlaten winkelwagentje-e-mail genereren als een klant een product aan een winkelwagentje heeft toegevoegd maar het afrekenproces vervolgens niet heeft voltooid.

In dit onderwerp leert u een verlaten wagentje-e-mail te bouwen door naar een `checkout` gebeurtenis te luisteren die van uw [!DNL Commerce] instantie wordt geproduceerd en op die gebeurtenis in Journey Optimizer te antwoorden.

>[!IMPORTANT]
>
>Voor demonstratiedoeleinden gebruikt u uw [!DNL Commerce] sandbox-omgeving, zodat u de productiegebeurtenisgegevens niet verwatert met de gegevens van de storefront- en back office-gebeurtenis die u naar Experience Platform verzendt.

### Vereisten

Voordat u met deze stappen begint, moet u controleren of:

- U bent ingericht om Adobe [!DNL Journey Optimizer] te gebruiken. Als u niet zeker bent, raadpleegt u uw systeemintegrator of ontwikkelingsteam dat projecten en omgevingen beheert.
- U [ installeerde ](install.md) en [ vormde ](connect-data.md) de [!DNL Data Connection] uitbreiding in [!DNL Commerce].
- U [ bevestigde ](connect-data.md#confirm-that-event-data-is-collected) dat uw [!DNL Commerce] gebeurtenisgegevens bij de rand van Experience Platform aankomen.

## Stap 1: Een gebruiker maken in de sandboxomgeving van [!DNL Commerce]

Maak een gebruiker in uw sandbox-omgeving en bevestig dat die gebruikersaccountgegevens in Experience Platform worden weergegeven. Zorg ervoor dat de e-mail die u hebt opgegeven geldig is, zoals die later in deze sectie wordt gebruikt om de verlaten e-mail met het winkelwagentje te verzenden.

1. Meld u aan of maak een account in uw [!DNL Commerce] sandbox-omgeving.

   ![ Teken binnen aan uw testrekening ](assets/sign-in-account.png){width="700" zoomable="yes"}

   Als de extensie [!DNL Data Connection] is geïnstalleerd en geconfigureerd, worden deze accountgegevens als een profiel naar de Experience Platform verzonden.

1. Controleer of de gegevens van uw gebruikersaccount worden weergegeven in de sectie **[!UICONTROL Profile]** van Experience Platform.

   Ga naar **[!UICONTROL Profiles]** in de Adobe Experience Platform. Klik op **[!UICONTROL Detail]** in het profiel om het profiel weer te geven dat u hebt gemaakt.

   ![ bevestigt profiel ](assets/check-event-profile.png){width="700" zoomable="yes"}

## Stap 2: Gebeurtenissen weergeven in Journey Optimizer

In uw [!DNL Commerce] zandbakmilieu, activeer gebeurtenissen op uw storefront door productpagina&#39;s te bekijken, punten toe te voegen aan een kar, en diverse andere activiteiten te voltooien die een verkoopster zou uitvoeren. Bevestig vervolgens dat deze gebeurtenissen naar Journey Optimizer stromen.

1. Start [ Adobe Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. Selecteer **[!UICONTROL Profiles]** .
1. Stel **[!UICONTROL Identity namespace]** in op `Email` .
1. Stel de **[!UICONTROL Identity value]** in op uw e-mailadres.
1. Selecteer uw profiel en selecteer vervolgens de tab **[!UICONTROL Events]** .

   ![ de gebeurtenisdetails van de Controle ](assets/check-event-details.png){width="700" zoomable="yes"}

   Zoek naar de `commerce.checkouts` -gebeurtenis en controleer de payload van de gebeurtenis:

   ```json
   "personID": "84281643067178465783746543501073369488", 
   "eventType": "commerce.checkouts", 
   "_id": "4b41703f-e42e-485b-8d63-7001e3580856-0", 
   "commerce": { 
       "cart": {}, 
       "checkouts": { 
           "value": 1 
       } 
   ```

   Zoals u kunt zien, bevat de volledige gebeurtenislading rijke gebeurtenisgegevens. In de volgende sectie configureert u gebeurtenissen in Journey Optimizer om te luisteren naar en te reageren op de gebeurtenis `commerce.checkouts` die is gegenereerd vanuit uw [!DNL Commerce] storefront.

## Stap 3: gebeurtenissen configureren in Journey Optimizer

Configureer twee gebeurtenissen in Journey Optimizer: de ene gebeurtenis luistert naar de `commerce.checkouts` -gebeurtenis van Commerce en de andere gebeurtenis is een eenvoudige time-outgebeurtenis die wacht tot een bepaalde hoeveelheid tijd is verstreken voordat een verlaten wagente-mail wordt geactiveerd.

### Een listenergebeurtenis maken

1. Start [ Adobe Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. Klik op **[!UICONTROL Configurations]** onder de sectie **[!UICONTROL Administration]** van het linkerdeelvenster.

1. Klik in de **[!UICONTROL Events]** -tegel op **[!UICONTROL Manage]** .

   ![ de Configuratie van de Gebeurtenis van Journey Optimizer ](assets/ajo-config.png){width="700" zoomable="yes"}

1. Klik op de pagina **[!UICONTROL Events]** op **[!UICONTROL Create Event]** .

1. Stel de gebeurtenis als volgt in in de rechternavigatie:

   1. Stel de waarde **[!UICONTROL Name]** in op: `firstname_lastname_checkout` .
   1. Stel **[!UICONTROL Type]** in op **[!UICONTROL Unitary]** .
   1. Plaats **[!UICONTROL Event id typ]e** aan **[!UICONTROL Rule based]**.
   1. Plaats **[!UICONTROL Schema]** aan uw [!DNL Commerce] [ schema ](update-xdm.md).
   1. Selecteer **[!UICONTROL Fields]** om de pagina van **[!UICONTROL Fields]** te openen. Selecteer vervolgens de velden die nuttig zijn voor deze gebeurtenis. Selecteer bijvoorbeeld alle velden onder **[!UICONTROL Product list items]** , **[!UICONTROL Commerce]** , **[!UICONTROL eventType]** en **[!UICONTROL Web]** .
   1. Klik op **[!UICONTROL OK]** om de geselecteerde velden op te slaan.
   1. Klik in het veld **[!UICONTROL Event id condition]** . Maak vervolgens een voorwaarde: `eventType` is gelijk aan `commerce.checkouts` AND `personalEmail.address` is gelijk aan het e-mailadres dat u hebt gebruikt toen u het profiel in de vorige sectie maakte.

      ![ Journey Optimizer plaatste Voorwaarde ](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. Klik op **[!UICONTROL OK]**.
   1. Klik op **[!UICONTROL Save]** om de gebeurtenis op te slaan.

### Een time-outgebeurtenis maken

1. Maak een gebeurtenis in Journey Optimizer zoals u dat eerder hebt gedaan.

1. Stel de gebeurtenis als volgt in in de rechternavigatie:

   1. Stel de waarde **[!UICONTROL Name]** in op: `firstname_lastname_timeout` .
   1. Stel **[!UICONTROL Type]** in op **[!UICONTROL Unitary]** .
   1. Stel **[!UICONTROL Event id type]** in op **[!UICONTROL Rule based]** .
   1. Plaats **[!UICONTROL Schema]** aan uw [!DNL Commerce] [ schema ](update-xdm.md).
   1. Stel de opties **[!UICONTROL Schema]** , **[!UICONTROL Fields]** en **[!UICONTROL Event id condition]** in op dezelfde waarde als hierboven.
   1. Klik op **[!UICONTROL Save]** om de gebeurtenis op te slaan.

Met deze twee gevormde gebeurtenissen, creeer een reis die een verlaten kart e-mail verzendt.

## Stap 4: Een afrekenreis maken

Maak een reis die luistert naar de `commerce.checkouts` -gebeurtenis en verstuurt vervolgens een verlaten winkelwagente-mail nadat een bepaalde hoeveelheid tijd is verstreken.

1. In Journey Optimizer, selecteer **[!UICONTROL Journeys]** onder **J[!UICONTROL OURNEY MANAGEMENT]**.
1. Klik op **[!UICONTROL Create Journey]**.
1. Geef de naam van uw reis op.
1. Klik op **[!UICONTROL OK]** om de rit op te slaan.
1. Zoek in de linkernavigatie onder de sectie **[!UICONTROL EVENTS]** naar de uitcheckgebeurtenis die u eerder hebt gemaakt: `firstname_lastname_checkout` en sleep deze naar het canvas.

   >[!TIP]
   >
   >Als u dubbelklikt op de gebeurtenis, wordt deze automatisch toegevoegd aan het canvas.

1. Zoek naar de timeout-gebeurtenis en voeg deze toe aan het canvas.
1. Dubbelklik op de time-outgebeurtenis.

   1. Selecteer in de sectie **[!UICONTROL Timeout]** het selectievakje **[!UICONTROL Define the event time]** .
   1. Typ `1` en `Minute` in het veld **[!UICONTROL Wait for]** .
   1. Schakel het selectievakje **[!UICONTROL Set a timeout path]** in.

   Met deze time-outconfiguratie activeert een winkelier die een afhandeling uitvoert maar de bestelling niet binnen één minuut voltooit, deze time-outvertakking. In een echte productieomgeving zou je dit voor een langere periode instellen, bijvoorbeeld 24 uur.

1. Voeg in de linkernavigatie onder **[!UICONTROL ACTIONS]** de handeling **[!UICONTROL Email]** toe aan de time-outvertakking. Uw reis zou als het volgende moeten kijken:

   ![ Journey Optimizer Canvas ](assets/ajo-canvas.png){width="700" zoomable="yes"}

### Een verlaten winkelwagentje maken

Maak een verlaten wagentje-e-mail die wordt verzonden wanneer een verlaten wagentje wordt ontdekt.

1. Dubbelklik tijdens de hierboven gemaakte reis op het pictogram **[!UICONTROL Email]** op het canvas.

1. Volg de [ stappen ](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) in de gids van Journey Optimizer om tot de verlaten kart e-mail te leiden.

U hebt nu een reis in Journey Optimizer die luistert naar de `commerce.checkouts` -gebeurtenis van uw [!DNL Commerce] -winkel en een verlaten e-mailbericht met een winkelwagentje dat wordt verzonden nadat een bepaalde periode is verstreken. In het volgende gedeelte ziet u hoe u de reis kunt testen.

## Stap 5: De gebeurtenis voor het uitchecken in real-time activeren

In deze sectie test u de gebeurtenis in real-time.

1. Schakel in Journey Optimizer de testmodus in.

   ![ laat testwijze ](assets/ajo-enable-test.png){width="700" zoomable="yes"} toe

1. Als u deze reis in real-time wilt testen, opent u een ander browsertabblad en gaat u naar de [!DNL Commerce] -website in uw sandboxomgeving.

   1. Voeg een product toe aan uw winkelwagentje.
   1. Ga naar de uitcheckpagina.
   1. Laat vanaf de afhandelingspagina het winkelwagentje los door terug te gaan naar de hoofdpagina of uw tab te sluiten.

      De reis wordt nu in gang gezet. Om te bevestigen, open het lusje dat uw reis in Journey Optimizer heeft. Er moet een groene pijl verschijnen die het pad weergeeft dat de gebruiker heeft doorlopen.

1. Controleer uw Postvak IN op de e-mail.
