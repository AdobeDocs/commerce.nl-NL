---
title: Gebruiksscenario van begin tot einde voor Storefront en Catalog Administrator
description: Leer hoe te om  [!DNL Adobe Commerce Optimizer]  te gebruiken om uw catalogus te beheren gebruikend catalogusmeningen en beleid en hoe te opstelling uw opslag die op uw catalogusconfiguratie wordt gebaseerd.
role: Admin, Developer
feature: Personalization, Integration
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: d11663f8-607e-4f1d-b68f-466a69bcbd91
source-git-commit: e5844cad1d666a81042db64e51e124e6444d19ac
workflow-type: tm+mt
source-wordcount: '2179'
ht-degree: 0%

---

# Gebruiksscenario van begin tot einde voor Storefront en Catalog Administrator

Dit gebruiksgeval is gebaseerd op een fictief automobielconglomeraat genaamd Carvelo Automobile, dat een complexe operationele opzet heeft. Het toont hoe te om [!DNL Adobe Commerce Optimizer] te gebruiken om een catalogus te beheren die veelvoudige merken, dealership, en prijsboeken steunt, terwijl het leveren van een aangepaste storefront ervaring.

## Vereisten

Dit gebruiksgeval is ontworpen voor beheerders en ontwikkelaars die willen leren hoe u een winkelcentrum kunt instellen en een catalogus kunt beheren met [!DNL Adobe Commerce Optimizer] . Hierbij wordt ervan uitgegaan dat u een basiskennis hebt van [!DNL Adobe Commerce Optimizer] en de bijbehorende functies.

**Geschatte tijd om te voltooien:** 45-60 minuten

### Vereiste instelling

Voordat u met deze zelfstudie begint, moet u controleren of aan de volgende voorwaarden is voldaan:

- **Instantie van Adobe Commerce Optimizer**
   - Toegang tot een testinstantie in Cloud Manager
   - Zie [ Begonnen ](../get-started.md) voor opstellingsinstructies krijgen

- **Toestemmingen van de Gebruiker**
   - Toegang voor beheerders tot Adobe Admin Console
   - Zie [ Gebruikersbeheer ](../user-management.md) voor rekeningsopstelling
   - Neem contact op met uw Adobe-accountvertegenwoordiger als u geen toegang hebt.

