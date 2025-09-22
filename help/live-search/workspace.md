---
title: Live zoeken instellen
description: De  [!DNL Live Search]  werkruimte wordt gebruikt om, onderzoeksprestaties te vormen te beheren en te controleren.
exl-id: 07c32b26-3fa4-4fae-afba-8a10866857c3
source-git-commit: bb212bf88ba7bad3deb2d2d699124413f4dd76ff
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 0%

---

# Live zoeken instellen

In de werkruimte kunt u de prestaties van [!DNL Live Search] configureren, beheren en controleren. Het menu boven biedt toegang tot de gereedschappen in elk functioneel gebied. De beschikbare functies weerspiegelen de huidige menuselectie.

![ Workspace ](assets/workspace.png)

## Gegevensverzameling

Om ervoor te zorgen dat elk functioneel gebied op de werkruimte de correcte gegevens bevat, moet u gegevensinzameling vormen die op de geselecteerde storefront implementatie wordt gebaseerd:

1. Luma - Gegevensverzameling is offline beschikbaar.
1. Headless - De inzameling van Gegevens moet manueel, afhankelijk van storefront implementatie worden gevormd.

Als u een koploze winkel gebruikt, raadpleegt u de volgende documentatie voor meer informatie over de vereiste gebeurtenissen die u moet toevoegen:

