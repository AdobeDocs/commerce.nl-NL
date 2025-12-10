---
title: Hoe  [!DNL Commerce]  de Behandelt van de Diensten de Verzoeken van de Privacy
description: Leer hoe  [!DNL Commerce]  de dienstenhandvatten verzoeken tot toegang en schrapping gegevens.
role: Admin, Leader
feature: Security, Compliance
exl-id: 1408ca77-6956-4519-93a6-bc9be9bffeff
source-git-commit: c6725fc524e9d239ccc0f16701e92ad5d2fc7729
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# Privacyverzoeken

Adobe Experience Platform Privacy Service biedt een RESTful-API en -gebruikersinterface waarmee u verzoeken om klantgegevens kunt beheren. Met Privacy Service kunt u verzoeken indienen om toegang te krijgen tot persoonlijke klantgegevens en deze te verwijderen uit Adobe Experience Cloud-toepassingen. Zo kunt u de automatische naleving van wettelijke en organisatorische privacyregels vereenvoudigen.

Raadpleeg de documentatie bij Adobe Experience Platform voor meer informatie over Privacy Service en hoe u uw privacyverzoeken kunt maken en beheren:

* [&#x200B; overzicht van Privacy Service &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/home)
* [&#x200B; het Leiden privacybanen in Privacy Service UI &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/ui/user-guide)

## Aanvragen voor persoonlijke gegevensprivacy beheren

U kunt afzonderlijke aanvragen voor toegang tot en verwijdering van consumentengegevens uit [!DNL Commerce] op twee manieren verzenden:

* Door **UI van Privacy Service**. Zie de documentatie [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/ui/user-guide#_blank).
* Door **Privacy Service API**. Zie hier de documentatie [&#x200B; &#x200B;](https://developer.adobe.com/experience-platform-apis/references/privacy-service/#_blank) en API informatie [&#x200B; &#x200B;](https://developer.adobe.com/experience-platform-apis/#_blank).

Privacy Service steunt twee soorten verzoeken: **gegevenstoegang** en **gegevensschrapping**.

>[!NOTE]
>
>Dit artikel richt zich op het indienen van privacyverzoeken voor [!DNL Commerce] . Als u van plan bent om privacyverzoeken voor [&#x200B; het gegevensmeer van het Platform &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/privacy) te maken, [&#x200B; Real-Time Profiel van de Klant &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/privacy), of [&#x200B; Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/privacy), verwijs naar hun respectieve gebruikersgidsen. Merk op dat schrappings en toegangsverzoeken aan elk systeem individueel moeten worden gedaan, aangezien een privacyverzoek aan Commerce geen gegevens uit al deze systemen verwijdert.

## Toegang tot gegevens

Voor **toegangsverzoeken**, specificeer &quot;Commerce (Personalization)&quot;van UI (of `commerceMarketingData` als productcode in API).

## Gegevensverwijdering

Voor verwijderingsaanvragen verwijdert Privacy Service [!DNL Commerce] -gegevens die zijn opgeslagen in Commerce SaaS-services voor marketingdoeleinden. Dit houdt in dat profielen en orders van betrokkenen niet langer worden verzonden naar Adobe-marketingtoepassingen voor gebruik in campagnes en klantreizen. Privacy Service verwijdert echter geen gegevens uit de [!DNL Commerce] -toepassing, omdat deze mogelijk vereist zijn voor zakelijke transactionele behoeften. Handelaars zijn verantwoordelijk voor alle aanvragen voor het verwijderen van gegevens/toegang in de [!DNL Commerce] -toepassing. Zie [&#x200B; Gedeelde verantwoordelijkheidsveiligheid en operationeel model &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility) om meer te leren.

[!DNL Commerce] stelt handelaren op de hoogte van verwijderingsverzoeken door hen informatie te sturen voor betrokkenen die verzoeken bepaalde gegevens te verwijderen.

## Hoe te om toegang tot te creëren en verzoeken te schrappen

### Vereisten

Om toegang te krijgen tot gegevens voor Adobe [!DNL Commerce] moet u beschikken over:

* een IMS-organisatie-id
* Een id van de identiteit van de persoon waarop u wilt optreden en de bijbehorende naamruimte(n). Voor meer informatie over identiteit namespaces in Adobe [!DNL Commerce] en Experience Platform, zie het [&#x200B; overzicht van identiteitskaart namespace &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces).

### Voorbeeld van toegang via GDPR-verzoek/verwijdering:

Voor **toegangsverzoeken**, specificeer &quot;Commerce (Personalization)&quot;van UI (of &quot;commerceMarketingData&quot;als productcode in API).

Voor **schrapt verzoeken**, zorg ervoor dat checkbox &quot;Commerce (Personalization)&quot;wordt toegelaten. Als er bovendien al gegevens van het klantprofiel en de bestelling zijn verzonden van [!DNL Commerce] naar Adobe Experience Platform, moet u verwijderingsaanvragen indienen bij de volgende downstreamservices.

* Profiel (productcode: &quot;profileService&quot;)
* AEP Data Lake (productcode: &quot;AdobeCloudPlatform&quot;)
* Identiteit (productcode: &quot;identiteit&quot;)

Als u aanvragen voor toegang en verwijdering wilt verzenden via de API voor privacy, moet u de machtigingen voor Privacy Service verifiëren en beheren:

* [&#x200B; verifieer en heb toegang tot Privacy Service API &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/api/getting-started)
* [&#x200B; beheert toestemmingen voor Privacy Service &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/privacy/permissions)

**Vereiste kopballen**

```bash
curl --location --request POST 'https://platform.adobe.io/data/core/privacy/jobs' \
--header 'Content-Type: application/json' \
--header 'x-api-key: {{CLIENT_ID}}' \
--header 'x-gw-ims-org-id: {{IMS_ORGID}}' \
--header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
```

**Verzoek**

```json
{
    "companyContexts": [
      {
        "namespace": "imsOrgID",
        "value": "{{IMS_ORGID}}"
      }
    ],
    "users": [
      {
        "key": "sampleUserKey1",
        "action": ["access"],
        "userIDs": [
          {
            "namespace": "email",
            "value": "dsmith@sample.com",
            "type": "standard"
          }
        ]
      },
      {
        "key": "sampleUserKey2",
        "action": ["access","delete"],
        "userIDs": [
          {
            "namespace": "email",
            "value": "ajones@sample.com",
            "type": "standard"
          }
        ]
      }
    ],
    "include": ["commerceMarketingData"],
    "expandIds": false,
    "priority": "normal",
    "regulation": "gdpr"
}
```

**Reactie**

```json
{
    "requestId": "17284033173196154RX-223",
    "totalRecords": 3,
    "jobs": [
        {
            "jobId": "a52ca032-858e-11ef-bbb4-27391388a0a6",
            "customer": {
                "user": {
                    "key": "sampleUserKey1",
                    "action": [
                        "access"
                    ],
                    "userIDs": [
                        {
                            "namespace": "email",
                            "value": "dsmith@sample.com",
                            "type": "standard",
                            "namespaceId": 6,
                            "isDeletedClientSide": false
                        }
                    ]
                }
            }
        },
        {
            "jobId": "a52ca034-858e-11ef-bbb4-d5d952d69769",
            "customer": {
                "user": {
                    "key": "sampleUserKey2",
                    "action": [
                        "delete"
                    ],
                    "userIDs": [
                        {
                            "namespace": "email",
                            "value": "ajones@sample.com",
                            "type": "standard",
                            "namespaceId": 6,
                            "isDeletedClientSide": false
                        }
                    ]
                }
            }
        },
        {
            "jobId": "a52ca033-858e-11ef-bbb4-8361a5022341",
            "customer": {
                "user": {
                    "key": "sampleUserKey2",
                    "action": [
                        "access"
                    ],
                    "userIDs": [
                        {
                            "namespace": "email",
                            "value": "ajones@sample.com",
                            "type": "standard",
                            "namespaceId": 6,
                            "isDeletedClientSide": false
                        }
                    ]
                }
            }
        }
    ]
}
```
