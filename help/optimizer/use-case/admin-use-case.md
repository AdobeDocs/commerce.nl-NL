---
title: Karvelo Use Case
description: Leer hoe te om  [!DNL Adobe Commerce Optimizer]  te gebruiken om uw catalogus te beheren die kanalen en beleid gebruiken en hoe te opstelling uw die opslagruimte op uw catalogusconfiguratie wordt gebaseerd.
hide: true
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d716dd9d75beb642bfad30271b6ecd3490ee7328
workflow-type: tm+mt
source-wordcount: '1656'
ht-degree: 0%

---

# Karvelo Use Case

>[!NOTE]
>
>Deze documentatie beschrijft een product in vroege-toegangsontwikkeling en weerspiegelt niet alle functionaliteit voorgenomen voor algemene beschikbaarheid.

In het volgende gebruiksgeval ziet u hoe u [!DNL Adobe Commerce Optimizer] kunt gebruiken om uw catalogus te ordenen zodat deze overeenkomt met de detailhandel en gebruik maakt van één basiscatalogus. Ook wordt getoond hoe u een winkel kunt instellen die wordt aangedreven door Edge Delivery Services.

## Vereiste

Alvorens u door dit gebruiksgeval gaat, zorg ervoor u [ opstelling uw storefront ](../storefront.md) hebt.

## Laten we beginnen

In dit geval werkt u met het volgende:

1. [!DNL Adobe Commerce Optimizer] Interface - Stel de vereiste kanalen en beleidsregels in voor het beheer van complexe operationele setup van de catalogus.

1. Commerce Storefront - Render de storefront met de catalogusgegevens die zijn ingesteld in [!DNL Adobe Commerce Optimizer] UI en de configuratiebestanden van Commerce Storefront `fstab.yaml` en `config.json` .

### ‌ Key-trajecten

Aan het einde van dit artikel zult u:

- Leer de basisprincipes van [!DNL Adobe Commerce Optimizer] met het unieke prestatiekrachtige en schaalbare gegevensmodel van de catalogus.
- Leer hoe het gegevensmodel van de catalogus naadloos aansluit bij platformagnostische winkelcomponenten die door Adobe zijn gemaakt.
- Leer hoe u Adobe Commerce Optimizer-kanalen en -beleid kunt gebruiken om aangepaste catalogusweergaven en gegevenstoegangsfilters te maken en de gegevens naar een Adobe Commerce-winkel met Edge Delivery te verzenden.

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

Carvelo wil onderdelen van de drie merken (Aurora, Bolt en Cruz) verkopen via de verschillende dealers (Akbridge, Kingsbluff en Celport). Carvelo wil ervoor zorgen dat de dealers alleen toegang hebben tot de correcte onderdelen en prijzen volgens hun respectieve licentieovereenkomsten.

Uiteindelijk heeft Carvelo twee belangrijke doelstellingen:

1. Een &quot;globale&quot; website onderhouden met alle SKU&#39;s voor alle drie de merken.
1. Geef een pad voor dealers om hun eigen winkeliers op te zetten op basis van unieke SKU-zichtbaarheid en -prijzen voor elke SKU voor elke dealership.

>[!ENDSHADEBOX]

Open nu uw [!DNL Adobe Commerce Optimizer] -instantie.

## 1. Open de instantie [!DNL Adobe Commerce Optimizer]

Nadat u aan boord aan het Vroege programma van de Toegang bent, verzendt Adobe een e-mail die URL verstrekt om tot de instantie van l [!DNL Adobe Commerce Optimizer] toegang te hebben provisioned voor u. Deze instantie is vooraf geconfigureerd met alles wat u nodig hebt om de stappen uit te voeren die in deze zelfstudie worden beschreven, inclusief catalogusgegevens die het gebruiksgeval Carvelo Automobile ondersteunen.

Wanneer u [!DNL Adobe Commerce Optimizer] start, ziet u het volgende:

![[!DNL Adobe Commerce Optimizer] UI ](../assets/user-interface.png)

>[!NOTE]
>
>Zie het [ overzicht ](../overview.md) artikel om meer over de verschillende delen te leren die omhoog [!DNL Adobe Commerce Optimizer] UI maken.

Vouw in de linkernavigatie de sectie **[!UICONTROL Catalog]** uit en klik op **[!UICONTROL Channels]** . Merk op dat de dealership Arkbridge en Kingsbluff al kanalen hebben gecreëerd:

![ preconfigured Kanalen ](../assets/existing-channels-list.png)

>[!NOTE]
>
>U kunt het **Globale** kanaal voor nu negeren.

Klik op het informatiepictogram om de kanaaldetails te bekijken.

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

In de volgende sectie maakt u een kanaal en beleidsregels voor het dealership Celport.

## 2. Een beleid en een kanaal maken

