---
title: Instellingen voor betalingsservices
description: Na installatie, kunt u  [!DNL Payment Services]  in het Huis vormen.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
feature: Payments, Checkout, Configuration, Paas, Saas
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '2420'
ht-degree: 0%

---

# Instellingen

U kunt [!DNL Payment Services] naar wens aanpassen met nuttige instellingen in het dialoogvenster [!DNL Payment Services] Home.

Als u [!DNL Payment Services] for [!DNL Adobe Commerce] en [!DNL Magento Open Source] click **[!UICONTROL Settings]** wilt configureren. Deze configuratieopties zijn slechts op het milieu van toepassing dat op het _[!UICONTROL Payment mode]_&#x200B;gebied van de[_ Algemene _configuratieopties ](#configure-general-settings) wordt geplaatst.

Voor multi-store of erfenisconfiguratie zie [ in Admin ](configure-admin.md) vormen.

## Algemene instellingen configureren

Met de instellingen van [!UICONTROL General] kunt u betalingsservices in- of uitschakelen als betalingsmethode en informatie toevoegen aan klanttransacties om een website of winkelweergave te markeren of voor te voegen met aangepaste informatie.

### Betalingsservices inschakelen

U kunt [!DNL Payment Services] inschakelen voor uw website en tests met sandboxen of live betalingen inschakelen.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

1. Klik op **[!UICONTROL Settings]**. Zie [ Inleiding aan  [!DNL Payment Services]  Huis ](payments-home.md) voor meer informatie.

   ![ Reageer montagesmening ](assets/react-settings-view.png){width="500" zoomable="yes"}

   De sectie _[!UICONTROL General]_&#x200B;bevat instellingen die worden gebruikt om [!DNL Payment Services] in te schakelen als betalingsmethode.

1. Als u [!DNL Payment Services] wilt inschakelen als betalingsmethode voor uw winkel, schakelt u _[!UICONTROL General]_&#x200B;in de sectie **[!UICONTROL Enable Payment Services as payment method]**&#x200B;in op `Yes` .

1. Als u nog [!DNL Payment Services] voor uw opslag test, plaats **de wijze van de Betaling** aan `Sandbox`. Als u live betalingen wilt inschakelen, stelt u deze in op `Production` .

1. Uw **[!UICONTROL Payment Services Sandbox ID]** en **[!UICONTROL Payment Services Production ID]** waarden worden automatisch bevolkt zodra u de [ Schakelaar van de Diensten van Commerce ](https://experienceleague.adobe.com/nl/docs/commerce-merchant-services/user-guides/integration-services/saas){target=_blank} opstelde en het [!DNL Payment Services] dashboard voor het eerst bezoekt. Doe dit om het instappen voor uw zandbak en/of productiemilieu&#39;s te beëindigen. Deze waarden koppelen uw SaaS-id aan [!DNL Payment Services] .

   >[!WARNING]
   >
   > Als u de id&#39;s van [!DNL Payment Services] opnieuw instelt, moet u opnieuw aan boord gaan.

1. Klik op **[!UICONTROL Save]**.

   Als u probeert weg van deze mening te navigeren zonder uw veranderingen op te slaan, verschijnt een modaal die u ertoe aanzet om veranderingen te verwerpen, het uitgeven te houden, of veranderingen te bewaren.

1. Navigeer naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]** en klik **[!UICONTROL Flush Cache]** om alle ongeldige caches te vernieuwen.

