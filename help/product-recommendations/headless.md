---
title: Koploos
description: Leer hoe te om  [!DNL Product Recommendations]  in een headless winkel te integreren.
exl-id: c40dac31-f87e-402a-ba50-e8aa4c1d66aa
source-git-commit: 1548b7e11249febc2cd8682581616619f80c052f
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# Koploos

U kunt [!DNL Product Recommendations] in een headless winkel integreren gebruikend of [&#x200B; PWA Studio &#x200B;](https://developer.adobe.com/commerce/pwa-studio/) of een douane vooruitgangsend technologie, zoals React of Vue JS.

Aangepaste integratoren en ontwikkelaars zonder kop dienen deze Luma- en PWA-instructies te gebruiken als een voorgestelde implementatie. Er zijn vele manieren om de Aanbevelingen van het Product in hoofdloze oplossingen uit te voeren en deze documentatie behandelt niet alle scenario&#39;s. Integratoren moeten gebeurtenissen, ontwerpen en testen voor hun implementaties bestrijken.

[!DNL Product Recommendations] vereist [&#x200B; gedrag en catalogusgegevens &#x200B;](https://experienceleague.adobe.com/docs/commerce/product-recommendations/developer/development-overview.html?lang=nl-NL) om te werken. Het synchronisatieproces van catalogusgegevens blijft ongewijzigd in een headless-implementatie, maar er zijn wijzigingen nodig voor het verzamelen van gedragsgegevens.

>[!NOTE]
>
>De instanties zonder kop moeten het afspelen implementeren om het dashboard met productaanbevelingen van stroom te voorzien.

Als u [!DNL Product Recommendations] wilt integreren in een koploze winkel, moet u:

1. Verstuur gedragsgegevens naar Adobe Sensei om de resultaten van de productaanbeveling te analyseren en te berekenen. U kunt extra gegevens ook verzenden om productaanbeveling [&#x200B; metriek toe te laten die &#x200B;](workspace.md) rapporteert.

1. Resultaten van productaanbevelingen ophalen en deze resultaten op de pagina weergeven.

U kunt beide handelingen uitvoeren met de beschikbare SDK&#39;s, zoals beschreven in de volgende workflow.

1. [&#x200B; installeer &#x200B;](install-configure.md) de [!DNL Product Recommendations] module.

1. Installeer en gebruik [&#x200B; de Gebeurtenis van Adobe Commerce Storefront SDK &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) om de [&#x200B; gedragsgebeurtenissen &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#product-recommendations) in brand te steken.

   De minimaal vereiste gebeurtenissen om [!DNL Product Recommendations] -resultaten te retourneren:

   | Gebeurtenis | Categorie |
   |--- | ---|
   | `view` | product |
   | `add-to-cart` | product |
   | `place-order` | uitchecken |

   Om [&#x200B; metriek toe te laten die &#x200B;](workspace.md) melden, worden de volgende extra gebeurtenissen vereist:

   | Gebeurtenis | Categorie |
   |--- | ---|
   | `impression-render` | aanbeveling-eenheid |
   | `view` | aanbeveling-eenheid |
   | `rec-click` | aanbeveling-eenheid |
   | `rec-add-to-cart-click` | aanbeveling-eenheid (als een knop &quot;Toevoegen aan winkelwagentje&quot; aanwezig is in de sjabloon met aanbevelingen) |

1. Wanneer de gebeurtenissen in brand worden gestoken, gebruik de [&#x200B; Collector van de Gebeurtenis van Adobe Commerce Storefront &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) om de gebeurtenissen te behandelen en hen te verzenden naar Adobe Sensei.

1. Nadat het gedragsgegeven wordt verzameld, kunt u [&#128279;](create.md) in Admin [!DNL Product Recommendations] creëren.

1. Gebruik de [&#x200B; Aanbevelingen SDK &#x200B;](https://developer.adobe.com/commerce/services/product-recommendations/) om de aanbevelingen eenheden op de storefront te halen. De SDK retourneert de benodigde productgegevens voor het weergeven van aanbevolen eenheden op een pagina.

1. Leer hoe te om de [`recommendations` vraag van GraphQL &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/product-recommendations/queries/recommendations/) te gebruiken om informatie over de blokken van de productaanbeveling voor bepaalde SKU en meer terug te keren.
