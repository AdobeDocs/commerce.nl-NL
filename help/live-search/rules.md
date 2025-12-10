---
title: Merchandising zoeken
description: In [!DNL Live Search] worden logica en acties gecombineerd om de winkelervaring vorm te geven.
exl-id: 9894bf2b-8556-4057-aa23-ebdcb1599914
source-git-commit: c6725fc524e9d239ccc0f16701e92ad5d2fc7729
workflow-type: tm+mt
source-wordcount: '681'
ht-degree: 0%

---

# Merchandising zoeken

Zoekhandel verwijst naar een set regels die logica combineert met handelingen om de zoekervaring van een klant in uw winkel vorm te geven. U kunt het veranderen van regels gebruiken om producten op te voeren, te begraven, te spelden, of te verbergen om onderzoeksresultaten in echt te kalibreren - tijd om uw bedrijfsdoelstellingen te steunen.

Elke regel heeft drie hoofdcomponenten:

* Voorwaarden - De voorwaarden die een handeling activeren.
* Gebeurtenissen - De acties die plaatsvinden wanneer aan de voorwaarden wordt voldaan.
* Details - De naam van de regel, en facultatief tijdkader en beschrijving.

U kunt meerdere voorwaarden en handelingen combineren en een regel voor een periode laten activeren. U kunt ook een standaardregel instellen die wordt toegepast, zelfs als er geen zoekterm is ingesteld.

## Vereisten

Een eenvoudige zoekregel kan één voorwaarde en één gebeurtenis hebben, terwijl een complexe regel tot tien voorwaarden kan hebben die tot 25 gebeurtenissen teweegbrengen.
Regels kunnen:

* Tot tien voorwaarden
* Tot 25 gebeurtenissen

Zoektekst kan het volgende bevatten:

* Alfanumerieke tekens (letters en cijfers)
* Hoofdletters of kleine letters. Kapitalisatie wordt genegeerd.

## Logische operatoren

De logische operatoren `AND` en `OR` voegen twee voorwaarden samen en retourneren verschillende resultaten. Alle logische operatoren die in een regel met meerdere voorwaarden worden gebruikt, zijn hetzelfde. Het is niet mogelijk om zowel `AND` als `OR` in dezelfde regel te gebruiken.

### Operatoren afstemmen

De operatoren Match `All` en `Any` bepalen de logische operator die wordt gebruikt om meerdere voorwaarden in de regel samen te voegen en kunnen worden gebruikt om de bestaande operator te wijzigen.

* `All` - Gebruikt de logische operator `AND` om meerdere voorwaarden te verbinden. Een regel die de operator `All` Match gebruikt, kan slechts één voorwaarde `Search query is` hebben.
* `Any` - Gebruikt de logische operator `OR` om meerdere voorwaarden te verbinden.

Wanneer het samenstellen van een complexe regel, kan het helpen om het met inspringing uit te schrijven om de voorwaarden, bijbehorende gebeurtenissen, en productnamen of SKUs te beschrijven die nodig zijn om de resultaten terug te keren u wilt bereiken. Vervolgens bouwt u de regel en test u het resultaat.

## Standaardregel

U kunt een standaardregel instellen die wordt toegepast wanneer geen zoekterm wordt opgegeven of wanneer geen andere zoekregel kan worden toegepast. Als u de standaardregel op &quot;Meest gekocht&quot;plaatst, dan zullen alle vragen aan dat rangschikkende type in gebreke blijven, tenzij super-ceded door een specifiekere onderzoekstermijn. Er kan geen zoekterm voor de standaardregel worden ingesteld.

## Volgorde van prioriteit met meerdere regels

Er wordt slechts één zoekregel tegelijk toegepast op een zoekterm.
Als meerdere regels van toepassing blijken te zijn op een zoekfrase, worden al deze regels toegepast. Als er een botsing tussen twee regels is— `rule 1` die sku1 opvoert maar `rule 2` het zelfde SKU-toen verbergt de onlangs toegepaste regel (`rule 2`) neemt belangrijkheid.

* Regels worden geordend met de tijdstempel &#39;Laatst gewijzigd&#39;. De regel die het laatst is gewijzigd, wordt eerst toegepast en daarna oudere regels in tijdstempelvolgorde.
* De voorwaarde `query is` heeft voorrang op andere voorwaarden. Als een nieuwere regel een voorwaarde `query contains` bevat, maar een oudere regel een voorwaarde `query is` heeft, wordt de regel `query is` toegepast.

### Storefront-aanvragen

Als een actieve regel met een voorwaarde `query is` overeenkomt met de zoekuitdrukking, wordt deze toegepast. Als er meerdere overeenkomende regels met een voorwaarde `query is` zijn, wordt de laatst bijgewerkte actieve regel toegepast.
Anders wordt de laatst bijgewerkte actieve regel toegepast.

### Voorvertoningsverzoeken

Aanvraag in de beheerder werkt iets anders. Wanneer u een voorvertoning weergeeft in de beheertoepassing, worden alle regels toegepast, inclusief de regels die zijn verlopen en gepland.

* Als de regel waarvan een voorvertoning wordt weergegeven een voorwaarde `query is` heeft, wordt deze toegepast.
* Als de regel waarvan een voorvertoning wordt weergegeven geen voorwaarde `query is` heeft en er een volgende actieve, overeenkomende regel met een voorwaarde `query is` wordt gevonden, wordt de regel `query is` toegepast.
* Als de regel waarvan een voorvertoning wordt weergegeven geen voorwaarde `query is` heeft en er geen andere regel met een voorwaarde `query is` wordt gevonden, wordt de regel toegepast die wordt voorvertoond.

## Rubriekhandel en producttoewijzingen van categorieën

Met [!DNL Live Search] kunt u filteren op categorieën. Zie [&#x200B; het Merchandising van de Categorie &#x200B;](category-merch.md) voor meer informatie.
Nochtans, in Adobe Commerce kunt u een virtuele categorie met [&#x200B; het producttaken van de Categorie &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html) tot stand brengen. Dit type categorie is gemaakt bij uitvoering en komt niet voor in de categoriedatabase. Daarom kan [!DNL Live Search] dit categorietype niet lezen of gebruiken.
