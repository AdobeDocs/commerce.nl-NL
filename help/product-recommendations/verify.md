---
title: Gebeurtenisverzameling verifiëren
description: Leer hoe u kunt controleren of er gedragsgegevens naar Adobe Commerce worden verzonden.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# Gebeurtenisverzameling verifiëren

Nadat u [ installeert en ](install-configure.md) vormt de `magento/product-recommendations` module, kunt u verifiëren dat de gedragsgegevens naar Adobe Commerce worden verzonden. U kunt de ontwikkelaarsgereedschappen gebruiken die beschikbaar zijn in Chrome, of de extensie Snowplow Chrome installeren. Als u extra hulp nodig hebt, verwijs naar [ los  [!DNL Product Recommendations]  module ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) in de Kennisbank van de Steun problemen op.

## Verifiëren met hulpprogramma&#39;s voor ontwikkelaars in Chrome

Om ervoor te zorgen dat het JS-bestand van de gebeurtenisverzamelaar op alle sitepagina&#39;s wordt geladen:

1. In Chrome, kies **aanpassen en Google Chrome** dan selecteren **Meer Hulpmiddelen** > **Hulpmiddelen van de Ontwikkelaar**.
1. Kies het **lusje van het Netwerk** dan het **JS** type.
1. Filter voor `ds.`
1. Laad de pagina opnieuw.
1. U zou `ds.js` of `ds.min.js` in de **kolom van de Naam** moeten zien.

![ de inzamelaar JS van de Gebeurtenis ](assets/filter-ds.png)
_de Collector JS van de Gebeurtenis_

Om ervoor te zorgen dat de gebeurtenissen op pagina&#39;s over uw plaats (huis, product, kassa, etc.) worden afgevuurd:

1. Zorg ervoor dat u eventuele advertentieblokkers in uw browser uitschakelt en cookies op de site accepteert.
1. In Chrome, kies **aanpassen en Google Chrome** (de drie verticale punten in de hogere juiste hoek van browser) dan selecteren **Meer Hulpmiddelen** > **Hulpmiddelen van de Ontwikkelaar**.
1. Kies het **lusje en de filter van het Netwerk** {voor `tp2`.
1. Laad de pagina opnieuw.
1. U zou vraag onder `tp2` in de **2} kolom van de Naam {moeten zien.**

![ het Vuren gebeurtenissen ](assets/filter-tp2.png)
_verifieer dat de gebeurtenissen_ ontsteken

## Verifiëren met de extensie Snowplow Chrome

Installeer de [ Debugger van de Analyse van de Snowplow uitbreiding voor Chrome ](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). Deze extensie geeft de gebeurtenissen weer die worden verzameld en naar Adobe Commerce worden verzonden.

1. Zorg ervoor dat u eventuele advertentieblokkers in uw browser uitschakelt en cookies op de site accepteert.

1. In Chrome, kies **aanpassen en Google Chrome** (de drie verticale punten in de hogere juiste hoek van browser) dan selecteren **Meer Hulpmiddelen** > **Hulpmiddelen van de Ontwikkelaar**.

1. Kies de **tabel van de Analyse van de Snowplow** Debugger.

1. Onder de **kolom van de Gebeurtenis**, uitgezochte **Gestructureerde Gebeurtenis**.

1. De rol neer tot u **Gegevens van de Context _n_**ziet. Zoek de storefront instantie in het **Schema**.

1. Verifieer dat [ identiteitskaart van de Ruimte van Gegevens SaaS ](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) correct wordt geplaatst.

![ Snowplow filter ](assets/snowplow-filter.png)
_Snowplow Filter_

>[!NOTE]
>
> De waarde `Data validity : NOT FOUND` in het foutopsporingsprogramma geeft een intern schema aan. De Snowplow Chrome-insteekmodule kan de gebeurtenissen niet valideren met een intern schema. Dit heeft geen invloed op de eigenlijke functionaliteit.

## Controleren of gebeurtenissen correct worden geactiveerd

Als u wilt controleren of de gebeurtenissen die voor metrische gegevens worden gebruikt, correct worden uitgevoerd, zoekt u naar de gebeurtenissen `impression-render` , `view` en `rec-click` in Foutopsporing voor Snowplow-analyse. Zie de [ volledige lijst van gebeurtenissen ](https://experienceleague.adobe.com/docs/commerce/product-recommendations/developer/events.html).

>[!NOTE]
>
> Als [ de Wijze van de Beperking van het Koekje ](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) wordt toegelaten, verzamelt Adobe Commerce geen gedragsgegevens tot de verkoopster toestemmingen. Als de modus Cookie-beperking is uitgeschakeld, worden standaardgedragsgegevens verzameld.
