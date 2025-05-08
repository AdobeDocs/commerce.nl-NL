---
title: Configuratie van verouderde betalingsservices
description: Na installatie, kunt u  [!DNL Payment Services]  in Admin bij de opslagconfiguratie vormen.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 51b3f5fffda1402d25bb57402eae82afc8515a14
workflow-type: tm+mt
source-wordcount: '1758'
ht-degree: 0%

---

# Verouderde [!DNL Payment Services] configuratie

U kunt [!DNL Payment Services] aan uw behoeften aanpassen met nuttige configuratieopties in Admin.

Wanneer u [!DNL Payment Services] for [!DNL Adobe Commerce] en [!DNL Magento Open Source] in de beheerfunctie configureert, zijn deze configuraties alleen van toepassing op de omgeving die is ingesteld in het _[!UICONTROL Method]_veld_[!UICONTROL General Configuration]_ . Wijzigingen die u aanbrengt in de configuratievelden, zijn onafhankelijk van het schakelen tussen de selectie van _[!UICONTROL Method]_. Als u van methode wisselt, worden de selecties niet opnieuw ingesteld.

## Algemene configuratie

U kunt [!DNL Payment Services] inschakelen voor uw winkel en uw _[!UICONTROL Merchant Location]_en het testen van sandboxen of live betalingen inschakelen in de sectie_[!UICONTROL General Configuration]_ .

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Stel het veld _[!UICONTROL Merchant Country]_in in de map_[!UICONTROL Merchant Location]_ . Als er geen _[!UICONTROL Merchant Country]_is opgegeven, wordt de lus_[!UICONTROL Default Country]_ uit de algemene configuratie gebruikt.
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_uit om de sectie_[!UICONTROL [!DNL Payment Services]]_ te openen.
1. Vouw in de sectie _[!UICONTROL [!DNL Payment Services]]_de sectie_[!UICONTROL General Configuration]_ uit.
1. Voor **laat** toe, plaats het aan `Yes` om [!DNL Payment Services] voor uw opslag toe te laten.
1. Voor **Methode**, plaats het aan `Sandbox` als u nog [!DNL Payment Services] voor uw opslag of `Production` test als u bereid bent om levende betalingen toe te laten.
1. Uw **[!UICONTROL Payment Services Sandbox ID]** en **[!UICONTROL Payment Services Production ID]** waarden worden automatisch bevolkt zodra u de [ Schakelaar van de Diensten van Commerce ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas){target=_blank} opstelde en het [!DNL Payment Services] dashboard voor het eerst bezoekt. Doe dit om het instappen voor uw zandbak en/of productiemilieu&#39;s te beëindigen. Deze waarden koppelen uw SaaS-id aan [!DNL Payment Services] .

   >[!WARNING]
   >
   > Als u uw ID voor de gegevensruimte in de Commerce Services-connector moet wijzigen, moet u de [!DNL Payment Services] -id opnieuw instellen. Klik **identiteitskaart van de Diensten van de Betaling van het Terugstellen** om uw Sandbox of Productie IDs terug te stellen. Als u de id&#39;s van [!DNL Payment Services] opnieuw instelt, moet u opnieuw aan boord gaan.

1. Uw **[!UICONTROL PayPal Merchant ID]** - en **[!UICONTROL PayPal Merchant Status]** -waarden worden automatisch door PayPal verschaft wanneer u het [!DNL Payment Services] -dashboard voor de eerste keer bezoekt.
1. Voor **Zachte beschrijver** (douanewaarden die op de verklaringen van de bank van de klantentransactie tonen om tussen opslag/brands/catalogi te afbakenen), voeg uw douanetekst (tot 22 karakters) op het tekstgebied toe, die `Soft descriptor` of de bestaande waarde vervangt.
1. Klik op **[!UICONTROL Save Config]** om de wijzigingen op te slaan.
1. Navigeer naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]** en klik vervolgens op **[!UICONTROL Flush Cache]** om alle ongeldige cache te vernieuwen.

![ Aanbevolen mening van de Oplossing van Adobe ](assets/config-view-all.png){width="700" zoomable="yes"}

### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Enable] | website | Schakel [!DNL Payment Services] voor uw website in of uit. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Method] | winkelweergave | Plaats de methode, of het milieu, voor uw opslag. Opties: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Payment Services Sandbox ID] | winkelweergave | De bedrijfs-id van de sandbox, die automatisch wordt gegenereerd tijdens het aan boord nemen van de sandbox. |
| [!UICONTROL Payment Services Production ID] | winkelweergave | Uw bedrijfs-id voor productie, die automatisch wordt gegenereerd tijdens productie (live) aan boord. |
| [!UICONTROL PayPal Merchant ID] | winkelweergave | Je unieke PayPal Merchant account-id die je hebt gegenereerd wanneer je je PayPal-rekening maakt. |
| [!UICONTROL PayPal Merchant Status] | winkelweergave | Status van je PayPal Merchant ID. |
| [!UICONTROL Soft Descriptor] | website- of winkelweergave | Voeg een elektronische beschrijving toe aan uw website(s) en sla de weergave(en) op om informatie toe te voegen aan klanttransacties die merken, winkels of productlijnen afbakenen. |

## [!UICONTROL Credit Card Fields]

De betalingsopties van [!UICONTROL Credit Card Fields] bieden een eenvoudige en veilige afhandeling voor betalingsmethoden met creditcard of bankpas.

