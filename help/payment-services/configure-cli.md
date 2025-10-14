---
title: Configuratie opdrachtregel
description: Na installatie, kunt u  [!DNL Payment Services]  vormen gebruikend de bevel-lijn Interface (CLI).
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
feature: Payments, Checkout, Configuration, Integration, Paas
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."
source-git-commit: 870c2497a2d6dcfc4066c07f20169fc9040ae81a
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Configuratie opdrachtregel

Nadat u [!DNL Payment Services] installeert, kunt u het van [&#x200B; binnen het huis &#x200B;](payments-home.md) of via de bevel-lijn Interface (CLI) gemakkelijk vormen.

## Gegevens exporteren configureren

[!DNL Payment Services] combineert uit [!DNL Magento Open Source] en [!DNL Adobe Commerce] geëxporteerde ordergegevens met samengevoegde betalingsgegevens van betalingsproviders om bruikbare rapporten te maken. De extensie [!DNL Payment Services] gebruikt indexeerders om op efficiënte wijze alle benodigde gegevens voor de rapporten te verzamelen.

Om over de gegevens te leren die in [!DNL Payment Services] rapportering worden gebruikt, zie [&#x200B; het rapport van de betalingsstatus van de Orde &#x200B;](order-payment-status.md#data-used-in-the-report).

### Uitsnede configureren op [!DNL Magento Open Source]

Als u een `BY SCHEDULE` indexmodus wilt gebruiken op [!DNL Magento Open Source] , moet u de uitsnede configureren. Zie [&#x200B; uitsnede &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) vormen en in werking stellen.

### Indexeerders instellen

De gegevens van de orde worden uitgevoerd en in de Betalingsdienst voortgeduurd, gebruikend één van twee indexwijzen— `ON SAVE` (gebrek) of `BY SCHEDULE` (geadviseerd).

De volgende indexen zijn voor [!DNL Payment Services]:

| Code | Naam | Beschrijving |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | Feed verkooporder | Index van ordergegevens samenstellen |
| `sales_order_status_data_exporter` | Statussen verkooporder Feed | Index van statussen van verkooporders samenstellen |
| `store_data_exporter` | Winkelfeed | Index van opslaggegevens samenstellen |

Voer de volgende handelingen uit om de indexmodus voor alle drie de indexen te wijzigen:

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>Als u geen indexeerders in uw bevel specificeert, worden alle indexeerders bijgewerkt aan de zelfde waarde. Als u een specifieke indexeerder wilt veranderen, moet u het in uw bevel een lijst maken.

Meer leren over het manueel veranderen van de wijze van een indexeerder, zie [&#x200B; indexeerders &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/manage-indexers#configure-indexers){target="_blank"} in de ontwikkelaarsdocumentatie vormen. Leren hoe te om het in Admin te veranderen, zie [&#x200B; beheer van de Index &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/index-management#change-the-index-mode){target="_blank"} in de gids van de kerngebruiker.

### Gegevens handmatig opnieuw indexeren

U kunt gegevens handmatig opnieuw indexeren in plaats van te wachten tot dit automatisch gebeurt. Zie [&#x200B; opnieuw indexeren &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/manage-indexers#reindex){target="_blank"} in [&#x200B; de Indexers &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/manage-indexers){target="_blank"} voor meer informatie beheren.

Wanneer de modus `BY SCHEDULE` is ingesteld, worden entiteiten gewijzigd door de systeemtracks en wordt de index voor entiteiten bijgewerkt door de snijtaak op basis van een setschema. Zie [&#x200B; de Bron van de Looppas van de bevellijn &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs#config-cli-cron-group-run) in [&#x200B; vormen en in werking stellen krun &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs)) leren hoe te om indexatie manueel teweeg te brengen gebruikend kroonbanen.

### Geïndexeerde gegevens naar betalingsservice verzenden

Nadat de gegevens zijn geïndexeerd, worden deze automatisch naar [!DNL Payment Services] verzonden. U kunt het proces van het verzenden van geïndexeerde gegevens met dit bevel ook manueel teweegbrengen:

```bash
bin/magento saas:resync --feed [feedName]
```

Gebruik de volgende opdrachtopties:

| Opdracht | Beschrijving |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | Voert een herindexatie van de gespecificeerde voer uit en verzendt het naar de overeenkomstige dienst |
| `bin/magento saas:resync --no-reindex` | Hiermee slaat u de indexering over en verzendt u ongesynchroniseerde gegevens uit de indexen |

Met de parameter `--feed` kunt u opgeven welke feed u wilt verzenden:

| Feed | Beschrijving |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | Voeding voor orders in productiemodus |
| `paymentServicesOrdersSandbox` | Voeding voor bestellingen in de modus Sandbox |
| `paymentServicesOrderStatusesProduction` | Statussen bestellen in productiemodus |
| `paymentServicesOrderStatusesSandbox` | Statussen ordenen in de modus Sandbox |
| `paymentServicesStoresProduction` | Winkels in productiemodus |
| `paymentServicesStoresSandbox` | Opgeslagen bestanden in de modus Sandbox |

Alle gegevens die nodig zijn voor de rapporten worden automatisch naar [!DNL Payment Services] verzonden als de uitsnede is geconfigureerd en geïnstalleerd. U kunt ook handmatig het verzenden van snijgegevens naar [!DNL Payment Services] activeren.

```bash
bin/magento cron:run --group payment_services_data_export
```

Meer over het opnieuw indexeren en indexeerders leren, zie [&#x200B; het indexeerders &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/cli/manage-indexers) onderwerp in de ontwikkelaarsdocumentatie beheren.

## Bereik configureren via CLI

[!DNL Payment Services] staat verkopers toe om [&#x200B; veelvoudige rekeningen te gebruiken PayPal &#x200B;](configure-admin.md#use-multiple-paypal-accounts). Nu, kunt u werkingsgebied voor deze rekeningen via CLI veranderen.

Voer de volgende handelingen uit om het bereik in te stellen op het `website` -niveau:

```bash
bin/magento config:set payment/payment_services/mba_scoping_level website
```

Als u het bereik wilt instellen op het niveau `store` , gebruikt u:

```bash
bin/magento config:set payment/payment_services/mba_scoping_level store
```

>[!TIP]
>
> Neem contact op met uw [!DNL Payment Services] verkoper als u het bereik wilt wijzigen om het niveau op te slaan.

Wanneer u het bereik hebt gewijzigd, wordt de cache leeggemaakt om wijzigingen weer te geven:

```bash
bin/magento cache:clean:payment_services_merchant_scopes
```

## L2/L3-verwerking configureren

[!DNL Payment Services] kan niveau 2- en niveau 3-gegevens van kaartbetalingstransacties verwerken om extra informatie voor handelaren te verschaffen.

>[!WARNING]
>
> De integratie met de verwerking van Niveau 2 en Niveau 3 met PayPal is beschikbaar voor de verkopers van de V.S. slechts. Zie [&#x200B; betalingsverwerking &#x200B;](https://developer.paypal.com/docs/checkout/advanced/processing/){target=_blank} in de documentatie van de Ontwikkelaar van PayPal voor meer informatie.

Als u L2/L3-verwerkingsgegevens wilt gebruiken voor [!DNL Payment Services] of als u vragen hebt, neemt u contact op met uw [!DNL Payment Services] -accountmanager.

Om over L2 en L3 verwerking te leren die in [!DNL Payment Services] wordt gebruikt, zie [&#x200B; Niveau 2 en niveau 3 verwerking &#x200B;](levels-card-payment-transactions.md).
