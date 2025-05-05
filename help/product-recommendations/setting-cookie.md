---
title: Cookie-beperkingen verwerken
description: Leer hoe aanbevelingen voor producten cookie-beperkingen verwerken.
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Cookie-beperkingen verwerken

Zowel Adobe Commerce als Magento Open Source vragen om toestemming voordat gegevens in browsercookies worden opgeslagen. Voor meer informatie, verwijs naar [ de beperkingswijze van het Koekje ](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html?lang=nl-NL).

Wanneer u de `magento/product-recommendations` module aan productie opstelt, begint het inzamelen van de gebeurtenissen van de winkelinteractie op uw storefront. Omdat de gegevens voor deze gebeurtenissen in browser koekjes of lokale opslag kunnen worden opgeslagen, steunt de eigenschap koekjesbeperkingswijze door geen gebeurtenissen te verzamelen tot de verkoopster koekjestoestemming heeft gegeven.

Dit werkt mogelijk niet met oplossingen voor cookie van derden. Het is de verantwoordelijkheid van elke handelaar om ervoor te zorgen dat er geen gegevens worden verzameld voordat toestemming voor het gebruik van cookies is gegeven, zoals vaak wettelijk vereist is. Als u de toestemming van cookies beheert met aangepaste code, kunt u een niet-bijgehouden cookie met de naam `mg_dnt` gebruiken om de gegevensverzameling te beperken.

- Naam van de cookie:

  ```text
  `const DNT_COOKIE = "mg_dnt";`
  ```

- Stel het cookie niet bijhouden in om gegevensverzameling uit te schakelen:

  ```text
  `$.mage.cookies.set(DNT_COOKIE, true);`
  ```

- De cookie wissen wanneer de gebruiker cookies heeft geaccepteerd:

  ```text
  `$.mage.cookies.clear(DNT_COOKIE);`
  ```
