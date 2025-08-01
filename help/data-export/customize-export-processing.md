---
title: De exportprestaties van SaaS-gegevens verbeteren
description: Leer hoe te om de prestaties van de gegevensuitvoer van SaaS voor de Diensten van Commerce te verbeteren door de multi-thread wijze van de gegevensuitvoer te gebruiken.
role: Admin, Developer
exl-id: 7151118c-5e30-44d0-b515-5801a73e44ec
source-git-commit: b8b7af1119163589b7d83654b13edae656fea339
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# De exportprestaties van SaaS-gegevens verbeteren

**Multithread gegevens de uitvoerwijze** versnelt het uitvoerproces door voedergegevens in partijen te verdelen en hen parallel te verwerken.

De ontwikkelaars of systeemintegrators kunnen prestaties verbeteren door de multi-draadgegevens te gebruiken uitvoeren wijze in plaats van de standaard single-thread wijze. In single-thread wijze, is er geen parallellisatie van het proces van de voedervoorlegging. Bovendien, wegens de vastgestelde standaardgrenzen, zijn alle cliënten beperkt tot het gebruiken van slechts één draad. In de meeste gevallen is het niet nodig de configuratie aan te passen.

## Overwegingen voor het gebruiken van multi-draadwijze

Wanneer u werkt met services voor het exporteren van gegevens, wilt u de prestaties optimaliseren en een nauwkeurige synchronisatie garanderen.
Adobe raadt aan de standaardconfiguratie voor gegevensinvoer te gebruiken, die doorgaans voldoet aan de synchronisatievereisten voor Commerce-handelaren. Er zijn echter scenario&#39;s waarin aanpassing de verwerkingstijd kan versnellen.

Houd rekening met de volgende belangrijke factoren wanneer u besluit of u de configuratie voor het exporteren van gegevens wilt aanpassen:

- **Aanvankelijke Synchronisatie** - evalueert het aantal producten en [ schat het gegevensvolume en de transmissietijd ](estimate-data-volume-sync-time.md) die op de standaardconfiguratie wordt gebaseerd. Vraag uzelf: Kan u wachten op deze eerste gegevenssynchronisatie na het instappen van een Commerce-service?

- **Toevoegend de Nieuwe Mening van de Opslag of Websites** - als u van plan bent om opslagmeningen of websites met de zelfde producttelling toe te voegen na het gaan levende, schat het gegevensvolume en transmissietijd. Bepaal of de synchronisatietijd met de standaardconfiguratie aanvaardbaar is of als multi-draadverwerking noodzakelijk is.

- **Reguliere Invoer** - Anticipate regelmatige invoer, zoals prijsupdates of veranderingen van de voorraadstatus. Bepaal of deze updates binnen een aanvaardbare tijd kunnen worden toegepast of als snellere verwerking nodig is.

- **Gewicht van het Product** - overweeg of uw producten lichtgewichtof zwaar zijn. Pas de grootte van de batch aan als de productbeschrijving of -kenmerken de productgrootte opblazen.

Herinner dat de doordachte planning, met inbegrip van het schatten van gegevensvolume en synchronisatietijd, vaak de behoefte aan aanpassing kan elimineren. Plan op basis van deze schattingen de inname van diervoeders om optimale resultaten te bereiken.

>[!NOTE]
>
>Adobe raadt u aan voorzichtig te zijn wanneer u multithread-verwerking gebruikt. Als u multi-threading configureert voor snellere prestaties, kunt u de meegeleverde Adobe Commerce Services-instructies activeren om misbruik van het systeem tijdens het invoeren van gegevens te voorkomen. Deze instructies beperken gebruikers ook van het activeren van synchronisatiewijzigingen die het systeem kunnen overladen. Wanneer de instructies worden geactiveerd, worden aanvragen geblokkeerd en retourneert het systeem 429 fouten. Als u deze fouten ontmoet, pas uw configuratie aan, en voorleg een steunkaartje voor hulp.

## Multithreading configureren

De multithread wijze wordt gesteund voor al [ synchronisatiemethodes ](data-synchronization.md#synchronization-process) - volledige synchronisatie, gedeeltelijke synchronisatie, en ontbroken puntensynchronisatie. Om multi-threading te vormen, specificeert u het aantal draden en partijgrootte om tijdens synchronisatie te gebruiken.

- `thread-count` is het aantal threads dat is geactiveerd om entiteiten te verwerken. De standaardwaarde `thread-count` is `1` .
- `batch-size` is het aantal entiteiten dat in één herhaling wordt verwerkt. De standaardwaarde `batch-size` is `100` records voor alle feeds behalve de prijsfeed. De standaardwaarde voor de prijsfeed is `500` records.

U kunt multi-threading als tijdelijke optie vormen wanneer het runnen van een resync bevel, of door de multi-draadconfiguratie aan de de toepassingsconfiguratie van Adobe Commerce toe te voegen.

>[!NOTE]
>
>Zorg ervoor dat u de prestaties van SaaS-gegevensexport aanpast aan de tarieflimiet die voor een client aan de zijde van de consument is gedefinieerd.

### Multithreading tijdens runtime configureren

Wanneer u een volledige synchronisatieopdracht uitvoert vanaf de opdrachtregel, geeft u de verwerking met meerdere verbindingen op door de opties `thread-count` en `batch-size` toe te voegen aan de CLI-opdracht.

```
bin/magento saas:resync --feed=products --thread-count=2 --batch-size=200
```

De opties op de opdrachtregel overschrijven de configuratie voor gegevensexport die is opgegeven in het Adobe Commerce-toepassingsbestand `config.php` .

### Multithread toevoegen aan de Commerce-configuratie

Als u alle bewerkingen voor het exporteren van gegevens wilt verwerken met multithreading, kunnen systeemintegrators of ontwikkelaars het aantal threads en de batch-grootte voor elke feed in de Commerce-toepassingsconfiguratie wijzigen.

Deze veranderingen kunnen worden toegepast door douanewaarden aan de [ systeemsectie ](https://experienceleague.adobe.com/nl/docs/commerce-operations/configuration-guide/files/config-reference-configphp#system) van het configuratiedossier toe te voegen, `app/etc/config.php`.

**Voorbeeld: Het vormen multithreading voor producten en prijzen**

```php
<?php
return [
    'system' => [
        'default' => [
            'commerce_data_export' => [
                'feeds' => [
                    'products' => [
                        'batch_size' => 100,
                        'thread_count' => 2,
                    ],
                    'prices' => [
                        'batch_size' => 400,
                        'thread_count' => 4,
                    ]
                ]
            ],
//   ...
```
