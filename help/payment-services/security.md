---
title: Beveiliging en naleving
description: Beoordeel de beveiligings- en compatibiliteitsvereisten voor uw site.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
feature: Payments, Checkout, Compliance
redirect_from: https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security.html
source-git-commit: 9f7690ae325853b9b4a590b3d1cd538909a26462
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Beveiliging en naleving

Beveiliging is van het grootste belang in [!DNL Payment Services] en er worden geen door de private of betaalkaartindustrie (PCI) gereguleerde gegevens doorgegeven aan uw [!DNL Payment Services] .

## Commerce-beveiliging

[!DNL Adobe Commerce] en [!DNL Magento Open Source] bieden ondersteuning voor verschillende beveiligingsfuncties.

Zie [ Veiligheid ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security){target="_blank"} in de gids van de kerngebruiker om veiligheid beste praktijken te herzien, en te leren hoe te om zittingen Admin en geloofsbrieven te beheren, CAPTCHA uit te voeren, en websitebeperkingen te beheren.

## PCI-compatibiliteit

De betaalkaartindustrie (PCI) heeft een reeks vereisten vastgesteld voor bedrijven die betalingen via een creditcard via internet accepteren. Naast het handhaven van een veilige omgeving, zijn de handelaren die de informatie van de klantencreditcard behandelen verantwoordelijk voor het voldoen aan sommige standaardrichtlijnen.

Zie {de Richtlijnen van de Naleving van 0} PCI ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/payments/compliance-pci){target="_blank"} voor meer informatie.[

De handelaren kunnen a [ zelfbeoordelingsvragenlijst (SAQ) voltooien ](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}, die een zelfbevestigingshulpmiddel is om veiligheid voor kaarthoudergegevens te beoordelen.

### Creditcardvelden

Met de Gebieden van de Kaart, worden geen PCI-Gereglementeerde gegevens overgegaan over uw diensten. U hoeft die gegevens niet op te slaan of te onderhouden, wat de bezorgdheid over PCI-compatibiliteit aanzienlijk vermindert.

### 3DS

PCI 3-D Secure (3DS) maakt kopersverificatie mogelijk met hun creditcardmaatschappij wanneer ze online aankopen doen op creditcards. Deze extra veiligheidslaag helpt fraude op het internet te voorkomen en is vereist in het kader van de EU-regelgeving inzake naleving.

[!UICONTROL Payment Services] biedt 3DS-functionaliteit om handelaren in staat te stellen te voldoen aan de EU-regelgeving en om klanten en handelaren te beschermen tegen frauduleuze activiteiten in hun winkels.

Als u een handelaar binnen de EU of Groot-Brittannië bent waar de 3DS naleving wordt vereist, moet u 3DS (het is `Off` door gebrek) manueel aanzetten in [ Montages ](settings.md#credit-card-fields).

>[!IMPORTANT]
>
>Het 3DS vereiste is op transacties van toepassing waar de zaken en de bank van kaarthouders in [ Europese Economische Ruimte ](https://www.efta.int/eea) (EEA) en Groot-Brittannië gevestigd zijn. Handelaren in de Verenigde Staten hebben geen 3DS nodig, maar kunnen deze desgewenst inschakelen voor hun transacties.

Orders die door het bedrijfs-/winkelpersoneel voor de koper worden geplaatst, zijn niet geconfigureerd met 3DS-compatibiliteitsmaatregelen.

>[!MORELIKETHIS]
>
> * Zie [ 3DS in montages ](settings.md#3ds) voor meer informatie.
> * Zie [ testkaarten ](https://developer.paypal.com/docs/checkout/advanced/customize/3d-secure/test/) in de ontwikkelaarsdocumentatie van PayPal voor meer informatie over specifieke creditcards voor het testen 3DS.

### Kaart vauleren

Wanneer een verkoopster [ vaults-of &quot;bewaart&quot;hun creditcardinformatie ](vaulting.md) voor toekomstige aankopen in uw opslag, wordt de minimale creditcardinformatie gedeeld met de verkoopster (laatste vier cijfers, kaartvervaldatum, en merk van kaart). Creditcardgegevens worden opgeslagen bij de betalingsdienstaanbieder. Wanneer een kaart verloopt of wanneer de gegevens niet meer hoeven te worden opgeslagen, kunnen zij die token verwijderen, zodat de informatie niet langer door de betalingsdienstaanbieder wordt opgeslagen.

Zie [ Kredietkaart die ](vaulting.md) voor meer informatie in kluizen.

### PayPal-betalingsknoppen

Met PayPal-betalingsknoppen worden er geen gegevens doorgegeven die door een PCI zijn gereguleerd. U hoeft die gegevens niet op te slaan of te onderhouden, wat de bezorgdheid over PCI-compatibiliteit aanzienlijk vermindert.

Om veiligheidsredenen geeft PayPal het factuuradres niet door tijdens het afrekenen. Land, e-mail en naam zijn de enige factuurgegevens die worden gebruikt. U kunt desgewenst het PayPal-afhandeling van uw site inschakelen om het volledige factureringsadres te retourneren door contact op te nemen met PayPal en een controleproces te voltooien.

PayPal heeft ook geïntegreerde fraudebescherming die computerleren gebruikt om fraude te bestrijden. Zie de documentatie van de Bescherming van de Verkoper van PayPal [ ](https://www.paypal.com/us/webapps/mpp/security/seller-protection) voor meer informatie.

## Fraudebescherming

U kunt geautomatiseerde fraudebescherming voor de Diensten van de Betaling met de [ Ondertekenende uitbreiding ](https://commercemarketplace.adobe.com/signifyd-module-connect.html) toelaten. Zie [ Ondertekenende fraudebescherming ](fraud-protection.md) voor meer informatie.

PayPal verstrekt andere opties voor [ fraudebescherming ](https://www.paypal.com/us/cshelp/article/what-is-fraud-protection-help1014){target=_blank} in hun ontwikkelaarsdocumentatie:

* Zie [ gevorderde fraudebescherming ](https://www.paypal.com/us/enterprise/fraud-protection-advanced#fraud-protection-advanced){target=_blank} voor meer informatie.
* Zie [ de bescherming van de Doorbelasting ](https://www.paypal.com/us/cshelp/article/what-is-chargeback-protection-help608){target=_blank} voor meer informatie.
