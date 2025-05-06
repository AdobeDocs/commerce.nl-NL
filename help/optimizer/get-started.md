---
title: Aan de slag met  [!DNL Adobe Commerce Optimizer]
description: Leer hoe te beginnen met  [!DNL Adobe Commerce Optimizer].
hide: true
recommendations: noCatalog
exl-id: de57d93d-e156-45c1-86aa-de29a8c34bd2
source-git-commit: ac79c8aa43ced017743fbef1f181b4eaf8e0a754
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Aan de slag

>[!NOTE]
>
>Deze documentatie beschrijft een product in vroege-toegangsontwikkeling en weerspiegelt niet alle functionaliteit voorgenomen voor algemene beschikbaarheid.

Deze handleiding begeleidt u bij het maken van en werken met een [!DNL Adobe Commerce Optimizer] -instantie.

<!--Click the tabs below to see high-level workflow overviews for the following user types:

- Administrators
- Merchants
- Developers

>[!BEGINTABS]

>[!TAB Administrator and merchant workflow]

This diagram provides a high-level overview of how administrators and merchants access and manage [!DNL Adobe Commerce Optimizer] instances. See the [Adobe Admin Console Guide](https://helpx.adobe.com/enterprise/admin-guide.html) for more information about administrator workflows.

NEED DIAGRAM

>[!TAB Developer workflow]

This diagram provides a high-level overview of how developers create integrations for [!DNL Adobe Commerce Optimizer] using App Builder. See the [API documentation](https://developer.adobe.com/commerce/services/cloud/) for more information.

NEED DIAGRAM

>[!ENDTABS]
-->

## Inrichting

Nadat de [!DNL Adobe Commerce Optimizer] -instanties gereed zijn, geeft het [!DNL Adobe Commerce Optimizer] -inrichtingsteam u de volgende eindpunten:

| Item | Voorbeeld-URL | Doel |
|---|---|---|
| [!DNL Adobe Commerce Optimizer] UI | `https://experience.adobe.com/#/@commerceprojectbeacon/commerce-optimizer-studio?tenant=<tenantId>` | Toegang Commerce Optimizer UI voor het beheren van uw catalogus over:<br> 1. Handelsregels (productontdekking, productaanbevelingen).<br> 2. Catalogusbeheer (kanaal en beleid maken).<br> 3. Gegevens-inzichten (de status van de inname van catalogusgegevens weergeven). |
| Storefront-API&#39;s | `https://na1-sandbox.api.commerce.adobe.com/<tenantId>/graphql` | Open de API&#39;s die nodig zijn voor het instellen van uw Commerce-winkel, aangedreven door Edge Delivery Services. |
| API&#39;s voor gegevensinvoer uit catalogi | `https://na1-sandbox.api.commerce.adobe.com/<tenantId>/v1/catalog/<entity>` | Open de API&#39;s die nodig zijn om uw catalogusgegevens in te voeren. |

>[!NOTE]
>
>Zie de [ ontwikkelaardocumentatie ](https://developer-stage.adobe.com/commerce/services/composable-catalog/) om meer over APIs nodig voor de opstelling van de storefront en catalogusopname te leren.

Als vroege toegangsdeelnemer, zult u een e-mail met een veilige verbinding ontvangen die, samen met uw token IMS, u aan [!DNL Adobe Commerce Optimizer] laat registreren of API vraag maken.

## De storefront instellen

Nu u een [!DNL Adobe Commerce Optimizer] instantie hebt, bent u bereid om [ vestiging ](./storefront.md) te werk te gaan uw Opslag van Commerce die door Edge Delivery Services wordt aangedreven.

## Beschikbare catalogusgegevens voor deelnemers die vroegtijdig toegang hebben

Als vroege toegangsdeelnemer, bevat de [!DNL Adobe Commerce Optimizer] instantie modelcatalogusgegevens die op het [ het gebruiksgeval van het Carvelo ](./use-case/admin-use-case.md) worden gebaseerd. De modelgegevens, samen met enkele vooraf geconfigureerde kanalen en beleidsregels, helpen u vertrouwd te raken met de gebruikersinterface van [!DNL Adobe Commerce Optimizer] .

<!--Ingest catalog data

By default, [!DNL Adobe Commerce Optimizer] instances do not include any product data.

See the [Ingestion API](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/using-the-api/) documentation to learn how you can import your catalog data into [!DNL Adobe Commerce Optimizer].

The catalog data that you ingest is visible in the [data insights](./insights-overview.md) page. Additionally, you can use the [Catalog](./catalog-overview.md) page to define the channels and policies.-->
