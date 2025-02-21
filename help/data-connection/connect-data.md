---
title: Commerce-gegevens verbinden met Adobe Experience Platform
description: Leer hoe u Commerce-gegevens koppelt aan de Adobe Experience Platform.
feature: Personalization, Integration, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '2910'
ht-degree: 0%

---

# Commerce-gegevens verbinden met Adobe Experience Platform

Wanneer u de [!DNL Data Connection] uitbreiding installeert, verschijnen twee nieuwe configuratiepagina&#39;s in het **Systeem** menu onder **Diensten** in Commerce _Admin_.

- Commerce Services Connector
- [!DNL Data Connection]

Als u uw Adobe Commerce-instantie wilt verbinden met de Adobe Experience Platform, moet u beide connectors configureren, te beginnen met de Commerce Services-connector en vervolgens voltooien met de [!DNL Data Connection] -extensie.

## De Commerce Services-connector configureren

Als u eerder een Adobe Commerce-service hebt geïnstalleerd, hebt u waarschijnlijk al de Commerce Services-connector geconfigureerd. Als niet, dan moet u de volgende taken op de [ schakelaar van de Diensten van Commerce ](../landing/saas.md) pagina voltooien:

1. Login aan uw rekening van Commerce [ wint uw productie en zandbak API sleutels ](../landing/saas.md#credentials) terug.
1. Selecteer a [ SaaS gegevensruimte ](../landing/saas.md#saas-configuration).
1. Login aan uw rekening van Adobe [ wint uw identiteitskaart van de Organisatie ](../landing/saas.md#ims-organization-optional) terug.

Nadat u de Commerce Services-connector hebt geconfigureerd, configureert u de extensie [!DNL Data Connection] .

## De extensie [!DNL Data Connection] configureren

In deze sectie leert u hoe u de extensie [!DNL Data Connection] configureert.

### Servicerekening en verificatiegegevens toevoegen

Als u van plan bent om [ historische ordegegevens ](#send-historical-order-data) of [ gegevens van het klantenprofiel ](#send-customer-profile-data) te verzamelen en te verzenden, moet u de dienstrekening en credentiedetails toevoegen. Ook, als u de [ uitbreiding van Audience Activation ](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) vormt, moet u deze stappen voltooien.

Als u slechts storefront of achterbureaugegevens verzamelt en verzendt, kunt u aan de [ algemene ](#general) sectie overslaan.

#### Stap 1: Een project maken in Adobe Developer Console

Maak in de Adobe Developer Console een project voor het verifiëren van Commerce zodat Experience Platform API-aanroepen kunnen worden uitgevoerd.

Om het project tot stand te brengen, volg de stappen die in [ worden geschetst voor authentiek verklaren en toegang Experience Platform APIs ](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html) leerprogramma.

Terwijl u de zelfstudie doorloopt, moet u ervoor zorgen dat uw project het volgende heeft:

- Toegang tot de volgende [ productprofielen ](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#select-product-profiles): **Standaardproductie alle toegang** en **Standaard AEP alle toegang**.
- De correcte [ rollen en de toestemmingen worden gevormd ](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#assign-api-to-a-role).
- Als u hebt besloten JSON Web Tokens (JWT) als uw server-aan-server authentificatiemethode te gebruiken, moet u ook een privé sleutel uploaden.

Het resultaat van deze stap leidt tot een configuratiedossier dat u in de volgende stap gebruikt.

#### Stap 2: configuratiebestand downloaden

Download het [ dossier van de werkruimteconfiguratie ](https://developer.adobe.com/commerce/extensibility/events/project-setup/#download-the-workspace-configuration-file). Kopieer en kleef de inhoud van dit dossier in de **Rekening van de Dienst/Credentiële details** pagina van Commerce Admin.

1. In Commerce Admin, navigeer aan **Opslag** > Montages > **Configuratie** > **de Diensten** > **[!DNL Data Connection]**.

1. Selecteer de server-aan-server vergunningsmethode die u van het **Van het Type van Vergunning van Adobe Developer** menu uitvoerde. Adobe raadt u aan OAuth te gebruiken. JWT is vervangen. [ leer meer ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

1. (JWT slechts) Exemplaar en kleef de inhoud van uw `private.key` dossier in het **Geheime** gebied van de Cliënt. Gebruik de volgende opdracht om de inhoud te kopiëren.

   ```bash
   cat config/private.key | pbcopy
   ```

   Zie [ Authentificatie van de Rekening van de Dienst (JWT) ](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) voor meer informatie over het `private.key` dossier.

1. Kopieer de inhoud van het `<workspace-name>.json` dossier in het **de Rekening van de Dienst/Credentiële details** gebied.

   ![[!DNL Data Connection] Beheerdersconfiguratie ](./assets/epc-admin-config.png){width="700" zoomable="yes"}

1. Klik **sparen Config**.

1. Klik op de knop **[!UICONTROL Test connection]** om te controleren of de ingevoerde serviceaccount en referentie-informatie juist zijn.

### Algemeen

1. In Admin, ga naar **Systeem** > de Diensten > **[!DNL Data Connection]**.

   ![[!DNL Data Connection] Instellingen ](./assets/epc-settings.png){width="700" zoomable="yes"}

1. Op het **lusje van Montages** onder **Algemeen**, verifieer identiteitskaart verbonden aan uw rekening van Adobe Experience Platform, zoals die in de [ Schakelaar van de Diensten van Commerce ](../landing/saas.md#organizationid) wordt gevormd. De organisatie-id is algemeen. Per Adobe Commerce-exemplaar kan slechts één organisatie-id worden gekoppeld.

1. In het **drop-down van het Werkgebied**, plaats de context aan **Website**.

1. (Optioneel) Als u al een [ AEP Web SDK (legering) ](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) aan uw site hebt geïmplementeerd, schakelt u het selectievakje in en voegt u de naam van uw AEP Web SDK toe. Anders laat u deze velden leeg en implementeert de extensie [!DNL Data Connection] er een voor u.

   >[!NOTE]
   >
   >Als u uw eigen AEP Web SDK opgeeft, gebruikt de extensie [!DNL Data Connection] de gegevensstroom-id die aan die SDK is gekoppeld en niet de gegevensstroom-id die op deze pagina is opgegeven (indien aanwezig).

### Gegevensverzameling

In deze sectie geeft u het type gegevens op dat u wilt verzamelen en naar de Experience Platform-rand wilt verzenden. Er zijn drie soorten gegevens:

- **Gedrag** (cliënt-zijgegevens) is gegevens die op storefront worden gevangen. Dit omvat winkelinteracties, zoals `View Page`, `View Product`, `Add to Cart`, en [ de lijstinformatie van de 3} aanvraag ](events.md#b2b-events) (voor B2B handelaren).

- **het bureau van de rug** (server-zijgegevens) is gegevens die in de servers van Commerce worden gevangen. Dit omvat informatie over de status van een bestelling, zoals of een bestelling is geplaatst, geannuleerd, terugbetaald, verzonden of voltooid. Het omvat ook [ historische ordegegevens ](#send-historical-order-data).

- **Profiel** is gegevens met betrekking tot de het profielinformatie van uw klant. Leer [ meer ](#send-customer-profile-data).

Om ervoor te zorgen dat uw instantie van Adobe Commerce met gegevensinzameling kan beginnen, herzie de [ eerste vereisten ](overview.md#prerequisites).

Zie het gebeurtenisonderwerp om meer over [ storefront ](events.md#storefront-events), [ achterkantoor ](events-backoffice.md), en [ profiel ](events-backoffice.md#customer-profile-events-server-side) gebeurtenissen te leren.

>[!NOTE]
>
>Alle gebieden in de **sectie van de inzameling van 0} Gegevens {zijn op het** 3} werkingsgebied van de Website {van toepassing.****

1. Selecteer **gebeurtenissen Storefront** als u storefront gedragsgegevens wilt verzenden.

1. Selecteer **de gebeurtenissen van het achterkantoor** als u de informatie van de ordestatus, zoals wilt verzenden als een orde werd geplaatst, geannuleerd, terugbetaald, of verscheept.

   >[!NOTE]
   >
   >Als u **de gebeurtenissen van het achterkantoor** selecteert, worden alle achterkantoorgegevens verzonden naar de rand van Experience Platform. Als een winkelier ervoor kiest zich af te melden voor gegevensverzameling, moet u de privacyvoorkeur van de winkels expliciet instellen in de Experience Platform. Dit is anders dan storefront-gebeurtenissen waarbij de verzamelaar al toestemming afhandelt op basis van de voorkeuren van de winkels. Leer [ meer ](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) over het plaatsen van de privacyvoorkeur van een verkoopster in Experience Platform.

1. (Sla deze stap over als u uw eigen SDK van het Web van AEP. gebruikt) [ creeer ](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#create) een gegevensstroom in Adobe Experience Platform of selecteer een bestaande gegevensstroom u voor inzameling wilt gebruiken. Ga die gegevensstroomidentiteitskaart op het **gebied van identiteitskaart 0} DataStream in.**

1. Ga **identiteitskaart van de Dataset** in die u uw gegevens van Commerce wilt bevatten. De id van de gegevensset zoeken:

   1. Open Experience Platform UI en selecteer **Datasets** in de linkernavigatie om het **** dashboard van Datasets {te openen. Het dashboard maakt een lijst van alle beschikbare datasets voor uw organisatie. De details worden getoond voor elke vermelde dataset, met inbegrip van zijn naam, het schema de dataset zich aan, en status van de meest recente versiereeks houdt.
   1. Open de dataset verbonden aan uw gegevensstroom.
   1. In de rechterruit, bekijk de details over de dataset. Kopieer de id van de gegevensset.

1. Om de updates van de achterkantoorgebeurtenisgegevens te verzekeren die op een programma volgens a [ worden gebaseerd bouwt ](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) baan, moet u de `Sales Orders Feed` index in `Update by Schedule` veranderen.

   1. Voor _Admin_ sidebar, ga **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. Schakel het selectievakje voor de `Sales Orders Feed` indexer in.

   1. Stel **[!UICONTROL Actions]** in op `Update by Schedule` .

   1. Als u de gegevens van het achterkantoor voor het eerst toelaat, stel de volgende bevelen in werking om opnieuw te indexeren en een resync teweeg te brengen. De verdere resyncs komen automatisch voor zolang de [ bouwt ](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) baan correct opstelling is.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

#### Veldomschrijvingen

| Veld | Beschrijving |
|--- |--- |
| Toepassingsgebied | Specifieke website waarop u de configuratie-instellingen wilt toepassen. |
| Organisatie-id (wereldwijd) | Id die behoort tot de organisatie die het Adobe DX-product heeft aangeschaft. Deze id koppelt uw Adobe Commerce-exemplaar aan Adobe Experience Platform. |
| Is de AEP Web SDK al geïmplementeerd op uw site | Schakel dit selectievakje in als u uw eigen AEP Web SDK op uw site hebt geïmplementeerd |
| AEP Web SDK Name (global) | Als er al een Experience Platform Web SDK op uw site is geïmplementeerd, geeft u de naam van die SDK in dit veld op. Hierdoor kunnen de Storefront Event Collector en Storefront Event SDK uw Experience Platform Web SDK gebruiken in plaats van de versie die door de [!DNL Data Connection] -extensie wordt geïmplementeerd. Als er geen Experience Platform Web SDK op uw site is geïmplementeerd, laat u dit veld leeg en implementeert de extensie [!DNL Data Connection] er een voor u. |
| Gebeurtenissen van Storefront | Wordt standaard ingeschakeld zolang de organisatie-id en de gegevensstroom-id geldig zijn. Met Storefront-gebeurtenissen worden geanonimiseerde gedragsgegevens verzameld bij kopers die door uw site bladeren. |
| Back office evenementen | Als deze optie is ingeschakeld, bevat de gebeurtenislading geanonimiseerde gegevens over de status van de bestelling, zoals of een bestelling is geplaatst, geannuleerd, terugbetaald of verzonden. |
| DataStream-id (website) | ID waarmee gegevens kunnen worden verzonden van Adobe Experience Platform naar andere Adobe DX-producten. Deze id moet zijn gekoppeld aan een specifieke website in uw specifieke Adobe Commerce-exemplaar. Als u uw eigen Experience Platform Web SDK opgeeft, geef dan geen gegevensstroom-id op in dit veld. De extensie [!DNL Data Connection] gebruikt de gegevensstroom-id die aan die SDK is gekoppeld en negeert de gegevensstroom-id die in dit veld is opgegeven (indien aanwezig). |
| Gegevensset-id (website) | Id van de dataset die uw gegevens van Commerce bevat. Dit gebied wordt vereist tenzij u de **gebeurtenissen Storefront** of **checkboxes van de het bureaugebeurtenissen** hebt geschrapt. Ook, als u uw eigen SDK van het Web van Experience Platform gebruikt en daarom geen gegevensstroom identiteitskaart specificeerde, moet u dataset nog toevoegen identiteitskaart verbonden aan uw gegevensstroom. Anders kunt u dit formulier niet opslaan. |

Na het instappen, beginnen de archiefgegevens aan de rand van Experience Platform te stromen. Het duurt ongeveer vijf minuten voordat de gegevens op het achterkantoor aan de rand worden weergegeven. Volgende updates zijn zichtbaar aan de rand op basis van het uitsnijdschema.

### Klantprofielgegevens verzenden

Er zijn twee typen profielgegevens die u naar de Experience Platform kunt verzenden: profielrecords en tijdreeksprofielgebeurtenissen.

Een profielrecord bevat gegevens die worden opgeslagen wanneer een gebruiker een profiel in uw Commerce-instantie maakt, zoals de naam van de klant. Wanneer uw schema en dataset [ behoorlijk worden gevormd ](profile-data.md), wordt een profielverslag verzonden naar Experience Platform en door:sturen aan het profielbeheer en de segmenteringsdienst van Adobe: [ Real-Time CDP ](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

Profielgebeurtenissen uit een tijdreeks bevatten gegevens over de profielgegevens van uw klant, zoals het maken, bewerken of verwijderen van een account op uw site. Wanneer de gegevens van de profielgebeurtenis naar Experience Platform worden verzonden, verblijft het in een dataset waar het door andere producten DX kan worden gebruikt.

1. Zorg ervoor u [ verstrekte ](#add-service-account-and-credential-details) de dienstrekening en credentiedetails hebt.

1. Zorg ervoor u een schema en dataset hebt die voor [ wordt gespecificeerd de gegevensopname van het profielverslag ](profile-data.md) en [ de gebeurtenisopname van het tijdreeksenprofiel ](update-xdm.md#time-series-profile-event-data).

1. Plaats een controleteken in **de profielen van de Klant** checkbox als u profielgegevens naar Experience Platform wilt verzenden.

1. Ga **identiteitskaart van de Dataset van het Profiel** in.

   De het verslaggegevens van het profiel moeten een verschillende dataset gebruiken dan wat u momenteel voor gedrags en achterkantoorgebeurtenisgegevens gebruikt.

1. Als u niet profielgebeurtenissen door zelfde gegevensstroom identiteitskaart wilt stromen die u voor gedrag en achterbureaugegevens gebruikt, verwijder het controleteken uit de **de klantenprofielen van de Stroom door zelfde datastream identiteitskaart** en ga gegevensstroom identiteitskaart in u in plaats daarvan wilt gebruiken.

Het kan ongeveer 10 minuten duren voordat een profielrecord beschikbaar is in Real-Time CDP. Profielgebeurtenissen beginnen direct met streamen.

>[!TIP]
>
>Als u profielgegevens in Experience Platform ziet, zie [ Commerce KnowledgeBase ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/data-connection-customer-profiles-not-exported) voor het oplossen van problemensuggesties.

#### Veldomschrijvingen

| Veld | Beschrijving |
|--- |--- |
| Klantprofielen | Schakel dit selectievakje in als u records met klantprofielen wilt verzamelen en verzenden. |
| Profielgegevensset-id | Een profielverslag moet een verschillende dataset gebruiken dan de dataset die voor gedrags en achterkantoorgebeurtenissen wordt gebruikt. |
| Klantprofielen streamen via dezelfde gegevensstroom-id | Bepaal of u dezelfde gegevensstroom wilt gebruiken die momenteel wordt gebruikt voor uw gedrags- en backoffice-gebeurtenissen. |
| DataStream voor klantprofielen | Geef de recordspecifieke gegevensstroom voor het klantprofiel op. |

### Gegevens in historische volgorde verzenden

Adobe Commerce verzamelt tot vijf jaar van [ historische ordegegevens en status ](events-backoffice.md#back-office-events). U kunt de extensie [!DNL Data Connection] gebruiken om die historische gegevens naar de Experience Platform te verzenden om uw klantprofielen te verrijken en de ervaringen van de klant op basis van die eerdere bestellingen aan te passen. De gegevens worden opgeslagen in een dataset binnen Experience Platform.

Hoewel Commerce de historische ordergegevens al verzamelt, moet u verschillende stappen uitvoeren om die gegevens naar Experience Platform te verzenden.

Bekijk deze video om meer over historische orden te leren dan voltooi de volgende stappen om historische ordeverzameling uit te voeren.

>[!VIDEO](https://video.tv.adobe.com/v/3424672)

#### De bestelsynchronisatieservice instellen

De dienst van de ordesynchronisatie gebruikt het [ Kader van de Rij van het Bericht ](https://developer.adobe.com/commerce/php/development/components/message-queues/) en RabbitMQ. Nadat u deze stappen hebt uitgevoerd, kunnen de statusgegevens van de bestelling worden gesynchroniseerd met SaaS, wat vereist is voordat deze naar Experience Platform worden verzonden.

1. Zorg ervoor u [ verstrekte ](#add-service-account-and-credential-details) de dienstrekening en credentiedetails hebt.

1. [ laat ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq.html) RabbitMQ toe.

   >[!NOTE]
   >
   >RabbitMQ is al ingesteld voor Commerce versie 2.4.7 en hoger, maar u moet de consument inschakelen.

1. Gebruikers in een wachtrij via een snijtaak inschakelen in `.magento.env.yaml` met behulp van de omgevingsvariabele `CRON_CONSUMERS_RUNNER` .

   ```yaml
      stage:
        deploy:
          CRON_CONSUMERS_RUNNER:
            cron_run: true
   ```

   >[!NOTE]
   >
   >Zie [ variabelen documentatie ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) opstellen om over alle beschikbare configuratieopties te leren.

Als de bestelsynchronisatieservice is ingeschakeld, kunt u het historische bereik van de ordedatum opgeven op de pagina **[!UICONTROL [!DNL Data Connection]]** .

#### Datumbereik van orderhistorie opgeven

Geef het datumbereik op voor de historische orders die u naar Experience Platform wilt verzenden.

1. In Admin, ga naar **Systeem** > de Diensten > **[!DNL Data Connection]**.

1. Selecteer de **Geschiedenis van de Orde** tabel.

   ![[!DNL Data Connection] Order History ](./assets/epc-order-history.png){width="700" zoomable="yes"}

1. Onder **de Synchronisatie van de Geschiedenis van de Orde**, wordt identiteitskaart van de Dataset van het Exemplaar van Montages **checkbox reeds toegelaten.** Dit verzekert u de zelfde dataset gebruikt die in de **wordt gespecificeerd Montages** tabel.

1. In **van** en **aan** gebieden, specificeer de datumwaaier voor de historische ordegegevens u wilt verzenden. U kunt geen datumbereik selecteren dat langer is dan vijf jaar.

1. Selecteer **[!UICONTROL Start Sync]** om de synchronisatie te starten. Historische ordegegevens zijn batchgegevens in tegenstelling tot opslag en achterkantoorgegevens die gegevens stromen. Het duurt ongeveer 45 minuten voordat de gegevens in de batch in Experience Platform zijn ontvangen.

##### Veldomschrijvingen

| Veld | Beschrijving |
|--- |--- |
| Gegevensset-id kopiëren uit instellingen | Kopieert dataset identiteitskaart u op het **lusje van Montages** inging. |
| Gegevensset-id (website) | Id van de dataset die uw gegevens van Commerce bevat. Dit gebied wordt vereist tenzij u de **gebeurtenissen Storefront** of **checkboxes van de het bureaugebeurtenissen** hebt geschrapt. Ook, als u uw eigen SDK van het Web van Experience Platform gebruikt en daarom geen gegevensstroom identiteitskaart specificeerde, moet u dataset nog toevoegen identiteitskaart verbonden aan uw gegevensstroom. Anders kunt u dit formulier niet opslaan. |
| Van | Datum vanaf wanneer u wilt beginnen met het verzamelen van gegevens over de ordergeschiedenis. |
| Naar | Datum vanaf welke u het verzamelen van de gegevens van de ordegeschiedenis wilt beëindigen. |
| Synchronisatie starten | Begint het proces om de gegevens van de ordegeschiedenis aan de rand van Experience Platform te synchroniseren. Deze knop is uitgeschakeld als het veld **[!UICONTROL Dataset ID]** leeg is of als de id van de gegevensset ongeldig is. |

### Aanpassing van gegevens

Op het **lusje van de Aanpassing van Gegevens**, kunt u om het even welke douanekenmerken bekijken die in [!DNL Commerce] worden gevormd en naar Experience Platform worden verzonden.

![[!DNL Data Connection] Gegevens aanpassen ](./assets/epc-data-customization.png){width="700" zoomable="yes"}

>[!IMPORTANT]
>
>Zorg ervoor dat gegevensstroomidentiteitskaart u [ ](#data-collection) op het **lusje van de Inzameling van Gegevens** verbonden identiteitskaart met het schema voor het opnemen van douaneattributen specificeerde.

Wanneer u aangepaste kenmerken voor bestellingen maakt en deze naar de Experience Platform verzendt, moeten de kenmerknamen in Commerce overeenkomen met die in het [!DNL Commerce] -schema op de Experience Platform. Als ze niet overeenkomen, kan het moeilijk zijn om de verschillen vast te stellen. Als u namen verkeerd hebt overtroffen, kan de **lijst van de Attributen van de Orde van de Douane** helpen het probleem oplossen.

De **Lijst van de Attributen van de Orde van de Douane** verstrekt zicht in de configuratie en de afbeelding van de attributen van de douaneorde tussen het [!DNL Commerce] achterbureau en het [!DNL Commerce] schema in Experience Platform. In deze tabel kunt u aangepaste kenmerken op orderniveau en orderniveau in verschillende bronnen weergeven, zodat u ontbrekende of onjuist uitgelijnde kenmerken gemakkelijker kunt herkennen. Het toont ook dataset IDs helpen zich tussen levende en historische datasets onderscheiden, aangezien elk zijn eigen douanekenmerken kan hebben.

Als er geen groen vinkje wordt weergegeven naast de naam van een aangepast kenmerk in de tabel, wordt aangegeven dat de kenmerknamen in de bronnen niet overeenkomen. Corrigeer de kenmerknaam in één bron en er verschijnt een groen vinkje om aan te geven dat de namen nu overeenkomen.

- Als de attributennaam in het schema in Experience Platform wordt bijgewerkt, moet u de configuratie op het **lusje van de Aanpassing van Gegevens** bewaren om de het schemaverandering van Experience Platform teweeg te brengen. Deze verandering zal in de **Lijst van de Attributen van de Orde van de Douane** worden weerspiegeld wanneer u de **[!UICONTROL Refresh]** knoop klikt.
- Als de attributennaam in [!DNL Commerce] wordt bijgewerkt, moet een ordegebeurtenis worden geproduceerd om de naam in de **Lijst van de Attributen van de Orde van de Douane bij te werken**. De verandering zal in ongeveer 60 minuten worden weerspiegeld.

Leer meer over hoe te [ de attributen van de opstellingsdouane ](custom-attributes.md).

#### Veldomschrijvingen

| Veld | Beschrijving |
|--- |--- |
| Gegevensset | Toont de datasets die de douanekenmerken bevatten. Levende en historische datasets kunnen hun eigen douanekenmerken hebben. |
| Adobe Commerce | Hiermee geeft u aangepaste kenmerken weer die in het [!DNL Commerce] achterkantoor zijn gemaakt. |
| Experience Platform | Geeft alle aangepaste kenmerken weer die in het [!DNL Commerce] -schema in Experience Platform zijn opgegeven. |
| Vernieuwen | Haalt namen van aangepaste kenmerken op uit het schema [!DNL Commerce] in Experience Platform. |

## Bevestig dat gebeurtenisgegevens worden verzameld

Om te bevestigen dat het gegeven van uw opslag van Commerce wordt verzameld, gebruik [ debugger van Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) om uw plaats van Commerce te onderzoeken. Nadat u bevestigt dat het gegeven wordt verzameld, kunt u verifiëren dat uw storefront en achterkantoorgebeurtenisgegevens bij de rand verschijnen door een vraag in werking te stellen die gegevens van de [ dataset terugkeert u ](overview.md#prerequisites) creeerde.

1. Selecteer **Vragen** in de linkernavigatie van Experience Platform en klik [!UICONTROL Create Query].

   ![ Redacteur van de Vraag ](assets/query-editor.png)

1. Wanneer de Redacteur van de Vraag opent, ga een vraag in die gegevens van de dataset selecteert.

   ![ creeer vraag ](assets/create-query.png)

   Uw query ziet er bijvoorbeeld als volgt uit:

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. Na de vraaglooppas, worden de resultaten getoond in het **lusje van Resultaten**, naast de **Console** tabel. In deze weergave ziet u de tabeluitvoer van uw query.

   ![ Redacteur van de Vraag ](assets/query-results.png)

In dit voorbeeld ziet u gebeurtenisgegevens van de deelvensters [`commerce.productListAdds`](events.md#addtocart) , [`commerce.productViews`](events.md#productpageview) , [`web.webpagedetails.pageViews`](events.md#pageview) , enzovoort. In deze weergave kunt u controleren of uw Commerce-gegevens zich aan de rand bevinden.

Als de resultaten niet zijn wat u verwacht, open uw dataset en zoek om het even welke ontbroken partijinvoer. Leer meer over [ de invoer van de het oplossen van problemenpartij ](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).

### Controleer of de profielgegevens worden weergegeven in de Experience Platform

Als u profielgegevens in Experience Platform ziet, zie [ Commerce KnowledgeBase ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/data-connection-customer-profiles-not-exported) voor het oplossen van problemensuggesties.

## Volgende stappen

Wanneer Commerce-gegevens naar de Experience Platform edge worden verzonden, kunnen andere Adobe Experience Cloud-producten, zoals Adobe Journey Optimizer, die gegevens gebruiken. U kunt Journey Optimizer bijvoorbeeld configureren om te luisteren naar bepaalde gebeurtenissen en op basis van die gebeurtenisgegevens een e-mail activeren voor een nieuwe gebruiker of als er een verlaten winkelwagentje is. Leer hoe u uw platform van Commerce kunt uitbreiden door [ klantenreizen ](using-ajo.md) in Journey Optimizer tot stand te brengen.
