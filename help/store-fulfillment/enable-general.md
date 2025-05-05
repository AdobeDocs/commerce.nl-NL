---
title: Algemene configuratie
description: Vorm algemene montages om  [!DNL Store Fulfillment]  voor uw opslag toe te laten. Configureer algemene extensie-instellingen, systeeminstellingen voor registratie, gegevenssynchronisatie en beveiliging. Belangrijke gegevens leveren om de integratie tussen Adobe Commerce en Store Fulfillment Services mogelijk te maken.
role: Admin
level: Intermediate
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '2405'
ht-degree: 0%

---

# Winkelservice en verkoopconfiguratie

Schakel [!DNL Store Fulfillment] -extensie in via [!DNL Commerce] Admin door extensie-instellingen, de beveiligingsinstellingen voor gebruikers van de app Store Assist en de opties voor de leveringsmethode te configureren.

>[!IMPORTANT]
>
>De configuratie van de service Afhandeling opslaan is alleen van toepassing nadat u een verbinding tot stand hebt gebracht tussen uw Adobe Commerce-exemplaar en de [!DNL Store Fulfillment] -app. Zie [ Connect Store Fulfillment ](connect-set-up-service.md).

## Instellingen voor services voor winkeluitvoering beheren

Instellingen voor services voor winkelvervulling beheren vanuit het menu [!DNL Commerce Admin Store Configuration] .

- Schakel de extensie in, configureer algemene instellingen en geef beveiligingsopties op voor gebruikersverbindingen en accounts van de app Store Assist door **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]** te selecteren.

  ![ de dienstenconfiguratie van de Opslag Admin voor de Afhandeling van de Opslag ](assets/store-services-admin-sf-config.png)

- Configureer leveringsmethoden door **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]** te selecteren.

  ![ de verkoopconfiguratie van de Winkel Admin voor de Afhandeling van de Opslag ](assets/store-sales-admin-sf-deliver-config.png)

## Basisinstellingen

<table>
<thead>
<tr>
<td><strong>Veld</strong></td>
<td><strong>Beschrijving</strong></td>
<td><strong>Toepassingsgebied</strong></td>
<td><strong>Vereist</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>De prijs die u de klant in rekening brengt voor het ophalen in de winkel. Heeft als standaardwaarde nul.</td>
<td>Website</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>De straal, in kilometers, die moet worden gebruikt wanneer een verkoopster zoekt naar een locatie voor het ophalen van een winkel in het winkeluitchecken. De zoekresultaten retourneren alleen opslagruimten die zich binnen de opgegeven zoekstraal bevinden.</td>
<td>Website</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>Bericht dat toont wanneer een klant in-store bestelwagen voor een punt selecteert dat niet beschikbaar voor in-store bestelwagen is. U kunt de standaardtekst desgewenst aanpassen.
</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>Het [!UICONTROL Search Radius] plaatsen wordt gebruikt slechts als u de [ opslagplaats en kaartopstelling ](store-location-map-provider-setup.md) voor Adobe Commerce hebt gevormd.

## De oplossing voor winkelvervulling inschakelen

Schakel de [!DNL Store Fulfillment] -oplossing in om de mogelijkheden voor het ophalen in de winkel en in de curbside toe te voegen aan de ervaringen bij winkelen en afrekenen in uw Adobe Commerce-winkel.

<table>
<thead>
<tr>
<td><strong>Veld</strong></td>
<td><strong>Beschrijving</strong></td>
<td><strong>Toepassingsgebied</strong></td>
<td><strong>Vereist</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>Schakel de oplossing in of uit. Indien deze optie is ingeschakeld, configureert en gebruikt u de mogelijkheden voor winkelvervulling en maakt u de verbinding tussen uw Adobe Commerce-winkel en [!DNL Store Fulfillment] -services. Als deze optie is uitgeschakeld, zijn alle functies van Afhandeling van winkel uitgeschakeld en is er geen communicatie tussen Adobe Commerce en de service Afhandeling van winkel. Bestelgegevens kunnen niet worden verwerkt of ontvangen.</td>
<td>Website</td>
<td>Ja</td>
</tr>
</tbody>
</table>

## Accountgegevens toevoegen

