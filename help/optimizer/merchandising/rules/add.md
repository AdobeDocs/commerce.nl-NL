---
title: Regels maken en beheren
description: Leer hoe u handelsregels maakt en beheert.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: fd4df2b2-83de-4c5c-b18c-e97aa07ef8f6
source-git-commit: bd54ff7afb0b6a5d78098225a8f98f81f96a7923
workflow-type: tm+mt
source-wordcount: '2146'
ht-degree: 0%

---

# Regels maken en beheren

Om een regel te bouwen, moet de eerste stap de regelredacteur gebruiken om de voorwaarden in de vraagtekst van de klant te bepalen die de bijbehorende gebeurtenissen teweegbrengen. Dan, voltooi de regeldetails, test de resultaten, en publiceer de regel.

## Een regel maken

1. In het linkerspoor, ga _Merchandising_ > **Regels van het Merchandising**.
1. Klik **creeer regel** om de regelredacteur te lanceren.

![&#x200B; creeer Regel &#x200B;](../../assets/create-rule.png)

In **bouwt uw regel** sectie, bepaalt u specifieke onderzoekscriteria, voorwaarden, en het rangschikken types.

1. Voer in het veld **[!UICONTROL Name]** een naam voor de regel in. Alle regelnamen moeten uniek zijn.
1. Voer in het veld **[!UICONTROL Description]** een beschrijving van de regel in.
1. Geef in het veld **[!UICONTROL Date range]** de datum of het datumbereik op waarop de regel actief moet zijn.
1. In de sectie **[!UICONTROL Rule applies to]** hebt u twee opties: **[!UICONTROL All product listings]** of **[!UICONTROL Specific conditions]** .

   - **Alle productlijsten** - dit is hoofdzakelijk uw standaardregel en toegepast op alle onderzoeksvragen, tenzij een specifiekere onderzoeksvraag wordt bepaald. U kunt slechts één standaardregel maken en deze mag geen voorwaarden bevatten. Kies het Intelligente ranking type en eventuele handmatige classificaties die u wilt toepassen op alle standaardzoekopdrachten.
   - **Specifieke voorwaarden** - zie de volgende sectie over de soorten voorwaarden leren u voor uw regel kunt plaatsen.

### Voorwaarden

Voorwaarden zijn de vereisten om een gebeurtenis te activeren. Een regel kan tot tien voorwaarden en 25 gebeurtenissen hebben. Een standaardregel kan geen voorwaarden hebben.

![&#x200B; Uitgezochte Voorwaarde van de Regel &#x200B;](../../assets/rule-set-condition.png)

#### Eén voorwaarde

1. Onder *bouwt uw regel*, selecteer de **Voorwaarde** om te ontmoeten, en volg de instructies om de verklaring te voltooien.

   - Zoekquery bevat - Voer de tekenreeks in die in de query van de winkels moet staan. De instelling Afstemmen bepaalt de mate waarin de query van de winkels overeenkomt met de catalogus. Opties:<br /> om het even welk - om het even welk deel van de vraagtekst van de verkoopster kan de voorwaarde aanpassen.<br /> allen - allen van de vraag van de verkoopster moet de voorwaarde aanpassen.
   - Zoekquery is - Voer een tekenreeks in die exact overeenkomt met de query van de verkoper. Bijvoorbeeld: &quot;yoga broek&quot;. Regels met `Search query is` en overeenkomsten `All` kunnen slechts één voorwaarde hebben.
   - Zoekopdracht begint met - Voer een teken of tekenreeks in die aan het begin van de zoekopdracht van de gebruiker moet staan.
   - Zoekopdracht eindigt met - Voer een teken of tekenreeks in die aan het einde van de zoekopdracht van de gebruiker moet staan.

   De resultaten verschijnen onmiddellijk in *Test uw regel* ruit en genummerd door prioriteit. U kunt de *Resultaten per rij* schuif in het hogere recht gebruiken om het aantal producten in elke rij te veranderen.

1. Om andere vragen te testen, verander de vraagtekst in de *Test uw doos van het regel* onderzoek en druk **Terugkeer**.
Aanvankelijk, geeft de testruit de vraag van het de onderzoeksvakje van de Voorwaarden terug. Maar nu geeft het de vraag van de doos van de testvraag terug. De testruit geeft slechts één vraag tegelijkertijd terug.
1. Als u van het resultaat houdt, werk de tekst in het *Voorwaarden* onderzoeksvakje bij. Klik vervolgens ergens op de pagina om de resultaten in het testvenster bij te werken.

#### Meerdere voorwaarden

1. Om een regel met veelvoudige voorwaarden te bouwen, klik **toevoegt voorwaarde**.
Een regel kan tot tien voorwaarden hebben. De logische exploitant die zich bij twee voorwaarden aansluit is gebaseerd op het huidige *plaatsen van de Gelijke*. Door gebrek, *Gelijke* is `All` en de logische exploitant is `AND`.

1. Selecteer de tweede voorwaarde en voer de vereiste querytekst in.

1. Om de logica van de regel te veranderen, verander **Gelijke** het plaatsen om te bepalen hoe dicht de het onderzoekscriteria van de verkoopster de vraagvoorwaarde moeten aanpassen. Plaats **Gelijke** aan één van het volgende:

   - Alle - (standaard) Alle logische operatoren in de regel zijn ingesteld op `OR` en de resultaten worden weergegeven in het testvenster.
   - Alles - Alle logische operatoren in de regel zijn ingesteld op `AND` en de resultaten worden weergegeven in het testvenster.

   De *gelijke* waarde bepaalt de logische exploitant die wordt gebruikt om zich bij veelvoudige voorwaarden aan te sluiten. Het veranderen van *Gelijke* het plaatsen verandert alle logische exploitanten in de regel. Het is niet mogelijk `AND` en `OR` in dezelfde regel te combineren.

   In dit voorbeeld zijn er twee aparte query&#39;s die zoeken naar &#39;yoga&#39; of &#39;broek&#39; in plaats van naar &#39;yoga-broek&#39; te zoeken. Deze regel is minder specifiek en wordt vaker geactiveerd in de winkel dan in de andere.

1. Om een andere voorwaarde toe te voegen, **voegt voorwaarde** toe en herhaalt het proces.

### Intelligente classificatie

De intelligente rangschikking combineert gebruikersgedrag en plaatsstatistieken om productrangschikking te bepalen.
Winkeleigenaars kunnen de volgende typen classificatiestrategieën instellen:

![&#x200B; Intelligente Rankings &#x200B;](../../assets/rule-intelligent-ranking.png)

- Meest aangeschaft: dit rangschikt de producten op basis van de totale aankopen per SKU in de afgelopen 7 dagen.
- Meestal toegevoegd aan winkelwagentjes in volgorde van de totale &quot;Add to Cart&quot;-activiteiten in de afgelopen 7 dagen.
- Meest bekeken: de totale weergaven per SKU zijn in de afgelopen 7 dagen opnieuw weergegeven.
- Aanbevolen voor u - Gebruikt het `viewed-viewed` gegevenspunt - Kopers die deze SKU bekeken ook naar deze andere SKU&#39;s keken.
- Trending: kijkt terug naar de gebeurtenissen van de paginaweergave in de afgelopen 72 uur voor achtergrondgebeurtenissen en 24 uur voor voorgrondgebeurtenissen.
- Geen: de producten worden bevolen door Relevantie.

Selecteer het type strategie voor de regel. De **Test uw regel** venster toont de verwachte resultaten.

#### Hoe intelligent classificeren werkt

Het intelligente rangschikken bepaalt de definitieve productorde door twee zeer belangrijke factoren te combineren: **tekstuele relevantie** en **gedragssignalen**. Als u begrijpt hoe deze factoren op elkaar inwerken, kunt u realistische verwachtingen voor uw zoekresultaten instellen.

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
- Om het intelligente rangschikken te verzekeren werkt correct, zorg ervoor dat het **Gewicht van het Onderzoek** voor om het even welke attributen die voor onderzoek of het filtreren (facetten) worden gebruikt `5` of minder is.

Voor informatie over het plaatsen van onderzoeksdikten, zie [&#x200B; Meta-gegevens API &#x200B;](https://developer.adobe.com/commerce/services/reference/rest/).

### Handmatige classificatie

**het Handmatig rangschikken** is acties die de onderzoeksresultaten wijzigen wanneer de bepaalde voorwaarden worden voldaan aan. Eén regel kan maximaal 25 gebeurtenissen bevatten.

- Verhogen - Verplaatst een product hoger in de onderzoeksresultaten.
- Branden - Verplaatst een SKU lager in de zoekresultaten.
- Een product vastzetten - Het product wordt weergegeven in de geselecteerde positie op de pagina.
- Een product verbergen - Hiermee sluit u een SKU uit van de zoekresultaten.

De eenvoudigste manier om een product vast te zetten is door te slepen en neer te zetten.

1. Klik en sleep een product in het deelvenster Testen. Sleep de aanwijzer naar de gewenste positie. De velden Product en Positie worden automatisch ingevuld in het deelvenster Gebeurtenissen.

U kunt ook op het speldpictogram klikken om een product op de huidige locatie vast te zetten. Gebruik het contextmenu voor ovalen om &#39;Aan de bovenkant vastzetten&#39; of &#39;Aan de onderkant vastzetten&#39;.

>[!NOTE]
>
>U kunt producten vastzetten die in de onderzoeksresultaten voor de gevormde vraag en regelvoorwaarden verschijnen.
>
>De producten moeten worden geïndexeerd, zichtbaar, in voorraad, en voldoen aan alle regelfilters om voor het pinnen in aanmerking te komen. Als een product niet in de voorvertoning of in de resultaten voor uw regel wordt weergegeven, heeft het vastzetten geen effect.

Of gebeurtenissen kunnen handmatig worden ingesteld:

1. Onder *Gebeurtenissen*, kies de **Gebeurtenis** om te gebeuren wanneer de bijbehorende voorwaarden worden voldaan.

   Kies bijvoorbeeld `Hide a product` . Voer vervolgens de naam in van het product dat u wilt verbergen. Producten worden voorgesteld terwijl u typt.

1. Voor meerdere gebeurtenissen kiest u andere gebeurtenissen die u wilt activeren als aan de voorwaarden is voldaan.

### De regel voltooien

1. Onderzoek de resultaten van de regel in de testruit.
1. Als de regel veelvoudige vragen heeft, test elk die door de regel zou kunnen worden beïnvloed.
1. Wanneer volledig, klik **sparen en publiceer**.

   De regel wordt toegevoegd aan de lijst in de *1&rbrace; werkruimte van Regels &lbrace;.*

1. Hoewel de actieve regels onmiddellijk in werking treden, zou u tot 15 minuten kunnen moeten wachten op de caching vraagresultaten in de storefront om worden verfrist.

>[!NOTE]
>
>Regels en handmatig gerangschikte producten worden toegepast op de zoekresultaten wanneer de standaardsorteervolgorde &quot;Sorteren op: meest relevant&quot; is geselecteerd. Als een winkelier de sorteervolgorde verandert in een sorteervolgorde op naam of prijs, zijn de regels en handmatige waarderingen niet meer van kracht.

## Regels bewerken, weergeven en verwijderen

Volg deze instructies om de eigenschappen van bestaande regels bij te werken.

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

## Veldomschrijvingen

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

### Handmatige classificatie

| Gebeurtenis | Beschrijving |
|--- |--- |
| Verhogen | Hiermee verplaatst u een SKU of reeks SKU&#39;s hoger in de zoekresultaten. Elk object wordt gemarkeerd met een &#39;gebooste&#39; voorvertoningsbadge in de zoekresultaten van de test. |
| Bury | Verplaatst een SKU of een waaier van SKUs lager in de onderzoeksresultaten. Elk object wordt gemarkeerd met een voorvertoningssymbool &quot;begraven&quot; in de zoekresultaten van de test. |
| Een product vastzetten | Koppelt één SKU aan een specifieke positie in de zoekresultaten. Het product wordt gemarkeerd met een &#39;vastgezette&#39; voorvertoningsbadge in de zoekresultaten van de test. |
| Een product verbergen | Sluit SKU, of waaier van SKUs, van de onderzoeksresultaten uit. |

### Details

| Veld | Beschrijving |
|--- |--- |
| Naam | De naam van de regel. Regelnamen moeten uniek zijn. |
| Type regel | Standaard of Query. Het gebrek wordt toegepast op alle regels, tenzij een specifiekere regel van de Vraag wordt bepaald. |
| Begindatum | De begindatum van de regel, indien gepland. |
| Einddatum | De einddatum van de regel, indien gepland. |
| Beschrijving | Een korte beschrijving van de regel. |
