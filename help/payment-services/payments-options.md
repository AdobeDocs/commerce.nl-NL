---
title: Betalingsopties
description: Stel de betalingsopties in om de beschikbare methoden voor uw winkelklanten aan te passen.
feature: Payments, Checkout, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---

# Betalingsopties

Met [!DNL Adobe Commerce] en [!DNL Magento Open Source] [!DNL Payment Services] hebt u meerdere betalingsopties beschikbaar.

U kunt deze betalingsopties in [ montages van het Huis ](payments-home.md) vormen of [ configuratie van de Opslag ](configure-admin.md) (geadviseerd voor de opties van de erfenisbetaling of een multi-store opstelling).

Er zijn verschillende gedragingen voor elke betalingsmethode, afhankelijk van waar u zich bevindt in het uitbetalingsproces:

* Productpagina—De productpagina voor een item
* Mini kart - Beschikbaar bij klikken op het pictogram van het karretje wanneer een product aan de winkelwagentjes is toegevoegd
* Het winkelen kar-Beschikbaar op klik van _Mening en geeft kar_ van de mini-kar uit
* Controle mening-Beschikbaar op klik van _ga aan Controle_ van mini-kar of het winkelwagentje

>[!IMPORTANT]
>
>[!DNL Payment Services] aan boord moet zijn voltooid voordat betalingen kunnen worden verwerkt.

## Standaard versus geavanceerde betalingservaring

[!DNL Payment Services] verstrekt **Geavanceerd** (volledig gesteund) en **Standaard** (Uitdrukkelijke Controle) betalingsopties en onboarding stromen, afhankelijk van het land waarin u werkt.