<table>
<tr>
<td><strong>Veld</strong></td>
<td><strong>Beschrijving</strong></td>
<td><strong>Toepassingsgebied</strong></td>
<td><strong>Vereist</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>Selecteer <i>[!UICONTROL Sandbox]</i> of <i>[!UICONTROL Production]</i><br></br> Selecteren [!UICONTROL Sandbox] om communicatie met uitvoeringsservices in een testomgeving mogelijk te maken.<br></br> Selecterend [!UICONTROL Production] laat communicatie met de uitvoeringsdiensten in een levende milieu toe.<br></br> u wordt gegeven een reeks geloofsbrieven voor elk milieu en kan beide reeksen in de zelfde installatie beheren. <br></br> sparen de geloofsbrieven alvorens de verbinding te bevestigen.</td>
<td>Algemeen</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>De URL naar het eindpunt van de Fulfillment API van de Winkel van de Marm. De waarde moet de volledig gekwalificeerde URL zijn die tijdens het instapproces wordt verstrekt. Klanten die aan Afhandeling van winkels werken, ontvangen zowel een sandbox- als een productie-URL. Wanneer u de waarden toevoegt, moet u de volledige URL kopiëren en plakken, inclusief de schuine streep "/".</td>
<td>Algemeen</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>URL aan het eindpunt van de Authentificatie van de Opslag van de Marm. De waarde moet de volledig gekwalificeerde URL zijn die tijdens het instapproces wordt verstrekt. U ontvangt zowel een sandbox als een productie-URL. Wanneer u de waarden toevoegt, moet u de volledige URL kopiëren en plakken, inclusief de schuine streep "/".</td>
<td>Algemeen</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>Uw unieke bedrijfs-id (huurder) die tijdens het instapproces is opgegeven. Deze identiteitskaart wordt gebruikt aan routeorden om ervoor te zorgen dat uw handelaarsopslag hen ontvangt.</td>
<td>Algemeen</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>De unieke integratie-id die tijdens het instapproces wordt opgegeven. Deze id wordt gebruikt om alle communicatie tussen Adobe Commerce te verifiëren en uitvoeringsservices op te slaan.</td>
<td>Algemeen</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>De unieke integratietoets die tijdens het instapproces wordt geleverd. Deze sleutel wordt gebruikt om alle communicatie tussen Adobe Commerce en de dienst van de opslagvervulling voor authentiek te verklaren.</td>
<td>Algemeen</td>
<td>Ja</td>
</tr>
</table>

Nadat u [!UICONTROL Account Credentials] hebt geconfigureerd, selecteert u <strong>[!UICONTROL Validate Credentials]</strong> om voor het eerst een verbinding tot stand te brengen met de service voor winkelvervulling.

## Logboek configureren

Logbestanden voor services voor winkelvervulling zijn beschikbaar in het logbestand `var/log/walmart-bopis.log` .

Vraag de systeembeheerder om uw milieu&#39;s te vormen om uitzonderingsbehandeling toe te staan zodat API-verwante uitzonderingen door de firewall of het geheime voorgeheugen kunnen worden gevangen.

Omdat het dossier van het toepassingslogboek snel kan groeien, laat registreren voor de toepassing slechts voor een korte tijd toe wanneer nodig-bijvoorbeeld wanneer het oplossen van problemen opslagkwesties voor een [!DNL Commerce] orde. Deze configuratie voorkomt problemen met de responstijd in productieomgevingen die worden veroorzaakt door grote logbestanden.

