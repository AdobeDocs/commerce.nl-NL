---
title: Gegevens synchroniseren met SaaS-gegevensexport
description: Leer hoe  [!DNL SaaS Data Export]  gegevens tussen de instanties van Adobe Commerce en de verbonden diensten verzamelt en synchroniseert SaaS.
role: Admin, Developer
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Gegevens synchroniseren met SaaS-gegevensexport

Wanneer u een dienst van Commerce installeert die gegevensuitvoer zoals de Dienst van de Catalogus, Levend Onderzoek, of de Aanbevelingen van het Product vereist, wordt een inzameling van de modules van de de gegevensuitvoer van het Saas geïnstalleerd om het gegevensinzameling en synchronisatieproces te beheren.

Bij het exporteren van SaaS-gegevens worden productgegevens doorlopend van een Adobe Commerce-instantie naar het Commerce Services-platform verplaatst om de gegevens up-to-date te houden. Bijvoorbeeld, vereist de Aanbevelingen van het Product huidige catalogusinformatie om aanbevelingen met correcte namen, prijs, en beschikbaarheid nauwkeurig terug te keren. Gebruik het [ dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/data-services/catalog-sync) om het synchronisatieproces waar te nemen en te beheren, of de bevel-lijn interface om een synchronisatie teweeg te brengen en productgegevens voor consumptie door de Diensten van Commerce opnieuw te indexeren.

Het volgende diagram toont de de gegevensuitvoerstroom van SaaS.

![ de gegevensuitvoerinzameling en synchronisatiestroom van SaaS voor Adobe Commerce ](assets/data-export-flow.png){width="900" zoomable="yes"}

De belangrijkste onderdelen van de SaaS-gegevensexportstroom zijn:

- SaaS-gegevensexportmodules die de gegevens voor feeds uit Adobe Commerce verzamelen, items in feed samenstellen, luisteren naar updates en de status van feed behouden.
- De de uitvoermodules van SaaS die gegevens uitvoeren, het verpletteren vormen, en het voer aan de verbonden diensten publiceren.
- De Adobe Commerce Service beheert het gegevensinvoerproces om binnenkomende feeds te valideren en updates van verbonden services te behouden.

## Synchronisatiemodi

De gegevensuitvoer van SaaS heeft twee wijzen om entiteitsvoer te verwerken:

- **Onmiddellijke de uitvoerwijze** - op deze wijze, wordt het gegeven verzameld en onmiddellijk verzonden naar de Dienst van Commerce in één enkele herhaling. Deze modus versnelt de levering van entiteitsupdates aan de Commerce Service en verkleint de opslaggrootte van de voedertabellen.

- **Verouderde de uitvoerwijze** - op deze wijze, wordt het gegeven verzameld in één enkel proces. Dan, verzendt een kroonbaan de verzamelde gegevens naar de verbonden handelsdiensten. In gegevensexportlogitems worden feeds die de oude modus gebruiken, aangeduid met `(legacy)` .

## Synchronisatietypen

SaaS-gegevensexport ondersteunt drie synchronisatietypen: volledige synchronisatie, gedeeltelijke synchronisatie en opnieuw proberen mislukte items te synchroniseren.

### Volledige synchronisatie

Nadat u een Adobe Commerce-instantie hebt verbonden met Commerce Service, voert u een volledige synchronisatie uit om gegevens van de entiteitsfeed van Adobe Commerce naar de verbonden service te verzenden.

>[!NOTE]
>
>Volledige synchronisatie is vooral bedoeld voor de instapfase. Vermijd regelmatig gebruik om databaseoverbelasting te voorkomen. Na de eerste synchronisatie worden doorlopende wijzigingen automatisch gesynchroniseerd met gedeeltelijke synchronisatie.

### Gedeeltelijke synchronisatie

Met gedeeltelijke synchronisatie, verzendt de gegevensuitvoer van SaaS automatisch updates van de toepassing van Commerce, zoals productnaamveranderingen of prijsupdates, naar de verbonden handelsdiensten.

Bij het exporteren van gegevens worden de volgende uitsnijdtaken gebruikt om de gedeeltelijke synchronisatie te automatiseren.

