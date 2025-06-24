---
title: Aan de slag
description: Leer hoe te beginnen met  [!DNL Adobe Commerce Optimizer].
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: f49a86b8793e2d91413acfbc0b922cb94db67362
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 0%

---

# Aan de slag

In dit artikel wordt uitgelegd hoe u snel kunt werken met [!DNL Adobe Commerce Optimizer] . Terwijl deze gids zich op handelaren en beheerderrollen concentreert, omvat het korte taken op hoog niveau die een ontwikkelaar zou uitvoeren. Zie de [ ontwikkelaardocumentatie ](https://developer-stage.adobe.com/commerce/services/composable-catalog/) voor gedetailleerde ontwikkelaar-specifieke inhoud.

## Wat is uw rol?

Bij het instellen van [!DNL Adobe Commerce Optimizer] worden meestal de volgende teamleden betrokken:

- Beheerder
- Ontwikkelaar
- Merchandiser

Elk teamlid heeft zijn eigen set rollen en verantwoordelijkheden zoals beschreven in de volgende tabel:

| Rol/rollen | Taak |
|---|---|
| Beheerder | Met Admin Console kunt u beheerders, gebruikersgroepen, gebruikers en ontwikkelaars &#x200B;. |
|  | Maak een nieuwe [!DNL Adobe Commerce Optimizer] -instantie in Commerce Cloud Manager. &#x200B; |
|  | Stel uw beleid en catalogusweergaven in. |
| Ontwikkelaar | Gebruik Developer Console om een project te maken, ontwikkelaars-API toegang te verlenen en de vereiste toepassingen en aanpassingen te installeren. |
|  | Maak verbinding met uw back office systeem (kar, kassa) met behulp van API Mesh en App Builder &#x200B;. |
|  | Maak een overzicht van de catalogusgegevens van uw bestaande handelsoplossing(en) met behulp van de &#x200B; Gegevensverwerking van de Diensten Merchandising |
|  | Winefront instellen |
| Merchandiser | &#x200B; voor productdetectie instellen. |
|  | Aanbevelingen voor producten instellen. |

Elke rol speelt een integraal onderdeel uit van het succesvol instappen en starten van uw [!DNL Adobe Commerce Optimizer] -omgeving. Het volgende diagram toont een begin op hoog niveau om werkschema voor elke rol in uw organisatie te beëindigen:

![ Werkschema op hoog niveau ](./assets/high-level-workflow.png){zoomable="yes"}

### Beheerder

Beheerders zijn verantwoordelijk voor het instellen van instanties, het beheren van gebruikers, groepen en rechten voor uw organisatie.

- **[heb toegang tot Adobe Admin Console ](https://helpx.adobe.com/enterprise/admin-guide.html)** - beheer Adobe Entitlements over uw volledige organisatie. Zie [ gebruikersbeheer ](./user-management.md) leren hoe u of het product van uw organisatie admin of systeem admin gebruikers aan het [!DNL Adobe Commerce Optimizer] product kunt toevoegen.

- **creeer een instantie** - [!DNL Adobe Commerce Optimizer] instanties gebruiken een op krediet-gebaseerd systeem. U kunt meerdere Sandbox- en Production-instanties maken, waarbij elke instantie één corresponderend krediet nodig heeft. Het bedrag aan kredieten dat u aanvankelijk hebt, is afhankelijk van uw abonnement. [ leer meer ](#create-an-instance).

- **heb toegang tot een instantie** - nadat u een instantie creeert, kunt u tot het van [!UICONTROL Commerce Cloud Manager] toegang hebben. [ leer meer ](#access-an-instance).

- **de catalogusmeningen en het beleid van de Opstelling** - leer hoe te [ uw catalogusmeningen en beleid ](./setup/catalog-view.md) bepalen. De catalogus bevat niet alleen uw productgegevens, maar helpt u ook uw bedrijfsstructuur te definiëren.

### Ontwikkelaar

Ontwikkelaars maken projecten en referenties, installeren extensies, voeren catalogusgegevens in en voeren algemene taken uit op het gebied van platformarchitectuur. Zie de [ ontwikkelaardocumentatie ](https://developer-stage.adobe.com/commerce/services/composable-catalog/) voor gedetailleerde ontwikkelaar-specifieke inhoud.

- **Toegang Developer Console** - heb toegang tot [ Developer Console ](https://developer.adobe.com/developer-console/docs/guides/getting-started) om een project voor [!DNL Adobe Commerce Optimizer] tot stand te brengen, toegangstokens te produceren, en vereiste toepassingen en aanpassingen te installeren.

- **Samenvatting catalogusgegevens** - zie de [ Inname API van Gegevens ](https://developer-stage.adobe.com/commerce/services/composable-catalog/data-ingestion/using-the-api/) documentatie leren hoe u catalogusgegevens in [!DNL Adobe Commerce Optimizer] kunt invoeren.

  De catalogusgegevens die worden opgenomen zijn zichtbaar in de [ pagina van de gegevenssynchronisatie ](./setup/data-sync.md).

- **opstelling de storefront** - alvorens u opstelling de storefront, moet u eerst een instantie tot stand brengen, die een taak typisch door de 2&rbrace; beheerder van uw organisatie [&#128279;](#administrator) wordt uitgevoerd.  Met uw gecreeerde instantie, bent u bereid om met [ vestiging ](./storefront.md) te werk te gaan uw Opslag van Commerce die door Edge Delivery Services wordt aangedreven.

### Merchandiser

De handelaar gebruikt verkoopgegevens en analyses om strategische besluiten over productplaatsing, tarifering, en promoties op de winkel te nemen, terwijl ook het optimaliseren van winkelervaring door productontdekking en aanbevelingen.

- **het productontdekking en aanbevelingen van de Opstelling** - leer hoe te [ gepersonaliseerde ervaringen ](./merchandising/overview.md) voor uw klanten door productontdekking en aanbevelingen creëren.

## Een instantie maken

1. Login aan uw [ Adobe Experience Cloud ](https://experience.adobe.com/) rekening.

1. Onder [!UICONTROL Quick access], klik [!UICONTROL **Commerce**] om [!UICONTROL Commerce Cloud Manager] te openen.

   In [!UICONTROL Commerce Cloud Manager] wordt een lijst weergegeven met [!DNL Adobe Commerce] -instanties die beschikbaar zijn in uw Adobe IMS-organisatie, inclusief beide instanties die zijn ingericht voor [!DNL Adobe Commerce Optimizer] en [!DNL Adobe Commerce as a Cloud Service] .

1. Klik [!UICONTROL **toevoegen Instantie**] in de hoger-juiste hoek van het scherm.

   ![ creeer instantie ](./assets/create-aco-instance.png){width="100%" align="center" zoomable="yes"}

1. Selecteer [!UICONTROL **Commerce Optimizer**].

1. Ga a **Naam** en **Beschrijving** voor uw instantie in.

1. Selecteer het gebied waar u uw instantie wilt ontvangen.

   >[!NOTE]
   >
   >Nadat u een instantie hebt gemaakt, kunt u het gebied niet meer wijzigen.

1. Kies één van het volgende [!UICONTROL **Type van Milieu**] voor uw instantie:

   - [!UICONTROL **Sandbox**] - Ideaal voor ontwerp en testende doeleinden. U moet de [!DNL Adobe Commerce Optimizer] -reis beginnen met de sandboxomgeving.
   - [!UICONTROL **Productie**] - voor levende opslag en klant-onder ogen ziet plaatsen.

   >[!NOTE]
   >
   >Sandbox-exemplaren zijn momenteel beperkt tot de regio Noord-Amerika.

1. Klik [!UICONTROL **toevoegen Instantie**].

   Het nieuwe exemplaar is nu beschikbaar in Cloud Manager.

1. Klik op het informatiepictogram naast de instantienaam om instantiedetails weer te geven, inclusief de eindpunten van de GraphQL- en Catalogusservice, de URL voor toegang tot de Adobe Commerce Optimizer-toepassing en de instantie-id (huurder-id).

   ![ creeer instantie ](./assets/aco-instance-details.png){width="100%" align="center" zoomable="yes"}

## Een instantie openen

1. Login aan uw [ Adobe Experience Cloud ](https://experience.adobe.com/) rekening.

1. Onder [!UICONTROL Quick access], klik [!UICONTROL **Commerce**] om [!UICONTROL Commerce Cloud Manager] te openen.

   In [!UICONTROL Commerce Cloud Manager] wordt een lijst weergegeven met instanties die beschikbaar zijn in uw Adobe IMS-organisatie.

1. Als u de [!UICONTROL Commerce Optimizer] -toepassing wilt openen die aan een instantie is gekoppeld, klikt u op de instantienaam.


