---
title: Het AEM Assets-project configureren
description: Schakel naadloze synchronisatie van middelen tussen Adobe Commerce en AEM Assets in door de vereiste metagegevens voor de integratie toe te voegen.
feature: CMS, Media, Integration
exl-id: a5d2cbab-5ea1-446b-8ab2-2c638128a40c
source-git-commit: 6cd37fda03bb51a1375b0e9dc542f9e02d3c6e54
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 0%

---

# AEM Assets-project configureren voor ondersteuning van Commerce-metagegevens

Als u Commerce-elementbestanden in AEM Assets wilt beheren, voert u de volgende stappen uit om het AEM Assets-project te configureren met de vereiste vaste code en metagegevens voor het beheer van Commerce-elementen in de AEM-ontwerpomgeving.

* **Stap 1:** installeer een het projectmalplaatje van AEM met de boilerplate code om Commerce toe te voegen namespace en de middelen van het meta-gegevensschema aan de de milieuconfiguratie van as a Cloud Service van Experience Manager Assets.
* **Stap 2:** Opstelling het meta-gegevensprofiel om op de activadossiers van Commerce van toepassing te zijn

## De bouwsteencode toevoegen aan uw AEM-project

Adobe biedt een AEM Commerce boilerplate, `assets-commerce` , voor het toevoegen van Commerce-naamruimte en metagegevensschema-bronnen aan de Experience Manager Assets as a Cloud Service-omgevingsconfiguratie. Stel deze code aan uw milieu als a **Gemaakt** pakket op. Configureer vervolgens de Commerce-metagegevens in de AEM Assets-ontwerpomgeving om de installatie te voltooien.

In het tekstbouwplan worden de volgende bronnen toegevoegd aan de AEM Assets-ontwerpomgeving:

