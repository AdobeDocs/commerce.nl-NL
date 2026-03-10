---
title: AEM Assets voor Commerce Optimizer configureren
description: Leer hoe te om de Integratie van AEM Assets voor  [!DNL Adobe Commerce Optimizer] te vormen.
feature: CMS, Media, Configuration, Integration
source-git-commit: 7f0970648663331fea2af19b981c4fd3b3aedcaa
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 0%

---


# AEM Assets configureren voor [!DNL Adobe Commerce Optimizer]

[!BADGE &#x200B; slechts SaaS &#x200B;]{type=Positive tooltip="Alleen van toepassing op Adobe Commerce Optimizer-projecten."}

Met de AEM Assets Integration for [!DNL Adobe Commerce Optimizer] kunnen handelaren AEM Assets gebruiken als de gecentraliseerde oplossing voor het beheer van digitale middelen voor productafbeeldingen. Deze handleiding behandelt de specifieke configuratie van [!DNL Commerce Optimizer] .

In tegenstelling tot Adobe Commerce (PaaS) of Adobe Commerce as a Cloud Service (ACCS), heeft [!DNL Commerce Optimizer] geen interface voor Admin-configuratie. Als u de integratie wilt inschakelen, maakt u een ondersteuningsticket met uw [!DNL Adobe Commerce Optimizer] - en AEM Assets-gegevens. Adobe Support configureert de integratie en registreert uw huurder bij de Assets Integration Service.

In het volgende diagram ziet u een overzicht van de productsynchronisatie tussen [!DNL Adobe Commerce Optimizer] en de AEM Assets-integratie.

![&#x200B; AEM Assets aan [!DNL Commerce Optimizer] stroom &#x200B;](../assets/aco-asset-sync-architecture.png){width="700"}

Deze integratie heeft twee hoofdstromen:

* **van AEM Assets**: Wanneer een activa wordt goedgekeurd, verworpen of verwijderd, stroomt de gebeurtenis door de Pijpleiding van Adobe aan de Dienst van de Integratie van Assets. De dienst past activa aan producten aan gebruikend `match-by-SKU` (meta-gegevens-gedreven) of a [&#x200B; douanematcher (App Builder) &#x200B;](../synchronize/custom-match.md){target=_blank}, dan verzendt de `product-asset` afbeeldingen naar Commerce Optimizer, waar zij als productlagen worden opgeslagen.

* **Van[!DNL Adobe Commerce Optimizer]**: Wanneer een product in [!DNL Commerce Optimizer] wordt bijgewerkt, stroomt de gebeurtenis door de Pijpleiding van Adobe aan de Dienst van de Integratie van Assets. De service synchroniseert alle overeenkomende elementen die worden toegewezen naar de [!DNL Adobe Commerce Optimizer] .

## Vereisten

Voordat u de integratie configureert, moet u ervoor zorgen dat:

* Een actieve [!DNL Adobe Commerce Optimizer] -instantie met Product Visuals machtiging of een AEM Assets-licentie met Dynamic Media.
* Toegang tot een AEM Assets as a Cloud Service-omgeving.
* Zowel [!DNL Commerce Optimizer] als AEM Assets in dezelfde Adobe IMS-organisatie.
* Dynamische media met OpenAPI ingeschakeld in uw AEM Assets-omgeving.

## Onboarding

Aan boord de Integratie van AEM Assets met [!DNL Commerce Optimizer], moet u [&#x200B; een steunkaartje &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) creëren.

De Steun van Adobe gebruikt de informatie in uw kaartje om uw huurder bij de Dienst van de Integratie van Assets te registreren, en de integratie te vormen.

Neem de volgende informatie op in uw ondersteuningsticket:

* **[!DNL Adobe Commerce Optimizer]Tenant ID** (Instance ID) gevonden in uw [!DNL Commerce Optimizer] URL of gebruikersinterface van Commerce Cloud Manager.
* **identiteitskaart van het Programma van AEM**.
* **identiteitskaart van het Milieu van AEM**.
* **Matching regel**: Gelijke door SKU of [&#x200B; externe matcher (App Builder) &#x200B;](../synchronize/custom-match.md){target=_blank}.
* **Laag**: De naam van de cataloguslaag om de huurder met te registreren. Geef indien nodig een aangepaste naam op. Anders wordt de standaardwaarde `AEM-Assets` gebruikt.
* **Landinstelling**: De scène van de catalogusbron om de huurder met (bijvoorbeeld, `en-US`) te registreren.

>[!IMPORTANT]
>
> De integratie steunt één bron per huurder, die de combinatie van één scène en één laag is.

Nadat de Steun van Adobe uw kaartje verwerkt, wordt de integratie gevormd en uw huurder wordt geregistreerd met de Dienst van de Integratie van Assets.

Zodra het instappen is voltooid:

1. **Registratie met de Dienst van de Integratie van Assets**: Uw [!DNL Commerce Optimizer] huurder wordt geregistreerd met de Dienst van de Integratie van Assets gebruikend [!DNL Adobe Commerce Optimizer] identiteitskaart van de Aannemer, identiteitskaart van het Programma van AEM, identiteitskaart van het Milieu van AEM, en huurder.

1. **abonnement van de Gebeurtenis**: De Dienst van de Integratie van Assets tekent aan:

   * AEM Assets-gebeurtenissen (middelen goedgekeurd, bijgewerkt, verwijderd)
   * [!DNL Commerce Optimizer] Catalogusgebeurtenissen (product gemaakt, bijgewerkt)

### Beperkingen

De integratie met [!DNL Commerce Optimizer] heeft de volgende beperkingen:

* **Enige laag per koopman** - de Integratie van AEM Assets steunt één laag AEM-Assets per koopman (één bron per huurder). Het configureren van meerdere lagen per leverancier wordt momenteel niet ondersteund.
* **Beelden slechts** - de integratie steunt geen video of andere media types.
* **geen categoriegelen** - de synchronisatie van het beeldbeeld van de Categorie is niet beschikbaar. Categorieafbeeldingen uit AEM Assets voor de Assets Selector (UI-invoeging) worden niet ondersteund.
* **geen multi-site onderscheid** - de integratie behandelt geen multi-plaats; een beeld verbonden aan een product wordt getoond het zelfde over alle kanalen en beleid.
* **de positie/het opdracht geven tot van het Beeld** - de positie en het opdracht geven tot van het Beeld worden niet gesteund.
* **Product moet bestaan** - als het product niet in [!DNL Commerce Optimizer] bestaat, zal de laag niet voor die product-activa afbeelding worden gecreeerd.
* **het gebied van de Laag die** beschrijven-Waarden in een laag beschrijven de basiscatalogus. Als een veld niet wordt verzonden in de laadopdracht, kan dit worden overschreven met een lege waarde. Gebruik een specifieke laag voor AEM Assets-inhoud. Als u een bestaande laag opnieuw gebruikt voor andere doeleinden, kan dit leiden tot onbedoeld gegevensverlies.

### Uw AEM Assets configureren

Het AEM Assets-installatie- en configuratieproces voor [!DNL Commerce Optimizer] is hetzelfde als voor Adobe Commerce as a Cloud Service. Zie [&#x200B; het project van AEM Assets vormen om de meta-gegevens van Commerce &#x200B;](configure-aem.md) voor de volledige stappen te steunen.

Zorg ervoor dat uw AEM Assets-omgeving gereed is:

1. **configuratie van AEM Assets**: Vorm het de meta-gegevensprofiel van Commerce. Zie [&#x200B; een meta-gegevensprofiel &#x200B;](configure-aem.md#configure-a-metadata-profile) vormen.

1. **Dynamische Media enablement**: Verifieer Dynamische Media met mogelijkheden OpenAPI op uw milieu van AEM Assets wordt toegelaten.

## AEM Assets configureren

Configureer uw AEM Assets-omgeving om productsynchronisatie mogelijk te maken.

### Stap 1: Dynamische media inschakelen met OpenAPI

Dynamische media met OpenAPI moeten zijn ingeschakeld in uw AEM Assets-omgeving. Met productvisa en nieuwe AEM Assets-licenties kunt u het product op een zelfbedieningsmanier via Cloud Manager inschakelen. Voor oudere AEM Assets-licenties is ondersteuning van Adobe vereist. Zie [&#x200B; het project van AEM Assets &#x200B;](configure-aem.md#prerequisites) voor enablement stappen vormen.

### Stap 2: Optioneel. Commerce-metagegevensprofiel configureren

Stel het metagegevensprofiel in AEM Assets in om Commerce-specifieke metagegevens op te slaan.

Zie [&#x200B; een meta-gegevensprofiel &#x200B;](configure-aem.md#step-2-optional-configure-a-metadata-profile) voor gedetailleerde instructies vormen.

### Stap 3: Metagegevens toepassen op elementen

Voeg Commerce-metagegevens toe aan uw productafbeeldingen in AEM Assets.

Zie de [&#x200B; het pakketinhoud van AEM Commerce &#x200B;](configure-aem.md#aem-commerce-assets-commerce-package-contents) voor gebiedsdefinities en [&#x200B; vorm een meta-gegevensprofiel &#x200B;](configure-aem.md#step-2-optional-configure-a-metadata-profile) voor de opstellingsstappen.

De activa moeten in een **goedgekeurde** status voor de gegevenssynchronisatie zijn om te teweegbrengen. De gebeurtenis wordt niet geactiveerd wanneer alleen metagegevens worden opgeslagen.

>[!CAUTION]
>
> Wijs de `AEM-Assets` laag aan uw [&#x200B; catalogusmening &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/optimizer/setup/catalog-view) toe. Als de laag niet wordt toegewezen, kunnen de gegevens van het productbeeld onverwacht worden beschreven.

## Synchronisatie

Zodra gevormd, synchroniseert de integratie `product-asset` afbeeldingen automatisch.

Zie [&#x200B; Aangepaste automatische aanpassing &#x200B;](../synchronize/custom-match.md) voor meer informatie.

### Afstemmen op voorbeeld van SKU-workflow

Een doorstroomsnelheid bij het toevoegen van een bestaand element aan een nieuw product:

1. Maak het product in [!DNL Commerce Optimizer] (via API of gegevensinvoer). Het product kan in eerste instantie zonder afbeeldingen bestaan.

1. Open in AEM Assets het element dat u wilt toewijzen aan het product.

1. Voeg productSKU aan de **handel:skus** meta-gegevens toe en wijs beeldrollen (bijvoorbeeld, `thumbnail`, `image`) toe.

1. Het middel goedkeuren voor levering. Dit activeert de gebeurtenis die de Dienst van de Integratie van Assets verwerkt.

1. Assets Integration Service verzendt de product-image-toewijzing naar [!DNL Commerce Optimizer] . Het product in [!DNL Commerce Optimizer] wordt bijgewerkt met de afbeeldingen uit het element.

1. Controleer of de afbeelding zichtbaar is. Zorg ervoor dat de synchronisatie is voltooid (meestal binnen een paar minuten) en controleer het product in de [!DNL Commerce Optimizer] -gebruikersinterface (bijvoorbeeld Gegevenssynchronisatie of catalogusweergave) of vraag de winkel-API&#39;s (Catalog Service, Live Search, Storefront GraphQL API) om te controleren of de afbeelding is geretourneerd.

## Rolverwerking van afbeeldingen

Wanneer een product meerdere elementen heeft die dezelfde afbeeldingsrol gebruiken (bijvoorbeeld twee elementen met de `thumbnail` -rol), zorgt de integratie ervoor dat slechts één element die rol behoudt om dubbele rollen in de [!DNL Commerce Optimizer] -laag en onverwacht storefront-gedrag te voorkomen.

**Gedrag:** wanneer een update van AEM Assets wordt verzonden, ontvangt het recentst bijgewerkte activa de beeldrol (bijvoorbeeld, `thumbnail`), en de rol wordt verwijderd uit het vorige middel dat het had. Hiermee voorkomt u dat dubbele afbeeldingsrollen in de winkel worden weergegeven.

## Meer als dit

* [Productvisa](../../optimizer/setup/product-visuals.md)
* [Het AEM Assets-project configureren](configure-aem.md)
* [Aangepaste automatische matching](../synchronize/custom-match.md)
* [Overzicht van AEM Assets-integratie](../overview.md)