- &quot;index&quot; voor taken van de structuurgroep:
   - De `indexer_reindex_all_invalid` -taak wijzigt alle ongeldige feeds opnieuw. Het is een standaard Adobe Commerce-bouwtaak.
   - De `saas_data_exporter` -taak is bedoeld voor verouderde exportfeeds.
   - De `sales_data_exporter` -taak is specifiek voor de exporteerfeed met verkoopgegevens.

Deze banen lopen elke minuut.

Voor gedeeltelijke synchronisatie is de volgende configuratie vereist voor de Commerce-toepassing:

- [ Taak het plannen wordt toegelaten via cron banen ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html)

- Alle SaaS-indexen voor gegevensexport worden geconfigureerd in de `Update by Schedule` -modus.

  In SaaS-gegevensexportversie 103.1.0 en hoger is de `Update by Schedule` -modus standaard ingeschakeld. U kunt de indexconfiguratie op de server verifiëren met de Commerce CLI-opdracht, `bin/magento indexer:show-mode | grep -i feed`

### Opnieuw Mislukte items synchroniseren

Bij Opnieuw proberen mislukte items synchroniseren wordt een afzonderlijk proces gebruikt om items opnieuw te verzenden die niet konden worden gesynchroniseerd vanwege fouten tijdens het synchronisatieproces, bijvoorbeeld een toepassingsfout, netwerkverstoring of SaaS-servicefout. De implementatie voor deze synchronisatie is ook gebaseerd op uitsnijdtaken.

- `resync_failed_feeds_data_exporter` taken voor de uitsnijdgroep:
   - De `<feed name>_feed_resend_failed_feeds_items` -taak herstelt items die niet konden worden gesynchroniseerd, bijvoorbeeld `products_feed_resend_failed_items` .

### Het synchronisatieproces weergeven en beheren

De meeste synchronisatieactiviteiten worden automatisch verwerkt op basis van de toepassingsconfiguratie. De SaaS-gegevensexport biedt echter ook tools om het proces te beheren.

- De gebruikers Admin kunnen synchronisatievooruitgang bekijken en volgen en informatie over de gegevens van het [ dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) krijgen.

- Ontwikkelaars, systeemintegrators of beheerders met toegang tot de Commerce-toepassingsserver kunnen het synchronisatieproces en de gegevensinvoer beheren met behulp van het opdrachtregelprogramma van Adobe Commerce (CLI). Zie {de Verwijzing van het Bevel van de Uitvoer van 0} Gegevens ](data-export-cli-commands.md).[

### Configuratie Commerce-toepassing controleren

Gedeeltelijke synchronisatie en Opnieuw mislukte items synchroniseren werken alleen als het Commerce-exemplaar correct is geconfigureerd. De configuratie wordt meestal voltooid wanneer u de Commerce Service instelt. Controleer de volgende configuratie als de gegevensexport niet correct werkt.

- [ Bevestig dat de bouwbanen ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues) lopen.

- Verifieer dat de indexen van [ Admin ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) lopen of door het bevel van Commerce CLI te gebruiken `bin/magento indexer:info`.

- Controleer of de indexeerders voor de volgende feeds zijn ingesteld op `Update by Schedule` : Cataloguskenmerken, Product, Productoverschrijvingen en Productvariabele. U kunt de indexen van [ Beheer van de Index ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) in Admin controleren of CLI gebruiken (`bin/magento indexer:show-mode | grep -i feed`).

### Meldingen van gebeurtenismanager voor het registreren van gegevensoverdracht

In versie 103.3.4 en hoger verzendt SaaS Data Export de gebeurtenis `data_sent_outside` wanneer gegevens van de Commerce-instantie naar Adobe Commerce-services worden verzonden.

```php
$this->eventManager->dispatch(
   "data_sent_outside",
   [
       "timestamp" => time(),
       "type" => $metadata->getFeedName(),
       "data" => $data
   ]
);
```

>[!NOTE]
>
>Voor informatie over gebeurtenissen en hoe te om aan hen in te tekenen, zie [ Gebeurtenissen en Waarnemers ](https://developer.adobe.com/commerce/php/development/components/events-and-observers) in de documentatie van de Ontwikkelaar van Adobe Commerce.