De handelsmanager van Carvelo moet opstelling een nieuwe winkel voor een handelaar genoemd *Celport* die tot het *Oost Coast Inc* bedrijf behoort. Celport verkoopt remmen en schorsingen voor de merken Bolt en Cruz.

![ Dealer van de Knol ](../assets/celport-dealer.png)

Met [!DNL Adobe Commerce Optimizer] zal de commercebeheerder:

1. Creeer een nieuw beleid genoemd *de categorieën van het Deel van de Knoophaven* voor Celport om slechts rem en hangingsdelen te verkopen.
1. Maak een nieuw kanaal voor de Celport-winkel.

   Dit kanaal gebruikt uw onlangs gecreeerde beleids *categorieën van het Deel van de Knooppunt* en het bestaande *Oost Coast Inc Banden* om ervoor te zorgen dat Celport slechts de merken van Bolt en van Cruz als deel van de overeenkomst met East Coast Inc. kan verkopen. Het kanaal van Celport zal het `east_coast_inc` prijsboek gebruiken om productprijsprogramma&#39;s te steunen die zich met merkvergunningsovereenkomsten richten.
1. Werk de configuratie van de handelsafzet bij om gegevens van het kanaal te gebruiken Celport dat u creeerde.

Aan het einde van deze sectie zal Celport klaar zijn om de producten van Carvelo te verkopen.

### Een beleid maken

Laten wij een nieuw beleid tot stand brengen genoemd *de categorieën van het Deel van Celport* om SKUs te filtreren die de handelaar van Celport verkoopt, die rem en hangingsdelen omvatten.

1. Vouw in de linkernavigatie de sectie **[!UICONTROL Catalog]** uit en klik op **[!UICONTROL Policies]** .

1. Klik op **[!UICONTROL Add Policy]**.

   Er wordt een nieuwe pagina weergegeven om de beleidsdetails toe te voegen.

1. Voeg de vereiste details toe:

   **Naam** = *Categorieën van het Deel van de Knol*

1. Klik op **[!UICONTROL Add Filter]**.

   Er wordt een dialoogvenster weergegeven waarin u filterdetails kunt toevoegen.

