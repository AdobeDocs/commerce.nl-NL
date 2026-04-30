---
title: Adobe Commerce Optimizer Connector
description: Leer hoe u uw gegevens van uw Commerce-cloud of -project op locatie kunt verbinden met Adobe Commerce Optimizer
feature: Personalization, Integration, Configuration
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."
source-git-commit: c9cce4766ef3f30390d50f53237328be1cfeefdf
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 0%

---


# Adobe Commerce Optimizer Connector

De Adobe Commerce Optimizer Connector is een native integratie tussen Adobe Commerce (cloud of op locatie) en Adobe Commerce Optimizer. De catalogus- en prijsgegevens van uw Adobe Commerce-winkels worden gesynchroniseerd naar Commerce Optimizer, zodat u:

- Macht **AI-gedreven productontdekking en aanbevelingen**
- De looppas **krachtige hoofdloze storefronts** (met inbegrip van Commerce storefronts die door Edge Delivery worden aangedreven)
- Analyseer **vóór en na** KPIs en gegeven-sync gezondheid in één enkele plaats

Commerce blijft uw systeem van verslagen voor producten, prijzen, en catalogusstructuur. Commerce Optimizer wordt uw ervarings- en verkooplaag en levert snelle, relevante resultaten op voor elke aangesloten winkel of elk ander verbonden kanaal.

## Belangrijkste voordelen {#key-benefits}

| Voordeel | Wat het voor u betekent |
| --- | --- |
| **Geen douaneschakelaar om te bouwen** | Gebruik een ondersteunde, eersteklas integratie in plaats van op maat gemaakte feeds en scripts te schrijven en te onderhouden. |
| **snellere tijd aan waarde met Commerce Optimizer** | Schakel AI-zoekopdrachten, aanbevelingen en headless storefronts in bovenop de bestaande Adobe Commerce-implementatie. |
| **uitgelijnd met het werkingsgebied van Commerce** | Hiermee worden websites, winkelweergaven en klantgroepen automatisch toegewezen aan catalogusconstructies van Commerce Optimizer (catalogusbronnen en prijsboeken). |
| **Operationeel zicht** | De gezondheid van de voer van de monitor, laatste synchronisatietijden, en per-SKU status van een specifieke mening van de Status van de Synchronisatie van de Diervoeders van Gegevens. |
| **Toekomstig-klaar weg naar SaaS** | Verstrekt een laag-risicomanagementweg van PaaS naar Adobe Commerce as a Cloud Service + Optimizer, zonder herplatform. |

## Connectorarchitectuur {#connector-architecture}

Het volgende diagram illustreert de end-to-end architectuur voor de schakelaar, van Adobe Commerce door Commerce Optimizer en uit aan opslagronts en checkout systemen.

![ Commerce Optimizer Connector de architectuur diagram Commerce van begin tot eind ](./assets/aco-connector-end2end-architecture.png){width="700" zoomable="yes"}

In deze architectuur:

- Adobe Commerce (in wolken of in gebouwen) is het systeem van registratie- en voederproducenten
- De Connector exporteert catalogus, prijs en categoriefeed
- Commerce Optimizer voert en normaliseert de voedergegevens in de Bronnen van de Catalogus, de Boeken van de Prijs, en de Weergaven van de Catalogus in
- Storefronts (Commerce storefront op Edge Delivery of aangepaste headless builds) roepen Commerce Optimizer GraphQL API&#39;s op voor detectie en aanbevelingen en roepen Commerce of een ander verbonden platform van derden op voor winkelwagentjes en afhandelingsbewerkingen

## Hoe de connector werkt met Adobe Commerce {#how-it-works}

- Commerce Optimizer neemt en normaliseert de voedergegevens in de Bronnen van de Catalogus, de Boeken van de Prijs, en de Weergaven van de Catalogus op.

- Storefronts (Commerce storefront op Edge Delivery of aangepaste headless builds) roepen Commerce Optimizer GraphQL API&#39;s op voor detectie en aanbevelingen en roepen Commerce of een ander verbonden platform van derden op voor winkelwagentjes en afhandelingsbewerkingen.

## Hoe de connector werkt met Adobe Commerce

De Adobe Commerce Optimizer Connector werkt door uw bestaande Commerce-bereik (websites en winkelweergaven) en klantsegmentatie te gebruiken om het Commerce Optimizer-catalogusmodel te vullen:

