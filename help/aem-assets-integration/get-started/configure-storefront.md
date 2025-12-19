---
title: Uw winkelfront configureren
description: Leer hoe u uw Edge Delivery Services-winkel koppelt aan uw AEM Assets-integratie.
feature: CMS, Media, Integration
source-git-commit: d426c7878f7a66fe1047673be7c5bf65ae1949a7
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Uw winkelfront configureren

Bij de integratie met AEM Assets worden productafbeeldingen weergegeven die in AEM Assets worden beheerd, in plaats van afbeeldingen die in Adobe Commerce worden gehost. De integratie maakt verbeterde mogelijkheden voor imagebeheer mogelijk, zoals geavanceerde optimalisatie, bijsnijden en levering via het CDN (Content Delivery Network) van Adobe.

Om de integratie in Commerce storefronts toe te laten die door Edge Delivery Services worden aangedreven, werk het storefront configuratiedossier (`config.json`) bij om de `"commerce-assets-enabled": true` parameter toe te voegen.

```json
{
  "public": {
    "default": {
      "commerce-assets-enabled": true
    }
  }
}
```

De Commerce-drop-ins detecteren automatisch de `commerce-assets-enabled` -configuratie en passen de afbeeldingsverwerking aan.

Voor meer informatie over hoe te om AEM Assets met Commerce te gebruiken Storefront die door Edge Delivery Services wordt aangedreven, voltooi de storefrontconfiguratie in het [&#x200B; wordt beschreven integratie van AEM Assets &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/aem-assets-configuration/) onderwerp in de *Adobe Commerce Storefront* documentatie die.