1. Voeg de filterdetails toe:

   - **Attribuut** = *part_category*
   - **Exploitant** = **IN**
   - **Waarde Source** = **STATIC**
   - **Waarde** = *slagen*, *opschorting*

   >[!IMPORTANT]
   >
   >Zorg ervoor dat de kenmerknaam die u opgeeft, exact overeenkomt met de SKU-kenmerknaam in de catalogus.

   Meer over het verschil tussen een STATISCHE en TRIGGER waardebron leren, zie [ de types van waardebron ](../catalog/policies.md#value-source-types).

1. Klik in het dialoogvenster **[!UICONTROL Filter details]** op **[!UICONTROL Save]** .

1. Om de filter toe te laten u enkel creeerde, klik de actiepunten (...) en selecteer **toelaten**.

1. Klik op **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Als de knop **[!UICONTROL Save]** niet actief (blauw) is, ontbreekt de naam van het beleid mogelijk. Klik het potloodpictogram naast *Nieuw Beleid* om het toe te voegen.

1. Ga terug naar de lijst met beleidsregels door op de pijl Terug te klikken.

   Uw nieuwe *het deelcategorieën van de Knoophaven* beleid verschijnt in de lijst.

### Een kanaal maken

Creeer een nieuw kanaal voor de *handelaar 0&rbrace; Celport &lbrace;en verbind het volgende beleid:* de brandmerken van Coast Inc van Cisco *en* de Categorieën van het Deel van de Knol *.*

1. Vouw in de linkernavigatie de sectie **[!UICONTROL Catalog]** uit en klik op **[!UICONTROL Channels]** .

   ![ Kanalen ](../assets/channels.png)

   Merk de bestaande kanalen op: *Arkbridge*, *Kingsbluff*, en *Globale*.

   ![ Bestaande Pagina van Kanalen ](../assets/existing-channels-list.png)

1. Klik op **[!UICONTROL Add Channel]**.

1. Kanaaldetails invullen:

   - **Naam** = *Celport*
   - **Scopes** = *en-US* (slag gaat binnen)
   - **Beleid** (gebruiksdrop) = *de Randen van Coast Inc van het Oosten*; *de categorieën van het Deel van de Knol*; *Merk*; *Model*                          

1. Klik op **[!UICONTROL Add]** om het kanaal te maken.

   De pagina Kanalen wordt bijgewerkt om het nieuwe kanaal weer te geven.

   ![ Bijgewerkte Lijst van Kanalen ](../assets/updated-channels-list.png)

   >[!NOTE]
   >
   >Als de **[!UICONTROL Add]** knoop niet blauw is, zorg ervoor dat het werkingsgebied door uw curseur in de **[!UICONTROL Scopes]** sectie te plaatsen en **te drukken** ingaat.

1. Haal de kanaal-id van Celport op.

   Klik het informatiepictogram voor het kanaal van de Knol op de **pagina van Kanalen**.

   ![ identiteitskaart van het Kanaal van de Knol ](../assets/celport-channel-id.png)

   Kopieer en sla de kanaal-id op. U hebt deze id nodig wanneer u de winkelconfiguratie bijwerkt om gegevens naar uw nieuwe Celport-catalogus te leveren.

Nadat u het kanaal Celport en het bijbehorende beleid creeert, moet de volgende stap de storefront vormen om uw nieuwe catalogus van de Knol tot stand te brengen.

## 3. Werk uw winkel bij

Het definitieve stuk van dit leerprogramma impliceert het bijwerken van de storefront dat [ u reeds ](#prerequisite) creeerde om gegevens aan de nieuwe catalogus van de Knol te leveren. In deze sectie vervangt u de kanaal-id in het configuratiebestand van de winkel door de kanaal-id voor Celport.

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
            "ac-channel-id": "9ced53d7-35a6-40c5-830e-8288c00985ad",
            "ac-environment-id": "Fwus6kdpvYCmeEdcCX7PZg",
            "ac-price-book-id": "west_coast_inc",
            "ac-scope-locale": "en-US"
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

   De kanaalkoptekst bevat de volgende regels:

   - `ac-channel-id`:`"9ced53d7-35a6-40c5-830e-8288c00985ad"`
   - `ac-environment-id`: `"Fwus6kdpvYCmeEdcCX7PZg"`
   - `ac-price-book-id`: `"west_coast_inc"`

   +++

1. Vervang de `ac-channel-id` -waarde door de ColdPort-kanaal-id die u eerder hebt gekopieerd.
1. Vervang zo nodig de waarde `ac-environment-id` door de huurder-id voor de instantie [!DNL Adobe Commerce Optimizer] . U kunt de id vinden in het instapkaartbericht voor het programma Vroege toegang of door contact op te nemen met uw Adobe-accountvertegenwoordiger.

   Zorg ervoor dat de waarde `commerce-endpoint` overeenkomt met het GraphQL-eindpunt voor uw [!DNL Adobe Commerce Optimizer] -instantie.

1. Vervang de waarde `ac-price-book-id` door `"east_coast_inc"` .
1. Sla het bestand op.

Wanneer u de wijzigingen opslaat, werkt u de catalogusconfiguratie bij om het Carvelo-kanaal te gebruiken dat is geconfigureerd om alleen remonderdelen en ophangingsonderdelen te verkopen.

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

   Klik op een afbeelding voor remonderdelen om de productdetails weer te geven met prijsinformatie en noteer de prijsinformatie van het product.

1. Zoek nu naar `tires` . Dit is een andere onderdelencategorie die beschikbaar is in de gebruikscasegegevens van uw [!DNL Adobe Commerce Optimizer] -instantie.

   ![ Configuratie Storefront met Onjuiste Kopballen ](../assets/storefront-configuration-with-incorrect-headers.png)

   Er worden geen resultaten geretourneerd. Dit komt omdat het Celport-kanaal zo is geconfigureerd dat alleen remonderdelen en ophangingsonderdelen worden verkocht.

1. Experimenteer met het bijwerken van uw storefront configuratiedossier (`config.json`).

   1. Wijzig de waarden `ac-channel-id` en `ac-price-book` .

      U kunt bijvoorbeeld de kanaal-id wijzigen in het kanaal Kingsbluff en de prijs-boek-id in `east_coast_inc` . U kunt de onderdelencategorieën zien beschikbaar voor Kingsbluff door het *Kingsbluff deelcategorieën* beleid te herzien.

   1. Sla het bestand op.

      Wanneer u het bestand opslaat, wordt de lokale voorvertoning automatisch bijgewerkt.

   1. Geef een voorvertoning van de wijzigingen weer in de browser door met de functie Zoeken naar bandonderdelen te zoeken.

      Let op de verschillende beschikbare onderdeeltypen en noteer de prijzen die aan het Kingsbluff-kanaal zijn toegewezen.

      Door kopbalwaarden in het storefront configuratiedossier te veranderen en de bijgewerkte storefront te verkennen, kunt u zien hoe gemakkelijk het is om de catalogusmening en gegevensfilters bij te werken om de storefront ervaring aan te passen.

## Dat is het!

In deze zelfstudie hebt u geleerd hoe u met [!DNL Adobe Commerce Optimizer] de catalogus kunt ordenen zodat deze overeenkomt met de handelsbewerkingen met behulp van één basiscatalogus. U hebt ook geleerd hoe u een winkel kunt instellen die wordt aangedreven door Edge Delivery Services.

## Hoe verder?

Om te leren hoe u de Ontdekking en de Aanbevelingen van het Product kunt gebruiken om de het winkelen ervaring voor uw klanten te personaliseren, zie het [ handelend overzicht ](../merchandising/overview.md).
