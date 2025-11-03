---
title: Overzicht van facetten
description: Leer over facetten in  [!DNL Adobe Commerce Optimizer]  en hoe zij onderzoeksresultaten verbeteren.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: cf16626e-8f85-47ca-b973-891b16c31fe3
source-git-commit: b786a8675625dc969b9542b4b4f716de5342c1af
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---

# Facetten

Facets is een methode voor het filteren van hoge prestaties waarbij meerdere dimensies van kenmerkwaarden worden gebruikt als zoekcriteria.

![&#x200B; Gefilterde onderzoeksresultaten &#x200B;](../../assets/storefront-search-results-run.png)

Binnen een facet kunnen kopers meerdere opties selecteren, zoals &quot;Standaard&quot; en &quot;Snug&quot; onder &quot;Stijl&quot; en in de zoekresultaten worden alleen die stijlen weergegeven. Op dezelfde manier geldt dat als een winkelier opties selecteert in verschillende facetten, zoals &quot;Standaard&quot; onder &quot;Stijl&quot; en &quot;Binnenshuis&quot; onder &quot;Klimaat&quot;, de zoekresultaten worden bijgewerkt om die geselecteerde stijl en dat geselecteerde klimaat weer te geven.

Elke gedefinieerde facet kan worden gebruikt als een URL-parameter en de resultaten worden gefilterd op basis van de parameterwaarden: `http://yourstore.com?brand=acme&color=red` .

## Facetaggregatie

Facetsamenvoeging wordt als volgt uitgevoerd: als de winkel drie facetten (categorieën, kleur en prijs) heeft en de winkelfilters op alle drie (kleur = blauw, de prijs is van $10.00-50.00, categorieën = `promotions`).

- `categories` aggregatie - aggregeert `categories` en past vervolgens de filters `color` en `price` toe, maar niet het filter `categories` .
- `color` aggregatie - aggregeert `color` en past vervolgens de filters `price` en `categories` toe, maar niet het filter `color` .
- `price` aggregatie - aggregeert `price` en past vervolgens de filters `color` en `categories` toe, maar niet het filter `price` .

## Standaardkenmerkwaarden

De volgende productkenmerken worden standaard gebruikt door [!DNL Adobe Commerce Optimizer] en ingeschakeld.

| Eigenschap | Beschrijving | Kenmerk |
|---|---|---|
| Sorteerbaar | Wordt gebruikt voor sorteren in de productlijst | `price` |
| Doorzoekbaar | Gebruiken in Zoeken | `price` <br />`sku`<br />`name` |

Zie de [&#x200B; Meta-gegevens API van de Ingestie van Gegevens &#x200B;](https://developer.adobe.com/commerce/services/optimizer/data-ingestion/#metadata) om meer over productattributen en hun eigenschappen te leren.

## Gelaagde zoekopdracht en uitbreiding van zoektypen

Gelaagd onderzoek, of onderzoek binnen een onderzoek, is een op attributen-gebaseerd het filtreren systeem dat de traditionele onderzoeksfunctionaliteit uitbreidt om extra onderzoeksparameters te omvatten. Deze extra onderzoeksparameters staan nauwkeurigere en flexibele productontdekking toe.

Met gelaagde zoekopdracht kunt u:

- Kopers kunnen in de zoekresultaten zoeken.
- Gebruik `startsWith` en `contains` zoekindexatie in de tweede laag van de gelaagde zoekopdracht om de resultaten verder te verfijnen.

De geavanceerde onderzoeksmogelijkheden worden uitgevoerd door de `filter` parameter in [`productSearch` vraag &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) gebruikend specifieke exploitanten:

- **Gelaagd onderzoek** - Onderzoek binnen een andere onderzoekscontext - met dit vermogen, kunt u tot twee lagen van onderzoek naar uw onderzoeksvragen ondernemen. Bijvoorbeeld:

   - **Laag 1 onderzoek** - Onderzoek naar &quot;motor&quot;op `product_attribute_1`.
   - **Laag 2 onderzoek** - Onderzoek naar &quot;deelaantal 123&quot;op `product_attribute_2`. In dit voorbeeld wordt gezocht naar &quot;part number 123&quot; in de resultaten naar &quot;motor&quot;.

  Gelaagde zoekopdracht is beschikbaar voor zowel `startsWith` zoekindexatie als `contains` zoekindexatie in de tweede laag van de gelaagde zoekopdracht, zoals hieronder wordt beschreven:

- **startWith onderzoeksindexatie** - Onderzoek gebruikend `startsWith` indexatie. Met deze functie is het mogelijk:

   - Zoeken naar producten waarbij de kenmerkwaarde begint met een opgegeven tekenreeks.
   - Het vormen van &quot;beëindigt met&quot;onderzoek zodat kunnen de kopers naar producten zoeken waar de attributenwaarde met een bepaalde koord beëindigt.
      - Om &quot;beëindigt met&quot;onderzoek toe te laten, moet het productattribuut in omgekeerde worden opgenomen en de API vraag zou ook een omgekeerde koord moeten zijn. Als u bijvoorbeeld wilt zoeken naar een productnaam die eindigt met een &quot;broek&quot;, moet u deze als &quot;stnap&quot; verzenden.

- **bevat onderzoeksindexatie** - Onderzoek een attribuut gebruikend bevat indexatie. Met deze nieuwe functie is het mogelijk:

   - Zoeken naar een query binnen een grotere tekenreeks. Als een winkel bijvoorbeeld het productnummer &quot;PE-123&quot; zoekt in de tekenreeks &quot;HAPE-123&quot;.

      - Nota: Dit onderzoekstype is verschillend van het bestaande [&#x200B; uitdrukkingsonderzoek &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#phrase), dat een autocomplete onderzoek uitvoert. Als de waarde van het kenmerk van het product bijvoorbeeld &quot;outdoorbroek&quot; is, retourneert een zoekopdracht met woordgroepen een reactie voor &quot;out pan&quot;, maar wordt geen reactie voor &quot;of ants&quot; geretourneerd. A contains search, echter, retourneert wel een reactie op ‘or ants’.

Deze nieuwe voorwaarden verbeteren het het filtreren van de onderzoeksvraag mechanisme om onderzoeksresultaten te raffineren. Deze nieuwe voorwaarden hebben geen invloed op de hoofdzoekquery.

### Implementatie

1. [&#x200B; plaats attributen als doorzoekbaar &#x200B;](https://developer.adobe.com/commerce/services/reference/rest/#tag/Metadata).

1. Specificeer het onderzoeksvermogen voor dat attribuut, zoals **bevat** (gebrek) of **begint met**. U kunt een maximum van zes attributen specificeren om voor **toe te laten bevat** en zes attributen om voor **toe te laten begint met**. Bovendien, voor **bevat** indexatie, is de koordlengte beperkt tot 50 karakters of minder.

1. Zie de [&#x200B; ontwikkelaardocumentatie &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#filtering-using-search-capability) voor voorbeelden van hoe te om uw [!DNL Commerce Optimizer] API vraag bij te werken gebruikend de nieuwe `contains` en `startsWith` onderzoeksmogelijkheden.

   U kunt deze nieuwe voorwaarden implementeren op de pagina met zoekresultaten. U kunt bijvoorbeeld een nieuwe sectie toevoegen op de pagina waar de gebruiker de zoekresultaten verder kan verfijnen. Je kunt kopers toestaan specifieke productkenmerken te selecteren, zoals &#39;Fabrikant&#39;, &#39;Onderdeelnummer&#39; en &#39;Beschrijving&#39;. Daarna zoeken ze binnen die kenmerken met behulp van de `contains` - of `startsWith` -voorwaarden.

### Wanneer gebruikt u gelaagde zoekopdracht in plaats van facetten

Gelaagde zoekopdrachten en facetten hebben verschillende doeleinden bij productdetectie, en het kiezen tussen deze doelen hangt af van uw specifieke gebruiksscenario:

**gelaagd onderzoek van het Gebruik aan:**

- Zoeken in zoekresultaten aan de hand van meerdere criteria
- Werken met artikelnummers, SKU&#39;s of technische specificaties waarvan gebruikers gedeeltelijke informatie kennen
- Kopers toestaan de resultaten stap voor stap te beperken tot geneste criteria
- Verminder het aantal API vraag door veelvoudige onderzoekscriteria in één enkele vraag te combineren
- Voer bedrijfsspecifieke onderzoekspatronen uit die verder gaan dan standaard beperkte navigatie

**de facetten van het Gebruik aan:**

- Standaardfilteropties voor categorieën, prijzen, merken en kenmerken bieden
- Intuïtieve filteropties bieden die gebruikers gemakkelijk kunnen begrijpen en selecteren
- Beschikbare opties tonen op basis van de huidige zoekresultaten
- Filteraantallen en -bereiken weergeven die gebruikers helpen inzicht te krijgen in beschikbare opties
- Werken met algemene productkenmerken zoals kleur, grootte, materiaal, enzovoort

**Beste praktijken:** Gebruik gelaagd onderzoek naar complexe, technische onderzoeken waar de gebruikers specifieke criteria hebben, en gebruik facetten voor standaard e-commerce het filtreren waar de gebruikers opties willen onderzoeken en visueel verfijnen.