- [ Vereiste gebeurtenissen ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#live-search) voor Levend dashboard van het Onderzoek.
- [ de gebeurtenisinzamelaar van de Storefront ](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) die als voorwaarde moet worden toegevoegd.
- [ Voorbeelden ](https://github.com/adobe/commerce-events/tree/main/examples) van de gebeurtenisstructuur.

### Gezondheidszorgklanten

Als u een gezondheidszorgklant bent en u de [ uitbreiding van HIPAA van de Diensten van Gegevens ](../data-connection/hipaa-readiness.md#installation) installeerde, die deel van de [ uitbreiding van de Verbinding van Gegevens ](../data-connection/overview.md) uitmaakt, worden de gegevens van de storefront gebeurtenis die door [!DNL Live Search] worden gebruikt niet meer gevangen. Dit komt doordat gebeurtenisgegevens voor storefront op de client worden gegenereerd. Als u wilt doorgaan met het vastleggen en verzenden van gegevens over storefront-gebeurtenissen, schakelt u gebeurtenisverzameling opnieuw in voor [!DNL Live Search] . Zie [ algemene configuratie ](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/general/general#data-services) om meer te leren.

## Bereik instellen

Aanvankelijk wordt het [ werkingsgebied ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=nl-NL#scope-settings) van alle [!DNL Live Search] montages geplaatst aan `Default Store View`. Als uw [!DNL Commerce] installatie veelvoudige opslagmeningen omvat, plaats **Reikwijdte** aan de [ opslagmening ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html?lang=nl-NL) waar uw facetmontages van toepassing zijn.

## Menuopties

| Optie | Beschrijving |
|--- |--- |
| [ Prestaties ](performance.md) | Het dashboard biedt insight in de zoekprestaties van producten. |
| [ Faceting ](facets.md) | Krachtig filteren waarbij meerdere dimensies van kenmerkwaarden worden gebruikt om zoekcriteria te verfijnen. |
| [ Synoniemen ](synonyms.md) | Breid het bereik van de zoekopdracht uit tot woorden die kopers kunnen gebruiken om producten te zoeken die afwijken van de producten in uw catalogus. |
| [ Merchandising van het Onderzoek ](rules.md) | Vorm de onderzoekservaring met logische regels die geplande acties teweegbrengen. Verhoog, bury, speld, of verberg producten om onderzoeksresultaten te kalibreren om uw bedrijfsdoelstellingen te steunen. |
| [ Merchandising van de Categorie ](category-merch.md) | Pas regels en Intelligent Merchandising op het niveau van de Categorie toe. |
| [ GraphQL ](graphql.md) | Ontwikkelaars die zijn aangemeld bij de beheerder van uw winkel, kunnen query&#39;s samenstellen en testen met werkelijke catalogusgegevens. Meer leren, ga naar [ het Overzicht van GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/) in de [!DNL Live Search] ontwikkelaarsdocumentatie. |
| [ Montages ](settings.md) | Bepaal hoe prijsfacetwaarden worden gegroepeerd op prijsbereik in de winkel en stel de indextaal in. |

## Kenmerken instellen als doorzoekbaar

Om hoogst-gerichte resultaten te veroorzaken, herzie de reeks [ doorzoekbare ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html?lang=nl-NL) (`searchable=true`) productattributen. Om relevantie te verzekeren, maak attributen doorzoekbaar slechts als zij inhoud bevatten die een duidelijke en beknopte betekenis heeft. Vermijd het gebruik van kenmerken die minder nauwkeurige, lange tekst bevatten, zoals `description` . Deze tekst kan de precisie van zoekresultaten verminderen, hoewel deze functie standaard is ingeschakeld. Als iemand bijvoorbeeld zoekt naar &quot;korte broeken&quot; en er overhemden zijn met een beschrijving die de term &quot;korte mouwen&quot; bevat, worden de overhemden opgenomen in de zoekresultaten.

Voer de volgende stappen uit om te zorgen dat kenmerken doorzoekbaar zijn:

1. In Admin, ga **>** Attribuut *>* Product **.**
1. Selecteer het kenmerk dat u wilt doorzoeken, bijvoorbeeld `color` .
1. Selecteer **Eigenschappen van 0&rbrace; Storefront en plaats** Gebruik in Onderzoek **aan**.`yes`

   ![ Workspace ](assets/attribute-searchable.png)

[!DNL Live Search] respecteert ook het [ gewicht ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html?lang=nl-NL#weighted-search) van een productattribuut, zoals die binnen Adobe Commerce wordt geplaatst. Kenmerken met een hogere dikte worden hoger weergegeven in de zoekresultaten.

De volgende kenmerken kunnen altijd worden doorzocht:

- `sku`
- `name`
- `categories`

[ Facets ](facets.md) zijn productattributen die in [!DNL Live Search] worden bepaald om filtreerbaar te zijn. U kunt om het even welk filtrable attribuut als facet in [!DNL Live Search] plaatsen, maar er zijn [ grenzen ](boundaries-limits.md) aan hoeveel facetten u in één keer kunt zoeken.

>[!NOTE]
>
>Een productattribuut is filtreerbaar slechts als de configuratie van het productattribuut de vereiste eigenschappen heeft: *Gebruik in Onderzoek = ja*, *Gebruik in Gelaagd Navigation=yes van het Onderzoek resultaten*, en *Gebruik in Gelaagd Navigation=Filterable (met resultaten)*. Als deze eigenschappen ontbreken, is het attribuut niet zichtbaar in de configuratie van Facet. Voor configuratieinstructies, zie [ een Facet ](facets-add.md#add-a-facet) toevoegen.

[ Synoniemen ](synonyms.md) zijn termijnen die u kunt bepalen helpen gebruikers aan het correcte product begeleiden. Gebruikers die op zoek zijn naar een broek kunnen &#39;broek&#39; of &#39;slacks&#39; typen. U kunt synoniemen zodanig instellen dat deze zoektermen gebruikers naar de resultaten van de &#39;&#39;broek&#39;&#39; brengen.

## Commerce-configuratie-instellingen

In de volgende sectie worden de ondersteunde en niet-ondersteunde Commerce-configuratie-instellingen voor [!DNL Live Search] beschreven.

### Ondersteunde configuratiewaarden

>[!IMPORTANT]
>
>We raden u aan de widgets voor productlijsten te gebruiken. Deze zijn standaard ingeschakeld in Live Search 4.0.0. De widgets zijn bedoeld om de adapterimplementatie in toekomstige versies volledig te vervangen. Zie [ product toelaten lijst widgets ](install.md#enable-product-listing-widgets) om meer te leren.

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
| Winkels > Configuratie > Catalogus > Storefront > Productaanbieding sorteren op | Hiermee bepaalt u de sorteervolgorde van de lijst met zoekresultaten. | Is niet op [!DNL Live Search] van toepassing [ Product het Van een lijst weergeven Widget van de Pagina ](plp-styling.md) |

### Zoektermen

[!DNL Live Search] steunt [ herleidt van de onderzoekstermijn ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html?lang=nl-NL) op implementaties waar Adobe Commerce het verpletteren, zoals op Luma en andere op php-Gebaseerde thema&#39;s behandelt.
