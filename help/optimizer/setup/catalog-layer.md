---
title: Cataloguslaag
description: Leer hoe u met cataloguslagen productgegevens kunt wijzigen zonder de oorspronkelijke brongegevens te wijzigen, zodat u wijzigingen op elk gewenst moment veilig kunt aanpassen en herstellen.
role: Admin, Developer
recommendations: noCatalog
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 4a904527af172a5e35b87410135d55484d07ad84
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# Cataloguslaag

Met cataloguslagen kunt u productgegevens wijzigen zonder de oorspronkelijke brongegevens te wijzigen. Lagen passen wijzigingen toe op specifieke productkenmerken, zoals naam, beschrijving, afbeeldingen, koppelingen en metagegevens, door een laag boven op de basiscatalogus te maken. Uw oorspronkelijke productgegevens blijven intact, zodat u producten veilig kunt aanpassen en wijzigingen op elk gewenst moment kunt herstellen.

![&#x200B; Lagen van de Catalogus &#x200B;](../assets/catalog-layers.png)

## De werking van cataloguslagen

Wanneer een klant de winkelvoorgrond weergeeft, combineert het systeem de basiscatalogusgegevens met actieve cataloguslagen om de uiteindelijke productinformatie weer te geven. Hieronder wordt beschreven hoe het proces werkt:

1. **toepassing van de Laag** - wanneer een verzoek met een kanaalidentiteitskaart en milieu identiteitskaart wordt gemaakt, wint de opslagdienst de relevante catalogusmening terug.

1. **Gegevens die** samenvoegen-het systeem past cataloguslagen op productgegevens toe die op laag prioritaire orde worden gebaseerd.

1. **gebied behandeling** - de Verschillende gebiedstypes worden verwerkt verschillend:

   - **treedt gebieden** met voeten - de gebieden van de Tekst zoals naam, beschrijving, en metatitels worden vervangen met de waarden die in de laag worden bepaald, met de hoog-prioritaire laag die belangrijkheid neemt.
   - **de gebieden van de Fusie** - de gebieden van de Serie zoals beelden, verbindingen, en attributen worden gecombineerd van veelvoudige lagen, die een verenigde reactie verstrekken.

1. **Prioritaire resolutie** - het ordegebied bepaalt welke laag belangrijkheid neemt. Wanneer meerdere lagen hetzelfde veld wijzigen, heeft de laag met het lagere volgordenummer een hogere prioriteit (bijvoorbeeld, is volgorde 1 het hoogst).

## Gebruiksscenario&#39;s voor cataloguslagen

Cataloguslagen worden doorgaans gebruikt voor:

- **optimalisering SEO** - de titels en beschrijvingen van productmeta van de met voeten treden die op AI aanbevelingen van [&#x200B; Sites Optimizer &#x200B;](../manage-results/opportunities.md) worden gebaseerd.
- **seizoenscampagnes** - werk tijdelijk productnamen, beschrijvingen, of beelden voor bevorderingen bij zonder brongegevens te veranderen.
- **Regionale aanpassing** - de verschillende productinformatie van de vertoning die op geografische plaats of taal wordt gebaseerd.
- **A/B het testen** - test verschillende productpresentaties om omzettingspercentages te optimaliseren.
- **beheer van meerdere merken** - pas productattributen voor verschillende meningen van de merkcatalogus aan.

## Een cataloguslaag toevoegen via gegevensinvoer

U kunt cataloguslagen toevoegen aan uw producten tijdens het invoeren van gegevens. Deze methode is ideaal voor bulkbewerkingen of geautomatiseerde workflows.

>[!NOTE]
>
>U voert cataloguslagen in gebruikend de opname API, maar [&#x200B; plaatsend de orde &#x200B;](#manage-layer-priorities) van de lagen wordt gedaan gebruikend UI.

**Eerste vereisten:**

- API-referenties met toestemming om toegang te krijgen tot de service voor gegevensinvoer
- Product-SKU&#39;s die al in uw basiscatalogus staan

**Stappen:**

1. Bereid uw laaggegevens in het vereiste formaat met de productkenmerken voor u wilt wijzigen.

1. Gebruik het API-eindpunt van de productlagen om de laaggegevens in te voeren.

1. Controleer of de laag is opgenomen door de configuratie van de catalogusweergave te controleren.

Voor gedetailleerde API specificaties en ladingsvoorbeelden, zie {de Lagen van het 0} Product [&#x200B; in de ontwikkelaarsdocumentatie.](https://developer.adobe.com/commerce/services/reference/rest/#tag/Product-Layers)

## Handmatig een cataloguslaag toevoegen in de gebruikersinterface

>[!NOTE]
>
>Deze functie is nog niet beschikbaar.

In de interface van de catalogusweergave kunt u handmatig lagen maken en beheren. Dit is vooral handig voor integratie zoals Sites Optimizer die aanbevelingen voor AI-toepassingen genereert.

>[!NOTE]
>
>Als een Sites Optimizer-laag niet bestaat in de catalogusweergave, maakt de functie voor automatische correctie in Sites Optimizer automatisch een laag en wordt hieraan de volgorde 1 toegewezen (hoogste prioriteit). Als u deze laag verwijdert, wordt deze de volgende keer dat de functie voor automatisch corrigeren in Sites Optimizer wordt uitgevoerd, opnieuw gemaakt en worden bestaande lagen omgezet in lagere volgordenummers. Als de Sites Optimizer-laag al een ander volgnummer heeft, wijzigt de functie voor automatische correctie de prioriteit niet.

>[!TIP]
>
>Voor bulklaagverrichtingen, gebruik de gegeven die API methode [&#x200B; hierboven wordt beschreven &#x200B;](#add-a-catalog-layer-via-data-ingestion).

**om een handlaag te creëren:**

1. Navigeer aan **opstelling van de Opslag** > **meningen van de Catalogus**.

1. Selecteer de catalogusweergave waarop u de laag wilt toepassen.

1. In de sectie van cataloguslagen, klik **toevoegen cataloguslaag**.

1. Configureer de laageigenschappen:

   - **naam van de Laag** - ga een beschrijvende naam in om het laagdoel te identificeren.
   - **Producten** - selecteer de producten waarop deze laag van toepassing is.
   - **Attributen** - kies welke productkenmerken (naam, beschrijving, beelden, metatags, etc.) te wijzigen.
   - **Waarden** - ga de nieuwe waarden voor elk geselecteerd attribuut in.

1. Klik **sparen** om de laag tot stand te brengen.

De nieuwe laag wordt toegevoegd aan de catalogusweergave en krijgt automatisch het volgende beschikbare ordernummer toegewezen.

## Laageffecten voorvertonen

>[!NOTE]
>
>Deze functie is nog niet beschikbaar.

Voordat u lagen activeert of prioriteiten wijzigt, kunt u een voorvertoning weergeven van de invloed die deze hebben op de productgegevens.

**aan voorproeflaagveranderingen:**

1. Navigeer aan **opstelling van de Opslag** > **meningen van de Catalogus**.

1. Selecteer de catalogusweergave met de lagen waarvan u een voorvertoning wilt weergeven.

1. Selecteer in de sectie Cataloguslagen een specifiek product of gebruik de voorvertoningsfunctie.

1. Bekijk de gecombineerde productgegevens die laten zien hoe lagen de waarden van de basiscatalogus wijzigen.

1. Breng desgewenst aanpassingen aan in de laaginhoud of de prioriteitsvolgorde.

## Lagen activeren, deactiveren of verwijderen

U kunt cataloguslagen in- of uitschakelen zonder deze te verwijderen, zodat u kunt bepalen wanneer specifieke aanpassingen worden toegepast.

**om een laag te activeren of te desactiveren:**

1. Navigeer aan **opstelling van de Opslag** > **meningen van de Catalogus**.

1. Selecteer de catalogusweergave die de laag bevat.

1. Zoek in de sectie Cataloguslagen de laag die u wilt schakelen.

1. Klik op de activeringsschakeloptie om de laag in of uit te schakelen.

   - **Actief** - de laag wordt toegepast op productgegevens.
   - **Inactief** - de laag wordt bewaard maar niet toegepast op productgegevens.

1. De wijziging wordt onmiddellijk van kracht op uw winkelcentrum.

**om een laag te schrappen:**

Gebruik de gegeven opname API om [&#x200B; een cataloguslaag &#x200B;](https://developer.adobe.com/commerce/services/reference/rest/#operation/deleteProductLayers) te schrappen.

## Laagprioriteiten beheren

De volgorde waarin lagen worden toegepast, bepaalt welke waarden in de winkel worden weergegeven wanneer meerdere lagen hetzelfde productkenmerk wijzigen. De beheerprioriteiten zorgen ervoor dat de juiste gegevens worden weergegeven.

**Begrijpend prioritaire orde:**

- Aan elke laag wordt een volgnummer toegewezen (1, 2, 3, enzovoort)
- Order 1 heeft de hoogste prioriteit en negeert alle andere lagen
- Wanneer meerdere lagen hetzelfde veld wijzigen, heeft de laag met het lagere volgordenummer voorrang
- Prioriteit is alleen van toepassing op overschrijvende velden (naam, beschrijving, metatags)
- In velden samenvoegen (afbeeldingen, koppelingen, kenmerken) worden gegevens uit alle lagen gecombineerd

**om laagprioriteiten opnieuw te rangschikken:**

1. Navigeer aan **opstelling van de Opslag** > **meningen van de Catalogus**.

1. Selecteer de catalogusweergave met de lagen die u opnieuw wilt rangschikken.

1. Zoek in de sectie Cataloguslagen de laag die u wilt verplaatsen.

1. Sleep de laag om de positie te wijzigen of gebruik de besturingselementen voor herschikken.

1. Het systeem werkt automatisch volgordenummers bij op basis van de nieuwe reeks.

1. Klik **sparen** om de nieuwe prioritaire orde toe te passen.

>[!IMPORTANT]
>
>De veranderingen in laagprioriteit worden onmiddellijk van kracht en kunnen beïnvloeden wat de klanten op uw winkel zien. Herzie de voorproef alvorens op te slaan om ervoor te zorgen de correcte waarden worden toegepast (**voorproef is nog niet beschikbaar**).

## Aanbevolen procedures

Volg de onderstaande aanbevelingen wanneer u werkt met cataloguslagen:

- **beschrijvende namen van het Gebruik** - de lagen van de Naam duidelijk om op hun doel (bijvoorbeeld, &quot;Campagne van de Vakantie 2025&quot;of &quot;Optimalisering SEO - de Pagina&#39;s van het Product&quot;te wijzen.

- **Beperk lagen** - terwijl het systeem veelvoudige lagen steunt, die teveel gebruiken kan prestaties beïnvloeden. Voeg lagen waar mogelijk samen.

<!--- **Test before activating**—Always preview layer effects before activating them on your live storefront. !!!REMOVE IF PREVIEW NOT AVAILABLE FOR GA!!!-->

- **prioritaire logica van het Document** - houd spoor waarvan de lagen belangrijkheid zouden moeten nemen om onbedoelde met voeten treden te vermijden.

- **de lagen van Sites Optimizer van het Overzicht** - wanneer het gebruiken van auto-moeilijke situatie van Sites Optimizer, leidt het systeem tot lagen bij de hoogste prioriteit. Let goed op wanneer u handmatige lagen toevoegt die de AI-aanbevelingen kunnen overschrijven. Leer meer over het gebruiken van [&#x200B; Sites Optimizer &#x200B;](../manage-results/opportunities.md).

- **prestaties van de Monitor** - als u langzaam productpagina laadt opmerkt, herzie uw laagconfiguratie en denk na consoliderend lagen.

## Meer als dit

- [&#x200B; de meningen van de Catalogus &#x200B;](catalog-view.md) - vorm catalogusmeningen voor verschillende storefronts
- [&#x200B; Kansen &#x200B;](../manage-results/opportunities.md) - Leer over AI-aangedreven optimalisering gebruikend cataloguslagen
