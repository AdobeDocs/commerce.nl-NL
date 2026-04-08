---
title: Regels maken en beheren
description: Leer hoe u regels voor het zoeken, standaardaanbiedingen van producten en rubriekpagina's maakt en beheert.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is op Adobe Commerce as a Cloud Service en  [!DNL Adobe Commerce Optimizer]  slechts projecten (Adobe-Beheerde infrastructuur SaaS) van toepassing."
exl-id: fd4df2b2-83de-4c5c-b18c-e97aa07ef8f6
source-git-commit: 0d1ebaddada8be82645164368ebfbb6dd0a569cd
workflow-type: tm+mt
source-wordcount: '2714'
ht-degree: 0%

---

# Regels maken en beheren

Om een regel te bouwen, open de regelredacteur, kies a **regeltype** (onderzoeksvoorwaarden, standaard lijst, of categoriepagina&#39;s), dan bepaal voorwaarden en rangschikking waar zij van toepassing zijn, test de resultaten, en publiceer de regel.

## Een regel maken {#create-a-rule}

1. In het linkerspoor, ga _Merchandising_ > **Regels van het Merchandising**.
1. (Facultatief) gebruik **drop-down van de mening van de Catalogus** om de catalogusmening te selecteren waar de regel zou moeten van toepassing zijn. De regel u creeert is scoped aan de geselecteerde mening (of aan alle catalogusmeningen als **Alle meningen** wordt geselecteerd). Zie [&#x200B; Uitgezochte catalogusmening &#x200B;](workspace.md#select-catalog-view) voor hoe de catalogusmening het scoping werkt.

   >[!IMPORTANT]
   >
   >De meningen van de catalogus zijn momenteel in [&#x200B; bèta &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/release/beta#merchandising-rules-globally-and-per-catalog-view-public-beta). Beta-deelnemers moeten bestaande regels voor het wijzigen van winkels opnieuw maken om te kunnen profiteren van het nieuwe weergavebereik voor catalogi.

1. Klik op **[!UICONTROL Create rule]** om de regeleditor te starten.

![&#x200B; creeer Regel &#x200B;](../../assets/create-rule.png)

### Regeltypen

Elk regeltype heeft een informatiepictogram in de redacteur met een korte verklaring. Gebruik het type dat overeenkomt met de locatie waar de koper de logica voor het wijzigen van handelsversies moet zien:

| Type regel | Doel |
| --- | --- |
| **Alle producten regel** | Standaardclassificatie en -verkoop in productaanbiedingen als er geen specifieke regel voor zoeken of rubrieken van toepassing is. U kunt slechts één dergelijke regel maken; deze mag geen voorwaarden bevatten. |
| **regel van de Categorie** (Beta) | Hiermee past u merchandising en rangschikking toe op een of meer geselecteerde categorieën, waarbij de productvolgorde op die categoriepagina&#39;s wordt bepaald. |
| **regel van het Onderzoek** | Past merchandising en rangschikking toe wanneer de kopers een onderzoek in werking stellen dat de de vraagvoorwaarden van de regel aanpast. |

In **bouwt uw regel** sectie, bepaalt u de regelnaam, programma, of de regel op alle lijsten of op specifieke onderzoeksvoorwaarden, en het rangschikken types van toepassing is.

1. Voer in het veld **[!UICONTROL Name]** een naam voor de regel in. Alle regelnamen moeten uniek zijn.
1. Voer in het veld **[!UICONTROL Description]** een beschrijving van de regel in.
1. Geef in het veld **[!UICONTROL Date range]** de datum of het datumbereik op waarop de regel actief moet zijn.
1. In de **[!UICONTROL Rule applies to]** sectie, selecteer het [&#x200B; regeltype &#x200B;](#rule-types) u wilt gebruiken.

>[!BEGINTABS]

>[!TAB  regel van het Onderzoek ]

Een zoekregel past merchandising- en ranking-logica toe wanneer kopers een zoekopdracht uitvoeren die overeenkomt met de gedefinieerde voorwaarden.

De voorwaarden zijn de vereisten om een gebeurtenis te activeren. Een regel kan tot tien voorwaarden en 25 gebeurtenissen hebben. Een standaardregel kan geen voorwaarden hebben.

![&#x200B; Uitgezochte Voorwaarde van de Regel &#x200B;](../../assets/rule-set-condition.png)

**Enige voorwaarde**

1. Onder *bouwt uw regel*, selecteer de **Voorwaarde** om te ontmoeten, en volg de instructies om de verklaring te voltooien.

   - Zoekquery bevat - Voer de tekenreeks in die in de query van de winkels moet staan. De instelling Afstemmen bepaalt de mate waarin de query van de winkels overeenkomt met de catalogus. Opties:<br /> om het even welk - om het even welk deel van de vraagtekst van de verkoopster kan de voorwaarde aanpassen.<br /> allen - allen van de vraag van de verkoopster moet de voorwaarde aanpassen.
   - Zoekquery is - Voer een tekenreeks in die exact overeenkomt met de query van de verkoper. Bijvoorbeeld: &quot;yoga broek&quot;. Regels met `Search query is` en overeenkomsten `All` kunnen slechts één voorwaarde hebben.
   - Zoekopdracht begint met - Voer een teken of tekenreeks in die aan het begin van de zoekopdracht van de gebruiker moet staan.
   - Zoekopdracht eindigt met - Voer een teken of tekenreeks in die aan het einde van de zoekopdracht van de gebruiker moet staan.

   De resultaten verschijnen onmiddellijk in *Test uw regel* ruit en genummerd door prioriteit. U kunt de *Resultaten per rij* schuif in het hogere recht gebruiken om het aantal producten in elke rij te veranderen.

1. Om andere vragen te testen, verander de vraagtekst in de *Test uw doos van het regel* onderzoek en druk **Terugkeer**.
Aanvankelijk, geeft de testruit de vraag van het de onderzoeksvakje van de Voorwaarden terug. Maar nu geeft het de vraag van de doos van de testvraag terug. De testruit geeft slechts één vraag tegelijkertijd terug.
1. Als u van het resultaat houdt, werk de tekst in het *Voorwaarden* onderzoeksvakje bij. Klik vervolgens ergens op de pagina om de resultaten in het testvenster bij te werken.
1. Plaats [&#x200B; Intelligente het rangschikken &#x200B;](#intelligent-ranking) en [&#x200B; het Handmatig rangschikken &#x200B;](#manual-ranking) zoals die in de volgende secties wordt beschreven. Dezelfde besturingselementen zijn van toepassing op categoriepagina&#39;s, met alle opgevraagde verschillen.

**Veelvoudige voorwaarden**

1. Om een regel met veelvoudige voorwaarden te bouwen, klik **toevoegt voorwaarde**.
Een regel kan tot tien voorwaarden hebben. De logische exploitant die zich bij twee voorwaarden aansluit is gebaseerd op het huidige *plaatsen van de Gelijke*. Door gebrek, *Gelijke* is `All` en de logische exploitant is `AND`.

1. Selecteer de tweede voorwaarde en voer de vereiste querytekst in.

1. Om de logica van de regel te veranderen, verander **Gelijke** het plaatsen om te bepalen hoe dicht de het onderzoekscriteria van de verkoopster de vraagvoorwaarde moeten aanpassen. Plaats **Gelijke** aan één van het volgende:

   - Alle - (standaard) Alle logische operatoren in de regel zijn ingesteld op `OR` en de resultaten worden weergegeven in het testvenster.
   - Alles - Alle logische operatoren in de regel zijn ingesteld op `AND` en de resultaten worden weergegeven in het testvenster.

   De *gelijke* waarde bepaalt de logische exploitant die wordt gebruikt om zich bij veelvoudige voorwaarden aan te sluiten. Het veranderen van *Gelijke* het plaatsen verandert alle logische exploitanten in de regel. Het is niet mogelijk `AND` en `OR` in dezelfde regel te combineren.

   In dit voorbeeld zijn er twee aparte query&#39;s die zoeken naar &#39;yoga&#39; of &#39;broek&#39; in plaats van naar &#39;yoga-broek&#39; te zoeken. Deze regel is minder specifiek en wordt vaker geactiveerd in de winkel dan in de andere.

1. Om een andere voorwaarde toe te voegen, **voegt voorwaarde** toe en herhaalt het proces.
1. Plaats [&#x200B; Intelligente het rangschikken &#x200B;](#intelligent-ranking) en [&#x200B; het Handmatig rangschikken &#x200B;](#manual-ranking) zoals die in de volgende secties wordt beschreven. Dezelfde besturingselementen zijn van toepassing op categoriepagina&#39;s, met alle opgevraagde verschillen.

>[!TAB  regel van de Categorie ]

>[!IMPORTANT]
>
>Categorieregels staan in bèta.

De regels van de categorie controleren hoe de producten op **categoriepagina&#39;s** worden bevolen. U combineert **categorieregels** met **intelligente rangschikking** (met inbegrip van AI-gedreven signalen), en **handboek** acties zoals speld, verhoging, en begraving-zodat kunt u ontdekking, looppas bevorderingen, en lijnt categoriepagina&#39;s met uw strategie zonder zich op externe hulpmiddelen te baseren.

1. Onder **Categorieën**, selecteer de categorie of de categorieën de regel zou moeten van toepassing zijn. De geselecteerde categorieën verschijnen onder de controle zodat kunt u het werkingsgebied bevestigen.
1. In de lijst met categorieën die worden weergegeven, kunt u op de drie punten klikken en selecteren:

   - **Schrapping** - verwijdert de categorie uit de regel.
   - **is op subcategorieën** van toepassing - past de regel op subcategorieën toe die reeds geen actieve handelsnormregel hebben die wordt bepaald.
   - **Voorproef** - toont hoe de categoriepagina op uw storefront zou verschijnen.

1. Plaats [&#x200B; Intelligente het rangschikken &#x200B;](#intelligent-ranking) en [&#x200B; het Handmatig rangschikken &#x200B;](#manual-ranking) zoals die in de volgende secties wordt beschreven. De zelfde controles zijn op onderzoeksregels van toepassing, met om het even welke geroepen verschillen.

>[!ENDTABS]

### Intelligente classificatie {#intelligent-ranking}

De intelligente rangschikkende ordeproducten die **gedragssignalen** gebruiken en, waar van toepassing, AI. Het is op **onderzoeksregels** van toepassing, **alle productlijsten** (standaardregels), en **categorieregels** (categoriepagina&#39;s). Voor verkoopster **onderzoeken**, weegt het rangschikken ook **tekstuele relevantie** aan de vraag; **categoriepagina&#39;s** gebruiken vraagtekst op de zelfde manier-redacteur zich op gedragsstrategieën concentreert.

Winkeleigenaars kunnen strategieën zoals de volgende instellen. De nauwkeurige etiketten en de tijdvensters passen de regelredacteur aan en kunnen lichtjes door regeltype verschillen.

![&#x200B; Intelligente Rankings &#x200B;](../../assets/rule-intelligent-ranking.png)

- **het meest gekochte** / **het meest gekochte** — Draait door aankoopfrequentie per SKU in een recent venster (bijvoorbeeld, de vorige 7 dagen voor onderzoekscontexten).
- **het meest toegevoegd aan wagentje** — Ranks door totale toe:voegen-aan-kartactiviteit in een recent venster (bijvoorbeeld, de vorige 7 dagen voor onderzoekscontexten).
- **het meest bekeken** — Draait door meningen per SKU in een recent venster (bijvoorbeeld, de vorige 7 dagen voor onderzoekscontexten).
- **geadviseerd voor u** — Gebruikt het `viewed-viewed` signaal: Kopers die dit SKU bekeken ook andere SKUs bekeken; steunt gepersonaliseerde het opdracht geven tot op categoriepagina&#39;s waar beschikbaar.
- **Trending** - benadrukt recente populariteit (voor onderzoek, paginameningen over de afgelopen 72 uren voor achtergrondgebeurtenissen en 24 uren voor voorgrondgebeurtenissen).
- **niets** - voor onderzoek en standaardlijsten, worden de producten bevolen door **Relevantie**. Voor **categorieregels**, gebruikt de standaard handelende orde voor de categorie wanneer u geen andere intelligente strategie kiest.

Selecteer de strategie voor uw regel. De **Test uw regel** ruit toont verwachte resultaten voor onderzoek-georiënteerde regels; **categorieregels** gebruiken de categorievoorproef.

#### Hoe intelligent het rangschikken (onderzoek) werkt

Voor **onderzoeksresultaten** (en de testvraag in de regelredacteur), bepaalt het intelligente rangschikken de definitieve productorde door twee zeer belangrijke factoren te combineren: **tekstuele relevantie** en **gedragssignalen**. Als u begrijpt hoe deze factoren op elkaar inwerken, kunt u realistische verwachtingen voor uw zoekresultaten instellen.

**het Scoren componenten:**

- **Textual relevantie**: De dominante factor in het noteren. Op deze manier wordt gemeten hoe goed de naam, beschrijving en kenmerken van een product overeenkomen met de zoekquery. De relevantiescore van de tekst is onbegrensd (heeft geen specifieke bovengrens) en wordt beïnvloed door factoren zoals:

   - Frequentie waarop overeenkomende woorden voorkomen.
   - Lengte (in woorden) van productnamen/beschrijvingen.

- **gedragssignalen**: Een begrensde verhoging die op de score van de tekstrelevantie wordt toegepast. Wanneer u een intelligente rangschikkingsstrategie selecteert zoals &quot;Meest bekeken&quot; of &quot;Meest aangekocht&quot;, krijgen producten met hogere gedragssignalen een vaste stimulans voor hun scores. Deze verhoging heeft echter een bepaalde limiet.

**waarom het meest bekeken product niet eerst zou kunnen verschijnen:**

De tekstuele relevantie domineert doorgaans de rangschikking omdat de score onbegrensd is, terwijl de gedragsversterking vast is. Als gevolg hiervan komen producten met sterke tekst vaak meer overeen dan producten met hogere betrokkenheidssignalen. Gedragingen alleen compenseren mogelijk grote leemten in de relevantie van tekst niet. De intelligente rangschikking richt dit door in zowel gelijke kwaliteit als winkelinteractie rekening te houden, verbeterend algemene relevantie. Kwaliteit van tekstovereenkomsten blijft echter het belangrijkste stuurprogramma voor de classificatie.

**Voorbeeld:**

Een handelaar gebruikt de &quot;meest bekeken&quot;intelligente rangschikkingsstrategie en zoekt naar &quot;kaars.&quot; Ze verwachten dat het product SKU YAN-K-E-512 boven aan de resultaten wordt weergegeven, omdat het de hoogste weergavetelling heeft. Andere producten zijn echter hoger:

- **de Kaars van Texas** (1ste positie): Heeft een kortere, schonere productnaam die tot een zeer hoge score van de tekstrelevantie leidt. Hoewel de tekst minder weergaven heeft dan YAN-K-E-512, is de superieure tekst groter dan de gedragsverhoging.

- **YAN-K-E-512** (lagere positie): Ondanks het hebben van het hoogste meningspercentiel in de &quot;Meest bekeken&quot;gedragsgegevens, produceert zijn complexe op SKU-Gebaseerde naam een lagere score van de tekstrelevantie. De vaste gedragsstimulans is niet genoeg om deze leemte in de relevantie van de tekst te overbruggen.

Zie [&#x200B; onderzoeksregels &#x200B;](./best-practice.md#tips-to-optimize-search-rules) leren hoe te om productfindability te verbeteren gebruikend regels.

#### Caveats

- Apostroffen en aanhalingstekens in query&#39;s kunnen leiden tot enkele kleine problemen met rangschikking en relevantie in sommige talen.
- Om intelligente het rangschikken te verzekeren werkt correct voor **onderzoek**, zorg ervoor dat het **Gewicht van het Onderzoek** voor om het even welke attributen die voor onderzoek of het filtreren (facetten) worden gebruikt `5` of minder is. (Deze leidraad is van toepassing op zoekindexering, niet op transactiestromen die alleen voor categorieën gelden.)

Voor informatie over het plaatsen van onderzoeksdikten, zie [&#x200B; Meta-gegevens API &#x200B;](https://developer.adobe.com/commerce/services/reference/rest/).

### Handmatige classificatie {#manual-ranking}

**het Handmatig rangschikken** gebeurtenissen passen productorde voor **onderzoeksresultaten** (wanneer de voorwaarden van uw regel), voor **standaardproductlijsten**, en voor **categoriepagina** lijsten worden voldaan. Eén regel kan maximaal 25 gebeurtenissen bevatten.

- **Verhoging** - verplaatst een product hoger in de lijst.
- **Doordrukken** - verplaatst een SKU lager in de lijst.
- **Vastzetten een product** — Bevestigt een product bij de geselecteerde positie in de lijst.
- **verberg een product** - sluit SKU van de resultaten (onderzoek-georiënteerd; bevestig gedrag voor categorieregels in de redacteur) uit.

De eenvoudigste manier om een product vast te zetten is door te slepen en neer te zetten.

1. Klik en sleep een product in het deelvenster Testen. Sleep de aanwijzer naar de gewenste positie. De velden Product en Positie worden automatisch ingevuld in het deelvenster Gebeurtenissen.

U kunt ook op het speldpictogram klikken om een product op de huidige locatie vast te zetten. Gebruik het contextmenu voor ovalen om &#39;Aan de bovenkant vastzetten&#39; of &#39;Aan de onderkant vastzetten&#39;.

>[!NOTE]
>
>**de regels van het Onderzoek** — U kunt slechts producten vastzetten die in de onderzoeksresultaten voor de gevormde vraag en regelvoorwaarden verschijnen. De producten moeten worden geïndexeerd, zichtbaar, in voorraad, en voldoen aan alle regelfilters om voor het pinnen in aanmerking te komen. Als een product niet in de voorvertoning of in de resultaten voor uw regel wordt weergegeven, heeft het vastzetten geen effect.
>
>**Standaard soort** - de Handmatige posities zijn van toepassing wanneer de verkoopster de standaardsoort gebruikt: **Soort door: Het meest relevante** voor onderzoek, of **relevantie** / **positie** voor categorielijsten. Als de sortering van de winkels wordt gewijzigd, bijvoorbeeld door een naam, vastgezet, gebrand, begraven of verborgen gedrag, komt deze mogelijk niet meer overeen met de voorvertoning.

Of gebeurtenissen kunnen handmatig worden ingesteld:

1. Onder *Gebeurtenissen*, kies de **Gebeurtenis** om te gebeuren wanneer de bijbehorende voorwaarden worden voldaan.

   Kies bijvoorbeeld `Hide a product` . Voer vervolgens de naam in van het product dat u wilt verbergen. Producten worden voorgesteld terwijl u typt.

1. Voor meerdere gebeurtenissen kiest u andere gebeurtenissen die u wilt activeren als aan de voorwaarden is voldaan.

### De regel voltooien {#finalizing-the-rule}

1. Onderzoek de resultaten van de regel in de testruit.
1. Als de regel veelvoudige vragen heeft, test elk die door de regel zou kunnen worden beïnvloed.
1. Wanneer volledig, klik **sparen en publiceer**.

   De regel wordt toegevoegd aan de lijst in de *1&rbrace; werkruimte van Regels &lbrace;.*

1. Hoewel de actieve regels onmiddellijk in werking treden, zou u tot 15 minuten kunnen moeten wachten op de caching vraagresultaten in de storefront om worden verfrist.

>[!NOTE]
>
>De regels en manueel gerangschikte producten worden toegepast op **onderzoek** resultaten wanneer de standaardsoortorde, &quot;Soort door: Relevant,&quot;wordt geselecteerd. Als een winkelier de sorteervolgorde wijzigt in een sorteervolgorde op naam, zijn de regels en handmatige waarderingen niet meer van kracht. Voor **categorie** lijsten, gebrek-soort gedrag wordt beschreven in [&#x200B; het Handboek rangschikken &#x200B;](#manual-ranking).

## Regels bewerken, weergeven en verwijderen {#edit-view-and-delete-rules}

Volg deze instructies om de eigenschappen van bestaande regels bij te werken. U kunt de catalogusweergave (bereik) van een regel niet wijzigen nadat deze is gemaakt; het bereik wordt ingesteld wanneer u de regel maakt. Zie [&#x200B; Uitgezochte catalogusmening &#x200B;](workspace.md#select-catalog-view).

### Regel bewerken

1. Op de *Merchandising regels* werkruimte, vind de regel in het net dat u **Meer** (...) opties uitgeven en wilt klikken.
1. Klik **uitgeven** om tot de regelredacteur toegang te hebben.
1. Werk de voorwaarden, operatoren en gebeurtenissen naar wens bij.
1. Werk de naam, de begin- en einddatum en beschrijvingsvelden naar wens bij. Alle regelnamen moeten uniek zijn.
1. Test de regel.
1. Publiceer de wijzigingen.
De regel wordt toegevoegd aan de lijst in de *1&rbrace; werkruimte van Regels &lbrace;.* Hoewel de actieve regels onmiddellijk in werking treden, zou het tot 15 minuten voor caching vraagresultaten in de storefront kunnen verfrissen vergen.

### Details weergeven

Deze optie verstrekt een snelle manier om alle regelparameters te zien, terwijl het blijven op de *Regels* lijst.

1. Op de *Merchandising regels* werkruimte, vind de regel in het net dat u **Meer** (...) opties uitgeven en wilt klikken.
1. Klik **details van de Mening** om de regelparameters te bekijken.
1. Kies **uitgeven** of **Schrapping**, of klik X om het paneel te sluiten.

### Regel verwijderen

1. Op de *Regels* werkruimte, vind de regel in het net dat u **Meer** (...) opties uitgeven en wilt klikken.
1. Klik **Schrapping**.

## Veldomschrijvingen {#field-descriptions}

### Voorwaarden (indien)

| Voorwaarde | Beschrijving |
|--- |--- |
| Zoekquery bevat | Een teken of tekenreeks die wordt opgenomen in de query van de winkelier. De vraag van de verkoopster moet slechts één enkel karakter aanpassen om aan deze voorwaarde te voldoen. |
| Zoekquery is | Een teken of tekenreeks die exact overeenkomt met de query van de winkelier. Complexe query&#39;s met meerdere voorwaarden kunnen niet worden samengesteld wanneer deze voorwaarde wordt gebruikt. |
| Zoekquery begint met | De query van de winkelier begint met dit teken of deze tekenreeks. |
| Zoekquery eindigt met | De zoekopdracht van de klant eindigt met dit teken of deze tekenreeks. |

### Logische operatoren

| Operator | Beschrijving |
|--- |--- |
| OF | (Standaard) De logische operator `OR` vergelijkt twee voorwaarden en voldoet aan de vereisten om een gebeurtenis te activeren als minstens één voorwaarde waar is. |
| EN | De logische operator `AND` vergelijkt twee voorwaarden en voldoet aan de vereisten om een gebeurtenis te activeren als beide voorwaarden true zijn. |

### Operatoren afstemmen

| Operator | Beschrijving |
|--- |--- |
| Alle | Wijzigt alle logische operatoren in de regel in `OR` en retourneert de set overeenkomende producten. |
| Alles | Wijzigt alle logische operatoren in de regel in `AND` en retourneert de set overeenkomende producten. |

### Handmatige waarderingsgebeurtenissen

| Gebeurtenis | Beschrijving |
|--- |--- |
| Verhogen | Hiermee verplaatst u een SKU of reeks SKU&#39;s hoger in de lijst (zoekopdracht of categorie). Elk object wordt in de testresultaten gemarkeerd met een &#39;gebooste&#39; voorvertoningssymbool. |
| Bury | Hiermee verplaatst u een SKU of reeks SKU&#39;s lager in de lijst. Elk object wordt in de testresultaten gemarkeerd met een voorvertoningssymbool &quot;begraven&quot;. |
| Een product vastzetten | Koppelt één SKU aan een specifieke positie in de lijst. Het product wordt in de testresultaten gemarkeerd met een voorvertoningssymbool &quot;vastgezet&quot;. |
| Een product verbergen | Sluit SKU, of waaier van SKUs, van de resultaten (onderzoek-georiënteerd; bevestig voor categorieregels in de redacteur) uit. |

### Details

| Veld | Beschrijving |
|--- |--- |
| Naam | De naam van de regel. Regelnamen moeten uniek zijn. |
| Type regel | **Gebrek** (alle productlijsten), **Vraag** (specifieke onderzoeksvoorwaarden), of **Categorie** (categoriepagina&#39;s), afhankelijk van **Regel is op** van toepassing. |
| Begindatum | De begindatum van de regel, indien gepland. |
| Einddatum | De einddatum van de regel, indien gepland. |
| Beschrijving | Een korte beschrijving van de regel. |
