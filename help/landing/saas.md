---
title: Commerce Services Connector
description: Leer hoe u uw Adobe Commerce- of Magento Open Source-exemplaar kunt integreren met services met behulp van productie- en sandbox-API-sleutels.
feature: Services, Saas
role: Admin, User
exl-id: 1aa6ba8b-be39-496e-b83d-a4a7db9f5dd8
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce on Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en on-premises projecten."
source-git-commit: be1c739f3821a5f1e846b3026088e3a3ff45a60f
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Sommige Adobe Commerce en Magento Open Source functies worden aangedreven door [!DNL Commerce Services] en geïmplementeerd als SaaS (software as a service). Als u deze services wilt gebruiken, moet u uw [!DNL Commerce] exemplaar verbinden met behulp van productie- en sandbox-API-sleutels en de gegevensruimte in de [configuratie](#saas-configuration) opgeven. U hoeft de verbinding slechts één keer voor elk exemplaar te configureren.

## Beschikbare diensten {#availableservices}

Hieronder vindt u een overzicht van de [!DNL Commerce] functies waartoe u toegang hebt via de [!DNL Commerce Services Connector]:

| Dienst | Beschikbaarheid |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) mogelijk gemaakt door Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) mogelijk gemaakt door Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce en Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/intro) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## Architectuur

Op hoog niveau bestaat het [!DNL Commerce Services Connector] uit de volgende kernelementen:

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
   >*Productie* en *sandbox* verwijzen naar de dataruimte-omgevingen waarin gegevens worden opgeslagen in Adobe SaaS-backendsystemen. Het verwijst niet naar de commerce-omgeving (en) waar u de sleutels gaat gebruiken.

1. Voer een naam in de _sectie API-sleutels_ in en klik op **Nieuwe** toevoegen om het dialoogvenster te openen om de nieuwe sleutel te downloaden.

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
> Als dit zou moeten gebeuren, [ voorlegt een verzoek van de Steun ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/overview) om gegevensschoonmaak te verzoeken.

### SaaS-gegevensruimteprovisioning

Alle Adobe Commerce-merchants hebben toegang tot één productiedataruimte en twee testdataspaces per SaaS-project.

U kunt de het testen gegevensruimten in om het even welke niet productiemilieu gebruiken zolang u niet de zelfde gegevensruimte in veelvoudige milieu&#39;s tezelfdertijd gebruikt. Om de ruimte van testgegevens in een verschillende milieu te gebruiken, voer een gegevensschoonmaakbeurt uit alvorens u selecteert en de gegevensruimte in die milieu vormt.

