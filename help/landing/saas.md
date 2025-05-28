---
title: Commerce Services Connector
description: Leer hoe u uw Adobe Commerce- of Magento Open Source-instantie integreert met productie- en sandbox-API-sleutels.
feature: Services, Saas
role: Admin, User
exl-id: 1aa6ba8b-be39-496e-b83d-a4a7db9f5dd8
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."
source-git-commit: 40423439823d264acf2ece7cf39074b8c931a7c2
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Sommige Adobe Commerce- en Magento Open Source-functies worden aangestuurd door [!DNL Commerce Services] en geïmplementeerd als SaaS (software als service). Om deze diensten te gebruiken, moet u uw [!DNL Commerce] instantie verbinden gebruikend productie en zandbak API sleutels, en de gegevensruimte in de [ configuratie ](#saas-configuration) specificeren. U hoeft de verbinding slechts één keer voor elke instantie te configureren.

## Beschikbare services {#availableservices}

In het volgende voorbeeld worden de [!DNL Commerce] -functies weergegeven waartoe u toegang hebt via [!DNL Commerce Services Connector] :

| Service | Beschikbaarheid |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) aangedreven door Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) aangedreven door Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/guide-overview.md) | Adobe Commerce en Magento Open Source |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## Architectuur

Op hoog niveau bestaat de [!DNL Commerce Services Connector] uit de volgende kernelementen:

![ Architectuur van de Schakelaar van de Diensten van Commerce ](assets/saas-config-sync-workflow.png)

In de volgende secties wordt elk van deze elementen nader besproken.

## Credentials {#apikey}

De productie en zandbak API sleutels worden geproduceerd van de [!DNL Commerce] rekening van de [ vergunningseigenaar ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/start/onboarding). Het Commerce-account wordt geïdentificeerd door een unieke [!DNL Commerce] ID (MageID). De eigenaar van de licentie voor de organisatie van de handelaar kan API-sleutels genereren voor services zoals productaanbevelingen of Live Search, zolang de account zich in goede staat bevindt.

De sleutels kunnen op een &quot;behoefte-aan-weet&quot;basis met het systeemintegrator of ontwikkelingsteam worden gedeeld dat projecten en milieu&#39;s namens de vergunninghouder beheert. Ontwikkelaars die [!DNL Shared Access] hebben gekregen van de eigenaar van de licentie, kunnen de sleutels niet namens hen genereren, zelfs niet als de organisatie van de handelaar aanwezig is in het vervolgkeuzemenu van [!DNL Switch Accounts] .

Daarnaast hebben integrators van oplossingen ook het recht om [!DNL Commerce Services] te gebruiken. Als u een integrator van de oplossing bent, zou de ondertekenaar van het [!DNL Commerce] partnercontract de API sleutels moeten produceren.

>[!NOTE]
>De belangrijkste herkenningstekens *Productie* en *Sandbox* verwijzen niet naar uw milieu. U gebruikt dezelfde set API-sleutels voor elk van uw omgevingen, bijvoorbeeld voor lokale omgevingen, ontwikkelings-, staging- of productieomgevingen.
>
>De eigenaar van de licentie is doorgaans de primaire contactpersoon op de Adobe Commerce-account en is niet altijd dezelfde als de projecteigenaar van de Adobe Commerce voor het infrastructuurproject in de cloud.

### De API-sleutels voor productie en sandbox genereren {#genapikey}

