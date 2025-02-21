---
title: App-instelling
description: Opstelling de  [!DNL Store Assist]  app om de werkschema's en processen van de archiefvervulling van begin tot eind te beheren voor het online kopen, neem in opslagorden op.
level: Intermediate
role: Admin
feature: Shipping/Delivery, Configuration, Tools and External Services
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---

# Setup van app

Store Assist is een FaaS-platform (fulfillment-as-a-service) dat wordt aangedreven door Walmart Commerce Technologies. De app biedt in-store uitvoeringsmogelijkheden voor het verwerken van [!DNL buy online, pick up in store] (BOPIS)-orders. Met de Hulp van de Opslag, kunnen de opslagvennoten zien welke punten klanten bestelde, de correcte punten sneller plukken, en opstelling vervulde orden voor de ophaallevering in-store of curbside aan klanten.

De app Store Assist ontvangt alle bestelling- en klantgegevens, van bestellingsgegevens tot ophaaltijden en stelt de gegevens beschikbaar voor het online opslaan van partners via mobiele apparaten. De app bevat [!UICONTROL Pick] -, [!UICONTROL Stage] -, [!UICONTROL Handoff] - en [!UICONTROL Orders] -modules om Winkelkoppelingen te helpen bij het uitvoeren van bijvoorbeeld de volgende uitvoeringsactiviteiten:

- Wijs leveringsdatums en -tijden voor bestellingen toe.
- Ontvang meldingen van klanten wanneer ze aankomen voor het ophalen van bestellingen.
- Werkgebiedbestellingen voor overdracht aan klanten.
- De orderstatus van het spoor voor alle orden in hun toegewezen opslagplaatsen.

>[!NOTE]
>
>Leer meer over de Hulp app van de Opslag door het [ bijstaan van de Opslag werkschema&#39;s van de vervulling ](store-assist-modules.md) onderwerp te herzien.

## De app Store Assist configureren

Voor de app Store Assist zijn twee soorten configuraties vereist:

- Adobe Commerce Admin systeemmontages om [ gebruikersrekeningen, gebruikersrollen, middeltoestemmingen ](user-setup.md) te beheren, en [ de auto maakt en modelselecties beschikbaar aan klanten tijdens het controle-in proces ](check-in-experience-setup.md).

- De configuratie-instellingen aan de voorzijde om de interface van de app Store Assist en andere instellingen aan te passen, zoals:

   - **merk de Winkel bijstaat app** - pas het toepassingsgebruikersinterface met uw bedrijfsembleem en kleuren aan.

   - **werk de standaardinstructies** bij - pas de instructies in de Slag bij Keuze, het Stadium, Handoff, en de modules van de Orde aan om de Vennoten van de Opslag door elke stap van het uitvoeringswerkschema voor uw bedrijf te begeleiden.

   - **Localization** - selecteer de beschikbare taal voor app. Kies de datum- en tijdnotatie en selecteer de standaardmaateenheden en de standaardvaluta.

   - **tijd van de Inactiviteit** - specificeer de hoeveelheid tijd dat app inactief moet zijn alvorens het zich uitlogt.

   - **Annulering van de opslag** - specificeer of de orden van de opslag kunnen worden geannuleerd en welke rollen annuleringstoestemmingen hebben

   - **Opschoonvenster van de Orde** - specificeer hoe lang voorbij de [ Geschatte Tijd van het Lood van de Bestelwagen ](enable-general.md#delivery-method-title-configuration) dat een geplakte orde in het opvoeren alvorens wordt herbevolkt-voor voorbeeld, drie dagen blijft. De standaardwaarde is zeven dagen. Als deze configuratie is ingeschakeld, wordt de volgorde automatisch geannuleerd wanneer deze tijd verloopt. De items worden opnieuw opgeslagen en de verkoper ontvangt een annuleringsbericht.

   - Alles aanpassen in app-instructies (kiezen, opvoeren, afleveren).

   - **het Schrappen berichten** - specificeer of om een duw bericht te verzenden om het plukken proces te beginnen nadat een klant een orde plaatst.

   - **Controle in berichten** - specificeer of om een duw bericht tijdens het controle proces voor orde te verzenden - na controle-binnen, nadat de klant tijd wacht een gespecificeerde tijdspanne overschrijdt. Of schakel de melding uit.

   - **Handje van proces** - laat facultatieve processen toe wanneer de Geassocieerde Opslag orde aan klant levert, bijvoorbeeld een klantenhandtekening vereist of de vennoot ertoe aanzet om klantenidentiteitskaart te controleren.

   - **laat puntafstoting op aflevering** toe - sta klanten toe om orde punten tijdens ordeafhandeling terug te keren of te annuleren.

  Werk met het Walmart team van de Diensten van de Cliënt van de Technologieën van Commerce om frontend configuratie voor de Hulp App van de Winkel te voltooien.

## Downloaden en installeren van apps

Nadat de app Store Assist is ingesteld en geconfigureerd, kunnen Store Associates vanaf hun mobiele apparaten de app Store Assist downloaden, installeren en aanmelden bij de app Store Assist.

- Verifieer dat het mobiele apparaat aan de [ hardware en softwarevereisten ](solution-requirements.md#store-assist-app-requirements) voor de oplossing van de Afhandeling van de Opslag voldoet.

- Download de Opslag bijstaat app van [ Apple App Store ](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539) {target="_blank"} of de [ opslag van Google Play ](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist) {target="_blank"}.

- Voor het aanmelden bij Store Associates is de volgende informatie vereist:

   - **[!UICONTROL Company name]** die is gekoppeld aan het account Winkelassistentie

   - **- gebruikersbenaming en wachtwoordgeloofsbrieven voor hun rekening van de Bewaarplaats van 0} bijstaat.**

  Een beheerder van Adobe Commerce kan [!DNL Store Assist app] gebruikersrekeningen voor alle opslagplaatsen tot stand brengen en beheren die [ In-Store Bestelwagen ](merchant-store-configuration.md#pickup-location-configuration) hebben die in de montages van de Bewaarplaatsen wordt toegelaten Admin.
