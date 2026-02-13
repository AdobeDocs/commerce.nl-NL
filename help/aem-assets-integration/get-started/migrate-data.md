---
title: Mediabestanden migreren naar AEM
description: Mediabestanden migreren van Adobe Commerce of een externe bron naar de AEM Assets DAM.
feature: CMS, Media, Integration
exl-id: ccb13e90-8b18-4f1e-94ce-f0dacea2f617
source-git-commit: ac880333814d9d9a45e658e2a637cd9634dbfb1f
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Mediabestanden migreren naar de AEM Assets DAM

Zowel Adobe Commerce als Adobe Experience Manager (AEM) verstrekken ingebouwde eigenschappen om media dossiermigratie van Commerce aan het AEM Assets **digitale systeem van het activabeheer (DAM) te stroomlijnen**. U kunt ook mediabestanden migreren uit andere bronnen.

## Vereisten

| Categorie | Vereiste |
|----------|-------------|
| **vereisten van het Systeem** | <ul><li>AEM as a Cloud Service-omgeving voorzien van AEM Assets</li><li>Voldoende opslagcapaciteit</li><li>Netwerkbandbreedte voor grote bestandsoverdrachten</li></ul> |
| **Vereiste toegang en toestemmingen** | <ul><li>Toegang tot AEM Assets as a Cloud Service voor beheerders</li><li>Toegang tot het bronsysteem waar mediabestanden worden opgeslagen (Adobe Commerce of extern systeem)</li><li>Geschikte machtigingen voor toegang tot cloudopslagservices</li></ul> |
| **de Rekening van de Opslag van de Wolk** | <ul><li>AWS S3- of Azure Blob Storage-account</li><li>Configuratie van privécontainer/emmertje</li><li>Verificatiegegevens</li></ul> |
| **Inhoud Source** | <ul><li>Georganiseerde mediabestanden gereed voor migratie</li><li>Beeld en videodossiers in <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/file-format-support#image-formats"> formaten die door AEM Assets </a> worden gesteund.</li><li>Schone, gedupliceerde elementen</li></li> |
| **Voorbereiding van meta-gegevens** | <ul><li><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/aem-asset-management/getting-started/aem-assets-configure-aem"> AEM Assets meta-gegevensprofiel dat voor de activa van Commerce wordt gevormd </a></li><li>Toegewezen metagegevenswaarden voor elk element</li><li>CSV-bestandseditor (bijvoorbeeld Microsoft Excel)</li></ul> |

## Best practices voor migratie

1. Elementen krullen vóór de migratie door ongebruikte en gedupliceerde inhoud te verwijderen.

1. Elementen logisch ordenen op grootte, opmaak of hoofdlettergebruik.

1. Overweeg grote migraties in kleinere batches te splitsen.

1. Plan de bronintensieve invoer tijdens off-piekuren.

1. Metagegevenstoewijzing valideren voordat de bestanden volledig worden geïmporteerd.

## Migratieworkflow

Volg de migratieworkflow om mediabestanden uit Adobe Commerce of een ander extern systeem te exporteren en deze te importeren in AEM Assets DAM.

### Stap 1: Inhoud exporteren uit de bestaande gegevensbron

[!BADGE  slechts PaaS ]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."}

Voor de handelaren van Adobe Commerce, kan de **Verre module van de Opslag** de invoer en de uitvoer van media dossier vergemakkelijken. Met deze module kunnen bedrijven mediabestanden opslaan en beheren met externe opslagservices zoals AWS S3. Aan opstellings verre opslag voor uw instantie van Commerce, zie [ Verre Opslag ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/storage/remote-storage/remote-storage-aws-s3) in de **Gids van de Configuratie van Commerce** vormen.

