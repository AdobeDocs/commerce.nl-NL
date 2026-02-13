---
title: Opmerkingen bij de release AEM Assets Integration
description: Raadpleeg de releaseopmerkingen voor informatie over alle AEM Assets Integration-releases.
feature: CMS, Media, Release Notes
exl-id: 0d639565-812f-481a-afd6-6e6fa54ed70e
source-git-commit: 56f31a320411c28d267dfd677d36e5ec04f6f2d8
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 0%

---

# Opmerkingen bij de release AEM Assets Integration

Deze releaseopmerkingen beschrijven alle releases voor de AEM Assets-integratie en bevatten:

![ Nieuwe ](../assets/new.svg) Nieuwe eigenschappen
![ Vaste kwestie ](../assets/fix.svg) Oplossingen en verbeteringen
![ Bekende kwestie ](../assets/bug.svg) Bekende kwesties

Voor eigenschapveranderingen en moeilijke situaties die buiten de regelmatige versie van de eigenschapversie worden vrijgegeven, herzie de _Gehoste de dienstupdates_ secties.

Leer meer over aanstaande versies, productsteun, en welke versies van Adobe Commerce de uitbreiding van de Integratie van AEM Assets steunen, zie het programma van de Versie van Adobe Commerce [ ](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) en [ de 3} onderwerpen van de Beschikbaarheid van het Product.](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability)

## Gehoste service-updates

Deze versienota&#39;s beschrijven eigenschapveranderingen en moeilijke situaties die voorkwamen en buiten de regelmatige eigenschapversies voor de ontvangen dienst werden vrijgegeven.

+++Gehoste service-updates

_september 2025_

![ Nieuwe kwestie ](../assets/new.svg) werkte [ douane automatische aanpassing ](https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/synchronize/custom-match){target=_blank} eindpunten met een nieuw `asset_matches` attribuut bij.

_11 Februari, 2025_

![ Nieuwe kwestie ](../assets/new.svg) nu, kunnen de handelaren beelden voor producten en categorieën synchroniseren.

+++

## v1.2.14

_13 Februari, 2026_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACCS-171 --> Vaste a [ de kwestie van de douanematcher ](https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/synchronize/custom-match) waar runtime acties dropdown niet bewaarde werkruimtegegevens na paginaherladen toonde.

## v1.2.13

_10 Februari, 2026_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Nieuwe kwestie ](../assets/new.svg)<!-- Issue ACCS-171 --> voegde een **[!UICONTROL Adobe I/O Workspace Configuration]** gebied toe dat de [ douane aanpassing ](https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/synchronize/custom-match){target=_blank} opstelling vereenvoudigt. Handelaars kunnen nu hun App Builder `workspace.json` -bestand uploaden om automatisch OAuth-referenties en eindpunten van handelingen bij uitvoering in te vullen.

## v1.2.12

_Januari 29, 2026_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1206 --> Vaste een kwestie waar de waliteit `no_selection` waarden in douanekenmerken voor activa rollen niet tijdens activa synchronisatie werden verwijderd, veroorzakend sommige beelden om correct in Edge Delivery Services te tonen.

## v1.2.11

_Januari 15, 2026_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1180 --> verbeterde product uitgeeft pagina door dossiergrootte en dimensies voor de activa van AEM te verbergen aangezien zij dynamisch door CDN worden geoptimaliseerd. Nu, pagina&#39;s correct preender wanneer de integratie van AEM Assets wordt toegelaten.

## v1.2.10

_Januari 12, 2026_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1178 --> een kwestie waar de attributen van de productdouane niet via REST API konden worden bijgewerkt wanneer het product een beeld had en de integratie van AEM Assets werd toegelaten. Aangepaste productkenmerken worden nu correct bijgewerkt via REST API.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1172 --> een kwestie waar de verborgen productbeelden niet zoals verborgen in Admin UI op de product uitgeeft pagina werden getoond. De zichtbaarheidsstatus van de afbeelding wordt nu correct weergegeven.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1170 --> een kwestie waar de productbeelden van AEM Assets niet aan Adobe Commerce wegens een deserialisatiefout werden gesynchroniseerd. Alle afbeeldingskenmerken ( `image` , `small_image` en `swatch_image` ) worden nu op de juiste wijze gesynchroniseerd.

