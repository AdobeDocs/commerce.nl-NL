---
title: Nieuwe aanbeveling maken
description: Leer hoe u een product aanbevelingseenheid kunt maken.
exl-id: 1d5f83c4-1613-4236-9d98-d455f45a47da
source-git-commit: 67d0b98f3a9317c0db944a176fd99375091a3970
workflow-type: tm+mt
source-wordcount: '1512'
ht-degree: 0%

---

# Nieuwe aanbeveling maken

Wanneer u een aanbeveling creeert, creeert u de eenheid van de a _aanbeveling_, of widget, die de geadviseerde product _punten_ bevat.

![&#x200B; eenheid van de Aanbeveling &#x200B;](assets/unit.png)
_eenheid van de Aanbeveling_

Wanneer u de aanbevelingseenheid activeert, begint Adobe Commerce [&#x200B; gegevens &#x200B;](workspace.md) te verzamelen om beelden, meningen, klikken, etc. te meten. In de tabel [!DNL Product Recommendations] worden de maatstaven voor elke aanbevolen eenheid weergegeven om u te helpen geïnformeerde zakelijke beslissingen te nemen.

>[!NOTE]
>
>Metrische gegevens voor productaanbevelingen zijn geoptimaliseerd voor Luma-winkels. Als uw storefront niet-Luma gebaseerd is, hoe de gegevens van het metriekspoor van hoe afhangen u [&#x200B; de gebeurtenisinzameling &#x200B;](events.md) uitvoert.

1. Op _Admin_ sidebar, ga **Marketing** > _Bevorderingen_ > **Aanbevelingen van het Product** om de _9&rbrace; werkruimte van de Aanbevelingen van het Product te tonen._

1. Specificeer de [&#x200B; Mening van de Opslag &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/start/setup/websites-stores-views) waar u de aanbevelingen aan vertoning wilt.

   >[!NOTE]
   >
   > De aanbevelingen van de Bouwer van de pagina moeten de eenheden in de standaardarchiefmening worden gecreeerd, maar kunnen dan overal worden gebruikt. Meer leren over het creëren van productaanbevelingen met de Bouwer van de Pagina, zie [&#x200B; Inhoud toevoegen - de Aanbevelingen van het Product &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations).

1. Klik **creëren Aanbeveling**.

1. In de _Naam uw sectie van de Aanbeveling_, ga een beschrijvende naam voor interne verwijzing, zoals `Home page most popular` in.

1. In de _Uitgezochte paginatype_ sectie, selecteer de pagina waar u de aanbeveling van de volgende opties wilt verschijnen:

   >[!NOTE]
   >
   > De Aanbevelingen van het product worden niet gesteund op de pagina van het Kart wanneer uw opslag aan [&#x200B; wordt gevormd tonen de het winkelwagentje pagina onmiddellijk na het toevoegen van een product aan de kar &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration).

   * Startpagina
   * Categorie
   * Productgegevens
   * Kar
   * Bevestiging
   * [&#x200B; de Bouwer van de Pagina &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations)

   U kunt maximaal vijf actieve aanbevelingen maken voor elk paginatype en maximaal 25 voor Page Builder. Het paginatype wordt grijs weergegeven wanneer de limiet is bereikt.

   ![&#x200B; naam en pagina van de Aanbeveling &#x200B;](assets/create-recommendation.png)
   _naam van de Aanbeveling en paginaplaatsing_

1. In de _Uitgezochte het type van Aanbeveling_ sectie, specificeer het [&#x200B; type van aanbeveling &#x200B;](type.md) u op de geselecteerde pagina wilt verschijnen. Voor sommige pagina&#39;s, is de [&#x200B; plaatsing &#x200B;](placement.md) van aanbevelingen beperkt tot bepaalde types.

1. In de _sectie van het vertoningsetiket van de Storefront_, ga het [&#x200B; etiket &#x200B;](placement.md#recommendation-labels) in dat aan uw kopers zichtbaar is, zoals &quot;Hoogste verkopers&quot;.

1. In _kies aantal producten_ sectie, gebruik de schuif om te specificeren hoeveel producten u in de aanbeveling eenheid wilt verschijnen.

   De standaardwaarde is `5` , met een maximum van `20` .

1. In de _Uitgezochte plaats_ sectie, specificeer de plaats waar de aanbeveling eenheid op de pagina moet verschijnen.

   * Onderaan de hoofdinhoud
   * Bovenaan de hoofdinhoud

1. (Facultatief) om de orde van de aanbevelingen te veranderen, selecteer, en beweeg de rijen in _kiezen positie_ lijst.

   _kies positie_ sectie toont alle (als om het even welk) gemaakte aanbevelingen voor het paginatype u selecteerde.

   ![&#x200B; orde van de Aanbeveling &#x200B;](assets/create-recommendation-select-placement.png)
   _orde van de Aanbeveling op pagina_

1. (Facultatief) in de _sectie van Filters_, [&#x200B; past filters &#x200B;](filters.md) toe om te controleren welke producten in de aanbeveling eenheid verschijnen.

   ![&#x200B; de filters van de Aanbeveling &#x200B;](assets/create-recommendation-filter-products.png)
   _het productfilters van de Aanbeveling_

1. Klik op een van de volgende opties als u klaar bent:

   * **sparen als ontwerp** om de aanbeveling eenheid later uit te geven. U kunt het paginatype of het aanbevelingen type voor een aanbeveling eenheid in een ontwerpstaat niet wijzigen.

   * **activeer** om de aanbeveling eenheid op uw storefront toe te laten.

>[!IMPORTANT]
>
>Sommige browsers blokkeren mogelijk essentiële scripts die verhinderen dat productaanbevelingen naar behoren werken.

## Gereedheidsindicatoren

Gereedheidsindicatoren laten zien welke aanbevolen typen het beste kunnen worden uitgevoerd op basis van de beschikbare catalogus- en gedragsgegevens. U kunt gereedheidsindicatoren ook gebruiken om te bepalen als u kwesties met uw [&#x200B; het verhinderen &#x200B;](events.md) hebt of als u niet genoeg verkeer hebt om het aanbevelingstype te bevolken.

De indicatoren van de bereidheid worden gecategoriseerd in of [&#x200B; op statisch-gebaseerd &#x200B;](#static-based) of [&#x200B; op dynamisch-gebaseerd &#x200B;](#dynamic-based). Alleen catalogusgegevens op basis van statische gegevens gebruiken; terwijl bij dynamisch gebaseerd gebruik gedragsgegevens van uw kopers worden gebruikt. Dat gedragsgegevens worden gebruikt aan [&#x200B; machine het leren modellen &#x200B;](events.md) om gepersonaliseerde aanbevelingen te bouwen en hun bereidheid te berekenen score.

### Hoe gereedheidsindicatoren worden berekend

De gereedheidsindicatoren geven aan hoeveel het model is opgeleid. De indicatoren zijn afhankelijk van de aard van de verzamelde gebeurtenissen, de omvang van de producten waarmee interactie is opgetreden en de omvang van de catalogus.

Het percentage van de gereedheidsindicator wordt afgeleid van een berekening die aangeeft hoeveel producten afhankelijk van het type aanbeveling kunnen worden aanbevolen. De statistieken worden toegepast op producten die op de algemene grootte van de catalogus, het volume van interactie (zoals meningen, klikken, toe:voegen-aan-wortels), en het percentage SKUs worden gebaseerd die die gebeurtenissen binnen een bepaald tijdvenster registreren. Zo kunnen de gereedheidsindicatoren tijdens piekvakantieseizoensverkeer hogere waarden laten zien dan in tijden van normaal volume.

Als gevolg van deze variabelen kan het percentage van de gereedheidsindicator fluctueren. Dit verklaart waarom u zou kunnen zien dat de aanbevelingstypes binnen en uit zijn &quot;bereid zijn op te stellen&quot;komen.

Gereedheidsindicatoren worden berekend op basis van een aantal factoren:

* Voldoende resultaat vastgestelde grootte: Zijn er genoeg resultaten die in de meeste scenario&#39;s worden teruggekeerd om te vermijden gebruikend [&#x200B; reserveaanbevelingen &#x200B;](events.md#backuprecs)?

* Voldoende variëteit van resultaatsets: vertegenwoordigen de producten die worden geretourneerd een verscheidenheid aan producten uit uw catalogus? Het doel van deze factor is te voorkomen dat een minderheid van producten de enige producten is die op de hele site worden aanbevolen.

Op basis van de bovenstaande factoren wordt de gereedheidswaarde als volgt berekend en weergegeven:

* 75% of hoger betekent dat de aanbevelingen voor dat soort aanbevelingen zeer relevant zullen zijn.
* Ten minste 50% betekent dat de aanbevelingen die voor dat soort aanbevelingen worden voorgesteld minder relevant zullen zijn.
* Minder dan 50% betekent dat de aanbevelingen voor dat soort aanbevelingen wellicht niet relevant zijn. In dit geval, [&#x200B; reserveaanbevelingen &#x200B;](events.md#backuprecs) worden gebruikt.

Leer meer over [&#x200B; waarom de gereedheidsindicatoren laag &#x200B;](#what-to-do-if-the-readiness-indicator-percent-is-low) zouden kunnen zijn.

### Op statisch basis

De volgende aanbevelingen zijn op statisch gebaseerd omdat ze alleen catalogusgegevens vereisen. Er worden geen gedragsgegevens gebruikt.

* _meer als dit_
* _Visuele Gelijkaardig_

### Dynamisch gebaseerd

De volgende aanbevelingen zijn dynamisch-gebaseerd omdat zij storefront gedragsgegevens gebruiken.

Laatste zes maanden van storefront gedragsgegevens:

* _Bekeken dit, bekeken dat_
* _Bekeken dit, kocht dat_
* _kocht dit, kocht dat_
* _geadviseerd voor u_

Laatste zeven dagen van gedragsgegevens van de storefront:

* _Meest bekeken_
* _het meest gekochte_
* _Meest toegevoegd aan Kar_
* _Trending_
* _Mening aan de Omzetting van de Aankoop_
* _Mening aan de Omzetting van de Kar_

Meest recente gedragsgegevens van winkels (alleen weergaven):

* _onlangs Bekeken_

### Voortgang visualiseren

Om u te helpen de opleidingsvooruitgang van elk aanbevelingstype visualiseren, _Uitgezochte het type van Aanbeveling_ sectie toont een maatregel van bereidheid voor elk type.

![&#x200B; Type van Aanbeveling &#x200B;](assets/create-recommendation-select-type.png)
_Type van Aanbeveling_

>[!NOTE]
>
>Indicatoren mogen nooit 100% bereiken.

Het percentage van de gereedheidsindicator voor aanbevolen typen die afhankelijk zijn van catalogusgegevens verandert niet veel omdat de catalogus van de handelaar niet vaak verandert. Maar het percentage van de gereedheidsindicator voor aanbevelingen op basis van gedragsgegevens van winkels kan vaak veranderen, afhankelijk van de dagelijkse verkoopactiviteit.

#### Wat moet u doen als het percentage gereedheidsindicator laag is

Een laag gereedheidspercentage geeft aan dat er niet veel producten uit uw catalogus zijn die in aanmerking komen om te worden opgenomen in de aanbevelingen voor dit soort aanbevelingen. Dit betekent dat er een hoge waarschijnlijkheid is dat [&#x200B; reserveaanbevelingen &#x200B;](events.md#backup-recommendations) zijn teruggekeerd als u dit aanbevelingstype hoe dan ook opstelt.

>[!IMPORTANT]
>
>_Bundel_, _gegroepeerde_, en de types van douaneproduct worden niet gesteund. Als uw catalogus een groot aantal van deze producttypen bevat, kunt u een lage gereedheidsscore verwachten. Bovendien, om het even welke SKUs met ruimten kan aanbeveling relevantie verminderen en zou moeten worden vermeden.

In het volgende voorbeeld worden mogelijke redenen en oplossingen voor algemene lage gereedheidsscores weergegeven:

* **op statisch-gebaseerde** - de lage percentages voor deze indicatoren kunnen door ontbrekende catalogusgegevens voor de getoonde producten worden veroorzaakt. Als deze lager zijn dan u had verwacht, kan dit probleem met een volledige synchronisatie worden verholpen.
* **op dynamisch-Gebaseerd** - de Lage percentages voor op dynamisch-gebaseerde indicatoren kunnen door worden veroorzaakt:

   * Ontbrekende gebieden in de vereiste [&#x200B; storefront gebeurtenissen &#x200B;](https://developer.adobe.com/commerce/services/shared-services/storefront-events/#product-recommendations) voor de respectieve aanbevelingen types (requestId, productcontext, etc.)
   * Het lage verkeer op de opslag zodat is het volume van gedragsgebeurtenissen wij ontvangen laag.
   * De verscheidenheid aan storefront gedragsgebeurtenissen over verschillende producten in uw opslag is laag. Als bijvoorbeeld slechts tien procent van uw producten meestal wordt bekeken of gekocht, zijn de respectievelijke gereedheidsindicatoren laag.

## Aanbevelingen voorvertonen {#preview}

Het _Aanbevolen paneel van de productvoorproef_ is altijd beschikbaar met een steekproefselectie van producten die in de aanbeveling eenheid zouden kunnen verschijnen wanneer het aan de opslag wordt opgesteld.

Om een aanbeveling te testen wanneer het werken in een niet productiemilieu, kunt u aanbevelingsgegevens van a [&#x200B; verschillende bron &#x200B;](settings.md) halen. Dit staat verkopers toe om met regels te experimenteren en de aanbevelingen voor te vertonen alvorens aan productie op te stellen.

| Veld | Beschrijving |
|---|---|
| Naam | De naam van het product. |
| SKU | De voorraadbewaareenheid die aan het product is toegewezen |
| Prijs | De prijs van het product. |
| Resultaattype | Primair - geeft aan dat er voldoende trainingsgegevens zijn verzameld om een aanbeveling weer te geven.<br /> Steun - wijst erop dat er niet genoeg opleidingsgegevens worden verzameld zodat wordt een reserveaanbeveling gebruikt om de groef te vullen. Ga naar [&#x200B; Gegevens van het Gedrag &#x200B;](events.md) om meer over machine het leren modellen en reserveaanbevelingen te leren. |

Als u een aanbevolen eenheid maakt, experimenteert u met het paginatype, het aanbevolen type en de filters om direct real-time feedback te krijgen over de producten die worden opgenomen. Aangezien u begint te begrijpen welke producten verschijnen, kunt u de aanbeveling eenheid vormen om aan uw bedrijfsbehoeften te voldoen.

Adobe Commerce [&#x200B; filters &#x200B;](filters.md) aanbevelingen vermijden tonend dubbele producten wanneer de veelvoudige aanbevelingen eenheden op één enkele pagina worden opgesteld. Hierdoor kunnen de producten die in het voorvertoningsvenster worden weergegeven afwijken van de producten die in het voorvertoningsvenster worden weergegeven.

>[!NOTE]
>
> U kunt geen voorvertoning van het `Recently viewed` -aanbevelingen weergeven, omdat de gegevens niet beschikbaar zijn in Admin.
