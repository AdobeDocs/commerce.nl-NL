---
title: Testen en valideren
description: Het testen en de bevestigingshulp verzekeren dat  [!DNL Payment Services]  functies zoals verwacht werken en de beste betalingsopties voor uw klanten verstrekken
feature: Payments, Checkout
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# Testen en valideren

Alvorens u [!DNL Payment Services] voor [!DNL Adobe Commerce] en [!DNL Magento Open Source] aan uw kopers blootstelt, is het een goed idee om in uw zandbakmilieu _en_ in productie te testen. Door tests en validatie kunt u ervoor zorgen dat [!DNL Payment Services] -functies naar behoren werken en kunt u de beste betalingsopties voor uw winkel en klanten bieden.

## Testen in sandboxomgeving

Het testen van [!DNL Payment Services] in een sandbox-omgeving is een belangrijke validatiestap, ook al is het een gesimuleerde omgeving die alleen is verbonden met de PayPal-sandbox, niet met echte banken en handelaren.

1. Voltooi een succesvolle controle van uw opslag, of met [ Gebieden van de Kaart van de Kaart ](payments-options.md#credit-card-fields) of om het even welke [ PayPal betaalknopen ](payments-options.md#paypal-smart-buttons). Zie [ Testende geloofsbrieven ](#testing-credentials) voor meer informatie over het gebruiken van valse creditcards voor het testen.
1. Vang (wanneer uw betalingsactie [ aan `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method) wordt geplaatst), [ terugbetaling ](refunds.md), of [ nietig ](voids.md) de enkel-voltooide orde. U kunt eenvoudig ook [ een factuur ](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice){target="_blank"}  voor een orde creëren, als uw betalingsactie aan `Authorize` in plaats van `Authorize and Capture` wordt geplaatst.
1. Binnen 24-48 uren, bekijk de transactie en andere informatie in het [ rapport van Uitkeringen ](payouts.md).
1. Zie details van de orde in het [ rapport van de betalingsstatus van de Orde ](order-payment-status.md).

### Referenties testen

Bij het testen en valideren van uw sandbox moet u valse creditcardnummers gebruiken, zodat u geen echte kosten maakt voor een bestaande creditcardaccount.

De Generator van de Kredietkaart van PayPal van het gebruik aan [ produceert willekeurige creditcardinformatie ](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) voor het testen.

Apple Pay in sandboxmodus testen:

* Creeer een [ de zandbak van Apple testerrekening ](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account), volledig met valse creditcard en het factureren informatie.
* [ registreer uw zandbakdomeinen ](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>De betalingsverwerking van de sandbox van PayPal is soms traag en de service kan af en toe omlaag gaan. Deze situatie geeft geen indicatie van de snelheid en de efficiëntie van de verwerking van de rechtstreekse betalingen.

## Test in productie

U wordt ten zeerste aangeraden [!DNL Payment Services] in productie te testen met echte creditcards en banken voordat u deze functionaliteit aan kopers beschikbaar maakt. Hoewel het testen van [!DNL Payment Services] in de sandbox belangrijk is, is het testen in productie de meest misleidende methode om te zorgen dat [!DNL Payment Services] werkt zoals verwacht.

U kunt [!DNL Payment Services] in productie testen op een van de volgende twee manieren:

* Kies een tijdstip waarop je weet dat kopers geen bestellingen plaatsen.
* Gebruik een webwinkel die tijdelijk niet toegankelijk is voor kopers, maar die u wel kunt testen.

Voltooi uw productietests met echte creditcards en PayPal-rekeningen en test de volledige levenscyclus van een betaling, inclusief het vastleggen en terugbetalen. Als u het hele afrekenen en de betalingsstroom tijdens de test voltooit, krijgt u een duidelijk beeld van de werking van de [!DNL Payment Services] -functionaliteit wanneer live kopers deze gebruiken.

U moet ook controleren of de gegevens die op de bankafschriften staan voor de betalingsmethoden die u gebruikt bij het testen van de productie juist en verwacht zijn (inclusief de beschrijving van uw bedrijf).

Om Apple te testen betaal op productiemodus, moet u [ uw productiedomeinen ](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) registreren.
