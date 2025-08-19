---
title: '[!DNL Payment Services] Configuratie'
description: Na installatie, kunt u  [!DNL Payment Services]  in Admin bij de opslagconfiguratie vormen.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 870c2497a2d6dcfc4066c07f20169fc9040ae81a
workflow-type: tm+mt
source-wordcount: '2568'
ht-degree: 0%

---

# [!DNL Payment Services] Configuratie

U kunt [!DNL Payment Services] aan uw behoeften aanpassen met nuttige configuratieopties in Admin.

Wanneer u [!DNL Payment Services] for [!DNL Adobe Commerce] en [!DNL Magento Open Source] in de beheerfunctie configureert, zijn deze configuraties alleen van toepassing op de omgeving die is ingesteld in het _[!UICONTROL Method]_&#x200B;veld&#x200B;_[!UICONTROL General Configuration]_ . Wijzigingen die u aanbrengt in de configuratievelden, zijn onafhankelijk van het schakelen tussen de selectie van _[!UICONTROL Method]_. Als u van methode wisselt, worden de selecties niet opnieuw ingesteld.

## Algemene configuratie

U kunt [!DNL Payment Services] inschakelen voor uw winkel en uw _[!UICONTROL Merchant Location]_&#x200B;en het testen van sandboxen of live betalingen inschakelen in de sectie&#x200B;_[!UICONTROL General Configuration]_ .

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Stel het veld _[!UICONTROL Merchant Country]_&#x200B;in in de map&#x200B;_[!UICONTROL Merchant Location]_ . Als er geen _[!UICONTROL Merchant Country]_&#x200B;is opgegeven, wordt de lus&#x200B;_[!UICONTROL Default Country]_ uit de algemene configuratie gebruikt.
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_&#x200B;uit om de sectie&#x200B;_[!UICONTROL [!DNL Payment Services]]_ te openen.
1. Vouw in de sectie _[!UICONTROL [!DNL Payment Services]]_&#x200B;de sectie&#x200B;_[!UICONTROL General Configuration]_ uit.
1. Voor **laat** toe, plaats het aan `Yes` om [!DNL Payment Services] voor uw opslag toe te laten.
1. Voor **Methode**, plaats het aan `Sandbox` als u nog [!DNL Payment Services] voor uw opslag of `Production` test als u bereid bent om levende betalingen toe te laten.
1. Uw **[!UICONTROL Payment Services Sandbox ID]** en **[!UICONTROL Payment Services Production ID]** waarden worden automatisch bevolkt zodra u de [ Schakelaar van de Diensten van Commerce ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas){target=_blank} opstelde en het [!DNL Payment Services] dashboard voor het eerst bezoekt. Doe dit om het instappen voor uw zandbak en/of productiemilieu&#39;s te beëindigen. Deze waarden koppelen uw SaaS-id aan [!DNL Payment Services] .

   >[!WARNING]
   >
   > Als u uw ID voor de gegevensruimte in de Commerce Services-connector moet wijzigen, moet u de [!DNL Payment Services] -id opnieuw instellen. Klik **identiteitskaart van de Diensten van de Betaling van het Terugstellen** om uw identiteitskaart Sandbox terug te stellen. Als u de [!DNL Payment Services] Sandbox-id opnieuw instelt, moet u opnieuw aan boord gaan.

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
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_&#x200B;uit.
1. Vouw in de sectie _[!UICONTROL Payment Services]_&#x200B;de sectie&#x200B;_[!UICONTROL Credit Card Fields]_ uit.
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

## [!UICONTROL Fastlane]

