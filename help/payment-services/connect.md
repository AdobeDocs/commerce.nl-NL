---
title: Uw instantie verbinden
description: Sluit uw Commerce-instantie aan met behulp van een API-sleutel en een persoonlijke sleutel en geef de gegevensruimte op in de configuratie.
feature: Payments, Checkout, Configuration, Saas
exl-id: f2b3be02-e9dd-4bca-b9e4-c80a56bf8691
source-git-commit: 16bd0e7ed1e8982e1571e2593115824a2004b7dc
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Uw instantie verbinden

[!DNL Payment Services] wordt aangedreven door Commerce Services en geïmplementeerd als SaaS (software als service). U verbindt uw instantie van Commerce gebruikend een API sleutel en een privé sleutel, en specificeert de gegevensruimte in de configuratie gebruikend de [ Schakelaar van de Diensten van Commerce ](https://experienceleague.adobe.com/docs/commerce/user-guides/saas.html). **u opstelling deze verbinding slechts eenmaal.**

>[!VIDEO](https://video.tv.adobe.com/v/3447835)

>[!INFO]
>
> Zie onze [&#128279;](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=nl-NL) video van de Schakelaar van de Diensten 0&rbrace; &lbrace;voor extra informatie.[!DNL Adobe Commerce] 

* Als u *reeds uw instantie* hebt verbonden, door uw API geloofsbrieven te verkrijgen en te gebruiken en de Diensten van Commerce te vormen, kunt u aan [ vestiging uw het testen zandbak ](https://experienceleague.adobe.com/docs/commerce/payment-services/get-started/sandbox.html?lang=nl-NL) te werk gaan.
* Als u nog *uw instantie* moet verbinden, zie de informatie in dit onderwerp over [ het verkrijgen API geloofsbrieven ](#obtain-api-credentials) en [ het vormen de Diensten van Commerce ](#configure-commerce-services).
* Als u *onzeker bent of uw instantie* wordt aangesloten, navigeer aan **Systeem** > de Diensten > **Verbinding van de Diensten van Commerce** en bekijk de openbare en privé API zeer belangrijke waarden in de [!UICONTROL Sandbox Keys] en [!UICONTROL Production Keys] secties, en *Project* en *gebieden van de Ruimte van 10&rbrace; Gegevens in de [!UICONTROL SaaS Identifier] sectie.* Als deze waarden aanwezig zijn, wordt de instantie verbonden.

>[!NOTE]
>
>Alle handelaren die recht hebben op Betalingsdiensten, kunnen gebruik maken van één ruimte voor productiegegevens en twee ruimten voor testgegevens.

## API-referenties verkrijgen

Om de dienst van Commerce te verbruiken SaaS, moet u API van uw instantie (de openbare sleutel van Commerce API en een privé sleutel) voor zowel zandbak als productie gebruiken, die worden gecreeerd en in uw [ Mijn Dashboard van de Rekening ](https://account.magento.com/customer/account/login) beheerd. [ het zeer belangrijke paar ](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/services/saas) kan voor een rekening-voor zandbak van Commerce en voor productie-hoewel slechts één paar actief kunnen tegelijkertijd worden gebruikt.

>[!NOTE]
>
>Hebt u hulp nodig bij het openen van uw [!UICONTROL My Account] dashboard? Zie [ een rekening van Commerce ](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/commerce-account/commerce-account-create) creëren.

Een openbare API-sleutel is altijd beschikbaar op het dashboard voor Mijn account nadat deze is gemaakt. Het kan worden gekopieerd of worden geschrapt zoals nodig. De persoonlijke API-sleutel wordt zichtbaar wanneer u een openbare API-sleutel maakt voor de sandbox of productie. Deze sleutel kan alleen worden gekopieerd of opgeslagen vanuit het dialoogvenster dat verschijnt en kan later niet worden geopend.

Een gegeven API zeer belangrijk paar is geldig voor alle Diensten van Commerce in een milieu, zodat als u reeds de Diensten van Commerce voor uw geval hebt gevormd, is uw API zeer belangrijk paar reeds aanwezig in de Schakelaar van de Diensten van Commerce.

Als uw API sleutel wordt verloren, moet een nieuw API zeer belangrijk paar [ worden geproduceerd ](https://experienceleague.adobe.com/docs/commerce/payment-services/get-started/connect.html?lang=nl-NL#generate-an-api-key-and-private-key) en [ worden toegepast ](https://experienceleague.adobe.com/docs/commerce/payment-services/get-started/connect.html?lang=nl-NL#configure-saas-project) op de Configuratie van de Verbinding van de Diensten van Commerce in Admin. Als de verkeerde sleutels worden gevormd of niets in config bestaat, verschijnt een de foutendialoog van de rekeningscontrole in de Diensten die van de Betaling u op de hoogte brengen dat de rekening niet werd geverifieerd.

Zie a [ lijst van de beschikbare Diensten van Commerce die API ](https://experienceleague.adobe.com/nl/docs/commerce/user-guides/integration-services/saas#availableservices) gebruiken.

Leren hoe te om een API sleutel voor of zandbak of productiemilieu&#39;s te produceren, zie [ Geloofsbrieven ](https://experienceleague.adobe.com/docs/commerce/user-guides/saas.html#apikey).

>[!IMPORTANT]
>
>Het wordt geadviseerd dat u geen API zeer belangrijk paar *regenereert en* verandert het herkenningsteken SaaS en/of gegevensruimte op een actieve productiemilitie. U verliest gegevens voor uw instantie als deze worden gewijzigd.

## Commerce Services configureren

De zelfde API sleutel kan over instanties worden gebruikt, maar elke instantie moet zijn eigen [ Ruimte van Gegevens SaaS ](https://experienceleague.adobe.com/docs/commerce/user-guides/saas.html#saasenv) hebben.

>[!NOTE]
>
>De handelaren moeten de zelfde sleutels gebruiken die voor MageID voor hun toeslagrechten worden geproduceerd.

Nu u uw geloofsbrieven hebt verkregen, kunt u uw project SaaS en de Ruimte van Gegevens van het Saas vormen.

1. Voor _Admin_ sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Klik op **[!UICONTROL Configure Commerce Services]**.

   Deze optie is zichtbaar als u nog geen Commerce Services voor uw account hebt geconfigureerd.

   U wordt verwezen naar het configuratiegebied in Admin, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, om uw Commerce Services-connector te configureren.

1. Om uw diensten van Commerce te vormen, volg de stappen die in [ configuratie SaaS ](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=nl-NL#saasenv) worden beschreven.

   >[!INFO]
   >
   > Zie onze [&#128279;](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/admin/adobe-commerce-services/configure-adobe-commerce-services-connector.html?lang=nl-NL#configuration-faqs) video van de Schakelaar van de Diensten 0&rbrace; &lbrace;voor extra informatie.[!DNL Adobe Commerce] 

## Endpoint

[!DNL Payment Services] gebruikt de [ Schakelaar van de Diensten van Commerce ](https://experienceleague.adobe.com/docs/commerce/user-guides/saas.html) om met de Diensten van Commerce te verbinden en als SaaS op te stellen. Deze [!DNL Commerce Services Connector] communiceert door het eindpunt bij:

* `commerce-beta.adobe.io` voor sandboxomgevingen.
* `commerce.adobe.io for` voor live omgevingen.