- **Gegevens van de Steekproef**
   - Carvelo Automobiel catalogusgegevens die in uw instantie zijn geladen
   - Volg de instructies in de [ bewaarplaats van de catalogusgegevens van de Steekproef ](https://github.com/adobe-commerce/aco-sample-catalog-data-ingestion)
   - U kunt voorbeeldgegevens na voltooiing verwijderen met het meegeleverde script `reset.js`

- **Milieu Storefront**
   - Lokale ontwikkelomgeving met Node.js
   - Storefront boilerplate-project gekloond en geconfigureerd
   - Zie [ opstelling Storefront ](../storefront.md) voor gedetailleerde instructies

## Laten we beginnen

In dit geval gebruikt u het volgende:

1. [!DNL Adobe Commerce Optimizer] UI - Opstelling catalogusmeningen en beleid om de complexe catalogus operationele opstelling voor het de gebruikscase van Carvelo te beheren.

1. Commerce Storefront - Render de storefront met de voorbeeldcatalogusgegevens die in uw [!DNL Adobe Commerce Optimizer] -instantie en de Commerce Storefront-configuratiebestanden `fstab.yaml` en `config.json` zijn geladen.

>[!NOTE]
>
> Leer over de dossiers van de storefrontconfiguratie door [ te herzien verken boilerplate ](https://experienceleague.adobe.com/developer/commerce/storefront/get-started/boilerplate-project/) onderwerp in de documentatie van de Storefront van Adobe Commerce.

### ‌ Key-trajecten

Aan het einde van dit artikel zult u:

- Leer de grondbeginselen van [!DNL Adobe Commerce Optimizer] met zijn prestatiesen en scalable model van catalogusgegevens.
- Leer hoe het gegevensmodel van de catalogus integreert met platformagnostische winkelcomponenten die door Adobe zijn gemaakt.
- Leer hoe u Adobe Commerce Optimizer-catalogusweergaven en -beleid kunt gebruiken om aangepaste catalogusweergaven en gegevenstoegangsfilters te maken en de gegevens naar een Adobe Commerce-winkel met Edge Delivery te verzenden.

## Bedrijfescenario - Carvelo Automobile

Carvelo Automobile is een fictief automobielconglomeraat met een complexe operationele opzet.

![ Carvelo Automobile ](../assets/carvelo.png)

In dit diagram zie je dat Carvelo autoproducten van drie merken verkoopt. Elk merk is een ander kindbedrijf:

- Aurora (elektrische voertuigen)
- Bolt (SUV&#39;s)
- Cruz (hybride)

Zij verkoopt deze merken via drie dealers:

- Arkbridge
- Kingsbluff
- Celport

Deze dealers behoren tot twee verschillende moedermaatschappijen:

- West Coast Inc. (Arkbridge)
- East Coast Inc. (Kingsbluff, Celport)

Elke onderneming heeft twee prijzenboeken die worden gebruikt om producten tegen een specifieke prijs voor verschillende kopers te verkopen (basis, VIP).

- `west_coast_inc` en `vip_west_coast_inc`
- `east_coast_inc` en `vip_east_coast_inc`

Zoals u kunt zien, is dit een zeer complex bedrijfsgebruik geval. Met [!DNL Adobe Commerce Optimizer] kan een handelaar een complexe bedrijfsstructuur steunen die één enkele basiscatalogus gebruikt om gegevens zonder catalogusduplicatie te synchroniseren, prijzenboeken (prijzenboeken van 30k+) te schrapen, en al deze gegevens aan een Edge Delivery Services storefront te leveren.

Nu u een overzicht van de bedrijfs gebruikscase hebt, is hier uw doel aangezien u door dit leerprogramma werkt:

>[!BEGINSHADEBOX]

Carvelo wil onderdelen van drie merken (Aurora, Bolt en Cruz) verkopen via de verschillende dealers (Arkbridge, Kingsbluff en Celport). Carvelo wil ervoor zorgen dat de dealers alleen toegang hebben tot de correcte onderdelen en prijzen volgens hun respectieve licentieovereenkomsten.

Uiteindelijk heeft Carvelo twee belangrijke doelstellingen:

1. Een &quot;globale&quot; website onderhouden met alle SKU&#39;s voor alle drie de merken.
1. Geef een pad voor dealers om hun eigen winkeliers op te zetten op basis van unieke SKU-zichtbaarheid en -prijzen voor elke SKU voor elke dealership. Alles bij gebruik van één basiscatalogus, waardoor dubbel werk met catalogi wordt voorkomen.

>[!ENDSHADEBOX]

## &#x200B;1. Open de instantie [!DNL Adobe Commerce Optimizer]

Navigeer naar de URL voor de Commerce Optimizer-toepassing die vooraf is geconfigureerd met de voorbeeldgegevens. U vindt de URL in Commerce Cloud Manager via de instantiedetails voor uw Commerce Optimizer-project of haalt deze op bij de systeembeheerder. (Zie [ Toegang tot een instantie ](../get-started.md#access-an-instance).)

Wanneer u [!DNL Adobe Commerce Optimizer] start, ziet u het volgende:

![[!DNL Adobe Commerce Optimizer] UI ](../assets/user-interface.png)

>[!NOTE]
>
>Zie het [ overzicht ](../overview.md) artikel over zeer belangrijke componenten van [!DNL Adobe Commerce Optimizer] UI leren.

In de linkernavigatie, breid de _sectie van de opstelling van de Opslag_ uit en klik **[!UICONTROL Catalog views]**. U ziet dat er al catalogusweergaven zijn gemaakt in de dealerschepen Arkbridge en Kingsbluff:

![ Bestaande catalogusmeningen die voor steekproefgegevens ](../assets/existing-channels-list.png) worden gevormd

>[!NOTE]
>
>U kunt de **Globale** catalogusmening voor nu negeren.

Klik op het informatiepictogram om de details van de catalogusweergave te bekijken.

Arkbridge heeft het volgende beleid:

- Merk
- Model
- West Coast Inc-merken
- Categorieën van onderdelen van Arkbridge

Kingsbluff heeft het volgende beleid:

- Merk
- Model
- East Coast Inc-merken
- Onderdeelcategorieën Kingsbluff

In de volgende sectie maakt u een catalogusweergave en beleidsregels voor de dealership Celport.

## &#x200B;2. Een beleid- en catalogusweergave maken

De handelsmanager van Carvelo moet opstelling een nieuwe winkel voor een handelaar genoemd *Celport* die tot het *Oost Coast Inc* bedrijf behoort. Celport verkoopt remmen en schorsingen voor de merken Bolt en Cruz.

![ Dealer van de Knol ](../assets/celport-dealer.png)

Met [!DNL Adobe Commerce Optimizer] zal de commercebeheerder:

1. Creeer een nieuw beleid genoemd *de categorieën van het Deel van de Knoophaven* voor Celport om slechts rem en hangingsdelen te verkopen.
1. Maak een nieuwe catalogusweergave voor de Celport-winkel.

   Deze catalogusmening gebruikt uw onlangs gecreeerd beleid *de categorieën van het Deel van de Knol* en de bestaande *OostCoast Inc Banden* om ervoor te zorgen dat Celport slechts de merken van Bolt en van Cruz als deel van de overeenkomst met East Coast Inc. kan verkopen. De de catalogusmening van Celport gebruikt het `east_coast_inc` prijsboek om productprijzenprogramma&#39;s te steunen die zich met merkvergunningsovereenkomsten richten.
1. Werk de configuratie van de handelsafzet bij om gegevens van de de catalogusmening te gebruiken Celport die u creeerde.

Aan het einde van deze sectie zal Celport klaar zijn om de producten van Carvelo te verkopen.

### Een beleid maken

Laten wij een nieuw beleid tot stand brengen genoemd *de categorieën van het Deel van Celport* om SKUs te filtreren die de handelaar van Celport verkoopt, die rem en hangingsdelen omvatten.

1. In het linkerspoor, breid de _sectie van de opstelling van de Opslag_ uit en klik op **[!UICONTROL Policies]**.

1. Klik op **[!UICONTROL Create Policy]**.

   Er wordt een nieuwe pagina weergegeven om de beleidsdetails toe te voegen.

1. Voeg de vereiste details toe:

   **Naam** = *Categorieën van het Deel van de Knol*

1. Klik op **[!UICONTROL Add Filter]**.

   Er wordt een dialoogvenster weergegeven waarin u filterdetails kunt toevoegen.

1. Voeg de filterdetails toe:

   - **Attribuut** = *part_category*
   - **Exploitant** = **IN**
   - **Waarde Source** = **STATIC**
   - **Waarde** = *slagen*
   - **Waarde** = *opschorting*

   >[!IMPORTANT]
   >
   >Elke kenmerkwaarde moet afzonderlijk worden ingevoerd. Na het ingaan van een waarde, druk **binnengaan** om het aan de filterconfiguratie toe te voegen. Voer vervolgens de volgende waarde in. Alle waarden moeten exact overeenkomen met de naam van het SKU-kenmerk in de catalogus.

   Meer over het verschil tussen een STATISCHE en TRIGGER waardebron leren, zie [ de types van waardebron ](../setup/policies.md#value-source-types).

1. Klik in het dialoogvenster **[!UICONTROL Filter details]** op **[!UICONTROL Save]** .

1. Om de filter toe te laten u enkel creeerde, klik de actiepunten (...) en selecteer **toelaten**.

1. Klik op **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Als de knop **[!UICONTROL Save]** niet actief (blauw) is, ontbreekt de naam van het beleid mogelijk. Klik het potloodpictogram naast *Nieuw Beleid* om het toe te voegen.

1. Ga terug naar de lijst met beleidsregels door op de pijl Terug te klikken.

   Uw nieuwe *het deelcategorieën van de Knoophaven* beleid verschijnt in de lijst.

**om deze stap te verifiëren correct werd voltooid:**

- Beleid wordt weergegeven in de lijst met beleidsregels
- Beleidsstatus wordt weergegeven als ingeschakeld (groene indicator)
- Gegevens over het filter tonen &quot;part_category IN (remmen, ophanging)&quot;
- Beleidsnaam is &quot;Celport Part Categories&quot;

### Een catalogusweergave maken

Creeer een nieuwe catalogusmening voor de *handelaar 0&rbrace; Celport &lbrace;en verbind het volgende beleid:* de brandmerken van Coast Inc van Cisco *en* Categorieën van het Deel van de Knoop *.*

1. In het linkerspoor, breid de _opstellings_ sectie van de Opslag uit en klik **[!UICONTROL Catalog views]**.

   Merk de bestaande catalogusmeningen op: *Arkbridge*, *Kingsbluff*, en *Globale*.

   ![ Bestaande de meningspagina van de Catalogus ](../assets/existing-channels-list.png)

1. Klik op **[!UICONTROL Add catalog view]**.

1. Details van catalogusweergave invullen:

   - **Naam** = *Celport*
   - **de bronnen van de Catalogus** = *en-US*
   - **Beleid** (gebruiksdrop) = *de Randen van Coast Inc van het Oosten*; *de categorieën van het Deel van de Knol*; *Merk*; *Model*
                         
1. Klik op **[!UICONTROL Add]** om de catalogusweergave te maken.

   De pagina met catalogusweergaven wordt bijgewerkt om de nieuwe catalogusweergave weer te geven.

   ![ Bijgewerkte Lijst van de Mening van de Catalogus ](../assets/updated-catalog-view-list.png)

1. Hiermee wordt de weergave-id van de Celport-catalogus opgehaald.

   Klik het informatiepictogram voor de de catalogusmening van de Haven op de **mening van de Catalogus** pagina.

   ![ identiteitskaart van de de catalogusmening van de Knol ](../assets/celport-channel-id.png)

   Kopieer en sla de weergave-id van de catalogus op. U hebt deze id nodig wanneer u de winkelconfiguratie bijwerkt om gegevens naar uw nieuwe Celport-catalogus te leveren.

   **om deze stap te verifiëren correct werd voltooid:**
   - Naam van catalogusweergave is &quot;Celport&quot;
   - In de Catalogusweergave worden 4 bijbehorende beleidsregels weergegeven
   - De weergave-id van de catalogus wordt weergegeven en kan worden gekopieerd
   - De catalogusbron toont &quot;en-US&quot;

Nadat u de de catalogusmening van Celport en bijbehorend beleid creeert, is de volgende stap de storefront te vormen om uw nieuwe catalogus van Celport te gebruiken.

## &#x200B;3. Werk uw winkel bij

Het definitieve stuk van dit leerprogramma impliceert het bijwerken van de storefront dat [ u reeds ](#prerequisite) creeerde om gegevens aan de nieuwe catalogus van de Knol te leveren. In deze sectie vervangt u de catalogusweergave-id in het configuratiebestand van de winkel door de catalogusweergave-id voor Celport.

1. In uw lokale ontwikkelomgeving, open de omslag waar u de bewaarplaats GitHub met uw opslag boilerplate configuratiedossiers kloond.

1. Open het bestand `config.json` in de hoofdmap van de map.

   +++config.json-code

   ```json
   {
    "public": {
      "default": {
      "commerce-core-endpoint": "https://www.aemshop.net/graphql",
      "commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/Fwus6kdpvYCmeEdcCX7PZg/graphql",
      "headers": {
         "cs": {
            "ac-view-id": "9ced53d7-35a6-40c5-830e-8288c00985ad",
            "ac-price-book-id": "west_coast_inc",
            "ac-source-locale": "en-US"
           }
         },
         "analytics": {
            "base-currency-code": "USD",
            "environment": "Production",
            "store-id": 1,
            "store-name": "ACO Demo",
            "store-url": "https://www.aemshop.net",
            "store-view-id": 1,
            "store-view-name": "Default Store View",
            "website-id": 1,
            "website-name": "Main Website"
          }
       }
      }
   }
   ```

   De koptekst van de catalogusweergave bevat de volgende waarden:

   - `commerce-endpoint`: `"https://na1-sandbox.api.commerce.adobe.com/Fwus6kdpvYCmeEdcCX7PZg/graphql"`
   - `ac-view-id`:`"9ced53d7-35a6-40c5-830e-8288c00985ad"`
   - `ac-price-book-id`: `"west_coast_inc"`
   - `ac-source-locale`: `"en-US"`

1. Vervang in de waarde `commerce-endpoint` de huurder-id in de URL door de URL voor de instantie [!DNL Adobe Commerce Optimizer] .

   U kunt de huurder-id vinden in de URL voor de gebruikersinterface van Commerce Optimizer. In de volgende URL is de huurder-id bijvoorbeeld `XDevkG9W6UbwgQmPn995r3` .

   ```text
   https://experience.adobe.com/#/@commerceprojectbeacon/in:XDevkG9W6UbwgQmPn995r3/commerce-optimizer-studio/catalog
   ```

1. Vervang de `ac-view-id` -waarde door de CelPort-weergave-id die u eerder hebt gekopieerd.

1. Vervang de waarde `ac-price-book-id` door `"east_coast_inc"` .

   Nadat u deze wijzigingen hebt aangebracht, ziet het `config.json` -bestand er ongeveer als volgt uit: de plaatsaanduidingen `ACO-tenant-id` en `celport-catalog-view-id` worden vervangen door de waarden:

   ```json
   {
     "public": {
        "default": {
        "commerce-core-endpoint": "https://www.aemshop.net/graphql",
        "commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/{{ACO-tenant-id}}/graphql",
        "headers": {
            "cs": {
                "ac-view-id": "{{celport-catalog-view-id}}",
                "ac-price-book-id": "east_coast_inc",
                "ac-source-locale": "en-US"
              }
            },
            "analytics": {
                "base-currency-code": "USD",
                "environment": "Production",
                "store-id": 1,
                "store-name": "ACO Demo",
                "store-url": "https://www.aemshop.net",
                "store-view-id": 1,
                "store-view-name": "Default Store View",
                "website-id": 1,
                "website-name": "Main Website"
             }
         }
     }
   }
   ```

1. Sla het bestand op.

   Wanneer u de wijzigingen opslaat, werkt u de catalogusconfiguratie bij zodat de catalogusweergave van Carvelo wordt gebruikt. Deze weergave is geconfigureerd om alleen remonderdelen en ophangingsonderdelen te verkopen.

## &#x200B;4. Voorvertoning van de winkel weergeven

Nu u de storefront-configuratie hebt bijgewerkt om de Celport-catalogusweergave te gebruiken, kunt u een voorvertoning van de storefront weergeven om te zien hoe de catalogusgegevens worden weergegeven.

1. Start de storefront om de Celport-specifieke cataloguservaring weer te geven die door uw storefront-configuratie is gemaakt.

   1. Van het eindvenster in uw winde, begin uw lokale archiefvoorproef.

      ```shell
      npm start
      ```

      De browser wordt geopend voor de voorvertoning van de lokale ontwikkeling op `http://localhost:3000` .

      Als het bevel ontbreekt of browser niet opent, herzie de [ instructies voor lokale ontwikkeling ](../storefront.md) in het de opstellingsonderwerp van de Storefront.

1. In browser, onderzoek naar `brakes`, en druk **binnengaan**.

   De winkel wordt bijgewerkt om de productlijstpagina met de remonderdelen weer te geven.

   ![ Van het Product van Remmen het Noteren Pagina ](../assets/brakes-listing-page.png)

   Klik op een afbeelding van een remonderdeel om de productdetails met prijsinformatie te bekijken en de productprijsinformatie te noteren.

1. Zoek naar `tires`. Dit is een andere onderdelencategorie die beschikbaar is in de gebruikscase-gegevens van uw [!DNL Adobe Commerce Optimizer] -instantie.

   ![ Configuratie Storefront met Onjuiste Kopballen ](../assets/storefront-configuration-with-incorrect-headers.png)

   Er worden geen resultaten geretourneerd. Dit komt omdat de CelPort-catalogusweergave zo is geconfigureerd dat alleen remonderdelen en ophangingsonderdelen worden verkocht.

1. Experimenteer met het bijwerken van uw storefront configuratiedossier (`config.json`).

   1. Wijzig de waarden `ac-view-id` en `ac-price-book` .

   U kunt bijvoorbeeld de weergave-id van de catalogusweergave wijzigen in de catalogusweergave Kingsbluff en de id van het prijzenboek in `east_coast_inc` . U kunt de onderdelencategorieën zien beschikbaar voor Kingsbluff door het *Kingsbluff deelcategorieën* beleid te herzien.

   1. Sla het bestand op.

      Wanneer u het bestand opslaat, wordt de lokale voorvertoning automatisch bijgewerkt.

   1. Geef een voorvertoning van de wijzigingen weer in de browser door met de functie Zoeken naar bandonderdelen te zoeken.

      U ziet de verschillende beschikbare onderdeeltypen en u ziet welke prijzen zijn toegewezen aan de catalogusweergave Kingsbluff.

   Deze experimenten tonen de flexibiliteit van Adobe Commerce Optimizer aan: u kunt snel schakelen tussen verschillende catalogusweergaven en prijzenboeken om aangepaste winkelervaringen voor verschillende soorten publiek te maken zonder uw catalogusgegevens te dupliceren.

## Problemen oplossen

Als er tijdens deze zelfstudie problemen optreden, kunt u de volgende oplossingen uitproberen:

### Problemen met het maken van beleid

**Probleem:** sparen knoop is niet actief

- **Oplossing:** zorg ervoor dat de beleidsnaam is ingegaan en alle vereiste gebieden worden voltooid

**Probleem:** Filter werkt niet zoals verwacht

- **Oplossing:** verifieer dat de attributennaam precies het attribuut van SKU in uw catalogus aanpast

### Weergaveproblemen met catalogus

**Probleem:** de mening van de Catalogus verschijnt niet in de lijst

- **Oplossing:** verifieer dat alle bijbehorende beleid wordt toegelaten en behoorlijk gevormd

### Problemen met configuratie Storefront

**Probleem:** Storefront laadt niet

- **Oplossing:** Controle dat uw identiteitskaart van de huurdersidentiteitskaart en identiteitskaart van de catalogusmening correct in het config.json- dossier zijn ingegaan

**Probleem:** Geen producten die tonen

- **Oplossing:** verifieer dat identiteitskaart van het prijzenboek in uw instantie van Adobe Commerce Optimizer beschikbaar aanpast

**Probleem:** Onderzoek terugkerend geen resultaten

- **Oplossing:** bevestig dat het beleid van de catalogusmening de gezochte productcategorie toestaat

Voor extra hulp, zie de [ documentatie van Adobe Commerce Optimizer ](../overview.md) of contacteer de steun van Adobe.

## Samenvatting

In deze zelfstudie hebt u het volgende bereikt:

- Een nieuw beleid voor het filteren van productcategorieën voor Celport-handel
- Een catalogusweergave instellen met meerdere beleidsregels om de zichtbaarheid van producten te regelen
- Een opslagruimte configureren voor de nieuwe catalogusweergave
- Verifieerde de configuratie door productzichtbaarheid en prijzen te testen

## Volgende stappen

Ga als volgt te werk om meer te leren over Adobe Commerce Optimizer:

- Verken [ het koopvaardiseren eigenschappen ](../merchandising/overview.md) om de het winkelen ervaring te personaliseren
- Leer over [ geavanceerde beleidsconfiguraties ](../setup/policies.md)
- Opstelling [ extra catalogusmeningen ](../setup/catalog-view.md) voor andere dealership
- Herzie de [ API documentatie ](https://developer.adobe.com/commerce/services/optimizer/) voor programmatic catalogusbeheer
- Leer hoe u drop-in componenten voor uw Edge Delivery Services-winkel kunt configureren om aangepaste storefront-ervaringen te maken voor productdetectie, aanbevelingen en andere opslagmogelijkheden. Zie de [ documentatie Storefront ](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/)
