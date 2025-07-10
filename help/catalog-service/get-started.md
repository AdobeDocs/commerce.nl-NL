---
title: Aan de slag met  [!DNL Catalog Service]
description: Leer hoe te om tot  [!DNL Catalog Service]  toegang te hebben en met frontend toepassingen en derdediensten te integreren.
role: Admin, Developer
source-git-commit: 3a6a81fa03f13c24ac08041c39452c553aa54f55
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Aan de slag met de [!DNL Catalog Service]

Nadat [!DNL Catalog Service] is ingeschakeld, kunt u de service openen en gebruiken om catalogusgegevens, zoals product- en categoriegegevens, op te halen uit uw Adobe Commerce-instantie. De service is beschikbaar als een GraphQL API die u kunt openen via de Commerce Admin of vanuit elke frontend-toepassing die GraphQL-query&#39;s ondersteunt.

## Toegang tot de service

[!DNL Catalog Service] is beschikbaar als een GraphQL API die u kunt benaderen vanuit de Commerce Admin of vanuit elke frontend-toepassing die GraphQL-query&#39;s ondersteunt. De service is beschikbaar in zowel SaaS- als PaaS-omgevingen.


[!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."}

| Omgeving | Endpoint |
|------------ | ----------: |
| **het Testen** | `https://catalog-service-sandbox.adobe.io/graphql` |
| **Productie** | `https://catalog-service.adobe.io/graphql` |

[!BADGE &#x200B; slechts SaaS &#x200B;]{type=Positive url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."}

| Omgeving | Endpoint |
| ------------ | --------:|
| Testen | `https://na1-sandbox.api.commerce.adobe.com/{{tenant-id}}/graphql` |
| Productie (nog niet beschikbaar) | `https://na1.api.commerce.adobe.com/{{tenant-id}}/graphql` |

**structuur URL voor eindpunten SaaS**

```text
https://<region>-<environment>.api.commerce.adobe.com/<tenantId>/graphql
```

- `<region>` is het wolkengebied waar uw instantie wordt opgesteld.
- `<environment>` is het omgevingstype, zoals `sandbox` . Als het milieu productie is, wordt deze waarde weggelaten.
- `<tenantId>` is de unieke id voor de specifieke instantie van uw organisatie in de Adobe Experience Cloud.

Voor details over het gebruiken van de Dienst GraphQL API van de Catalogus, zie de [ Dienst van de Catalogus voor de Gids van Adobe Commerce ](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/) in de *documentatie van de Ontwikkelaar van Adobe Commerce*.


## Integreren met een headless winkel of services van derden

Om met een koploze winkel te integreren, moet u de storefront configuratie bijwerken om communicatie tussen de storefront en [!DNL Catalog Service] toe te laten om product en categoriegegevens terug te winnen.

Als u Adobe Commerce storefront op Edge Delivery Services gebruikt, voegt u het eindpunt van de Dienst van de Catalogus aan de storefrontconfiguratie toe. Voor details, zie de [ documentatie van Edge Delivery Services ](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/commerce-configuration/?lang=nl-NL#storefront-configuration).

Voor andere integratie, zie de documentatie van de projectopstelling voor details over hoe te om integratie tussen de dienst en achterste gegevensbronnen te vormen.


### Configuratie van firewall

Als u [!DNL Catalog Service] wilt toestaan via een firewall, voegt u `commerce.adobe.io` toe aan de lijst van gewenste personen.

## Catalogusservice en API-net

Het [ API Net voor Adobe Developer App Builder ](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) laat ontwikkelaars toe om privé of derde APIs en andere interfaces met de producten van Adobe te integreren gebruikend Adobe IO.

Zie het [[!DNL Catalog Service]  en API Net ](mesh.md) onderwerp voor installatie en configuratiedetails.

## Het dashboard voor gegevensbeheer gebruiken

Gebruik het [ dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/data-dashboard) om gegevenssynchronisatie tussen [!DNL Catalog Service] en uw instantie van Adobe Commerce te controleren. Het dashboard biedt inzicht in het gegevensoverdrachtsproces, waaronder de status van gegevensexport en een lijst van gesynchroniseerde producten.
