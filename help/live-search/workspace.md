---
title: Live zoeken instellen
description: De  [!DNL Live Search]  werkruimte wordt gebruikt om, onderzoeksprestaties te vormen te beheren en te controleren.
exl-id: 07c32b26-3fa4-4fae-afba-8a10866857c3
source-git-commit: 4ba9734946f551784cd429ffa7cb23358f0f9710
workflow-type: tm+mt
source-wordcount: '2013'
ht-degree: 0%

---

# Live zoeken instellen

In de werkruimte kunt u de prestaties van [!DNL Live Search] configureren, beheren en controleren. Het menu boven biedt toegang tot de gereedschappen in elk functioneel gebied. De beschikbare functies weerspiegelen de huidige menuselectie.

![&#x200B; Workspace &#x200B;](assets/workspace.png)

## Gegevensverzameling

Om ervoor te zorgen dat elk functioneel gebied op de werkruimte de correcte gegevens bevat, moet u gegevensinzameling vormen die op de geselecteerde storefront implementatie wordt gebaseerd:

1. Luma - Gegevensverzameling is offline beschikbaar.
1. Headless - De inzameling van Gegevens moet manueel, afhankelijk van storefront implementatie worden gevormd.

Als u een koploze winkel gebruikt, raadpleegt u de volgende documentatie voor meer informatie over de vereiste gebeurtenissen die u moet toevoegen:

- [&#x200B; Vereiste gebeurtenissen &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#live-search) voor Levend dashboard van het Onderzoek.
- [&#x200B; de gebeurtenisinzamelaar van de Storefront &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) die als voorwaarde moet worden toegevoegd.
- [&#x200B; Voorbeelden &#x200B;](https://github.com/adobe/commerce-events/tree/main/examples) van de gebeurtenisstructuur.

### Gezondheidszorgklanten

Als u een gezondheidszorgklant bent en u de [&#x200B; uitbreiding van HIPAA van de Diensten van Gegevens &#x200B;](../data-connection/hipaa-readiness.md#installation) installeerde, die deel van de [&#x200B; uitbreiding van de Verbinding van Gegevens &#x200B;](../data-connection/overview.md) uitmaakt, worden de gegevens van de storefront gebeurtenis die door [!DNL Live Search] worden gebruikt niet meer gevangen. Dit komt doordat gebeurtenisgegevens voor storefront op de client worden gegenereerd. Als u wilt doorgaan met het vastleggen en verzenden van gegevens over storefront-gebeurtenissen, schakelt u gebeurtenisverzameling opnieuw in voor [!DNL Live Search] . Zie [&#x200B; algemene configuratie &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/general#data-services) om meer te leren.

## Bereik instellen

Aanvankelijk wordt het [&#x200B; werkingsgebied &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) van alle [!DNL Live Search] montages geplaatst aan `Default Store View`. Als uw [!DNL Commerce] installatie veelvoudige opslagmeningen omvat, plaats **Reikwijdte** aan de [&#x200B; opslagmening &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) waar uw facetmontages van toepassing zijn.

## Menuopties

| Optie | Beschrijving |
|--- |--- |
| [&#x200B; Prestaties &#x200B;](performance.md) | Het dashboard biedt insight in de zoekprestaties van producten. |
| [&#x200B; Faceting &#x200B;](facets.md) | Krachtig filteren waarbij meerdere dimensies van kenmerkwaarden worden gebruikt om zoekcriteria te verfijnen. |
| [&#x200B; Synoniemen &#x200B;](synonyms.md) | Breid het bereik van de zoekopdracht uit tot woorden die kopers kunnen gebruiken om producten te zoeken die afwijken van de producten in uw catalogus. |
| [&#x200B; Merchandising van het Onderzoek &#x200B;](rules.md) | Vorm de onderzoekservaring met logische regels die geplande acties teweegbrengen. Verhoog, bury, speld, of verberg producten om onderzoeksresultaten te kalibreren om uw bedrijfsdoelstellingen te steunen. |
| [&#x200B; Merchandising van de Categorie &#x200B;](category-merch.md) | Pas regels en Intelligent Merchandising op het niveau van de Categorie toe. |
| [&#x200B; GraphQL &#x200B;](graphql.md) | Ontwikkelaars die zijn aangemeld bij de beheerder van uw winkel, kunnen query&#39;s samenstellen en testen met werkelijke catalogusgegevens. Meer leren, ga naar [&#x200B; het Overzicht van GraphQL &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) in de [!DNL Live Search] ontwikkelaarsdocumentatie. |
| [&#x200B; Montages &#x200B;](settings.md) | Bepaal hoe prijsfacetwaarden worden gegroepeerd op prijsbereik in de winkel en stel de indextaal in. |

## Kenmerken instellen als doorzoekbaar

Om hoogst-gerichte resultaten te veroorzaken, herzie de reeks [&#x200B; doorzoekbare &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) productattributen. Om relevantie te verzekeren, maak attributen doorzoekbaar slechts als zij inhoud bevatten die een duidelijke en beknopte betekenis heeft. Vermijd het gebruik van kenmerken die minder nauwkeurige, lange tekst bevatten, zoals `description` . Deze tekst kan de precisie van zoekresultaten verminderen, hoewel deze functie standaard is ingeschakeld. Als iemand bijvoorbeeld zoekt naar &quot;korte broeken&quot; en er overhemden zijn met een beschrijving die de term &quot;korte mouwen&quot; bevat, worden de overhemden opgenomen in de zoekresultaten.

Voer de volgende stappen uit om te zorgen dat kenmerken doorzoekbaar zijn:

1. In Admin, ga **>** Attribuut *>* Product **.**
1. Selecteer het kenmerk dat u wilt doorzoeken, bijvoorbeeld `color` .
1. Selecteer **Eigenschappen van 0&rbrace; Storefront en plaats** Gebruik in Onderzoek **aan**.`yes`

[!DNL Live Search] respecteert ook het [&#x200B; gewicht &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search) van een productattribuut, zoals die binnen Adobe Commerce wordt geplaatst. Kenmerken met een hogere dikte worden hoger weergegeven in de zoekresultaten.

De volgende kenmerken kunnen altijd worden doorzocht:

- `sku`
- `name`
- `categories`

### Gelaagde zoekopdracht en uitbreiding van zoektypen

Gelaagd onderzoek, of onderzoek binnen een onderzoek, is een krachtig, op attributen-gebaseerd het filtreren systeem dat de traditionele onderzoeksfunctionaliteit uitbreidt om extra onderzoeksparameters te omvatten. Deze extra onderzoeksparameters staan nauwkeurigere en flexibele productontdekking toe.

>[!NOTE]
>
>Gelaagde zoekopdracht is beschikbaar in Live zoeken 4.6.0.

Met gelaagde zoekopdracht kunt u:

- Kopers kunnen in de zoekresultaten zoeken.
- Gebruik `startsWith` en `contains` zoekindexatie in de tweede laag van de gelaagde zoekopdracht om de resultaten verder te verfijnen.

De geavanceerde onderzoeksmogelijkheden worden uitgevoerd door de `filter` parameter in [`productSearch` vraag &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) gebruikend specifieke exploitanten:

- **Gelaagd onderzoek** - Onderzoek binnen een andere onderzoekscontext - met dit vermogen, kunt u tot twee lagen van onderzoek naar uw onderzoeksvragen ondernemen. Bijvoorbeeld:

   - **Laag 1 onderzoek** - Onderzoek naar &quot;motor&quot;op `product_attribute_1`.
   - **Laag 2 onderzoek** - Onderzoek naar &quot;deelaantal 123&quot;op `product_attribute_2`. In dit voorbeeld wordt gezocht naar &quot;part number 123&quot; in de resultaten naar &quot;motor&quot;.

  Gelaagde zoekopdracht is beschikbaar voor zowel `startsWith` zoekindexatie als `contains` zoekindexatie in de tweede laag van de gelaagde zoekopdracht, zoals hieronder wordt beschreven:

- **startWith onderzoeksindexatie** - Onderzoek gebruikend `startsWith` indexatie. Met deze nieuwe functie is het mogelijk:

   - Zoeken naar producten waarbij de kenmerkwaarde begint met een opgegeven tekenreeks.
   - Het vormen van &quot;beëindigt met&quot;onderzoek zodat kunnen de kopers naar producten zoeken waar de attributenwaarde met een bepaalde koord beëindigt. Om &quot;beëindigt met&quot;onderzoek toe te laten, moet het productattribuut in omgekeerde worden opgenomen en de API vraag zou ook een omgekeerde koord moeten zijn. Als u bijvoorbeeld wilt zoeken naar een productnaam die eindigt met een &quot;broek&quot;, moet u deze als &quot;stnap&quot; verzenden.

- **bevat onderzoeksindexatie** - Onderzoek een attribuut gebruikend bevat indexatie. Met deze nieuwe functie is het mogelijk:

   - Zoeken naar een query binnen een grotere tekenreeks. Als een winkel bijvoorbeeld het productnummer &quot;PE-123&quot; zoekt in de tekenreeks &quot;HAPE-123&quot;.

      - Nota: Dit onderzoekstype is verschillend van het bestaande [&#x200B; uitdrukkingsonderzoek &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#phrase), dat een autocomplete onderzoek uitvoert. Als de waarde van het kenmerk van het product bijvoorbeeld &quot;outdoorbroek&quot; is, retourneert een zoekopdracht met woordgroepen een reactie voor &quot;out pan&quot;, maar wordt geen reactie voor &quot;of ants&quot; geretourneerd. A contains search, echter, retourneert wel een reactie op ‘or ants’.

Deze nieuwe voorwaarden verbeteren het het filtreren van de onderzoeksvraag mechanisme om onderzoeksresultaten te raffineren. Deze nieuwe voorwaarden hebben geen invloed op de hoofdzoekquery.

#### Implementatie

1. In Admin, [&#x200B; plaats een productattribuut &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/product-attributes-add#step-5-describe-the-storefront-properties) om doorzoekbaar te zijn.

   Zie de lijst van doorzoekbare [&#x200B; attributen &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types).

1. Specificeer het onderzoeksvermogen voor dat attribuut, zoals **bevat** (gebrek) of **begint met**. U kunt een maximum van zes attributen specificeren die voor **worden toegelaten bevat** en zes attributen die voor **worden toegelaten begint met**. Bovendien, voor **bevat** indexatie, is de koordlengte beperkt tot 50 karakters of minder.

   ![&#x200B; specificeer onderzoeksvermogen &#x200B;](./assets/search-filters-admin.png)

1. Zie de [&#x200B; ontwikkelaardocumentatie &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#filtering-using-search-capability) voor voorbeelden van hoe te om uw [!DNL Live Search] API vraag bij te werken gebruikend de nieuwe `contains` en `startsWith` onderzoeksmogelijkheden.

   U kunt deze nieuwe voorwaarden implementeren op de pagina met zoekresultaten. U kunt bijvoorbeeld een nieuwe sectie toevoegen op de pagina waar de gebruiker de zoekresultaten verder kan verfijnen. Je kunt kopers toestaan specifieke productkenmerken te selecteren, zoals &#39;Fabrikant&#39;, &#39;Onderdeelnummer&#39; en &#39;Beschrijving&#39;. Daarna zoeken ze binnen die kenmerken met behulp van de `contains` - of `startsWith` -voorwaarden.

### Wanneer gebruikt u gelaagde zoekopdracht in plaats van facetten

Gelaagde zoekopdrachten en facetten hebben verschillende doeleinden bij productdetectie, en het kiezen tussen deze doelen hangt af van uw specifieke gebruiksscenario:

**gelaagd onderzoek van het Gebruik wanneer:**

- U moet in zoekresultaten zoeken aan de hand van meerdere criteria.
- Werken met artikelnummers, SKU&#39;s of technische specificaties waarvan gebruikers gedeeltelijke informatie kennen.
- Winkelaars moeten de resultaten stap voor stap beperken tot geneste criteria.
- U wilt het aantal API vraag verminderen door veelvoudige onderzoekscriteria in één enkele vraag te combineren.
- U moet zaken-specifieke onderzoekspatronen uitvoeren die voorbij standaard beperkte navigatie gaan.

**facetten van het Gebruik wanneer:**

- Typische categorie-, prijs-, merk- en kenmerkfilters bieden
- Intuïtieve filteropties bieden die gebruikers gemakkelijk kunnen begrijpen en selecteren
- Beschikbare opties weergeven op basis van de huidige zoekresultaten
- Filteraantallen en -bereiken weergeven die gebruikers helpen de beschikbare opties te begrijpen
- Werken met algemene productkenmerken zoals kleur, grootte, materiaal, enzovoort.

**Beste praktijken:** Gebruik gelaagd onderzoek naar complexe, technische onderzoeken waar de gebruikers specifieke criteria hebben, en gebruik facetten voor standaard e-commerce het filtreren waar de gebruikers opties willen onderzoeken en versmallen visueel.

## Facetten en synoniemen

Facetten en synoniemen zijn een andere manier om de zoekervaring voor kopers te verbeteren.

[&#x200B; Facets &#x200B;](facets.md) zijn productattributen die in [!DNL Live Search] worden bepaald om filtreerbaar te zijn. U kunt om het even welk filtrable attribuut als facet in [!DNL Live Search] plaatsen, maar er zijn [&#x200B; grenzen &#x200B;](boundaries-limits.md) aan hoeveel facetten u in één keer kunt zoeken.

>[!NOTE]
>
>Een productattribuut is filtreerbaar slechts als de configuratie van het productattribuut de vereiste eigenschappen heeft: *Gebruik in Onderzoek = Nr*, *Gebruik in Gelaagd Navigation=yes van het Onderzoek resultaten*, en *Gebruik in Gelaagd Navigation=Filterable (met resultaten)*. Als deze eigenschappen ontbreken of niet correct plaatsen, is het attribuut niet zichtbaar in de configuratie van het Facet. Voor configuratieinstructies, zie [&#x200B; een Facet &#x200B;](facets-add.md#add-a-facet) toevoegen.

[&#x200B; Synoniemen &#x200B;](synonyms.md) zijn termijnen die u kunt bepalen helpen gebruikers aan het correcte product begeleiden. Gebruikers die op zoek zijn naar een broek kunnen &#39;broek&#39; of &#39;slacks&#39; typen. U kunt synoniemen zodanig instellen dat deze zoektermen gebruikers naar de resultaten van de &#39;&#39;broek&#39;&#39; brengen.

## Commerce-configuratie-instellingen

In de volgende sectie worden de ondersteunde en niet-ondersteunde Commerce-configuratie-instellingen voor [!DNL Live Search] beschreven.

### Ondersteunde configuratiewaarden

>[!IMPORTANT]
>
>We raden u aan de widgets voor productlijsten te gebruiken. Deze zijn standaard ingeschakeld in Live Search 4.0.0. De widgets zijn bedoeld om de adapterimplementatie in toekomstige versies volledig te vervangen. Zie [&#x200B; product toelaten lijst widgets &#x200B;](install.md#enable-product-listing-widgets) om meer te leren.

| Commerce-configuratie-instelling | Beschrijving | Ondersteund door Popover | Ondersteund door adapter |
|---|---|---|---|
| Winkels > Configuratie > Catalogus > Catalogus > Cataloguszoekopdracht > Alle producten per pagina toestaan | Indien ingesteld op `Yes` , neemt u de optie `ALL` op in het besturingselement &#39;Tonen per pagina&#39;. | Ja. Maximaal 500 producten | Ja. Maximaal 500 producten |
| Winkels > Configuratie > Catalogus > Catalogus > Cataloguszoekopdracht > Minimale lengte query | Het minimale aantal tekens dat is toegestaan in een cataloguszoekopdracht. | Ja | Ja |
| Winkels > Configuratie > Catalogus > Catalogus > Cataloguszoekopdracht > Producten per pagina op toegestane rasterwaarden | Hiermee bepaalt u het aantal producten dat wordt weergegeven in de rasterweergave. | Ja | Ja |
| Winkels > Configuratie > Catalogus > Catalogus > Cataloguszoekopdracht > Producten per pagina op standaardrasterwaarde | Hiermee bepaalt u het aantal producten dat standaard per pagina wordt weergegeven in de rasterweergave. | Ja. Maximaal 500 producten | Ja. Maximaal 500 producten |
| Winkels > Configuratie > Catalogus > Inventaris > Producten uit voorraad weergeven | Hiermee geeft u producten weer die uit voorraad zijn. | Ja | Ja |
| Stores > Configuration > Currency > Default Display Currency | De primaire valuta die wordt gebruikt om prijzen weer te geven. | Ja | Ja |
| Storingen > Configuratie > Algemeen > Valuta-instelling > Valuta-opties > Basisvaluta | De primaire valuta die wordt gebruikt voor alle online betalingstransacties. | Ja | Ja |

Prijzen in de aanbiedingspagina van het widgetproduct en in de pop-upmenu&#39;s worden met de geconfigureerde valutakoersen omgezet in de standaardweergavemunt.

### Niet-ondersteunde configuratiewaarden

| Commerce-configuratie-instelling | Beschrijving | Notities |
|---|---|---|
| Storingen > Configuratie > Catalogus > Storefront > Lijstmodus | Bepaalt de indeling van de lijst met zoekresultaten. | Rendering is correct, maar gebeurtenissen worden niet verzonden voor bepaalde paginainteracties |
| Winkels > Configuratie > Catalogus > Catalogus > Cataloguszoekopdracht > Maximale lengte query | Het maximum aantal tekens dat is toegestaan in een cataloguszoekopdracht. | Niet geïmplementeerd; zoekservices accepteren maximaal 255 tekens |
| Configuration > Sales > Tax > Price Display Settings > Display Product Prices in Catalog | Bepaalt of de productprijzen die in de catalogus worden gepubliceerd belasting omvatten of uitsluiten, of twee versies van de prijs tonen; één met, en andere zonder belasting |  |
| Winkels > Configuratie > Catalogus > Storefront > Productaanbieding sorteren op | Hiermee bepaalt u de sorteervolgorde van de lijst met zoekresultaten. | Is niet op [!DNL Live Search] van toepassing [&#x200B; Product het Van een lijst weergeven Widget van de Pagina &#x200B;](plp-styling.md) |

### Zoektermen

[!DNL Live Search] steunt [&#x200B; herleidt van de onderzoekstermijn &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) op implementaties waar Adobe Commerce het verpletteren, zoals op Luma en andere op php-Gebaseerde thema&#39;s behandelt.

## Standaardkenmerkwaarden

De volgende productkenmerken hebben [&#x200B; storefront eigenschappen &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) die door [!DNL Live Search] worden gebruikt en door gebrek worden toegelaten.

| Eigenschap | Storefront, eigenschap | Kenmerk |
|---|---|---|
| Sorteerbaar | Wordt gebruikt voor sorteren in de productlijst | `price` |
| Doorzoekbaar | Gebruiken in Zoeken | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Gebruik in gelaagde navigatie - Filterbaar (met resultaten) | `price`<br />`visibility`<br />`category_name` |

## Standaardeigenschappen van niet-systeemkenmerken

In de volgende tabel worden de standaardzoekeigenschappen en filterbare eigenschappen van niet-systeemkenmerken weergegeven, inclusief de eigenschappen die specifiek zijn voor de Luminantiemonsteringsgegevens. Het plaatsen van het *Gebruik in het 1&rbrace; attributenbezit van het Onderzoek &lbrace;aan* maakt de attributen doorzoekbaar in zowel `Yes` als inheemse Adobe Commerce.[!DNL Live Search]

| Kenmerkcode | Doorzoekbaar | Gebruiken in gelaagde navigatie |
|--- |--- |--- |
| activiteit | Ja | Filterbaar (met resultaten) |
| attributes_brand | Ja | Nee |
| merk | Ja | Nee |
| klimaat | Ja | Filterbaar (met resultaten) |
| halsband | Ja | Filterbaar (met resultaten) |
| kleur | Ja | Filterbaar (met resultaten) |
| kosten | Ja | Nee |
| eco_collection | Ja | Filterbaar (met resultaten) |
| sekse | Ja | Filterbaar (met resultaten) |
| fabrikant | Ja | Filterbaar (met resultaten) |
| materiaal | Ja | Filterbaar (met resultaten) |
| doel | Ja | Filterbaar (met resultaten) |
| riem_tassen | Ja | Filterbaar (met resultaten) |
| style_general | Ja | Filterbaar (met resultaten) |

## Standaardsysteemkenmerkeigenschappen

In de volgende tabel worden de standaardzoekeigenschappen en filterbare eigenschappen van systeemkenmerken weergegeven.

| Kenmerkcode | Doorzoekbaar | Gebruiken in gelaagde navigatie |
|--- |--- |--- |
| allow_open_amount | Ja | Filterbaar (met resultaten) |
| beschrijving | Ja | Nee |
| name | Ja | Nee |
| prijs | Ja | Filterbaar (met resultaten) |
| short_description | Ja | Nee |
| sku | Ja | Nee |
| status | Ja | Nee |
| tax_class_id | Ja | Nee |
| url_key | Ja | Nee |
| gewicht | Ja | Nee |