[[!DNL Fastlane by PayPal] ](https://www.paypal.com/us/cshelp/article/what-is-fastlane-by-paypal-help1096) is een snelle en gemakkelijke manier om veilig online te betalen. Tijdens de controle van de Gast van de a **&#x200B;**, kunt u veilig uw kaart en verschepende details voor nog snellere aankopen in de toekomst opslaan.

Zie [ de opties van de Betaling ](payments-options.md#fastlane-button) voor meer informatie.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_&#x200B;uit.
1. Vouw in de sectie _[!UICONTROL Payment Services]_&#x200B;de sectie&#x200B;_[!UICONTROL Fastlane]_ uit.
1. Selecteer `Yes` voor **[!UICONTROL Enable Fastlane]** (`No` schakelt het uit) om het in te schakelen.

   >[!NOTE]
   >
   > Als [!UICONTROL Fastlane] is ingeschakeld, is de betalingsoptie [!UICONTROL Credit Card Fields] uitgeschakeld.

1. Voer bij **[!UICONTROL Title]** (indien nodig) tekst in om de naam van de betalingsmethode te wijzigen, zoals tijdens het uitchecken wordt getoond. De standaardtitel is `Credit Card (via Fastlane)`
1. Om [ de betalingsactie ](production.md#set-payment-services-as-payment-method) te plaatsen, selecteer **[!UICONTROL Authorize]** of **machtigt en vangt**.
1. Geef een `Numeric Only` -waarde op in het **[!UICONTROL Sort order]** -veld op als u de prioriteit van een betalingsmethode op de uitcheckpagina wilt bepalen.
1. Geef op of de branding van [!UICONTROL Fastlane] is ingeschakeld tijdens het uitchecken in Adobe Commerce door het veld **[!UICONTROL Enable messaging]** in te stellen op `Yes` .
1. Klik op **[!UICONTROL Save Config]** om de wijzigingen op te slaan.
1. Navigeer naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]** en klik vervolgens op **[!UICONTROL Flush Cache]** om alle ongeldige cache te vernieuwen.

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Enable Fastlane] | winkelweergave | Schakel [!DNL Fastlane] in of uit op de uitcheckpagina. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Title] | winkelweergave | Voeg de tekst die tijdens het afrekenen als titel voor deze betalingsoptie moet worden weergegeven, toe in de weergave Betalingsmethode. De standaardwaarde is `Credit Card (via Fastlane)` . Opties: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | website | De [ betalingsactie ](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) voor de gespecificeerde betalingsmethode. Opties: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | winkelweergave | De sorteervolgorde voor de opgegeven betalingsmethode op de uitcheckpagina. `Numeric Only` value |
| [!UICONTROL Enable messaging] | winkelweergave | Geef op of de branding van [!UICONTROL Fastlane] is ingeschakeld tijdens het uitchecken in Adobe Commerce. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

### Optioneel. Geavanceerde stijlinstellingen

Met deze optionele instellingen kunt u aanpassen hoe [!UICONTROL Fastlane] op uw website wordt weergegeven.

>[!TIP]
>
>De standaardinstellingen worden hersteld voor stijlen die niet aan de richtlijnen voor toegankelijkheid voldoen.

1. Navigeer in de sectie _[!UICONTROL Payment Services]_&#x200B;naar de sectie&#x200B;_[!UICONTROL Fastlane]_ .
1. Vouw de sectie _[!UICONTROL Advanced Style Settings (optional)]_&#x200B;uit.
1. Wijzig de instellingen naar wens.
1. Klik op **[!UICONTROL Save Config]** om de wijzigingen op te slaan.

Zie [ Dokken van de Ontwikkelaar van PayPal ](https://developer.paypal.com/limited-release/accelerated-checkout-bt/) voor meer informatie over aanpassing.

#### Basisinstellingen

Met deze optionele instellingen wijzigt u de algemene component [!UICONTROL Fastlane] checkout.

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Background Color] | winkelweergave | Definieert de achtergrondkleur van de component. Alleen `RGB` -waarden |
| [!UICONTROL Border Color] | winkelweergave | Definieert de randkleur van de component. Alleen `RGB` -waarden |
| [!UICONTROL Font Family] | winkelweergave | Hiermee stelt u het lettertype van de component in. Alleen de fonts die beschikbaar zijn in uw thema, worden weergegeven |
| [!UICONTROL Font Size Base] | winkelweergave | Hiermee definieert u de grootte van het lettertype. Alleen waarden `px` (pixel) |
| [!UICONTROL Padding] | winkelweergave | Hiermee stelt u de opvulling in de component in. Alleen waarden `px` (pixel) |
| [!UICONTROL Primary Color] | winkelweergave | Hiermee definieert u de hoofdkleur van de component. Alleen `RGB` -waarden |
| [!UICONTROL Text Color] | winkelweergave | Definieert de hoofdkleur van de tekst in de component. Alleen `RGB` -waarden |

#### Invoerinstellingen

Deze optionele instellingen zijn van toepassing op de invoervelden van de klant van de [!UICONTROL Fastlane] -component.

| Veld | Toepassingsgebied | Beschrijving |
|---|---|---|
| [!UICONTROL Background Color] | winkelweergave | Definieert de achtergrondkleur van de component. Alleen `RGB` -waarden |
| [!UICONTROL Border Color] | winkelweergave | Definieert de randkleur van de component. Alleen `RGB` -waarden |
| [!UICONTROL Border Radius] | winkelweergave | Hiermee definieert u de straal van de rand. Alleen waarden `px` (pixel) |
| [!UICONTROL Border Width] | winkelweergave | Hiermee definieert u de breedte van de rand. Alleen waarden `px` (pixel) |
| [!UICONTROL Focus Border Color] | winkelweergave | Definieert de kleur van de focusrand van de component. Alleen `RGB` -waarden |
| [!UICONTROL Text Color Base] | winkelweergave | Definieert de hoofdkleur van de tekst in de component. Alleen `RGB` -waarden |