U kunt nu aan het veranderen van de standaardmontages voor [ betalingsopties ](#configure-payment-options) functies en storefront vertoning nu te werk gaan.

### soft descriptor toevoegen

U kunt een [!UICONTROL Soft Descriptor] toevoegen aan de configuratie van uw website(s) of afzonderlijke winkelweergave(s). Zachte beschrijvingen worden weergegeven op bankafschriften van klanttransacties. Als u bijvoorbeeld meerdere winkels/merken/catalogi hebt, kunt u deze eenvoudig afbakenen door aangepaste tekst toe te voegen aan het veld [!UICONTROL Soft Descriptor] .

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klik op **[!UICONTROL Settings]**. Zie [ Inleiding aan  [!DNL Payment Services]  Huis ](payments-home.md) voor meer informatie.
1. Selecteer in het vervolgkeuzemenu **[!UICONTROL Scope]** de website- of winkelweergave waarvoor u een elektronische descriptor wilt maken. Voor de eerste setup laat u deze waarde als **[!UICONTROL Default]** instellen.
1. Voeg uw aangepaste tekst (maximaal 22 tekens) toe aan het tekstveld en vervang `Soft descriptor` .
1. Klik op **[!UICONTROL Save]**.
1. U kunt als volgt een andere softdescriptor maken dan de geconfigureerde standaardwaarde voor een website- of opslagweergave:
   1. Selecteer in het vervolgkeuzemenu **[!UICONTROL Scope]** de website- of winkelweergave waarvoor u een elektronische descriptor wilt maken.
   1. Wissel _van_ af **[!UICONTROL Use website]** (of **[!UICONTROL Use default]**, afhankelijk van welk werkingsgebied u selecteerde).
   1. Voeg uw aangepaste tekst toe aan het tekstveld.
   1. Klik op **[!UICONTROL Save]**.
1. Om voor een website toe te laten of opslag bekijkt de standaardzachte beschrijver _of_ de zachte beschrijver die voor de ouderwebsite wordt gebruikt:
   1. Selecteer in het vervolgkeuzemenu **[!UICONTROL Scope]** de website- of winkelweergave waarvoor u een bestaande elektronische descriptor wilt inschakelen.
   1. Wissel _op_ **[!UICONTROL Use website]** (of **[!UICONTROL Use default]**, afhankelijk van het werkingsgebied u selecteerde).
   1. Klik op **[!UICONTROL Save]**.

   Als u probeert weg van deze mening te navigeren zonder uw veranderingen op te slaan, verschijnt een modaal die u ertoe aanzet om veranderingen te verwerpen, het uitgeven te houden, of veranderingen te bewaren.

### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Enable] | website | Schakel [!DNL Payment Services] voor uw website in of uit. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Payment mode] | winkelweergave | Plaats de methode, of het milieu, voor uw opslag. Opties: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Payment Services Sandbox ID] | winkelweergave | De bedrijfs-id van de sandbox, die automatisch wordt gegenereerd tijdens het aan boord nemen van de sandbox. |
| [!UICONTROL Payment Services Production ID] | winkelweergave | Uw bedrijfs-id voor productie, die automatisch wordt gegenereerd tijdens productie (live) aan boord. |
| [!UICONTROL Soft Descriptor] | website- of winkelweergave | Voeg een elektronische beschrijving toe aan uw website(s) en sla de weergave(en) op om informatie toe te voegen aan klanttransacties die merken, winkels of productlijnen afbakenen. Met de schakeloptie [!UICONTROL Use website] past u elke schermdescriptor toe die op websiteniveau is toegevoegd. Met de schakeloptie [!UICONTROL Use default] past u elke schermdescriptor toe die als standaard is toegevoegd. |

## Betalingsopties configureren

Nu u [!UICONTROL Payment Services] voor uw website hebt ingeschakeld, kunt u de standaardinstellingen voor betalingsfuncties en de storefront-weergave wijzigen.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klik op **[!UICONTROL Settings]**. Zie [ Inleiding aan  [!DNL Payment Services]  Huis ](payments-home.md) voor meer informatie.
1. Vorm betalingsopties voor [ creditcards ](#credit-card-fields), [ betalingsknopen ](#payment-buttons), en [ knoopstijl ](#button-style), per de volgende secties.

### Creditcardvelden

De _[!UICONTROL Credit Card Fields]_-instellingen bieden een eenvoudige en veilige afrekenoptie voor betalingsmethoden voor creditcard of bankpas.

Zie [ de opties van Betalingen ](payments-options.md#credit-card-fields) voor meer informatie.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Selecteer in het vervolgkeuzemenu van **[!UICONTROL Scope]** de winkelweergave waarvoor u een betalingsmethode wilt inschakelen.
1. Bewerk in de sectie **[!UICONTROL Credit card fields]** de waarde in het veld **[!UICONTROL Checkout title]** om de naam te wijzigen van de betalingsmethode die tijdens het uitchecken wordt weergegeven.
1. Om [ te plaatsen de betalingsactie ](production.md#set-payment-services-as-payment-method), knevel **[!UICONTROL Payment action]** aan `Authorize` of `Authorize and Capture`.
1. Geef een `Numeric Only` -waarde op in het **[!UICONTROL Sort order]** -veld op als u de prioriteit van een betalingsmethode op de uitcheckpagina wilt bepalen.
1. Om [ 3DS Veilige authentificatie ](security.md#3ds) toe te laten (`Off` door gebrek) knevel de **[!UICONTROL 3DS Secure authentication]** selecteur aan `Always` of `When required`.
1. Schakel de kiezer van **[!UICONTROL Show on checkout page]** in of uit als u creditcardvelden op de uitcheckpagina wilt in- of uitschakelen.
1. Om [ kaart toe te laten of onbruikbaar te maken die ](#card-vaulting) in- en uitschakelt, knevel de **[!UICONTROL Vault enabled]** selecteur.
1. Om [ in gebreke gebleven betalingsmethodes in Admin ](#card-vaulting) (voor verkopers toe te laten of onbruikbaar te maken om orden voor klanten in Admin te voltooien gebruikend hun in gebreke gebleven betalingsmethode), knevel de **[!UICONTROL Show vaulted methods in Admin]** selecteur.
1. Schakel de kiezer van **[!UICONTROL Debug Mode]** in of uit om de foutopsporingsmodus in of uit te schakelen.
1. Klik op **[!UICONTROL Save]**.

   Als u probeert weg van deze mening te navigeren zonder uw veranderingen op te slaan, verschijnt een modaal die u ertoe aanzet om veranderingen te verwerpen, het uitgeven te houden, of veranderingen te bewaren.

1. [ duw het geheime voorgeheugen ](#flush-the-cache).

#### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Title] | winkelweergave | Voeg de tekst die tijdens het afrekenen wordt weergegeven als titel voor deze betalingsoptie toe aan de weergave Betalingsmethode. Opties: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | De [ betalingsactie ](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} voor de gespecificeerde betalingsmethode. Opties: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | winkelweergave | De sorteervolgorde voor de opgegeven betalingsmethode op de uitcheckpagina. `Numeric Only` value |
| [!UICONTROL 3DS Secure authentication] | website | Laat of maak [ 3DS Veilige authentificatie ](security.md#3ds) toe onbruikbaar. Opties: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Show on checkout page] | website | In- of uitschakelen van creditcardvelden voor weergave op de afhandelingspagina. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Vault enabled] | winkelweergave | Laat toe of maak [ creditcard het vaulteren ](vaulting.md) onbruikbaar. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show vaulted payment methods in Admin] | winkelweergave | Laat of maak capaciteit voor koopman toe onbruikbaar om orden voor klanten in Admin [ te voltooien gebruikend een in kluizen uitbetaalde betalingsmethode ](vaulting.md). Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | website | De foutopsporingsmodus in- of uitschakelen. Opties: [!UICONTROL Off] / [!UICONTROL On] |

### Apple Pay

Met de betalingsoptie [!UICONTROL Apple Pay] voor knoppen kunt u via de Safari-browser een [!UICONTROL Apple Pay] betalingsknop opgeven voor het uitchecken van de winkel (voor maximaal 99 domeinen per zakelijke account).

U kunt Apple slechts gebruiken betaalt als u [ Apple voltooit betaal zelfregistratie via PayPal ](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) en dan [ vorm Apple betaalt ](settings.md/#payment-buttons) voor uw opslag. Zie [ de opties van Betalingen ](payments-options.md#apple-pay-button) voor meer informatie.

U kunt de knopbetalingsoptie [!UICONTROL Apple Pay] inschakelen en configureren:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Selecteer in het vervolgkeuzemenu van **[!UICONTROL Scope]** de winkelweergave waarvoor u een betalingsmethode wilt inschakelen.
1. Bewerk in de sectie **[!UICONTROL Apple Pay]** de waarde in het veld _[!UICONTROL Checkout title]_&#x200B;om de naam te wijzigen van de betalingsmethode die tijdens het uitchecken wordt weergegeven.
1. Om [ te plaatsen de betalingsactie ](production.md#set-payment-services-as-payment-method), knevel **[!UICONTROL Payment action]** aan `Authorize` of `Authorize and Capture`.
1. Schakel de kiezer van **[!UICONTROL Show Apple Pay on checkout page]** in of uit om Apple Pay op de afhandelingspagina in of uit te schakelen.
1. Schakel de kiezer van **[!UICONTROL Show Apple Pay on product detail page]** in of uit om Apple Pay op de pagina met productdetails in of uit te schakelen.
1. Schakel de kiezer van **[!UICONTROL Show Apple Pay on the mini cart preview]** in of uit om Apple Pay in te schakelen op de voorvertoning van de mini-winkelwagen.
1. Schakel de kiezer van **[!UICONTROL Show Apple Pay on cart page]** in of uit om Apple Pay op de winkelwagentpagina in of uit te schakelen.
1. Schakel de kiezer van **[!UICONTROL Debug Mode]** in of uit om de foutopsporingsmodus in of uit te schakelen.
1. Klik op **[!UICONTROL Save]**.

   Als u probeert weg van deze mening te navigeren zonder uw veranderingen op te slaan, verschijnt een modaal die u ertoe aanzet om veranderingen te verwerpen, het uitgeven te houden, of veranderingen te bewaren.

1. [ duw het geheime voorgeheugen ](#flush-the-cache).

#### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Checkout title] | winkelweergave | Voeg de tekst die tijdens het afrekenen wordt weergegeven als titel voor deze betalingsoptie toe aan de weergave Betalingsmethode. Opties: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | De [ betalingsactie ](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions) voor de gespecificeerde betalingsmethode. Opties: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | website | Schakel de button Apple Pay in of uit om op de afhandelingspagina weer te geven. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on checkout page] | website | Schakel de button Apple Pay in of uit om weer te geven op de pagina met productdetails. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on mini cart preview] | website | Schakel de button Apple Pay in of uit om de voorvertoning van de mini-winkelwagen weer te geven. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show on cart page] | website | Schakel de button Apple Pay in of uit om op de winkelwagentje te tonen. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | website | De foutopsporingsmodus in- of uitschakelen. Opties: [!UICONTROL Off] / [!UICONTROL On] |

### Betalingsknoppen

De betalingsopties van [!DNL PayPal payment buttons] bieden een eenvoudig, snel en veilig afrekeningsproces voor uw klant. Zie [ de opties van Betalingen ](payments-options.md#paypal-smart-buttons) voor meer informatie.

U kunt de betalingsopties van de PayPal-betalingsknoppen inschakelen en configureren:

1. Selecteer in het vervolgkeuzemenu van **[!UICONTROL Scope]** de winkelweergave waarvoor u een betalingsmethode wilt inschakelen.
1. Als u de naam van de betalingsmethode wilt wijzigen, zoals wordt weergegeven tijdens het uitchecken, bewerkt u de waarde in het veld **[!UICONTROL Checkout Title]** .
1. Om [ te plaatsen de betalingsactie ](production.md#set-payment-services-as-payment-method), knevel **[!UICONTROL Payment action]** aan `Authorize` of `Authorize and Capture`.
1. Geef een `Numeric Only` -waarde op in het **[!UICONTROL Sort order]** -veld op als u de prioriteit van een betalingsmethode op de uitcheckpagina wilt bepalen.
1. U kunt de weergavefuncties van [!DNL PayPal smart button] in- of uitschakelen met de schakelkiezers:

   - **[!UICONTROL Show PayPal buttons on product checkout page]**
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**
   - **[!UICONTROL Show PayPal Credit and Debit Card button]**

     >[!NOTE]
     >
     > Om Apple te gebruiken betaal u [ moet een de zandbaktesterrekening van Apple ](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account) (volledig met valse creditcard en het facturerings informatie) hebben om het te testen. Wanneer u bereid bent om Apple te gebruiken betaal in zandbak _of_ productiemodus, na het voltooien van om het even welke [ het testen en bevestiging ](test-validate.md#test-in-sandbox-environment), volledige [ zelfregistratie met  [!DNL Apple Pay] ](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_registreer uw levende domein_ sectie slechts) en [ vormt het voor uw opslag in  [!DNL Payment Services]](settings.md#payment-buttons).

     Terwijl u de zichtbaarheid van betalingsknoppen of het Later bericht PayPal Pay (PayPal Pay) in- of uitschakelt, wordt onder aan de pagina Settings een visuele voorvertoning van die configuratie weergegeven.

1. Schakel de kiezer van **[!UICONTROL Debug Mode]** in om de foutopsporingsmodus in te schakelen.
1. Klik op **[!UICONTROL Save]**.

   Als u probeert weg van deze mening te navigeren zonder uw veranderingen op te slaan, verschijnt een modaal die u ertoe aanzet om veranderingen te verwerpen, het uitgeven te houden, of veranderingen te bewaren.

1. [ duw het geheime voorgeheugen ](#flush-the-cache).

#### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Title] | winkelweergave | Voeg tijdens het afrekenen de tekst toe die als titel voor deze betalingsoptie moet worden weergegeven in de weergave Betalingsmethode. Opties: tekstveld |
| [!UICONTROL Payment Action] | website | De [ betalingsactie ](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/sales/payment-methods/payment-methods#payment-actions){target="_blank"} voor de gespecificeerde betalingsmethode. Opties: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | winkelweergave | De sorteervolgorde voor de opgegeven betalingsmethode op de uitcheckpagina. `Numeric Only` value |
| [!UICONTROL Show PayPal buttons on checkout page] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit op de uitcheckpagina. Opties: [!UICONTROL &#x200B; Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on product detail page] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit op de pagina met productdetails. Opties: [!UICONTROL &#x200B; Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit in de voorvertoning van de miniwinkelwagentje. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal buttons on cart page] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit op de tekstpagina. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later button] | winkelweergave | De weergave van betalingsopties voor latere betalingen in- of uitschakelen wanneer betalingsknoppen worden weergegeven. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Pay Later Message] | website | Schakel het bericht Later betalen in of uit in het winkelwagentje, de productpagina, de miniwinkelwagentje en tijdens de afrekenstroom. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Venmo button] | winkelweergave | Schakel de betalingsoptie van Venmo in of uit waar betalingsknoppen worden weergegeven. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show Apple Pay button] | winkelweergave | Schakel de betalingsoptie Apple Pay in of uit waar de betalingsknoppen worden weergegeven. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Show PayPal Credit and Debit card button] | winkelweergave | Schakel de betalingsoptie Creditcard en Creditcard in of uit wanneer betalingsknoppen worden weergegeven. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Debug Mode] | website | De foutopsporingsmodus in- of uitschakelen. Opties: [!UICONTROL Off] / [!UICONTROL On] |

### Knopstijl

U kunt ook de opties voor _[!UICONTROL Button style]_&#x200B;van de betaalknoppen configureren:

1. Selecteer `Vertical` of `Horizontal` om de **[!UICONTROL Layout]** te wijzigen.

   >[!NOTE]
   >
   > Als de knopstijl is geconfigureerd als `Horizontal` en uw winkel is geconfigureerd om meerdere betalingsknoppen weer te geven, worden mogelijk slechts twee knoppen weergegeven op de productpagina, de afhandelingspagina en de mini-cart, en één knop in het winkelwagentje.

1. Schakel de kiezer van **[!UICONTROL Show tagline]** in om de taglijn in een horizontale lay-out in te schakelen.
1. Als u **[!UICONTROL Color]** wilt wijzigen, selecteert u de gewenste kleuroptie.
1. Selecteer `Pill` of `Rectangle` als u de **[!UICONTROL Shape]** wilt wijzigen.
1. Schakel de kiezer van **[!UICONTROL Responsive button height]** in of uit om de knophoogteselector in te schakelen.
1. Als u **[!UICONTROL Label]** wilt wijzigen, selecteert u de gewenste labeloptie.

   Terwijl u de configuratieopties voor lay-out, kleur, vorm, hoogte en label wijzigt, wordt onder aan de pagina Instellingen een visuele voorvertoning van die configuratie weergegeven. In het beeld hieronder, wordt **[!UICONTROL Shape]** geplaatst aan _Rechthoek_ en **[!UICONTROL Label]** wordt geplaatst aan _(geadviseerde) PayPal_.

   ![[!DNL PayPal payment buttons] opties ](assets/payment-buttons.png){width="400" zoomable="yes"}

1. Klik op **[!UICONTROL Save]**.

   Als u probeert weg van deze mening te navigeren zonder uw veranderingen op te slaan, verschijnt een modaal die u ertoe aanzet om veranderingen te verwerpen, het uitgeven te houden, of veranderingen te bewaren.

1. [ duw het geheime voorgeheugen ](#flush-the-cache).

U kunt het stileren van de betalingsknoop [ in de configuratie van de Oudheid in Admin ](configure-admin.md#configure-paypal-smart-buttons) of hier in [!DNL Payment Services Home] vormen. Zie {de stijlgids van de Knopen van 0} PayPal [&#128279;](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) voor meer informatie over het stileren van PayPal betalingsknopen.

#### Configuratieopties

| Veld | Toepassingsgebied | Beschrijving |
|--- |--- |--- |
| [!UICONTROL Layout] | Winkelweergave | Definieer de lay-outstijl voor de betaalknoppen. Opties: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Winkelweergave | Taglijn in-/uitschakelen. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Color] | Winkelweergave | Geef de kleur van de betaalknoppen op. Opties: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Winkelweergave | Vorm van de betaalknoppen definiëren. Opties: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Winkelweergave | Definieert of voor de betalingsknoppen een standaardhoogte wordt gebruikt. Opties: [!UICONTROL Off] / [!UICONTROL On] |
| [!UICONTROL Height] | Winkelweergave | Geef de hoogte van de betaalknoppen op. Standaardwaarde: geen |
| [!UICONTROL Label] | Winkelweergave | Definieer het label dat in de betaalknoppen wordt weergegeven. Opties: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## Rollen configureren

Om ervoor te zorgen dat Admin-gebruikers in Commerce Admin orders kunnen maken en beheren, schakelt u [!DNL Payment Services] -specifieke bronnen in voor gebruikersrollen.

Zie {de rollen van 0} Gebruiker [&#128279;](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-user-roles.html?lang=nl-NL) leren hoe te om rollen te beheren.

Wanneer u bronnen toewijst aan de rol, moet u het volgende selecteren:

- **betaal met[!DNL Payment Services]** - Deze middel zorgt ervoor dat wanneer u een orde in Admin creeert, [!DNL Payment Services] creditcards beschikbaar als betalingsmethode zijn. Als u het **1&rbrace; oudermiddel van Acties &lbrace;selecteert, zal dit middel ook worden geselecteerd.**
- **[!DNL Payment Services]** - Dit middel omvat het **dashboard** en **Proxy van de Diensten SaaS** middelen, die ook moeten worden geselecteerd. Zij zorgen ervoor dat [!DNL Payment Services] in het _Verkoop_ menu verschijnt.

  {de middelen van de Diensten van 0} Betaling ![&#128279;](assets/roles-payments.png){width="400" zoomable="yes"}

## De cache leegmaken

Als u de configuratie in _Montages_ verandert, bijvoorbeeld het van een knevel voorzien van de Pay, Venmo, of PayPal PayLater knopen van Apple, spoel manueel het geheime voorgeheugen zodat uw opslag de recentste configuraties toont.

1. Voor _Admin_ sidebar, ga **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Klik op **[!UICONTROL Flush Cache]** om alle ongeldige cache te vernieuwen.

Als om het even welk Type van Geheime voorgeheugen in de lijst van het Beheer van het Geheime voorgeheugen een `INVALIDATED` status heeft, zou uw opslag niet de meest recente configuratie voor dat punt kunnen tonen. Duw het geheime voorgeheugen om uw opslag bij te werken om de recentste configuratie te tonen.

Om ervoor te zorgen dat uw opslag de correcte configuratie toont, verwijder periodiek [ het geheime voorgeheugen ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/cache-management).

## Kaart vauleren

U kunt functionaliteit inschakelen waarmee uw klanten hun creditcardgegevens in hun Mijn account kunnen opslaan en gebruiken voor toekomstige aankopen.

U kunt ook kaartvaulting in Admin gebruiken om verdere orden voor bestaande klanten te voltooien.

Laat of maak kaartvaulting in de [ montages van het kaartgebied van de Krediet ](#credit-card-fields) toe onbruikbaar.

Zie [ Kredietkaart die ](vaulting.md) voor meer informatie in kluizen.

## 3DS

3DS beschermt klanten en handelaren tegen frauduleuze activiteiten in hun winkels en maakt naleving van de EU-normen mogelijk.

Laat of maak 3DS in de [ montages van het kaartgebied van de Krediet ](#credit-card-fields) toe onbruikbaar.

Zie [ 3DS in Veiligheid ](security.md#3ds) voor meer informatie.

## Meerdere PayPal-accounts gebruiken

In [!UICONTROL Payment Services], kunt u veelvoudige rekeningen gebruiken PayPal binnen **één** commerciële rekening op het websiteniveau. Bijvoorbeeld, als u uw opslag(s) in veelvoudige landen (die verschillende [ munten ](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/site-store/currency/currency) gebruiken) in werking stelt of Adobe Commerce voor sommige delen van uw zaken maar niet _allen_ wilt gebruiken, kunt u opstelling uw handelende rekening om veelvoudige rekeningen te gebruiken PayPal.

Zie [ Plaats, Opslag, en het Toepassingsgebied van de Mening ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=nl-NL) voor meer informatie over de hiërarchie van websites, opslag, en opslagmeningen.

Zie [ bevel-lijn configuratie ](configure-cli.md#configure-scope-via-cli) voor meer informatie bij het vormen van werkingsgebied voor veelvoudige rekeningen PayPal via CLI.

Uw vertegenwoordiger van de Verkoop kan een nieuw [ werkingsgebied ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=nl-NL#scope-settings) voor uw handelaarrekening en op de extra plaats met PayPal tot stand brengen zodat om het even welke PayPal knopen u vormt om op uw plaats te verschijnen zal tonen. Neem contact op met uw verkoper voor hulp bij het gebruik van meerdere PayPal-accounts voor uw websites.