Voor de Pro projecten van de Wolk van de Handel van Adobe met veelvoudige het opvoeren milieu&#39;s, kunt u extra het testen gegevensruimten voor elk het opvoeren milieu verzoeken door [ een verzoek van de Steun ](https://experienceleague.adobe.com/home?support-tab=home#support) voor te leggen. Als u echter maar één testomgeving hebt en extra testgegevenspaties nodig hebt, hebt u de volgende opties:
- Neem contact op met het team voor succes van de klant of met de door u aangewezen manager voor succes van de klant om een extra testomgeving aan te vragen.
- [ legt een verzoek van de Steun ](https://experienceleague.adobe.com/home?support-tab=home#support) voor om de extra het testen gegevensruimte te verzoeken en op de bedrijfsrechtvaardiging voor het extra datasnelheid te wijzen. Dit verzoek moet worden goedgekeurd.

Magento Open Source-klanten die gebruikmaken van Adobe Payment Services kunnen ook een extra gegevensruimte aanvragen. Neem contact op met het betalingsteam voor voorafgaande goedkeuring van de extra gegevensruimten voordat u een [ondersteuningsverzoek](https://experienceleague.adobe.com/home?support-tab=home#support) indient om de testgegevensruimte aan te vragen.

Klanten die eigenaar zijn van meerdere cloudprojecten of on-premises (live/productie) installaties, kunnen ook extra productie- en testgegevensruimten aanvragen voor elk project of exemplaar door [een ondersteuningsverzoek in](https://experienceleague.adobe.com/home?support-tab=home#support) te dienen.

### Selecteer of maak een SaaS-project {#createsaasenv}

Als u een SaaS-project wilt selecteren of maken, vraagt u de [!DNL Commerce] API-sleutel aan bij de [!DNL Commerce] licentie-eigenaar voor uw winkel:

>[!NOTE]
>
> Als u het **[!UICONTROL Commerce Services Connector]** gedeelte niet in de [!DNL Commerce] configuratie ziet, moet u de modules voor de [!DNL Commerce] gewenste [[!DNL Commerce] service](#availableservices) installeren.

1. Ga in de _zijbalk > Beheerder_ naar **System** Services > **Commerce Services Connector**.

   Als u het **[!UICONTROL Commerce Services Connector]** gedeelte niet ziet in de [!DNL Commerce] configuratie, installeert u de modules voor de [!DNL Commerce] gewenste [[!DNL Commerce] service](#availableservices). Zorg er ook voor dat het `magento/module-services-id` pakket is geïnstalleerd.

1. Plak de belangrijkste waarden in de _[!UICONTROL Sandbox API Keys]_&#x200B;secties en&#x200B;_[!UICONTROL Production API Keys]_ .

   - Privésleutels moeten aan het begin van de sleutel en `----END PRIVATE KEY----` aan het einde van de sleutel worden opgenomen`----BEGIN PRIVATE KEY---`.
   - Als u geen kopie van de daadwerkelijke sleutels heeft, vraagt u de accounteigenaar erom en voert u de waarden vervolgens in de configuratie in.

   >[!WARNING]
   >
   > Als u sleutelwaarden toevoegt door een query uit te voeren op een back-up of momentopname van de database en de waarden in de configuratie te plakken, wordt een extra versleutelingslaag toegepast en werken de sleutels niet.

1. Klik op **Opslaan**.

Alle SaaS-projecten die aan uw sleutels zijn gekoppeld, worden weergegeven in het **veld Project** in de **sectie SaaS-id** .

1. Als er geen SaaS-projecten bestaan, klikt u op **Project** maken. Voer vervolgens in het **veld Project** een naam in voor uw SaaS-project.

>[!NOTE]
>
>Om verwarring te voorkomen, moet u geen specifieke handelsservice gebruiken als naam voor uw project, bijvoorbeeld *Live Zoeken*, *Productaanbevelingen* of *Gegevensverbinding*.  Tenzij uw licentie is ingericht voor meerdere SaaS-projecten, kunt u hetzelfde SaaS-project voor meerdere services gebruiken.

1. Selecteer de **gegevensruimte** die u wilt gebruiken voor de huidige configuratie van uw [!DNL Commerce] winkel.

>[!NOTE]
>
>Als u afzonderlijke exemplaren hebt om te integreren met Commerce Services, [dient u een ondersteuningsticket](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) in om een nieuw SaaS-project aan te vragen voor elk extra exemplaar. Nadat de ondersteuning het SaaS-project heeft gemaakt, configureert u de Commerce Services-integratie voor het exemplaar met behulp van dezelfde API-sleutel en selecteert u het nieuwe SaaS-project voor de gegevensruimte.

>[!WARNING]
>
> Als u nieuwe sleutels genereert in de sectie API-portal van Mijn account, moet u de API-sleutels onmiddellijk bijwerken in de beheerdersconfiguratie. Als je nieuwe sleutels genereert en deze niet bijwerkt in de Admin, werken je SaaS-extensies niet meer en verlies je waardevolle data.

Als u de namen van uw SaaS-project of gegevensruimte wilt wijzigen, klikt u op **Naam wijzigen** naast een van de namen. Het wijzigen van de naam heeft geen invloed op uw service, omdat de naam slechts een label is om u te helpen bij het identificeren en onderscheiden van projecten en gegevensruimten.

## IMS-organisatie (optioneel) {#organizationid}

Als u uw Adobe Commerce-exemplaar wilt verbinden met de Adobe Experience Platform, meldt u zich aan bij uw Adobe-account met uw Adobe ID. Nadat u zich hebt aangemeld, wordt de IMS-organisatie die is gekoppeld aan uw Adobe-account in deze sectie weergegeven.

## SaaS-gegevens exporteren

Wanneer uw [!DNL Commerce] -instantie verbinding heeft gemaakt met [!DNL Commerce Services] , exporteert het SaaS-gegevensexportproces Commerce-gegevens van uw [!DNL Commerce] -server naar [!DNL Commerce SaaS Services] , zodat deze kunnen worden gesynchroniseerd met verbonden Commerce Services. In Admin, kunt u synchronisatiestatus controleren gebruikend het [ dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Voor details, zie de [ Gids van de Uitvoer van Gegevens SaaS ](../data-export/overview.md).
