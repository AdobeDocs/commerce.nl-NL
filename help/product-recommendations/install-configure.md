---
title: Installeren en configureren
description: Leer om te installeren, bij te werken, en te desinstalleren  [!DNL Product Recommendations].
role: Admin, Developer
exl-id: 2e7f6454-d4cb-44bc-982f-354a179e8e59
source-git-commit: 3821893c3df01e2e36ab0142616e52c1c92b4d51
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Installeren en configureren

Het opstellen van [!DNL Product Recommendations] aan uw opslag en Admin vereist dat u de module installeert en de [ Schakelaar van de Diensten van Commerce ](../landing/saas.md) vormt. Wanneer updates worden uitgebracht, kunt u de installatie eenvoudig bijwerken met de nieuwste versie.

- [Installeren](#install)
- [Configureren](#configure)
- [Bijwerken](#update)
- [Verwijderen](#uninstall)

## Installeren [!DNL Product Recommendations] {#install}

Aangezien de module [!DNL Product Recommendations] een zelfstandig metapakket is, worden updates vaker uitgebracht dan Adobe Commerce. Om ervoor te zorgen u met de recentste insectenmoeilijke situaties en de eigenschappen bijgewerkt bent, verwijs naar de [ versienota&#39;s ](release-notes.md).

>[!IMPORTANT]
>
>Zorg ervoor u de correcte [ rechten ](../landing/saas.md#credentials) hebt om de Aanbevelingen van het Product te gebruiken.

Installeer de module `magento/product-recommendations` met Composer:

```bash
composer require magento/product-recommendations
```

### Ondersteuning voor Page Builder toevoegen {#pbsupport}

[!DNL Product Recommendations] voor Page Builder is een optionele module en wordt apart geïnstalleerd. Als u [!DNL Product Recommendations] wilt gebruiken met Page Builder, installeert u de module met de volgende opdracht:

```bash
composer require magento/module-page-builder-product-recommendations
```

Door [!DNL Product Recommendations] in de Bouwer van de Pagina toe te laten, kunt u een bestaande, actieve [ aanbeveling eenheid ](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) aan om het even welke inhoud toevoegen die in de Bouwer van de Pagina, zoals pagina&#39;s, blokken, en dynamische blokken wordt gecreeerd.

Zie [ Gebruikend  [!DNL Product Recommendations]  met de Inhoud van de Bouwer van de Pagina ](page-builder.md) voor verdere instructies.

### Het aanbevolen type Visuele gelijkenis toevoegen {#vissimsupport}

Het _Visuele gelijkenis_ aanbevelingen type staat u toe om een aanbeveling eenheid aan uw productdetailpagina op te stellen die producten toont die [ visueel gelijkaardig ](type.md#visualsim) aan het product zijn dat wordt bekeken. Dit soort aanbevelingen is vooral handig wanneer afbeeldingen en visuele aspecten van de producten belangrijke onderdelen zijn van de boodschappenervaring. Installeer het _Visuele gelijkenis_ aanbevelingstype door het volgende bevel in werking te stellen:

```bash
composer require magento/module-visual-product-recommendations
```

## Configureren [!DNL Product Recommendations] {#configure}

1. Nadat u de `magento/product-recommendations` module installeert, vorm de [ Schakelaar van de Diensten van Commerce ](../landing/saas.md) door API Sleutels te specificeren en een Ruimte van Gegevens te selecteren SaaS.

   Het vormen van deze verbinding laat de gegevenssynchronisatie en de communicatie tussen de instantie van Commerce, de Dienst van de Catalogus, en andere ondersteunende diensten toe. De synchronisatie van gegevens wordt behandeld door de [ uitbreiding van de Uitvoer van Gegevens SaaS ](../data-export/overview.md).

1. Om ervoor te zorgen dat de catalogusuitvoer correct kan lopen, bevestig dat de [ bebouwde ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) banen en de [ indexeerders ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/manage-indexers) lopen en `Product Feed` indexeerder wordt geplaatst aan `Update by Schedule`.

Nadat u met succes de toepassing van Commerce aan de Diensten van Commerce verbindt en de [ Ruimte van Gegevens SaaS ](../landing/saas.md#saas-configuration) specificeert, begint de catalogussynchronisatie. U kunt [ dan verifiëren ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/verify/) dat het gedragsgegeven wordt verzonden naar uw storefront.

## Gegevenssynchronisatie controleren en problemen oplossen

Van Commerce Admin, kunt u het synchronisatieproces controleren gebruikend het [ Dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Gebruik [ CLI van Commerce ](../data-export/data-export-cli-commands.md#troubleshooting) en logboeken om het proces te beheren en problemen op te lossen.

U kunt [ dan verifiëren ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/verify/) dat het gedragsgegeven wordt verzonden naar uw storefront.

## De installatie van [!DNL Product Recommendations] bijwerken {#update}

Net als in alle Adobe Commerce gebruikt [!DNL Product Recommendations] Composer voor installatie en updates. Voer de volgende handelingen uit om de module `magento/product-recommendations` bij te werken:

```bash
composer update magento/product-recommendations --with-dependencies
```

Als u wilt bijwerken naar een hoofdversie, bijvoorbeeld van 5.0 tot 6.0, moet u het hoofdbestand `composer.json` voor uw project bewerken. (Zie de [ versienota&#39;s ](release-notes.md) voor informatie over de recentste versie.) Laten we bijvoorbeeld het hoofdbestand van `composer.json` openen en zoeken naar de module `magento/product-recommendations` :

```json
"require": {
    ...
    "magento/product-recommendations": "^5.0",
    ...
}
```

Laten we de hoofdversie van `5.0` naar `6.0` verplaatsen:

```json
"require": {
    ...
    "magento/product-recommendations": "^6.0",
    ...
}
```

Sla het `composer.json` -bestand op en voer de bewerking uit:

```bash
composer update magento/product-recommendations --with-dependencies
```

Of als u de modules `magento/module-visual-product-recommendations` en `magento/module-page-builder-product-recommendations` hebt geïnstalleerd:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> In versies 3.x.x van de Aanbevelingen van het Product, had u slechts één enkele sleutel van API nodig. In versies 4.x.x en hoger moet u openbare en persoonlijke API-sleutels opgeven voor zowel de sandbox- als productieomgeving. Als u geen van beide API-sleutels biedt, hebt u geen toegang tot de functie Productaanbevelingen in Admin. De gegevensverzameling gaat echter door op uw winkel en de bestaande aanbevelingen worden nog steeds aan de kopers getoond.

## Firewalls

Voeg `commerce.adobe.io` toe aan de lijst van gewenste personen om productaanbevelingen via een firewall te laten uitvoeren.

## Verwijderen [!DNL Product Recommendations] {#uninstall}

Indien noodzakelijk, kunt u [ de product-aanbevelingen module ](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules) desinstalleren.
