---
title: Catalogusweergave
description: Leer welke catalogusweergaven zijn en hoe u deze kunt maken om uw productcatalogus te ordenen op basis van de bedrijfsstructuur, het beleid en de prijzen.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: 76c1b81c-b456-4334-89bd-6027308cbc47
source-git-commit: 2e47c770d204c9c7f959893704dd0ebcc6ac792a
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---


# Catalogusweergaven voor Merchandising Services

Catalogusweergaven vormen de basis van Adobe Commerce Optimizer Merchandising Services, waarmee u uw productcatalogus kunt ordenen op basis van de bedrijfsstructuur, het beleid en de prijzen. Dit flexibele gegevensmodel ondersteunt multibrand, multi-business unit en meertalige scenario&#39;s terwijl het handhaven van operationele efficiency.

## Wat zijn catalogusweergaven?

In de catalogusweergaven wordt gedefinieerd hoe de productcatalogus wordt ingedeeld en weergegeven. Ze fungeren als filters die bepalen:

- **Welke producten** zichtbaar zijn die op bedrijfsstructuur (merken, gebieden, dealers) wordt gebaseerd
- **welke tarifering** door verbonden prijsboeken wordt getoond
- **hoe de producten** gebruikend beleid (attributen zoals merk, model, categorie) worden gefiltreerd
- **welke catalogusbron** wordt gebruikt die op attributen zoals scène wordt gebaseerd

Beschouw catalogusweergaven als verschillende &#39;lenzen&#39; waardoor klanten uw catalogus zien. Bijvoorbeeld:

- In de catalogusweergave van een dealer kunnen alleen producten worden weergegeven die beschikbaar zijn voor die specifieke dealer
- Een regionale catalogusweergave kan producten en prijzen weergeven die specifiek zijn voor een geografisch gebied
- Een merkcatalogusweergave kan alleen producten van een bepaald merk weergeven

## Een catalogusweergave maken

In deze sectie, creeert u een catalogusmening, selecteert a [ beleid ](policies.md), en a [ prijsboek ](pricebooks.md).

Voordat u een catalogusweergave maakt, moet u controleren of:

- [ Gemaakt beleid ](policies.md) om productfilters te bepalen

- [ Verwoekerde prijsboeken ](pricebooks.md) voor het tarief

1. Van het linkermenu, ga naar _opstelling van de Opslag_, en klik **[!UICONTROL Catalog views]**.

1. Klik op **[!UICONTROL Create catalog view]** . &#x200B;

1. Configureer de details van de catalogusweergave:

   - **Naam** - ga de naam van de catalogusmening in, bijvoorbeeld `Celport`. &#x200B;
   - **de bronnen van de Catalogus** - selecteer de catalogusbron (scène), bijvoorbeeld `en-US`.
   - **Beleid** - gebruik drop-down om het relevante beleid te selecteren. Bijvoorbeeld &#39;Merk&#39;, &#39;Model&#39;. &#x200B;Zorg ervoor u reeds [ een beleid ](policies.md) creeerde.

1. Selecteer het prijzenboek om aan de catalogusmening te verbinden.

   - **gebruik alle beschikbare prijsboeken** - Deze optie trekt prijsgegevens van alle beschikbare prijsboeken.
   - **staat geselecteerde prijsboeken slechts toe** - Deze optie toont **toegestane prijsboeken** dialoog toevoegen waar u kunt selecteren welk specifiek prijsboek voor de catalogusmening te gebruiken.
   - **maak prijzen**-Deze optie onbruikbaar op dit ogenblik niet beschikbaar.

1. Klik op **[!UICONTROL Add]** om de catalogusweergave te maken met de gekoppelde prijsboeken en het bijbehorende beleid.

De pagina van de catalogusweergaven wordt bijgewerkt om de nieuwe catalogusweergave weer te geven. &#x200B;

Nadat u deze stappen hebt uitgevoerd, is de catalogusweergave nu geconfigureerd voor het weergeven van producten en prijzen op basis van uw geselecteerde bronnen en beleid.

## Overzicht van architectuur

