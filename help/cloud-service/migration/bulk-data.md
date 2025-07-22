---
title: Bulkgegevensmigratie
description: Leer hoe u het Bulk-hulpprogramma voor gegevensmigratie kunt gebruiken om gegevens van uw bestaande Adobe Commerce op Cloud-instantie te migreren naar  [!DNL Adobe Commerce as a Cloud Service] .
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
role: Architect
exl-id: 81522de9-df54-4651-b8ed-58956376af86
source-git-commit: 8bf8eb58aa9c1ae965f4bbf5a2987fb22f004769
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# Bulkgegevensmigratiehulpprogramma

Het hulpmiddel voor bulkgegevensmigratie volgt een gedistribueerde architectuur die veilige en efficiënte gegevensmigratie van PaaS naar SaaS-omgevingen mogelijk maakt. Dit hulpmiddel is ontworpen voor oplossingsimplementators om gegevens van een bestaande Adobe Commerce on Cloud instantie (PaaS) aan [!DNL Adobe Commerce as a Cloud Service] (SaaS) te migreren. Voor meer informatie over het migratieproces, zie het [ overzicht van de Migratie ](./overview.md).

>[!NOTE]
>
>Het hulpmiddel van de bulkgegevensmigratie steunt slechts het migreren van de eerste-partijkern handelsgegevens. Aangepaste gegevensmigratie wordt momenteel niet ondersteund.

In de volgende afbeelding ziet u de architectuur en de belangrijkste componenten voor het gebruik van het gereedschap Bulk voor gegevensmigratie.

![ Bulk de architectuur van het Hulpmiddel van de Migratie van Gegevens ](../assets/bulk-data-diagram.png)

## Migratieworkflow

De workflow voor bulkgegevensmigratie bestaat uit de volgende stappen:

1. Stel een nieuwe omgeving in voor uw migratie.
1. Kopieer uw gegevens van uw oude systeem.
1. Verplaats uw gegevens naar het nieuwe systeem.
1. Maak uw productcatalogus beschikbaar in het nieuwe systeem.
1. Controleer of uw gegevens correct zijn gemigreerd.

In de volgende secties worden deze stappen gedetailleerd beschreven.

## Toegang tot het hulpprogramma voor bulkgegevensmigratie

De beschikbaarheid van het bulkgegevensmigratiehulpmiddel is als volgt:

- **Q3 2025** - om tot het bulkhulpmiddel van de gegevensmigratie toegang te hebben, leg een steunkaartje voor.
- **Q3 2025** - het bulkhulpmiddel van de gegevensmigratie zal openbaar beschikbaar zijn en zal van deze pagina toegankelijk zijn.

## Doelomgeving maken

De oplossingsimplementer (SI) leidt tot een doelmilieu voor de migratie. Deze omgeving wordt gebruikt om de gegevens op te slaan die uit de broninstantie zijn gemigreerd.

Eerst, [ creeer een nieuwe  [!DNL Adobe Commerce as a Cloud Service]  (SaaS) instantie ](../getting-started.md#create-an-instance).

### Extractieprogramma configureren

Het extractiegereedschap wordt gebruikt om gegevens uit de broninstantie te extraheren.

1. Download het extractiegereedschap via de koppeling die u van Adobe hebt ontvangen.
1. Stel de volgende omgevingsvariabelen in het extractiegereedschap in:
   - Verbindingsgegevens met uw bestaande MySQL-database
   - De doel-huurder-id voor uw [!DNL Adobe Commerce as a Cloud Service] -instantie
   - Uw IMS-referenties, waaronder:
      - Client-id
      - Clientgeheim
      - IMS-bereik
      - IMS URL - De basis-URL. Bijvoorbeeld `https://ims-na1.adobelogin.com/` .
      - IMS-organisatie-id

   Voor werkingsgebied IMS en andere waarden, selecteer uw type OAuth in de **sectie van Referenties** binnen uw project in [ Adobe Developer Console ](https://developer.adobe.com/console/). Meer informatie vindt u in het `.example.env` -bestand dat bij het extractiegereedschap wordt geleverd.

### Gegevens extraheren

Alvorens het winningshulpmiddel in werking te stellen, moet de oplossingsimplementator een tunnel van SSH aan het gegevensbestand van PaaS vestigen gebruikend:

```bash
magento-cloud tunnel:open
```

Voer vervolgens het extractiegereedschap uit, dat:

1. Verbind met het gegevensbestand van PaaS, analyseer zijn schema, en vergelijk het met de details van het huurdersschema SaaS.
1. Genereer een extractie- en transformatieplan op basis van de gemeenschappelijke schema-elementen tussen PaaS en SaaS.
1. Haal de gegevens uit de Catalog Data Management Service (CDMS).

### Gegevens laden

Voer het gereedschap voor het laden van gegevens van Adobe uit. Dit gereedschap:

1. Verbind met het huurdersgegevensbestand SaaS gebruikend een migratierekening.
1. Genereer een laadplan.
1. Voer het plan uit, bewegend gegevens naar het huurdersgegevensbestand SaaS in partijen.
1. De catalogusmedia verwerken en deze naar de doelomgeving overbrengen.
1. Voegt het geheime voorgeheugen van SaaS Redis en maakt gegevensbestandindexen voor de huurder ongeldig.

### Gegevens uit catalogus

Nadat de gegevens worden geladen, stromen de catalogusgegevens automatisch van het huurdersgegevensbestand SaaS aan de Dienst van de Catalogus.

De Catalogusservice deelt deze gegevens met Live zoeken en productaanbevelingen. Voor dit proces is geen handmatige interventie vereist. De gegevens zijn beschikbaar in alle services nadat de invoer is voltooid.

### Verificatie van gegevensintegriteit

Na de migratie voert CDMS de volgende automatische controles op de gegevensintegriteit uit om de nauwkeurigheid en volledigheid van de gemigreerde gegevens te waarborgen:

**op API-Gebaseerde controle**

Tijdens verificatie vergelijkt CDMS REST- en GraphQL API-antwoorden van eerder uitgevoerde query&#39;s met corresponderende records van de doelinstantie. Eventuele verschillen zijn zichtbaar in de migratiestatus.

**gegevensbestand-vlakke controle**

Tijdens controle, telt CDMS het aantal gehaalde verslagen en vergelijkt dat aantal met de hoeveelheid geladen verslagen.

**Controle op bestelling (facultatief)**

U kunt ook handmatig een uitgebreide verificatie van alle systeemrecords starten:

>[!NOTE]
>
>Dit proces is hulpbronnenintensief en mag alleen worden gebruikt in sandboxomgevingen.

De volledige verificatie omvat:

- Volledige API-verificatie met alle vooraf uitgenomen REST- en GraphQL API-reacties
- Gedetailleerd verslag van eventuele geconstateerde inconsistenties
