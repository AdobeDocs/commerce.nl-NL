---
title: Afhandeling van winkel testen en implementeren
description: Test een plan om de functionaliteit voor winkelvervulling te verifiëren. De tests hebben betrekking op de API voor inventarissynchronisatie, de end-to-end uitvoeringsworkflow voor geannuleerde bestellingen, het gebruikersbeheer van de app voor winkelafhandeling en de ervaring die de klant heeft met het inchecken.
role: User, Admin
level: Intermediate
feature: Shipping/Delivery, User Account, Roles/Permissions
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '2661'
ht-degree: 0%

---

# Afhandeling van winkel testen en implementeren voor Adobe Commerce

Nadat u het instapproces in uw ontwikkelingsmilieu hebt voltooid, kunt u het proces beginnen om de oplossing van de Vervulling van de Opslag aan uw productiemilieu te testen en op te stellen.

**Eerste vereisten**

Voordat u gegevens, opslaggegevens of bestellingen gaat testen of synchroniseren, controleert u of u de volgende taken hebt uitgevoerd:

- Voltooide de [ Algemene Configuratie ](enable-general.md) voor de diensten van de Afhandeling van de Opslag.

- [De accountgegevens en verbindingsgegevens voor uw sandbox- en productieomgeving toevoegen en valideren](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- Bevestig dat de [ Integratie van Adobe Commerce ](connect-set-up-service.md#configure-store-fulfillment-account-credentials) voor de oplossing van de Afhandeling van de Opslag beschikbaar en geautoriseerd is.

## Voorbereiden op testen

De verbindingsconfiguratie moet worden voltooid alvorens u om het even welke testorden kunt tot stand brengen of integratie het testen uitvoeren. Voordat u gaat testen, moet u ook controleren of de opslaggegevens zijn gesynchroniseerd.

1. De bronnen van de Afhandeling van de Opslag synchroniseren.

   - Ga naar **[!UICONTROL Stores > Sources]** .

   - Selecteer **[!UICONTROL Synchronize Store Fulfillment Sources]** .

1. Controleer in het opslagraster of opslagruimten zijn gemarkeerd als `Synced` voordat u testorders maakt.

## Monstertestplan

De detailhandelaars bevestigen de basisfunctionaliteit van de oplossing van de Afhandeling van de Opslag tijdens de configuratie en testfasen van een plaatsing. Dit voorbeeldtestplan biedt een beginpunt voor het testen. Voeg extra scenario&#39;s toe die op uw vereisten worden gebaseerd.

>[!NOTE]
>
>Nadat u het eerste instapsysteem voor de oplossing van de Behandeling van de Opslag hebt voltooid of een bestaande installatie hebt bijgewerkt, test u de toepassing altijd in een niet-productieomgeving voordat u de toepassing implementeert in de productie.

Dit steekproeftestplan bestrijkt de volgende functionele gebieden:

| Functioneel gebied | Functie | Rol |
|-------------------------------------|------------------------------------------|----------------------------------|
| Synchronisatie van inventarisatie en bestelling | API-inventarisatie | Adobe Commerce Admin |
| End-to-end | Workflows voor annulering van bestellingen | Klant, Admin, Store Associated |
| Beheerder | Machtigingen voor App-uitvoering opslaan | Beheerder |
| Adobe Commerce Frontend | Producttypen | Klant, beheerder |
| Frontend Controle </br> controle-binnen Vorm | Inchecken | Klant, beheerder |
| App Winkelassistentie | Het Stadium van de Bestelling </br> van de Beweging &lbrace;</br> en Handoff</br> | Winkelkoppeling |

### API-inventarisatie

Deze sectie van het testplan behandelt inventaris en ordesynchronisatie om te verifiëren dat de updates aan bestelbronnen en de voorraden correct tussen Adobe Commerce en de oplossing van de Behandeling van de Opslag worden gesynchroniseerd.

**Functioneel Gebied**: Overzicht en de Synchronisatie van de Orde </br>
**Rol:** Admin </br>
**Type van Test:** Alle Positief

<table>
<thead>
<tr>
<th>Functie</th>
<th>Scenario testen</th>
<th>Verwachte resultaten</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Ophaalvoorraadbron toevoegen</strong></td>
<td>Sla een nieuwe bron voor opgehaalde bestanden op.</td>
<td>De synchronisatie in real time verzendt de brondetails naar de dienst van Walmart GIF binnen 5 minuten.</td>
</tr>
<tr>
<td><strong>Bestaande bron van opgehaalde bestanden bijwerken</strong></td>
<td>Sla updates op naar een bestaande bron van ophaalvoorraad.</td>
<td>De synchronisatie in real time verzendt de details naar Walmart GIF binnen 5 minuten</td>
</tr>
<tr>
<td><strong>Status van voorraadbron voor ophaalservice </br><code>Is Synced</code></strong></td>
<td>Sla updates op naar een bestaande bron van ophaalvoorraad.</td>
<td>Na een geslaagde bewerking wordt de kolom <code>Is Synced</code> op de pagina Source beheren bijgewerkt van <code>No</code> naar <code>Yes</code> .</td>
</tr>
<tr>
<td><strong>Gewijzigde voorraadreserveringsprocedure</strong></td>
<td>Maak en verzend een nieuwe bestelling voor een product.</td>
<td>De verkoopbare hoeveelheid voor het product neemt dienovereenkomstig af.</td>
</tr>
<tr>
<td><strong>Nieuwe order-push, API-synchronisatie—Klantenvolgorde</strong></td>
<td>De klant dient een bestelling in voor het ophalen van de winkel.</td>
<td><ul><li>In de Admin mening van de Orde, ziet een <strong> gebruiker Admin van Adobe Commerce </strong> dat de status van de Synchronisatie van de Orde aan wordt bijgewerkt <code>Sent</code></li><li>Het logboek met de orderdetails bevat het bericht <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>New Order Push, API Sync—Admin verzendt order</strong></td>
<td>Een Adobe Commerce <strong> Admin </strong> legt een bestelorde voor.</td>
<td><ul><li>In de weergave Admin Order wordt de status van Order Sync bijgewerkt naar <code>Sent</code> .</li><li>Het logboek met de orderdetails bevat het bericht <code>Order was sent to BOPIS solution for sync, it's not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>New Order Push, Exception Queue<strong></td>
<td>Identificeer verscheidene Virtuele en downloadbare producten in de Admin van Adobe Commerce die door Adobe Commerce kunnen worden vervuld zonder interactie met de dienst van de Afhandeling (FaaS) te vereisen.</td>
<td>Deze producten worden in de uitvoer op de juiste wijze verwijderd of gemarkeerd om een downstreamconflict met de FaaS te voorkomen.</td>
</tr>
</tbody>
</table>

### Workflows voor annulering van bestellingen

Deze sectie van het testplan omvat scenario&#39;s om het werkschema van begin tot eind voor orden te testen die door Adobe Commerce worden geannuleerd.

**Functioneel gebied:** Admin van Adobe Commerce </br>
**Rol:** Eind-aan-Eind (Admin, de Associatie van de Opslag, Klant) </br>
**Resultaattype van de Test:** Positief voor alle scenario&#39;s

<table style="table-layout:fixed">
<tr>
<th>Functie</th>
<th>Scenario</th>
<th>Verwachte resultaten</th>
</tr>
<tr>
<td><strong>Volledige annulering van bestelling</strong></td>
<td><ol>
<li>Plaatsingsvolgorde.</li>
<li>Wacht tot de volgorde is gesynchroniseerd.</li>
<li>Controleer of de factuur is aangemaakt (als u autoriseert en vastlegt).</li>
<li>Maak een creditmemo met alle bestelde producten uit de weergave Factuur.</li>
</ol>
</td>
<td>
<ul>
<li>Ordergeschiedenis bijgewerkt met <code>We refunded $X online. Transaction ID: transactionID</code> en <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>Status van bestelling is <code>Closed</code> . (We hebben nu een BETALINGSREVISIE ingesteld.)</li>
<li>Creditnota gemaakt in Adobe Commerce. (Wacht tot het uitsnijden werkt.)</li>
<li>Als alle items zijn opgepakt, verschijnt de markering <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> is <code>true</code> .) en verschijnt deze e-mail vervolgens.<code>DISPLAY COMMENT HISTORY</code></li>
<li>Als alle items niet zijn gekozen, wordt het e-mailbericht geannuleerd en wordt de HISTORIE VOOR OPMERKINGEN WEERGEGEVEN <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> markering is <code>true</code> .)</li>
</ul>
</td>
</tr>
<tr><td><strong>Ongedaan maken gedeeltelijke bestelling<strong></td>
<td>
<ol>
<li>Plaats de bestelling met ten minste twee producten.</li>
<li>Wacht tot de volgorde is gesynchroniseerd.</li>
<li>Controleer of de factuur is gemaakt (indien geautoriseerd en vastgelegd) en of de factuur per e-mail is ontvangen.</li>
<li>Wacht twee uur op transactieafwikkeling.</li>
<li>Maak een creditmemo met slechts een deel van de bestelde producten uit de weergave Factuur.</li>
</td>
<td>
<ul>
<li>Update voor ordergeschiedenis: <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>Update voor ordergeschiedenis: <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>E-mailbericht voor terugbetaling van bestelling: <code>$x amount was refunded</code></li>
<li>Status van bestelling is <code>Processing</code> .</li>
<li>Creditnota gemaakt in Adobe Commerce (wacht tot de afbouw werkt).</li>
<li>Als sommige items niet zijn gekozen, controleert u of het e-mailbericht van [!UICONTROL Ready for Pickup] met de sectie Geen keuze of Geen terugbetaling wordt weergegeven. <code>DISPLAY COMMENT HISTORY</code> toont <code>Order is ready for pickup, but some items not available.</code> .</li>
<li><code>CUSTOMER NOTIFIED</code> markering is <code>true</code> .</li>
</ul>
</td>
</tr>
<td><strong>Klaar voor Bestelwagen </br></br> Volledige annulering </br> (alle producten worden geplaatst zoals opgenomen met 0 qty)</strong></td>
<td>
<ol>
<li>Plaats de bestelling.</li>
<li>Wacht tot de volgorde is gesynchroniseerd.</li>
<li>Controleer of de factuur is gemaakt (indien geautoriseerd en vastgelegd) en of de factuur per e-mail is ontvangen.</li>
<li>Ga naar de Postman en voer de aanvraag Ready for Pickup uit met alle producten ingesteld als <code>picked</code> met <code>0 qty</code> .</li>
</ol>
</td>
<td>
<ul>
<li>Orderhistorie bijgewerkt: <code>We refunded $X offline</code></li>
<li>De orderstatus is <code>CLOSED</code> .
<li>Het creditmemo wordt gemaakt. (Wacht tot het uitsnijden werkt.)</li>
<li>E-mailadres voor terugbetaling ontvangen: <code>$x amount was refunded</code></li>
<li>E-mailbericht voor annulering van bestelling verzonden.</li>
</ul>
</td>
</tr>
<tr>
<td><strong> Klaar voor Bestelwagen - Gedeeltelijke annulering </strong></br></br> <strong> (Sommige producten worden geplukt, en sommige worden genomen met <code>0 qty</code>) </strong>
</td>
<td>
<ol>
<li>Plaats de bestelling.</li>
<li>Wacht tot de volgorde is gesynchroniseerd.</li>
<li>Controleer of de factuur is gemaakt (indien geautoriseerd en vastgelegd) en of de factuur per e-mail is ontvangen.</li>
<li>Ga naar de Postman en voer het "Ready for Pickup"-verzoek uit met een deel van de producten die zijn ingesteld op 0 qty en de rest van de producten is opgepikt.</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> met [!UICONTROL Ready for Pickup Items] en [!UICONTROL Canceled Items] tabellen. </li>
<li>De status van de bestelling is READY FOR PICKUP. </li>
<li>Orderhistorie bijgewerkt: <code>We refunded $X offline.</code>
<li>Orderhistorie bijgewerkt: <code>Order notified as partly canceled at: Date and hour</code>
<li>E-mailadres voor terugbetaling ontvangen: <code>$x amount was refunded</code>
<li>De creditmemo wordt gemaakt. (Wacht tot het uitsnijden werkt.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong> Klaar voor Bestelwagen - Gedeeltelijke Annulering </br></br> Sommige producten worden geplukt, en sommige worden genomen met <code>0 qty</code>) </strong>
</td>
<td><ol>
<li>Plaats de bestelling.</li>
<li>Wacht tot de volgorde is gesynchroniseerd.</li>
<li>Controleer of de factuur is gemaakt (indien geautoriseerd en vastgelegd) en of de factuur per e-mail is ontvangen.</li>
<li>Ga naar de Postman en voer het "Ready for Pickup"-verzoek uit met een deel van de producten die zijn ingesteld op 0 qty en de rest van de producten is opgepikt.</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> met [!UICONTROL Ready for Pickup Items] en [!UICONTROL Canceled Items] tabellen. </li>
<li>De status van de bestelling is READY FOR PICKUP. </li>
<li>Orderhistorie bijgewerkt: <code>We refunded $X offline.</code>
<li>Orderhistorie bijgewerkt: <code>Order notified as partly canceled at: Date and hour</code>
<li>E-mailadres voor terugbetaling ontvangen: <code>$x amount was refunded</code>
<li>De creditmemo wordt gemaakt. (Wacht tot het uitsnijden werkt.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong> Verworpen (tijdens dispensatie) </br></br> Volledige annulering (alle producten worden geplaatst zoals verworpen) </strong>
</td>
<td>
<ol>
<li>Plaats de bestelling.</li>
<li>Wacht tot de volgorde is gesynchroniseerd.</li>
<li>Controleer of de factuur is gemaakt (indien geautoriseerd en vastgelegd) en of de factuur per e-mail is ontvangen.</li>
<li>Ga naar de Postman en voer het "Ready for Pickup"-verzoek uit met alle producten ingesteld zoals u hebt gekozen.</li>
<li>Open uw brievenbus, vind Klaar voor Bestelwagen e-mail. Klik vervolgens op **[!UICONTROL Confirm Arrival]**.</li>
<li>Inchecken.</li>
<li>Ga naar Postman en voer het verzonden verzoek uit terwijl alle producten zijn ingesteld als afgewezen.</li>
</ol>
<td><ul>
<li>Orderhistorie bijgewerkt: <code>We refunded $X offline.</code></li>
<li>E-mailadres voor terugbetaling ontvangen: <code>$x amount was refunded</code></li>
<li>Status ingesteld op <code>CLOSED</code> .</li>
<li>Creditmemo gemaakt. (Wacht tot het uitsnijden werkt.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong> Verzonden (tijdens dispensatie) </br></br> Gedeeltelijke Annulering </br> (Sommige producten worden weggelaten; sommige worden verworpen.) </strong>
</td>
<td>
<ol>
<li>Plaats de bestelling.</li>
<li>Wacht tot de volgorde is gesynchroniseerd.</li>
<li>Controleer of de factuur is gemaakt (indien geautoriseerd en vastgelegd) en of de factuur per e-mail is ontvangen.</li>
<li>Ga naar Postman en voer het "Ready for Pickup"-verzoek uit met alle producten die zijn ingesteld als gekozen.</li>
<li>Open uw postvak. Zoek de e-mail Ready for Pickup en selecteer <code>Confirm Arrival</code> .</li>
<li>Inchecken.</li>
<li>Ga naar de Postman en voer het verzonden verzoek uit met bepaalde producten die zijn opgegeven en waarvan sommige zijn afgewezen</li>
</ol>
</td>
<td>
<li>Orderhistorie bijgewerkt: <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>E-mailadres voor terugbetaling ontvangen: <code>$x amount was refunded</code>
<li>Status van bestelling ingesteld op <code>Ready for pickup Dispensed</code>
<li>Creditmemo gemaakt. (Wacht tot het uitsnijden werkt.)</li>
</td>
</tr>
<tr>
<td> <strong> Nieuwe RMA na terugkeer (volledig) </strong>
</td>
<td>
<ol>
<li>Plaats de bestelling.</li>
<li>Wacht tot de volgorde is gesynchroniseerd.</li>
<li>Als de optie voor autoriseren en vastleggen is geconfigureerd, controleert u of de factuur is gemaakt en of de klant de factuur per e-mail heeft ontvangen.</li>
<li>Kies alle producten met Postman.</li>
<li>Inchecken.</li>
<li>Maak een dispensatie.</li>
<li>Ga naar orde, en selecteer <strong>[!UICONTROL Create returns]=
<li>Maak de RMA.</li>
</ol>
</td>
<td>
<ul>
<li>De RMA is gemaakt en wordt weergegeven onder het tabblad <strong>[!UICONTROL Returns]</b> in de weergave Volgorde.</li>
<li>De klant heeft een bevestigingsbericht van RMA ontvangen.</li>
</ul>
</td>
</tr>
<tr>
<td><strong> Nieuwe RMA na terugkeer - Gedeeltelijk </strong>
</td>
<td>
<ol>
<li>Plaats de bestelling.</li>
<li>Wacht tot de volgorde is gesynchroniseerd.</li>
<li>Controleer of de factuur is gemaakt (indien geautoriseerd en vastgelegd) en of de factuur per e-mail is ontvangen.</li>
<li>Kies alle producten met Postman.</li>
<li>Inchecken.</li>
<li>Maak een dispensatie.</li>
<li>Ga de orde, en selecteer  <strong>[!UICONTROL Create returns]</strong></li>
<li>Creeer RMA met een deel van de bevolen producten.</li>
</ol>
<td>
<ul>
<li>RMA gemaakt en weergegeven onder het tabblad <strong>[!UICONTROL Returns]</strong> in de weergave Volgorde.</li>
<li>De klant heeft het bevestigingsbericht van RMA ontvangen.</li>
<li>Nadat u RMA hebt gemaakt, haalt u de RMA-autorisatie op: Ga vanuit de beheerfunctie naar <strong>[!UICONTROL Sales > Returns]</strong> . Selecteer de RMA die u hebt gemaakt en autoriseer deze.</li>
<li>Controleer of de klant het bevestigingsbericht voor de RMA-autorisatie heeft ontvangen.</li>
<li>Controleer of de restitutie is toegevoegd aan de transacties en de ordergeschiedenis.</li>
</ul>
</td>
</tr>
</table>


### Machtigingen voor App-uitvoering opslaan

In dit gedeelte van het testplan wordt het accountbeheer voor App Users-gebruikers voor Store Fulfillment besproken.

- Bevestig dat een Winkelgeassocieerde kan verifiëren met een nieuwe gebruikersaccount die is gemaakt met Adobe Commerce Admin.
- Bevestig dat updates van bestaande accounts correct zijn toegepast.

**Functioneel gebied:** Admin van Adobe Commerce </br>
**Rol:** Admin, Geassocieerde Opslag </br>
**Type van Test:** Alle positief

<table style="table-layout:auto">
<tr>
<th>Functie</th>
<th>Scenario</th>
<th>Verwachte resultaten</th>
</tr>
<tr>
<td><strong> Beheer van de Rekening van de Gebruiker - creeer Rekening </strong></br></br>
</td>
<td>
<ol>
<li><strong> Admin </strong> — Logboek in Admin van Adobe Commerce</li>
<li>Ga naar <strong>[!UICONTROL System] &gt; Enable Fulfillment App &gt; All Store Fulfillment App Users </strong></li>
<li><strong>Nieuwe gebruiker toevoegen.</strong></li>
</ol>
<td>
<ul>
<li>Account is gemaakt.</li>
<li>De nieuwe rekening van de Gebruiker wordt getoond op het [!UICONTROL Store Fulfillment Users] dashboard.</li>
<li><strong> Geassocieerde van de Opslag </strong> login aan Winkel bijstaat app met nieuwe gebruikersrekening.</li>
</ul>
</td>
</tr>
<tr>
<td><strong> Beheer van de Rekening van de Gebruiker - werk bestaande gebruikersrekening </strong> bij
</td>
<td>
<ol>
<li>Meld u aan bij de Adobe Commerce Admin-gebruikersaccount.</li>
<li>Ga naar <strong>[!UICONTROL System] &gt; Enable Fulfillment App &gt; All Store Fulfillment App Users </strong>.</li>
<li>Open in de lijst Gebruikersaccount een bestaande actieve gebruikersaccount door <strong>[!UICONTROL Edit]</strong> te selecteren.
<li>Maak de rekening onbruikbaar door <strong>[!UICONTROL Is Active]</strong> in <strong> Nr </strong> te veranderen.</li>
</ol>
</td>
<td>
<ul>
<li>Op het dashboard van <strong>[!UICONTROL Store Fulfillment App Users]</strong> is de status voor de bijgewerkte account gewijzigd in <strong>[!UICONTROL Inactive]</strong> .</li>
<li>Store Associate kan zich niet aanmelden bij de app Store Assist met de inactieve accountgegevens.</li>
</ul>
</td>
</tr>
</table>

## Adobe Commerce-producttypen

De testscenario&#39;s voor de Types van Product van Adobe Commerce verifiëren dat de klanten het correcte product, de voorraad, en de informatie van de leveringsmethode voor verschillende producttypes zien:

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] in de Adobe Commerce-winkel.

**Functioneel gebied:** Voorste van Adobe Commerce </br>
**Rol:** de Hulp van de opslag App Gebruiker (Geassocieerde Opslag) </br>
**Type van Test:** Alle positief

<table style="table-layout:auto">
<tr>
<th>Functie</th>
<th>Scenario</th>
<th>Opmerkingen</th>
</tr>
<tr>
<td><strong> Configureerbare producten </strong>
</td>
<td>
<ul>
<li>Verifieer dat de gebruiker slechts die configureerbare opties kan zien, welke bron wordt toegelaten, de voorraad wordt toegewezen en dat er sommige punten in voorraad-controle kindproducten zijn.</li>
<li>Controleer of bij het selecteren van een andere winkel de opties die niet beschikbaar zijn, worden weergegeven als doorgestreept.</li>
<li>Controleer of configureerbare opties niet zijn geselecteerd als de gebruiker een andere winkel selecteert.</li>
<li>Controleer of een configureerbaar product al in de winkelwagentje zit en een gebruiker een andere winkel selecteert, zodat het product niet meer in voorraad is.</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong> Gegroepeerde producten </strong>
</td>
<td>
<ul>
<li>Controleren of de leveringsmethoden en de knop [!UICONTROL Add to cart] zijn uitgeschakeld voor de klant wanneer alle onderliggende producten
<code>qty</code> ingesteld op <code>0</code> .</li>
<li>Controleren of de leveringsmethoden zijn ingeschakeld voor de klant wanneer ten minste een van de onderliggende producten is ingesteld op <code>qty</code> <code>0.</code></li>
<li>Controleer of de methode [!UICONTROL Store Pickup Delivery] alleen zichtbaar en actief is voor de producten waarvoor [!UICONTROL Available for Store Pickup] is ingeschakeld. (Controleer het onderliggende product.)</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong> Virtuele producten </strong>
</td>
<td>
Controleer of virtuele producten de leveringsmethode [!UICONTROL In-store Pickup] niet bieden.
<td></td>
</td>
</tr>
<tr>
<td><strong> Bundel producten </strong>
</td>
<td>
<ul>
<li>Controleer of als [!UICONTROL Available for Store Pickup] ten minste één onderliggend product is uitgeschakeld, de optie Ophalen bij opslaan niet beschikbaar is voor de klant.</li>
<li>Controleer of de optie Home Delivery niet beschikbaar is voor de klant als ten minste één onderliggend product [!UICONTROL Available for Home Delivery] is uitgeschakeld.</li>
<li>Controleren of ten minste een van de onderliggende producten in een bundel uit voorraad is, wordt de bundel (het bovenliggende product) ook weergegeven
als [!UICONTROL Out of stock] .</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## Inchecken

Deze sectie van het testplan behandelt de Controle-In Ervaring voor de Bestellingen van de Bestelwagen van de Opslag voor de volgende mogelijkheden:

- Contact opnemen met andere gebruikers - Controleer de workflow voor het toevoegen van een [!UICONTROL Alternate Pickup Contact] en het selecteren van een [!UICONTROL Preferred Contact] op bestellingen voor ophaalbewerkingen in de winkel.

- Inchecken formulier—Controleer de workflow voor het indienen van een incheckaanvraag voor bestellingen voor winkelbestellingen.

**Functionele gebieden:** Controle van de Kar, Controle-binnen Vorm voor de orden van de archiefbestelwagen </br>
**Rol:** Admin, Klant, Geassocieerde Opslag </br>
**Type van Test:** Alle positief

### Contactpersoon voor afhalen alternatief


**Functioneel gebied:** Uitchecken van winkelwagentje </br>
**Rol:** Klant </br>
**Type van Test:** Alle positief

<table style="table-layout:auto">
<tr>
<th>Functie</th>
<th>Scenario</th>
<th>Verwachte resultaten</th>
</tr>
<tr>
<td><strong>De Afwisselende Contact van de Bestelwagen </br>
Inchecken<strong>
</td>
<td>
Een klant verzendt een bestelling met de optie Ophalen in de winkel.</td>
<td>Tijdens het afrekenen ziet de klant de optie [!UICONTROL Alternate Pickup Contact] op de stap Verzenden.
</td>
</tr>
<tr>
<td><strong> Afwisselende Gewenste Contact van de Bestelwagen, Controle binnen </strong>
<td>
Een klant verzendt een bestelling met de optie Ophalen in de winkel. Tijdens het uitchecken voegt de klant een [!UICONTROL Alternate Pickup Contact] toe.</td>
<td>Tijdens het afrekenproces ziet de klant de optie [!UICONTROL Preferred Contact] voor de verzending.</td>
</td>
</tr>
<tr>
<td><strong> Afwisselende Details van het Contact van de Bestelwagen, Controle binnen </strong>
</td>
<td>
Een klant verzendt een bestelling met de optie Ophalen in de winkel. Tijdens het afrekenen selecteert de klant [!UICONTROL Alternate Pickup Contact] bij de verzendstap.
</td>
<td>De klant ziet invoeropties voor het invoeren van contactgegevens: [!UICONTROL First name] , [!UICONTROL Last name] , [!UICONTROL Phone] en [!UICONTROL Email] .</td>
</tr>
<tr>
<td><strong> Afwisselende Bestelwagen, Controle in E-mail </strong>
</td>
<td>Een klant verzendt een bestelling met de optie Ophalen in de winkel. Tijdens het afrekenen selecteert de klant [!UICONTROL Alternate Pickup Contact] bij de verzendstap, voegt de contactgegevens toe en verzendt de bestelling.</td>
<td>Zowel de klant als de andere contactpersoon ontvangen een incheckbericht voor de bestelling.</td>
</tr>
<td><strong>Alternatieve ophaling, orderdetails</strong></td>
<td>Een klant verzendt een bestelling met de optie Ophalen in de winkel. Tijdens het afrekenen selecteert de klant [!UICONTROL Alternate Pickup Contact] bij de verzendstap, voegt de contactgegevens toe en verzendt de bestelling.</td>
<td>De beheerder ziet de extra contactinformatie over de bewaarde orde.</td>
</tr>
<tr>
<td><strong> Afwisselend Contact van de Bestelwagen, de Geassocieerde de ordemening van de Opslag </strong>
</td>
<td>Een klant verzendt een bestelling met de optie Ophalen in de winkel. Tijdens het afrekenen selecteert de klant [!UICONTROL Alternate Pickup Contact] bij de verzendstap, voegt de contactgegevens toe en verzendt de bestelling.</td>
<td>De Store Associate kan de extra contactinformatie over de orde in FaaS/ChaaS zien.</td>
</td>
</tr>
</tbody>
</table>

### Formulier inchecken


**Functioneel gebied:** Controle-binnen Vorm </br>
**Rol:** Klant </br>
**Type van Test:** Alle positief

<table style="table-layout:auto">
<tr>
<th>Functie</th>
<th>Scenario</th>
<th>Verwachte resultaten</th>
</tr>
<tr>
<td><strong> Controle in actie-voorlegt verzoek </strong>
</td>
<td>Op het incheckformulier vult een klant alle vereiste velden in en verzendt de aanvraag.</td>
<td>De klant ontvangt een succesantwoord.</td>
</tr>
<tr>
<td><strong>Inchecken van handeling—Gegevens verzoek weergeven</strong></td>
<td>Een klant verzendt met succes een verzoek om inchecken.</td>
<td>De de statusupdates van de orde in het systeem FaaS, en de Vennoot van de Opslag kunnen de controle-binnen verzoekdetails in FaaS zien.
</td>
</tr>
<tr>
<td><strong>Inchecken - Verzoek slechts eenmaal indienen</strong></td>
<td>Na het voorleggen van een controle-binnen verzoek om een orde, selecteert een klant de verbinding aan controle een tweede keer.</td>
<td>Op het inchecken-formulier ziet de klant geen optie voor het bewerken of opnieuw verzenden van het formulier.</td>
</tr>
<tr>
<td><strong>Inchecken - Arrival bevestigen</strong></td>
<td>Een ophaalvolgorde in de winkel is gemarkeerd en kan worden opgehaald in de FaaS. De klant ontvangt een e-mailbericht Ready for Pickup en selecteert [!UICONTROL Confirm Arrival] .</td>
<td>De klant ziet het incheckformulier voor de bestelling.</td>
</tr>
</tbody>
</table>

## App Winkelassistentie

Deze sectie van het testplan behandelt scenario&#39;s voor het testen van orde, selecteren, en afleveringswerkschema&#39;s in de App van de Hulp van de Opslag.

**Functioneel gebied:** De opslag staat App </br> bij
**Rol:** Geassocieerde opslag </br>
**Type van Test:** Alle positief

<table style="table-layout:auto">
<tr>
<th>Functie</th>
<th>Scenario</th>
<th>Verwachte resultaten</th>
</tr>
<tr>
<td>
<strong> Enige orde het plukken-gelukkig weg, curbside oppikken </strong></td>
<td>Selecteer objecten van één en meerdere aantallen. Geen gelijke plukken, en curbside oppeling (met het opvoeren).
</td>
<td>
</td>
</tr>
<tr>
<td><strong>Ophalen van meerdere bestellingen—gelukkig pad, ophalen van curven</strong></td>
<td>Enkelvoudige en meervoudige items. Geen gelijke plukken, en curbside oppeling (met het opvoeren)</td>
<td></td>
</tr>
<tr>
<td><strong>Ophalen via één bestelling—ophalen via een gelukkig pad in de winkel</strong></td>
<td>Enkelvoudige en meervoudige items. Geen plukken van nul en ophalen in de winkel (met ophaling)</td>
<td>
</td>
</tr>
<tr>
<td><strong>Ophalen van meerdere bestellingen—gelukkig pad, ophalen in winkel</strong></td>
<td>Selecteer objecten van één en meerdere aantallen. Geen gelijke plukken, en curbside oppeling (met het opvoeren).</td>
<td></td>
</tr>
<tr>
<td><strong>Eén bestelling kiezen—geen gelukkig pad, in-store ophalen</strong></td>
<td>Afzonderlijke objecten en meerdere objecten kiezen met gedeeltelijk en niloogst en ophaalbewerkingen in de winkel (met ophaling)</td>
</td>
<td></td>
</tr>
<td><strong>Ophalen van meerdere bestellingen—niet ophalen van padcurbside</strong></td>
<td>Afzonderlijke objecten en meerdere objecten kiezen met gedeeltelijk en niloogst en ophaalbewerkingen in de winkel (met ophaling)</td>
<td></td>
</tr>
<td><strong>Eén bestelling selecteren—geen gelukkig pad, ophalen op de achtergrond</strong></td>
<td>Items van één of meerdere aantallen selecteren met gedeeltelijke en automatische selectie en curbside oppikken (met ophaling)</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>Geplaatst bestelling - geannuleerd voor kiezen</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Geplaatste bestelling - geannuleerd voor verzending</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Plaatsende orde - onderzoek in orde module</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Plaatsende orde - onderzoek en manuele controle binnen voor overdracht</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Geplaatste bestelling - alle items die niet zijn geselecteerd of niet beschikbaar zijn gemarkeerd door de kiezer</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Volgorde geplaatst met bundelitems - plukken en afleveren</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Opdracht geplaatst - Handje af met afwijzing</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Opdracht geplaatst - Handje af met afwijzing van alle items</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>

## Implementeren

Nadat u hebt geverifieerd dat de oplossing aan uw specificaties is gevormd en getest, bent u bereid om van het opvoeren aan productie op te stellen.

De implementatie en het testen zijn afhankelijk van uw infrastructuur en mogelijkheden.

>[!TIP]
>
>Voor plaatsingsrichtlijnen, checklists, en beste praktijken voor Adobe Commerce op de projecten van de wolkeninfrastructuur, zie [ uw opslag ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/staging-production) in de documentatie van de Ontwikkelaar van Adobe Commerce opstellen.
