---
title: Aanvullende informatie
description: De recentste versieinformatie voor  [!DNL Adobe Commerce Optimizer].
role: Admin, Developer, User, Leader
recommendations: noCatalog
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is op Adobe Commerce as a Cloud Service en  [!DNL Adobe Commerce Optimizer]  slechts projecten (Adobe-Beheerde infrastructuur SaaS) van toepassing."
exl-id: e420d461-9ea2-4e32-aa37-230b14a297d7
source-git-commit: a42f6b3348eed476095c6d9777ac9486579fe6ea
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 1%

---

# Aanvullende informatie

De volgende releaseopmerkingen bevatten updates voor [!DNL Adobe Commerce Optimizer] .

## April 2026

**de datum van de Versie**: 7 April, 2026

>[!BEGINSHADEBOX]

### Catalogusregels (bèta)

De regels van de handel drijven omvatten nu [&#x200B; categorieregels &#x200B;](./merchandising/rules/add.md), zodat kunt u één of meerdere categorieën en de orde van het controleproduct op categoriepagina&#39;s richten gebruikend de zelfde intelligente rangschikking en handacties (speld, verhoging, begraving) zoals voor onderzoek.

### Prijsfilter (bèta)

De filters van de aanbeveling steunen nu a [&#x200B; prijsfilter &#x200B;](./merchandising/recommendations/filters.md#price) dat u kunt gebruiken om een minimum en maximumprijswaaier voor producten te plaatsen.

{{aco-release}}

>[!ENDSHADEBOX]

## februari 2026

**de datum van de Versie**: 19 februari, 2026

>[!BEGINSHADEBOX]

### Catalogusweergave voor handelsregels en aanbevelingen (bèta)

Toegevoegde capaciteit om een catalogusmening te specificeren wanneer u [&#x200B; aanbeveling tot eenheden &#x200B;](./merchandising/recommendations/create.md) of [&#x200B; het merchandising regels &#x200B;](./merchandising/rules/add.md) leidt.

{{aco-release}}

>[!ENDSHADEBOX]

## december 2025

**de datum van de Versie**: 10 December, 2025

>[!BEGINSHADEBOX]

### Kansen

De op AI-Gebaseerde aanbevelingen van de plaatsoptimalisering zijn nu beschikbaar door [&#x200B; integratie van Adobe Sites Optimizer &#x200B;](./manage-results/opportunities.md). Met deze functie kunnen handelaren problemen die gevolgen hebben voor de prestaties van de handelsplaats, identificeren en aanpakken via geautomatiseerde detectie en intelligente aanbevelingen.

### Cataloguslagen

Toegevoegde [&#x200B; cataloguslagen &#x200B;](./setup/catalog-layer.md) zodat kunt u productgegevens wijzigen zonder brongegevens, met inbegrip van laag prioritair beheer en integratie met Adobe Sites Optimizer auto-moeilijke situatie eigenschappen te veranderen.

{{aco-release}}

>[!ENDSHADEBOX]

## Oktober 2025

**de datum van de Versie**: 14 Oktober, 2025

>[!BEGINSHADEBOX]

### Commerce Optimizer Salesforce Commerce Connector

[!DNL Commerce Optimizer Salesforce Commerce Connector] is een nieuwe App Builder-integratiestartkit waarmee Commerce-beheerders en -ontwikkelaars Salesforce B2C Commerce-catalogusgegevens naadloos kunnen verbinden met [!DNL Commerce Optimizer] . <!--COMOPT-536-->

**voor Admins:**

* Catalogusupdates in Salesforce (producten, prijzen, metagegevens, prijsboeken) worden automatisch gesynchroniseerd met Commerce Optimizer. Handmatige tussenkomst is niet vereist.
* De integratie werkt onafhankelijk van Adobe Commerce, waardoor de complexiteit en potentiële mislukkingen afnemen.
* Beheerders kunnen gebruikmaken van geplande regelmatige updates om ervoor te zorgen dat de catalogusgegevens in Commerce Optimizer accuraat zijn. Hierdoor wordt het winkelen verbeterd en worden de productaanbevelingen verbeterd.

**voor Ontwikkelaars:**

* De startkit biedt een gestroomlijnd, uitbreidbaar raamwerk voor het opnemen van Salesforce-catalogusgegevens in SaaS Merchandising Services.
* De implementaties van de verwijzing, de ontwerpdocumentatie, en de codesteekproeven zijn beschikbaar om douaneintegratie of het oplossen van problemen te versnellen.<!--COMOPT-536-->

### Gelaagde zoekopdracht

* GA-release voor de volgende geavanceerde zoekmogelijkheden: gelaagd zoeken met `startsWith` en `contains` . [Meer info](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#layered-search-and-expansion-of-search-types).

### Categorieën-API&#39;s

Er is nu een nieuwe REST API voor categorieën beschikbaar, waarmee beheerders en ontwikkelaars programmatisch meerdere categorieconomen voor navigatie en productgroepering kunnen maken, bijwerken en beheren. De API ondersteunt zowel algemene configuraties als kanaalspecifieke configuraties en is ontworpen voor hoge schaalbaarheid, met ondersteuning voor maximaal 10.000 categorieconomen en 500 categorieën per boom. Voor details, zie [&#x200B; Categorieën &#x200B;](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/#categories) in de _Gids van de Ontwikkelaar van de Diensten van de Merchandising_.<!--DCAT-2649-->

{{aco-release}}

>[!ENDSHADEBOX]

## augustus 2025

**de datum van de Versie**: 28 augustus, 2025

>[!BEGINSHADEBOX]

### EU-regio nu beschikbaar

Ondersteuning voor de regio van de Europese Unie (eu1) voor IMS-organisaties van klanten is nu beschikbaar. U kunt **Europese Unie** nu selecteren als a **Gebied** wanneer [&#x200B; toevoegend een instantie van Commerce Optimizer &#x200B;](./get-started.md#step-1-create-an-instance) in Cloud Manager. De regio van de Europese Unie is alleen beschikbaar voor productieomgevingen.

De basis-productie-URL&#39;s voor de regio van de Europese Unie zijn:

* Admin: `https://eu1.admin.commerce.adobe.com`
* REST en GraphQL: `https://eu1.api.commerce.adobe.com`

![&#x200B; creeer instantie &#x200B;](./assets/create-instance.png){width="600" align="center" zoomable="yes"}

{{aco-release}}

>[!ENDSHADEBOX]
