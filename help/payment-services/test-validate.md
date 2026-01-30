---
title: Testen en valideren
description: Het testen en de bevestigingshulp verzekeren dat  [!DNL Payment Services]  functies zoals verwacht werken en de beste betalingsopties voor uw klanten verstrekken
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
feature: Payments, Checkout, Paas, Saas
source-git-commit: 91a4b8fa7228fb91c8ee0bf0a1623d104f061894
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 0%

---

# Testen en valideren

Alvorens u [!DNL Payment Services] voor [!DNL Adobe Commerce] en [!DNL Magento Open Source] aan uw kopers blootstelt, is het een goed idee om in uw zandbakmilieu _en_ in productie te testen. Door tests en validatie kunt u ervoor zorgen dat [!DNL Payment Services] -functies naar behoren werken en kunt u de beste betalingsopties voor uw winkel en klanten bieden.

## Testen in sandboxomgeving

Het testen van [!DNL Payment Services] in een sandbox-omgeving is een belangrijke validatiestap, ook al is het een gesimuleerde omgeving die alleen is verbonden met de PayPal-sandbox, niet met echte banken en handelaren.

1. Voltooi een succesvolle controle van uw opslag, of met [&#x200B; Gebieden van de Kaart van de Kaart &#x200B;](payments-options.md#credit-card-fields) of om het even welke [&#x200B; PayPal betaalknopen &#x200B;](payments-options.md#paypal-smart-buttons). Zie [&#x200B; Testende geloofsbrieven &#x200B;](#testing-credentials) voor meer informatie over het gebruiken van valse creditcards voor het testen.
1. Vang (wanneer uw betalingsactie [&#x200B; aan `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method) wordt geplaatst), [&#x200B; terugbetaling &#x200B;](refunds.md), of [&#x200B; nietig &#x200B;](voids.md) de enkel-voltooide orde. U kunt eenvoudig ook [&#x200B; een factuur &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice){target="_blank"} voor een orde tot stand brengen, als uw betalingsactie aan `Authorize` in plaats van `Authorize and Capture` wordt geplaatst.
1. Binnen 24-48 uren, bekijk de transactie en andere informatie in het [&#x200B; rapport van Uitkeringen &#x200B;](payouts.md).
1. Zie details van de orde in het [&#x200B; rapport van de betalingsstatus van de Orde &#x200B;](order-payment-status.md).

### Testen op lokale ontwikkelomgevingen

Wanneer u PayPal-, PayLater- en Venmo-betalingsmethoden test op lokale ontwikkelomgevingen, moet uw omgeving toegankelijk zijn via internet. Deze betalingsmethodes gebruiken a [&#x200B; server-kant het verschepen callback &#x200B;](https://developer.paypal.com/docs/multiparty/checkout/standard/customize/shipping-module/) die PayPal vereist om met uw instantie van Commerce te communiceren om het verschepen opties terug te winnen en totalen te berekenen.

>[!INFO]
>
>Zonder een voor internet toegankelijke URL kan de callback voor verzending niet functioneren, wat resulteert in een andere uitcheckflow dan productie. Test altijd met een toegankelijke URL voor nauwkeurige resultaten.

Uw lokale omgeving toegankelijk maken:

1. Gebruik een het een tunnel graven dienst zoals [&#x200B; ngrok &#x200B;](https://ngrok.com/) om openbaar toegankelijke URL voor uw lokaal milieu tot stand te brengen.

1. Werk de configuratie van de basis-URL van Commerce bij zodat deze overeenkomt met de URL van het knooppunt:

   ```bash
   bin/magento config:set web/unsecure/base_url https://your-ngrok-url.ngrok.io/
   bin/magento config:set web/secure/base_url https://your-ngrok-url.ngrok.io/
   bin/magento cache:flush
   ```

1. Voltooi uw tests met de betalingsmethoden PayPal, PayLater of Venmo.

1. Herstel de oorspronkelijke basis-URL-configuratie wanneer het testen is voltooid.

Als de reactietijd van het eindpunt minder dan 5 seconden is, toont PayPal een foutenmelding in pop-up.

#### Lokale ontwikkeling van Apple Pay

Apple Pay vereist een extra configuratie voor lokale ontwikkeling. Apple Pay gebruikt domeinregistratie om te controleren of je site geautoriseerd is om betalingen voor Apple Pay te accepteren. Dit betekent dat Apple uw domein moet kunnen bereiken om een domeinverificatiebestand op `/.well-known/apple-developer-merchantid-domain-association` te valideren.

Voor lokale ontwikkeling moet uw omgeving aan de volgende vereisten voldoen:

* **openbaar toegankelijke**, Apple moet uw domein van Internet kunnen bereiken.
* **HTTPS protocol**, betaalt Apple slechts werkt op veilige verbindingen.

Het gebruiken van een het een tunnel graven dienst als [&#x200B; ngrok &#x200B;](https://ngrok.com/) voldoet beide vereisten. Na vestiging registreert het netwerk zoals hierboven beschreven, [&#x200B; uw zandbakdomein &#x200B;](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains) met PayPal gebruikend **ingrok** URL.

### Referenties testen

Bij het testen en valideren van uw sandbox moet u valse creditcardnummers gebruiken, zodat u geen echte kosten maakt voor een bestaande creditcardaccount.

De Generator van de Kredietkaart van PayPal van het gebruik aan [&#x200B; produceert willekeurige creditcardinformatie &#x200B;](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) voor het testen.

Apple Pay in sandboxmodus testen:

* Creeer een [&#x200B; de zandbak van Apple testerrekening &#x200B;](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account), volledig met valse creditcard en het factureren informatie.
* [&#x200B; registreer uw zandbakdomeinen &#x200B;](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

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

### Betalen met Apple testen tijdens productie

Om Apple te testen betaal op productiemodus, moet u [&#x200B; uw productiedomeinen &#x200B;](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) registreren.
