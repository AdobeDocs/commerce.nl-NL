---
source-git-commit: 156ed7a480de9239843c96b6b6bc252585f498d6
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---
# Commerce-fragmenten


## Merchandising Services for Optimizer {#aco-merchandising-services}

>[!NOTE]
>
>Voor de oplossingen van Commerce die Adobe Commerce Optimizer of de schakelaar van Adobe Commerce Optimizer gebruiken, gebruik de [ Merchandising Services GraphQL API ](https://developer.adobe.com/commerce/services/optimizer/merchandising-services/using-the-api/) in plaats van de dienst GraphQL API van de Catalogus.

## Controle van de Synchronisatie van gegevens voor Optimizer {#aco-data-sync-verification}

>[!NOTE]
>
>Als u de [ Schakelaar van Adobe Commerce Optimizer ](../aco-connector/overview.md) hebt geïnstalleerd om catalogusgegevens naar Adobe Commerce Optimizer uit te voeren, gebruik de [ pagina van de Status van de Synchronisatie van het Gegeven van Gegevens ](../optimizer/setup/data-sync.md) in Commerce Optimizer Studio om gegevens te controleren die met succes aan Adobe Commerce Optimizer in plaats van het Dashboard van het Beheer van Gegevens worden gesynchroniseerd.

## ACCS vroege toegang {#accs-early-access}

>[!NOTE]
>
>Deze documentatie beschrijft een product in vroege-toegangsontwikkeling en weerspiegelt niet alle functionaliteit voorgenomen voor algemene beschikbaarheid.

<!--
## Nav hack ACCS {#nav-hack-accs}

>[!BEGINSHADEBOX]

<table style="table-layout:fixed">
  <tr>
    <td style="vertical-align: middle;"><a href="https://developer.adobe.com/commerce/webapi/"><img alt="Developers" src="../assets/icons/developers.svg" /> <strong>Developers</strong></a></td>
    <td style="vertical-align: middle;"><a href="https://experienceleague.adobe.com/developer/commerce/storefront/"><img alt="Storefront" src="../assets/icons/storefront.svg" /> <strong>Storefront</strong></a></td>
    <td style="vertical-align: middle;"><a href="../cloud-service/overview.md"><img alt="Merchants" src="../assets/icons/merchants.svg" /> <strong>Merchants</strong></a></td>
    <td style="vertical-align: middle;"><a href="https://experienceleague.adobe.com/en/docs/commerce-learn/tutorials/getting-started/commerce-as-a-cloud-service/overview"><img alt="Videos" src="../assets/icons/videos.svg" /> <strong>Videos</strong></a></td>
    <td style="vertical-align: middle;"><a href="https://experienceleague.adobe.com/developer/commerce/storefront/playgrounds/commerce-services/"><img alt="Playgrounds" src="../assets/icons/playgrounds.svg" /> <strong>Playgrounds</strong></a></td>
  </tr>
</table>

>[!ENDSHADEBOX]
-->

## Experimentele functie van alleen de ACCS-sandbox {#accs-sandbox-experimental}

>[!IMPORTANT]
>
>Deze functie is experimenteel en is alleen beschikbaar in Sandbox-omgevingen van [!DNL Adobe Commerce as a Cloud Service] .
>
>Deze functie kan zonder voorafgaande kennisgeving worden gewijzigd.

[!BADGE  Sandbox ]{type=Caution tooltip="De vermelde items zijn momenteel alleen beschikbaar in Sandbox-omgevingen. Adobe stelt nieuwe releases eerst beschikbaar in Sandbox-omgevingen om tijd te bieden voor het testen van aanstaande wijzigingen voordat de release beschikbaar is in Productomgevingen."}

## AEM Assets-instantietoewijzing {#aem-assets-instance-mapping}

>[!NOTE]
>
>Wanneer u [!DNL Adobe Commerce as a Cloud Service] verbindt met [!DNL AEM Assets] , wijst uw [!DNL AEM Assets] Stage-instantie de inhoud toe aan uw Sandbox [!DNL Adobe Commerce as a Cloud Service] -instantie en andere niet-productieomgevingen. De [!DNL AEM Assets] Production-instantie verwijst naar uw [!DNL Adobe Commerce as a Cloud Service] Production-instantie.

## IMS-identiteit en Single Sign-On-informatie {#ims-identity-and-sso-config}

Adobe Commerce-identiteitsbeheer en -verificatie worden beheerd door het Adobe Identity Management System (IMS) via de Adobe Admin Console.

Voor informatie over de opties van de identiteitsconfiguratie met inbegrip van Adobe ID, Enterprise ID, en Federated ID, en instructies voor het vormen Enige Sign-On (SSO) voor veilige toegang tot Adobe apps, zie [ de identiteit van de Opstelling en Enige Sign-On ](https://helpx.adobe.com/enterprise/using/set-up-identity.html) in de *Admin Console van de Onderneming* documentatie.

## ACCS-services en opmerkingen bij de uitbreidingsrelease {#accs-release}

### Aanvullende opmerkingen bij de release

[!DNL Adobe Commerce as a Cloud Service] bevat de meest recente versies van de handelsdiensten, de betalingsdiensten, en de uitbreidingsversies. Gebruik de volgende koppelingen om de releaseopmerkingen voor elke versie weer te geven:

| Services | Uitbreidbaarheid | Storefront |
| --- | --- | --- |
| <ul><li>[ de Dienst van de Catalogus ](../catalog-service/release-notes.md)</li><li>[ Levend Onderzoek ](../live-search/release-notes.md)</li><li>[ de Diensten van de Betaling ](../payment-services/release-notes.md)</li><li>[ Aanbevelingen van het Product ](../product-recommendations/release-notes.md)</li><li>[ de Uitvoer van Gegevens SaaS ](../data-export/release-notes.md)</li></ul> | <ul><li>[ Admin UI SDK ](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/release-notes/)</li><li>[ API Net ](https://developer.adobe.com/graphql-mesh-gateway/mesh/release)</li><li>[ Gebeurtenissen ](https://developer.adobe.com/commerce/extensibility/events/release-notes/)</li><li>[ Webhooks ](https://developer.adobe.com/commerce/extensibility/webhooks/release-notes/)</li></ul> | <ul><li>[ de informatie van de Versie ](https://experienceleague.adobe.com/developer/commerce/storefront/releases/)</li><li>[ Changelog ](https://experienceleague.adobe.com/developer/commerce/storefront/releases/changelog/)</li></ul> |

## Opmerkingen bij de release Adobe Commerce Optimizer Services {#aco-release}

### Aanvullende opmerkingen bij de release

[!DNL Adobe Commerce Optimizer] werkt met de nieuwste releases van AEM Assets-integratie, de Commerce Optimizer-aansluiting en [!DNL Adobe Commerce Storefront] . Gebruik de volgende koppelingen om releaseopmerkingen voor elk gebied weer te geven:

| Services | Storefront |
| --- | --- |
| [ de integratie van AEM Assets ](../aem-assets-integration/release-notes.md)<br>[ schakelaar van Commerce Optimizer ](../aco-connector/release-notes.md) | [ de versieinformatie van de Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/releases/) <br>[ veranderd Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/releases/changelog/) |
