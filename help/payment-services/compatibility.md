---
title: Compatibiliteit voor  [!DNL Payment Services]
description: Leer als  [!DNL Payment Services]  in uw land, en zijn verenigbaarheid met uw versie van Adobe Commerce beschikbaar is.
role: User
level: Intermediate
feature: Payments, Checkout, Paas, Saas
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---


# Compatibiliteit voor [!DNL Payment Services]

[!DNL Payment Services] is beschikbaar voor Adobe Commerce en Magento Open Source. [!DNL Payment Services] is nu compatibel met Adobe Commerce versie 2.4.x.

## Vereisten

Als u [!DNL Payment Services] wilt gebruiken, moet u eerst een verbinding maken met uw Commerce-instantie. **u opstelling deze verbinding slechts eenmaal**.

1. Als u onzeker bent of uw instantie wordt aangesloten, navigeer aan **Systeem** > de Diensten > **de Schakelaar van de Diensten van Commerce** en bekijk de openbare en privé API zeer belangrijke waarden in de Sandbox Sleutels en de secties van de Sleutels van de Productie, en de gebieden van de Ruimte van het Project en van Gegevens in de sectie van het Herkenningsteken SaaS. Als deze waarden aanwezig zijn, wordt de instantie verbonden.

1. Als u nog uw instantie moet verbinden, bekijk de instructies op de [&#128279;](../landing/saas.md) pagina van de Schakelaar van de Diensten van 0&rbrace; Commerce &lbrace;.

   >[!TIP]
   >
   > Zie onze [&#128279;](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector) zelfstudie van de Schakelaar van de Diensten van 0&rbrace; Adobe Commerce &lbrace;voor extra informatie.

1. Als u reeds uw instantie hebt verbonden, navigeer aan [ het instappen ](onboard.md) pagina voor volgende stappen.

>[!IMPORTANT]
>
> Alle handelaars gerechtigd voor [!DNL Payment Services] kunnen **één ruimte van productiegegevens** en **twee het testen gegevensruimten** gebruiken.

## Standaard versus geavanceerde [!DNL Payment Services] ervaring

[!DNL Payment Services] verstrekt **Standaard** (Uitdrukkelijke Controle) en **Geavanceerd** (volledig gesteund) betalingsopties en onboarding stromen, afhankelijk van het land waarin u werkt.

>[!NOTE]
>
> [!DNL Payment Services] verstrekt [ Uitdrukkelijke mogelijkheden van de Controle ](../payment-services/payments-options.md) (ondergroep van betalingsopties) voor andere [ beschikbare landen tijdens onboarding ](../payment-services/production.md#complete-merchant-onboarding).

### Welke [!DNL Payment Services] optie is geschikt voor u?

>[!VIDEO](https://video.tv.adobe.com/v/3447811)

Zie [ verbinden ](connect.md) voor meer informatie bij vestiging uw [!DNL Payment Services] uitbreiding.

>[!BEGINTABS]

>[!TAB  Standaard (Uitdrukkelijke Controle) ]

![ controle ](assets/icon-check.png) PayPal Afhandeling

![ controle ](assets/icon-check.png) PayPal Debit of Creditcard knoop

![ controle ](assets/icon-check.png) de controleconfiguraties van de Douane

![ controle ](assets/icon-check.png) Standaard tarifering

![ controle ](assets/icon-check.png) **Beschikbaar in XX landen**

[![ leer meer ](assets/learn-more-button.svg)](onboard.md)

>[!TAB  Geavanceerd (volledig gesteund) ]

![ controle ](assets/icon-check.png) Debit card

![ controle ](assets/icon-check.png) PayPal-krediet

![ controle ](assets/icon-check.png) de Gebieden van de Kaart

![ controle ](assets/icon-check.png) Apple Pay button

![ controle ](assets/icon-check.png) Google Pay button

![ controle ](assets/icon-check.png) PayPal Betalingsknopen

![ controle ](assets/icon-check.png) knoop van Venmo

![ controle ](assets/icon-check.png) PayPal Debit of Creditcard knoop

![ controle ](assets/icon-check.png) Betaal Latere Knoop

![ controle ](assets/icon-check.png) de controleconfiguraties van de Douane

![ controle ](assets/icon-check.png) Aangepaste tarifering

![ controle ](assets/icon-check.png) (L2/L3 tariferingsmogelijkheden - slechts US)

![ controle ](assets/icon-check.png) **slechts beschikbaar in Verenigde Staten (VS), Canada (CA), Australië (AUS). Frankrijk (FR), Verenigd Koninkrijk (UK)**

[![ leer meer ](assets/learn-more-button.svg)](onboard.md)

>[!ENDTABS]

Zie het [ beleid van de Levenscyclus ](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html?lang=nl-NL) en de [[!DNL Payment Services]  versienota&#39;s ](release-notes.md) pagina&#39;s voor meer versie en versie-specifieke informatie.

Om de volledige instructies te krijgen en het onboarding proces te beginnen, zie [ Begonnen met  [!DNL Payment Services]](onboard.md) worden.

### Geaccepteerde kredietkaarten en valuta&#39;s

[!DNL Payment Services] keurt de valuta&#39;s van de landen [ goed waarin het ](#availability) beschikbaar is. Zie [ configuratie van de Valuta ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html?lang=nl-NL) voor meer informatie bij vestiging deviezen.

Raadpleeg de volgende pagina&#39;s voor meer informatie over de valuta&#39;s en betalingsmethoden die beschikbaar zijn bij PayPal-producten en -services:

* [ Ondersteunde muntdocumentatie ](https://developer.paypal.com/docs/reports/reference/paypal-supported-currencies/).

* [ documentatie van de methodes van de Betaling ](https://developer.paypal.com/docs/checkout/payment-methods/).