Catalogusweergaven maken deel uit van het Merchandising Services-framework dat het in Adobe Commerce-stichtingen gebruikte kader voor websites, winkels en winkels vervangt door een flexibeler model:

![[!DNL Merchandising Services] Architectuur ](../assets/merchandising-svcs-architecture.png)

### Hoe het werkt

**1. Gegevensinname**
Catalogusgegevens van PIM, ERP en andere systemen worden opgenomen in het framework Merchandising Services. Elke SKU bevat locale informatie en productkenmerken die aan catalogusmeningen, beleid, en scènes in kaart brengen. Voor meer informatie over gegevensopname, zie de [ documentatie van de ontwikkelaar ](https://developer.adobe.com/commerce/services/optimizer/).

**2. Unified Base-catalogus**
De ingesloten gegevens leiden tot een verenigde basiscatalogus in de de gegevenspijpleiding van de Dienst van de Catalogus. Met deze ene bron voorkomt u dubbele gegevens in verschillende bedrijfseenheden.

**3. Catalogusweergaven**
Meerdere catalogusweergaven vertegenwoordigen verschillende bedrijfseenheden (bijvoorbeeld &quot;Texas Retail&quot;, &quot;Texas Retail Seasonal&quot;). Landinstellingen, beleidsregels en prijzenboeken kunnen worden gedeeld door catalogusweergaven voor flexibiliteit.

**4. Levering via meerdere kanalen**
De gefilterde catalogusgegevens worden geleverd aan verschillende bestemmingen, waaronder Edge Delivery Services-winkels, -markten, -advertentieplatforms en aangepaste microwinkels. Voor meer informatie over de levering van catalogusgegevens, zie de [ ontwikkelaardocumentatie ](https://developer.adobe.com/commerce/services/optimizer/).

### Belangrijkste onderdelen

| Component | Doel | Voorbeeld |
|---|---|---|
| **de Mening van de Catalogus** | Zakelijke eenheid of distributiekanaal | Dealer-netwerk, regionale winkel |
| **Beleid** | Productfilter op basis van kenmerken | Merk, model, categorie |
| **Landinstelling** | Taal/regio-instelling | en-US, fr-CA, es-MX |
| **Boek van de Prijs** | Prijsstructuur | Detailhandel, groothandel, werknemer |

### Gegevensstroom

1. **Samenvatting** - de gegevens van het Product van systemen PIM/ERP
2. **Proces** - pas catalogusmeningen, beleid, en tarifering toe
3. **lever** - de server filtreerde catalogus aan winkelcentra, markten, enz.

## Belangrijkste kenmerken

| Functie | Voordeel |
|---|---|
| **Enige Catalogus van de Basis** | Gegevensduplicatie elimineren voor verschillende bedrijfseenheden |
| **Flexibele Prijsstelling** | Meerdere prijzenboeken per SKU voor verschillende klantensegmenten |
| **Scalable** | 200M+ SKU&#39;s efficiënt beheren |
| **Multikanaal** | Catalogi leveren aan winkels, markten en advertentieplatforms |
| **Updates in real time** | Snel catalogusgegevens bijwerken voor promoties en campagnes |

## Gevallen gebruiken

### Meermerkconglomeraat

**Uitdaging**: Beheer veelvoudige merken, landen, en talen <br>
**Oplossing**: Enige catalogus met catalogusmeningen voor elke merk/gebiedcombinatie

### Dealer voor auto-onderdelen

**Uitdaging**: 3.000 dealers met zelfde producten maar verschillende tarifering <br>
**Oplossing**: Één catalogus met dealer-specifieke catalogusmeningen en prijsboeken

### Multi-Location Retailer

**Uitdaging**: Verschillende tarifering en inventaris per plaats <br>
**Oplossing**: Op plaats-gebaseerde catalogusmeningen met gebied-specifiek beleid

>[!INFO]
>
>Voor gedetailleerde informatie over de opname en levering van catalogusgegevens, zie de [ documentatie van de ontwikkelaar ](https://developer.adobe.com/commerce/services/optimizer/).
