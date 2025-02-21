---
title: Testen in testomgeving
description: Leer hoe te om  [!DNL Product Recommendations]  van uw productiemilieu in uw het opvoeren milieu voor testende doeleinden te gebruiken.
feature: Services, Recommendations, Staging
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Testen in testomgeving

Alvorens u aanbevelingen aan uw productiemilieu opstelt, test de dienst in een niet productiemilieu om ervoor te zorgen dat alles zoals verwacht werkt.

[!DNL Product Recommendations] terugkeerproducten die op [ worden gebaseerd verkoopsgedrag gegevens ](events.md) van uw storefront worden verzameld. In een niet-productieomgeving is het echter waarschijnlijk dat u geen gedragsgegevens van kopers hebt. Het enige type aanbevelingen dat u zonder gedragsgegevens kunt testen, is `More like this` . Voor dit soort aanbevelingen zijn geen invoergegevens vereist, omdat er een gelijksoortige directe inhoud wordt gebruikt.

De volgende aanbevelingen vereisen gedragsgegevens:

- Meest bekeken
- Bekeken dit, gezien dat
- Dit gekocht

Hoe kunt u uw aanbevelingen testen in een niet-productieomgeving met behulp van gedragsgegevens? Er zijn een paar opties.

## Aanbevelingen inzake het ophalen uit de productieomgeving (aanbevolen)

Adobe Commerce staat u toe om aanbevelingen van uw productiemilieu en voorproef hen in uw niet-productiemilieu door [ omschakeling ](settings.md) te halen SaaS gegevensruimte.

Om aanbevelingen van uw productiemilieu te halen, moet u ervoor zorgen dat:

- De gegevensinzameling van de opslag wordt [ gevormd en toegelaten ](install-configure.md) in het productiemilieu.
- De catalogus in uw niet-productieomgeving is grotendeels dezelfde als in de productieomgeving. Het gebruik van vergelijkbare catalogi zorgt ervoor dat de producten die in de aanbevolen eenheden worden geretourneerd, de producten in de productieomgeving op dezelfde manier na benaderen.

## Gedragsgegevens genereren over een andere omgeving dan de productieomgeving

1. Implementeer de module `magento/product-recommendations` in een niet-productieomgeving waarin de catalogusgegevens overeenkomen met de productiecatalogus.

1. Gebruik één van niet-productie van de Ruimte IDs van Gegevens voor [ configuratie ](../landing/saas.md#saas-configuration) in Admin.

1. Genereer de gegevens zelf door rond de winkelpagina te klikken om het gedrag van echte kopers na te bootsen (of een automatiseringsscript te maken). Door het testen genereert u gedragsgebeurtenissen in uw niet-productieomgeving. Deze gebeurtenissen worden gebruikt om de productaffiniteiten te produceren die aanbevelingen van de macht voorzien. Voor het testen, [!DNL Commerce] adviseert dat u met de volgende aanbevelingstypes in wisselwerking staat:

   - Meest bekeken - vereist minimale invoergegevens. Gebruikers moeten producten weergeven.
   - Bekeken dit, bekeken die - veelvoudige gebruikers vereist om veelvoudige producten te bekijken.
   - Koop dit, kocht dat - Vereist veelvoudige gebruikers om veelvoudige producten te kopen.

### Caveats

- De gedrag en catalogusgegevens van de niet-productie [ Ruimte van Gegevens SaaS ](../landing/saas.md#saas-configuration) identificeren een geïsoleerd milieu waarin de resulterende productaanbevelingen volledig op de gedragsgegevens gebaseerd zijn die op de bijbehorende storefront worden geproduceerd.

- Omdat u niet over grote hoeveelheden gedragsgegevens beschikt, zijn de inputgegevens voor de gegevenssamenvoeging van de computer weinig. Deze gegevens worden echter nog steeds naar Sensei verzonden om de modellen voor machinaal leren te berekenen en aanbevelingen te doen op basis van gegevens die binnen deze omgeving zijn gegenereerd.
