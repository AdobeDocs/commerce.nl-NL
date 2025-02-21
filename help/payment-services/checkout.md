---
title: Uitchecken in  [!DNL Payment Services]
description: Pas  [!DNL Payment Services]  controle aan om de behoeften van uw klant te passen.
feature: Payments, Checkout
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Uitchecken in [!DNL Payment Services]

U kunt de afhandeling voor Adobe Commerce [!DNL Payment Services] zo configureren dat deze het beste aansluit bij uw klanten. De functionaliteit zoals [ orde auto-ongeldig maakt ](#order-auto-voided-if-error) en [ creditcardhet vaulteren ](#credit-card-vaulting) zorgt ervoor uw klanten een vlotte gebruikerservaring hebben.

## Volgorde automatisch ongeldig maken als er een fout optreedt

Als tijdens het uitchecken een fout optreedt, wordt de volgorde door [!DNL Payment Services] automatisch gewist of geannuleerd.

Er wordt een foutbericht weergegeven op de uitcheckpagina voor de winkelier. Het bericht kan variëren.

![ Fout terwijl het controleren ](assets/user-checkout-error.png " Fout terwijl het controleren "){width="600" zoomable="yes"}

Een commentaar betreffende de geannuleerde orde toont ook in Admin voor een specifieke [ orde ](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/orders.html?lang=en).

![ Geannuleerde ordecommentaar in Admin voor orde ](assets/admin-checkout-error.png " Geannuleerde ordecommentaar in Admin voor orde "){width="600" zoomable="yes"}

Als een winkelier autorisatie voor een bestelling krijgt, maar de bestelling niet is gemaakt en omgezet in een `Capture` , wordt de bestelling automatisch ongeldig gemaakt. Dit proces zorgt ervoor dat er geen krediet op de creditcard van de winkels wordt gereserveerd en vermijdt de provisie voor de betalingsaanbieder die ontstaat wanneer de machtiging aan het einde van de standaardperiode van 29 dagen wordt ingetrokken.

>[!NOTE]
>
>Volgorde automatisch intrekken vindt alleen plaats wanneer de klant een betalingsmethode gebruikt die is ingesteld op `Authorize` mode, niet op `Authorize and Capture` mode.

## Afhandeling vanaf productpagina

Wanneer een klant rechtstreeks vanaf de productpagina uitcheckt met de PayPal- of [!DNL Pay Later] -knoppen, wordt alleen het object op de huidige productpagina aangeschaft. Objecten die al in de winkelwagentje van de klant staan, worden niet aan de afrekenstroom toegevoegd en niet aangeschaft.

Met deze functie kan de klant snel het object kopen dat hij of zij momenteel bekijkt, terwijl de eerder aan zijn of haar winkelwagentje toegevoegde items behouden blijven.
Als de klant de bestelling annuleert, wordt het item op de huidige productpagina toegevoegd aan de winkelwagentje van de klant.

Wanneer een klant de afrekenstroom op de productpagina invoert, wordt de afhandelingspagina vereenvoudigd. In de weergave worden alleen gegevens en opties weergegeven die betrekking hebben op de volgorde.

## Creditcard vaulting

Klanten kunnen hun creditcardgegevens voor toekomstige aankopen op websiteniveau (elke winkel binnen dezelfde zakelijke account) invullen (of &quot;opslaan&quot;).

Zie [ Kredietkaart het vauleren ](vaulting.md) voor meer informatie