1. Login aan uw [!DNL Commerce] rekening in [ https://account.magento.com ](https://account.magento.com/customer/account/login){:target="_blank"}.

1. Onder het **Magento** lusje, uitgezochte **API Portaal** op sidebar.

1. Van het _Milieu_ menu, uitgezochte **Productie** of **Sandbox**.

   >[!NOTE]
   >
   >*de Productie* en *Sandbox* verwijzen naar de milieu&#39;s van het gegevensgebied waar het gegeven in Adobe SaaS achtergrondsystemen wordt opgeslagen. Het verwijst niet naar de handelsomgeving(en) waar u de sleutels zult gebruiken.

1. Ga een naam in de _API Sleutels_ sectie in, en klik **voeg Nieuw** toe om de dialoog te openen om de nieuwe sleutel te downloaden.

   ![ Download privé sleutel ](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Dit dialoogvenster biedt alleen de mogelijkheid om uw toetsen te kopiëren of te downloaden.

1. Klik **Download** dan klikken **annuleert**.

1. Herhaal bovenstaande stappen voor elke omgeving (productie en sandbox).

   De **API Sleutels** sectie toont nu uw (Openbare) API sleutels. U hebt alle vier sleutels (zowel de productie als zandbaksleutels, Public+Private) nodig wanneer u [ selecteert of een project SaaS ](#createsaasenv) in om het even welke milieu&#39;s of installaties verbonden aan de vergunning creeert.

## SaaS-configuratie {#saasenv}

[!DNL Commerce] -instanties moeten worden geconfigureerd met een SaaS-project en een SaaS-gegevensruimte, zodat [!DNL Commerce Services] gegevens naar de juiste locatie kan verzenden. Een SaaS-project groepeert alle SaaS-gegevensruimten. De SaaS gegevensruimten worden gebruikt om gegevens te verzamelen en op te slaan die [!DNL Commerce Services] toelaat om te werken. Sommige van deze gegevens kunnen worden geëxporteerd uit de [!DNL Commerce] -instantie en sommige kunnen worden verzameld op basis van winkelgedrag in de winkel. Die gegevens blijven vervolgens bewaard om de cloudopslag te beveiligen.

Voor [!DNL Product Recommendations] bevat de SaaS-gegevensruimte catalogus- en gedragsgegevens. U kunt a [!DNL Commerce] instantie aan aSaaS gegevensruimte richten door het [ te selecteren ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) in de [!DNL Commerce] configuratie.

>[!WARNING]
>
> Gebruik uw **gegevens van productieSaaS** slechts op uw productie [!DNL Commerce] installatie om gegevensbotsingen te vermijden. Anders loopt u het risico dat u gegevens van uw productiesite verontreinigt met testgegevens, wat implementatievertragingen veroorzaakt. De gegevens van uw productieproduct kunnen bijvoorbeeld per ongeluk worden overschreven door opvoergegevens, zoals ophalings-URL&#39;s.
> &#x200B;> Als dit zou moeten gebeuren, [ voorlegt een verzoek van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview) om gegevensschoonmaak te verzoeken.

### SaaS-gegevensruimteprovisioning

Alle Adobe Commerce-handelaren hebben per SaaS-project toegang tot één ruimte voor productiegegevens en twee ruimten voor testgegevens.

U kunt de het testen gegevensruimten in om het even welke niet productiemilieu gebruiken zolang u niet de zelfde gegevensruimte in veelvoudige milieu&#39;s tezelfdertijd gebruikt. Om de ruimte van testgegevens in een verschillende milieu te gebruiken, voer een gegevensschoonmaakbeurt uit alvorens u selecteert en de gegevensruimte in die milieu vormt.

Voor de Pro projecten van de Wolk van de Handel van Adobe met veelvoudige het opvoeren milieu&#39;s, kunt u extra het testen gegevensruimten voor elk het opvoeren milieu verzoeken door [ een verzoek van de Steun ](https://experienceleague.adobe.com/home?support-tab=home#support) voor te leggen. Als u echter maar één testomgeving hebt en extra testgegevenspaties nodig hebt, hebt u de volgende opties:

- Neem contact op met het team voor succes van de klant of met de door u aangewezen manager voor succes van de klant om een extra testomgeving aan te vragen.

- [ legt een verzoek van de Steun ](https://experienceleague.adobe.com/home?support-tab=home#support) voor om de extra het testen gegevensruimte te verzoeken en op de bedrijfsrechtvaardiging voor het extra datasnelheid te wijzen. Dit verzoek moet worden goedgekeurd.

Magento Open Source-klanten die Adobe Payment Services gebruiken, kunnen ook om een extra gegevensruimte vragen. Contacteer het team van Betalingen voor vroegere goedkeuring van de extra gegevensruimten alvorens het verzoek van de a [ Steun ](https://experienceleague.adobe.com/home?support-tab=home#support) voor te leggen om de het testen gegevensruimte te verzoeken.

De klanten die veelvoudige projecten van de Wolk of op-gebouw (levend/productie) installaties bezitten kunnen extra productie en het testen gegevensruimten voor elk project of instantie ook verzoeken door [ een verzoek van de Steun ](https://experienceleague.adobe.com/home?support-tab=home#support) voor te leggen.

### Een SaaS-project selecteren of maken {#createsaasenv}

Als u een SaaS-project wilt selecteren of maken, vraagt u de API-sleutel [!DNL Commerce] aan bij de eigenaar van de [!DNL Commerce] -licentie voor uw winkel:

>[!NOTE]
>
> Als u niet de **[!UICONTROL Commerce Services Connector]** sectie in de [!DNL Commerce] configuratie ziet, moet u de [!DNL Commerce] modules voor uw gewenste [[!DNL Commerce]  dienst ](#availableservices) installeren.

1. Op _Admin_ sidebar, ga **Systeem** > de Diensten > **Schakelaar van de Diensten van Commerce**.

   Als u niet de **[!UICONTROL Commerce Services Connector]** sectie in de [!DNL Commerce] configuratie ziet, installeer de [!DNL Commerce] modules voor uw gewenste [[!DNL Commerce]  dienst ](#availableservices). Controleer ook of het pakket `magento/module-services-id` is geïnstalleerd.

1. Plak de hoofdwaarden in de secties _[!UICONTROL Sandbox API Keys]_&#x200B;en&#x200B;_[!UICONTROL Production API Keys]_ .

   - Persoonlijke sleutels moeten `----BEGIN PRIVATE KEY---` aan het begin van de toets en `----END PRIVATE KEY----` aan het einde van de toets bevatten.
   - Als u geen exemplaar van de daadwerkelijke sleutels hebt, vraag de Eigenaar van de Rekening voor hen, dan stop de waarden in de configuratie.

   >[!WARNING]
   >
   > Als u sleutelwaarden toevoegt door een gegevensbestandsteun of een momentopname te vragen en de waarden in de configuratie te kleven, wordt een extra laag van encryptie toegepast, en de sleutels zullen niet werken.

1. Klik **sparen**.

Om het even welke projecten SaaS die met uw sleutels worden geassocieerd verschijnen op het **1&rbrace; gebied van het Project &lbrace;in de** **sectie van het Herkenningsteken SaaS.**

1. Als geen projecten SaaS bestaan, leidt de klik **tot Project**. Dan op het **gebied van het Project**, ga een naam voor uw project SaaS in.

>[!NOTE]
>
>Om verwarring te vermijden, gebruik geen specifieke dienst van Commerce als naam voor uw project, bijvoorbeeld *Levend Onderzoek*, *Aanbevelingen van het Product*, of *Verbinding van Gegevens*.  Tenzij uw vergunning voor veelvoudige projecten SaaS is provisioned, kunt u het zelfde project SaaS voor de veelvoudige diensten gebruiken.

1. Selecteer de **Ruimte van Gegevens** voor de huidige configuratie van uw [!DNL Commerce] opslag te gebruiken.

>[!NOTE]
>
>Als u afzonderlijke instanties hebt om met de Diensten van Commerce te integreren, [ een kaartje van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) voorleggen om een nieuw project SaaS voor elke extra instantie te verzoeken. Nadat de steun het project SaaS heeft gecreeerd, vorm de integratie van de Diensten van Commerce voor de instantie gebruikend de zelfde API sleutel en selecterend het nieuwe project SaaS voor de gegevensruimte.

>[!WARNING]
>
> Als u nieuwe sleutels in de sectie van het Portaal API van Mijn Rekening produceert, werk onmiddellijk de API sleutels in de configuratie Admin bij. Als u nieuwe sleutels produceert en niet hen in Admin bijwerkt, werken uw uitbreidingen SaaS niet meer en u verliest waardevolle gegevens.

Om de namen van uw project SaaS of gegevensruimte te veranderen, klik **anders noemen** naast één van beide. Het veranderen van de naam beïnvloedt niet uw dienst omdat de naam slechts een etiket is om u te helpen tussen projecten en gegevensruimten identificeren en onderscheiden.

## IMS-organisatie (optioneel) {#organizationid}

Als u uw Adobe Commerce-exemplaar wilt verbinden met de Adobe Experience Platform, meldt u zich aan bij uw Adobe-account met uw Adobe ID. Nadat u zich hebt aangemeld, wordt de IMS-organisatie die is gekoppeld aan uw Adobe-account in deze sectie weergegeven.

## SaaS-gegevens exporteren

Wanneer uw [!DNL Commerce] -instantie verbinding heeft gemaakt met [!DNL Commerce Services] , exporteert het SaaS-gegevensexportproces Commerce-gegevens van uw [!DNL Commerce] -server naar [!DNL Commerce SaaS Services] , zodat deze kunnen worden gesynchroniseerd met verbonden Commerce Services. In Admin, kunt u synchronisatiestatus controleren gebruikend het [ dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Voor details, zie de [ Gids van de Uitvoer van Gegevens SaaS ](../data-export/overview.md).
