---
title: Aan de slag met  [!DNL Adobe Commerce as a Cloud Service]
description: Leer hoe te beginnen met  [!DNL Adobe Commerce as a Cloud Service].
role: Admin, Developer, User
exl-id: 58d98b9e-b41d-44db-9666-c924a5b005b3
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 061b976872fae614cf1fb3db5aaabd9ffdc5e0f9
workflow-type: tm+mt
source-wordcount: '1264'
ht-degree: 0%

---

# Aan de slag

[!DNL Adobe Commerce as a Cloud Service] biedt de meeste configuratie uit het vak. Nadat u een aantal basisinstallatieprocessen hebt voltooid, wordt uw winkel zo snel mogelijk in bedrijf gesteld. Deze gids begeleidt u door het creëren van en het werken met een instantie. Deze handleiding helpt u ook uw organisatie in te stellen voor succes door ervoor te zorgen dat uw teams juiste toegang hebben tot [!DNL Adobe Commerce as a Cloud Service] en de gereedschappen die u nodig hebt om aan de slag te gaan.

[!DNL Adobe Commerce as a Cloud Service] is een &#39;cloud-native&#39; handelsplatform dat flexibiliteit, schaalbaarheid en efficiëntie biedt voor het bieden van ervaringen met digitale handel. Dit SaaS-aanbod is een volledig beheerd, versieloos platform dat een naadloze upgrade biedt zonder dat u handmatig moet ingrijpen.

## Belangrijkste componenten

[!DNL Adobe Commerce as a Cloud Service] bestaat uit de volgende componenten:

* **[Adobe Experience Cloud &#x200B;](https://experience.adobe.com/)** - Uw centraal ingangspunt aan alle [!DNL Adobe Commerce] producten bij [&#x200B; experience.adobe.com &#x200B;](https://experience.adobe.com/)
   * Klik [!UICONTROL **Commerce**] onder [!UICONTROL **Snelle Toegang**] om de Manager van Commerce Cloud te openen
* **[de Manager van Commerce Cloud &#x200B;](https://experience.adobe.com/#/commerce/cloud-service)** - creeer en beheer instanties, toegang API URLs, en uw Admin van Commerce
* **[Adobe Admin Console &#x200B;](https://adminconsole.adobe.com/)** - beheer gebruikers en rollen
* **Admin van Commerce** - beheer producten, orden, klanten, en opslagconfiguratie
* **[Storefront aangedreven door Edge Delivery Services](./storefront.md)** - creeer en pas een klant-onder ogen ziet opslag aan gebruikend een composable, krachtig systeem dat uitzonderlijke snelheid, SEO, en gebruikerservaring voor handelaren en ontwikkelaars levert
* **[Adobe Developer App Builder &#x200B;](https://developer.adobe.com/app-builder/)** - bouw douaneintegratie gebruikend App Builder, samen met andere rekbaarheidshulpmiddelen zoals de [&#x200B; uitrusting van de integratieaanzet &#x200B;](https://developer.adobe.com/commerce/extensibility/starter-kit/integration/) en [&#x200B; API Net &#x200B;](https://developer.adobe.com/graphql-mesh-gateway/)

## Instellen en beheren

Als onderdeel van het installatieproces van [!DNL Adobe Commerce as a Cloud Service] configureren uw systeembeheerder, leveranciers en ontwikkelaars toegang en bronnen voor uw organisatie, inclusief bronnen voor de inrichtingscloud en het toewijzen van gebruikers aan de juiste rollen op basis van hun verantwoordelijkheden.

### Workflow instellen en beheren

Als gecombineerde groep, moeten de systeembeheerder, de handel, en de ontwikkelaar deze essentiële stappen volgen om uw instantie van Commerce in werking te stellen:

1. **Alle Gebruikers**: [&#x200B; creeer een instantie &#x200B;](#create-an-instance)
1. **Beheerder van het Systeem**: [&#x200B; voeg gebruikers toe en wijs rollen &#x200B;](user-management.md#add-users-and-admins) toe
1. **Merchants**: [&#x200B; heb toegang tot Commerce Admin &#x200B;](#access-an-instance) en [&#x200B; voer uw catalogus &#x200B;](#import-your-catalog) in
1. **Ontwikkelaars**: [&#x200B; opstelling uw storefront &#x200B;](storefront.md) en onderzoek het [&#x200B; ontwikkelaarsplatform &#x200B;](overview.md#developer-platform)

#### Workflow AEM Assets en Product Visuals

De volgende stappen zijn vereist om [!DNL Adobe Experience Manager Assets] of [!DNL Product Visuals powered by AEM Assets] met [!DNL Adobe Commerce as a Cloud Service] te integreren:

1. **Beheerder van het Systeem**: [&#x200B; voeg gebruikers aan het het productprofiel van AEM Assets en van het Product Visuals &#x200B;](user-management.md#add-a-user-to-aem-assets-or-product-visuals) toe
1. **Ontwikkelaars**: [&#x200B; integreer AEM Assets en de Visuals van het Product &#x200B;](../aem-assets-integration/overview.md)
1. **Merchants**: [&#x200B; heb toegang tot uw Visuals van AEM Assets en van het Product &#x200B;](./user-management.md#access-the-experience-manager-interface)

### Op rollen gebaseerde installatie- en beheertaken

Selecteer hieronder een tabblad om werkstroomafbeeldingen op hoog niveau voor de bijbehorende rol weer te geven:

>[!BEGINTABS]

>[!TAB  de beheerder van het Systeem en handelsstroom ]

Dit diagram biedt een overzicht op hoog niveau van de manier waarop systeembeheerders en verkopers [!DNL Adobe Commerce as a Cloud Service] -instanties benaderen en beheren. Zie de [&#x200B; Gids van Adobe Admin Console &#x200B;](https://helpx.adobe.com/nl/enterprise/admin-guide.html) voor meer informatie over beheerderwerkschema&#39;s.

![[!DNL Adobe Commerce as a Cloud Service] merchant flow diagram &#x200B;](./assets/merchant-flow.svg){zoomable="yes"}

>[!TAB  werkschema van de Ontwikkelaar ]

Dit diagram biedt een overzicht op hoog niveau van de manier waarop ontwikkelaars integratie maken voor het gebruik van App Builder in [!DNL Adobe Commerce as a Cloud Service] . Zie de [&#x200B; API documentatie &#x200B;](https://developer.adobe.com/commerce/webapi/rest/) voor meer informatie.

![[!DNL Adobe Commerce as a Cloud Service] Stroomdiagram voor ontwikkelaars &#x200B;](./assets/developer-flow.svg){zoomable="yes"}

>[!ENDTABS]

Selecteer uw rol om middelen te vinden om met uw opstellingsproces te beginnen:

>[!BEGINTABS]

>[!TAB  beheerder van het Systeem ]

Als systeembeheerder, bent u verantwoordelijk voor vestiging de organisatie en het beheren van gebruikerstoegang.

| Taak | Beschrijving | Bron |
|------|-------------|----------|
| Het platform begrijpen | Meer informatie over Adobe Commerce as a Cloud Service-architectuur en -voordelen | [&#x200B; Overzicht &#x200B;](overview.md) |
| Functies vergelijken | Begrijp de verschillen tussen Cloud Service en andere aanbiedingen van Adobe Commerce | [&#x200B; vergelijking van de Eigenschap &#x200B;](feature-comparison.md) |
| Een instantie maken | Sandbox- en productieomgevingen instellen | [&#x200B; creeer een geval &#x200B;](#create-an-instance) |
| Gebruikersbeheer instellen | Gebruikers toevoegen, rollen toewijzen en machtigingen beheren | [&#x200B; Gebruikersbeheer &#x200B;](user-management.md) |
| AEM Assets en producthandleidingen instellen (optioneel) | Gebruikers toevoegen, rollen toewijzen en machtigingen beheren | [&#x200B; Gebruikersbeheer &#x200B;](user-management.md#add-a-user-to-aem-assets-or-product-visuals) |

>[!TAB  Merchant ]

Als handelaar, richt u zich op het beheren van producten, orden, en opslag inhoud.

| Taak | Beschrijving | Bron |
|------|-------------|----------|
| Toegang tot uw instantie | Meld u aan bij Commerce Admin om uw winkel te beheren | [&#x200B; heb toegang tot een instantie &#x200B;](#access-an-instance) |
| Gebruiksgevallen verkennen | Meer informatie over praktische zakelijke scenario&#39;s en workflows | [&#x200B; Gevallen van het Gebruik &#x200B;](./use-cases.md) |
| Catalogus importeren | Meer informatie over het importeren van productgegevens naar het platform | [&#x200B; de Invoer uw catalogus &#x200B;](#import-your-catalog) |
| Toegang tot AEM Assets en producthandleidingen (optioneel) | Toegang tot de Experience Manager om AEM Assets en producthandleidingen te gaan gebruiken | [&#x200B; heb toegang tot de interface van de Manager van de Ervaring &#x200B;](./user-management.md#access-the-experience-manager-interface) |


>[!TAB  Ontwikkelaar ]

Als ontwikkelaar moet u weten hoe u aangepaste integratie kunt bouwen en de functionaliteit van het platform kunt uitbreiden.

| Taak | Beschrijving | Bron |
|------|-------------|----------|
| Architectuur begrijpen | Meer informatie over de uitbreidbaarheid en API&#39;s van het platform | [&#x200B; Overzicht - het platform van de Ontwikkelaar &#x200B;](overview.md#developer-platform) |
| Een ontwikkelomgeving instellen | Een sandboxinstantie maken voor ontwikkeling en testen | [&#x200B; creeer een geval &#x200B;](#create-an-instance) |
| Opslagruimte bouwen | Meer informatie over het instellen en aanpassen van de Commerce Storefront | [&#x200B; opstelling Storefront &#x200B;](./storefront.md) |
| Uw winkel configureren | Meer informatie over het instellen van je winkel | [&#x200B; opstelling Storefront &#x200B;](./storefront.md) |
| Verken integratieopties | Meer informatie over App Builder, API Mesh en andere uitbreidbaarheidsgereedschappen waartoe u toegang hebt | [&#x200B; Overzicht - het platform van de Ontwikkelaar &#x200B;](overview.md#developer-platform) |
| AEM Assets en productvisuele producten integreren (optioneel) | Leer hoe u AEM Assets en producthandleidingen kunt integreren met Adobe Commerce | [&#x200B; de integratie van AEM Assets &#x200B;](../aem-assets-integration/overview.md) |

>[!ENDTABS]

### Volgende stappen

Na het voltooien van uw rol-specifieke opstellingstaken:

* **Beheerders van het Systeem**: Herzie [&#x200B; gedeelde verantwoordelijkheid &#x200B;](shared-responsibility.md) richtlijnen
* **Merchants**: Onderzoek [&#x200B; gebruiksgevallen &#x200B;](use-cases.md) voor gemeenschappelijke bedrijfsscenario&#39;s
* **Ontwikkelaars**: Controle uit de [&#x200B; documentatie van de ontwikkelaar van Adobe Commerce &#x200B;](https://developer.adobe.com/commerce/docs)

## Basisbegrippen van Adobe Commerce as a Cloud Service

In de volgende secties worden de basisprocessen beschreven die u moet voltooien om uw Commerce-instantie in bedrijf te stellen.

### Een instantie maken

>[!NOTE]
>
>Voordat u een instantie kunt maken, moet de productbeheerder van uw organisatie of de systeembeheerder u toevoegen als gebruiker van het [!DNL Adobe Commerce as a Cloud Service] -product. Zie [&#x200B; gebruikers en beheerders &#x200B;](./user-management.md#add-users-and-admins) voor meer informatie toevoegen.

[!DNL Adobe Commerce as a Cloud Service] -instanties gebruiken een op krediet gebaseerd systeem. U kunt meerdere instanties maken, maar voor elke instantie zijn beschikbare credits vereist. Het aantal credits dat u aanvankelijk hebt, is afhankelijk van uw abonnement.

1. Login aan uw [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com/) rekening.

1. Onder [!UICONTROL Quick access], klik [!UICONTROL **Commerce**] om [!UICONTROL Commerce Cloud Manager] te openen.

   In [!UICONTROL Commerce Cloud Manager] wordt een lijst weergegeven met [!DNL Adobe Commerce as a Cloud Service] -instanties die beschikbaar zijn in uw Adobe IMS-organisatie.

1. Klik [!UICONTROL **toevoegen Instantie**] in de hoger-juiste hoek van het scherm.

   ![&#x200B; creeer instantie &#x200B;](./assets/create-instance.png){width="50%" align="center" zoomable="yes"}

1. Selecteer [!UICONTROL **Commerce as a Cloud Service**].

1. Ga a **Naam** en **Beschrijving** voor uw instantie in.

1. Kies het [!UICONTROL **Type van Milieu**] voor uw instantie. U kunt kiezen uit de volgende opties:

   * [!UICONTROL **Sandbox**] - Ideaal voor ontwerp en testende doeleinden. U moet de [!DNL Adobe Commerce as a Cloud Service] -reis beginnen met de sandboxomgeving.
   * [!UICONTROL **Productie**] - voor levende opslag en klant-onder ogen ziet plaatsen.

   >[!NOTE]
   >
   >* Sandbox-exemplaren zijn beperkt tot Noord-Amerika.
   >* De optie voor het installeren van voorbeeldgegevens is momenteel niet beschikbaar.

1. Selecteer het gebied waar u uw instantie wilt ontvangen.

   >[!NOTE]
   >
   >Nadat u de instantie hebt gemaakt, kunt u het gebied niet meer wijzigen.

1. Klik [!UICONTROL **toevoegen Instantie**].

### Een instantie openen

Nadat u een instantie hebt gemaakt, kunt u deze openen vanuit de map [!UICONTROL Commerce Cloud Manager] .

1. Login aan uw [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com/) rekening.

1. Onder [!UICONTROL Quick access], klik [!UICONTROL **Commerce**] om [!UICONTROL Commerce Cloud Manager] te openen.

   In [!UICONTROL Commerce Cloud Manager] wordt een lijst weergegeven met instanties die beschikbaar zijn in uw Adobe IMS-organisatie.

1. Als u [!UICONTROL Commerce Admin] voor een instantie wilt openen, klikt u op de instantienaam.

>[!TIP]
>
>Klik op het informatiepictogram naast de instantienaam voor informatie over uw instantie, zoals de REST- en GraphQL-eindpunten en de Admin-URL.

De basis-URL&#39;s voor uw beheerder en eindpunten verschillen afhankelijk van het gebied en de omgeving. Hierbij wordt het volgende patroon gebruikt:

* Beheerder
   * Productiebeheer Noord-Amerika: `https://na1.admin.commerce.adobe.com`
   * Sandbox Admin. Noord-Amerika: `https://na1-sandbox.admin.commerce.adobe.com`
   * Europe production Admin: `https://eu1.admin.commerce.adobe.com`
* REST en GraphQL
   * GraphQL voor productie in Noord-Amerika: `https://na1.api.commerce.adobe.com`
   * Noord-Amerika sandbox GraphQL: `https://na1-sandbox.api.commerce.adobe.com`
   * Europe production GraphQL: `https://eu1.api.commerce.adobe.com`

### Uw catalogus importeren

Standaard bevatten [!DNL Adobe Commerce as a Cloud Service] -instanties geen productgegevens. U kunt voorbeeldproductgegevens opnemen wanneer u een exemplaar maakt voor test- en leerdoeleinden voordat u uw eigen catalogus importeert.

U kunt uw catalogus op twee manieren importeren in [!DNL Adobe Commerce as a Cloud Service] :

* [**Admin van Commerce** &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/import/data-import) - een gebruikersvriendelijke interface die u toestaat om uw catalogusgegevens in een paar kliks in te voeren.
* [**de Invoer JSON API** &#x200B;](https://developer.adobe.com/commerce/webapi/rest/modules/import/#import-json-api) - VERTONEN API die u toestaat om uw catalogusgegevens programmatically in te voeren.

### De storefront instellen

Nu u een instantie hebt gecreeerd, bent u klaar aan [&#x200B; opstelling uw storefront &#x200B;](storefront.md) aangedreven door Edge Delivery Services.

## Aanvullende bronnen

* [Opmerkingen bij de release](release-notes.md)
* [Migratiehandleiding](migration/overview.md)
* [&#x200B; Commerce Storefront documentatie &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/?lang=nl-NL)