Als u media dossiers hebt die buiten Adobe Commerce worden opgeslagen, upload hen rechtstreeks aan één van de [ gegevensbronnen ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/assets-view/bulk-import-assets-view#prerequisites) door AEM as a Cloud Service worden gesteund.

### Stap 2: Een CSV-bestand maken voor de toewijzing van metagegevens

Maak een CSV-bestand waarmee elk mediabestand wordt toegewezen aan de Commerce-productgegevens. Kies een van de volgende methoden:

* **Adobe Commerce (PaaS)**: Gebruik het CLI bevel om CSV van uw catalogus auto-te produceren
* Handmatig het CSV-bestand maken

#### Metagegevens exporteren met CLI

[!BADGE  slechts PaaS ]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."}

Met de CLI-opdracht AEM Assets Integration kunt u automatisch een CSV-bestand met metagegevens genereren dat URL&#39;s, posities en rollen van de productmediabestanden bevat die in uw Commerce-project zijn opgeslagen.

1. Beschikbare opdrachten weergeven om te controleren of de AEM Assets Integration-module is geïnstalleerd:

   ```bash
   bin/magento list aem
   ```

   De opdrachten voor aangepaste extensies worden onder `aem` weergegeven aan het begin van de opdrachtlijst.

1. Voer de opdracht voor het exporteren van metagegevens uit met het voorvoegsel van het AEM-pad:

   ```bash
   bin/magento aem:assets:export:csv <AEM-path-prefix>
   ```

   `<AEM-path-prefix>` is het pad naar de basismap waarin uw elementen worden opgeslagen in AEM Assets DAM (bijvoorbeeld `/content/dam/commerce/` ).

   ```bash
   bin/magento aem:assets:export:csv /content/dam/commerce/
   ```

   Hiermee maakt u een `metadata.csv` -bestand in de map `var/export` met URL&#39;s, posities en rollen voor elk productelement in de Commerce-catalogus.

#### De CSV handmatig maken

Voor mediabestanden die buiten Adobe Commerce zijn opgeslagen, maakt u het CSV-bestand handmatig. De kolomkopballen **moeten** de gebiedsnamen aanpassen die in uw [ worden gevormd de meta-gegevensprofiel van AEM Assets ](configure-aem.md). Nadat u het bestand hebt gemaakt, vult u de rijen met de metagegevenswaarden voor elk mediabestand in.

| Metagegevens | Beschrijving | Waarde |
|-------|-------------|--------|
| assetPath | Het volledige pad waar het middel wordt opgeslagen in de AEM Assets-opslagplaats.<br><br> gebruik de weg om subomslagen tot stand te brengen om de activa van Commerce te organiseren, bijvoorbeeld `content/dam/commerce/<brand>/<type>`. | `/content/dam/commerce/<sub-folder>/..<filename>` |
| commerce :positions | De positie/volgorde van het element in productgalerieën | Meerdere numerieke waarden, gescheiden door pipe (&quot;Number: multi&quot;) |
| commerce :isCommerce | Markering die aangeeft of het actief in de handel wordt gebruikt | `Yes` |
| commerce :skus | Product-SKU&#39;s die aan dit element zijn gekoppeld | Meerdere tekenreekswaarden, gescheiden door pipe (String: multi) |
| commerce :roles | De rollen of typen afbeeldingen voor het element (bijvoorbeeld `thumbnail` , `main image` , `swatch` ) | Meerdere waarden, gescheiden door puntkomma&#39;s (bijvoorbeeld &quot;miniatuur; afbeelding; staal_afbeelding; small_image&quot;) |

+++CSV-code

Gebruik deze CSV-voorbeeldcode om het bestand te maken in een code-editor of spreadsheettoepassing zoals Microsoft Excel.

```csv
assetPath,commerce:positions{{Number: multi}},commerce:isCommerce{{String}},commerce:skus{{String: multi}},commerce:roles{{String: multi}}
/content/dam/commerce/sample1.jpg,1,Yes,sku1,thumbnail; image; swatch_image; small_image
/content/dam/commerce/sample2.jpg,1|1|1,Yes,sku1|sku2|sku3,thumbnail; image; swatch_image; small_image|image|image; small_change
```

+++

### Stap 3: Bulkimport van Assets naar AEM Assets

Nadat u het metagegevenstoewijzingsbestand hebt gemaakt, importeert u uw elementen met het gereedschap AEM Assets Bulk importeren.

Hieronder vindt u een overzicht op hoog niveau voor het gebruik van het gereedschap.

1. [ Login aan uw het auteursmilieu van AEM Assets as a Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/aem-users#login-aem).

1. Selecteer in de weergave Experience Manager Tools **[!UICONTROL Assets]** > **[!UICONTROL Bulk Import]** .

   ![ AEM Assets authoring ](../assets/aem-assets-bulk-import-selection.png){width="600" zoomable="yes"}

1. Selecteer in het venster Configuraties voor bulkimport de optie **[!UICONTROL Create]** om het configuratieformulier te openen.

   ![ AEM Assets authoring ](../assets/aem-assets-bulk-import-configuration.png){width="600" zoomable="yes"}

1. Opstelling en sparen de configuratie.

   U hebt het volgende nodig:

   * Verificatiereferenties voor uw gegevensbron
   * De doelmap in AEM Assets waarin geïmporteerde bestanden worden opgeslagen
   * Optioneel. Informatie over de MIME-typen, bestandsgrootte en andere parameters om de importconfiguratie aan te passen
   * Het pad naar het CSV-bestand met metagegevenstoewijzing dat u hebt geüpload naar de opslaginstantie in de cloud.

   Voor gedetailleerde stappen, zie [ het Bulk hulpmiddel van de Invoer ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/add-assets#configure-bulk-ingestor-tool) in de *Gids van de Gebruiker van AEM Assets as a Cloud Service* vormen.

1. Nadat u de configuratie hebt opgeslagen, gebruikt u de gereedschappen voor bulkimport om de importbewerking te testen en uit te voeren.

>[!MORELIKETHIS]
>
> [ Bulk het hulpmiddel van de Invoer videodemo ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/add-assets#asset-bulk-ingestor)
> [Tips, beste praktijken, en beperkingen ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/manage/add-assets#tips-limitations)
> [Elementen uploaden of invoegen met behulp van API&#39;s ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/admin/developer-reference-material-apis#asset-upload)