## v1.2.7

_6 November, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1169 --> Vaste een kwestie waar de beelden van de productduimnagel na het toelaten van de integratie van AEM Assets op de **MiniKaart**, **Kaart**, en **Afhandeling** pagina&#39;s werden getoond. Productafbeeldingen worden nu consistent gerenderd op alle pagina&#39;s, zelfs na het vernieuwen van de pagina.

## v1.2.6

_24 oktober, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1163 --> Oplossing een kwestie waar de opeenvolgende verzoeken van de bulkproductupdate de status het volgen vlag konden verlaten die verdere updates verhinderen correct te verwerken. De status wordt nu opnieuw ingesteld, zelfs als een fout optreedt.

## v1.2.5

_22 oktober, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1161 --> Vaste een kwestie waar het bijwerken van de positie van een bestaande beeldafbeelding in Adobe Commerce Admin in een PHP typefout resulteerde.

## v1.2.4

_17 oktober 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1155 --> Verbeterde algemene stabiliteit van douanekenmerken. Aangepaste kenmerken worden nu correct bijgewerkt wanneer asynchrone API&#39;s worden gebruikt.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1074 --> nu, [ product-activa synchronisatie ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-urls#configure-the-base-url){target=_blank} niet ontbreekt wanneer een basis verbindings URL wordt bepaald.

## v1.2.3

_2 Oktober, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1135 --> een kwestie met het bijwerken van productattributen. Productkenmerken worden nu bijgewerkt zoals verwacht en er wordt een geschikte fout geretourneerd in plaats van een 200-reactie als updates mislukken.

## v1.2.2

_18 september, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-1110 --> Verbeterde algemene beeldstabiliteit op mini kart, kar, en controlepagina&#39;s. Afbeeldingen op deze pagina&#39;s worden nu op de juiste wijze geladen.

## v1.2.0

_7 Augustus, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Nieuwe kwestie ](../assets/new.svg)<!-- Issue ACAP-1018 --> nu, kunnen de handelaren de bron voor beeld en media activa kiezen door a [ eigenaar van de Visualisatie ](https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/get-started/setup-synchronization){target=_blank} te selecteren wanneer het vormen van de integratie van Assets van Admin.

![ Nieuwe kwestie ](../assets/new.svg)<!-- Issue ACAP-1078 --> werkte [ douane automatische aanpassing ](https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/synchronize/custom-match){target=_blank} eindpunten met een nieuw `asset_matches` attribuut bij. Dankzij deze wijziging kunt u uw eigen overeenkomende logica implementeren om alle elementen te retourneren die aan een specifieke `productSku` zijn gekoppeld.

## v1.1.2

_11 Juni, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Nieuwe kwestie ](../assets/new.svg)<!-- Issue ACAP-1041 --> Toegevoegde steun voor Adobe Commerce 2.4.8 en PHP 8.4.

## v1.1.0

_23 April, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Nieuwe kwestie ](../assets/new.svg)<!-- Issue ACAP-955 --> nu, a [ Douane URL van het Domein van de Douane ](https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/get-started/setup-synchronization#optional-configure-the-custom-domain-url) kan in plaats van de Levering URL van AEM worden gebruikt. Als een handelaar a **Naam van het Domein van de Douane** in hun dashboard van AEM plaatst, is het noodzakelijk om dit **Domein URL van de Douane** in Commerce toe te voegen.

![ Vaste kwestie ](../assets/fix.svg)<!-- Issue ACAP-987 --> Verbeterde algemene logboeken voor de synchronisatieprocessen van AEM Assets.

## v1.0.22

_Maart 12, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Nieuwe kwestie ](../assets/new.svg)<!-- Issue ACAP-xx --> nu, wordt identiteitskaart van de Cliënt IMS van de selecteur van Assets [ ](https://experienceleague.adobe.com/en/docs/commerce/aem-assets-integration/get-started/setup-synchronization) vereist door de Selecteur van Assets om afbeelding van AEM Assets met productcategorieën en de Bouwer van de Pagina toe te laten geproduceerde inhoud.

## v1.0.20

_11 Februari, 2025_

[!BADGE  Ondersteunde ]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![ Nieuwe ](../assets/new.svg)<!-- Issue ACAP-xx --> Algemene beschikbaarheidsversie.
