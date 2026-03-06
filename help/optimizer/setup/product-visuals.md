---
title: Productvisa voor AEM Assets
description: Leer hoe te om AEM Assets voor productbeelden in  [!DNL Adobe Commerce Optimizer] te gebruiken.
feature: CMS, Media, Configuration, Integration
role: Admin, Developer
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is op Adobe Commerce as a Cloud Service en  [!DNL Adobe Commerce Optimizer]  slechts projecten (Adobe-Beheerde infrastructuur SaaS) van toepassing."
source-git-commit: c7c21df464685783b5fae1c99d60ca91e0c334d2
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---


# Productvisa voor AEM Assets

Met producthandleidingen kunnen [!DNL Adobe Commerce Optimizer] -handelaren productafbeeldingen beheren via Adobe Experience Manager (AEM) Assets. Deze integratie biedt een naadloze workflow voor het synchroniseren van productafbeeldingen van hoge kwaliteit van AEM Assets naar uw [!DNL Commerce Optimizer] -catalogus met cataloguslagen.

## Belangrijkste voordelen

* **Gecentraliseerd activabeheer**: Beheer alle productbeelden in AEM Assets, de onderneming-rang oplossing van het digitale activabeheer.
* **Automatische synchronisatie**: De beelden van het product synchroniseren automatisch wanneer de activa in AEM Assets worden goedgekeurd of bijgewerkt.
* **Dynamische levering van Media**: De Dynamische Media van de hefboomwerking met mogelijkheden OpenAPI voor geoptimaliseerde beeldlevering.
* **de lagen van de Catalogus**: De beelden van het product worden toegepast als cataloguslaag, toestaand u om AEM Assets beelden op uw basiscatalogus te bedekken.

## Hoe werkt het

De integratie heeft twee hoofdstromen:

* **van AEM Assets**: Wanneer een activa wordt goedgekeurd, verworpen of verwijderd, stroomt de gebeurtenis door de Pijpleiding van Adobe aan de Dienst van de Integratie van Assets. De service stemt elementen overeen met producten met behulp van een `match-by-SKU` - of aangepaste matcherstrategie en verzendt vervolgens de `product-asset` toewijzingen naar de [!DNL Commerce Optimizer] -map, waar ze als productlagen worden opgeslagen.

* **van ACO**: Wanneer een product in [!DNL Commerce Optimizer] wordt bijgewerkt, stroomt de gebeurtenisstromen door de Pijpleiding van Adobe aan de Dienst van de Integratie van Assets. De service synchroniseert alle overeenkomstige assettoewijzingen naar ACO.

De bijgewerkte afbeeldingen zijn beschikbaar via de winkel-API&#39;s (Catalog Service, Live Search, Productaanbevelingen).

### Source en laagconfiguratie

Afbeeldingen uit AEM Assets worden opgenomen als een cataloguslaag met de volgende bronconfiguratie:

> Voorbeeld van een bronconfiguratie

```json
{
  "source": {
    "locale": "en-US",
    "layer": "AEM-Assets"
  }
}
```

Deze configuratie zorgt ervoor dat AEM Assets-afbeeldingen worden toegepast als een overlay in uw basisproductcatalogus.

## Vereisten

Alvorens de Visuals van het Product toe te laten, zorg u aan de [&#x200B; eerste vereisten voor Commerce Optimizer &#x200B;](../../aem-assets-integration/get-started/configure-aco.md#prerequisites) voldoet.

## Instellen

Om de integratie toe te laten, [&#x200B; creeer een steunkaartje &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) met uw [!DNL Commerce Optimizer] en details van AEM Assets. Adobe Support configureert de integratie en registreert uw huurder bij de Assets Integration Service.

Zie [&#x200B; AEM Assets voor Commerce Optimizer &#x200B;](../../aem-assets-integration/get-started/configure-aco.md) voor aan boord komende informatie vormen.

### AEM Assets-metagegevens configureren

Om automatische productmatching toe te laten, vorm uw activa in AEM Assets met de meta-gegevens van Commerce.

Zie [&#x200B; AEM Assets &#x200B;](../../aem-assets-integration/get-started/configure-aco.md#configure-aem-assets) voor de vereiste meta-gegevensgebieden en de stappen vormen.

## Productvisa gebruiken

Nadat de integratie is geconfigureerd, kunt u uw productafbeeldingen beheren via AEM Assets.

### Afbeeldingen toevoegen aan producten

1. Upload afbeeldingen naar uw AEM Assets-opslagplaats.

1. Voeg Commerce-metagegevens toe aan het element. Zie [&#x200B; meta-gegevens op activa &#x200B;](../../aem-assets-integration/get-started/configure-aco.md#step-3-apply-metadata-to-assets) toepassen.

1. Het middel goedkeuren voor levering. De activa moeten in **goedgekeurde** status zijn om synchronisatie teweeg te brengen.

1. De afbeelding wordt automatisch gesynchroniseerd met [!DNL Commerce Optimizer] .

### De AEM-Assets-laag toepassen

Om AEM Assets beelden op uw storefront te tonen, [&#x200B; wijs de `AEM-Assets` laag aan uw catalogusmening &#x200B;](catalog-layer.md#assign-the-aem-assets-layer-to-a-catalog-view) toe.

## Meer als dit

* [Cataloguslagen](catalog-layer.md)
* [Catalogusweergaven](catalog-view.md)
* [AEM Assets Integration Guide](../../aem-assets-integration/overview.md)
