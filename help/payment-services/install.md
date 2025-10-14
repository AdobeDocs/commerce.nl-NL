---
title: Installeren  [!DNL Payment Services]
description: Installeer de uitbreiding van de Diensten van Betalingen.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
role: Admin
feature: Payments, Checkout, Install, Upgrade, Paas
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."
source-git-commit: 5271668c99e7a66fbe857cd3ae26edfa54211621
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Installeren [!DNL Payment Services]

Voer een paar instapstappen uit om te beginnen met het gebruik van Betalingsservices voor [!DNL Adobe Commerce] en [!DNL Magento Open Source] .

>[!INFO]
>
> Zie ons [&#x200B;  [!DNL Payment Services]  voor Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-payment-services) video voor extra informatie vormen.

Het downloaden en installeren van de extensie [!DNL Payment Services] voor [!DNL Adobe Commerce] en [!DNL Magento Open Source] is een eerste vereiste stap voor het gebruik van [!DNL Payment Services] .

## De extensie downloaden

U moet de uitbreiding van [&#x200B; Commerce Marketplace &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html?lang=nl-NL) eerst downloaden alvorens het te installeren.

1. Navigeer aan de [&#x200B; uitbreiding van de Diensten van de Betaling in Commerce Marketplace &#x200B;](https://commercemarketplace.adobe.com/magento-payment-services.html).
1. Als u de editie en versie wilt kiezen, schakelt u **[!UICONTROL Edition]** en **[!UICONTROL Your store version]** in op de gewenste selecties.
1. Klik op **[!UICONTROL Add to Cart]**.
1. Voltooi het uitchecken en klik op **[!UICONTROL Place Order]** .
1. Controleer het e-mailadres dat is gekoppeld aan het downloaden van uw Marketplace voor bevestiging van de bestelling en voor meer informatie.

>[!NOTE]
>
> Voor Adobe Commerce versie 2.4.7 of hoger is [!DNL Payment Services] offline beschikbaar.

## De extensie installeren

U kunt de [!DNL Payment Services] uitbreiding voor zowel [!DNL Adobe Commerce] op wolkeninfrastructuur als op-gebouw instanties installeren, die met uw Commerce rekening [&#x200B; mageid &#x200B;](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) verbonden zijn die in het ondertekeningsproces wordt verstrekt.
[!DNL Magento Open Source] gebruiken de instructies op locatie.

Composer gebruikt deze toetsen tijdens de eerste installatie van [!DNL Adobe Commerce] of in situaties waarin de Composer-toetsen niet eerder in het `auth.json` -bestand zijn opgeslagen.

Zie [&#x200B; uw authentificatietoetsen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) voor meer informatie over het verkrijgen van de sleutels van de Samensteller krijgen.

Zie [&#x200B; installeren een uitbreiding &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/tutorials/extensions) voor meer informatie over wat te overwegen alvorens een uitbreiding te downloaden en te installeren.

### [!DNL Adobe Commerce] op cloudinfrastructuur

Deze methode wordt gebruikt voor het installeren van de extensie [!DNL Payment Services] voor een Commerce Cloud-instantie.

1. Werk uw `composer.json` -bestand bij:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Afhankelijkheden bijwerken en de extensie installeren:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Gebruik de opdracht `composer update` om alle basisafhankelijkheden bij te werken.

1. Leg de wijzigingen vast en duw op deze.

### Op het terrein en in andere configuraties

Deze methode wordt gebruikt voor het installeren van de extensie [!DNL Payment Services] voor een instantie op locatie en klanten van [!DNL Magento Open Source] .

1. Voer de volgende opdrachten uit om de extensie te verkrijgen:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Afhankelijkheden bijwerken en de extensie installeren:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Gebruik de opdracht `composer update` om alle basisafhankelijkheden bij te werken.

1. Upgrade uw exemplaar:

   ```bash
   bin/magento setup:upgrade
   ```

1. Cache wissen:

   ```bash
   bin/magento cache:clean
   ```

1. Wijzigingen vastleggen.
1. Om ervoor te zorgen dat de toegewijde code wordt opgesteld, werk uw instantie bij.

>[!NOTE]
>
> [!DNL Payment Services] 1.6.1 is compatibel met PHP versie 7.x. Het wordt echter ten zeerste aanbevolen om de nieuwste versie van [!DNL Payment Services] te installeren.

## De extensie upgraden

Wanneer een nieuwe versie van [!DNL Payment Services] wordt uitgebracht, kunt u uw uitbreiding gemakkelijk bevorderen.

1. De meest recente versie van het pakket ophalen:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Gebruik de opdracht `composer update` om alle basisafhankelijkheden bij te werken.

1. Voer de volgende handelingen uit nadat de composer is bijgewerkt:

   ```bash
   bin/magento setup:upgrade
   ```

1. Leg de wijzigingen vast en duw op deze.

## Problemen oplossen

Er kunnen fouten optreden wanneer u de extensie [!DNL Payment Services] probeert te installeren. Gebruik de volgende methoden voor het oplossen van problemen om de fouten op te lossen.

### Lijst van gegevensbanken

Controleer of `repo.magento.com` aanwezig is in uw lijst met opslagplaatsen.

### Onjuiste Composer-sleutels

Als de volgende fout aangeeft dat u onjuiste Composer-toetsen hebt:

```
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Controleer of uw Composer-sleutels geldig zijn en of u toegang hebt tot andere Magento-pakketten.

Om te zien welke Composer sleutels worden gevormd:

1. Zoek de locatie van het `auth.json` -bestand:

   ```bash
   composer config --global home
   ```

1. Geef het `auth.json` -bestand weer:

   ```bash
   cat /path/to/auth.json
   ```

1. Zie [&#x200B; welke sleutels met uw rekening van Commerce `MageID` &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) worden geassocieerd.

### Onvoldoende geheugen voor PHP

Als je de volgende foutmelding ziet, heb je onvoldoende geheugen voor PHP:

```
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[&#x200B; verhoog de geheugengrens &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/app/php-settings#increase-php-memory-limit) voor PHP op uw milieu in `php.ini`.

U kunt ook de geheugenlimiet opgeven met deze opdracht: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services` .

Bijvoorbeeld:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
