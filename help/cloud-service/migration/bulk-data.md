---
title: Bulk Data Migratietool
description: Leer hoe je de Bulk Data Migration Tool gebruikt om data te migreren van je bestaande Adobe Commerce on Cloud-instantie [!DNL Adobe Commerce as a Cloud Service].
feature: Cloud
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Van toepassing op Adobe Commerce als Cloud Service en alleen Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
role: Developer
level: Intermediate
exl-id: 81522de9-df54-4651-b8ed-58956376af86
source-git-commit: e582ce85b58b57922a8cdd63dbe32bd0f08c64f9
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 0%

---

# Bulk datamigratietool

De bulk datamigratietool volgt een gedistribueerde architectuur die veilige en efficiënte datamigratie van PaaS naar SaaS-omgevingen mogelijk maakt. Deze tool helpt oplossingsimplementeerders om data te migreren van een bestaande Adobe Commerce on Cloud-instantie (PaaS) naar [!DNL Adobe Commerce as a Cloud Service] (SaaS). Voor meer informatie over het migratieproces, zie het overzicht[ van migratie](./overview.md).

>[!NOTE]
>
>De bulk datamigratietool ondersteunt alleen het migreren van eerstepartij kernhandelsgegevens. Aangepaste datamigratie wordt momenteel niet ondersteund.

De volgende afbeelding beschrijft de architectuur en de belangrijkste componenten voor het gebruik van de Bulk datamigratietool.

![Diagram van de architectuur van de Bulk Data Migration Tool dat PaaS naar SaaS dataflow toen.](../assets/bulk-data-diagram.png){zoomable="yes"}

## Migratieworkflow

De workflow voor bulkdatamigratie bestaat uit de volgende stappen:

1. Richt een nieuwe omgeving in voor je migratie.
1. Kopieer je gegevens van je oude systeem.
1. Verplaats je gegevens naar het nieuwe systeem.
1. Maak je productcatalogus beschikbaar in het nieuwe systeem.
1. Bevestig dat je data correct is gemigrerd.

De volgende secties beschrijven deze stappen in detail.

## Toegang tot de bulk datamigratietool

De beschikbaarheid van de bulk datamigratietool is als volgt:

- **Q1 2026** (nog niet beschikbaar) - Na de eerste release van de bulk data migratietool kun je er toegang toe krijgen door een supportticket in te dienen.
- **Q1 2026** (nog niet beschikbaar) - Na de publieke release van de bulk data migratietool zal deze toegankelijk zijn vanaf deze pagina.

## Creëer doelomgeving

De solution implementer (SI) creëert een doelomgeving voor de migratie. Deze omgeving slaat de data op die van de broninstantie is gegenereerd.

Maak eerst [een nieuwe [!DNL Adobe Commerce as a Cloud Service]  (SaaS)instantie](../getting-started.md#create-an-instance).

### Configureer extractietool

Gebruik de extractietool om data uit de broninstantie te halen.

1. Download de extractietool via de link die Adobe je heeft gegeven.
1. Stel de volgende omgevingsvariabelen in in de extractietool:
   - Verbindingsgegevens naar je bestaande MySQL-database
   - De target tenant ID voor jouw [!DNL Adobe Commerce as a Cloud Service] instantie
   - Je IMS-kwalificaties, waaronder:
      - Klant-ID
      - Cliëntgeheim
      - IMS-scopes
      - IMS URL - De basis-URL. Bijvoorbeeld, `https://ims-na1.adobelogin.com/`.
      - IMS-organisatie-ID

   Voor IMS-scopes en andere waarden selecteert u uw OAuth-type in het **gedeelte Credentials** binnen uw project in de [Adobe Developer Console](https://developer.adobe.com/console/). Meer informatie wordt verstrekt in het `.example.env` bestand dat bij de extractietool is geleverd.

### Gegevens extraheren

Voordat de extractietool wordt uitgevoerd, moet de oplossingsimplementator een SSH-tunnel naar de PaaS-database opzetten met behulp van:

```bash
magento-cloud tunnel:open
```

Voer vervolgens het extractiegereedschap uit, dat zal:

1. Maak verbinding met de PaaS-database, analyseer het schema en vergelijk het met de details van de SaaS-tenant-schema.
1. Genereer een extractie- en transformatieplan gebaseerd op de gemeenschappelijke schema-elementen tussen PaaS en SaaS.
1. Haal de gegevens uit met behulp van de Catalog Data Management Service (CDMS).

### Laadgegevens

Voer de load data-tool uit die door Adobe wordt geleverd. Deze tool zal:

1. Maak verbinding met de SaaS-tenantdatabase via een migratieaccount.
1. Maak een laadplan.
1. Voer het plan uit en verplaats data in batches naar de SaaS-tenantdatabase.
1. Verwerk catalogusmedia en breng deze over naar de doelomgeving.
1. Leeg de SaaS Redis-cache en maak database-indexen voor de tenant ongeldig.

### Catalogusgegevensopname

Nadat de data is geladen, stroomt de catalogusgegevens automatisch van de SaaS-tenantdatabase naar de Catalogusdienst.

De Catalogusdienst deelt deze gegevens met Live Search en Product Recommendations. Voor dit proces is geen handmatige interventie nodig. De data is beschikbaar in alle diensten zodra de invoering is voltooid.

### Verificatie van gegevensintegriteit

Na migratie voert CDMS de volgende automatische gegevensintegriteitscontroles uit om de nauwkeurigheid en volledigheid van de gemigreerde data te waarborgen:

**API-gebaseerde verificatie**

Tijdens verificatie vergelijkt CDMS REST- en GraphQL API-antwoorden van eerder uitgevoerde queries met de bijbehorende records van de doelinstantie. Eventuele afwijkingen zijn zichtbaar in de migratiestatus.

**Verificatie op databaseniveau**

Tijdens verificatie telt CDMS het aantal geëxtraheerde records en vergelijkt dat aantal met het aantal geladen records.

**On-demand verificatie (optioneel)**

U kunt ook handmatig een uitgebreide verificatie van alle systeemrecords activeren:

>[!NOTE]
>
>Dit proces is resource-intensief en mag alleen worden gebruikt in sandbox-omgevingen.

De volledige verificatie omvat:

- Volledige API-gebaseerde verificatie met alle vooraf geëxtraheerde REST- en GraphQL API-antwoorden
- Gedetailleerde rapportage van eventuele gevonden inconsistenties