* A [&#x200B; douanenamespace &#x200B;](https://github.com/ankumalh/assets-commerce/blob/main/ui.config/jcr_root/apps/commerce/config/org.apache.sling.jcr.repoinit.RepositoryInitializer~commerce-namespaces.cfg.json), `Commerce` om op Commerce betrekking hebbende eigenschappen te identificeren.

   * Een aangepast metagegevenstype `commerce:isCommerce` met het label `Eligible for Commerce` om Commerce-elementen die aan een Adobe Commerce-project zijn gekoppeld, van tags te voorzien.

   * Een aangepast metagegevenstype `commerce:skus` en een overeenkomende UI-component om een eigenschap **[!UICONTROL Product Data]** toe te voegen. De Gegevens van het product omvatten de meta-gegevenseigenschappen om een activa van Commerce met product SKUs te associëren.

     ![&#x200B; Controle UI van de Gegevens van het Product van de Douane &#x200B;](../assets/aem-commerce-sku-metadata-fields-from-template.png){width="600" zoomable="yes"}

   * Een aangepast type metagegevens `commerce:roles` en `commerce:positions` om te tonen hoe het element in Commerce wordt weergegeven.

* Een metagegevensschema met een Commerce-tabblad dat de velden `Eligible for Commerce` en `Product Data` bevat voor het labelen van Commerce-elementen. Het formulier bevat ook opties voor het weergeven of verbergen van de velden `roles` en `position` in de gebruikersinterface van AEM Assets.

  ![&#x200B; Commerce lusje voor de vorm van het de meta-gegevensschema van AEM Assets &#x200B;](../assets/assets-configure-metadata-schema-form-editor.png){width="600" zoomable="yes"}

* A [&#x200B; steekproef geëtiketteerde en goedgekeurde activa van Commerce &#x200B;](https://github.com/ankumalh/assets-commerce/blob/main/ui.content/src/main/content/jcr_root/content/dam/wknd/en/activities/hiking/equipment_6.jpg/.content.xml) `equipment_6.jpg` om aanvankelijke activasynchronisatie te steunen. Alleen goedgekeurde Commerce-middelen kunnen van AEM Assets naar Adobe Commerce worden gesynchroniseerd.

>[!NOTE]
>
> Zie [&#x200B; Lees &#x200B;](https://github.com/ankumalh/assets-commerce) pagina voor meer informatie over **Commerce boilerplate van AEM**.

### Vereisten

U hebt de volgende bronnen en machtigingen nodig om het `commerce-assets` -pakket te implementeren in de AEM Assets as a Cloud Service AEM-omgeving:

* [&#x200B; Toegang tot het Programma van AEM Assets Cloud Manager en milieu&#39;s &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager#access-sysadmin-bo) met de rollen van de Manager van het Programma en van de Plaatsing.

* A [&#x200B; lokale de ontwikkelomgeving van AEM &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview) en vertrouwdheid met het lokale ontwikkelingsproces van AEM.

* Begrijp [&#x200B; het projectstructuur van AEM &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure) en hoe te om de pakketten van de douaneinhoud op te stellen gebruikend Cloud Manager.

### Het pakket `commerce-assets` installeren

1. Creëer vanuit de AEM Cloud Manager productie- en staging-omgevingen voor uw AEM Assets-project, indien nodig.

1. Vorm een plaatsingspijpleiding, indien nodig.

1. Van GitHub, download de code van [&#x200B; AEM Commerce boilerplate &#x200B;](https://github.com/ankumalh/assets-commerce).

1. Van uw [&#x200B; lokale de ontwikkelomgeving van AEM &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview), installeer de douanecode in uw het milieuconfiguratie van AEM Assets als Geweven pakket, of door de code in de bestaande projectconfiguratie manueel te kopiëren.

1. Leg de wijzigingen vast en duw uw lokale ontwikkelingsvertakking naar de Cloud Manager Git-opslagplaats.

1. Van AEM Cloud Manager, [&#x200B; stelt uw code op om het milieu van AEM &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code#deploying-code-with-cloud-manager) bij te werken.

## Optioneel. Een metagegevensprofiel configureren

Stel in de AEM Assets-auteursomgeving standaardwaarden in voor metagegevens van Commerce-elementen door een metagegevensprofiel te maken. Pas vervolgens het nieuwe profiel toe op de mappen AEM Asset om deze standaardinstellingen automatisch te gebruiken. Deze configuratie stroomlijnt de verwerking van bedrijfsmiddelen door handmatige stappen te verminderen.

Wanneer u het profiel van meta-gegevens vormt, moet u slechts de volgende componenten vormen:

* Voeg een Commerce-tabblad toe. Op dit tabblad worden Commerce-specifieke configuratie-instellingen ingeschakeld die door de sjabloon worden toegevoegd
* Voeg het veld `Eligible for Commerce` toe aan het tabblad Commerce.

De UI-component Productgegevens wordt automatisch toegevoegd op basis van de sjabloon.

### Het metagegevensprofiel definiëren

1. Meld u aan bij de Adobe Experience Manager-ontwikkelomgeving.

1. Ga in de Adobe Experience Manager-werkruimte naar de werkruimte voor het beheer van inhoud van de auteur voor AEM Assets door op het Adobe Experience Manager-pictogram te klikken.

   ![&#x200B; AEM Assets authoring &#x200B;](../assets/aem-assets-authoring.png){width="600" zoomable="yes"}

1. Open de Hulpmiddelen van de Beheerder door het hamerpictogram te selecteren.

   ![&#x200B; Admin van de Auteur van AEM beheert meta-gegevensprofielen &#x200B;](../assets/aem-manage-metadata-profiles.png){width="600" zoomable="yes"}

1. Open de pagina voor profielconfiguratie door op **[!UICONTROL Metadata Profiles]** te klikken.

1. **[!UICONTROL Create]** een metagegevensprofiel voor de Commerce-integratie.

   ![&#x200B; Admin van de Auteur van AEM voegt meta-gegevensprofielen &#x200B;](../assets/aem-create-metadata-profile.png){width="600" zoomable="yes"} toe

1. Voeg een tabblad toe voor Commerce-metagegevens.

   1. Klik links op **[!UICONTROL Settings]** .

   1. Klik op **[!UICONTROL +]** in de tabsectie en geef vervolgens de **[!UICONTROL Tab Name]** , `Commerce` op.

1. Voeg het veld `Eligible for Commerce` toe aan het formulier.

   ![&#x200B; Admin van de Auteur van AEM voegt meta-gegevensgebieden aan profiel toe &#x200B;](../assets/aem-edit-metadata-profile-fields.png){width="600" zoomable="yes"}

   * Klik op **[!UICONTROL Build form]**.

   * Sleep het veld `Single Line text` naar het formulier.

   * Voeg de tekst `Eligible for Commerce` voor het label toe door op **[!UICONTROL Field Label]** te klikken.

   * Voor het lusje van Montages, voeg de etikettekst aan **Etiket van het Gebied** toe.

   * Stel de plaatsaanduidingstekst in op `yes` .

   * Kopieer en plak in het veld **[!UICONTROL Map to Property]** de volgende waarde

     ```terminal
     ./jcr:content/metadata/commerce:isCommerce
     ```

1. Optioneel. Als u goedgekeurde Commerce-elementen automatisch wilt synchroniseren terwijl deze naar de AEM Assets-omgeving worden geüpload, stelt u de standaardwaarde voor het veld _[!UICONTROL Review Status]_&#x200B;op de `Basic` tab in op `approved` .

1. Sla de update op.

#### Het metagegevensprofiel toepassen op de bronmap van Commerce-elementen

1. Van de [!UICONTROL &#x200B; Metadata Profiles] pagina, selecteer het de integratieprofiel van Commerce.

1. Selecteer **[!UICONTROL Apply Metadata Profiles to Folders]** in het menu Handeling.

1. Selecteer de map met Commerce-elementen.

   Maak een Commerce-map als deze niet bestaat.

1. Klik op **[!UICONTROL Apply]**.

## Volgende stappen

[!BADGE &#x200B; PaaS slechts &#x200B;]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."} [&#x200B; installeer de pakketten van Adobe Commerce &#x200B;](configure-commerce.md)

**vorm uw die Storefront van Commerce** - AEM Assets met Commerce Storefront te gebruiken door Edge Delivery Services wordt aangedreven, voltooi de storefront configuratie in het [&#x200B; wordt beschreven EDS AEM Assets configuratie &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/setup/configuration/aem-assets-configuration/) onderwerp dat.
