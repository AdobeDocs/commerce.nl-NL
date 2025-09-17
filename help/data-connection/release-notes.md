---
title: Aanvullende informatie
description: De recentste versieinformatie voor de  [!DNL Data Connection]  uitbreiding van Adobe Commerce.
feature: Personalization, Integration, Release Notes
exl-id: f3b92632-947d-40cd-89b7-24ed0680be51
source-git-commit: 9c10aecb303dd09a85bdafa93d791d30611ec8b2
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Aanvullende informatie

>[!IMPORTANT]
>
>De naam van de Experience Platform-connector is gewijzigd in [!DNL Data Connection] .

Deze releaseopmerkingen bevatten updates van de extensie [!DNL Data Connection] en bevatten:

![ Nieuw ](../assets/new.svg) - Nieuwe eigenschappen
![ Repareren ](../assets/fix.svg) - Oplossingen en verbeteringen
![ Bug ](../assets/bug.svg) - Bekende kwesties

Voor eigenschapveranderingen en moeilijke situaties met betrekking tot uitbreidingen die door de [!DNL Data Connection] uitbreiding worden gebruikt, zie **Ondersteunde de dienstupdates**.

Zie [ Komende Versies ](https://experienceleague.adobe.com/nl/docs/commerce-operations/release/planning/schedule) om over versieschema&#39;s en steun te leren.

Zie de ontwikkelaardocumentatie aan [ leren welke versies van Commerce deze module ](https://experienceleague.adobe.com/nl/docs/commerce-operations/release/product-availability) steunen.

## Ondersteunde service-updates

In deze releaseopmerkingen worden wijzigingen in de functies beschreven en oplossingen gevonden voor extensies die worden gebruikt door de extensie [!DNL Data Connection] .

+++Ondersteunde service-updates

_7 Augustus, 2025_

![ Nieuw ](../assets/new.svg) - met de 3.3.0 versie, kunt u [ douaneattributen aan profielen ](custom-identities.md) nu toevoegen.

_Augustus 2, 2024_

![ Bevestig ](../assets/fix.svg) - Vaste het totale bedrag van betalingen wanneer het ordertotaal wordt gevormd om belastingen te omvatten.
![ Nieuw ](../assets/new.svg) - Toegevoegd a `taxAmount` gebied aan de gebeurtenissen van de ordeaankoop.
![ Nieuw ](../assets/new.svg) - voegde de capaciteit toe om douanegegevens aan gebeurtenissen toe te voegen. Zie het volgende voor een [ voorbeeld ](https://github.com/adobe/commerce-events/blob/main/examples/events/custom-event-override.md).

_Januari 24, 2024_

![ Nieuw ](../assets/new.svg) - werkte de `data-services-b2b` uitbreiding bij om een nieuwe vraaggebeurtenis te omvatten die `deleteRequisitionList` voor B2B handelaren wordt geroepen.

_16 november 2023_

![ bevestig ](../assets/fix.svg) - Vloeiende een kwestie waar een foutenmelding verkeerd verscheen wanneer u een orde plaatste die veelvoudige verschepende adressen had.
![ bevestig ](../assets/fix.svg) - een kwestie in de `productPageView` gebeurtenis waar het `productListItems.priceTotal` gebeurtenisgebied niet de prijs na het schakelen van de munt op de archiefmening omzet.
![ bevestig ](../assets/fix.svg) - een kwestie in het `productListItems` gebeurtenisgebied waar de muntcode niet bijwerkte toen handelaars de archiefmening veranderde.

_10 oktober, 2023_

![ Nieuw ](../assets/new.svg) - Toegevoegde nieuwe gebeurtenissen van de ordestatus: [ Gecodeerde orde ](events-backoffice.md#orderinvoiced), [ Terugkeer van het Punt van de Orde die ](events-backoffice.md#orderitemsreturninitiated) wordt geïnitieerd, en [ Terugkeer van het Punt van de Orde voltooide ](events-backoffice.md#orderitemreturncompleted).
![ Bevestig ](../assets/fix.svg) - Vaste een kwestie waar de veranderingen van de muntconfiguratie niet in de gebeurtenissen na het verfrissen van het geheime voorgeheugen werden weerspiegeld.
![ Repareren ](../assets/fix.svg) - Vaste fout wanneer het bericht van de ordesbevestiging niet verschijnt als de asynchrone ordeplaatsing wordt toegelaten.
![ Nieuw ](../assets/new.svg) - Toegevoegde gegevens aan `addToRequisitionList` gebeurtenis voor eenvoudige producten op de de meningspagina van de Categorie.
![ bevestig ](../assets/fix.svg) - een kwestie in de `selectedOptions` gegevens in de `addToRequisitionList` gebeurtenis opgelost wanneer de producten van de bevestigingspagina van de Orde worden toegevoegd.
![ Nieuw ](../assets/new.svg) - Toegevoegde productgegevens aan `addToRequisitionList` gebeurtenis wanneer de producten aan de verzoeklijst van de de meningspagina van de Categorie worden toegevoegd.
![ Nieuw ](../assets/new.svg) - Toegevoegde `addToRequisitionList` gebeurtenis wanneer de configureerbare producten aan de verzoeklijst van de de meningspagina van het Product worden toegevoegd.
![ Nieuw ](../assets/new.svg) - Toegevoegde `addToRequisitionList` en `removeFromRequisitionList` gebeurtenissen wanneer het productaantal van een verzoeklijst wordt verhoogd en/of verminderd.

_10 Juni, 2023_

![ bevestig ](../assets/fix.svg) - een kwestie opgelost toen `orderId` niet in de context wegens prefixen in het de ordeherkenningsteken van Commerce overging.
![ bevestig ](../assets/fix.svg) - de bijgewerkte configuraties van het Beleid van de Veiligheid van de Inhoud.

_Maart 30, 2023_

![ Nieuw ](../assets/new.svg) - Toegevoegde een uitbreiding riep `data-services-b2b` die [ gebeurtenissen van de verzoeklijst ](events.md#b2b-events) voor B2B handelaren omvat.
![ Nieuw ](../assets/new.svg) - voegde het `uniqueIdentifier` gebied aan [ onderzoek ](events.md#search-events) gebeurtenissen toe. Met dit nieuwe veld kunnen verkopers zoekopdrachten en zoekreacties doorzoeken.

_12 oktober 2022_

![ Nieuw ](../assets/new.svg) - voegde twee [ storefront gebeurtenissen ](events.md) toe, `openCart` en `removeFromCart`, aan de Gebeurtenissen SDK en de Collector van Adobe Commerce Storefront.
![ Nieuw ](../assets/new.svg) - toegevoegde steun voor een [ AEM storefront ](overview.md#aem-support).

+++

## 3.4.0.

_16 September, 2025_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) [!DNL Data Connection] respecteert nu volledig de wijze van de koekjesbeperking door gegevensinzameling en opslag in koekjes/lokale opslag te verhinderen wanneer de beperkingen worden toegelaten.

## 3.3.0.

_Maart 21, 2025_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuwe ](../assets/new.svg) Toegevoegde PHP 8.4 steun.

## 3.2.1.

_Januari 17, 2025_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) - voegde de [ HIPAA-klaar uitbreiding ](hipaa-readiness.md) aan [!DNL Data Connection] toe zodat kunnen de handelaren [!DNL Commerce] gegevens van de achterkantoorgebeurtenis met Experience Platform delen en naleving van HIPAA handhaven.
![ bevestig ](../assets/fix.svg) - Vloeiende een kwestie waar de [!DNL Data Connection] uitbreiding `eventForwarding` gegevens en het plaatsen van de `HIPAA` vlag voor alle klanten met voeten trad. Nu plaatst de uitbreiding slechts de vlag voor klanten HIPAA.

## 3.2.0.

_7 Oktober, 2024_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) - Toegevoegde capaciteit om [ attributen van de douaneorde ](custom-attributes.md) aan achterbureaugegevens tot stand te brengen.
![ Nieuw ](../assets/new.svg) - Toegevoegde nieuwe [ Lijst van de Attributen van de Orde van de Douane ](connect-data.md#data-customization) om u te helpen om het even welke douanekenmerken bekijken die in [!DNL Commerce] worden gevormd en naar Experience Platform worden verzonden.
![ Nieuw ](../assets/new.svg) - Toegevoegde capaciteit om [ profielverslagen ](connect-data.md#send-customer-profile-data) en gegevens te verzamelen en te verzenden naar Experience Platform.

## 3.2.0-bèta3

_Augustus 27, 2024_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) - als u aan bèta deelneemt, zorg ervoor uw `composer.json` dossier het volgende op het wortelniveau heeft: ` "minimum-stability": "beta"`. Voeg ook `composer require "magento/customers-connector: ^1.2.0"` toe om klantprofielen van uw Commerce-exemplaar naar SaaS te verzenden.
![ Nieuw ](../assets/new.svg) - Deze versie bevat de flarden die in 3.1.1, 3.1.2, 3.1.3, en 3.1.4 worden vrijgegeven.

## 3.1.4.

_9 augustus, 2024_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Repareren ](../assets/fix.svg) - werkte het `experience-platform-connector` metapakket bij om extra ongebruikte gegevensexporteurs en indexeerders te verwijderen.

## 3.1.3

_22 Juli, 2024_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Repareren ](../assets/fix.svg) - werkte het `experience-platform-connector` metapakket bij om ongebruikte gegevensexporteurs en indexeerders te verwijderen.

## 3.1.2.

_5 Juni, 2024_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Bevestig ](../assets/fix.svg) - Vaste een kwestie waar het verkeerde datumformaat werd gebruikt toen het in werking stellen van a [ historische synchronisatie ](connect-data.md#specify-order-history-date-range).
![ bevestig ](../assets/fix.svg) - Vloeiende een kwestie waar de `startCheckout` gebeurtenis niet op Adobe Commerce 2.4.7 werd verzonden.

## 3.1.1

_4 April, 2024_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) - Toegevoegde steun voor PHP 8.3 voor alle [!DNL Data Connection] uitbreidingen.
![ Nieuw ](../assets/new.svg) - toegevoegd artikel over hoe te [&#128279;](mobile-sdk-epc.md) Adobe Experience Platform Mobile SDK met Commerce integreren.

## 3.2.0-bèta2

_Maart 4, 2024_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) - als u aan bèta deelneemt, zorg ervoor uw `composer.json` dossier het volgende op het wortelniveau heeft: ` "minimum-stability": "beta"`. Voeg ook `composer require "magento/customers-connector: ^1.2.0"` toe om klantprofielen van uw Commerce-exemplaar naar SaaS te verzenden.
![ Nieuw ](../assets/new.svg) - Toegevoegde capaciteit om [ douanekenmerken ](custom-attributes.md) toe te voegen.
![ Nieuw ](../assets/new.svg) - Toegevoegde capaciteit om [ profielverslagen ](connect-data.md#send-customer-profile-data) en gegevens te verzamelen en te verzenden naar Experience Platform.

## 3.1.0.

_16 november 2023_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

![ Nieuw ](../assets/new.svg) - de schakelaar van Experience Platform is anders genoemd aan [!DNL Data Connection].
![ Repareren ](../assets/fix.svg) - Toegevoegde capaciteit om foutenreactie te registreren als IMS van Adobe niet het toegangstoken kan produceren.
![ Repareren ](../assets/fix.svg) - voegde een berichtbericht toe als u probeert om Historische Orden te synchroniseren maar geen rekeningsgeloofsbrieven hebben gespecificeerd.

## 3.0.0.

_10 oktober, 2023_

[!BADGE &#x200B; Verenigbaarheid &#x200B;]{type=Informative tooltip="Compatibiliteit"} versies van Adobe Commerce 2.4.4 en nieuwer

Dit is een belangrijke versie. [ geeft ](install.md#update-the-data-connection) het wortel composer.json- dossier van uw project uit.

![ Nieuw ](../assets/new.svg) - Algemene beschikbaarheid om [ historische orde ](connect-data.md#send-historical-order-data) gegevens en status naar Experience Platform te verzenden.
![ Nieuw ](../assets/new.svg) - Toegevoegde steun voor OAuth 2.0 wanneer u [&#128279;](connect-data.md#connect-commerce-data-to-adobe-experience-platform) de [!DNL Data Connection] uitbreiding vormt.
![ Nieuw ](../assets/new.svg) - Eind steun voor Adobe Commerce 2.4.3.

## 2.3.0.

_Juni 27, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.3 en nieuwer

![ Nieuw ](../assets/new.svg) - Toegevoegde capaciteit aan [ draai van het verzenden van storefront gebeurtenissen ](connect-data.md#data-collection) aan Experience Platform.
![ bevestig ](../assets/fix.svg) - de bijgewerkte configuraties van het Beleid van de Veiligheid van de Inhoud.
![ Repareren ](../assets/fix.svg) - Vaste steun voor achterbureaugebeurtenissen op Commerce 2.4.7 versie.
![ Nieuw ](../assets/new.svg) - voegde een berichtbericht over geheim voorgeheugenongeldigheid toe wanneer u veranderingen in de [!DNL Data Connection] uitbreidingsvorm opslaat.

## 3.0.0-bèta1 (alleen intern)

_13 Juni, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.3 en nieuwer

![ Nieuw ](../assets/new.svg) - (Beta) Toegevoegde capaciteit om [ historische orde ](connect-data.md#beta-send-historical-order-data) gegevens en status naar Experience Platform te verzenden.

## 2.2.0.

_Maart 30, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.3 en nieuwer

![ Nieuw ](../assets/new.svg) - Bundelde `commerce-data-export` en `saas-export` gebiedsdelen met de `experience-platform-connector` uitbreiding. Eerder, moest u deze gebiedsdelen afzonderlijk installeren. Deze gebiedsdelen, samen met handelaarconfiguratie, laten server-zijverwerking van [ achterbureaugebeurtenissen ](events-backoffice.md) toe.
![ Nieuw ](../assets/new.svg) - Toegevoegde nieuwe geroepen backoffice gebeurtenis [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1.

_28 februari, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.3 en nieuwer

![ Nieuw ](../assets/new.svg) - Toegevoegde steun voor PHP 8.2 voor alle [!DNL Data Connection] uitbreidingen.

## 2.1.0.

_Januari 17, 2023_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.3 en nieuwer

![ Nieuw ](../assets/new.svg) - werkte [[!DNL Data Connection]  uitbreiding Admin ](connect-data.md) bij zodat kunt u uw eigen SDK van het Web van AEP (legering) specificeren.
![ Repareren ](../assets/fix.svg) Veranderde in het gebruiken `identityMap` in plaats van `personID` toen het plaatsen van de primaire identiteit voor om het even welke gegevens die aan de rand worden geduwd.

## 2.0.1.

_10 November, 2022_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.3 en nieuwer

![ Bevestig ](../assets/fix.svg) - nu wordt de context van Adobe Experience Platform geplaatst slechts nadat de Collector van de Gebeurtenis Storefront en de Gebeurtenis SDK met succes worden geladen.

## 2.0.0.

_12 oktober 2022_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.3 en nieuwer

![ Nieuw ](../assets/new.svg) - Toegevoegde capaciteit om uw eigen SDK van het Web van AEP te specificeren wanneer [ verbindend ](connect-data.md) uw instantie van Adobe Commerce met Experience Platform.
![ Repareren ](../assets/fix.svg) - de bijgewerkte vereisten van het gegevensstroomwerkingsgebied zodat datastream IDs aan de website eerder dan storeview moet worden behandeld.

## 1.0.0.

_9 augustus, 2022_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versies van Adobe Commerce 2.4.3 en nieuwer

![ Nieuw ](../assets/new.svg) - Algemene beschikbaarheidsversie.