![ het in kaart brengen van de gegevens van Commerce aan Adobe Commerce Optimizer ](/help/aco-connector/assets/storeview-to-catalogview-mapping.png){width="750" zoomable="yes"}

- **de Mening van de Opslag → De Bronnen van de Catalogus** — Elke opslagmening wordt een afzonderlijke Catalogus Source in Commerce Optimizer. Die bron omvat gelokaliseerde productkenmerken en om het even welke opslag-mening-specifieke gegevens
- **Websites → De Boeken van de Prijs** — Elke website van Commerce brengt aan één of meerdere Boeken van de Prijs in Commerce Optimizer in kaart. Prijsstelling voor websites en prijzen voor klantgroepen als prijsboeken en prijsgegevens
- **de groepen van de Klant → De varianten van de Prijs** — de prijsstelling van de de klantengroep van Commerce verschijnt als extra ingangen in de relevante Prijsboeken

Nadat Commerce Optimizer de gegevens heeft ingevoerd, kunt u het volgende configureren:

- **de Weergaven en het Beleid van de Catalogus** in Commerce Optimizer (voor bouwgebied, merk, of klant-specifieke ondergroepen)
- **Ontdekking van het Product** (onderzoek, facetten, handelsregels)
- **Aanbevelingen van het Product**

Wanneer u de connector inschakelt, blijft de Adobe Commerce-instantie het recordsysteem voor catalogus- en prijsgegevens. Wanneer u gegevens bijwerkt in Commerce, synchroniseert de connector deze updates naar de [!DNL Adobe Commerce Optimizer] -instantie.

