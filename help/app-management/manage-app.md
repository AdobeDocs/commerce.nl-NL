---
title: Uw app beheren
description: Koppel, configureer en koppel App Builder-toepassingen aan uw Commerce-instantie.
feature: App Builder, Extensibility, Integration
source-git-commit: 780cef7af3574cd846fd7ee82d7814f2ebe9d6cc
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---


# Uw app beheren

Een App Manager koppelt een App Builder-toepassing aan hun Commerce-instantie. Configuratieformulieren worden dynamisch gerenderd op basis van het schema van de app. Er is dus geen aangepaste ontwikkeling van de interface voor Admin vereist. App Manager configureert instellingen via formulieren die automatisch door Commerce worden gegenereerd.

![ App beheer ](assets/app-management-view.png){width="500" zoomable="yes"}

## Een toepassing zoeken in Admin

Onder **[!UICONTROL Apps]** > **[!UICONTROL App Management]** wordt elke toepassing weergegeven als een kaart. De lijst kan elke toepassing bevatten die is gekoppeld aan het Adobe Commerce-exemplaar voor de geselecteerde Adobe IMS-organisatie. Gebruik de besturingselementen boven de kaarten om de resultaten te beperken:

| Besturing | Beschrijving |
| --- | --- |
| **Filter door app..** | Zoeken op toepassingsnaam. |
| **Status** | Kaarten beperken tot levenscyclusstatus. **Alle Statussen** toont elke app; andere waarden omvatten **Geassocieerde**, **Geïnstalleerde**, **Gedeeltelijk Geïnstalleerde**, en **Niet geassocieerd**. De status op elke kaart komt overeen met de gekleurde indicator in de lijst. |
| **de patronen van de Rekbaarheid** | Beperk kaarten met de mogelijkheden die de app gebruikt. **Alle Patronen van de Uitbreidbaarheid** toont elke app; andere waarden richten zich op de badges op elke kaart, zoals **BedrijfsConfiguratie**, **Admin UI SDK**, **Webhooks**, en **Gebeurtenissen**. |

De tekst van het onderzoek en beide dropdowns zijn samen van toepassing (logische EN). Om de volledige lijst opnieuw te tonen, plaats **Status** en **de patronen van de Rekbaarheid** terug naar hun **allen..** opties, en ontruim het onderzoeksgebied.

## App ophalen

**[!UICONTROL Acquire App]** opent een nieuw browser lusje (of een afzonderlijke browser mening) aan [ Adobe Exchange ](https://exchange.adobe.com/experiencecloud){target="_blank"}, waar u Commerce-Verwante marktplaatslijsten kunt ontdekken en toepassingen aan uw organisatie van Adobe IMS kunt toevoegen. Zodra app wordt verworven, goedgekeurd, en opgesteld, verschijnt app in [!DNL App Management] voor [ vereniging en installatie ](#associate-an-app).

## Vereisten

Controleer voordat u een app gaat koppelen het volgende:

| Vereiste | Beschrijving |
|-------------|-------------|
| **toegang Admin** | Commerce Admin met [!DNL App Management] -machtigingen |
| **Gedistribueerde app** | App Builder-toepassing geïmplementeerd op uw organisatie en klaar voor verbinding |
| **Toegang van de Organisatie** | Toegang tot de Adobe-organisatie waar de app wordt geïmplementeerd |

## Zelfstudie

Bekijk deze video om te leren hoe u een toepassing aan een Commerce-instantie kunt koppelen en instellingen kunt configureren.

>[!VIDEO](https://video.tv.adobe.com/v/3478944)

## Een app koppelen

Tijdens het associatieproces worden websites geïmporteerd, opgeslagen en opgeslagen weergaven vanuit Commerce en wordt de koppeling gemaakt tussen de app en uw Commerce-exemplaar.

Een App Builder-toepassing koppelen aan een Commerce-instantie:

1. Navigeer naar **[!UICONTROL Apps]** > **[!UICONTROL App Management]** .

1. Klik op **[!UICONTROL Associate App]** .

   ![ Associate app ](assets/associate-app.png){width="500" zoomable="yes"}

1. Selecteer een **[!UICONTROL Project]** in de lijst.

1. Selecteer de **[!UICONTROL Workspace]** .

1. Klik op **[!UICONTROL Associate]** .

   ![ details van de Toepassing ](assets/app-details.png){width="500" zoomable="yes"}

>[!WARNING]
>
>Als bereiksynchronisatie mislukt, wordt de koppeling nog steeds voltooid. U kunt het bereik later handmatig synchroniseren vanuit de **[!UICONTROL Manage Scopes]** -weergave in de configuratie van de bijbehorende app.

## Instellingen configureren

Nadat u een toepassing in de weergave [!DNL App Management] hebt gekoppeld, configureert u de instellingen via het formulier:

1. Klik op **[!UICONTROL Configure]** in de bijbehorende app.

1. In het formulier worden de configureerbare instellingen van de app weergegeven.

1. Wijzig de waarden naar wens.

1. Klik op **[!UICONTROL Save]** .

### Toepassingsspecifieke configuratie

Gebruik een bereikspecifieke configuratie wanneer verschillende websites, winkels of winkelweergaven unieke instellingen nodig hebben. Schakel bijvoorbeeld een functie alleen in voor een bepaald gebied of een bepaalde winkelweergave, of gebruik verschillende instellingen per merk. Instellingen in een lager bereik overschrijven de instellingen van een hoger bereik.

Algemene waarden op een specifiek bereikniveau overschrijven:

1. Klik op **[!UICONTROL Change Scope]** .

1. Selecteer een bereik in de lijst.

1. Wijzig waarden voor dit bereik.

1. Klik op **[!UICONTROL Save]** .

## Bereik beheren

Open **[!UICONTROL Manage Scopes]** vanuit het scherm met toepassingsdetails om de bereikhiërarchie voor uw app te beheren.

![ beheer werkingsgebied ](assets/manage-scopes.png){width="500" zoomable="yes"}

| Actie | Beschrijving |
|--------|-------------|
| **[!UICONTROL Add root scope]** | Voeg een bereik toe dat alleen van toepassing is op de app. |
| **[!UICONTROL Sync Commerce scopes]** | Vernieuw de lijst met websites, winkels en winkelweergaven van Commerce nadat u deze hebt toegevoegd of gewijzigd. |
| **[!UICONTROL Import scopes]** | Het bereik van de invoer in bulk van een dossier. |

## Koppeling van een app opheffen

Koppel een app los wanneer u deze niet meer nodig hebt om verbinding te maken met uw Commerce-exemplaar. U moet bijvoorbeeld een integratie uitschakelen, overschakelen naar een andere werkruimte of testconfiguraties opschonen.

>[!WARNING]
>
> Als u de koppeling ongedaan maakt, worden alle configuratiewaarden voor deze instantie verwijderd. Dit kan niet ongedaan worden gemaakt.

Een app verwijderen uit een Commerce-instantie:

1. Navigeer naar **[!UICONTROL Apps]** > **[!UICONTROL App Management]** .

1. Klik op **[!UICONTROL Unassociate]** in de app.

1. Bevestig de handeling.

## Gerelateerde documentatie

* [ het Oplossen van problemen  [!DNL App Management]](troubleshooting.md) - los gemeenschappelijke kwesties met toepassingsvereniging en configuratie op.
