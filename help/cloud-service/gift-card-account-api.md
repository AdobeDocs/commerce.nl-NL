---
title: REST-eindpunten van Cadeaukaartaccount
description: Leer hoe te om het BEDRIJF APIs van de Rekening van de Kaart van de Cadeaukaart te gebruiken om, kwitantiekaarten programmatically in  [!DNL Adobe Commerce as a Cloud Service] tot stand te brengen bij te werken, te schrappen en te vragen.
role: Admin, Developer
level: Experienced
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 160180d9d779514f6faee3c7de46531ebf191c7d
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Cadeaukaartaccount-API

{{accs-sandbox-experimental}}

De weergave van REST-eindpunten van de cadeau-kaartaccount biedt programmatisch beheer van cadeau-kaartaccounts op accountniveau, niet op het niveau van de kaart of aanhalingstekens. Gebruik deze API om geschenkkaartrekeningen te creëren, terug te winnen, bij te werken en te schrappen, of aan de rekeningen van de leveringskaartenrekening in bulk door het JSON de invoereindpunt van de Invoer.

Deze eindpunten zijn ontworpen voor:

* Beheerders die cadeaukaartprogramma&#39;s beheren
* Inrichtingsgeschenkkaarten voor integratie van derden vanaf externe systemen, zoals ERP, CRM en marketingplatforms
* Geautomatiseerde workflows voor het maken van een cadeau-kaart

## Verificatie

Voor alle eindpunten is een beheerderstoken of een token voor de integratie vereist. Het token moet worden gekoppeld aan een rol die de `Magento_GiftCardAccount::giftcardaccount` Access Control List (ACL)-bron bevat.

Voor bulkimportverrichtingen, moet de rol ook het `Magento_ImportExport::import_api` ACL middel omvatten.

## Website- en winkelcontext

De waarden van de website en van de opslagmening worden opgelost van de HTTP- verzoekkopballen, niet van het verzoeklichaam. Geef een van de volgende kopteksten door met elk verzoek:

* `Store: <store_view_code>`
* `Magento-Website-Code: <website_code>`

De API lost de website automatisch van deze kopballen op. Neem `website_id` niet op in de payload van de REST-aanvraag.

>[!NOTE]
>
>Het bulkimporteindpunt is een uitzondering. Omdat import bulksgewijs werkt en mogelijk op specifieke websites gericht is, is voor elke rij in de importlading een expliciete `website_id` -waarde vereist.

## REST API-referentie

De API stelt de volgende bewerkingen onder `/V1/giftcardaccounts` beschikbaar, allemaal beveiligd door de `Magento_GiftCardAccount::giftcardaccount` ACL-bron:

| Methode | URL | Beschrijving |
|--------|-----|-------------|
| POST | `/rest/V1/giftcardaccounts` | Een kaartenaccount voor cadeaus maken |
| GET | `/rest/V1/giftcardaccounts` | Lijstaccounts (ondersteunt zoekcriteria) |
| GET | `/rest/V1/giftcardaccounts/:id` | Account ophalen op ID |
| GET | `/rest/V1/giftcardaccounts/code/:code` | Account ophalen op code |
| PUT | `/rest/V1/giftcardaccounts/:id` | Account bijwerken (semantiek samenvoegen) |
| DELETE | `/rest/V1/giftcardaccounts/:id` | Account verwijderen |

### Veldverwijzing

| Veld | Type | Geldige waarden | REST maken | Importeren |
|---|---|---|---|---|
| `code` | string | Max. 255 tekens | Vereist | Vereist |
| `balance` | zweven | >= 0 | Vereist | Vereist |
| `status` | int | `0` (uitgeschakeld), `1` (ingeschakeld) | Optioneel, standaard ingesteld op `1` | Optioneel, standaard ingesteld op `1` |
| `state` | int | `0` (beschikbaar), `1` (gebruikt), `2` (ingewisseld), `3` (verlopen) | Optioneel, standaard ingesteld op `0` | Optioneel, standaard ingesteld op `0` |
| `is_redeemable` | int | `0` of `1` | Optioneel, standaard ingesteld op `1` | Optioneel, standaard ingesteld op `1` |
| `date_expires` | string | `YYYY-MM-DD` of null | Optioneel | Optioneel |
| `date_created` | string | `YYYY-MM-DD` | Automatisch instellen | Optioneel, automatisch instellen indien weggelaten |
| `website_id` | int | Geldige website-id | Niet geaccepteerd (automatisch omgezet vanuit kopteksten) | Vereist |

### Een kaartenaccount voor cadeaus maken

Hiermee maakt u een nieuw cadeaukaartaccount met dubbele codedetectie.

| Item | Waarde |
|---|---|
| **Methode** | `POST` |
| **URL** | `/V1/giftcardaccounts` |

**het lichaam van het Verzoek:**

```json
{
  "giftcardAccount": {
    "code": "GIFT-1234-ABCD",
    "balance": 100.00,
    "status": 1,
    "state": 0,
    "is_redeemable": 1,
    "date_expires": "2027-12-31"
  }
}
```

**Reactie (200):**

```json
{
  "account_id": 42,
  "code": "GIFT-1234-ABCD",
  "balance": 100,
  "status": 1,
  "state": 0,
  "is_redeemable": 1,
  "date_expires": "2027-12-31",
  "date_created": "2026-03-12"
}
```

### Een kaartenaccount voor cadeautjes ophalen via ID

| Item | Waarde |
|---|---|
| **Methode** | `GET` |
| **URL** | `/V1/giftcardaccounts/:id` |

**Reactie (200):**

Retourneert één kaartobject voor een cadeau-kaart.

### Een kaartenaccount via code ophalen

