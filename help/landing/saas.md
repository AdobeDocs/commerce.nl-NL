---
title: Commerce Services Connector
description: Leer hoe u uw Adobe Commerce- of Magento Open Source-instantie integreert met productie- en sandbox-API-sleutels.
feature: Services, Saas
role: Admin, User
exl-id: 1aa6ba8b-be39-496e-b83d-a4a7db9f5dd8
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."
source-git-commit: 6e107238b8eae31f35f43524aee5690c0fe0e03d
workflow-type: tm+mt
source-wordcount: '1564'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Sommige Adobe Commerce- en Magento Open Source-functies worden aangestuurd door [!DNL Commerce Services] en geïmplementeerd als SaaS (software als service). Om deze diensten te gebruiken, moet u uw [!DNL Commerce] instantie verbinden gebruikend productie en zandbak API sleutels, en de gegevensruimte in de [&#x200B; configuratie &#x200B;](#saas-configuration) specificeren. U hoeft de verbinding slechts één keer voor elke instantie te configureren.

Alleen de eigenaar van de [!DNL Commerce] -licentie kan deze API-sleutels genereren. Als u niet de eigenaar van de licentie bent, vraagt u de sleutels aan bij de persoon of het team die de Commerce-licentie voor uw winkel heeft.

## Beschikbare services {#availableservices}

In het volgende voorbeeld worden de [!DNL Commerce] -functies weergegeven waartoe u toegang hebt via [!DNL Commerce Services Connector] :

| Service | Beschikbaarheid |
| --- | --- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) aangedreven door Adobe AI | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) aangedreven door Adobe AI | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/guide-overview.md) | Adobe Commerce en Magento Open Source |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## Architectuur

Op hoog niveau bestaat de [!DNL Commerce Services Connector] uit de volgende kernelementen:

![&#x200B; Architectuur van de Schakelaar van de Diensten van Commerce &#x200B;](assets/saas-config-sync-workflow.png)

In de volgende secties wordt elk van deze elementen nader besproken.

## Credentials {#apikey}

De productie en zandbak API sleutels worden geproduceerd van de [!DNL Commerce] rekening van de [&#x200B; vergunningseigenaar &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/start/onboarding). Het Commerce-account wordt geïdentificeerd door een unieke [!DNL Commerce] ID (MageID). De eigenaar van de licentie voor de organisatie van de handelaar kan API-sleutels genereren voor services zoals productaanbevelingen of Live Search, zolang de account zich in goede staat bevindt.

De sleutels kunnen op een &quot;behoefte-aan-weet&quot;basis met het systeemintegrator of ontwikkelingsteam worden gedeeld dat projecten en milieu&#39;s namens de vergunninghouder beheert. Ontwikkelaars die [!DNL Shared Access] door de eigenaar van de licentie hebben gekregen, kunnen de sleutels niet namens de eigenaar van de licentie genereren, zelfs niet als de organisatie van de handelaar aanwezig is in het vervolgkeuzemenu van [!DNL Switch Accounts] voor hun account.

Daarnaast kunnen integrators van oplossingen [!DNL Commerce Services] gebruiken. Als u een integrator van de oplossing bent, zou de ondertekenaar van het [!DNL Commerce] partnercontract de API sleutels moeten produceren.

De belangrijkste herkenningstekens *Productie* en *Sandbox* verwijzen naar milieu&#39;s van het gegevensgebied SaaS waar [!DNL Commerce Services] gegevens (niet aan uw milieu&#39;s van Adobe Commerce) opslaat. U kunt dezelfde set API-sleutels gebruiken voor uw lokale, ontwikkelings-, staging- en productieomgeving. Het belangrijkste is dat u het juiste sleutelpaar plakt voor de gegevensruimte die u configureert.

De eigenaar van de licentie is doorgaans de primaire contactpersoon op de Adobe Commerce-account en is niet altijd dezelfde als de projecteigenaar van de Adobe Commerce voor het infrastructuurproject in de cloud.

### De API-sleutels voor productie en sandbox genereren {#genapikey}

1. Login aan uw [!DNL Commerce] rekening in [&#x200B; https://account.magento.com &#x200B;](https://account.magento.com/customer/account/login){:target="_blank"}.

1. Onder het **Magento** lusje, uitgezochte **API Portaal** op sidebar.

1. Van het _Milieu_ menu, uitgezochte **Productie** of **Sandbox**.

1. Ga een naam in de _API Sleutels_ sectie in, en klik **voeg Nieuw** toe om de dialoog te openen om de nieuwe sleutel te downloaden.

   ![&#x200B; Download privé sleutel &#x200B;](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > U kunt de persoonlijke sleutel slechts eenmaal kopiëren of downloaden. Bewaar deze veilig.

1. Klik **Download** om de privé sleutel te bewaren, dan de dialoog te sluiten.

1. Herhaal bovenstaande stappen voor elke omgeving (productie en sandbox).

   De **API Sleutels** sectie toont nu uw (Openbare) API sleutels. U hebt alle vier sleutels (zowel de productie als zandbaksleutels, Public+Private) nodig wanneer u [&#x200B; selecteert of een project SaaS &#x200B;](#createsaasenv) in om het even welke milieu&#39;s of installaties verbonden aan de vergunning creeert.

## SaaS-configuratie {#saasenv}

[!DNL Commerce] -instanties moeten worden geconfigureerd met een SaaS-project en een SaaS-gegevensruimte, zodat [!DNL Commerce Services] gegevens naar de juiste locatie kan verzenden. Een SaaS-project groepeert alle SaaS-gegevensruimten. De SaaS gegevensruimten worden gebruikt om gegevens te verzamelen en op te slaan die [!DNL Commerce Services] toelaat om te werken. Sommige van deze gegevens kunnen worden geëxporteerd uit de [!DNL Commerce] -instantie en sommige kunnen worden verzameld op basis van winkelgedrag in de winkel. Die gegevens blijven vervolgens bewaard om de cloudopslag te beveiligen.

Voor [!DNL Product Recommendations] en [!DNL Live Search] bevat de SaaS-gegevensruimte catalogus- en gedragsgegevens. U kunt a [!DNL Commerce] instantie aan aSaaS gegevensruimte richten door het [&#x200B; te selecteren &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/services/saas) in de [!DNL Commerce] configuratie.

>[!WARNING]
>
> Gebruik uw **gegevens van productieSaaS** slechts met uw productie [!DNL Commerce] installatie. Het gebruik ervan in niet-productieomgevingen kan tests en live-gegevens combineren (bijvoorbeeld het opvoeren van URL&#39;s of het testen van catalogusgegevens). Als dit gebeurt, [&#x200B; voorlegt een verzoek van de Steun &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/overview) om gegevensschoonmaak te verzoeken.

Als u de configuratievelden van Live Search niet kunt vinden in de beheerfunctie, controleert u of u het juiste API-sleutelpaar hebt ingevoerd voor de gegevensruimte die u hebt geselecteerd (voor productiedesecties worden productietoetsen gebruikt; voor het testen van gegevensruimten worden sandboxsleutels gebruikt). Als u onjuiste toetsen configureert, zijn SaaS-services zoals Live Search niet beschikbaar in die Adobe Commerce-omgeving.

### Een API-sleutel verwijderen {#delapikey}

>[!WARNING]
>
>Als u een sleutel verwijdert die nog actief wordt gebruikt, wordt de verbinding met de services onmiddellijk verbroken.

Voordat u een API-sleutel verwijdert, moet u een vervangende sleutel genereren en veilig opslaan. Werk alle integratie bij om de nieuwe sleutel te gebruiken, en bevestig dat de afhankelijke diensten zoals verwacht werken.

Als u de configuratievelden van **[!DNL Live Search]** niet ziet in het deelvenster Beheer, controleert u of u de juiste SaaS API-sleutel voor die omgeving hebt ingevoerd. Gebruik de productieSaaS sleutel voor de ruimte van productiegegevens en de het opvoeren sleutel voor de het opvoeren gegevensruimte. Als de verkeerde sleutel is geconfigureerd, zijn SaaS-services (inclusief **[!DNL Live Search]**) niet beschikbaar in uw Adobe Commerce-omgeving.

Klik op **[!UICONTROL Delete]** op de API-sleutel die u wilt verwijderen. Bevestig bij de aanwijzing de bewerking om de toets permanent te verwijderen.

### SaaS-gegevensruimteprovisioning

Alle Adobe Commerce-handelaren hebben per SaaS-project toegang tot één ruimte voor productiegegevens en twee ruimten voor testgegevens.

U kunt de testgegevensruimten gebruiken in niet-productieomgevingen, maar u kunt niet tegelijkertijd in meerdere omgevingen dezelfde gegevensruimte gebruiken. Als u een testgegevensruimte naar een andere omgeving wilt verplaatsen, moet u de gegevens opschonen voordat u deze in de nieuwe omgeving selecteert en configureert.

Voor de Pro projecten van de Wolk van de Handel van Adobe met veelvoudige het opvoeren milieu&#39;s, kunt u extra het testen gegevensruimten voor elk het opvoeren milieu verzoeken door [&#x200B; een verzoek van de Steun &#x200B;](https://experienceleague.adobe.com/home?lang=nl-NL&support-tab=home#support) voor te leggen. Als u echter maar één testomgeving hebt en extra testgegevenspaties nodig hebt, hebt u de volgende opties:

- Neem contact op met het team voor succes van de klant of met de door u aangewezen manager voor succes van de klant om een extra testomgeving aan te vragen.

- [&#x200B; legt een verzoek van de Steun &#x200B;](https://experienceleague.adobe.com/home?lang=nl-NL&support-tab=home#support) voor om de extra het testen gegevensruimte te verzoeken en op de bedrijfsrechtvaardiging voor de extra gegevensruimte te wijzen. Dit verzoek moet worden goedgekeurd.

Magento Open Source-klanten die Adobe Payment Services gebruiken, kunnen ook om een extra gegevensruimte vragen. Contacteer het team van Betalingen voor vroegere goedkeuring van de extra gegevensruimten alvorens het verzoek van de a [&#x200B; Steun &#x200B;](https://experienceleague.adobe.com/home?lang=nl-NL&support-tab=home#support) voor te leggen om de het testen gegevensruimte te verzoeken.

De klanten die veelvoudige projecten van de Wolk of op-gebouw (levend/productie) installaties bezitten kunnen extra productie en het testen gegevensruimten voor elk project of instantie ook verzoeken door [&#x200B; een verzoek van de Steun &#x200B;](https://experienceleague.adobe.com/home?lang=nl-NL&support-tab=home#support) voor te leggen.

### Een SaaS-project selecteren of maken {#createsaasenv}

Als u een SaaS-project wilt selecteren of maken, vraagt u de API-sleutels van [!DNL Commerce] aan bij de eigenaar van de [!DNL Commerce] -licentie voor uw winkel:

1. Op _Admin_ sidebar, ga **Systeem** > de Diensten > **Schakelaar van de Diensten van Commerce**.

   Als u niet de **[!UICONTROL Commerce Services Connector]** sectie ziet, installeer de [!DNL Commerce] modules voor uw gewenste [[!DNL Commerce]  dienst &#x200B;](#availableservices) en zorg ervoor dat het `magento/module-services-id` pakket geïnstalleerd is.

1. Plak de hoofdwaarden in de secties _[!UICONTROL Sandbox API Keys]_&#x200B;en&#x200B;_[!UICONTROL Production API Keys]_ .

   - Persoonlijke sleutels moeten `-----BEGIN PRIVATE KEY-----` aan het begin van de toets en `-----END PRIVATE KEY-----` aan het einde van de toets bevatten.
   - Als u geen exemplaar van de daadwerkelijke sleutels hebt, vraag de vergunningseigenaar voor hen, dan stop de waarden in de configuratie.

   Plak geen sleutelwaarden die uit een gegevensbestandsteun of een momentopname worden gekopieerd. Wanneer de configuratie wordt opgeslagen, wordt een extra coderingslaag toegepast en werken de sleutels niet.

1. Klik **sparen**.

   Om het even welke projecten SaaS die met uw sleutels worden geassocieerd verschijnen op het **1&rbrace; gebied van het Project &lbrace;in de** **sectie van het Herkenningsteken SaaS.**

1. Als geen projecten SaaS bestaan, leidt de klik **tot Project**. Dan op het **gebied van het Project**, ga een naam voor uw project SaaS in.

   Om verwarring te vermijden, gebruik geen specifieke dienst van Commerce als naam voor uw project (bijvoorbeeld, *Levend Onderzoek*, *Aanbevelingen van het Product*, of *Verbinding van Gegevens*). Tenzij uw vergunning voor veelvoudige projecten SaaS is provisioned, kunt u het zelfde project SaaS voor de veelvoudige diensten gebruiken.

1. Selecteer de **Ruimte van Gegevens** voor de huidige configuratie van uw [!DNL Commerce] opslag te gebruiken.

   Als u afzonderlijke instanties hebt om met de Diensten van Commerce te integreren, [&#x200B; een kaartje van de Steun &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) voorleggen om een nieuw project SaaS voor elke extra instantie te verzoeken. Na Steun leidt tot het project SaaS, vorm de Schakelaar van de Diensten van Commerce voor de instantie **gebruikend de zelfde API sleutels** en selecteer het nieuwe project SaaS en gegevensruimte.

>[!WARNING]
>
> Als u nieuwe sleutels in het Portaal van API produceert, werk onmiddellijk de sleutels API in de configuratie Admin bij. Als Admin nog oude sleutels gebruikt, werken uw uitbreidingen SaaS niet meer en de gegevensinzameling wordt onderbroken.

Om de namen van uw project SaaS of gegevensruimte te veranderen, klik **anders noemen** naast één van beide. Het veranderen van de naam beïnvloedt niet uw dienst omdat de naam slechts een etiket is om u te helpen tussen projecten en gegevensruimten identificeren en onderscheiden.

## IMS-organisatie (optioneel) {#organizationid}

Als u uw Adobe Commerce-exemplaar wilt verbinden met de Adobe Experience Platform, meldt u zich aan bij uw Adobe-account met uw Adobe ID. Nadat u zich hebt aangemeld, wordt de IMS-organisatie die is gekoppeld aan uw Adobe-account in deze sectie weergegeven.

## SaaS-gegevens exporteren

Wanneer uw [!DNL Commerce] -instantie verbinding heeft gemaakt met [!DNL Commerce Services] , exporteert het SaaS-gegevensexportproces Commerce-gegevens van uw [!DNL Commerce] -server naar [!DNL Commerce SaaS Services] , zodat deze kunnen worden gesynchroniseerd met verbonden Commerce Services. In Admin, kunt u synchronisatiestatus controleren gebruikend het [&#x200B; dashboard van het Beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard). Voor details, zie de [&#x200B; Gids van de Uitvoer van Gegevens SaaS &#x200B;](../data-export/overview.md).
