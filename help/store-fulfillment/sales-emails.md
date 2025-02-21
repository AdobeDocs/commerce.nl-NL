---
title: E-mailsjablonen voor verkoop
description: Configureer de transactionele e-mailsjablonen voor de communicatie met klanten en sla beheerders op tijdens het uitvoeringsproces voor ophaalopdrachten van de winkel.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Communications, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 0%

---


# E-mailsjablonen voor verkoop

Store Fulfillment biedt een uitgebreide reeks transactie-e-mailsjablonen aan ter ondersteuning van workflows voor bestellingen en afhandeling. Zij bieden verenigbare, geautomatiseerde mededeling en overseinen over kanalen-het op de hoogte brengen van klant en opslagbeheerders over de veranderingen van de ordestatus, instructies voor in-store bestelorden, en meer aan.

E-mailsjablonen voor afhandeling van opslagruimte worden geconfigureerd met standaardberichten en -instellingen. Merchant beheerders in Adobe Commerce kunnen configuraties beheren en wijzigen, en de e-mailmalplaatjes selecteren om met klanten in verschillende scenario&#39;s te communiceren. Beheerders kunnen sjablonen ook configureren en aanpassen.

Configureer de e-mailsjablonen voor verkoop via de beheerfunctie: **[!UICONTROL Stores > Configuration > Sales > Sales Emails]** .

