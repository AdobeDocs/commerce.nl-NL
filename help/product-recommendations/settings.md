---
title: Instellingen
description: Leer hoe te om de bron van uw  [!DNL Product Recommendations]  gegevens te veranderen en hoe te om visuele aanbevelingen toe te laten.
exl-id: fe37624d-c53e-40cd-b182-10f62cba74c0
source-git-commit: 458f34c45406db871ec61ff408aa624f163b6ee0
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Instellingen

Wanneer u [&#x200B; een SaaS gegevensruimte &#x200B;](../landing/saas.md#saas-configuration) voor Aanbevelingen vormt, verzamelt de SaaS gegevensruimte catalogusgegevens en opslag-gedrag gegevens. [&#x200B; Adobe AI &#x200B;](https://business.adobe.com/nl/ai.html) analyseert dat de gegevens en de productverenigingen verwerken die worden gebruikt om de Aanbevelingen van het Product te dienen.

Niet-productieomgevingen voor het testen of opvoeren hebben doorgaans niet de hoeveelheid of kwaliteit van gedragsgegevens van de winkel om realistische productaanbevelingen te kunnen doen. Werkelijk winkelgedrag op schaal kan alleen in een productieomgeving worden vastgelegd. Om dit probleem op te lossen, staat Adobe Commerce u toe om productaanbevelingen van uw productiemilieu met andere, niet productieSaaS gegevensruimten te gebruiken. Met werkelijke storefront-gegevens in een niet-productieomgeving kunt u een voorvertoning weergeven van de aanbevelingen die uw klanten zien en experimenteren met verschillende soorten aanbevelingen en plaatsingslocaties. Aanbevelingen vanuit een andere SaaS-gegevensruimte kunnen door kopers worden voorvertoond, maar er wordt niet op geklikt.

Staging-orders worden opgenomen met de testvolgorde `environmentId` . Zij heeft geen invloed op de productiegegevens. De productiegegevens worden opgehaald met de `alternateEnvironmentId` .

>[!NOTE]
>
>Wanneer het gebruiken van de Aanbevelingen van het Product door REST, kan de `alternateEnvironmentId` parameter worden gebruikt om andere dataspaces te specificeren. Wanneer het gebruiken van de Aanbevelingen van het Product door [&#x200B; GraphQL &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/), is deze parameter niet beschikbaar.

## Kies de bron voor aanbevelingen

Als u de bron van de gegevens van uw productaanbevelingen wilt wijzigen, kiest u de SaaS-gegevensruimte met de gedragsgegevens die u wilt gebruiken. Voordat u begint, moet u ervoor zorgen dat:

- De gegevensinzameling van de opslag moet [&#x200B; worden gevormd en worden toegelaten &#x200B;](install-configure.md) voor uw productiemilieu en [&#x200B; verifieerde &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/verify/) dat het gedragsgegevens worden verzonden naar Adobe Commerce.
- De niet-productieomgevingscatalogus moet in wezen hetzelfde zijn als de productiecatalogus. Het gebruik van vergelijkbare catalogi zorgt ervoor dat de eenheden van de productaanbeveling de eenheden in productie dicht navielen.

1. Meld u aan bij de beheerder van uw Adobe Commerce-omgeving die niet voor productie is bedoeld.

1. Op _Admin_ sidebar, ga **Marketing** > _Bevorderingen_ > **Aanbevelingen van het Product**.

1. Klik **Montages**.

   ![&#x200B; montages van de productaanbeveling &#x200B;](assets/settings.png)
   _Montages_

1. In de _bron van Aanbevelingen_ sectie, laat de **aanbevelingen van de Ophalen van een verschillende SaaS gegevensruimte** optie toe. De _bron van Aanbevelingen_ sectie verschijnt slechts in een non-production milieu.

   Een lijst van _Beschikbare Spaties van Gegevens SaaS_ verschijnt.

   ![&#x200B; montages van de productaanbeveling &#x200B;](assets/settings-select-saas.png)
   _Montages_

1. Selecteer de SaaS-gegevensruimte met winkelgegevens die u wilt gebruiken.

1. Klik **sparen veranderingen**.

   Adobe Commerce haalt nu aanbevelingen op uit de geselecteerde gegevensruimte.

   >[!NOTE]
   >
   > Terwijl u aanbevelingen kunt bekijken die van een andere SaaS gegevensruimte op de niet-productiereilter worden gehaald, kunt u niet de aanbevelingen klikken.

### Een nieuwe SaaS-gegevensruimte configureren

1. In de Bron van Aanbevelingen sectie, geeft de klik **Configuratie** uit.

1. Volg de instructies om een nieuwe [[!DNL Commerce]  dienst &#x200B;](/help/landing/saas.md) te vormen.

## Visuele aanbevelingen inschakelen

Als de [&#x200B; Visuele module van de Aanbevelingen van het Product &#x200B;](install-configure.md) geïnstalleerd is, moet u Visuele Aanbevelingen toelaten om het [&#x200B; Visuele &#x200B;](type.md#visualsim) type van de aanbeveling van de Gelijksgelijkenis te gebruiken.

In de _Visuele sectie van Aanbevelingen_, plaats **laat Visuele Aanbevelingen** aan de actieve positie toe.
