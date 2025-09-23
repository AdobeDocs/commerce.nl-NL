---
title: '[!DNL Payment Services] Opmerkingen bij de release'
description: Herzie de versienota's voor informatie over alle  [!DNL Payment Services]  versies.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 1f9bbcf1b9bc6a65190fd608f0c9489bccdd1c5d
workflow-type: tm+mt
source-wordcount: '4184'
ht-degree: 0%

---


# Aanvullende informatie

Deze releaseopmerkingen beschrijven de eerste versie van [!DNL Payment Services] en bevatten:

![ Nieuwe ](../assets/new.svg) Nieuwe eigenschappen
![ Vaste kwestie ](../assets/fix.svg) Oplossingen en verbeteringen
![ Bekende kwestie ](../assets/bug.svg) Bekende kwesties

Voor eigenschapveranderingen en moeilijke situaties die buiten de regelmatige versie van de eigenschapversie worden vrijgegeven, herzie de _Gehoste de dienstupdates_ secties.

Leer meer over aanstaande versies, productsteun, en welke versies van Adobe Commerce de [!DNL Payment Services] uitbreiding steunen, zie het programma van de Versie van Adobe Commerce [ ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) en [ de onderwerpen van de Beschikbaarheid van het Product ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## Gehoste service-updates

Deze versienota&#39;s beschrijven eigenschapveranderingen en moeilijke situaties die voorkwamen en buiten de regelmatige eigenschapversies voor de ontvangen dienst werden vrijgegeven.

+++Gehoste service-updates

_25 April, 2025_

![ Nieuwe kwestie ](../assets/new.svg)<!-- Issue PAY-6051 --> nu, [!DNL Payment Services] dashboard toont zowel de huidige uitbreidingsversie als de dashboardversie.

_Augustus 30, 2024_

![ Nieuwe kwestie ](../assets/new.svg)<!-- Issue PAY-5658 --> nu, kunnen de handelaren transacties door het Detail van de Betaling in het [ transactierapport ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) voor meer gedetailleerde en nauwkeurige gegevens van betalingsmethodes filtreren.

_15 juli 2024_

![ Nieuwe kwestie ](../assets/new.svg)<!-- Issue PAY-5571 --> nu, kunnen de handelaren transacties door de klant-e-mail van Commerce in het [ transactierapport ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) filtreren. Voer de e-mail van de klant in om transacties voor die specifieke e-mail te filteren.

_9 Juli, 2024_

![ Nieuwe kwestie ](../assets/new.svg)<!-- Issue PAY-5488 --> nu, kunnen de handelaren Commerce klantenidentiteitskaart als kolom in het [ transactierapport ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) bekijken helpen transacties identificeren die een bepaalde klant heeft geplaatst. Bovendien kunnen verkopers het transactierapport door deze klant-id van Commerce voor bijbehorende orders filteren.

_Maart 5, 2024_

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-5252 --> nu, kunnen de handelaren gegevens van de dashboardnetwerken kopiëren door de inhoud van één enkele cel te selecteren.

_10 oktober, 2023_

![ Nieuwe kwestie ](../assets/fix.svg)<!-- Issue PAY-4888 --> nu, kunnen de handelaren krediet en debetkaarttransacties door de laatste vier cijfers van het kaartaantal in het [ rapport van Transacties ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) filtreren.

_12 juli 2023_

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-4587 --> Een kwestie die in [!DNL Payment Services] 2.1.0 wordt geïntroduceerd versie die vergunningslege die door vorige uitbreidingsversies wordt geplaatst verhindert wordt nu opgelost. Handelaars die een willekeurige versie van [!DNL Payment Services] gebruiken, kunnen autorisaties annuleren.

_9 Juni, 2023_

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-4288 --> nu, kunnen de handelaren [ _slechts_ PayPal betaalknopen ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons) vormen - en _gebruiken_ niet de optie van de creditcardbetaling van PayPal. Op deze manier kunnen verkopers verschillende betalingsopties aanbieden, zoals de betalingsknoppen Venmo en PayPal, en een bestaande creditcardprovider gebruiken in plaats van de optie PayPal-creditcardbetaling.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-4050 --> Toegevoegde a [ mening van de gegevensvisualisatie ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view), die op het Huis van de Dienst van de Betaling, voor het rapport van de de betalingsstatus van de Orde verschijnt.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-4486--> Eerder, verscheen de PayPal knoop PayLater niet in controle voor Britse handelaren. Dat probleem is opgelost.

![ Vaste de gegevensvisualisatiemeningen van het 1} Rapport van de kwestie {verschijnen nu op ](../assets/fix.svg)<!-- Issue PAY-4485--> Huis wanneer [!DNL Payment Services] gehandicapt is.[!DNL Payment Services]

_Januari 25, 2023_

![ Bekende kwestie ](../assets/bug.svg)<!-- Issue PAY-4102 --> Nieuwe installaties van [!DNL Payment Services] kunnen de Diensten van Commerce niet vormen, die [!DNL Payment Services] inoperable teruggeven. U kunt dit probleem verhelpen door de extensie [!DNL Payment Services] bij te werken naar versie 1.5.3.

_12 September, 2022_

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-3705 --> `increment_id` is nu beschikbaar voor gebruik in het in overeenstemming brengen van uitbetalingen in externe systemen ERP. Het wordt verspreid aan [`custom_id` _en_ `invoice_id` ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), zichtbaar in zowel de PayPal webhaak als het handelaarsactiviteitendetail voor een uitbetaling.

_Augustus 31, 2022_

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3629 --> wanneer een nieuwe handelaar tot het [!DNL Payment Services] Huis voor het eerst toegang heeft, laadt de pagina nu onmiddellijk om de inhoud te tonen in plaats van te vereisen verfrist zich een pagina.

_9 augustus, 2021_

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-3420 --> Pay van Apple is nu beschikbaar als Slimme Knoop van PayPal. Deze [ betalingsoptie ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) laat klanten toe om de eigenschap van identiteitskaart van de Aanraking op hun iOS of apparaat van macOS te gebruiken om Apple te selecteren betaalt. Apple Pay verwerkt de betaling met de betalingsgegevens van de creditcard en de bankpas die op het apparaat zijn opgeslagen.

_Juni 28, 2021_

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-1720 --> Geschillen voor opslagorden zijn nu beschikbaar in [ het rapport van de de betalingsstatus van de Orde ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). U kunt geschillen oplossen door rechtstreeks vanuit [!DNL Payment Services] naar het PayPal Resolution Center te navigeren.

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-2854 --> de ervaringsverbeteringen van de Gebruiker van [!DNL Payment Services] Huis omvatten de capaciteit om een configuratie op het huidige overervingsniveau en verbeteringen aan de vertoning van de kopbal en de navigatie te wijzigen.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-2854 --> u kunt waarschuwingen nu zien wanneer u van zandbakwijze aan productiemodus overschakelt en wanneer u probeert weg van een mening met updates te navigeren die niet zijn bewaard.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-2761 --> U kunt de gegevens nu aanpassen die in het [ rapport van de de betalingsstatus van de Orde ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) en het [ rapport van Uitbetalingen ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) door kolommen te tonen of te verbergen gebruikend de de montagecontrole van de Kolom tonen.

+++

>[!NOTE]
>
> De versies komen vaak voor om nieuwe eigenschappen en moeilijke situaties te leveren zoals nodig. De releaseplanning is niet vast.

## v2.12.2

_23 September, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-6275 --> Geweigerde [!DNL Fastlane] transacties op vangstwijze leiden niet meer tot orden in Commerce.

## v2.12.1

_18 september, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-6164 --> nu, [!DNL Payment Services] gebruikt basismunt voor de beschikbare het verschepen methodes in de **server-kant van PayPal verzendende callback (SSSC)**.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-6267 --> het **verschepen aan** blok is verborgen op de controlepagina wanneer **In-Store Bestelwagen (ISPU)** wordt geselecteerd.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-6271 --> nu, [!DNL Payment Services] vertoningen bewaarde creditcarddetails van PayPal PayFlow in de **Rekening van de Klant** > **Opgeslagen sectie van de Methoden van de Betaling**.

## v2.12.0

_Augustus 20, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- PAY-6022 --> [ Fastlane ](https://experienceleague.adobe.com/en/docs/commerce/payment-services/payments-checkout/payments-options) biedt een snellere aankoop tijdens gastcontroles aan.

![ Nieuw ](../assets/new.svg)<!-- PAY-6168 --> voegde de [`addProductsToNewCart` ](https://developer.adobe.com/commerce/webapi/graphql/payment-services-extension/mutations/) mutatie aan [!DNL Payment Services] toe om vlottere overgangen en beter karthergebruik toe te laten.

![ Nieuw ](../assets/new.svg)<!-- PAY-6169 --> voegde de [`setCartAsInactive` ](https://developer.adobe.com/commerce/webapi/graphql/payment-services-extension/mutations/) mutatie aan [!DNL Payment Services] toe om het beheer van de citaatlevenscyclus te verbeteren.

![ Nieuw ](../assets/new.svg)<!-- PAY-6227 --> wanneer het controleren met PayPal, [!DNL Payment Services] slaat pop-up van de ordesbevestiging voor een sneller aankoopproces over.

![ Nieuw ](../assets/new.svg)<!-- PAY-6234 --> voegde een nieuwe eigenschap voor de [ betaaloptie van de Betaal Later ](https://experienceleague.adobe.com/en/docs/commerce/payment-services/payments-checkout/payments-options) toe. Nu, verstrekt de BNPL overseinenconfigurator meer flexibiliteit in het tonen van het overseinen van het Betalen Later BNPL op de pagina&#39;s van de klantenkassa.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5505 --> nu, [!DNL Payment Services] plaatst het citaat als inactief wanneer een Google Pay of PayPal pop-up binnen de productpagina wordt gesloten.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5754 --> In [!DNL Payment Services] kunnen geen bestellingen meer worden gemaakt op basis van lege aanhalingstekens.

## v2.11.1

_Maart 14, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5849 --> Vaste een kwestie die [ Punten van de Lijn ](line-items.md) tijdens controle beïnvloedde. Nu, [!DNL Payment Services] heeft de betrouwbaarheid van het controleproces voor **Punten van de Lijn** verbeterd. Als u een soortgelijk probleem tegenkomt, neemt u contact op met uw [!DNL Payment Services] -vertegenwoordiger voor hulp.

## v2.11.0

_Maart 13, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer


![ Nieuw ](../assets/new.svg)<!-- PAY-5938 --> nu, [!DNL Payment Services] staat verkopers toe om betalingsmontages te beheren om flexibiliteit in hun zaken te maximaliseren. Deze versie verbetert de capaciteit om [ veelvoudige rekeningen PayPal ](https://experienceleague.adobe.com/en/docs/commerce/payment-services/configure/settings#use-multiple-paypal-accounts) voor de gebieden en de merken vast te maken een handelaars steunt. Ons verkoopteam kan een koppeling aan boord bieden om uw website in te stellen en weergavebereiken op te slaan.

![ Nieuw ](../assets/new.svg)<!-- PAY-5968 --> nu, [!DNL Payment Services] werkt de configuratie Admin met **PayPal Merchant identiteitskaart** en **PayPal Merchant Status** waarden bij. Deze waarden geven verkopers meer inzicht in hun status van hun PayPal-rekening.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5816 --> herstelde normale ordefunctionaliteit in [!DNL Payment Services] door een kwestie op te lossen die fouten in alle orde plaatsingen met versie v2.9.0 veroorzaakte.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5825 --> Vaste een kwestie waar Apple Pay mini-kart onjuiste geschatte totalen URL voor het programma geopende klanten gebruikte. Nu zorgt [!DNL Payment Services] voor nauwkeurige totale berekeningen.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5826 --> Verbeterde betrouwbaarheid van het ordebeheer door een kwestie op te lossen die een fout van HTTP 500 wanneer het veranderen van de citaatstatus in `inactive` veroorzaakte.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5849 --> een kwestie waar `LineItemProvider` uitzonderingen voor decimale hoeveelheden onder 1 wierp. Nu biedt [!DNL Payment Services] betere ondersteuning voor breukhoeveelheden.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5868 --> Vaste een fout van het geschenkkaartbedrag tijdens controle. [!DNL Payment Services] zorgt nu voor nauwkeurige waarden tijdens het uitrekenen.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5911 --> Opgeloste fouten tijdens ladingsverwezenlijking voor orden geplaatst gebruikend niet [!DNL Payment Services] online betalingsmethodes, die algemene betrouwbaarheid verbeteren.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5954 --> [!DNL Payment Services] biedt nu een vloeiender afrekenervaring door een probleem op te lossen waarbij Apple Pay geen bestelling heeft geplaatst toen een andere creditcard in de portemonnee was geselecteerd.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-5971 --> [!DNL Payment Services] leidt klanten niet meer naar de pagina voor het controleren van bestellingen wanneer Apple Pay mislukt, waardoor onnodige onderbrekingen van het afrekenen worden voorkomen.

## v2.10.3

_24 Februari, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-xxxx --> Verbeterde algemene stabiliteit en prestaties.

![ Vaste kwestie ](../assets/fix.svg)<!-- PAY-xxxx --> Algemene verbeteringen en optimalisaties. Correctie van kritieke fouten van v2.10.2.

## v2.10.2

_21 Februari, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Bekende kwestie ](../assets/bug.svg)<!-- PAY-xxxx --> bevat kritieke insecten die stabiliteit en prestaties kunnen beïnvloeden. Adobe raadt aan een upgrade naar v2.10.3 uit te voeren in plaats van deze versie te gebruiken (v2.10.2).

## v2.10.1

_5 Februari, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- PAY-5813 --> Toegevoegde steun voor Adobe Commerce 2.4.8 en PHP 8.4.

## v2.10.0

_December 13, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- PAY-5702 --> [!DNL Payment Services] biedt nu ondersteuning voor GraphQL-eindpunten voor archivering zonder aankoop, zodat klanten hun betalingsmethoden kunnen opslaan zonder een transactie te voltooien.

![ Nieuw ](../assets/fix.svg)<!-- PAY-5789 --> [!DNL Payment Services] steunt nu [ 3D Veilige authentificatie met Google Betalen ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/security-compliance/security#3ds), die veiligheid voor handelaren en klanten tijdens betalingstransacties verbeteren.

![ Repareren ](../assets/fix.svg)<!-- PAY-5703 --> [!DNL Payment Services] voegt de capaciteit voor [ klanten toe om kaarten direct in hun **Mijn Rekening** te bewaren ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting), verbeterend gemak en vereenvoudigend toekomstige controles. `Vault without purchase functionality might not be 100% compatible with Adobe Commerce 2.4.4 due to a known issue with` [`GraphQL authorization mechanisms` ](https://developer.adobe.com/commerce/webapi/graphql/usage/authorization-tokens/).

![ bevestig ](../assets/fix.svg)<!-- PAY-5762 --> een kwestie waar de couponcodes niet werden toegepast op de pagina van het ordeoverzicht toen de orde van de pagina van het productdetail (PDP) in werking werd gesteld.

![ Repareren ](../assets/fix.svg)<!-- PAY-5792 --> [!DNL Payment Services] toont nu beschrijvingen en het facturerings adressen voor [ gefactureerde kaarten op de controlepagina ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting), die klanten meer zicht in hun bewaarde betalingsmethodes geven.

![ Repareren ](../assets/fix.svg)<!-- PAY-5793 --> Met [!DNL Payment Services] kunnen verkopers het factuuradres voor gefactureerde kaarten direct vanaf de afhandelingspagina opslaan, zodat ze nauwkeurige en volledige betalingsgegevens kunnen opslaan.

## v2.9.0

_7 November, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- PAY-5629 --> [!DNL Payment Services] steunt nu een **bevorderd SDK URL voor Apple Betalen**, die de integratie voor verkopers verbeteren gebruikend Apple Pay. Deze functie is compatibel met macOS 14 en hoger. Apparaten met eerdere versies van macOS geven deze functionaliteit niet weer.

![ Nieuw ](../assets/new.svg)<!-- PAY-5630 --> werkte de **Controle** bij, **Product**, **Kaart**, en **MiniCart** pagina&#39;s om **promoot SDK URL voor Apple Betalen**, verbeterend de gebruikerservaring voor handelaren die Apple als betalingsoptie aanbieden.

![ Nieuwe ](../assets/new.svg)<!-- PAY-5635 --> Verbeterde verzendingsramingen **die op het adres van het Betalen van Apple** worden gebaseerd, die klanten toestaan om nauwkeurige verzendkosten tijdens controle te bekijken.

![ Vaste diverse ](../assets/fix.svg)<!-- PAY-5661 --> kwesties **[!DNL Payment Services]herstellen bij controle**, die de betrouwbaarheid van het betalingsproces voor handelaren en kopers verbeteren.

![ bevestig ](../assets/fix.svg)<!-- PAY-5692 --> een kwestie waar de **eerste en laatste namen van de klant** niet aan de orde werden toegevoegd wanneer het gebruiken van **slimme knopen voor uitdrukkelijke controle**.

![ bevestig ](../assets/fix.svg)<!-- PAY-5712 --> een kwestie opgelost waar de handelaren **niet uitchecken konden voltooien gebruikend de Nul Subtotal de betalingsoptie van de Uitbetaling** toen het totale bedrag vrij was.

## v2.8.1

_13 September, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ bevestig ](../assets/fix.svg)<!-- PAY-5644 --> een kwestie met het geheime voorgeheugen van de parameters van SDK wanneer het gebruiken van veelvoudige werkingsgebied in [!DNL Payment Services]. De configuratie van SDK wordt nu in het voorgeheugen ondergebracht afzonderlijk voor elk werkingsgebied in plaats van onder één enkele sleutel. Dit zorgt ervoor dat het geheime voorgeheugen van elk werkingsgebied onafhankelijk ongeldig wordt gemaakt, verbeterend betrouwbaarheid wanneer het beheren van veelvoudige werkingsgebieden.

## v2.8.0

_13 September, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- PAY-5499 --> [!DNL Payment Services] steunt nu het verzenden van het volgen aantalinformatie naar PayPal wanneer a [ het volgen aantal ](track-shipment.md) in Adobe Commerce is ingegaan.

![ Repareren ](../assets/fix.svg)<!-- PAY-5626 --> [!DNL Payment Services] heeft het aanvraagproces voor het handelsregister geoptimaliseerd wanneer klanten de Commerce-pagina voor afrekenen bezoeken. Er zijn eerder afzonderlijke aanvragen ingediend voor elke betalingsmethode (Gehoste velden, Google Pay, Apple Pay en Smart Buttons). Deze verbetering vermindert het aantal vraag, verbeterend prestaties en efficiency tijdens het controleproces.

![ Repareren ](../assets/fix.svg)<!-- PAY-5645 --> [!DNL Payment Services] voorkomt nu dat het PayPal/Google-pop-upmenu wordt geopend als de verkoper niet heeft ingestemd met aangepaste voorwaarden die door de verkoper zijn gemaakt op de afhandelingspagina.

![ Repareren ](../assets/fix.svg)<!-- PAY-5648 -->  [!DNL Payment Services] heeft een probleem opgelost met betrekking tot de verdeling van de belasting over de line-items op het PayPal-portaal. Als er belasting is gekoppeld aan de verzendkosten van een bestelling, wordt de belasting opgenomen als onderdeel van de verzendkosten en wordt deze belasting weergegeven in de details van de lijstitem die worden weergegeven in het PayPal-portaal.

## v2.7.0

_Augustus 2, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- PAY-4844 --> [!DNL Payment Services] steunt nu [ gegevens van het lijnpunt op het ordeniveau ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/payments-checkout/manage/line-items). Met deze functie kunnen handelaren gedetailleerde informatie over de artikelen in een bestelling bekijken, zoals productdetails, hoeveelheid en prijs (inclusief BTW, kortingen en andere relevante informatie).

![ Nieuw ](../assets/new.svg)<!-- PAY-5380 --> [!DNL Payment Services] verbetert de [ Configuratie in de Admin ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/configure/configure-admin#general-configuration) ervaring voor handelaren voor een gemakkelijker en intuïtiever aan boord gaan proces. Met deze functie kunnen verkopers hun [!DNL Payment Services] id&#39;s opnieuw instellen.

![ Nieuw ](../assets/new.svg)<!-- PAY-5255 --> [!DNL Payment Services] omvat a [ bericht van de mislukking van de Betaling ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-payment-failed-emails). Deze functie biedt vrijwel realtime meldingen van betalingsfouten aan handelaren, zodat bestellingen kunnen worden opgeslagen door naar de winkel te gaan en de probleemoplossing mogelijk te verbeteren.

![ bevestig ](../assets/fix.svg)<!-- PAY-5469 --> een kwestie waar **pop-up van de Betaal Google door Safari** werd geblokkeerd. Kopers kunnen nu hun Google Pay-betalingstransacties uitvoeren op Safari.

![ beval ](../assets/fix.svg)<!-- PAY-5492 --> een kwestie vast wanneer een handelaar aangepaste termijnen en voorwaarden aan de controlepagina toevoegt. Tijdens een [ uitdrukkelijke controle ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options#standard-vs-advanced-payments-experience) heeft een verkoopster nu de capaciteit om deze termijnen en voorwaarden goed te keuren om de controle zonder enige kwesties te voltooien.

![ bevestig ](../assets/fix.svg)<!-- PAY-5532 --> Verbeterde functionaliteit In-Store Pickup (ISPU) met **InstantPurchase**. {de methodes van de Levering ISPU **worden niet meer getoond wanneer een verkoopster een orde met** InstantPurchase **plaatst.**

![ Vaste een kwestie binnen de ](../assets/fix.svg)<!-- PAY-5606 --> het landkiezer van de Pagina van de Configuratie **die voorkwam wanneer het land van de handelaar aan** Duitsland **wordt geplaatst.**

## v2.6.0

_4 Juni, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- PAY-4877 --> nu, [!DNL Payment Services] steunt [ L2/L3 tariferingsmogelijkheden ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/levels-card-payment-transactions.html). Deze functie is alleen beschikbaar voor [!DNL Payment Services] klanten met IC++-prijzen ingeschakeld. Neem contact op met uw [!DNL Payment Services] -accountmanager als u L2/L3-verwerkingsgegevens wilt gebruiken voor [!DNL Payment Services] .

![ Repareren ](../assets/fix.svg)<!-- PAY-5455 -->[!DNL Payment Services] staat u toe om Apple direct van de uitbreiding toe te laten zonder het [ dossier van de domeinvereniging te downloaden en te ontvangen ](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).

## v2.5.0

_23 April, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Repareren ](../assets/fix.svg)<!-- Issue PAY-5396 -->[!DNL Payment Services] steunt nu [ richtlijnen van Adobe Commerce voor de `--db-prefix` parameter ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced#install-from-the-command-line) voor versies 2.4.7 van Adobe Commerce en nieuwer.

## v2.4.3

_16 april 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ beval ](../assets/fix.svg)<!-- Issue PAY-5106 --> een kwestie die verkeerd de totalen van het ordebedrag tijdens controle tussen PayPal en Adobe Commerce bevolkte. Handelaars kunnen er nu voor zorgen dat de totalen van het orderbedrag correct zijn wanneer ze een bestelling plaatsen.

## v2.4.2

_11 april 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- Issue xxx --> Toegevoegde steun voor Adobe Commerce 2.4.7.

## v2.4.1

_4 April, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ bevestig ](../assets/fix.svg)<!-- PAY-5322 --> een PCI compatibiliteitskwestie met de nieuwere versies van Adobe Commerce. Nu is [!DNL Payment Services] aangepast aan de betalingsvereisten in Adobe Commerce.

![ Fix ](../assets/fix.svg)<!-- PAY-5323 --> PayLater en Venmo worden correct getoond in Adobe Commerce. Probleem verholpen waarbij de optie voor het in- en uitschakelen van PayLater en Venmo niet werd toegestaan voor de beheerder.

## v2.4.0

_Maart 20, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- PAY-4868 --> Merchants kunnen [ met succes betalen Google door de aankoopervaring ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html) vormen, gelijkend op andere betalingsknopen in [!DNL Payment Services] door Admin.

![ Nieuw ](../assets/new.svg)<!-- PAY-4381 --> [ de Diensten van de Betaling steunt Google betalen door GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/payment-services/) toestaand verkopers om een koploze ervaring van Commerce met de betalingsmethode van Google te hebben.

![ Nieuw ](../assets/new.svg)<!-- PAY-4878 --> nu, wordt de [!DNL Payment Services] basiscontroleeigenschap gebundeld voor de handelaars van Adobe Commerce en van Magento Open Source.[!DNL Payment Services] kan nu handelaren met bedrijven in 200 geografische gebieden wereldwijd ondersteunen.[!DNL Payment Services] standaardafhandeling biedt opties voor debiteren/crediteren, PayPal, Venmo (indien beschikbaar) en PayLater (indien beschikbaar) in een systeem voor automatische inboeking.

![ verbeter ](../assets/fix.svg)<!-- PAY-5291 --> Ontvangend betalingsbevestiging voor sommige transacties kan worden vertraagd. In dat geval kunnen verkopers nu een bijgewerkte betalingsstatus voor een bestelling krijgen. [ de diensten van de Betaling ontdekt de hangende status van een betalingstransactie ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html) in een orde door hangende transacties te ontdekken en deze transacties proactief te controleren en bij te werken wanneer de hangende status is gevangen.

## v2.3.4

_Maart 1, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- PAY-5244 --> Vaste async controleverenigbaarheid.

![ bevestig ](../assets/fix.svg)<!-- PAY-5253 --> een fout waar een kluisteken dat niet tot [!DNL Payment Services] behoort niet kon worden geschrapt.

## v2.3.3

_14 Februari, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- PAY-5048 --> Toegevoegde steun voor PHP 8.3

![ bevestig ](../assets/fix.svg)<!-- PAY-5048 --> een fout met de `is_deleted` vlag. Bestellingen mislukken nu niet omdat de status `Rejected` is verzonden vanuit de extensie.

## v2.3.2

_Januari 26, 2024_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ bevestig ](../assets/fix.svg)<!-- PAY-5183 --> Vaste REST/GraphQL prestatieskwesties. De creditcardknop wordt nu weergegeven wanneer deze via de API wordt opgehaald.

## v2.3.1

_7 December, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- PAY-5047 --> Het merk van de krediet/debetkaart of het type van betalingsmethode is nu beschikbaar bij de volgende plaatsen:
- de pagina van de klantenorde op de winkel
- het bevestigingsbericht voor bestelling dat naar de klant is verzonden
- van de [ mening van de orde details ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) in Commerce Admin.

## v2.3.0

_December 1, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- PAY-4381 --> [ de Diensten van de Betaling steunt nu de integratie van GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). Met GraphQL-ondersteuning voor PayPal-betalingsknoppen, gehoste velden en Apple Pay, biedt [!DNL Payment Services] nu ondersteuning voor Commerce-instellingen zonder kop.

## v2.2.1

_27 September, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-4870 --> Vaste een kwestie die correct het nieuwe kopbalattribuut in Storefront bevolkte toen het verzenden van de uitbreidingsversie met de recentste versie. Eerder, met de `1.3.0` release van de Commerce Services-connector, kon u de `User-Agent header` niet uitbreiden vanuit de [!DNL Payment Services] -extensie.

## v2.2.0

_Augustus 30, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- PAY-4638 --> voegde een [ integratie met het Ondertekenen ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html) toe, die de geautomatiseerde diensten van de fraudebescherming verleent.

![ Nieuw ](../assets/new.svg)<!-- PAY-3981 --> [ Bevorderde Apple Betalen aan een afzonderlijke betalingsoptie ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button), buiten de PayPal betaalknopen, om winkelzichtbaarheid van de betalingsoptie te verhogen en handelaars toe te staan om de plaatsing en het stileren van het Betaal van Apple te controleren.

![ Nieuw ](../assets/new.svg)<!-- PAY-4002 --> verbeterde de gebruikerservaring van de controle van creditcardgebieden, met inbegrip van het stileren verhogingen zoals het toevoegen van betalingspictogrammen, aan lagere van de winkelcognitieve lading en verhogingsomzettingen.

![ Nieuwe ](../assets/new.svg)<!-- PAY-4002 --> Toegevoegde functionaliteit om handelaren toe te staan om de orde van hun betalingsopties [ te sorteren om bepaalde betalingsopties voorrang te geven. ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) Deze functionaliteit moedigt een hoger tarief van het controlegesprek aan.

![ Nieuwe ](../assets/new.svg)<!-- PAY-4035 --> Merchants kunnen nu efficiënt de gezondheid van hun opslag controleren en om het even welke transactiekwesties identificeren gebruikend het nieuwe [ rapport van Transacties ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) beschikbaar bij de [!DNL Payment Services] Admin homepage. In het verslag worden ook gegevens gepresenteerd over de percentages van de transactievergunning en de negatieve tendensen in de transacties.

## v2.1.0

_9 Juni, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- Issue xxx --> Toegevoegde steun voor Adobe Commerce 2.4.7-bèta1.

![ Nieuwe ](../assets/new.svg)<!-- Issue xxx --> toegevoegde [ beschikbaarheid in de volgende landen en bijbehorende valuta ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability): Australië, Frankrijk, Verenigd Koninkrijk.

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-4296 --> Toegevoegde [ uitgebreide middelen voor rollen Admin ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) om Admin gebruikers te verzekeren kunnen orden voor klanten tot stand brengen en beheren en kunnen [!DNL Payment Services] in het menu van de Verkoop zien.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-4236 --> Toegevoegde [ auto-voiding voor orden die fouten tijdens controle ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error) veroorzaken.

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-4183 --> Gemaakt functionaliteit aan [ toont de knoop van de de optietoewijzing van de creditcard/debetkaart ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) op de controlepagina.

## v2.0.0

_Maart 10, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-4152 --> Toegevoegde steun voor PHP 8.2 en Adobe Commerce 2.4.6. Niet compatibel met PHP 7.x.

## v1.6.1

_Maart 10, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.4 en nieuwer

![ bevestig ](../assets/fix.svg)<!-- Issue PAY-4226 --> een kwestie die nieuwe [!DNL Payment Services] verkopers verhinderde controle in Admin te gebruiken.[!DNL Payment Services] gebruikte eerder de Commerce-klant-id, die niet bestaat voor nieuwe klanten.

![ bevestig ](../assets/fix.svg)<!-- Issue PAY-4205 --> een kwestie die de gespecificeerde het verschepen adresstaat veroorzaakte om door de staat in de standaard belastingmontages tijdens controle worden vervangen gebruikend de [ optie PayPal ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). Nu kunnen klanten hun bestellingen naar een andere staat laten verzenden dan die welke in de belastinginstellingen van de handelaar als standaard is geconfigureerd.

![ beval ](../assets/fix.svg)<!-- Issue PAY-4202 --> een kwestie Vast die klanten verhindert kaartvaulting te gebruiken om een aankoop te voltooien of een in gebreke gebleven betalingsmethode voor een opslag te schrappen [ gebruikend de `Authorize and Capture` betalingsactie ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). Eerder werd een fout met betrekking tot de &quot;Provider Vault ID not found&quot; weergegeven toen de klant probeerde de gefactureerde creditcards te gebruiken of te wijzigen.

## v1.6.0

_17 Februari, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-3540 --> Toegevoegde [ 3DS nalevingseigenschap voor handelaren die in de Europese Unie (EU) en Groot-Brittannië overdragen ](security.md#3ds). Deze extra beveiligingslaag, die vereist dat kopers zich verifiëren bij hun creditcardmaatschappij, helpt internetfraude te voorkomen en is vereist in het kader van de EU-regelgeving inzake naleving.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-3609 --> voegde de capaciteit toe om [ kaartvaulting in Admin ](vaulting.md#use-vaulting-in-the-admin) toe te laten. Op deze manier kunnen handelaren via hun gefactureerde betalingsmethoden een bestelling voor klanten in de beheerder maken.

## v1.5.4

_Januari 29, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-4110 --> een kwestie die kopers verhinderde om een orde te plaatsen gebruikend betalingsknopen op de productpagina, de minikaart, en de kar. Kopers kunnen nu bestellingen voltooien.

## v1.5.3

_Januari 25, 2023_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-4102 --> gaf een moeilijke situatie aan een achteruit onverenigbare bekende kwestie vrij. Deze release vergrendelt de extensie van de service-id naar de nieuwste stabiele versie, die nieuwe [!DNL Payment Services] -installaties opnieuw inschakelt om Commerce Services te configureren.

## v1.5.2

_December 22, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3992 --> Verbeterde facturering in [!DNL Payment Services] wanneer een betalingsmethode wordt verworpen.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3999 -->[!DNL Payment Services] toont nu correct PayPal betaalknopen voor handelaren gebruikend [ het douanemalplaatje van de Afhandeling van de Vuur van de Vuur ](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} voor de controlepagina. Eerder werden de knoppen periodiek weergegeven door de minicart.

## v1.5.1

_23 November, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-3923 -->[!DNL Payment Services] omvat nu het versieaantal in de kopbal van de gebruikersagent zodat de verzoeken, ongebruikte eindpunten kunnen volgen, filtreren of verwerpen.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3968 -->[!DNL Payment Services] toont nu correct ordegegevens wanneer een orde van de productpagina gebruikend betalingsknopen wordt geplaatst.

## v1.5.0

_18 November, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-3880 --> een verkoopster kan nu [ kluis (sparen) hun creditcardinformatie tijdens controle ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) aan gebruik in een recentere aankoop voor het zelfde of een andere opslag binnen de zelfde handelaarrekening.

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-3950 --> Merchants kunnen de [ Onmiddellijke eigenschap van Commerce van de Aankoop ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) voor hun opslag nu toelaten zodat de winkels (gebruik [ in kluis informatie van de creditcard ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) kunnen (gebruiken) om controle te versnellen.

## v1.4.1

_14 oktober 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ bevestigen ](../assets/fix.svg)<!-- Issue PAY-3766 --> wanneer de betalingsmethode van een klant wordt verworpen, is het zichtbare foutenbericht beschrijvelijker. Het adviseert de klant om betalingsinformatie opnieuw in te voeren en opnieuw te proberen, een andere betalingsmethode te proberen, of hun bank over de geweigerde transactie te contacteren.

## v1.4.0

_30 September, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-784 -->[!DNL Payment Services] omvat nu de capaciteit aan opstelling een handelaarrekening aan [ gebruiks veelvoudige PayPal bedrijfsrekeningen ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). Hierdoor kan de handelaar in meerdere landen uw winkels bedienen met verschillende valuta&#39;s, of Adobe Commerce gebruiken voor een deel van uw bedrijf.

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-3231 --> Merchants kunnen [ a [!UICONTROL Soft Descriptor] ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) aan websites of individuele configuratie van de opslagmeningen toevoegen die op de verklaringen van de de bank van de klantentransactie tonen om merken, opslag, of productlijnen te afbakenen.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-3707 --> [ laat of maak creditcardgebieden en PayPal betaalknopen ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) voor controle in [!DNL Payment Services] montages toe onbruikbaar.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3546 --> wanneer een klant **[!UICONTROL Edit cart]** klikt, richt de pagina aan de wortelpagina opnieuw en toont de bijgewerkte punten in plaats van het tonen van een leeg karretje.

## v1.3.1

_6 September, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3663 --> nu, wanneer de opslag van een handelaar een orde vastlegt die met een niet globale munt wordt gemachtigd, voltooit het vangstproces en geen fout wordt getoond.

## v1.3.0

_9 augustus, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-XX --> Algemene beschikbaarheidsversie - [!DNL Payment Services] wordt nu gesteund door [  [!DNL Adobe Commerce]  en  [!DNL Magento Open Source]  versies 2.4.0 aan 2.4.5 ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-x --> Apple Pay is nu compatibel met browser Safari v15.5 op mobiel en Desktop.

## v1.2.0

_Juni 29, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Bekende kwestie ](../assets/bug.svg)<!-- Issue PAY-x --> het Betalen van Apple is onverenigbaar met browser Safari v15.5 op mobiel en Desktop. Als je Safari versie 15.5 gebruikt, kun je het afrekenen met Apple Pay niet voltooien.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3264 --> eerder, toen een het programma geopende gebruiker een het factureren/verschepen adres buiten het standaardadres voor hun rekening selecteerde, ontbrak het afrekenen. Het geselecteerde facturerings-/verzendadres wordt nu verzonden (in plaats van het standaard opgeslagen adres) en de afhandeling is voltooid.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3314 --> als u PayPal betalingsknopen voor controle onbruikbaar maakt, worden geen fouten getoond.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3330 --> Betalingen ontbreken niet meer tijdens controle wanneer een gastgebruiker een telefoonaantal ingaat dat streepjes omvat.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> wanneer de geloofsbrieven van de Diensten van Commerce ongeldig zijn, [!DNL Payment Services] alarm nu u door een geloofsbrieven van het [!DNL Payment Services] Huis in Admin te tonen.

![ Bekende kwestie ](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] is onverenigbaar met `commerce-data-export` v101.20 en hoger, die het onverenigbaar met de [[!DNL Channel manager]  uitbreiding ](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html) teruggeeft.

## v1.1.0

_Maart 31, 2022_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-2127 --> Algemene beschikbaarheidsversie - [!DNL Payment Services] wordt nu gesteund door [  [!DNL Adobe Commerce]  en  [!DNL Magento Open Source]  versies 2.4.0 aan 2.4.4 ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-2682 --> De [!DNL Payment Services] uitbreiding voor [!DNL Adobe Commerce] en [!DNL Magento Open Source] is nu beschikbaar voor Canadese handelaren. De handelaren kunnen betalingsconfiguratie in of [ Frans ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) of [ Engels ](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies) bekijken.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] steunt [ Canadese dollars (CAD) ](introduction.md#accepted-credit-cards-and-currencies) voor creditcards en transacties PayPal.

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-2680 --> Merchants kunnen [ aan boord  [!DNL Payment Services]](onboard.md) uitbreiding in Engelse of Franse talen.

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-2678 --> Merchants kunnen financiële rapporten nu bekijken, zowel de [ betalingsstatus van de Orde ](order-payment-status.md) als [ uitbetalingsrapporten ](payouts.md), in Canadese dollars (CAD).

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-2710 -->[!DNL Payment Services] is nu compatibel met [ PHP 8.1 ](https://www.php.net/releases/8.1/en.php).

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-3017 --> Verbeterde zandbakwijze alarm om juiste alarm met veelvoudige opslag te tonen.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-2742 --> U kunt beschikbare betalingsmethodes, zoals Venmo, op het niveau van de archiefmening nu toelaten en onbruikbaar maken. Eerder kon u alleen betalingsmethoden per website configureren.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-2277 --> U kunt nu selectief [ toelaten of individuele PayPal betalingsknopen onbruikbaar maken ](configure-admin.md#payment-buttons).

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue PAY-2561 --> Eerder verwijderde producten verschijnen niet in de kar op de _3} pagina van de Orde van het Overzicht {._

![ Bekende kwestie ](../assets/bug.svg)<!-- Issue PAY-2842 --> de creditcardtransacties van de Test [ kan met PayPal ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) ontbreken wanneer het verwerken van betalingen in een zandbakmilieu.

## v1.0.0

_November 29, 2021_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.0 en nieuwer

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-2127 --> Algemene beschikbaarheidsversie - [[!DNL Payment Services] ](https://commercemarketplace.adobe.com/magento-payment-services.html) wordt nu gesteund door [!DNL Adobe Commerce] en [!DNL Magento Open Source] versies 2.4.0 tot 2.4.3-p1.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-124 --> de [!DNL Payment Services] uitbreiding voor [!DNL Adobe Commerce] en [!DNL Magento Open Source] kan of voor [[!DNL Adobe Commerce]  op wolkeninfrastructuur ](install.md#adobe-commerce-on-cloud-infrastructure) of [ op-gebouw ](install.md#on-premises) instanties worden geïnstalleerd. Deze methoden vereisen het gebruik van een opdrachtregelinterface.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] steunt de rekening van de a [ zandbak ](sandbox.md) die verkopers toestaat om de uitbreiding op testwijze te beoordelen.

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-666 --> Merchants kunnen [ de uitbreiding van de Diensten van de Betaling ](configure-admin.md) met basisbetalingsgedrag, zoals het gebruiken van [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) omschakeling tussen zandbak of productiemilieu&#39;s vormen.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-780 --> Uw klanten kunnen uit controleren met [!DNL Payment Services] of via [ handordeverwezenlijking ](create-order.md).

![ Nieuwe ](../assets/new.svg)<!-- Issue PAY-1856 --> Uitgebreide rapportering, via [ de betalingsstatus van de Orde ](order-payment-status.md) en [ de rapporten van Uitbetalingen ](payouts.md), zijn beschikbaar voor [!DNL Payment Services] om u een duidelijke mening van de orden van uw opslag en verwante betalingen te geven.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] biedt ondersteuning voor flexibele, gedifferentieerde prijzen op basis van het totale verwerkingsvolume, aangepast aan elke handelaar.

![ Nieuw ](../assets/new.svg)<!-- Issue PAY-1443 --> U kunt gemakkelijk [ de blik en het gevoel ](payments-options.md) van PayPal betaalknopen en creditcardgebieden voor de [!DNL Payment Services] uitbreiding aanpassen.

![ Bekende kwestie ](../assets/bug.svg)<!-- Issue PAY-2473 --> Gebruikend [ onjuiste Composer sleutels ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) tijdens installatie van de uitbreiding verhindert de gebruiker [ ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) voor authentiek verklaren met het correcte `MAGEID`.

![ Bekende kwestie ](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] rapporten [ kunnen niet onmiddellijk ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html) synchroniseren.

![ Bekende kwestie ](../assets/bug.svg)<!-- Issue PAY-2475 --> Uw [ PayPal zandbakrekening ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) voor [!DNL Payment Services] kan niet worden geverifieerd als u dat rekening tijdens het in- en uitstappen creeert.
