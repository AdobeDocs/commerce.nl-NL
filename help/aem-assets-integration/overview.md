---
title: AEM Assets-integratie voor Commerce
description: Leer hoe te om Adobe Experience Manager Assets met uw  [!DNL Commerce]  instantie te integreren om de media dossiers voor uw Commerce opslagefront tot stand te brengen en te beheren.
feature: CMS, Media, Configuration, Integration
exl-id: f450752a-bef1-419e-ad14-ff8879ab204b
source-git-commit: 9e6f8ae86b28577e2b2c675dbf274c762abe9f3f
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---

# AEM Assets-integratie voor Commerce

De vraag naar gepersonaliseerde inhoud neemt snel toe terwijl de marketingbudgetten onder druk staan. Detailhandelaars en merken hebben moeite om gelijke tred te houden met de groeiende behoefte aan variaties in productbeeldvorming, die worden veroorzaakt door regionale, seizoensgebonden en segmentspecifieke vereisten.

Neem bijvoorbeeld een retailer met 1.000 producten. Zelfs voordat u rekening houdt met variaties in kenmerken, neemt het aantal vereiste digitale elementen aanzienlijk toe wanneer u rekening houdt met verschillende regio&#39;s, klantsegmenten en inspanningen op het gebied van personalisatie. Dit kan tot een overweldigend aantal activa variëren, die in miljoenen bereiken.

![ overzicht ](assets/product-visuals-example.png){width="700" zoomable="yes"}

De integratie van AEM Assets pakt deze uitdaging aan door workflows voor middelenbeheer te automatiseren. De integratie zorgt ervoor dat digitale elementen, zoals productafbeeldingen en marketinginhoud, dynamisch worden gekoppeld aan de juiste handelsentiteiten, waaronder producten en categorieën in Adobe Commerce, op basis van SKU of andere sleutelkenmerken. Dit proces stroomlijnt verrichtingen en verbetert efficiency door toe te laten:

* **Naadloze Installatie en Configuratie** - de handelaars teams en de ontwikkelaars kunnen de integratie snel opstelling gebruikend de vertrouwde hulpmiddelen en de werkschema&#39;s van Adobe.

* **Dynamische de Updates van Activa** - de beelden van het Product en marketing activa wijzen automatisch op de recentste veranderingen in AEM Assets, die opslaghoeken nauwkeurig en relevant houden.

* **Gestroomlijnd Beheer van de Catalogus** - Automatiseert activa verfrissen en schoonmaken, minimaliserend handinspanning en het verzekeren van een verenigbare, goed onderhouden productcatalogus.

## Vereisten voor het gebruik van de integratie

Als u deze integratie wilt benutten met Product Visuals of AEM Assets, moeten bedrijven aan de volgende vereisten voldoen:

>[!BEGINTABS]

>[!TAB  Visuals van het Product ]

[!BADGE &#x200B; SaaS slechts &#x200B;]{type=Positive url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."} Actieve vergunningen voor Adobe Commerce, Visuals van het Product die door AEM Assets worden aangedreven, en [ Dynamische Media van AEM ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/assets/dynamic/administering-dynamic-media) (Deze vergunningen zijn beschikbaar uit-van-de-doos met [!DNL Adobe Commerce as a Cloud Service] en [!DNL Adobe Commerce Optimizer]).

>[!TAB  AEM Assets ]

[!BADGE &#x200B; SaaS slechts &#x200B;]{type=Positive url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."} Actieve vergunningen voor Adobe Commerce, Adobe Experience Manager Assets, en [ AEM Dynamische Media ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/assets/dynamic/administering-dynamic-media).

[!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."} Adobe Commerce 2.4.5+

* PHP 8.1, 8.2, 8.3 en 8.4

* Composer 2.x

[!BADGE &#x200B; SaaS slechts &#x200B;]{type=Positive url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."} Adobe Experience Manager wordt provisioned met [ Adobe Experience Manager Assets as a Cloud Service ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/assets/overview)

>[!ENDTABS]

De gebruiker die van Adobe Commerce de integratie vormt moet toegang tot de [ IMS Organisatie ](https://experienceleague.adobe.com/nl/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255) hebben waar het project van AEM Assets provisioned is.

>[!BEGINSHADEBOX]

## Belangrijkste zakelijke voordelen

![ controle ](assets/icon-check.png) **Geen Extra Kosten** - Deze integratie wordt verstrekt kosteloos voor verkopers die aan de vergunningsvereisten voldoen.

![ controle ](assets/icon-check.png) **Officiële Oplossing van Adobe** - ontwikkeld, gehandhaafd, en volledig gesteund door Adobe, die stabiliteit en groepering met toekomstige platformverhogingen verzekeren.

![ controle ](assets/icon-check.png) **Adobe Beheerde Model van de Steun** - de Hulp en het oplossen van problemen worden behandeld direct door Adobe, die vrede van mening en gestroomlijnde probleemresolutie verstrekt.

![ controle ](assets/icon-check.png) **de mogelijkheden van de Bouwer van Adobe Storefront** - de oplossing van het digitale activabeheer (DAM) staat het gebruik van activa als beelden, video&#39;s, en andere media op de [ Bouwer van de Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/merchants/storefront-builder/?lang=nl-NL#userlabs-commerce-genai-product-visuals) toe.

>[!ENDSHADEBOX]

Bekijk deze video om te leren hoe Adobe Commerce en AEM Assets samenwerken om inhoudsworkflows te stroomlijnen:

>[!VIDEO](https://video.tv.adobe.com/v/3447889?captions=dut)

## Volgende stappen

De integratie van Commerce met Experience Manager Assets mogelijk maken is een driestappenproces:

1. [ vorm uw project van AEM Assets om de meta-gegevens van Commerce ](get-started/configure-aem.md) te steunen.

1. [!BADGE &#x200B; PaaS slechts &#x200B;]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."} [ installeert de pakketten van Adobe Commerce ](get-started/configure-commerce.md).

1. [ vorm de integratie ](get-started/setup-synchronization.md).

## Ondersteuning

Als u informatie nodig hebt of vragen hebt die niet in deze gids worden behandeld, contacteer uw vertegenwoordiger van de Integratie van AEM Assets of creeer a [ steunkaartje ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=nl-NL#submit-ticket) om extra hulp te ontvangen.
