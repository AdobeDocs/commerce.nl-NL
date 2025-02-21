---
title: Creeer een publiek in Real-Time CDP gebruikend  [!DNL Commerce]  gebeurtenisgegevens
description: Leer hoe te om  [!DNL Commerce]  gebeurtenisgegevens te gebruiken om een publiek in Real-Time CDP te creëren
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# Soorten publiek maken in Real-Time CDP met behulp van [!DNL Commerce] gebeurtenisgegevens

Gebruik gebeurtenisgegevens die zijn vastgelegd in uw [!DNL Commerce] -winkel om een publiek te maken in Real-Time CDP. De vastgelegde gegevens zijn gebaseerd op browsergedrag, aankopen in het verleden, profielkenmerken, eigenschappen die moeten worden omgezet of omgezet in een churn, loyaliteitsstatus, hoge en lage klantwaarde en meer.

## Welke gegevens moet ik overwegen te gebruiken?

Maak een publiek in Real-Time CDP met gegevens van winkel-, back-office- en profielgebeurtenissen.

| Gegevenstypen | Storefront-gegevens (gedragsgebeurtenissen) | Back Office-gegevens (server-side gebeurtenissen) | Klantprofiel en segmentgegevens |
|---|---|---|---|
| **Definitie** | Klik of acties die klanten op uw site uitvoeren. | Informatie over de levenscyclus en details van elke bestelling (verleden en huidig). | Wie zijn de kopers en voor welke segmenten komen ze in aanmerking? |
| **Gebeurtenissen die door Adobe Commerce** worden gevangen | [ productPageView ](events.md#productpageview)<br>[ addToCart ](events.md#addtocart) | [ placeOrder ](events.md#completecheckout)<br>[ geplaatst ](events-backoffice.md#orderplaced)<br>[ orderLineItemRefunded ](events-backoffice.md#orderlineitemrefunded)<br>[ orde Geannuleerde ](events-backoffice.md#ordercancelled)<br>[ orde geschiedenis ](connect-data.md#send-historical-order-data) | [ createAccount ](events.md#createaccount)<br>[ editAccount ](events.md#editaccount)<br>[ Verslag van het Profiel ](events-profilerecord.md) |

## Wat hebben andere klanten bereikt?

Adobe [!DNL Commerce]-klanten hebben belangrijke zakelijke effecten bereikt door in Real-Time CDP ingebouwde soorten publiek te activeren en deze te implementeren in hun [!DNL Commerce] -exemplaar.

Een wereldwijde, multibrand-kledinghandelaar bereikte:

- Één bron van waarheid met 10 s van miljoenen verenigde klantenprofielen
- 40+ unieke doelgroepen van &quot;klanten met hoge intentie&quot; gemaakt voor deelname aan verschillende kanalen

Een wereldwijd drankenbedrijf verzamelde:

- 98 miljoen klantprofielen uit meer dan 100 landen

## Laten we beginnen

In dit artikel leert u hoe u:

- Een publiek maken in Real-Time CDP op basis van de [!DNL Commerce] -gegevens die de gebeurtenissen verzamelen
- Activeer dat publiek voor uw [!DNL Commerce] -winkel
- Gebruik het publiek in [!DNL Commerce] om een regel voor de winkelwagenprijs op te geven

>[!IMPORTANT]
>
>Voltooi de in dit artikel beschreven taken met behulp van de [!DNL Commerce] -sandboxomgeving. Zo zorgt u ervoor dat de gegevens van de winkel- en back-office-gebeurtenis die u naar Experience Platform verzendt, uw productiegebeurtenisgegevens niet verwateren.

### Vereisten

Voordat u begint, controleert u of:

- U bent ingericht om Real-Time CDP te gebruiken. Als u niet zeker bent, raadpleegt u uw systeemintegrator of ontwikkelingsteam dat projecten en omgevingen beheert.
- U [ installeerde ](install.md) en [ vormde ](connect-data.md) de [!DNL Data Connection] uitbreiding in [!DNL Commerce].
- U [ bevestigde ](connect-data.md#confirm-that-event-data-is-collected) dat uw [!DNL Commerce] gebeurtenisgegevens bij de rand van Experience Platform aankomen.

### 1. Een publiek maken

Een publiek is een reeks klanten die gelijkaardig gedrag of kenmerken delen. In deze oefening, creeer u een publiek dat mensen kwalificeert die in een bepaald product van uw winkel geinteresseerd zijn.

Om deze oefening te vereenvoudigen, gebruikt u gebeurtenisgegevens van de [ productPageView ](events.md#productpageview) gebeurtenis. Deze gebeurtenis legt details vast over het product dat is weergegeven, zoals de productnaam, SKU, prijs, enzovoort.

Gebruik deze gebeurtenisgegevens om op te geven dat het publiek personen bevat met ten minste één gebeurtenis &quot;Productweergaven&quot; waarbij de SKU (product-id) gelijk is aan een specifiek product op uw site en de gebeurtenis plaatsvindt binnen de laatste dag. &#x200B;

1. Open Experience Platform en selecteer **[!UICONTROL Audiences]** in het navigatiemenu links.

   ![ Dashboard van de Publiek ](assets/audience-left-rail.png)

1. Klik op **[!UICONTROL Create Audience]**.

   ![ creeer Publiek ](assets/browse-create-audience.png)

   De **werkruimtevertoningen van de Bouwer van het 1} Segment.**

1. In de **werkruimte van de Bouwer van het 1} Segment**, selecteer de **bouwt regel** creatiemethode.

   ![ bouwt Regel ](assets/build-rule.png)

   De **werkruimte van de Bouwer van het Segment** is waar u de regels en de voorwaarden voor uw publiek bepaalt. &#x200B; Deze regels en voorwaarden zijn gebaseerd op gebeurtenis- en profielgegevens uit uw Commerce-winkel en definiëren de criteria die bepalen of een gebruiker voor het publiek in aanmerking komt. U kunt bijvoorbeeld een regel maken die gebruikers bevat die een bepaald product hebben weergegeven, of gebruikers die een aankoop binnen een bepaalde tijdsperiode hebben gedaan. Leer meer over [ de Bouwer van het Segment ](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) en regels en voorwaarden.

1. Selecteer de [ Gebeurtenissen ](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder#events) tabel.

   ![ het Lusje van Gebeurtenissen ](assets/audience-events-tab.png)

1. Zoek naar het gebeurtenistype &quot;Productweergaven&quot;. Dan, sleep en laat vallen het in de **werkruimte van de Bouwer van het 1} Segment**.

1. Keer terug naar het **lusje van Gebeurtenissen** en onderzoek naar &quot;SKU&quot;terug, dat gegevensgebied onder het `productListItems` gebied is. De belemmering en laat vallen het aan de **werkruimte van de Bouwer van het 1} Segment bovenop de** Mening van het Product **gebeurtenis.**

   De **de sectievertoningen van Regels van de Gebeurtenis 0} {waar u het specifieke product kunt specificeren u uw publiek van wilt bouwen.**

   ![ Uitgezochte SKU ](assets/audience-addsku.png)

1. Plaats het tijdinterval aan één dag door op **te klikken om het even welke Tijd** en het selecteren *in laatste* met een waarde van *1*.

   Wanneer het bouwen van een publiek, kunt u een tijdinterval specificeren om recente activiteit te vangen. Door een tijdinterval in te stellen, kunt u gebruikers als doel instellen op basis van hun recente interacties of gedragingen binnen een bepaald tijdsbestek.

1. In de **sectie van de Eigenschappen van het publiek 1} op de rechterkant van de werkruimte, plaats de publiekseigenschappen door een naam, een beschrijving, en een evaluatiemethode voor het publiek te verstrekken.**

