---
title: Inleiding tot  [!DNL Product Recommendations]
description: '[!DNL Product Recommendations] is een krachtig marketinginstrument dat u kunt gebruiken om conversies te verhogen, de inkomsten te verhogen en de betrokkenheid van klanten te stimuleren.'
recommendations: noCatalog
badgePaas: label="Alleen PaaS" type="Informative" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."
exl-id: 72850cfd-555c-4e0e-ac3e-097e6dac2030
source-git-commit: 3821893c3df01e2e36ab0142616e52c1c92b4d51
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Inleiding tot [!DNL Product Recommendations]

De aanbevelingen van het product zijn een krachtig marketing hulpmiddel dat u kunt gebruiken om omzettingen te verhogen, opbrengst te verhogen, en winkelbetrokkenheid te stimuleren. De het productaanbevelingen van Adobe Commerce worden aangedreven door [ Adobe Sensei ](https://www.adobe.com/sensei.html), die kunstmatige intelligentie en machine-leert algoritmen gebruikt om een diepe analyse van bijeengevoegde bezoekersgegevens uit te voeren. Als deze gegevens worden gecombineerd met uw Adobe Commerce-catalogus, resulteert dit in een zeer aantrekkelijke, relevante en persoonlijke ervaring.

De aanbevelingen van het product worden getoond op de winkel als eenheden met etiketten, zoals &quot;Klanten die dit product ook bekeken&quot;hebben. U kunt rechtstreeks vanuit Adobe Commerce Admin aanbevelingen maken, beheren en implementeren in uw winkelweergaven.

Als uw opslag gebruikend PWA Studio wordt uitgevoerd, verwijs naar de [ documentatie van PWA ](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Als u een douane frontend technologie zoals React of Vue JS gebruikt, leer hoe te [&#128279;](headless.md) integreren [!DNL Product Recommendations] in uw headless opslag.

>[!NOTE]
>
>Er zijn vele manieren om een headless of douaneimplementatie te ontwikkelen. In deze handleiding wordt een manier beschreven waarop u dit kunt doen met PWA Studio. Zij heeft geen betrekking op alle scenario&#39;s of gebeurtenissen.

## Privacy

Gegevensverzameling ten behoeve van [!DNL Product Recommendations] omvat geen persoonlijk identificeerbare informatie (PII). Ook, zijn alle gebruikers - herkenningstekens zoals koekje IDs en IP adressen strikt geanonimiseerd. Meer leren, zie het [ Beleid van de Privacy van Adobe ](https://www.adobe.com/privacy/policy.html).

[!DNL Product Recommendations] de gebruikers kunnen naar het [ dashboard van het Beheer van Gegevens ](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html?lang=nl-NL) voor meer gegevens over gegevens verwijzen synchroniseren.

## Productaanbevelingen versus productrelaties

Gezien de voortdurend veranderende complexiteit van online winkelen, is wat het beste werkt voor uw winkel vaak een combinatie van meerdere sleuteltechnologieën. Het gebruiken van zowel [!DNL Product Recommendations] als [ Verhoudingen van het Product ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/product-relationships/product-relationships.html?lang=nl-NL) geeft u meer flexibiliteit wanneer het bevorderen van producten. U kunt [!DNL Product Recommendations] van Adobe Sensei gebruiken om uw aanbevelingen op intelligente wijze op schaal te automatiseren. Dan, kunt u hefboomwerking [ Verwante Regels van het Product ](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/product-relationships/product-related-rules.html?lang=nl-NL) wanneer u moet manueel tussenkomen en ervoor zorgen dat een specifieke aanbeveling aan een doelverkoopsegment wordt gemaakt, of wanneer bepaalde bedrijfsdoelstellingen moeten worden verwezenlijkt.

Met productaanbevelingen kunt u:

- Maak een keuze uit negen verschillende soorten intelligente aanbevelingen op basis van de volgende gebieden: winkelgebaseerd, op items gebaseerd, op populariteit gebaseerd, trending en op gelijkenis gebaseerd
- Gebruik gedragsgegevens om aanbevelingen te personaliseren gedurende de hele winkelreis
- Bepaal de belangrijkste metriek relevant voor elke aanbeveling om u te helpen het effect van uw aanbevelingen begrijpen

## [!DNL Product Recommendations] demo

Bekijk deze video voor meer informatie over [!DNL Product Recommendations] :

>[!VIDEO](https://video.tv.adobe.com/v/343991?quality=12)

## Beleid voor het bewaren van catalogusgegevens

Als u gedurende 90 opeenvolgende dagen geen query verzendt voor de catalogusgegevens in uw testomgeving, worden de catalogusgegevens ingesteld op de slaapstand en worden er geen gegevens geretourneerd voor een query. Dit beleid heeft geen invloed op catalogusgegevens in uw productieomgeving.

Om de catalogusgegevens in uw het testen milieu opnieuw te activeren, [ voorlegt een steunverzoek ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#experience-league-start-page) met de titel: &quot;Reactivate [!DNL Product Recommendations]&quot;en omvat milieu IDs. De catalogusgegevens in de testomgeving moeten binnen een paar uur worden hersteld.
