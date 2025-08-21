---
title: Gedragsgebeurtenissen
description: Leer welke gegevens elke gedraggebeurtenis vastlegt.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bcabccc9-8a2e-4045-9306-1d999bb75624
source-git-commit: 631dfacd26a333e70a70f354d191d256d90d946f
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# [!DNL Data Connection] Gedragsgebeurtenissen

In het volgende voorbeeld worden de Commerce-gedragsgebeurtenissen weergegeven die beschikbaar zijn wanneer u de extensie [!DNL Data Connection] installeert. De gegevens die deze gebeurtenissen verzamelen, worden naar de Adobe Experience Platform verzonden. U kunt [ douanegebeurtenissen ](custom-events.md) ook tot stand brengen om extra gegevens te verzamelen die niet uit de doos worden verstrekt.

Naast de gegevens verzamelen de volgende gebeurtenissen zich, krijgt u ook [ andere gegevens ](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) die door het Web SDK van Adobe Experience Platform worden verstrekt.

De gedragsgebeurtenissen verzamelen geanonimiseerde gedragsgegevens van uw kopers wanneer ze door uw site bladeren. U kunt de gegevens die deze gebeurtenissen verzamelen gebruiken om promoties en campagnes te maken voor een specifieke groep kopers.

>[!NOTE]
>
>Alle gedragsgebeurtenissen omvatten het [`identityMap` ](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) gebied, dat het e-mailadres van de verkoopster, indien beschikbaar, en ECID omvat.

## Gebeurtenissen van Storefront

Storefront-gebeurtenissen leggen gegevens vast van de interacties van kopers op de site en bevatten gebeurtenissen zoals `addToCart` , `pageView` , `createAccount` , `editAccount` , `startCheckout` , `completeCheckout` , `signIn` , `signOut` , enzovoort. De gebeurtenissen van het winkelfront zijn op eenvoudige en configureerbare slechts producten van toepassing.

Zie de [ ontwikkelaardocumentatie ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#data-connection) om meer over storefront gebeurtenissen te leren.

## Klantprofielgebeurtenissen

Profielgebeurtenissen die zijn vastgelegd vanuit de storefront, bevatten accountinformatie, zoals `signIn` , `signOut` , `createAccount` en `editAccount` . Deze gegevens worden gebruikt om belangrijke klantendetails te bevolken die nodig zijn om segmenten beter te bepalen of marketing campagnes, zoals het verzenden van aanbiedingen van de inschrijvingskorting, bevestigingen van de rekeningsverandering, etc. uitvoeren.

Zie de [ documentatie van de ontwikkelaar ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#data-connection) om meer over de gebeurtenissen van het klantenprofiel te leren.

## Zoeken in gebeurtenissen

De zoekgebeurtenissen bevatten gegevens die relevant zijn voor de intentie van de klant. Met insight in de intentie van een winkelier kunnen verkopers zien hoe kopers objecten zoeken, waarop ze klikken en op termijn kopen of verlaten. Een voorbeeld van hoe u deze gegevens kunt gebruiken is als u bestaande kopers wilt richten die naar uw topproduct zoeken, maar nooit het product kopen. U moet de extensie [[!DNL Live Search]](../live-search/install.md) installeren om toegang te krijgen tot deze gebeurtenissen.

Gebruik de velden `searchRequest.id` en `searchResponse.id` in de gebeurtenissen `searchRequestSent` en `searchResponseReceived` om een zoekaanvraag te doorverwijzen naar de corresponderende zoekreactie.

Zie de [ ontwikkelaardocumentatie ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#data-connection) om meer over onderzoeksgebeurtenissen te leren.

## B2B-gebeurtenissen

![ B2B voor Adobe Commerce ](../assets/b2b.svg) voor B2B handelaren, moet u [ ](install.md#install-the-b2b-extension) de `experience-platform-connector-b2b` uitbreiding installeren om tot deze gebeurtenissen toegang te hebben.

De B2B gebeurtenissen bevatten [ informatie van de 0} verzoeklijst {, zoals als een verzoeklijst werd gecreeerd, aan, of geschrapt van werd toegevoegd. ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) Door gebeurtenissen te volgen specifiek voor aanvraaglijsten, kunt u zien welke producten uw klanten vaak kopen en campagnes tot stand brengen die op die gegevens worden gebaseerd.

Zie de [ ontwikkelaardocumentatie ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#data-connection) om meer over gebeurtenissen te leren B2B.
