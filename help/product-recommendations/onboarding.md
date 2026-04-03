---
title: Onboarding
description: Leer de vereisten en de gesteunde platforms in  [!DNL Product Recommendations].
exl-id: 7b8a1117-b6d5-4e5d-bb97-09f76a024cbd
source-git-commit: 8f421bd4421b9599ad52aa68c5caaee6592ccb43
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# Onboarding

>[!IMPORTANT]
>
>**de Aanbevelingen van het Product is geen HIPAA-Klaar dienst.** Schakel de productaanbevelingen niet in en gebruik ze niet in Adobe Commerce-implementaties die gebruikmaken van het HIPAA-bestand dat beschermde gezondheidsinformatie (PHI) aanbiedt of anderszins verwerkt. De Aanbevelingen van het product maken deel uit van de diensten van Commerce SaaS die momenteel als niet-HIPAA klaar worden geclassificeerd.
>
>Voor details over welke mogelijkheden van Adobe Commerce HIPAA klaar zijn en welke diensten niet met PHI moeten worden gebruikt, zie [&#x200B; bereidheid van HIPAA op Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) en [&#x200B; Verrichtingen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/compliance/hipaa-ready-service/operations#adobe-commerce-services).

Het instapproces voor [!DNL Product Recommendations] vereist toegang tot de opdrachtregel van de server en bestaat uit de volgende stappen. Als u niet bekend bent met het werken vanaf de opdrachtregel, vraagt u een ontwikkelaar of systeemintegrator om hulp.

- [Implementatieworkflow](implementation-workflow.md)
- [Installeren en configureren](install-configure.md)
- [Instellingen](settings.md)
- [&#x200B; verifieer &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/verify/)
- [Stationele omgeving](staging-environment.md)

## Vereisten

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2, 8.3 of 8.4
- Composer 2

### Ondersteunde platforms

- Adobe Commerce on premise (EE) : 2.4.4+
- Adobe Commerce on Cloud (ECE) : 2.4.4+

## Endpoint

[!DNL Product Recommendations] communiceert via het eindpunt op `https://catalog-service.adobe.io/graphql` .

### Ondersteuning voor Page Builder

[!DNL Product Recommendations] kan aan een pagina worden toegevoegd als een inhoudstype van de Bouwer van de Pagina. Om de steun van de Bouwer van de Pagina aan de Aanbevelingen van het Product toe te voegen, verwijs naar [&#x200B; installeer en vorm &#x200B;](install-configure.md).

Zie [[!DNL Page Builder]  Integratie &#x200B;](page-builder.md) voor instructies op hoe te om [!DNL Product Recommendations] in [!DNL Page Builder] inhoud toe te voegen.

### Prijsindexering SaaS

De klanten van de Aanbeveling van het product kunnen [&#x200B; Prijs gebruiken SaaS indexerend &#x200B;](../price-index/price-indexing.md), die snellere prijsveranderingen updates en synchronisatietijd verstrekt.

### B2B-ondersteuning {#b2bsupport}

B2B-winkels vereisen vaak complexe logica die de zichtbaarheid en prijsstelling van het product voor elke winkel of klantengroep bepaalt. [!DNL Product Recommendations] nu [&#x200B; steun &#x200B;](release-notes.md) deze functionaliteit door [&#x200B; categorietoestemmingen &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html?lang=nl-NL), [&#x200B; gedeelde catalogi &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html?lang=nl-NL), en [&#x200B; klant groep-specifieke tarifering &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html?lang=nl-NL) te ontvangen. Bijvoorbeeld, als u bepaalde categorieën van uw retailklantensegment hebt verborgen, dan zou een verkoopster in dat segment geen aanbevelingen voor producten in die categorieën worden getoond. Ook, wanneer u een gedeelde catalogus voor specifieke klantengroepen en bedrijven bepaalt, zien die kopers aanbevelingen slechts voor producten zij kunnen toegang hebben. Alle geadviseerde producten weerspiegelen correcte klant groep-specifieke prijs die op de klantengroep van elke klant wordt gebaseerd.

>[!NOTE]
>
>De handelaars kunnen widgets of storefront elementen aanpassen en uitbreiden door de [&#x200B; Storefront API van de Dienst van de Catalogus te gebruiken &#x200B;](../catalog-service/overview.md) maar om het even welke aanpassing is buiten werkingsgebied voor het ondersteuningsteam van Adobe.
