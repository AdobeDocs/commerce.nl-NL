---
title: Gebeurtenisschema's uit tijdreeks bijwerken voor Commerce-gegevensinsluiting
description: Leer hoe te om een schema, dataset, en gegevensstroom tot stand te brengen om tijdreeksgebeurtenisgegevens voor de gegevensopname van Commerce te verzamelen en te verzenden.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Gebeurtenisschema&#39;s uit tijdreeks bijwerken voor Commerce-gegevensinsluiting

Één van [&#x200B; op het instappen stappen &#x200B;](overview.md#onboarding-steps) voor het gebruiken van de [!DNL Data Connection] uitbreiding moet tot de werkruimte van de gegevensstroom toegang hebben en [&#x200B; creeert een datastream &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=nl-NL) die voor Adobe Commerce specifiek is. Wanneer u die gegevensstroom creeert, moet u ook een schema selecteren dat de gegevens beschrijft u van plan bent in te voeren. Dat schema moet handels-specifieke gebiedsgroepen omvatten.

In dit artikel worden de veldgroepen weergegeven die uw schema moet opnemen om de volgende tijdreeksgegevens van de Adobe Commerce-gebeurtenissen te kunnen verzamelen:

- [&#x200B; Gedrag &#x200B;](events.md) - omvat storefront, profiel, onderzoek, en gebeurtenissen B2B.
- [&#x200B; achterbureau &#x200B;](events-backoffice.md) - omvat ordestatus en profielgebeurtenissen.

Leer meer over [&#x200B; gegevens van de tijdreeksen &#x200B;](data-ingestion.md).

Leer meer over de [&#x200B; grondbeginselen van schemacompositie &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=nl-NL).

## Het schema van de update met het gedrag van de tijdreeks en de gegevens van de achterkantoorgebeurtenis

In deze sectie leert u hoe u uw bestaande schema bijwerkt of een schema maakt om gedrags- en back-office gebeurtenisgegevens op te nemen.

>[!NOTE]
>
>Zie {de gebeurtenisgegevens van het 0} tijdreeksenprofiel [&#128279;](#time-series-profile-event-data) leren hoe te om profiel-specifieke gebieden toe te voegen.

1. Als u reeds geen schema hebt, [&#x200B; creeer &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=nl-NL#create) met de klasse die aan **wordt geplaatst de Gebeurtenis van de Ervaring**.

1. [&#x200B; voeg &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=nl-NL#add-field-groups) de volgende Commerce-Specifieke gebiedsgroepen toe (of geef uw bestaand schema uit en voeg deze gebiedsgroepen toe):

   - Zoeken op site
   - Webpagina bezoeken
   - Aanmeldingsproces gebruiker
   - Referentietoetsen
   - Persoonlijke contactgegevens
   - Kanaaldetails
   - Commerce-gegevens
   - Adobe Analytics ExperienceEvent Commerce (als u gegevens naar Adobe Analytics wilt verzenden)

   >[!NOTE]
   >
   > Stel geen Commerce-specifieke veldgroepen in als `Primary identity` . Hierbij wordt het veld naar wens geïdentificeerd en Experience Platform verwacht dat veld in elke gebeurtenis. Als dat veld ontbreekt, mislukt het invoeren van gegevens.

   Uw schema bevat nu Commerce-Specifieke gebiedsgroepen zodat de gegevens van de tijdreeksen die van Commerce [&#x200B; worden verzameld gedrag &#x200B;](events.md) en [&#x200B; achterbureau &#x200B;](events-backoffice.md) gebeurtenissen in het schema worden vertegenwoordigd.

1. [&#x200B; laat &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=nl-NL#profile) het schema voor Profiel toe.

   Wanneer een schema voor Profiel wordt toegelaten, nemen om het even welke datasets die van dit schema worden gecreeerd aan Real-Time CDP deel, die gegevens uit ongelijksoortige bronnen samenvoegt om een volledige mening van elke klant te construeren.

1. [&#x200B; creeer een dataset &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=nl-NL#create-a-dataset) die van het schema wordt gebaseerd u creeerde of bijgewerkt.

   Een dataset is een opslag en beheersconstructie voor een inzameling van gegevens, typisch een lijst die een schema (kolommen) en gebieden (rijen) bevat. Datasets bevatten ook metagegevens die verschillende aspecten van de gegevens beschrijven die ze opslaan.

1. [&#x200B; creeer een gegevensstroom &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=nl-NL) en selecteer het schema dat de Commerce-Specifieke gebiedsgroepen en de overeenkomstige dataset bevat.

   De gegevensstroom door:sturen de verzamelde gegevens aan de dataset. De gegevens worden vertegenwoordigd in de dataset die op het geselecteerde schema wordt gebaseerd.

Met de schema&#39;s, datasets, en gegevensstromen die voor gedrag en achterbureaugegevens worden gevormd, kunt u [&#128279;](connect-data.md#data-collection) uw instantie van Commerce vormen om die gegevens te verzamelen en te verzenden naar Experience Platform.

Om de het profielinformatie van uw klant te omvatten, zie {de gebeurtenisgegevens van het tijdreeksprofiel van 0} [&#128279;](#time-series-profile-event-data).

## Gebeurtenisgegevens tijdreeksprofiel

De gebeurtenisgegevens van het tijdreeksprofiel worden gegenereerd uit de volgende gebeurtenissen:

- [` accountCreated`](events-backoffice.md#accountcreated)
- [` accountUpdated`](events-backoffice.md#accountupdated)
- [` accountDelette`](events-backoffice.md#accountdeleted)

Als u de profielgebeurtenisgegevens van uw klant in de Experience Platform wilt opnemen, kunt u uw bestaande Commerce-schema bijwerken en dezelfde reeds geconfigureerde gegevensstroom gebruiken, of u kunt een profielspecifieke gegevensstroom en -schema maken. Dat besluit is gebaseerd op het gegevensbeheer van uw bedrijf. De volgende twee secties lopen u door beide gevallen.

### Tijdreeksprofielgebeurtenisgegevens naar Experience Platform verzenden met behulp van uw bestaande gegevensstroom

Als u tijdreeks [&#x200B; server-zijprofielgebeurtenisgegevens &#x200B;](events-backoffice.md#customer-profile-events-server-side) aan uw bestaande gegevensstroom van Commerce wilt toevoegen, voeg de `Demographic Details` gebiedsgroep aan uw schema toe. Uw schema bevat nu de volgende Commerce-specifieke veldgroepen:

- Zoeken op site
- Webpagina bezoeken
- Aanmeldingsproces gebruiker
- Referentietoetsen
- Persoonlijke contactgegevens
- Kanaaldetails
- Commerce-gegevens
- Adobe Analytics ExperienceEvent Commerce (als u gegevens naar Adobe Analytics wilt verzenden)
- Nieuw: **Demografische Details**

Als u de veldgroep `Demographic Details` toevoegt aan uw bestaande Commerce-schema, worden de gegevensset en de gegevensstroom die al aan uw Commerce-schema zijn gekoppeld, gebruikt voor deze tijdreeksprofielgegevens.

### Gegevens van tijdreeksprofielgebeurtenissen naar Experience Platform verzenden in een aparte gegevensstroom

Als u [&#x200B; server-zijprofielgebeurtenisgegevens &#x200B;](events-backoffice.md#customer-profile-events-server-side) aan een nieuwe profiel-specifieke gegevensstroom en schema wilt toevoegen, voltooi de volgende stappen.

1. [&#x200B; creeer &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=nl-NL#create) een schema en plaats de klasse aan **Gebeurtenis van de Ervaring**.

1. [&#x200B; voeg &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=nl-NL#add-field-groups) de volgende profiel-specifieke gebiedsgroepen toe:

   - Demografische details
   - Persoonlijke contactgegevens
   - Kanaaldetails
   - Commerce-gegevens

1. [&#x200B; laat &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=nl-NL#profile) het schema voor Profiel toe.

   Wanneer een schema voor Profiel wordt toegelaten, nemen om het even welke datasets die van dit schema worden gecreeerd aan Real-Time CDP deel, die gegevens uit ongelijksoortige bronnen samenvoegt om een volledige mening van elke klant te construeren.

1. [&#x200B; creeer een dataset &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html?lang=nl-NL#create-a-dataset) die van het schema wordt gebaseerd dat u creeerde.

   Een dataset is een opslag en beheersconstructie voor een inzameling van gegevens, typisch een lijst die een schema (kolommen) en gebieden (rijen) bevat. Datasets bevatten ook metagegevens die verschillende aspecten van de gegevens beschrijven die ze opslaan.

1. [&#x200B; creeer een gegevensstroom &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html?lang=nl-NL) en selecteer het schema XDM dat de Commerce-Specifieke gebiedsgroepen en de overeenkomstige dataset bevat.

   De gegevensstroom door:sturen de verzamelde gegevens aan de dataset. De gegevens worden vertegenwoordigd in de dataset die op het geselecteerde schema wordt gebaseerd.

Met de schema&#39;s, datasets, en gegevensstromen die voor de gegevens van het klantenprofiel worden gevormd, kunt u [&#128279;](connect-data.md#data-collection) uw instantie van Commerce vormen om die gegevens te verzamelen en te verzenden naar Experience Platform.

Om een schema, dataset, en gegevensstroom voor profielverslaggegevens tot stand te brengen, zie [&#x200B; profielrecordgegevens naar Experience Platform &#x200B;](profile-data.md) verzenden.
