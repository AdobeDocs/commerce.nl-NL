---
title: Opmerkingen bij de release AEM Assets Integration
description: Raadpleeg de releaseopmerkingen voor informatie over alle AEM Assets Integration-releases.
feature: CMS, Media, Release Notes
exl-id: 0d639565-812f-481a-afd6-6e6fa54ed70e
source-git-commit: 141f2291d1ead324a159053145e92ee7d4237a7d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Opmerkingen bij de release AEM Assets Integration

In deze releaseopmerkingen wordt de eerste release van AEM Assets Integration beschreven en staan onder andere:

![&#x200B; Nieuwe &#x200B;](../assets/new.svg) Nieuwe eigenschappen
![&#x200B; Vaste kwestie &#x200B;](../assets/fix.svg) Oplossingen en verbeteringen
![&#x200B; Bekende kwestie &#x200B;](../assets/bug.svg) Bekende kwesties

Voor eigenschapveranderingen en moeilijke situaties die buiten de regelmatige versie van de eigenschapversie worden vrijgegeven, herzie de _Gehoste de dienstupdates_ secties.

Leer meer over aanstaande versies, productsteun, en welke versies van Adobe Commerce de uitbreiding van de Integratie van AEM Assets steunen, zie het programma van de Versie van Adobe Commerce [&#x200B; &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/release/planning/schedule) en [&#x200B; de 3&rbrace; onderwerpen van de Beschikbaarheid van het Product.](https://experienceleague.adobe.com/nl/docs/commerce-operations/release/product-availability)

## Gehoste service-updates

Deze versienota&#39;s beschrijven eigenschapveranderingen en moeilijke situaties die voorkwamen en buiten de regelmatige eigenschapversies voor de ontvangen dienst werden vrijgegeven.

+++Gehoste service-updates

_september 2025_

![&#x200B; Nieuwe kwestie &#x200B;](../assets/new.svg) werkte [&#x200B; douane automatische aanpassing &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/aem-assets-integration/synchronize/custom-match){target=_blank} eindpunten met een nieuw `asset_matches` attribuut bij.

_11 Februari, 2025_

![&#x200B; Nieuwe kwestie &#x200B;](../assets/new.svg) nu, kunnen de handelaren beelden voor producten en categorieën synchroniseren.

+++

## v1.2.4

_17 oktober 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![&#x200B; Vaste kwestie &#x200B;](../assets/fix.svg)<!-- Issue ACAP-1155 --> Verbeterde algemene stabiliteit van douanekenmerken. Aangepaste kenmerken worden nu correct bijgewerkt wanneer asynchrone API&#39;s worden gebruikt.

## v1.2.3

_2 Oktober, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![&#x200B; Vaste kwestie &#x200B;](../assets/fix.svg)<!-- Issue ACAP-1135 --> een kwestie met het bijwerken van productattributen. Productkenmerken worden nu bijgewerkt zoals verwacht en er wordt een geschikte fout geretourneerd in plaats van een 200-reactie als updates mislukken.

## v1.2.2

_18 september, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![&#x200B; Vaste kwestie &#x200B;](../assets/fix.svg)<!-- Issue ACAP-1110 --> Verbeterde algemene beeldstabiliteit op mini kart, kar, en controlepagina&#39;s. Afbeeldingen op deze pagina&#39;s worden nu op de juiste wijze geladen.

## v1.2.0

_7 Augustus, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![&#x200B; Nieuwe kwestie &#x200B;](../assets/new.svg)<!-- Issue ACAP-1018 --> nu, kunnen de handelaren de bron voor beeld en media activa kiezen door a [&#x200B; eigenaar van de Visualisatie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/aem-assets-integration/get-started/setup-synchronization){target=_blank} te selecteren wanneer het vormen van de integratie van Assets van Admin.

![&#x200B; Nieuwe kwestie &#x200B;](../assets/new.svg)<!-- Issue ACAP-1078 --> werkte [&#x200B; douane automatische aanpassing &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/aem-assets-integration/synchronize/custom-match){target=_blank} eindpunten met een nieuw `asset_matches` attribuut bij. Dankzij deze wijziging kunt u uw eigen overeenkomende logica implementeren om alle elementen te retourneren die aan een specifieke `productSku` zijn gekoppeld.

## v1.1.2

_11 Juni, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![&#x200B; Nieuwe kwestie &#x200B;](../assets/new.svg)<!-- Issue ACAP-1041 --> Toegevoegde steun voor Adobe Commerce 2.4.8 en PHP 8.4.

## v1.1.0

_23 April, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![&#x200B; Nieuwe kwestie &#x200B;](../assets/new.svg)<!-- Issue ACAP-955 --> nu, a [&#x200B; Douane URL van het Domein van de Douane &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/aem-assets-integration/get-started/setup-synchronization#optional-configure-the-custom-domain-url) kan in plaats van de Levering URL van AEM worden gebruikt. Als een handelaar a **Naam van het Domein van de Douane** in hun dashboard van AEM plaatst, is het noodzakelijk om dit **Domein URL van de Douane** in Commerce toe te voegen.

![&#x200B; Vaste kwestie &#x200B;](../assets/fix.svg)<!-- Issue ACAP-987 --> Verbeterde algemene logboeken voor de synchronisatieprocessen van AEM Assets.

## v1.0.22

_Maart 12, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![&#x200B; Nieuwe kwestie &#x200B;](../assets/new.svg)<!-- Issue ACAP-xx --> nu, wordt identiteitskaart van de Cliënt IMS van de selecteur van Assets [&#x200B; &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/aem-assets-integration/get-started/setup-synchronization) vereist door de Selecteur van Assets om afbeelding van AEM Assets met productcategorieën en de Bouwer van de Pagina toe te laten geproduceerde inhoud.

## v1.0.20

_11 Februari, 2025_

[!BADGE &#x200B; Ondersteunde &#x200B;]{type=Informative tooltip="Ondersteund"} versie 2.4.5 van Adobe Commerce en recentere versies.

![&#x200B; Nieuwe &#x200B;](../assets/new.svg)<!-- Issue ACAP-xx --> Algemene beschikbaarheidsversie.
