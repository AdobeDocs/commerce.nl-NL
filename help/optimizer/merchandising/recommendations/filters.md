---
title: Aanbevelingsfilters
description: Leer hoe te om filters te gebruiken om te controleren welke producten in  [!DNL Adobe Commerce Optimizer]  aanbevelingen verschijnen.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is op Adobe Commerce as a Cloud Service en  [!DNL Adobe Commerce Optimizer]  slechts projecten (Adobe-Beheerde infrastructuur SaaS) van toepassing."
exl-id: f6100538-23c0-4e90-9834-a895d4707282
source-git-commit: e15624322fabb89d0b618f9d6c689445a7c448df
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 0%

---

# Filterproducten

[!DNL Adobe Commerce Optimizer] past automatisch niet-configureerbare standaardfilters op aanbeveling-eenheden toe. Als u meerdere aanbevelingen-eenheden op een pagina hebt geïmplementeerd, filtert [!DNL Adobe Commerce Optimizer] alle producten uit die in de eenheden worden herhaald. Alleen de eerste verwijzing naar een herhaald product wordt gebruikt om ruimte te maken voor andere producten die kunnen worden aanbevolen. [!DNL Adobe Commerce Optimizer] filtert ook eerder aangeschafte producten en producten in de kar uit.

Wanneer u [&#x200B; &#x200B;](create.md) creeert een aanbeveling eenheid, kunt u filters bepalen die controleren welke producten in aanbevelingen kunnen worden getoond. Deze filters zijn gebaseerd op een reeks opname- of uitsluitingsvoorwaarden die u definieert. In aanbevelingen worden alleen producten weergegeven die aan alle inclusiemogelijkheden voldoen. Producten die aan een van de uitsluitingsvoorwaarden voldoen, worden niet aanbevolen.

U kunt veelvoudige filters vormen en slechts die toelaten u wilt door de knevel op elke filterpagina te selecteren. Op deze manier kunt u concepten van filters maken voor toekomstig gebruik. Het aantal ingeschakelde filters wordt weergegeven op elk tabblad.

## Voorwaarden

De voorwaarden kunnen statisch of dynamisch zijn.

- Een statische voorwaarde gebruikt bestaande productkenmerken om te bepalen welke producten in de eenheid kunnen verschijnen. U kunt bijvoorbeeld opgeven dat alleen producten in voorraad met een prijs hoger dan € 25 in de eenheid worden weergegeven.

- Een dynamische voorwaardensleutel van de huidige context van een winkelier, zoals de momenteel bekeken categorie of het product. Wanneer u bijvoorbeeld een productaanbeveling maakt die moet worden geïmplementeerd op pagina&#39;s met productdetails, kunt u een voorwaarde maken om alleen producten aan te bevelen die binnen een relatief prijsbereik van het momenteel weergegeven product vallen.

### Logische operatoren

De logische operatoren `AND` en `OR` worden gebruikt om meerdere voorwaarden samen te voegen. Als zowel insluitings- als uitsluitingsfilters worden gebruikt, worden de insluitingen eerst geëvalueerd om te bepalen welke producten kunnen worden aanbevolen, waarna producten die overeenkomen met eventuele uitsluitingsfilters uit de lijst worden verwijderd.

- `AND` - Sluit aan bij twee insluitingsfiltervoorwaarden
- `OR` - Voegt twee uitsluitingsfiltervoorwaarden samen

## Filtertypen

Elk filtertype richt een verschillend aspect van de catalogus, zoals product en prijs, zodat kunt u beperken of uitbreiden welke producten voor een eenheid in aanmerking komen. Kies de typen die overeenkomen met uw marketingdoelstellingen en combineer vervolgens de opname- en uitsluitingsvoorwaarden naar wens. In de subsecties hieronder wordt beschreven hoe elk type zich gedraagt en hoe [!DNL Adobe Commerce Optimizer] dit toepast.

>[!NOTE]
>
>Slechts kunnen de producten die uw **opneming** filters aanpassen worden geadviseerd, en om het even welk product dat een **uitsluitings** filter aanpast wordt verwijderd.

### Prijs

>[!IMPORTANT]
>
>De volgende functie is in bèta.

Het filtreren van de prijs gebruikt definitieve gegevens verwerkte prijs van elk product **voor het actieve prijsboek van de opslag** **- die aan de opslag wordt toegewezen waar de aanbevelingseenheid wordt teruggegeven.** Deze waarde weerspiegelt kortingen, promoties en speciale prijzen die in dat prijzenboek zijn gedefinieerd, en niet alleen de catalogusprijs. Bij de evaluatie wordt alleen gebruik gemaakt van het prijzenboek van die winkel; andere winkeliers of prijzenboeken zijn niet van toepassing. Hoe de prijzenboeken aan een storefront in kaart brengen wordt gevormd met uw catalogus en [&#x200B; prijsboeken &#x200B;](../../setup/pricebooks.md) opstelling.

#### Prijs gebruiken om regels in te voeren en uit te sluiten

- **Regels van de Opsluiting** - slechts producten de waarvan definitieve prijs **alle** bepaalde integratievoorwaarden aanpast blijven in aanmerking komend. Dat omvat elk toegelaten inclusiefilter (bijvoorbeeld, uw prijswaaier plus om het even welke andere inclusieregels).
- **de regels van de Uitsluiting** - Producten de waarvan definitieve prijs **om het even welke** bepaalde uitsluitingsvoorwaarde aanpast worden verwijderd uit aanbevelingen.

**Weergegeven prijs** - de prijs die op producten binnen de aanbevelingseenheid wordt getoond is de zelfde **definitieve prijs** van het de prijsboek van die opslag, zodat wat de kopers de waarde zien die voor het filtreren wordt gebruikt.

#### Prijsfilter instellen

1. Terwijl [&#x200B; creërend of het uitgeven &#x200B;](create.md) een aanbeveling eenheid, open **[!UICONTROL Filter products]** (of ga naar de _stap van Filters_ van het eenheidswerkschema).
1. Selecteer de tab **[!UICONTROL Inclusions]** of **[!UICONTROL Exclusions]** , afhankelijk van de vraag of u alleen producten in een prijsbereik of blokproducten in een bereik wilt toestaan. De badge op elk lusje toont hoeveel filters van dat type worden toegelaten.
1. Selecteer **[!UICONTROL Price]** in de lijst aan de linkerkant.
1. Schakel **[!UICONTROL Enable filter]** in.

   De waarden van de prijs gebruiken de **basismunt van de website**, zoals genoteerd op de pagina.

1. Open **[!UICONTROL Include products based on]** (op de **[!UICONTROL Inclusions]** tab) of het equivalente besturingselement op de **[!UICONTROL Exclusions]** tab en kies **[!UICONTROL Set price range]** .
1. Stel een optioneel **[!UICONTROL Min price]** en/of **[!UICONTROL Max price]** in met de velden naast het valutasymbool. U kunt hoeveelheden typen of de besturingselementen **-** en **+** gebruiken om waarden aan te passen. Laat een gebonden leeg als u geen minimum of maximum nodig hebt. Het bereik wordt vergeleken met de uiteindelijke berekende prijs van elk product voor het actieve prijsboek van de winkel.
1. Voltooi de configuratie van de aanbevolen eenheid en sla op of publiceer deze op de normale manier, zodat het filter van kracht wordt.

![&#x200B; de Filter van de Prijs &#x200B;](../../assets/filter-price.png)

### Product

De filters van het product richten individuele cataloguspunten door **SKU**. U voegt één of meerdere SKUs toe om of slechts die producten toe te staan (**Opnamen**) of hen te blokkeren (**Uitsluitingen**), gebruikend de zelfde **[!UICONTROL Filter products]** pagina zoals [&#x200B; prijsfilters &#x200B;](#price). U kunt uitgeschakelde producten of producten die niet afzonderlijk zichtbaar zijn in een aanbevolen eenheid niet aan de oppervlakte brengen; die producten verschijnen nooit op de opslagruimte ongeacht filters.

#### Een productfilter instellen

1. Terwijl [&#x200B; creërend of het uitgeven &#x200B;](create.md) een aanbeveling eenheid, open **[!UICONTROL Filter products]** (of ga naar de _stap van Filters_ van het eenheidswerkschema).
1. Selecteer de tab **[!UICONTROL Inclusions]** of **[!UICONTROL Exclusions]** . De badge op elk lusje toont hoeveel filters van dat type worden toegelaten.
1. Selecteer **[!UICONTROL Product]** in de lijst aan de linkerkant.
1. Schakel **[!UICONTROL Enable filter]** in.

   De kop in het rechterdeelvenster weerspiegelt de tab, bijvoorbeeld **[!UICONTROL Product inclusions]** of het equivalent voor uitsluitingen.

1. Voer in **[!UICONTROL Product SKU]** een SKU in en klik op **[!UICONTROL Add]** . Herhaal dit om meer SKU&#39;s toe te voegen.

   Onder **[!UICONTROL Product SKUs]** wordt elke SKU weergegeven als een verwijderbare tag. Klik **X** op een markering om die SKU te verwijderen, of klik **[!UICONTROL Clear All]** om elke SKU uit de lijst te verwijderen.

1. Voltooi de configuratie van de aanbevolen eenheid en sla op of publiceer deze op de normale manier, zodat het filter van kracht wordt.

Voor **toevoegingen**, slechts kunnen de producten waarvan SKUs vermeld zijn (en die uw andere toegelaten inclusiefilters tevredenstellen) worden geadviseerd. Voor **uitsluitingen**, wordt om het even welk product waarvan SKU vermeld is niet geadviseerd, zelfs als het anders zou kwalificeren.

![&#x200B; de Filter van het Product &#x200B;](../../assets/filter-product.png)

>[!NOTE]
>
>De producten van het kind van een configureerbaar product worden niet getoond in een aanbeveling eenheid omdat die kindproducten het zicht van _hebben individueel niet Zichtbaar_.

<!--### Attribute

You can filter products based on attribute criteria, including attribute values. Selected values use OR logic to either include or exclude products when any of the specified values are found.-->