Zie [ de opties van Betalingen ](payments-options.md#paypal-smart-buttons) voor meer informatie.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_uit.
1. Vouw in de sectie _[!UICONTROL Payment Services]_de sectie_[!UICONTROL Credit Card Fields]_ uit.
1. Voer bij **[!UICONTROL Title]** (indien nodig) tekst in om de naam van de betalingsmethode te wijzigen, zoals tijdens het uitchecken wordt getoond.
1. Om [ de betalingsactie ](production.md#set-payment-services-as-payment-method) te plaatsen, selecteer **[!UICONTROL Authorize]** of **machtigt en vangt**.
1. Geef een `Numeric Only` -waarde op in het **[!UICONTROL Sort order]** -veld op als u de prioriteit van een betalingsmethode op de uitcheckpagina wilt bepalen.
1. Kies bij **[!UICONTROL Show on checkout page]** de optie `Yes` om creditcardvelden op de uitcheckpagina in te schakelen.
1. Kies bij **[!UICONTROL Vault Enabled]** de optie `Yes` om het uitchecken van creditcardgegevens in te schakelen.
1. Kies bij **[!UICONTROL Vault Enabled in Admin]** de optie `Yes` om de handelaar in staat te stellen orders voor klanten te maken met behulp van hun gefactureerde creditcard.
1. Als u **[!UICONTROL 3D Secure authentication]** (`Off` standaard) wilt inschakelen, kiest u `Always` of `When required` .
1. Kies bij **[!UICONTROL Debug Mode]** `Yes` om de foutopsporingsmodus in te schakelen of `No` om deze uit te schakelen.
1. Klik op **[!UICONTROL Save Config]** om de wijzigingen op te slaan.
1. Navigeer naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]** en klik vervolgens op **[!UICONTROL Flush Cache]** om alle ongeldige cache te vernieuwen.

### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Title] | winkelweergave | Voeg de tekst die tijdens het afrekenen als titel voor deze betalingsoptie moet worden weergegeven, toe in de weergave Betalingsmethode. Opties: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | De [ betalingsactie ](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) voor de gespecificeerde betalingsmethode. Opties: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | winkelweergave | De sorteervolgorde voor de opgegeven betalingsmethode op de uitcheckpagina. `Numeric Only` value |
| [!UICONTROL Show on checkout page] | website | Schakel creditcardvelden op de afrekenpagina in of uit. Opties: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | winkelweergave | Laat toe of maak [ creditcard het vaulteren ](vaulting.md) onbruikbaar. Opties: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | winkelweergave | Laat of maak capaciteit voor [ merchant toe onbruikbaar om orden voor klanten in Admin ](vaulting.md) te voltooien gebruikend een in gebreke gebleven betalingsmethode. Opties: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3D Secure authentication] | website | Laat of maak [ 3DS Veilige authentificatie ](security.md#3ds) toe onbruikbaar. Opties: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | website | De foutopsporingsmodus in- of uitschakelen. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Apple Pay]

Met de betalingsoptie [!UICONTROL Apple Pay] kan de handelaar Apple Pay aanbieden aan zijn kopers, die met Touch ID op hun apparaten aankopen kunnen doen via de Safari-browser. Merchants kunnen maximaal 99 domeinen per zakelijke account toevoegen.

Zie [ de opties van Betalingen ](payments-options.md#apple-pay-button) voor meer informatie.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_uit.
1. Vouw in de sectie _[!UICONTROL Payment Services]_de sectie_[!UICONTROL Apple Pay]_ uit.
1. Voer bij **[!UICONTROL Title]** (indien nodig) tekst in om de naam van de betalingsmethode te wijzigen, zoals tijdens het uitchecken wordt getoond.
1. Om [ de betalingsactie ](production.md#set-payment-services-as-payment-method) te plaatsen, selecteer **[!UICONTROL Authorize]** of **[!UICONTROL Authorize and Capture]**.
1. Geef aan waar de optie [!DNL Apple Pay] in Adobe Commerce is ingeschakeld door `Yes` te selecteren in de volgende opties, indien nodig:
   * **[!UICONTROL Show Apple Pay on checkout page]**
   * **[!UICONTROL Show Apple Pay on product detail page]**
   * **[!UICONTROL Show Apple Pay in mini cart preview]**
   * **[!UICONTROL Show Apple Pay on cart page]**
1. Als u de foutopsporingsmodus wilt inschakelen, selecteert u `Yes` voor **[!UICONTROL Debug Mode]** (`No` schakelt u deze uit).
1. Klik op **[!UICONTROL Save Config]** om de wijzigingen op te slaan.
1. Navigeer naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]** en klik vervolgens op **[!UICONTROL Flush Cache]** om alle ongeldige cache te vernieuwen.

### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Title] | winkelweergave | Voeg de tekst die tijdens het afrekenen als titel voor deze betalingsoptie moet worden weergegeven, toe in de weergave Betalingsmethode. Opties: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | De [ betalingsactie ](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) voor de gespecificeerde betalingsmethode. Opties: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | website | Schakel [!DNL Apple Pay] in of uit op de uitcheckpagina. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | winkelweergave | De sorteervolgorde voor de opgegeven betalingsmethode op de uitcheckpagina. `Numeric Only` value |
| [!UICONTROL Show buttons on product detail page] | winkelweergave | Schakel [!DNL Apple Pay] in of uit op de pagina met productdetails. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | winkelweergave | Schakel [!DNL Apple Pay] in of uit in de voorvertoning van de miniwinkelwagentje. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | winkelweergave | Schakel [!DNL Apple Pay] in of uit op de tekstpagina. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | website | De foutopsporingsmodus in- of uitschakelen. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Google Pay]

Met de betalingsoptie [!UICONTROL Google Pay] kan de handelaar Google Pay aanbieden aan zijn kopers, die de Google Wallet op hun apparaten kunnen gebruiken om aankopen te doen.

Zie [ de opties van Betalingen ](payments-options.md#google-pay-button) voor meer informatie.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_uit.
1. Vouw in de sectie _[!UICONTROL Payment Services]_de sectie_[!UICONTROL Google Pay]_ uit.
1. (Optioneel) Wijzig de naam van de betalingsmethode die tijdens het afrekenen wordt weergegeven door de nieuwe naam in te voeren in het veld **[!UICONTROL Title]** .
1. [ plaats de betalingsactie ](production.md#set-payment-services-as-payment-method) door te selecteren **[!UICONTROL Authorize]** of **[!UICONTROL Authorize and Capture]**.
1. Geef aan waar de optie [!DNL Google Pay] in Adobe Commerce is ingeschakeld door `Yes` te selecteren in de volgende opties, indien nodig:
   * **[!UICONTROL Show Google Pay on checkout page]**
   * **[!UICONTROL Show Google Pay on product detail page]**
   * **[!UICONTROL Show Google Pay in mini cart preview]**
   * **[!UICONTROL Show Google Pay on cart page]**
1. Als u **[!UICONTROL 3D Secure authentication]** (`Off` standaard) wilt inschakelen, kiest u `Always` of `When required` .
1. Als u de foutopsporingsmodus wilt inschakelen, selecteert u `Yes` voor **[!UICONTROL Debug Mode]** (`No` schakelt u deze uit).
1. Configureer de weergave van de knop _[!UICONTROL Google Pay]_door de knoppen **[!UICONTROL Button Color]**,**[!UICONTROL Button Type]**en **[!UICONTROL Button Style]**naar wens te selecteren.
1. Als u de hoogte wilt instellen, gebruikt u de standaardwaarde voor de hoogte die is gedefinieerd in **[!UICONTROL Button Style]** .
1. Klik op **[!UICONTROL Save Config]** om de wijzigingen op te slaan.
1. Navigeer naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]** en klik vervolgens op **[!UICONTROL Flush Cache]** om alle ongeldige cache te vernieuwen.

### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Title] | winkelweergave | Hiermee geeft u het tekstlabel op dat voor deze betalingsoptie wordt weergegeven in de weergave Betalingsmethode tijdens het uitchecken. Opties: `[!UICONTROL text field]` |
| [!UICONTROL Payment Action] | website | De [ betalingsactie ](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) voor de gespecificeerde betalingsmethode. Opties: `[!UICONTROL Authorize]` / `[!UICONTROL Authorize and Capture]` |
| [!UICONTROL Show on checkout page] | website | Schakel [!DNL Google Pay] in of uit op de uitcheckpagina. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Sort order] | winkelweergave | De sorteervolgorde voor de opgegeven betalingsmethode op de uitcheckpagina. `Numeric Only` value |
| [!UICONTROL Show buttons on product detail page] | winkelweergave | Schakel [!DNL Google Pay] in of uit op de pagina met productdetails. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | winkelweergave | Schakel [!DNL Google Pay] in of uit in de voorvertoning van de miniwinkelwagentje. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | winkelweergave | Schakel [!DNL Google Pay] in of uit op de tekstpagina. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL 3D Secure authentication] | winkelweergave | Laat of maak [ 3D Veilige authentificatie ](security.md#3ds) toe onbruikbaar. Opties: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | website | De foutopsporingsmodus in- of uitschakelen. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Button Color] | Winkelweergave | Definieer de kleur van de knop [!DNL Google Pay] . Opties: `[!UICONTROL Default]` / `[!UICONTROL Black]` / `[!UICONTROL White]` |
| [!UICONTROL Button Type] | Winkelweergave | Geef het type van de knop [!DNL Google Pay] op. Opties: `[!UICONTROL buy]` / `[!UICONTROL checkout]` / `[!UICONTROL order]` / `[!UICONTROL pay]` / `[!UICONTROL plain]` |

Zie ](https://developers.google.com/pay/api/web/reference/request-objects) documentatie van het de verzoekvoorwerp van Google van de Betaling API van 0} {voor meer informatie.[

## [!DNL PayPal Payment Buttons]

De betalingsopties van [!DNL PayPal payment buttons] bieden een eenvoudig, snel en veilig afrekeningsproces voor uw klant.

Zie [ de opties van Betalingen ](payments-options.md#paypal-smart-buttons) voor meer informatie.

Configureren [!DNL PayPal payment buttons]

U kunt de betalingsopties van de PayPal-betalingsknoppen inschakelen en configureren in de beheerfunctie:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_uit.
1. Vouw in de sectie _[!UICONTROL Payment Services]_de sectie_[!UICONTROL PayPal payment buttons]_ uit.
1. Als u de naam van de betalingsmethode wilt wijzigen, zoals wordt weergegeven tijdens het uitchecken, bewerkt u het veld _[!UICONTROL Title]_.
1. Om [ de betalingsactie ](production.md#set-payment-services-as-payment-method) te plaatsen, selecteer **[!UICONTROL Authorize]** of **[!UICONTROL Authorize and Capture]**.
1. Geef een `Numeric Only` -waarde op in het **[!UICONTROL Sort order]** -veld op als u de prioriteit van een betalingsmethode op de uitcheckpagina wilt bepalen.
1. Om [ toe te laten/onbruikbaar te maken betaal het Later overseinen ](payments-options.md#pay-later-button), uitgezocht `Yes`/ `No` voor **[!UICONTROL Display Pay Later Message]**.
1. Geef aan waar de PayPal-betalingsknoppen in Adobe Commerce zijn ingeschakeld door `Yes` in de volgende opties te selecteren:
   * **[!UICONTROL Show buttons on checkout page]**
   * **[!UICONTROL Show buttons on product detail page]**
   * **[!UICONTROL Show buttons in mini cart preview]**
   * **[!UICONTROL Show buttons on cart page]**
1. Als u Venmo wilt inschakelen als betalingsoptie, selecteert u `Yes` for **[!UICONTROL Venmo Enabled]** .
1. Selecteer `Yes` voor **[!UICONTROL Credit and Debit Card Enabled]** om krediet- en debetkaarten in te schakelen als betalingsoptie (PayPal Smart-knop).
1. Om [ PayPal te toelaten/onbruikbaar te maken betaalt later ](payments-options.md#pay-later-button) betalingsoptie, uitgezocht `Yes`/ `No` voor **[!UICONTROL PayPal Pay Later Enabled]**.
1. Als u de foutopsporingsmodus wilt inschakelen, selecteert u `Yes` voor **[!UICONTROL Debug Mode]** (`No` schakelt u deze uit).
1. Klik op **[!UICONTROL Save Config]** om de wijzigingen op te slaan.
1. Navigeer naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]** en klik vervolgens op **[!UICONTROL Flush Cache]** om alle ongeldige cache te vernieuwen.

### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Title] | winkelweergave | Voeg tijdens het afrekenen de tekst toe die als titel voor deze betalingsoptie moet worden weergegeven in de weergave Betalingsmethode. Opties: tekstveld |
| [!UICONTROL Payment Action] | website | De [ betalingsactie ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} voor de gespecificeerde betalingsmethode. Opties: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | website | Schakel het bericht Later betalen in of uit in het winkelwagentje, de productpagina, de miniwinkelwagentje en tijdens de afrekenstroom. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on checkout page] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit op de uitcheckpagina. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit op de pagina met productdetails. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit in de voorvertoning van de miniwinkelwagentje. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit op de tekstpagina. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | winkelweergave | Schakel de betalingsoptie van Venmo in of uit waar betalingsknoppen worden weergegeven. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | winkelweergave | Schakel de opties voor creditering en incasso in of uit waar de betalingsknoppen worden weergegeven. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | winkelweergave | De weergave van PayPal-betalingsopties voor latere betalingen in- of uitschakelen wanneer betalingsknoppen worden weergegeven. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | website | De foutopsporingsmodus in- of uitschakelen. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Knopstijl

U kunt ook de opties voor _[!UICONTROL Button style]_van de betaalknoppen configureren:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_uit.
1. Vouw in de sectie _[!UICONTROL [!DNL Payment Services]]_de sectie_[!UICONTROL PayPal Smart Button Styling]_ uit.
1. Selecteer `Vertical` of `Horizontal` for **[!UICONTROL Layout]** om de lay-out in te stellen
1. Selecteer een van de beschikbare kleuren in **[!UICONTROL Color]** om de kleur in te stellen.
1. Selecteer `Rectangular` of `Pill` for **[!UICONTROL Shape]** om de vorm in te stellen.
1. Selecteer `Yes` of `No` for **[!UICONTROL Use Default Height]** om de standaardhoogte te gebruiken.
1. Als u de aangepaste hoogte wilt instellen, voegt u de gewenste pixelhoogte voor **[!UICONTROL Height]** toe.
1. Selecteer `Yes` of `No` for **[!UICONTROL Tagline]** om de taglijn in te stellen.
1. Klik op **[!UICONTROL Save Config]** om de wijzigingen op te slaan.
1. Navigeer naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]** en klik vervolgens op **[!UICONTROL Flush Cache]** om alle ongeldige cache te vernieuwen.

U kunt betalingsknoopstileren [ in Montages ](settings.md#button-style) van het Huis van de Diensten van de Betaling ook vormen.

### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|--- |--- |--- |
| [!UICONTROL Layout] | Winkelweergave | Definieer de lay-outstijl voor PayPal-betalingsknoppen. Opties: `[!UICONTROL Vertical]` / `[!UICONTROL Horizontal]` |
| [!UICONTROL Color] | Winkelweergave | Geef de kleur van de PayPal-betalingsknoppen op. Opties: [!UICONTROL Blue] / `[!UICONTROL Gold]` / `[!UICONTROL Silver]` / `[!UICONTROL White]` / `[!UICONTROL Black]` |
| [!UICONTROL Shape] | Winkelweergave | Vorm van de PayPal-betalingsknoppen definiëren. Opties: `[!UICONTROL Rectangular]` / `[!UICONTROL Pill]` |
| [!UICONTROL Use Default Height] | Winkelweergave | Hiermee wordt gedefinieerd of voor PayPal-betalingsknoppen een standaardhoogte wordt gebruikt. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Height] | Winkelweergave | Bepaal de hoogte van de PayPal-betalingsknoppen. Standaardwaarde: geen |
| [!UICONTROL Label] | Winkelweergave | Definieer het label dat wordt weergegeven in de PayPal-betalingsknoppen. Opties: `[!UICONTROL PayPal]` / `[!UICONTROL Checkout]` / `[!UICONTROL Buynow]` / `[!UICONTROL Pay]` / `[!UICONTROL Installment]` |
| [!UICONTROL Tagline] | Winkelweergave | Hiermee schakelt u de taglijn in. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## De cache leegmaken

Als u de configuratie verandert, [ ontruim manueel het geheime voorgeheugen ](/help/payment-services/settings.md#flush-the-cache) zodat uw opslag de recentste configuratiemontages toont.
