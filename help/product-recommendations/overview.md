---
title: Wat zijn productaanbevelingen?
description: Meer weten over productaanbevelingen in Adobe Commerce? Ontdek door AI gestuurde winkeleenheden, privacy-, beheer- en winkelpaden en belangrijke gegevensbewaring.
recommendations: noCatalog
exl-id: 72850cfd-555c-4e0e-ac3e-097e6dac2030
source-git-commit: 6bfc2c0ed53b44fb30a142dc87f87dca8a601a33
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 0%

---

# Wat zijn [!DNL Product Recommendations]?

[!DNL Product Recommendations] hulp u gepersonaliseerde productaanbevelingen op de winkelcentra van Adobe Commerce toont gebruikend [&#x200B; Adobe AI &#x200B;](https://business.adobe.com/nl/ai.html) en machine het leren op samengevoegd verkoopgedrag en uw catalogus. Dit overzicht behandelt de dienstbeperkingen (met inbegrip van HIPAA), gegevens en privacy, waar de aanbevelingen eenheden verschijnen, de wegen van de storefront implementatie, hoe de aanbevelingen productverhoudingen, en catalogusgegevensbehoud aanvullen.

>[!IMPORTANT]
>
>**[!DNL Product Recommendations]is geen HIPAA-klaar dienst.** Schakel [!DNL Product Recommendations] niet in of gebruik het niet in Adobe Commerce-implementaties die gebruikmaken van de HIPAA-ready-aanbieding of die anderszins beschermde gezondheidsinformatie (PHI) verwerken. [!DNL Product Recommendations] maakt deel uit van de Commerce SaaS-services die momenteel zijn geclassificeerd als zijnde gereed voor niet-HIPAA.
>
>Voor details over welke mogelijkheden van Adobe Commerce HIPAA klaar zijn en welke diensten niet met PHI moeten worden gebruikt, zie [&#x200B; bereidheid van HIPAA op Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) en [&#x200B; Verrichtingen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/compliance/hipaa-ready-service/operations#adobe-commerce-services).

## Gegevensverwerking en privacy

Gegevensverzameling voor [!DNL Product Recommendations] bevat geen persoonlijk identificeerbare informatie (PII). Alle gebruikers-id&#39;s, zoals cookie-id&#39;s en IP-adressen, worden strikt geanonimiseerd. Meer leren, zie het [&#x200B; Beleid van de Privacy van Adobe &#x200B;](https://www.adobe.com/privacy/policy.html).

Voor meer informatie over gegevens die synchroniseren, zie het [&#x200B; Dashboard van het Beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard.html?lang=nl-NL).

## Waar worden aanbevelingen weergegeven

Aanbevelingen worden in de winkel weergegeven als eenheden met labels, zoals &quot;Klanten die dit product ook hebben bekeken&quot;. U kunt vanuit Adobe Commerce Admin aanbevelingen voor uw winkel maken, beheren en implementeren. Als uw project van Commerce de [&#x200B; Schakelaar van Adobe Commerce Optimizer &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/aco-optimizer-connector/overview) gebruikt, creeert, beheert en, aanbevelingen door [&#x200B; Adobe Commerce Optimizer &#x200B;](../optimizer/overview.md) opstelt.

## Storefront-implementaties

Kies de documentatie die overeenkomt met uw storefront:

- **PWA Studio** — [&#x200B; documentatie van PWA &#x200B;](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/)
- **Eigen frontends van de Douane (bijvoorbeeld, Reageren of Vue.js)** - [&#x200B; integreert  [!DNL Product Recommendations]](headless.md) in een headless storefront
- **Commerce Edge Delivery Services (EDS)** — [&#x200B; Adobe Commerce Storefront documentatie voor EDS &#x200B;](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/?lang=nl-NL)

>[!NOTE]
>
>De instellingen voor Koptekst en Aangepast variëren per stapel. In dit productgebied wordt een PWA Studio-pad en een algemeen patroon van de integratie zonder kop weergegeven. het omvat niet elk derde of douanescenario.

## Productaanbevelingen versus productrelaties

Gezien de voortdurend veranderende complexiteit van online winkelen, is wat het beste werkt voor uw winkel vaak een combinatie van meerdere sleuteltechnologieën. Het gebruiken van zowel [!DNL Product Recommendations] als [&#x200B; Verhoudingen van het Product &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/product-relationships/product-relationships.html?lang=nl-NL) geeft u meer flexibiliteit wanneer het bevorderen van producten. U kunt [!DNL Product Recommendations] van Adobe AI gebruiken om uw aanbevelingen op intelligente wijze op schaal te automatiseren. Dan, kunt u hefboomwerking [&#x200B; Verwante Regels van het Product &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/product-relationships/product-related-rules.html?lang=nl-NL) wanneer u moet manueel tussenkomen en ervoor zorgen dat een specifieke aanbeveling aan een doelverkoopsegment wordt gemaakt, of wanneer bepaalde bedrijfsdoelstellingen moeten worden verwezenlijkt.

Met productaanbevelingen kunt u:

- Kies uit negen verschillende soorten intelligente aanbevelingen op basis van de volgende gebieden: op basis van winkels, items, populariteit, trending en op basis van gelijkenis
- Gebruik gedragsgegevens om aanbevelingen te personaliseren gedurende de hele winkelreis
- Bepaal de belangrijkste metriek relevant voor elke aanbeveling om u te helpen het effect van uw aanbevelingen begrijpen

## Productaanbevelingen demo

Bekijk deze video voor meer informatie over [!DNL Product Recommendations] :

>[!VIDEO](https://video.tv.adobe.com/v/3449964?captions=dut&quality=12)

## Beleid voor het bewaren van catalogusgegevens

De service [!DNL Product Recommendations] is afhankelijk van catalogusgegevens die synchroon blijven met uw Adobe Commerce-omgeving. Inactieve catalogi of omgevingen die stoppen met het opvragen van die gegevens kunnen worden gehiberneerd. Dit beïnvloedt wat de service retourneert totdat u de gegevens opnieuw activeert.

Als u geen vraag voor de catalogusgegevens in uw **het testen** milieu voor 90 opeenvolgende dagen indient, wordt het catalogusgegeven geplaatst aan hibernatiemodus en geen gegeven is teruggekeerd voor om het even welke vraag. De gegevens van de catalogus in uw **productie** milieu wordt niet beïnvloed door de regel van 90 dagen.

Als uw milieu een **lege catalogus** 45 dagen na wordt gecreeerd heeft, worden de catalogusgegevens geplaatst aan hibernatiemodus en geen gegevens zijn teruggekeerd voor om het even welke vraag. Dit geldt zowel voor productie- als testomgevingen.

### Catalogusgegevens opnieuw activeren

Om catalogusgegevens na hibernatie te herstellen, [&#x200B; voorlegt een steunverzoek &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#experience-league-start-page) met de titel &quot;Reactivate [!DNL Product Recommendations]&quot;en omvat milieu IDs. Catalogusgegevens moeten binnen een paar uur worden hersteld.