>[!TIP]
>
>Vraag uw systeembeheerder voor Adobe Commerce-installaties op locatie om logrotatie voor het `var/log/walmart-bopis.log` -bestand in te stellen om de grootte tot een minimum te beperken. Voor Adobe Commerce op-gebouw installaties, zie {de omwenteling van het 0} Logboek [&#128279;](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings) in de _Gids van de Installatie van Adobe Commerce_.  Voor Adobe Commerce op de projecten van de wolkeninfrastructuur, zie [ Mening en beheer logboeken ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).

<table>
<thead>
<tr>
<td><strong>Veld</strong></td>
<td><strong>Beschrijving</strong></td>
<td><strong>Toepassingsgebied</strong></td>
<td><strong>Vereist</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>Zuiver Wijze wordt gebruikt om de geregistreerde activiteit binnen de integratie te verhogen. Als deze optie is uitgeschakeld, wordt er geen foutopsporingsinformatie geregistreerd. Wanneer toegelaten, zuivert alle informatie <br></br> wordt het programma geopend Alle geregistreerde gegevens kunnen in het dossier worden gevonden: <pre>var/log/walmart-bopis.log</pre>
<td>Algemeen</td>
<td>Nee</td>
</tr>
</tbody>
</table>

## Ordersynchronisatie beheren

Configureer de instellingen voor het beheer van foutafhandeling voor ordersynchronisatie, cataloguskenmerken die moeten worden gebruikt voor het scannen van streepjescodes tijdens het selecteren van bestellingen, en configureer de batchformaten voor de wachtrij met opslagtegoeden.

U kunt details over de verrichtingen van de ordesynchronisatie van het dashboard van het Beheer van de Rij van de Opslag in Admin bekijken (
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>).

### Synchronisatie-foutbeheer

<table>
<tr>
<td><strong>Veld</strong></td>
<td><strong>Beschrijving</strong></td>
<td><strong>Toepassingsgebied</strong></td>
<td><strong>Vereist</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>Hiermee worden de pogingen voor het opnieuw proberen van een recordsynchronisatiebewerking opgegeven nadat een kritieke fout is opgetreden.<br></br> de Kritieke fouten komen voor wanneer de integratie er niet in slaagt een positieve reactie van de uitvoeringsdienst te krijgen. Deze kwesties komen voor wanneer de dienst neer is, of wanneer er een fout in de ordegegevens is die worden verzonden.<br></br> wanneer de retry drempel wordt bereikt, blijft het punt in een rij maar niet opnieuw verwerkt. Alle items met fouten van <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> Management weergeven in de beheerfunctie. Neem contact op met uw accountmanager om problemen op te lossen met onderdelen die op consistente wijze mislukken.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>Schakel foutmeldingen in om een e-mail te ontvangen wanneer de [!UICONTROL Retry Critical Error Threshold] voor een bestelling is bereikt. Het bericht bevat alle beschikbare gegevens over de fout.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>Een door komma's gescheiden lijst met e-mailadressen van ontvangers voor foutmeldingen.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>Hier geeft u de e-mailsjabloon op die wordt gebruikt om ontvangers op de hoogte te stellen van fouten bij de synchronisatie van bestellingen. Er is een standaardsjabloon beschikbaar. Aanpassing wordt niet ondersteund.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
</table>

### Ordersynchronisatie

<table>
<thead>
<tr>
<td><strong>Veld</strong></td>
<td><strong>Beschrijving</strong></td>
<td><strong>Toepassingsgebied</strong></td>
<td><strong>Vereist</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>Het cataloguskenmerk dat de scannbare code voor overeenkomende items opslaat op uw bedrijfslocaties.<br></br> als u slechts één bestaande handelaarplaats hebt, is het waarschijnlijk dat u codes UPC gebruikt, terwijl uw e-commercekanaal producten door SKU identificeert. In dit scenario, selecteer het catalogusattribuut dat de code UPC bevat.<br></br> Dit het plaatsen zorgt ervoor dat de orden die naar uw punten van de opslaglijst met het correcte herkenningsteken worden verzonden zodat de opslagvennoten punten tijdens het plukken proces nauwkeurig kunnen aftasten.<br></br> als u onzeker bent, controleer met uw uitvoeringsassociates in de Verzending en het Schoppen afdeling om te bepalen welke eigenschap zou moeten worden verzonden. Als het kenmerk momenteel niet is opgenomen in de database, kunt u het kenmerk toevoegen aan de set Adobe Commerce-productkenmerken.</td>
<td>Website</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>Het cataloguskenmerk dat de bron van de streepjescode voor overeenkomende items opslaat op uw bedrijfslocaties.<br></br> Dit het plaatsen zorgt ervoor dat de orden die naar uw punten van de opslaglijst met correct herkenningsteken worden verzonden zodat de opslagvennoten punten tijdens het plukken proces nauwkeurig kunnen aftasten. De opties omvatten - SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Price Embedded UPC.<br></br> als u onzeker bent, selecteer de optie die het meest op de waarden in uw [!UICONTROL Barcode Source] attribuut lijkt. Associaten van winkels kunnen nog steeds handmatig overeenkomen met items in hun keuzelijst.</td>
<td>Website</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>Het maximumaantal items dat in één keer uit de wachtrij voor winkelvervulling moet worden verzonden.<br></br> BOPIS de orden worden verzonden naar de uitvoeringsdienst in partijen, met regelmatige intervallen. Met deze instelling kunt u de grootte van de batch bepalen.<br></br> de standaardwaarde is 100 punten. Afhankelijk van het volume en de capaciteit van uw bestelling kunt u de maximale waarde naar boven of naar beneden aanpassen.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
</tbody>
</table>

## Verzendopties voor winkelvervulling inschakelen

Configureer de verzendopties voor de afhandeling van winkels die de beschikbaarheid bepalen van opties voor het ophalen en leveren van items in de winkel voor uw Adobe Commerce-winkels.

### Verzenden naar winkel

<table>
<thead>
<tr>
<td><strong>Veld</strong></td>
<td><strong>Beschrijving</strong></td>
<td><strong>Toepassingsgebied</strong></td>
<td><strong>Vereist</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>De instelling voor het naar de winkel verzenden van verzendingen is gebaseerd op uw bestaande verzendmogelijkheden. Als u Inventory management gebruikt, of als u bestellingen kunt accepteren en uitvoeren op zakelijke locaties zonder voorraad via voorraadoverdrachten van winkel naar winkel, stelt u deze optie in op Ja.<br></br> als u niet de schip-aan-opslag optie kunt steunen of het niet wenst aan te bieden, reeks aan ` Geen `. Als deze optie is uitgeschakeld, worden items in uw catalogus met een nulvoorraad voor een winkel of items die onder de [!DNL Out of Stock Threshold] voor die locatie liggen, niet aangeboden met opties voor het ophalen in de winkel.<br></br> u kunt de waarde van dit het plaatsen per handelaarplaats aanpassen.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
</tbody>
</table>

### Verzenden uit winkel

<table>
<thead>
<tr>
<td><strong>Veld</strong></td>
<td><strong>Beschrijving</strong></td>
<td><strong>Toepassingsgebied</strong></td>
<td><strong>Vereist</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>Schakelt de optie Home Delivery in of uit in uw winkels. Als deze optie is ingeschakeld, worden de locaties van uw winkels beschouwd als zijnde geaggregeerd met andere toegewezen bronnen in het bestand dat aan uw website is gekoppeld.<br></br> in de standaard diensten van Inventory management, is [!DNL Ship from Store] optie inherent en kan niet worden onbruikbaar gemaakt. Met de oplossing Afhandeling bewaren kunt u deze in- of uitschakelen.<br></br> u kunt dit het plaatsen per handelaarplaats en product aanpassen.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
</tbody>
</table>


## Gebruik accounts en machtigingen voor winkeluitvoering App beheren

Configureer de instellingen voor de gebruikersaccount en wachtwoordbeveiliging van de Store Fulfillment App en verificatie met twee factoren.

### Toepassingsbeveiliging

<table>
<thead>
<tr>
<td><strong>Veld</strong></td>
<td><strong>Beschrijving</strong></td>
<td><strong>Toepassingsgebied</strong></td>
<td><strong>Vereist</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>Het tijdframe, in seconden, dat een gebruikerssessie met een aan een winkel gekoppelde gebruiker actief blijft voordat deze automatisch wordt afgemeld. Geldige waarden liggen tussen 60 en 31536000.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>Hiermee geeft u het aantal mislukte aanmeldpogingen op dat is toegestaan voordat een aan een winkel gerelateerde persoon uit zijn of haar account is vergrendeld.<br></br> om rekeningslockout onbruikbaar te maken, plaats de waarde aan 0.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>Aantal minuten om een account te vergrendelen na mislukken van aanmelding.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td><em>[!UICONTROL Yes]</em>: Vereisen dat de gebruiker zijn wachtwoord wijzigt na het instellen van de account.<br></br><em>[!UICONTROL No]</em>: raadt de gebruiker aan het wachtwoord te wijzigen na het instellen van de account.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>Het aantal dagen dat een wachtwoord geldig blijft voordat een vereist wachtwoord wordt gewijzigd. Laat leeg om deze optie uit te schakelen.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
</tbody>
</table>

## Leveringsmethoden

Store Fulfillment werkt door de native Adobe Commerce [!DNL In-Store Delivery] mogelijkheden uit te breiden. Nadat u de extensie hebt geïnstalleerd, kunt u in-store leveringsmethoden configureren met behulp van de volgende uitgebreide instellingen die aan Admin worden toegevoegd.

- **Opname in-opslag** - de opties van de aanbieding voor in-opslag levering tijdens het controleproces
Deze montages vormen de gemeenschappelijkste leveringsscenario&#39;s voor bevelen BOPIS.

- **[!UICONTROL Curbside pick up]** - Aanbiedingsopties voor klanten om op een opslagplaats te parkeren en hun orde te laten leveren aan hen door een archiefmedewerker.

Configureer deze instellingen vanuit de beheerfunctie door <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong> te selecteren.

>[!NOTE]
>
>Voor extra informatie over het vormen van in-opslag leveringsopties, zie [ In-Store Levering ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery) in de _Gids van de Gebruiker van Adobe Commerce_.


### Configuratie van leveringsmethoden

Met de in-store leveringsmethode, kan de klant een bron selecteren die als oppiklocatie tijdens het uitrekenen moet worden gebruikt.

<table>
<thead>
<tr>
<td><strong>Veld</strong></td>
<td><strong>Beschrijving</strong></td>
<td><strong>Toepassingsgebied</strong></td>
<td><strong>Vereist</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>Schakel de optie Ophalen in de winkel die tijdens het uitchecken beschikbaar is in of uit voor klanten die Ophalen uit de winkel kiezen. Wanneer het ophalen in de winkel is uitgeschakeld, wordt de optie niet weergegeven.<br></br> dit globale plaatsen is op alle detailhandelsplaatsen van toepassing. Wanneer toegelaten, kunt u het bij de detailhandel plaats selectief onbruikbaar maken.</td>
<td>Website</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>Schakel de optie Ophalen curven tijdens het uitrekenen in of uit voor klanten die Ophalen van winkel kiezen.<br></br> dit globale plaatsen is op alle detailhandelsplaatsen van toepassing. Wanneer toegelaten, kunt u het bij de detailhandel plaats selectief onbruikbaar maken.</td>
<td>Website</td>
<td>Nee</td>
</tr>
</tbody>
</table>

### Configuratie van titel leveringsmethode

<table>
<thead>
<tr>
<th><strong>Veld</strong></th>
<th><strong>Beschrijving</strong></th>
<th><strong>Toepassingsgebied</strong></th>
<th><strong>Vereist</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Titel van thuislevering</strong></td>
<td>Hier geeft u de titel op die u wilt weergeven voor de optie Home Delivery in de producten-, winkelwagentje- en afrekengebieden. De levering van het huis verwijst naar de standaardverzendmogelijkheden van Adobe Commerce-van een pakhuis, door een drager, of direct aan het klant-verstrekte verzendadres. </br></br> Dit etiket beïnvloedt niet de verschepende methodeetiketten voor de geselecteerde verzendende drager.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Beschrijving van thuislevering</strong></td>
<td>Een optionele beschrijving die wordt weergegeven wanneer de Titel van thuislevering aan klanten wordt getoond. Meestal, is de beschrijving een statisch bericht om uw leveringsbeloftes mee te delen. Enkele voorbeelden:</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Titel voor ophalen van winkel</strong></td>
<td>Wanneer een klant leveringsopties wordt voorgesteld en de opname in de winkel beschikbaar is, wordt dit etiket getoond. </br></br> u kunt dit etiket aanpassen, dat in het product, het karretje, en controlegebieden toont.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<td><strong>Ophaalbeschrijving van winkel</strong></td>
<td>Waar de titel Ophalen winkel wordt weergegeven, kun je eventueel een beschrijving opnemen. Dit statische bericht helpt klantenmededelingen met betrekking tot de ervaring van de archiefbestelwagen verbeteren. Enkele voorbeelden:</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Titel voor ophaalservice in de winkel</strong></td>
<td>Wanneer Ophalen in de winkel is ingeschakeld, wordt deze titel aan klanten weergegeven als de optie Ophalen uit de winkel. U kunt het label ervan aanpassen.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<tr>
<td><strong>Titel voor ophalen krullen</strong></td>
<td>Wanneer de Bestelwagen van de Band wordt toegelaten, wordt de optie getoond aan klanten als een type van de optie van de Bestelwagen van de Opslag. U kunt het label hier aanpassen.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Instructies voor het in-store ophalen</strong></td>
<td>Wanneer een bestelling klaar is om in uw winkels te worden opgehaald, wordt de klant per e-mail op de hoogte gebracht. Als de klant [!DNL In-Store Pickup] heeft geselecteerd tijdens het uitchecken, kunt u hier de instructies voor het ophalen aanpassen. </br></br> deze instructies worden geplaatst globaal en zijn op alle detailhandelsplaatsen van toepassing. U kunt de instructies ook aanpassen op het niveau van de detailhandel.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Instructies voor ophaalcurven</strong></td>
<td>Geeft aangepaste instructies voor het ophalen van bestellingen op die moeten worden opgenomen in e-mailmeldingen van klanten voor bestellingen voor het ophalen van bestellingen op de achtergrond. </br></br> deze instructies worden geplaatst globaal en zijn op alle detailhandelsplaatsen van toepassing. U kunt de instructies ook aanpassen op het niveau van de detailhandel.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Geschatte levertijd voor afhalen</strong></td>
<td>Het aantal minuten dat is vereist voordat een bestelling is ontvangen, uitgevoerd en klaar om te worden opgehaald. Deze informatie wordt aan de klant getoond wanneer het selecteren van een detailhandelplaats voor de leveringsoptie van de Opslag van de Opslag. Deze instelling geldt voor alle winkellocaties. U kunt de aanlooptijd ook aanpassen op het niveau van de detailhandel.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Label voor geschatte ophaaltijd</strong></td>
<td>Hiermee geeft u de geschatte tijd weer tot een bestelling beschikbaar is voor het ophalen door de klant. Deze informatie wordt aan klanten getoond wanneer zij een detailhandelsplaats voor de [!DNL In-Store Pickup] leveringsoptie selecteren. </br></br> wanneer het aanpassen van dit etiket, kunt u de code <code>%1</code> gebruiken om uw <strong> Geschatte Tijd van de Bestelwagen van de Bestelwagen </strong> op te nemen. Bijvoorbeeld:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br> dit het plaatsen is op alle detailhandelopslagplaatsen van toepassing. U kunt de aanlooptijd ook aanpassen op het niveau van de detailhandel.</td>
<td>Winkelweergave</td>
<td>Nee</td>
<tr>
<td><strong>Disclaimer ophaaltijd</strong></td>
<td>De inhoud die wordt weergegeven op de productpagina in de knopinfo met winkeluren, feestdagen, onverwachte sluitingen enzovoort</td>
<td>Winkelweergave
</td>
<td>Nee
</td>
</tr>
</tbody></table>

### Configuratie Beschikbaarheid voorraad

<table>
<thead>
<tr>
<th><strong>Veld</strong></th>
<th><strong>Beschrijving</strong></th>
<th><strong>Toepassingsgebied</strong></th>
<th><strong>Vereist</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>In voorraad</strong></td>
<td>Wanneer een klant de detailhandel locator gebruikt, wordt de voorraadbeschikbaarheid voor de huidige punten getoond voor elke plaats. </br></br> U kunt het <em>[!UICONTROL in-stock]</em> statusetiket hier aanpassen.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Buiten de voorraad</strong></td>
<td>Wanneer een klant de detailhandel locator gebruikt, wordt de voorraadbeschikbaarheid voor om het even welke huidige punten getoond voor elke plaats.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Gedeeltelijk in voorraad</strong></td>
<td>Wanneer een klant de locator van de detailhandel gebruikt, wordt de voorraadbeschikbaarheid voor om het even welke huidige punten getoond voor elke plaats. </br></br> U kunt het <em>[!UICONTROL partially in-stock]</em> statusetiket hier aanpassen.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
</tbody></table>