| Item | Waarde |
|---|---|
| **Methode** | `GET` |
| **URL** | `/V1/giftcardaccounts/code/:code` |

>[!IMPORTANT]
>
>Als een code van een cadeaukaart puur numeriek is (bijvoorbeeld `12345` ), komt een aanvraag naar `/V1/giftcardaccounts/12345` overeen met de ID-route, niet met de coderoute. Gebruik `/V1/giftcardaccounts/code/12345` altijd voor op code gebaseerde zoekopdrachten wanneer de code numeriek kan zijn.

**Reactie (200):**

Retourneert één kaartobject voor een cadeau-kaart.

### Creditcardaccounts aanbieden met zoekcriteria

| Item | Waarde |
|---|---|
| **Methode** | `GET` |
| **URL** | `/V1/giftcardaccounts` |

Geef zoekcriteria door als queryparameters. In het volgende voorbeeld worden cadeau card-accounts geretourneerd waarbij `status` gelijk is aan `1` (ingeschakeld):

```text
GET /V1/giftcardaccounts?searchCriteria[filterGroups][0][filters][0][field]=status&searchCriteria[filterGroups][0][filters][0][value]=1&searchCriteria[pageSize]=10&searchCriteria[currentPage]=1
```

**Reactie (200):**

```json
{
  "items": [
    {
      "account_id": 42,
      "code": "GIFT-1234-ABCD",
      "balance": 100,
      "status": 1,
      "state": 0,
      "is_redeemable": 1,
      "date_expires": "2027-12-31",
      "date_created": "2026-03-12"
    }
  ],
  "search_criteria": { ... },
  "total_count": 1
}
```

### Een cadeaukaartaccount bijwerken

Hiermee werkt u een bestaand cadeaukaartaccount bij met behulp van samenvoegsemantiek. Alleen velden die niet &#39;null&#39; zijn in de aanvraag worden toegepast. Het veld `code` is onveranderlijk. Als u een andere code doorgeeft, wordt een validatiefout geretourneerd.

| Item | Waarde |
|---|---|
| **Methode** | `PUT` |
| **URL** | `/V1/giftcardaccounts/:id` |

**het lichaam van het Verzoek:**

```json
{
  "giftcardAccount": {
    "balance": 75.00,
    "status": 1
  }
}
```

**Reactie (200):**

Retourneert het bijgewerkte kaartobject van de cadeau-kaart.

### Een kaartenaccount voor cadeaus verwijderen

| Item | Waarde |
|---|---|
| **Methode** | `DELETE` |
| **URL** | `/V1/giftcardaccounts/:id` |

**Reactie (200):**

```json
true
```

## Bulkimport via JSON

Cadeaukaartaccounts kunnen bulksgewijs worden ingericht met `POST /V1/import/json` met het type entiteit `giftcardaccount` . Dit eindpunt vereist het `Magento_ImportJsonApi::import_api` middel van de Lijst van het Toegangsbeheer (ACL) naast het de rekening ACL van de giftekaartrekening.

### Ondersteund gedrag

| Gedrag | Beschrijving |
|---|---|
| `append` | Hiermee maakt u nieuwe cadeaukaartaccounts. Als er al een code bestaat, mislukt die rij en gaat het importeren verder met de resterende rijen. |
| `replace` | Hiermee werkt u de creditcardaccounts bij en voegt u deze per code in. Hiermee wordt de account gemaakt als de code niet bestaat en wordt deze zo nodig vervangen. |
| `delete` | Hiermee verwijdert u cadeaukaartaccounts op code. |

### Voorbeeld aanvragen

```json
{
  "source": {
    "entity": "giftcardaccount",
    "behavior": "append",
    "validation_strategy": "validation-stop-on-errors",
    "allowed_error_count": "10",
    "items": [
      {
        "code": "BULK-001",
        "balance": 50.00,
        "website_id": 1,
        "status": 1,
        "state": 0,
        "is_redeemable": 1,
        "date_expires": "2027-06-30"
      },
      {
        "code": "BULK-002",
        "balance": 25.00,
        "website_id": 1
      }
    ]
  }
}
```

### Gedetailleerde gegevens importeren

* Voor elke rij in de importlading is een expliciete `website_id` vereist, in tegenstelling tot REST-eindpunten die de website afleiden van aanvraagheaders.
* Elke rij wordt onafhankelijk gevalideerd. Ongeldige rijen veroorzaken per-rijfouten zonder geldige rijen in de zelfde partij te beïnvloeden.
* Dubbele codes in dezelfde batch worden gedetecteerd en gerapporteerd als fouten per rij in plaats van dat er een transactie terugdraait.
* Importeren schrijft rechtstreeks naar de database voor prestaties en omzeilt de opslagcyclus van het leveranciersmodel. Items in de anamnese voor het wijzigen van de balans worden niet gemaakt tijdens het importeren.
* Met REST kunt u bewerkingen maken die de afgelopen vervaldatums negeren. De invoer keurt vroegere vervaldata door ontwerp goed, om historische gegevensmigratie te steunen.

## Foutafhandeling

De API retourneert standaard HTTP-statuscodes:

| Statuscode | Voorwaarde |
|---|---|
| `400` | Validatiefout. Ontbrekende vereiste velden, ongeldige waarden of vervaldatum in REST. |
| `401` | Token voor toonder ontbreekt of is ongeldig. |
| `403` | Het token heeft niet de vereiste ACL-resource. |
| `404` | Creditcardaccount niet gevonden. |
| `409` | Dubbele code voor cadeaukaart. |

Invoervalidatie geldt voor vereiste velden, waardebereiken (status moet `0` of `1` zijn, status moet `0` - `3` zijn, balans moet niet-negatief zijn), datumnotatie en typeveiligheid. Niet-numerieke waarden voor numerieke velden worden geweigerd.