* **Geavanceerd** - Alle beschikbare [ betalingsopties ](../payment-services/payments-options.md) zijn beschikbaar voor huidige [ volledig gesteunde landen ](../payment-services/overview.md#availability). Tijdens onboarding om levende betalingen toe te laten, selecteer de [ Geavanceerde onboarding optie ](../payment-services/production.md#advanced-onboarding).
* **Standaard** - een ondergroep betalingsopties (Uitdrukkelijke Afhandeling) - PayPal krediet en debetkaarten-is beschikbaar voor andere beschikbare gesteunde landen. [ de gebieden van de Kredietkaart ](#credit-card-fields) en [ Betalen Apple ](#apple-pay-button) zijn niet beschikbaar voor deze onboarding optie. Tijdens het aan boord gaan om levende betalingen toe te laten, selecteer de [ Standaard aan boord komende optie ](../payment-services/production.md#standard-onboarding).

Zie [  [!DNL Payment Services]  toelaten voor productie ](../payment-services/production.md#complete-merchant-onboarding) voor informatie over de voltooiing van Geavanceerde en Standaard op het instappen.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] biedt een eenvoudige en veilige afhandeling voor betalingsmethoden met creditcard of bankpas. Wanneer een winkelier uitcheckt met gebruik van creditcardvelden, geeft hij zijn naam, factuuradres en creditcardgegevens op om zijn bestelling te plaatsen. De klantgegevens worden tijdens de aankoopsessie veilig gebruikt om ze naadloos door de afrekenstroom te begeleiden.

![ de gebieden van de Kredietkaart in controle ](assets/credit-card-fields.png){width="500" zoomable="yes"}

Laat [ creditcard toe die ](#vaulting) voor uw opslag in kluizen aanklaagt om klanten toe te staan (sparen) hun creditcardinformatie voor een snelle controle later te vault.

U kunt [!UICONTROL Credit Card Fields] configureren in de winkelconfiguratie of in [!DNL Payment Services] Home. Zie [ Montages ](settings.md#credit-card-fields) voor meer informatie.

U kunt ook de lay-out, breedte, hoogte en buitenstijl van de creditcardvelden wijzigen. Zie [ documentatie PayPal ](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) voor meer informatie.

## [!DNL Apple Pay] knop

Klanten kunnen [[!DNL Apple Pay] gebruiken ](https://www.apple.com/apple-pay/), dat creditcard- en betaalgegevens gebruikt die op een iOS- of macOS-apparaat zijn opgeslagen, om aankopen te doen.

[!DNL Apple Pay] is alleen beschikbaar in de Safari browser. Merchants kunnen maximaal 99 domeinen per zakelijke account toevoegen.

![ de knoop van het Betalen van Apple in minicart ](assets/applepay-button.png){width="500" zoomable="yes"}

De knop [!DNL Apple Pay] is zichtbaar vanaf de productpagina, de miniwinkelwagentje, het winkelwagentje en de afrekenweergave.

Om [!DNL Apple Pay] voor uw opslag te gebruiken, volledig [ zelfregistratie met  [!DNL Apple Pay] ](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_registreer uw levende domein_ sectie slechts) en [ vormt het voor uw opslag in  [!DNL Payment Services]](settings.md#payment-buttons).

>[!NOTE]
>
> Zie [ geavanceerde controle ](https://www.paypal.com/us/cshelp/article/what-is-paypal-advanced-checkout-and-how-do-i-get-started-help953){target=_blank}  in de ontwikkelaarsdocumentatie PayPal om te controleren hoe te om kopers toe te laten om met Apple te betalen op uw plaats te betalen.

U kunt [!UICONTROL Apple Pay] configureren in de winkelconfiguratie of in de startpagina van de betalingsservices. Zie [ Montages ](settings.md#apple-pay) voor meer informatie.

## [!DNL Google Pay] knop

Klanten kunnen [[!DNL Google Pay] ](https://pay.google.com/about/) gebruiken door betalingsgegevens toe te voegen aan hun Google-account, waar ze veilig zijn opgeslagen voor een naadloze afhandeling.

[!DNL Google Pay] is alleen beschikbaar in bepaalde landen of regio&#39;s en op bepaalde apparaten. Zie [[!DNL Google Pay]  documentatie ](https://developer.paypal.com/docs/checkout/apm/google-pay/#link-googlepayintegration) voor meer informatie.

![ de knoop van de Betaling van Google in de controle ](assets/google-pay-button.png){width="500" zoomable="yes"}

De knop [!DNL Google Pay] is zichtbaar vanaf de productpagina, de miniwinkelwagentje, het winkelwagentje en de afrekenweergave.

U kunt [!UICONTROL Google Pay] configureren in de winkelconfiguratie of in de startpagina van de betalingsservices. Zie [ Montages ](configure-admin.md) voor meer informatie.

>[!NOTE]
>
> De API van [!DNL Google Pay] kan alleen worden gebruikt op websites in een veilige context. Zie [ het Oplossen van problemen ](https://developers.google.com/pay/api/web/support/troubleshooting) documentatie voor meer informatie.

## [!DNL PayPal Payment Buttons]

[!DNL PayPal payment buttons] , dat PayPal gebruikt om een aankoop te voltooien, slaat het verzendadres, het factuuradres en de betalingsgegevens van uw winkels op voor later gebruik. Kopers kunnen elke betalingsmethode gebruiken die eerder door PayPal is opgeslagen of aangeboden.

![ PayPal knoop ](assets/paypal-button.png){width="350" zoomable="yes"}

U kunt [!UICONTROL PayPal payment buttons] configureren in de winkelconfiguratie of in [!DNL Payment Services] Home. Zie [ Montages ](settings.md#payment-buttons) voor meer informatie.

Leer over beschikbaarheid van betalingsmethodes door land in de documentatie van de Methodes van de Betaling van PayPal [&#128279;](https://developer.paypal.com/docs/checkout/payment-methods/).

### [!DNL PayPal] knop

Klanten kunnen met gemak en vertrouwen uitchecken met de PayPal-knop.

De knop [!DNL PayPal] is zichtbaar vanaf de productpagina, de miniwinkelwagentje, het winkelwagentje en de afrekenweergave.

### [!DNL Venmo] knop

De klanten kunnen uit het gebruiken van de [ knoop van Venmo ](https://venmo.com/) controleren.

De knop [!DNL Venmo] is zichtbaar vanaf de productpagina, de miniwinkelwagentje, het winkelwagentje en de afrekenweergave.

### PayPal-incasso of creditcard

Klanten kunnen uitchecken via de button PayPal-incasso of creditcard.

De button PayPal Debit of Creditcard is zichtbaar vanaf de betalingspagina.

Met deze optie kun je een betalingsoptie voor een debet of creditcard aan kopers aanbieden met een PayPal-gehoste knop als alternatief voor de integratie met een creditcard.

### [!DNL Pay Later] knop

Bied uw klanten kortetermijnbetalingen, rentevrije betalingen en andere financieringsopties aan, zodat ze nu kunnen kopen en later kunnen betalen met de knop [!DNL Pay Later] .

De knop [!DNL Pay Later] is zichtbaar vanaf de productpagina, de miniwinkelwagentje, het winkelwagentje en de afrekenweergave.

Zie informatie over de Pay Later aanbiedingen in [ PayPal van PayPal biedt later documentatie ](https://developer.paypal.com/docs/checkout/pay-later/us/) aan. Gebruik **Land of gebied** dropdown om een gebied van belang te selecteren.

Leer om het [!DNL Pay Later] overseinen onbruikbaar te maken of toe te laten door de [ configuratie van Montages ](settings.md#payment-buttons) bij te werken.

## Alleen PayPal-betalingsknoppen gebruiken

Om uw opslag in productiemodus snel te krijgen, kunt u _slechts_ PayPal betalingsknopen (Venmo, PayPal, etc.) vormen.—in plaats van ook de optie PayPal-creditcardbetaling te gebruiken.

Zo kunt u:

* Geef uw klanten verschillende betalingsopties, waaronder de betaalknoppen Venmo en PayPal, met de optie om door PayPal gehoste kaartvelden uit te schakelen en een bestaande creditcardprovider te gebruiken.
* Gebruik de bestaande creditcardprovider voor creditcardbetalingen en gebruik ook de andere betalingsopties van PayPal.
* Gebruik de betalingsknoppen van PayPal in regio&#39;s waar PayPal geen creditcards als betalingsoptie ondersteunt.

**vangt betalingen met _slechts_ PayPal betaalknopen (_niet_ de optie van de creditcardbetaling van PayPal)**:

1. Zorg ervoor dat uw opslag [ op productiemodus ](settings.md#enable-payment-services) is.
1. [ vorm de gewenste PayPal betalingsknopen ](settings.md#payment-buttons) in Montages.
1. Draai _weg_ de **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** optie in de _[!UICONTROL Payment buttons]_&#x200B;sectie.

Om **betalingen met uw bestaande creditcardleverancier _en_ PayPal betaalknopen** te vangen:

1. Zorg ervoor dat uw opslag [ op productiemodus ](settings.md#enable-payment-services) is.
1. [ vorm de gewenste PayPal betalingsknopen ](settings.md#payment-buttons).
1. Draai _weg_ de **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** optie in de _[!UICONTROL Payment buttons]_&#x200B;sectie.
1. Draai _van_ de **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** optie in de _[!UICONTROL Credit card fields]_&#x200B;sectie en gebruik uw [ bestaande rekening van de creditcardleverancier ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## Orderrecalculatie

Wanneer een klant de afhandelingsstroom invoert van de mini-cart, winkelwagentje of productpagina, wordt deze doorgestuurd naar een pagina voor het controleren van bestellingen waar hij het geselecteerde verzendadres kan zien in een pop-upvenster van PayPal. Nadat de klant de verzendmethode heeft geselecteerd, wordt het orderbedrag op de juiste wijze herberekend en kan de klant de verzendkosten en -belastingen zien.

Wanneer een klant de afrekenstroom vanaf de afhandelingspagina invoert, is het systeem zich al bewust van het verzendadres en het uiteindelijke berekende bedrag en worden de totalen op de juiste wijze weergegeven.

Belastingvrije dagen, verzendkosten en BTW kunnen per locatie sterk verschillen. Nadat [!DNL Payment Services] het verzendadres en de verzendkosten heeft ontvangen, worden alle toepasselijke kosten snel opnieuw berekend en op de juiste wijze weergegeven tijdens de laatste stappen van de afhandeling.

## Creditcard vaulting

Klanten kunnen hun creditcardgegevens voor toekomstige aankopen op websiteniveau (elke winkel binnen dezelfde zakelijke account) invullen (of &quot;opslaan&quot;).

Zie [ Kredietkaart die ](vaulting.md) voor meer informatie in kluizen.

## Beveiliging

Zie [ naleving PCI ](security.md#pci-compliance) voor meer informatie.
