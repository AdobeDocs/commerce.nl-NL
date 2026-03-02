---
title: Productvisa voor AEM Assets
description: Leer hoe te om AEM Assets voor productbeelden in  [!DNL Adobe Commerce Optimizer] te gebruiken.
feature: CMS, Media, Configuration, Integration
role: Admin, Developer
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: bf1d88ef7daec25872678bb27bce0bb7c97fd296
workflow-type: tm+mt
source-wordcount: '454'
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

Alvorens de Visuals van het Product toe te laten, zorg u aan de [ eerste vereisten voor Commerce Optimizer ](../../aem-assets-integration/get-started/configure-aco.md#prerequisites) voldoet.

## Instellen

Om de integratie toe te laten, [ creeer een steunkaartje ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) met uw [!DNL Commerce Optimizer] en details van AEM Assets. Adobe Support configureert de integratie en registreert uw huurder bij de Assets Integration Service.

Zie [ AEM Assets voor Commerce Optimizer ](../../aem-assets-integration/get-started/configure-aco.md) voor aan boord komende informatie vormen.

### AEM Assets-metagegevens configureren

Om automatische productmatching toe te laten, vorm uw activa in AEM Assets met de meta-gegevens van Commerce.

Zie [ AEM Assets ](../../aem-assets-integration/get-started/configure-aco.md#configure-aem-assets) voor de vereiste meta-gegevensgebieden en de stappen vormen.

## Productvisa gebruiken

Nadat de integratie is geconfigureerd, kunt u uw productafbeeldingen beheren via AEM Assets.

### Afbeeldingen toevoegen aan producten

1. Upload afbeeldingen naar uw AEM Assets-opslagplaats.

1. Voeg Commerce-metagegevens toe aan het element. Zie [ meta-gegevens op activa ](../../aem-assets-integration/get-started/configure-aco.md#step-3-apply-metadata-to-assets) toepassen.

1. Het middel goedkeuren voor levering. De activa moeten in **goedgekeurde** status zijn om synchronisatie teweeg te brengen.

1. De afbeelding wordt automatisch gesynchroniseerd met [!DNL Commerce Optimizer] .

### De AEM-Assets-laag toepassen

Om AEM Assets beelden op uw storefront te tonen, [ wijs de `AEM-Assets` laag aan uw catalogusmening ](catalog-layer.md#assign-the-aem-assets-layer-to-a-catalog-view) toe.

## Meer als dit

* [Cataloguslagen](catalog-layer.md)
* [Catalogusweergaven](catalog-view.md)
* [AEM Assets Integration Guide](../../aem-assets-integration/overview.md)
