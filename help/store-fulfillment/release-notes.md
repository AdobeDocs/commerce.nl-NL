---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Opmerkingen bij de release'
description: Herzie de versienota's voor informatie over alle  [!DNL Store Fulfillment by Walmart Commerce Technologies]  versies.
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# Aanvullende informatie

Deze releaseopmerkingen beschrijven de eerste versie van [!DNL Store Fulfillment Services by Walmart Commerce Technologies] en bevatten:

![ Nieuwe ](../assets/new.svg) Nieuwe eigenschappen
![ Vaste kwestie ](../assets/fix.svg) Oplossingen en verbeteringen
![ Bekende kwestie ](../assets/bug.svg) Bekende kwesties

Zie [ Komende Versies ](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) om over versieschema&#39;s en steun te leren.

Zie [ Beschikbaarheid van het Product ](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) om te leren welke versies van Adobe Commerce deze uitbreiding steunen.

## v1.5.0

*3 Augustus, 2023*

[!BADGE  Gesteund ]{type=Informative tooltip="Ondersteund"}[ Adobe Commerce 2.4.4 aan 2.4.6 ](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), met inbegrip van 2.4.6-p1, 2.4.5-p3, en 2.4.4-p4 de veiligheidsflardversies

Deze release bevat de volgende updates:

![ Nieuw ](../assets/fix.svg) werkte de uitbreiding bij om [ de veiligheidsflardversies van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1, 2.4.5-p3, en 2.4.4-p4 te steunen.

![ Nieuwe ](../assets/new.svg)<!-- WMTP-918 --> Toegevoegde steun voor de [ Asynchrone verzendende ](sales-emails.md) configuratieoptie voor Verkoop E-mail. Handelaars die een upgrade naar versie 1.5.0 uitvoeren, kunnen e-mailberichten direct (standaard) of asynchroon verzenden.

![ Nieuw ](../assets/new.svg)<!-- WMTP-916--> werkte de [ Bronconfiguratie ](merchant-store-configuration.md) bij om internationale formaten van het telefoonaantal te steunen.

![ Nieuwe ](../assets/new.svg) Toegevoegde logica om restitutiebedragen te verhinderen het resterende of gefactureerde bedrag te overschrijden.

![ Nieuw ](../assets/new.svg)<!-- WMTP-882 --> Vervangen `google.map.LatLng` voorwerp met literals JSON om verenigbaarheid met oudere versies van [!DNL Google Maps] te steunen.

![ Vaste kwestie ](../assets/fix.svg)<!-- WMTP- --> werkte het manuscript bij dat tot de `[!DNL Available for Store Pickup]` en `[!DNL Available for Home Delivery]` productattributen leidt om attributencategorieconflict te verhinderen.

![ Vaste kwestie ](../assets/fix.svg)<!-- WMTP-915 --> een verenigbaarheidskwestie die een eindeloze lijn veroorzaakte toen het laden van en het opslaan van sommige entiteiten.

![ Vaste kwestie ](../assets/fix.svg)<!-- WMTP-921 --> Vaste een kwestie die [!DNL Ship to Store] citaatbevestiging verhinderde teweegbrengen wanneer een punt aan de kar van een productdetailpagina (PDP) wordt toegevoegd.

![ Vaste kwestie ](../assets/fix.svg)<!-- WMTP- 932 --> Vaste een controlekwestie die klanten toestond om de methode van de huislevering voor punten te selecteren die niet geschikt voor huislevering zijn.

![ de updates van de 1} Installatie van de Vaste kwestie ](../assets/fix.svg):

- <!-- WMTP-880--> Probleem verholpen waarbij een onjuiste websitecode werd geretourneerd tijdens de installatie van de extensie [!DNL Store Fulfillment] .

- <!-- WMTP-878--> Probleem verholpen met betrekking tot SKU-gehele getallen waarbij het gegevenstype tijdens de installatie naar tekenreekstype moest worden gecast.

![ Vaste kwestie ](../assets/fix.svg)<!-- WMTP-915--> een mislukking die door ontbrekende Check-in foutencode wordt veroorzaakt.

![ Vaste kwestie ](../assets/fix.svg)<!-- WMTP-932 --> Vaste een insect met betrekking tot gedeeltelijke verwerping tijdens afstotingsverrichtingen.

![ Nieuw ](../assets/new.svg)<!-- WMTP-953 --> werkte het Cancel API eindpunt bij om de statusparameter als facultatief voorwerp te verbruiken.

![ Nieuwe ](../assets/new.svg)<!-- WMTP-960 --> Verbeterde registrerendetails voor het punt van de Verkoop API.

## v1.4.0

*13 april 2023*

[!BADGE  Gesteund ]{type=Informative tooltip="Ondersteund"}

![ Nieuw ](../assets/fix.svg) [!DNL Store Fulfillment] is nu [ compatibel met  [!DNL Adobe Commerce]  2.4.4 aan 2.4.6 ](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*27 Februari, 2023*

[!BADGE  Gesteund ]{type=Informative tooltip="Ondersteund"}

Deze release bevat de volgende update:

![ Nieuw ](../assets/fix.svg)<!-- WMTP-795 --> voegde het vermogen toe om de oplossing van de Afhandeling van de Opslag voor een specifieke plaats onbruikbaar te maken door het standaardwerkingsgebied voor het plaatsen van de Configuratie van het Systeem van website aan globaal te veranderen.

## v1.2.0

*27 September, 2022*

[!BADGE  Gesteund ]{type=Informative tooltip="Ondersteund"}

Deze release bevat de volgende update:

![ Nieuw ](../assets/fix.svg) [!DNL Store Fulfillment] is nu [ compatibel met  [!DNL Adobe Commerce]  2.4.4 aan 2.4.5 ](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*15 juli 2022*

[!BADGE  Gesteund ]{type=Informative tooltip="Ondersteund"}

Stabiliteit: algemene beschikbaarheid

![ Nieuw ](../assets/fix.svg)<!-- WMTP-731 --> Vereenvoudigde de [ Controle-in ervaringsconfiguratie ](check-in-experience-setup.md) voor de Winkel bijstaat app door standaardauto toe te voegen maakt en modelselecties. In de vorige versie moesten handelaren de selecties van het merk en het model van de auto handmatig configureren.

## v1.0.0

*Maart 4, 2022*

[!BADGE  Gesteund ]{type=Informative tooltip="Ondersteund"}

Stabiliteit: algemene beschikbaarheid

## App Winkelassistentie

Voor informatie over nieuwe versies van de Winkel bijstaat app, zie de toepassingsinformatie in [ Apple App Store ](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539) {target="_blank"} of [ de opslag van Google Play ](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist) {target="_blank"}.