## E-mails - Algemene instellingen

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
<td><strong>Asynchroon verzenden</strong></td>
<td>Hiermee bepaalt u of e-mails over verkopen asynchroon worden verzonden. Opties: <br/>**'Disable`** - (Standaard) Verkoop-e-mails worden verzonden wanneer deze door een gebeurtenis worden geactiveerd. Gebruik de standaardinstelling voor de snelste communicatie en reactietijd voor Ophalen. <br/>**'Enable`** - Als u deze optie inschakelt, worden processen die het uitchecken van e-mailberichten afhandelen en de verwerking ervan naar de achtergrond verplaatst en worden deze op vooraf bepaalde, regelmatige intervallen verzonden.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
</tbody></table>

## Order Ready for Pickup in Store

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
<td><strong>Ingeschakeld</strong></td>
<td>Dit e-mailbericht wordt naar de klant verzonden wanneer de partner van de winkel het ophalen van de bestelling heeft voltooid. Stel deze optie in op Nee om het e-mailbericht uit te schakelen. Als de e-mailsjabloon is uitgeschakeld, voorkomt dit niet dat een bestelling wordt gekozen door de partner in de winkel.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Order gereed voor afhalen e-mailafzender</strong></td>
<td>De identiteit van de afzender die wordt gebruikt bij het verzenden van het e-mailbericht.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Order gereed voor e-mailsjabloon voor afhalen</strong></td>
<td>De e-mailberichtsjabloon die wordt gebruikt om geregistreerde klanten op de hoogte te brengen. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<td><strong>Order Ready for Pickup Email Template for Guest</strong></td>
<td>De e-mailberichtsjabloon die wordt gebruikt om gastklanten op de hoogte te brengen. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Order Ready for Pickup Email Template for Alternate Pickup Contact</strong></td>
<td>Het e-mailberichtmalplaatje wordt gebruikt om extra contacten mee te delen die in de orde worden genoemd. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Bestelling gereed voor afhalen e-mailkopie naar</strong></td>
<td>Een door komma's gescheiden lijst met e-mailadressen om een kopie van elke melding te verzenden.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Send Order Ready for Pickup Email Copy Method</strong></td>
<td>De methode voor het kopiëren van e-mail (koolstofkopie) voor gebruik.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
</tbody></table>


## De bestelling is opgehaald in de winkel

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
<td><strong>Ingeschakeld</strong></td>
<td>Dit e-mailbericht wordt naar de klant verzonden wanneer deze bevestigt dat deze zijn bestelling heeft opgehaald uit de winkel. Stel deze optie in op Nee om het e-mailbericht uit te schakelen. Als de e-mailsjabloon is uitgeschakeld, voorkomt dit niet dat een bestelling door de klant wordt opgehaald.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>De bestelling is opgehaald door de e-mailafzender</strong></td>
<td>De identiteit van de afzender die wordt gebruikt bij het verzenden van het e-mailbericht.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>De bestelling is opgezocht in e-mailsjabloon</strong></td>
<td>De e-mailberichtsjabloon die wordt gebruikt om geregistreerde klanten op de hoogte te brengen. Er wordt een standaardsjabloon bij de integratie geleverd</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<td><strong>De bestelling is opgezocht in een e-mailsjabloon voor gasten</strong></td>
<td>De e-mailberichtsjabloon die wordt gebruikt om gastklanten op de hoogte te brengen. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Verzenden is opgezocht naar</strong></td>
<td>Een door komma's gescheiden lijst met e-mailadressen om een kopie van elke melding te verzenden.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>De methode Verzenden is uitgezocht voor kopiëren via e-mail</strong></td>
<td>De methode voor het kopiëren van e-mail (koolstofkopie) voor gebruik.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
</tbody></table>

## Bestelling vertraagd

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
<td><strong>Ingeschakeld</strong></td>
<td>Dit e-mailbericht wordt naar de klant verzonden om hen op de hoogte te stellen van een vertraging bij de verwerking of het selecteren van hun bestelling in de winkel. Stel deze optie in op Nee om het e-mailbericht uit te schakelen. Als de e-mailsjabloon is uitgeschakeld, voorkomt deze functie niet dat een bestelling wordt vertraagd.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Vertraagde e-mailafzender bestellen
</strong></td>
<td>De identiteit van de afzender die wordt gebruikt bij het verzenden van het e-mailbericht.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Vertraagde e-mailsjabloon bestellen</strong></td>
<td>De e-mailberichtsjabloon die wordt gebruikt om geregistreerde klanten op de hoogte te brengen. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<td><strong>Vertraagde e-mailsjabloon voor gasten bestellen</strong></td>
<td>De e-mailberichtsjabloon die wordt gebruikt om gastklanten op de hoogte te brengen. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>E-mailkopie voor bestelling met vertraging verzenden naar</strong></td>
<td>Een door komma's gescheiden lijst met e-mailadressen om een kopie van elke melding te verzenden.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Verzendvolgorde vertraagde kopieermethode</strong></td>
<td>De methode voor het kopiëren van e-mail (koolstofkopie) voor gebruik.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
</tbody></table>



## Bestelling geannuleerd

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
<td><strong>Ingeschakeld</strong></td>
<td>Dit e-mailbericht wordt naar de klant verzonden om deze te laten weten dat zijn bestelling in de winkel is geannuleerd. Stel in op <code>No</code> om de e-mailmelding uit te schakelen. Als de e-mailsjabloon is uitgeschakeld, voorkomt deze functie niet dat een bestelling wordt geannuleerd.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Bestelling geannuleerde e-mailafzender
</strong></td>
<td>De identiteit van de afzender die wordt gebruikt bij het verzenden van het e-mailbericht.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>E-mailsjabloon bestellen geannuleerd</strong></td>
<td>De e-mailberichtsjabloon die wordt gebruikt om geregistreerde klanten op de hoogte te brengen. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<td><strong>Bestelling geannuleerd voor gast</strong></td>
<td>De e-mailberichtsjabloon die wordt gebruikt om gastklanten op de hoogte te brengen. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Geannuleerde e-mailkopie van bestelling verzenden naar</strong></td>
<td>Een door komma's gescheiden lijst met e-mailadressen om een kopie van elke melding te verzenden.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Kopieermethode voor bestelling geannuleerd</strong></td>
<td>De methode voor het kopiëren van e-mail (koolstofkopie) voor gebruik.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
</tbody></table>


## Bestelling gedeeltelijk geannuleerd

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
<td><strong>Ingeschakeld</strong></td>
<td>Dit e-mailbericht wordt naar de klant verzonden om deze te laten weten dat een deel van zijn bestelling in de winkel is geannuleerd. Stel in op <code>No</code> om de e-mailmelding uit te schakelen. Als de e-mailsjabloon is uitgeschakeld, kan een bestelling niet gedeeltelijk worden geannuleerd.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Gedeeltelijk geannuleerde e-mailafzender bestellen
</strong></td>
<td>De identiteit van de afzender die wordt gebruikt bij het verzenden van het e-mailbericht.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Gedeeltelijk geannuleerde e-mailsjabloon bestellen</strong></td>
<td>De e-mailberichtsjabloon die wordt gebruikt om geregistreerde klanten op de hoogte te brengen. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<td><strong>Gedeeltelijk geannuleerde e-mailsjabloon bestellen voor alternatief ophaalcontact</strong></td>
<td>Het e-mailberichtmalplaatje wordt gebruikt om extra contacten mee te delen die in de orde worden genoemd. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Bestelling gedeeltelijk geannuleerd voor gast</strong></td>
<td>De e-mailberichtsjabloon die wordt gebruikt om gastklanten op de hoogte te brengen. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Gedeeltelijk geannuleerde e-mailkopie verzenden naar</strong></td>
<td>Een door komma's gescheiden lijst met e-mailadressen om een kopie van elke melding te verzenden.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Gedeeltelijk geannuleerde kopieermethode voor bestelling verzenden</strong></td>
<td>De methode voor het kopiëren van e-mail (koolstofkopie) voor gebruik.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
</tbody></table>

## Verzenden naar winkel

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
<td><strong>De bestelling is verzonden om e-mailafzender van producten op te slaan</strong></td>
<td>De e-mail die naar het opgegeven bedrijfspersoneel is verzonden als een geaggregeerd rapport van alle open bestellingen die pas in een handelswinkel kunnen worden uitgepakt als hun inventaris beschikbaar is. </br></br> Handelaars kunnen dit rapport gebruiken om voorraadoverdrachten of aanvulling te initiëren en te beheren. </br></br> Dit bericht is slechts van toepassing wanneer de [!DNL Ship-to-Store] eigenschappen worden toegelaten.
</br></br> Dit etiket beïnvloedt niet de geselecteerde verschepende drager of hun beschikbare het verschepen methodeetiketten.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>Verzenden om e-mailontvangers op te slaan</strong></td>
<td>Een door komma's gescheiden lijst met e-mailadressen om een kopie van elke melding te verzenden.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>E-mailsjabloon</strong></td>
<td>De sjabloon voor e-mailberichten die wordt gebruikt om ontvangers op de hoogte te stellen. De integratie bevat een standaardsjabloon.</td>
<td>Winkelweergave</td>
<td>Nee</td>
</tr>
</tbody></table>

>[!NOTE]
>
>Als u backorders toestaat, moet u een beheerder e-mailadres verstrekken om berichten over deze orden te ontvangen. Voeg het adres aan de volgende configuratiemontages toe: **[!UICONTROL Send Order Delayed Email Copy To]** in het [ malplaatje van de Vertraging van de Orde ](#order-delayed), en [!UICONTROL Ship To Store Email Recipients] in het [ Schip om ](#ship-to-store) malplaatje op te slaan.



