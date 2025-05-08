---
title: Restituties
description: Creeer restituties voor  [!DNL Payment Services]  orden in Admin als deel van het proces van het creditnota.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout, Paas, Saas
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Restituties

Restituties voor [!DNL Payment Services] -orders worden in de beheerfunctie gemaakt als onderdeel van het creditcardproces. Een creditnota is een document dat het bedrag toont dat aan de klant, voor een volledige of gedeeltelijke terugbetaling verschuldigd is, die op een aankoop kan worden toegepast of direct aan de klant kan worden teruggegeven. De memo&#39;s van het krediet kunnen slechts voor orden worden uitgegeven die [&#128279;](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/invoices#create-an-invoice){target="_blank"} worden gefactureerd.

Zie [ Memo&#39;s van het Krediet ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos){target="_blank"} in onze gids van de kerngebruiker voor meer informatie en te leren om creditmemo&#39;s uit te geven en te drukken.

Voor bestellingen die met PayPal of een creditcard worden verwerkt, kunt u:

* Het volledige bedrag van de bestelling terugbetalen
* Een gedeeltelijk bedrag van een bestelling terugbetalen (of meerdere gedeeltelijke bedragen)
* Een bedrag terugbetalen dat lager is dan de waarde van een specifiek orderitem

Zie [ Uitgevend een Memo van het Krediet ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memo-create){target="_blank"} in onze gids van de kerngebruiker voor meer informatie.

>[!NOTE]
>
>Er treedt een fout op bij bestellingen die met PayPal of een creditcard zijn verwerkt als u probeert een bestelling gedeeltelijk te retourneren voor meer dan het resterende bedrag van de bestelling (oorspronkelijk bedrag minus het totaal van de bestaande terugbetalingen), of als u een terugbetaling geeft voor een bedrag dat groter is dan het volledige bedrag van de bestelling.

[!UICONTROL Payment Action] het plaatsen in uw [!UICONTROL Payment Settings] configuratie-of `Authorize` of `Authorize and Capture` - bepaalt het [ basisterugbetalingswerkschema ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memos#refund-workflow){target="_blank"} voor orden.

Zie de [ actie die sectie ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/credit-memos/credit-memo-create#payment-action-setting){target="_blank"} plaatsen van de Betaling van _een Memo van het Krediet_ voor meer informatie uitgeven.
