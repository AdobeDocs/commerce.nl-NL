---
title: Fraudebescherming ondertekenen
description: Laat geautomatiseerde fraudebescherming voor  [!DNL Payment Services]  met Ondertekenen toe.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Ondertekening van de fraudebescherming

U kunt geautomatiseerde fraudebescherming voor [!DNL Payment Services] met de [ Ondertekenende uitbreiding ](https://commercemarketplace.adobe.com/signifyd-module-connect.html) toelaten.

Adobe Commerce ondersteunt ondertekenende versies 5.4.0 en hoger. [!DNL Payment Services] biedt ondersteuning voor pre-auth- en post-auth-ondertekeningsstromen.

De integratie Ondertekenen/[!DNL Payment Services] biedt dekking voor creditcards, debetkaarten, gefactureerde kaarten, uitchecken via de betalingsmethoden Admin en PayPal en Apple Pay. Hoewel sommige details van de transacties niet worden gedeeld door Betalingsdiensten en Ondertekenen, biedt Signifyd uitgebreide risicodekking voor alle betalingsmethoden, waardoor een maximale bescherming wordt geboden.

Zie [ Ondertekende documentatie ](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) leren over het installeren van en het vormen van de uitbreiding.

## Onboarding

U moet rechtstreeks communiceren met Handtekening aan boord van de extensie voor gebruik met [!DNL Payment Services] - er is geen [!DNL Payment Services] -configuratie nodig. U kunt de extensie Handtekening configureren in Beheer nadat deze is geïnstalleerd. Alle ondersteuning met betrekking tot deze extensie wordt beheerd door Ondertekenen.

Wanneer u aan boord gaat met handtekening, moet u:

1. Neem contact op met de ondertekenaar om een nieuwe account in te stellen.
1. Door gebrek, wordt het Ondertekenen gevoegd op lijst van gewenste personen [ ](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) om ervoor te zorgen het Ondertekenen niet voor andere betalingsopties teweegbrengt het momenteel niet steunt. Als u een bepaalde betalingsmethode wilt verbieden, moet u wijzigingen aanbrengen.
1. Bevestig met Ondertekenen dat PayPal geen bestellingen afwijst die via de instelling voor fraudebescherming van de handelaar in Paypal kunnen worden goedgekeurd door Ondertekenen.
1. Zorg ervoor dat de extensie Ondertekenen compatibel is met [!DNL Payment Services] :
   * Wanneer het gebruiken van [!DNL Payment Services] op _Levende_ wijze, moet het Ondertekenen op de wijze van de Productie zijn.
   * Wanneer het gebruiken van [!DNL Payment Services] op _zandbak_ wijze, moet het Ondertekenen op de wijze van de Test zijn.

## Configuratie

Aangezien Signifyd enige actie onderneemt op uw bestellingen, is het noodzakelijk om de extensie zodanig te configureren dat deze zich correct gedraagt op basis van de betalingsactie waarvoor u instelt [!DNL Payment Services] .

Deze configuratieopties zijn niet compatibel met Betalingsservices en de integratie Ondertekenen:

* Wanneer [!DNL Payment Services] met de `Authorize` betalingsactie _wordt gevormd en_ Ondertekenen is op `PostAuth` wijze met de _[!UICONTROL Decline Guarantees]_optie die aan **wordt geplaatst creeer creditnota**.

  Reden: [!DNL Payment Services] maakt een machtigingstransactie die Ondertekenaar vervolgens probeert terug te betalen.


* [!DNL Payment Services] wordt gevormd met `Authorize and Capture` betalingsactie _en_ Ondertekenen is op `PostAuth` wijze met de _[!UICONTROL Decline Guarantees]_optie die aan **wordt geplaatst orde**annuleert.

  Reden: [!DNL Payment Services] maakt een vastlegtransactie die tijdens de ondertekening wordt vermeden.


Zie Ondertekenende documentatie voor informatie over [ vormend de uitbreiding ](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

Zie Ondertekenende documentatie aan [ meer over de ordewerkschema&#39;s ](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works) leren.
