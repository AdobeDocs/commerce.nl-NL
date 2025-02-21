---
title: Beschikbare gegevens
description: Gebruik gegevens over financiële verslaggeving om rapportage te combineren met niet-Commerce-systemen.
role: User
level: Intermediate
feature: Payments, Checkout, Data Import/Export
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Beschikbare gegevens

U beschikt over bepaalde bestellingen en uitbetalingsgegevens, zodat u de financiële rapportage van Adobe Commerce op externe systemen kunt coördineren.

## Wisselen met ERP-systeem

U kunt de financiële rapportage van Adobe Commerce afstemmen op uw ERP-systeem (Enterprise Resource Planning) van een andere leverancier dan Adobe met de verhogende id die aan een specifieke bestelling is gekoppeld.

Wanneer de Diensten van de Betaling de orde van Commerce naar PayPal verzendt, is verhogingsidentiteitskaart inbegrepen als `custom_id` _en_ in `invoice_id` (die ook een willekeurig koord na `increment_id` bevat).

De id&#39;s zijn gemakkelijk toegankelijk in zowel de zakelijke activiteitengegevens voor een betaling als in de PayPal-website.

De `invoice_id` en `custom_id` worden onder aan de details van de zakelijke activiteit weergegeven voor een uitbetaling:

![`custom_id` in details met betrekking tot handelsactiviteit ](assets/merchant-activity-ids.png){width="600" zoomable="yes"}

`custom_id` en `invoice_id` in de details in de website van PayPal:

```json
   ...
   {
    "id": "4E855005GK253170H",
    "intent": "AUTHORIZE",
    "status": "COMPLETED",
    "payment_source": {
        ...
    },
    "purchase_units": [
        {
            ...
            "custom_id": "000001322",
            "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
            ...
            "payments": {
                "authorizations": [
                    {
                       ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ],
                "captures": [
                    {
                        ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ]
            }
        }
    ],
    "payer": {
        ...
    },
    "create_time": "2022-09-12T14:59:01Z",
    "update_time": "2022-09-12T14:59:45Z",
    "links": [
        ...
    ]
}
   ...
```

Zie de REST APIs-documentatie van PayPal voor meer informatie:

* [`purchase_unit` , waarin `custom_id` en `invoice_id` zich bevinden ](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit)
* [ toon orderdetails ](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