1. Klik op **[!UICONTROL Save and Close]** om het publiek op te slaan.

   De details van uw publieksvertoningen op het **dashboard van het publiek 0}.**

### 2. Activeer het publiek naar de [!DNL Commerce] -bestemming

U maakt een publiek beschikbaar in [!DNL Commerce] door het voor de [!DNL Commerce] bestemming te activeren.

>[!IMPORTANT]
>
>Als u niet reeds [!DNL Commerce] als beschikbare bestemming hebt geplaatst om gegevens te ontvangen, zie het [ Adobe  [!DNL Commerce]  3} onderwerp van de Verbinding {.](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-commerce)

1. In het **lusje van Details** van uw publiek, activeert de klik **aan bestemming**.

1. Selecteer de [!DNL Commerce] -bestemming. Dan, klik **daarna**.

1. Voltooi het activeringsproces door op **[!UICONTROL Finish]** te klikken.

## 3. Bekijk het publiek in het dashboard Soorten publiek

In [!DNL Commerce], kunt u alle [ actieve ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations) publiek bekijken dat voor uw [!DNL Commerce] instantie kan worden gepersonaliseerd gebruikend het **publiek van Real-Time CDP** dashboard.

Om tot het **publiek van Real-Time CDP** dashboard toegang te hebben, ga naar _Admin_ sidebar, dan ga **[!UICONTROL Customers]** > **[!UICONTROL Real-time CDP Audience]**.

Zoek in het dashboard naar het publiek dat u hebt gemaakt. Let op: het wordt niet gebruikt in een winkelprijregel of een dynamisch blok. In de volgende sectie koppelt u het publiek aan een regel voor de winkelwagenprijs.

![ het Dashboard van het Soorten Soorten publiek van Real-Time CDP ](assets/real-time-cdp-dashboard.png)

### 4. Maak een regel voor de prijs van een winkelwagentje op basis van het publiek

In deze sectie ziet u hoe u een regel voor de winkelwagenprijs kunt maken op basis van uw nieuwe publiek.

1. Bevestig dat uw nieuw publiek in het **1} dashboard van het Soorten publiek van Real-Time CDP {wordt getoond.**
1. [ creeer een regel van de kartprijs ](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create).
1. [ plaats de voorwaarde ](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#use-real-time-cdp-audiences-to-set-a-condition) van de regel van de wortelprijs gebruikend uw nieuw publiek.
1. [ plaats de actie ](https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-create#step-3-define-the-actions) die u wilt voorkomen wanneer het product aan de kar wordt toegevoegd.
1. Ga door met het configureren van de regel voor de winkelwagenprijs.
1. Ga naar de klantenweergave van uw sandboxinstantie.
1. Voeg het product dat u hebt gemaakt, toe aan de winkelwagen. U ziet dat de prijsregel voor winkelwagentjes is ingeschakeld.

## Bezig met samenvoegen

In deze oefening, creeerde u een publiek in Real-Time CDP en activeerde het aan de [!DNL Commerce] bestemming. Vervolgens hebt u in de [!DNL Commerce] -beheerder op basis van dat publiek een regel voor de winkelwagenprijs gemaakt en de regel in uw sandboxomgeving ingeschakeld.
