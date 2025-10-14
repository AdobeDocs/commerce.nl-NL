---
title: De testsandbox instellen
description: Gebruik een Paypal- zandbakrekening om  [!DNL Payment Services]  op testwijze te gebruiken.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
feature: Payments, Checkout, Configuration, Install, Paas, Saas
source-git-commit: 870c2497a2d6dcfc4066c07f20169fc9040ae81a
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# De testsandbox instellen

Voordat u de sandbox aan boord gaat, moet u zich aanmelden voor een gratis PayPal Developer&#39;s account en zowel zakelijke accounts (voor onboarding) als winkelaccounts maken (voor het testen van uw afhandeling). U kunt desgewenst meerdere Developer-accounts maken.

Met een PayPal-sandboxaccount kunt u [!DNL Payment Services] gebruiken in de testmodus. PayPal vereist dat u een door PayPal Developer Portal gegenereerde Business-sandbox testaccount, e-mail en wachtwoord gebruikt voor sandboxen aan boord. *creeer geen andere rekening tijdens zandbak op het instappen proces.*

## Sandbox aan boord

Sandbox aan boord voltooien:

1. Navigeer aan de [&#x200B; pagina van de Rekening van de Ontwikkelaar van PayPal &#x200B;](https://developer.paypal.com/developer/accounts/).
1. Klik **[!UICONTROL Log in to Dashboard]** en login met uw bestaande Portaal-Gegenereerde Van Bedrijfs PayPal Ontwikkelaar sandbox testrekening of klik **Teken omhoog** om een rekening tot stand te brengen.
1. Een PayPal-sandboxaccount maken:
   1. Ga naar _[!UICONTROL Testing Tools]_>**[!UICONTROL Sandbox Accounts]**.
   1. Klik op **[!UICONTROL Create account]**.

      Als u een Paypal- zandbakrekening tijdens het zandbakPayPal op instapend proces creeerde, moet u [&#x200B; uw onboarding zandbak &#x200B;](#reset-your-sandbox-account) opnieuw instellen omdat of u kunt uw e-mail niet verifiëren.

   1. Selecteer **[!UICONTROL Business]** als het accounttype en klik op **[!UICONTROL Create]** .
   1. Klik in de sectie _[!UICONTROL Sandbox Accounts]_&#x200B;op de drie stippen in de kolom&#x200B;_[!UICONTROL Manage accounts]_ voor de sandboxaccount die u hebt gemaakt.
   1. Klik op **[!UICONTROL View/edit account]**.

      ![&#x200B; PayPal - Mening/geef zandbakrekening uit &#x200B;](assets/onboarding-viewedit-sandbox.png){width="300" zoomable="yes"}

   1. Kopieer en sla de e-mailid en het door het systeem gegenereerde wachtwoord op voor toekomstig gebruik.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Klik op **[!UICONTROL Sandbox onboarding]**.

   Deze optie is zichtbaar als u de sandbox voor [!DNL Payment Services] nog niet hebt voltooid.

   Een zandbak handelings identiteitskaart wordt auto-geproduceerd en bevolkt in [&#x200B; montages &#x200B;](configure-admin.md). Wijzig of wijzig deze id niet.

   Je krijgt een PayPal-venster te zien waarin je een PayPal-rekening verbindt om betalingen te accepteren.

1. Voer het e-mailadres en het wachtwoord in van de Paypal-sandboxaccount die u hebt gegenereerd in stap 3 (niet uw Paypal-zakelijke accountgegevens) en uw land of regio.
1. Klik op **[!UICONTROL Next]**.

   ![&#x200B; PayPal - Connect PayPal-rekening voor betalingen &#x200B;](assets/paypal-connectacct.png){width="300" zoomable="yes"}

1. Ga door met het volgen van de PayPal-stroom en gebruik de gegevens van uw eerder opgeslagen sandbox-account.
1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   De knop **[!UICONTROL Sandbox onboarding]** is niet meer zichtbaar en u ziet de tekst &quot;Sandbox-betalingen in behandeling&quot;.

Wanneer uw PayPal-sandbox is goedgekeurd, wordt een melding weergegeven dat uw betalingssysteem zich in de sandboxmodus bevindt en geen live betalingen verwerkt.

>[!IMPORTANT]
>
>Als u de toestemming van [!DNL Payment Services] for [!DNL Adobe Commerce] en [!DNL Magento Open Source] voor het verwerken van uw betalingen intrekt (in de instellingen van uw Paypal-account), kunnen bestellingen in uw winkel niet worden verwerkt door [!DNL Payment Services] . Op de homepage van Betalingsdiensten verschijnt een waarschuwing over de ingetrokken toestemming. Klik op **[!UICONTROL Do not show again]** om de waarschuwing te sluiten.

### Uw sandboxaccount opnieuw instellen

Als u een Paypal-sandboxaccount hebt gemaakt tijdens het PayPal-instapproces in de sandbox, moet u de instapsandbox opnieuw instellen, omdat of omdat u uw e-mail niet kunt verifiëren.

Uw sandboxaccount opnieuw instellen:

1. Klik op **[!UICONTROL Reset sandbox]**. [&#x200B; creeer een Paypal zaken zandbakrekening &#x200B;](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. Klik op **[!UICONTROL Sandbox onboarding]** en voer de volgende reeks stappen uit.

## Telefoonnummer van contactpersoon inschakelen

Met het telefoonnummer waarmee je contact kunt opnemen, kun je telefoonnummers opvragen die PayPal van je klanten ophaalt. PayPal verzamelt altijd telefoonnummers van PayPal-rekeninghouders om hun identiteit te bevestigen en contact met hen op te nemen om problemen op hun accounts op te lossen of om hun afhandeling te voltooien. PayPal ontmoedigt echter het gebruik van contacttelefoonnummers rechtstreeks van de handelaar, omdat dit negatieve gevolgen kan hebben voor de verkoop. Zie [&#x200B; PayPal krijgen de telefoonaantallen van het contactcontact &#x200B;](https://www.sandbox.paypal.com/businessmanage/preferences/website) documentatie voor meer informatie.

Deze functie is standaard ingesteld op `off` . Wanneer u het toelaat, kunnen de opslagbeheerders telefoonaantallen zien wanneer een klant een Branded stroom van de Controle buiten de controlepagina voltooit.

>[!IMPORTANT]
>
>Deze instelling is niet van toepassing op andere uitcheckstromen.

## Testen in sandboxomgeving

Het wordt ten zeerste aanbevolen testgegevensruimten te gebruiken voor integratie- en staging-omgevingen, en Betalingen in productie te testen met echte creditcards en banken, voordat u deze functionaliteit toegankelijk maakt voor klanten.

Zie [&#x200B; Testen en bevestigen &#x200B;](test-validate.md) voor meer informatie.
