---
title: De integratie configureren
description: Leer hoe u uw Adobe Commerce-project en Experience Manager Assets-projecten kunt verbinden om de synchronisatie van middelen tussen deze twee systemen mogelijk te maken.
feature: CMS, Media
exl-id: 3533d010-926f-4d78-935c-98a9b7040d27
source-git-commit: d59c9d179018318d7a0ab1685d8e9e172eefa3ed
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 0%

---

# De integratie configureren

Configureer de integratie door Commerce aan te sluiten op de AEM Assets-instantie en de bijbehorende strategie voor de synchronisatie van bedrijfsmiddelen te selecteren.

Nadat u het AEM Assets-project hebt geïdentificeerd, selecteert u de regel voor het synchroniseren van elementen tussen Adobe Commerce en AEM Assets.

* **[!UICONTROL Match by product SKU]** - Standaard regel die SKU in de activameta-gegevens met het [ product SKU van Commerce ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/glossary#sku) aanpast om ervoor te zorgen dat de activa met de correcte producten worden geassocieerd.

* **[!UICONTROL Custom match]** - Het stemmen regel voor complexere scenario&#39;s of specifieke bedrijfsvereisten die aangepaste passende logica vereisen. Voor het implementeren van aangepaste overeenkomsten moet in Adobe Developer App Builder aangepaste code worden ontwikkeld om te bepalen hoe elementen op producten worden afgestemd. Binnenkort komen er meer details...

Voor de aanvankelijke opstelling, gebruik de standaard *Gelijke door productSKU* regel.

## Vereisten

Controleer voordat u de AEM Assets-integratie configureert of u de volgende stappen hebt uitgevoerd:

* [Het AEM Assets-project configureren](configure-aem.md)

* [!BADGE  PaaS slechts ]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."} [ installeert de pakketten van Adobe Commerce ](configure-commerce.md) om de uitbreiding toe te voegen en de vereiste geloofsbrieven en de verbindingen te produceren om de uitbreiding te gebruiken.

### IMS- en gebruikersmachtigingen

Als u de Asset Selector wilt gebruiken en een vloeiendere installatie wilt uitvoeren in Commerce, hebt u de volgende machtigingen nodig:

>[!BEGINTABS]

>[!TAB  ACCS ]

[!BADGE  slechts SaaS ]{type=Positive tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."}

IMS-verificatie is standaard ingeschakeld. Voeg de gebruiker aan de **AEM Assets DM OpenAPI Gebruikers toe - levering** productprofiel in [ Adobe Admin Console ](https://adminconsole.adobe.com/) om toegang tot de leveringslaag van AEM Assets te verlenen.

![ het productprofiel van Admin Console voor levering AEM Assets ](../assets/aem-assets-delivery-product-profile.png){width="600" zoomable="yes"}

>[!TAB  PaaS ]

[!BADGE  slechts PaaS ]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."}

1. [ laat Adobe IMS voor Commerce ](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/ims/adobe-ims-config.html){target=_blank} toe door de instructies in de *Gids van Admin van Commerce te volgen*.

1. [ Open een kaartje van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) om een identiteitskaart van de Cliënt van douaneIMS voor de Selecteur van Activa te verzoeken.

1. Voeg de gebruiker aan de **AEM Assets DM OpenAPI Gebruikers toe - levering** productprofiel in [ Adobe Admin Console ](https://adminconsole.adobe.com/) om toegang tot de leveringslaag van AEM Assets te verlenen.

>[!ENDTABS]

## De verbinding configureren

1. Open vanuit Commerce Admin de AEM Assets Integration-configuratie.

   1. Ga naar **[!UICONTROL Store]** > Configuratie > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]** .

      ![ de Integratie van AEM Assets laat de integratie ](../assets/aem-assets-view.png){width="600" zoomable="yes"} toe

>[!INFO]
>
> De integratie van AEM Assets steunt slechts configuratie bij het globale (gebrek) werkingsgebied. Configuratie op websiteniveau wordt niet ondersteund. Wanneer u probeert om de integratie op het niveau van de Website te vormen, negeert het systeem website-vlakke montages en gebruikt in plaats daarvan de globale configuratiewaarden.

1. [!BADGE  PaaS slechts ]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."} gaat **[!UICONTROL Asset Selector IMS Client ID]** in.

   Deze id is vereist om de functie Asset Selector en de functie Automatisch invullen in te schakelen voor de velden Programma-id en Milieu-id. Zie [ IMS en gebruikerstoestemmingen ](#ims-and-user-permissions) om deze identiteitskaart te verkrijgen. Voor details over de Selecteur van Activa, zie [ manueel selecterend activa ](../synchronize/asset-selector-integration.md).

1. Selecteer de AEM Assets-omgeving **[!UICONTROL Program ID]** en **[!UICONTROL Environment ID]** in de vervolgkeuzemenu&#39;s.

   De dropdowns automatisch bevolkt op basis van de zitting IMS van de gebruiker. Om deze eigenschap te gebruiken, verzeker u juiste [ IMS en gebruikerstoestemmingen ](#ims-and-user-permissions) hebt.

   Als de vervolgkeuzelijsten niet beschikbaar zijn, kunt u de id&#39;s handmatig invoeren via de AEM Cloud Manager-URL: `https://author-p[Program ID]-e[EnvironmentID].adobeaemcloud.com/`

   Bewerk de configuratiewaarden door de selectie uit *[!UICONTROL Use system value]* te verwijderen.

1. [!BADGE  slechts PaaS ]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."} Selecteer [[!UICONTROL Commerce integration]](configure-commerce.md#add-the-integration-to-the-commerce-environment) voor het voor authentiek verklaren van verzoeken tussen Commerce en de activa passende dienst.

1. Stel **[!UICONTROL Synchronization enabled]** in op `Yes` als u wilt dat Commerce binnenkomende updates van AEM Assets accepteert.

   Nadat u de integratie hebt ingeschakeld, zijn aanvullende configuratieopties beschikbaar om criteria voor het afstemmen van elementen op te geven.

1. Selecteer in het vervolgkeuzemenu **[!UICONTROL Asset matching rule]** een van de regels voor het afstemmen van elementen voor het synchroniseren van elementen.

   * Selecteer **[!UICONTROL Match by SKU]** voor [ standaard automatische aanpassing ](../synchronize/default-match.md),
   * Selecteer **[!UICONTROL Custom match]** voor [ douane automatische aanpassing ](../synchronize/custom-match.md) (vereist [ Adobe Developer App Builder ](https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder).)

1. Voeg de [ AEM Assets naam van het meta-gegevensgebied ](configure-aem.md#configure-metadata) toe die voor het product SKUs van Commerce op het **[!UICONTROL Match by product SKU attribute name]** gebied wordt bepaald, `commerce:skus` door gebrek.

1. Selecteer **[!UICONTROL Save Config]** om updates toe te passen en de synchronisatie van elementen te starten.

   De configuratieupdate activeert het eerste synchronisatieproces, zodat Commerce binnenkomende updates van AEM Assets kan accepteren. De tijd die nodig is voor synchronisatie is afhankelijk van het volume van elementen en specifieke configuraties. De integratie gebruikt geautomatiseerde processen om de tijd die nodig is voor synchronisatie te minimaliseren.

### Synchronisatie SLA

De integratie garandeert de volgende synchronisatieprestatieniveaus:

* `< 5 minutes for 99% of updates`

* `< 30 minutes for 99.9% of updates`

Op deze manier zorgt u ervoor dat op productpagina&#39;s altijd de meest actuele afbeeldingen worden weergegeven, zodat de inhoud van de winkel nauwkeurig blijft en visueel aantrekkelijk is.

### De eigenaar van de visualisatie configureren

Het **plaatsen van de Eigenaar van de Visualisatie** bepaalt welk systeem productbeelden in de integratie dient:

* Adobe Commerce - Hierbij worden afbeeldingen gebruikt die in Commerce worden gehost.

* AEM Assets - Hierbij worden afbeeldingen gebruikt die vanuit AEM zijn gesynchroniseerd.

Admin toont de beschikbare beelden voor die eigenaar, terwijl de rest beelden grayed uit en getoond met a **verborgen** etiket worden.

Zie het [ plaats beelddetails ](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/digital-assets/product-image#set-image-details){target=_blank} onderwerp voor details op beeldvertoningsgedrag.

>[!TIP]
>
> Tijdens een migratie van Commerce aan AEM Assets, plaats de **Eigenaar van de Visualisatie** aan Commerce om gebroken beeldverbindingen te vermijden. Nadat alle producten met AEM Assets zijn gesynchroniseerd, schakelt u over naar de AEM Assets-eigenaar om de overgang te voltooien. Dit verzekert ononderbroken beeldbeschikbaarheid door het proces.

1. Navigeer naar **[!UICONTROL Store]** > Configuratie > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]** .

   ![ de visualisatieeigenaareigenschap van de Integratie van AEM Assets ](../assets/visualization-owner-detail.png){width="400" zoomable="yes"}

1. Selecteer de **bron van de Eigenaar van de Visualisatie** om de beelden te tonen.

1. Klik op **[!UICONTROL Save Config]** om updates toe te passen en de synchronisatie van elementen te starten.

### Optioneel. De URL van het aangepaste domein configureren

Als het project van AEM Assets as a Cloud Service met de Naam van het Domein van de a [ Douane ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name){target=_blank} is gevormd, moet u de domeinnaam aan de de archiefconfiguratie van Commerce toevoegen zodat de integratie van AEM Assets voor Commerce het kan gebruiken.

1. Navigeer naar **[!UICONTROL Store]** > Configuratie > **[!UICONTROL ADOBE SERVICES]** > **[!UICONTROL AEM Assets Integration]** .

   ![ de Integratie van AEM Assets laat de integratie ](../assets/aem-assets-view.png){width="700" zoomable="yes"} toe

1. Voeg **URL van het Domein van de Douane** aan het **[!UICONTROL Asset Custom Domain]** gebied toe.

1. Klik op **[!UICONTROL Save Config]** om updates toe te passen en de synchronisatie van elementen te starten.

## Volgende stap

* **vorm uw Commerce Storefront** - om AEM Assets met Commerce te gebruiken Storefront die door Edge Delivery Services wordt aangedreven, voltooi de storefront configuratie die in het [ wordt beschreven de integratie van AEM Assets ](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/aem-assets-configuration/) onderwerp in de *documentatie van Adobe Commerce Storefront*.

* Opstelling [ passende regels ](../synchronize/default-match.md) tussen Adobe Commerce en de integratie van AEM Assets.

* [ beheert de activa van Commerce ](../manage-assets.md).