>[!NOTE]
>
>Voor details bij het vormen van Commerce Optimizer, zie [[!DNL Adobe Commerce Optimizer]  Merchandising hulpmiddelen ](../optimizer/overview.md#quick-tour).

## Typische workflows {#typical-workflows}

In deze workflows wordt beschreven hoe teams de Adobe Commerce Optimizer-connector instellen en gebruiken. Voor details op hoe te opstelling de integratie en deze werkschema&#39;s toelaten, zie [ Begonnen krijgen ](get-started.md).

### Eerste configuratie {#initial-setup}

1. **installeer het schakelaarpakket in Adobe Commerce** gebruikend Composer:

   `composer require adobe-commerce/commerce-data-export-aco-adapter`

1. **vorm authentificatie en omgevingsdetails** in Commerce Admin of via CLI:

   ```terminal
   bin/magento aco:config:init \
     --org_id=<your-org> \
     --tenant_id=<your-tenant> \
     --client_id=<your-client-id> \
     --client_secret=<your-secret> \
     --region=na1 \
     --type=production
   ```

1. {het werkingsgebied van Commerce van 0} Kaart aan Commerce Optimizer:****

   - Bevestig welke websites en winkelweergaven binnen het bereik moeten vallen
   - Zorgen dat klantgroepen en prijsregels zoals verwacht worden gemodelleerd

1. **verifieer connectiviteit:**

   - Voer een testsync uit en bevestig dat de Bron van de Catalogus, de Boeken van de Prijs, en de aanvankelijke producten in Commerce Optimizer verschijnen
   - De statuspagina voor synchronisatie van gegevensfeed in Commerce en de dashboards voor gegevenssynchronisatie in Commerce Optimizer gebruiken voor validatie

### Doorlopende gegevenssynchronisatie {#ongoing-sync}

Na de aanvankelijke configuratie, steunt de schakelaar:

- **Volledige catalogussynchronisatie** voor aanvankelijke migratie of grote structurele veranderingen
- **syncs van Delta** voor aan de gang zijnde updates wanneer de producten of de prijzen veranderen
- **Resync bevelen** voor gerichte voer (met inbegrip van categorieën vanaf v1.0.12):

   - `bin/magento saas:resync --feed=products`
   - `bin/magento saas:resync --feed=prices`
   - `bin/magento saas:resync --feed=categories`

### Verkopen en winkeliers configureren {#merchandising-storefronts}

Nadat Commerce-gegevens beschikbaar zijn in Commerce Optimizer, gebruikt u Commerce Optimizer Studio om merchandising- en winkelervaringen te koppelen aan uw gesynchroniseerde catalogus.

**om handel te vormen en winkelefronts:**

1. **creeer de Mening en het Beleid van de Catalogus** in de Studio van Commerce Optimizer:

   - De catalogus filteren op merk, regio, klantsegment of kanaal
   - Regels voor gegevenstoegang afdwingen per winkel of partner

1. **vorm de Ontdekking en de Aanbevelingen van het Product** in Optimizer UI:

   - Handelswijzigingsregels, facetten, synoniemen en aanbevelingen maken
   - De connector zorgt ervoor dat alle zoek- en aanbevolen configuratie naar Commerce Optimizer wordt verplaatst (Live Search-regels en productaanbevelingen in Commerce Admin zijn niet meer van toepassing op deze stromen)

1. **verbind storefronts** met Commerce Optimizer:

   - Voor een Commerce Storefront die door Edge Delivery Services wordt aangedreven, vorm de storefront om de correcte Optimizer huurder en de Mening van de Catalogus te gebruiken, en onderzoek en aanbeveling eindpunten door de Merchandising API te roepen
   - Voor derdewinkelcentra, gebruik Optimizer openbare APIs of SDKs voor onderzoek en aanbeveling vraag

   >[!NOTE]
   >
   >Voor een voorbeeldderdeintegratie, zie de [ Schakelaar van Salesforce Commerce voor Commerce Optimizer ](../optimizer/developer/salesforce-connector.md).

1. **handhaaf controle** op uw bestaand platform:

   - Winkelwagentje, kassa, orderbeheer en klantenaccounts in Adobe Commerce of een extern platform bewaren
   - App Builder- en API-net gebruiken voor het wegwerken van winkelwagentjes wanneer u integreert met externe uitchecksystemen

## Ondersteunde scenario&#39;s {#supported-scenarios}

De connector is ontworpen voor B2C-handelaren met Adobe Commerce op cloud- en on-premisse implementaties die Commerce Optimizer willen gebruiken zonder hun back-end opnieuw op te bouwen.

**Gemeenschappelijke gebruiksgevallen:**

- **het moderniseren van slechts de storefront**
Behoud uw bestaande Commerce-back-end, verplaats PLP/Search/PDP naar Edge Delivery-winkeliers met Commerce Optimizer

- **Scaling catalogus en onderzoeksprestaties**
Verplaats zware catalogusindexering en zoekopdracht naar de SaaS-services van Commerce Optimizer met behoud van product- en prijseigendom in Commerce

- **Incrementele aanneming van SaaS**
Gebruik de connector als een springplank naar Adobe Commerce as a Cloud Service + Optimizer, met een compatibele, composable Commerce-catalogus

## Verantwoordelijkheden en vereisten voor de uitvoering {#responsibilities-prerequisites}

Commerce is de bron van de waarheid voor producten, prijzen, en klantengroepen. Breng wijzigingen aan in Commerce; de connector synchroniseert ze met Commerce Optimizer.

**Commerce Optimizer is verantwoordelijk voor:**

- Catalogusmodellen (catalogusbronnen, Prijsboeken, Catalogusweergaven, Beleid)
- Productdetectie en aanbevelingen
- De metriek van de opslag, gegevens-synchronisatie dashboards, en de rapporten van de Metriek van het Succes

**de schakelaar doet niet:**

- Commerce-winkelwagentjes, -kassa of -orderstromen wijzigen
- Automatisch opslagprojecten leveren (gereedschapshandgrepen voor Commerce Storefront / Edge Delivery die worden gebruikt)

**alvorens u begint:**

- Controleer of Commerce voldoet aan de minimale vereisten voor versie- en serviceverbinding. Zie [ Begonnen ](get-started.md#prerequisites) voor details krijgen.
- Controleer of u toegang hebt tot IMS org, een [!DNL Adobe Commerce Optimizer] -instantie en de benodigde gegevens en regiogegevens.

## Gerelateerde documentatie {#related-documentation}

- De integratie instellen en sleutelworkflows inschakelen: [ krijgen Begonnen met de Schakelaar van Adobe Commerce Optimizer ](get-started.md)
- Meer informatie over Commerce Optimizer-concepten en -architectuur: [ wat is Adobe Commerce Optimizer?](../optimizer/overview.md)
