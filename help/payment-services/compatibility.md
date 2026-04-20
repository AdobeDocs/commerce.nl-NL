---
title: Compatibiliteit voor  [!DNL Payment Services]
description: Leer als  [!DNL Payment Services]  in uw land, en zijn verenigbaarheid met uw versie van Adobe Commerce beschikbaar is.
role: User
level: Intermediate
feature: Payments, Checkout, Paas, Saas
exl-id: 4bef8429-5053-424d-806a-9e8b96295b1b
source-git-commit: c532d72cb4aa7c920af790d345cce3ae6cbd2281
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# Compatibiliteit voor [!DNL Payment Services]

[!DNL Payment Services] is beschikbaar voor Adobe Commerce en Magento Open Source. [!DNL Payment Services] is nu compatibel met Adobe Commerce versie 2.4.x.

## Vereisten

Als u [!DNL Payment Services] wilt gebruiken, moet u eerst een verbinding maken met uw Commerce-instantie. **u opstelling deze verbinding slechts eenmaal**.

1. Als u onzeker bent of uw instantie wordt aangesloten, navigeer aan **Systeem** > de Diensten > **de Schakelaar van de Diensten van Commerce** en bekijk de openbare en privé API zeer belangrijke waarden in de Sandbox Sleutels en de secties van de Sleutels van de Productie, en de gebieden van de Ruimte van het Project en van Gegevens in de sectie van het Herkenningsteken SaaS. Als deze waarden aanwezig zijn, wordt de instantie verbonden.

1. Als u nog uw instantie moet verbinden, bekijk de instructies op de [&#x200B; pagina van de Schakelaar van de Diensten van 0&rbrace; Commerce &lbrace;.](../landing/saas.md)

   >[!TIP]
   >
   > Zie onze [&#x200B; zelfstudie van de Schakelaar van de Diensten van 0&rbrace; Adobe Commerce &lbrace;voor extra informatie.](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector)

1. Als u reeds uw instantie hebt verbonden, navigeer aan [&#x200B; het instappen &#x200B;](onboard.md) pagina voor volgende stappen.

>[!IMPORTANT]
>
> Alle handelaars gerechtigd voor [!DNL Payment Services] kunnen **één ruimte van productiegegevens** en **twee het testen gegevensruimten** gebruiken.

## Standaard versus geavanceerde [!DNL Payment Services] ervaring

[!DNL Payment Services] verstrekt **Standaard** (Uitdrukkelijke Controle) en **Geavanceerd** (volledig gesteund) betalingsopties en onboarding stromen, afhankelijk van het land waarin u werkt.

>[!NOTE]
>
> [!DNL Payment Services] verstrekt [&#x200B; Uitdrukkelijke mogelijkheden van de Controle &#x200B;](../payment-services/payments-options.md) (ondergroep van betalingsopties) voor andere [&#x200B; beschikbare landen tijdens onboarding &#x200B;](../payment-services/production.md#complete-merchant-onboarding).

### Welke [!DNL Payment Services] optie is geschikt voor u?

>[!VIDEO](https://video.tv.adobe.com/v/3447811)

Zie [&#x200B; verbinden &#x200B;](connect.md) voor meer informatie bij vestiging uw [!DNL Payment Services] uitbreiding.

>[!BEGINTABS]

>[!TAB  Standaard (Uitdrukkelijke Controle) ]

![&#x200B; controle &#x200B;](assets/icon-check.png) PayPal Afhandeling

![&#x200B; controle &#x200B;](assets/icon-check.png) PayPal Debit of Creditcard knoop

![&#x200B; controle &#x200B;](assets/icon-check.png) de controleconfiguraties van de Douane

![&#x200B; controle &#x200B;](assets/icon-check.png) Standaard tarifering

![&#x200B; controle &#x200B;](assets/icon-check.png) **Beschikbaar in XX landen**

[![&#x200B; leer meer &#x200B;](assets/learn-more-button.svg)](onboard.md)

>[!TAB  Geavanceerd (volledig gesteund) ]

![&#x200B; controle &#x200B;](assets/icon-check.png) Debit card

![&#x200B; controle &#x200B;](assets/icon-check.png) PayPal-krediet

![&#x200B; controle &#x200B;](assets/icon-check.png) de Gebieden van de Kaart

![&#x200B; controle &#x200B;](assets/icon-check.png) Apple Pay button

![&#x200B; controle &#x200B;](assets/icon-check.png) Google Pay button

![&#x200B; controle &#x200B;](assets/icon-check.png) PayPal Betalingsknopen

![&#x200B; controle &#x200B;](assets/icon-check.png) knoop van Venmo

![&#x200B; controle &#x200B;](assets/icon-check.png) PayPal Debit of Creditcard knoop

![&#x200B; controle &#x200B;](assets/icon-check.png) Betaal Latere Knoop

![&#x200B; controle &#x200B;](assets/icon-check.png) de controleconfiguraties van de Douane

![&#x200B; controle &#x200B;](assets/icon-check.png) Aangepaste tarifering

![&#x200B; controle &#x200B;](assets/icon-check.png) (L2/L3 tariferingsmogelijkheden - slechts US)

![&#x200B; controle &#x200B;](assets/icon-check.png) **slechts beschikbaar in Verenigde Staten (VS), Canada (CA), Australië (AUS). Frankrijk (FR), Verenigd Koninkrijk (UK)**

[![&#x200B; leer meer &#x200B;](assets/learn-more-button.svg)](onboard.md)

>[!ENDTABS]

Zie het [&#x200B; beleid van de Levenscyclus &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/lifecycle-policy.html?lang=nl-NL) en de [[!DNL Payment Services]  versienota&#39;s &#x200B;](release-notes.md) pagina&#39;s voor meer versie en versie-specifieke informatie.

Om de volledige instructies te krijgen en het onboarding proces te beginnen, zie [&#x200B; Begonnen met  [!DNL Payment Services]](onboard.md) worden.

### Geaccepteerde kredietkaarten en valuta&#39;s

[!DNL Payment Services] accepteert de valuta&#39;s van de landen waarin deze beschikbaar is. Zie [&#x200B; configuratie van de Valuta &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html?lang=nl-NL) voor meer informatie bij vestiging deviezen.

Raadpleeg de volgende pagina&#39;s voor meer informatie over de valuta&#39;s en betalingsmethoden die beschikbaar zijn bij PayPal-producten en -services:

* [&#x200B; Ondersteunde muntdocumentatie &#x200B;](https://developer.paypal.com/docs/reports/reference/paypal-supported-currencies/).

* [&#x200B; documentatie van de methodes van de Betaling &#x200B;](https://developer.paypal.com/docs/checkout/payment-methods/).
