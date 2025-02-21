---
title: Profielrecordschema bijwerken voor Commerce-gegevensinsluiting
description: Leer hoe u een schema, gegevensset en gegevensstroom maakt voor het verzamelen en verzenden van Commerce-profielrecordgegevens naar de Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%

---

# Profielrecordschema bijwerken voor Commerce-gegevensinsluiting

Wanneer uw klanten een profiel op uw Commerce-site maken, wordt een profielrecord gemaakt en worden gegevens vastgelegd. U moet een schema en een dataset tot stand brengen specifiek voor dat profielverslag alvorens u die profielgegevens aan de Experience Platform kunt stromen.

1. [ creeer ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) een schema en plaats de klasse aan **Individueel Profiel**.

1. [ voeg ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) de volgende profiel-specifieke gebiedsgroepen toe:

   - identityMap
   - Demografische details
   - Persoonlijke contactgegevens
   - Gebruikersaccountgegevens

1. [ laat ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) het schema voor Profiel toe.

   Wanneer een schema voor Profiel wordt toegelaten, nemen om het even welke datasets die van dit schema worden gecreeerd aan Real-Time CDP deel, die gegevens uit ongelijksoortige bronnen samenvoegt om een volledige mening van elke klant te construeren.

1. [ creeer een dataset ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform) die op het schema wordt gebaseerd u creeerde of bijgewerkt.

   Een dataset is een opslag en beheersconstructie voor een inzameling van gegevens, typisch een lijst die een schema (kolommen) en gebieden (rijen) bevat. Datasets bevatten ook metagegevens die verschillende aspecten van de gegevens beschrijven die ze opslaan.

1. Creeer de ruimte van de a [ douanenaam ](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces#create-namespaces) in Experience Platform met de volgende waarden:

   - **Naam van de Vertoning**: _identiteitskaart van de Klant van Commerce_
   - **Symbool van de Identiteit**: _CustomerId_
   - **Type**: _Individuele cross-device identiteitskaart_

   ![ creeer douanenamespace ](assets/custom-namespace.png){width="700" zoomable="yes"}

   Klik op **[!UICONTROL Create]**. Een aangepaste naamruimte wordt door de Unified Profile Service gebruikt om profielfragmenten aan elkaar te koppelen.

Met het schema, de dataset, en de ruimte van de douanenaam die voor het verslaggegeven van het klantenprofiel wordt gevormd, kunt u [ ](connect-data.md#data-collection) uw instantie van Commerce vormen om die gegevens te verzamelen en te verzenden naar Experience Platform.

Om een schema, dataset, en gegevensstroom voor gedrags en achterkantoorgebeurtenisgegevens tot stand te brengen, zie [ de gebeurtenisschema&#39;s van de tijdreeksen van de updatetijd voor de gegevensopname van Commerce ](update-xdm.md).