## [!UICONTROL Apple Pay]

Met [!DNL Apple Pay] kunnen handelaren een veilige, snelle en naadloze afrekenervaring bieden in Safari. Deze biedt ondersteuning voor maximaal 99 domeinen per zakelijke account. Met de knop [!DNL Apple Pay] worden de betaling-, contact- en verzendgegevens automatisch ingevuld op het iOS- of macOS-apparaat van de klant. Zo kunt u snel en zonder tussenkomst aankopen uitvoeren die de conversietarieven kunnen verhogen.

Zie [ de opties van Betalingen ](payments-options.md#apple-pay-button) voor meer informatie.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_&#x200B;uit.
1. Vouw in de sectie _[!UICONTROL Payment Services]_&#x200B;de sectie&#x200B;_[!UICONTROL Apple Pay]_ uit.
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
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_&#x200B;uit.
1. Vouw in de sectie _[!UICONTROL Payment Services]_&#x200B;de sectie&#x200B;_[!UICONTROL Google Pay]_ uit.
1. (Optioneel) Wijzig de naam van de betalingsmethode die tijdens het afrekenen wordt weergegeven door de nieuwe naam in te voeren in het veld **[!UICONTROL Title]** .
1. [ plaats de betalingsactie ](production.md#set-payment-services-as-payment-method) door te selecteren **[!UICONTROL Authorize]** of **[!UICONTROL Authorize and Capture]**.
1. Geef aan waar de optie [!DNL Google Pay] in Adobe Commerce is ingeschakeld door `Yes` te selecteren in de volgende opties, indien nodig:
   * **[!UICONTROL Show Google Pay on checkout page]**
   * **[!UICONTROL Show Google Pay on product detail page]**
   * **[!UICONTROL Show Google Pay in mini cart preview]**
   * **[!UICONTROL Show Google Pay on cart page]**
1. Als u **[!UICONTROL 3D Secure authentication]** (`Off` standaard) wilt inschakelen, kiest u `Always` of `When required` .
1. Als u de foutopsporingsmodus wilt inschakelen, selecteert u `Yes` voor **[!UICONTROL Debug Mode]** (`No` schakelt u deze uit).
1. Configureer de weergave van de knop _[!UICONTROL Google Pay]_&#x200B;door de knoppen **[!UICONTROL Button Color]**,**[!UICONTROL Button Type]**&#x200B;en **[!UICONTROL Button Style]**&#x200B;naar wens te selecteren.
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

Zie [ documentatie van het de verzoekvoorwerp van Google van de Betaling API van 0&rbrace; &lbrace;voor meer informatie.](https://developers.google.com/pay/api/web/reference/request-objects)

## [!DNL PayPal Payment Buttons]

De betalingsopties van [!DNL PayPal payment buttons] bieden een eenvoudig, snel en veilig afrekeningsproces voor uw klant.

Zie [ de opties van Betalingen ](payments-options.md#paypal-smart-buttons) voor meer informatie.

Configureren [!DNL PayPal payment buttons]

U kunt de betalingsopties van de PayPal-betalingsknoppen inschakelen en configureren in de beheerfunctie:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_&#x200B;uit.
1. Vouw in de sectie _[!UICONTROL Payment Services]_&#x200B;de sectie&#x200B;_[!UICONTROL PayPal payment buttons]_ uit.
1. Als u de naam van de betalingsmethode wilt wijzigen, zoals wordt weergegeven tijdens het uitchecken, bewerkt u het veld _[!UICONTROL Title]_.
1. Om [ de betalingsactie ](production.md#set-payment-services-as-payment-method) te plaatsen, selecteer **[!UICONTROL Authorize]** of **[!UICONTROL Authorize and Capture]**.
1. Geef een `Numeric Only` -waarde op in het **[!UICONTROL Sort order]** -veld op als u de prioriteit van een betalingsmethode op de uitcheckpagina wilt bepalen.
1. Om [ toe te laten/onbruikbaar te maken betaal het Later overseinen ](payments-options.md#pay-later-button), uitgezocht `Yes`/ `No` voor **[!UICONTROL Display Pay Later Message]**.

   * Als u het [ Later overseinen van de Betaal ](payments-options.md#pay-later-button) toelaat, wordt een **[!UICONTROL Configure Messaging]** modale knoop getoond zodat kunt u de stijlen voor **[!UICONTROL PayPal Pay Later messaging]** plaatsen.

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
| [!UICONTROL Display Pay Later Message] | website | Schakel de PayPal Pay Later-berichten in of uit in het winkelwagentje, de productpagina, de mini-kar en tijdens de afrekenstroom. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Configure Messaging] | winkelweergave | Wijzig de PayPal Pay Later Messaging-stijlen. Opties: `[!UICONTROL Product page]` / `[!UICONTROL Cart]` |
| [!UICONTROL Show buttons on checkout page] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit op de uitcheckpagina. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit op de pagina met productdetails. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit in de voorvertoning van de miniwinkelwagentje. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | winkelweergave | Schakel [!DNL PayPal payment buttons] in of uit op de tekstpagina. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | winkelweergave | Schakel de betalingsoptie van Venmo in of uit waar betalingsknoppen worden weergegeven. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | winkelweergave | Schakel de opties voor creditering en incasso in of uit waar de betalingsknoppen worden weergegeven. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | winkelweergave | De weergave van PayPal-betalingsopties voor latere betalingen in- of uitschakelen wanneer betalingsknoppen worden weergegeven. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | website | De foutopsporingsmodus in- of uitschakelen. Opties: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Knopstijl

U kunt ook de opties voor _[!UICONTROL Button style]_&#x200B;van de betaalknoppen configureren:

1. Voor _Admin_ sidebar, ga **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Vouw in het linkerdeelvenster **[!UICONTROL Sales]** uit en kies **[!UICONTROL Payment Methods]** .
1. Vouw de sectie _[!UICONTROL FEATURED ADOBE PAYMENT SOLUTION]_&#x200B;uit.
1. Vouw in de sectie _[!UICONTROL [!DNL Payment Services]]_&#x200B;de sectie&#x200B;_[!UICONTROL PayPal Smart Button Styling]_ uit.
1. Selecteer `Vertical` of `Horizontal` for **[!UICONTROL Layout]** om de lay-out in te stellen
1. Selecteer een van de beschikbare kleuren in **[!UICONTROL Color]** om de kleur in te stellen.
1. Selecteer `Rectangular` of `Pill` for **[!UICONTROL Shape]** om de vorm in te stellen.
1. Selecteer `Yes` of `No` for **[!UICONTROL Use Default Height]** om de standaardhoogte te gebruiken.
1. Als u de aangepaste hoogte wilt instellen, voegt u de gewenste pixelhoogte voor **[!UICONTROL Height]** toe.
1. Selecteer `Yes` of `No` for **[!UICONTROL Tagline]** om de taglijn in te stellen.
1. Klik op **[!UICONTROL Save Config]** om de wijzigingen op te slaan.
1. Navigeer naar **[!UICONTROL System]** > **[!UICONTROL Cache Management]** en klik vervolgens op **[!UICONTROL Flush Cache]** om alle ongeldige cache te vernieuwen.

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

Als u de configuratie in _Montages_ verandert, bijvoorbeeld het van een knevel voorzien van de Pay, Venmo, of PayPal PayLater knopen van Apple, spoel manueel het geheime voorgeheugen zodat uw opslag de recentste configuraties toont.

1. Voor _Admin_ sidebar, ga **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Klik op **[!UICONTROL Flush Cache]** om alle ongeldige cache te vernieuwen.

Als om het even welk Type van Geheime voorgeheugen in de lijst van het Beheer van het Geheime voorgeheugen een `INVALIDATED` status heeft, zou uw opslag niet de meest recente configuratie voor dat punt kunnen tonen. Duw het geheime voorgeheugen om uw opslag bij te werken om de recentste configuratie te tonen.

Om ervoor te zorgen dat uw opslag de correcte configuratie toont, verwijder periodiek [ het geheime voorgeheugen ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management).

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

In [!UICONTROL Payment Services], kunt u veelvoudige rekeningen gebruiken PayPal binnen **één** commerciële rekening op het websiteniveau. Bijvoorbeeld, als u uw opslag(s) in veelvoudige landen (die verschillende [ munten ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency) gebruiken) in werking stelt of Adobe Commerce voor sommige delen van uw zaken maar niet _allen_ wilt gebruiken, kunt u opstelling uw handelende rekening om veelvoudige rekeningen te gebruiken PayPal.

Zie [ Plaats, Opslag, en het Toepassingsgebied van de Mening ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) voor meer informatie over de hiërarchie van websites, opslag, en opslagmeningen.

Zie [ bevel-lijn configuratie ](configure-cli.md#configure-scope-via-cli) voor meer informatie bij het vormen van werkingsgebied voor veelvoudige rekeningen PayPal via CLI.

Uw vertegenwoordiger van de Verkoop kan een nieuw [ werkingsgebied ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) voor uw handelaarrekening en op de extra plaats met PayPal tot stand brengen zodat om het even welke PayPal knopen u vormt om op uw plaats te verschijnen zal tonen. Contact opnemen met je verkoper
voor hulp bij het gebruik van meerdere PayPal-accounts voor uw websites.
