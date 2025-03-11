---
title: '[!DNL Live Search] Gebeurtenissen'
description: Leer hoe de gebeurtenissen gegevens voor  [!DNL Live Search] verzamelen.
feature: Services, Eventing
exl-id: a9f4f254-d8ff-46f1-8deb-a75b90d70d52
source-git-commit: 94d2a9911ab10d164d75779d1f310e5bdf2aea74
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# [!DNL Live Search] Gebeurtenissen

In [!DNL Live Search] worden gebeurtenissen gebruikt om zoekalgoritmen zoals &quot;Meest bekeken&quot; en &quot;Dit bekeken, heeft dat bekeken&quot;, van stroom te voorzien. Terwijl het [ het thema van de steekproefLuminantie van Commerce ](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/design/themes/themes#the-default-theme) uit de doos uitkomt, moeten de hoofd en andere douaneimplementaties het voorkomen voor hun eigen behoeften uitvoeren.

Deze lijst beschrijft de gebeurtenissen die door [!DNL Live Search] [ worden gebruikt rangschikkend strategieën ](rules-add.md#intelligent-ranking).

| Rangschikkingsstrategie | Gebeurtenissen | Pagina |
| --- | --- | --- |
| Meest bekeken | `page-view`<br>`product-view` | Productdetailpagina |
| Meest aangekocht | `page-view`<br>`place-order` | Winkelwagentje/Afhandeling |
| Meest toegevoegd aan winkelwagentje | `page-view`<br>`add-to-cart` | De detailpagina van het product <br> product die pagina <br> van de Lijst van de Kar <br> van de Wenslijst van het Product |
| Bekeken dit, gezien dat | `page-view`<br>`product-view` | Productdetailpagina |

>[!NOTE]
>
>Gegevensverzameling ten behoeve van [!DNL Live Search] omvat geen PII (Persoonlijk identificeerbare informatie). Alle gebruikers-id&#39;s, zoals cookie-id&#39;s en IP-adressen, worden strikt geanonimiseerd. [ leer meer ](https://www.adobe.com/privacy/experience-cloud.html).

## Vereiste dashboardgebeurtenissen

Sommige gebeurtenissen worden vereist om het [ Levende dashboard van het Onderzoek ](performance.md) te bevolken

| Dashboardgebied | Gebeurtenissen | Veld samenvoegen |
| ------------------- | ------------- | ---------- |
| Unieke zoekopdrachten | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Zoekopdrachten met nulresultaten | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Resultaatsnelheid nul | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Populaire zoekopdrachten | `page-view`, `search-request-sent`, `search-response-received` | `searchRequestId` |
| Gem. klikpositie | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | `searchRequestId` |
| Doorklikfrequentie | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | `searchRequestId`, `sku`, `parentSku` |
| Omrekeningskoers | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | `searchRequestId`, `sku`, `parentSku` |

### Vereiste contexten

Voor alle gebeurtenissen is de context `Page` en `Storefront` vereist. Dit moet gebeuren op paginaniveau/storefront toepassingslaag eerder dan wanneer het produceren van individuele gebeurtenissen (bijvoorbeeld, in een PHP opslag, is de PHP toepassingscontainer verantwoordelijk voor het plaatsen van hen bij runtime).

## Gebruik

Hier volgt een voorbeeldimplementatie van de gebeurtenis `search-request-sent` :

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## Caveats

- Ad blokkers en privacymontages kunnen gebeurtenissen verhinderen worden gevangen en zouden de overeenkomst en opbrengst [ metriek ](performance.md) kunnen veroorzaken om worden onderdrukt. Bovendien kunnen bepaalde gebeurtenissen niet worden verzonden omdat de gebruiker de pagina of het netwerk heeft verlaten.
- Bij een ononderbroken implementatie moet de gebeurtenis worden geïmplementeerd om intelligente handel mogelijk te maken.

>[!NOTE]
>
>Als [ de Wijze van de Beperking van het Koekje ](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) wordt toegelaten, verzamelt Adobe Commerce geen gedragsgegevens tot de verkoopster toestemming geeft om koekjes te gebruiken. Als de modus Cookie-beperking is uitgeschakeld, verzamelt Adobe Commerce standaard gedragsgegevens.
