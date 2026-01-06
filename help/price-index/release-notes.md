---
title: '[!DNL Catalog Adapter] Opmerkingen bij de release'
description: De recentste versieinformatie voor  [!DNL Catalog Adapter]  voor Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
roles: Admin, Developer
exl-id: d4dd0288-8853-43fe-9103-1aead8d3b56e
source-git-commit: 47419e7e19611dc4a045c195f259e2126ab77372
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# [!DNL Catalog Adapter] Opmerkingen bij de release Extension

In deze releaseopmerkingen worden de nieuwste versies van de extensie [!DNL Catalog Adapter] beschreven. Er wordt ondersteuning geboden voor de belangrijkste uitgebrachte versie. Opmerkingen bij de release voor oudere versies worden ter referentie verschaft.

Updates zijn:

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Nieuwe eigenschappen
![&#x200B; bevestig &#x200B;](../assets/fix.svg) Bevestigingen en verbeteringen
![&#x200B; Bug &#x200B;](../assets/bug.svg) Bekende kwesties


>[!NOTE]
>
>De [&#x200B; uitbreiding van de Adapter van de Catalogus &#x200B;](catalog-adapter.md) maakt prijsindexering van Adobe Commerce onbruikbaar. Als u de toepassing hebt geïnstalleerd, kunt u de versie controleren die op uw systeem is geïnstalleerd met behulp van composer. In sommige gevallen kunt u de extensie van de catalogusadapter op uw systeem upgraden om oplossingen of nieuwe mogelijkheden op te halen zonder de Commerce Service-versie bij te werken.

## Huidige hoofdversie

## 1.0.10 Release

![&#x200B; beval &#x200B;](../assets/fix.svg) een kwestie vast waar de prijsvragen voor ingevoerde of onlangs gecreeerde bundelproducten in interne serverfouten konden resulteren omdat het systeem probeerde om samengevoegde SKU voor raadpleging in plaats van correcte, geldige SKU te gebruiken. De vragen van de prijs voor bundelproducten gebruiken nu aangewezen SKU en lossen correct op.<!--MDEE-1040-->

## 1.0.9 Release

![&#x200B; Toegevoegde verenigbaarheid voor PHP 8.4 herstellen &#x200B;](../assets/fix.svg). <!--MDEE-941-->

## 1.0.8 Release

![&#x200B; beval &#x200B;](../assets/fix.svg) een kwestie vast die een fout in het uitzonderingslogboek veroorzaakte wanneer het toevoegen van configureerbare productvarianten met numerieke SKUs aan de wenslijst. <!--MDEE-876-->
