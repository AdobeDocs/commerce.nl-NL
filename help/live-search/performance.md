---
title: Prestaties
description: De  [!DNL Live Search]  werkruimte van Prestaties verstrekt insight in de onderzoekstermijnen die de kopers gebruiken.
exl-id: 07a63df8-b981-4913-841a-7e81ec634281
source-git-commit: 5978a400d985e3099962af8bcefdd6f29f687d67
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# Prestaties

De *werkruimte van Prestaties* verstrekt insight in de onderzoekstermijnen die de kopers gebruiken. De informatie kan worden gebruikt om tendensen te identificeren, klik-door te verhogen, en de omzettingspercentage te verbeteren. De werkruimte van Prestaties verstrekt een momentopname van onderzoeksmetriek voor een specifieke datumwaaier en omvat de volgende rapporten:

* Unieke zoekopdrachten
* Resultaten nul
* Populaire resultaten

![&#x200B; Prestaties &#x200B;](assets/performance-unique-searches.png)

U kunt ook naar het [&#x200B; dashboard van het Beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-sync/data-dashboard.html?lang=nl-NL) voor meer gegevens over gegevens het synchroniseren verwijzen.

>[!NOTE]
>
>De werkruimte voor prestaties wordt elke 12 uur bijgewerkt.

## Een rapport weergeven

1. Om de **waaier van de Datum** in te gaan, klik de kalender (![&#x200B; Kalender &#x200B;](assets/btn-calendar.png)) en doe één van het volgende:

   * Als u één datum wilt opgeven, dubbelklikt u op de datum in de kalender.
   * Als u een datumbereik wilt opgeven, klikt u op de eerste en laatste datum in de kalender.

>[!NOTE]
>
>Het datumbereik mag niet langer zijn dan één jaar.

## Veldomschrijvingen

| Opnamegegevens | Beschrijving | Berekeningsvoorbeeld |
|--- |--- |--- |
| Unieke zoekopdrachten | Het totale aantal unieke zoekopdrachten voor het opgegeven datumbereik. De veelvoudige onderzoeken door de zelfde verkoopster, zelfs als voor de zelfde vraag, worden beschouwd als uniek als voorgelegd meer dan één uur uit elkaar. | **Voorbeeld:**<br /> Zoekt:<br /> - &quot;broek&quot;bij 10 :00 AM <br /> - &quot;broek&quot;bij 10 :30 AM (binnen 1 uur → niet uniek) <br /> - &quot;broek&quot;bij 12 :00 PM (na 1 uur → uniek) <br /> - &quot;shirt&quot;bij 1 :00 PM <br /><br />**unieke onderzoeken = 3** |
| Doorklikfrequentie | Het percentage zoekopdrachten dat wordt afgesloten met het klikken op een product door de verkoper. De doorklikfrequentie is bijvoorbeeld 50% als de winkel op &quot;broek&quot; en &quot;shirt&quot; zoekt en vervolgens op één resultaat klikt in de &quot;shirt&quot;-zoekopdracht. | **Formule:**<br /> klik-door tarief = Zoekopdrachten met ≥ 1 klik:Totaal uniek onderzoek <br /><br />**Voorbeeld:**<br /> Totaal unieke onderzoeken = 4 <br /> Zoekopdrachten met minstens één klik = 2 <br /><br /> CTR = 2:4 = **50%** |
| Omrekeningskoers | Het percentage producten de winkelaankopen tegenover het aantal producten de verkoopster voor de gespecificeerde datumwaaier klikt. De conversiesnelheid van de interactie is bijvoorbeeld 100% als de klant zes producten in de popover weergeeft, op een product klikt en een aankoop doet. <br /><br /> de omzettingssnelheid wordt niet beïnvloed door het aantal meningen van een bepaald product. De omrekeningskoers blijft bijvoorbeeld hetzelfde als de gebruiker van de zoekopdracht op een product klikt. | **Formule:**<br /> het tarief van de Omzetting = Totale gekochte producten:Totaal geklikte producten <br /><br />**Voorbeeld 1:**<br /> Geklikte Producten = 5 <br /> Gekochte Producten = 2 <br /><br /> CVR = 2:5 = **40%**<br /><br />**Voorbeeld 2 (5-uursamenvoeging):**<br /> klikt op uur: 4, 5, 6, 10, 2 <br /> Aankopen door uur: 1, 3, 0, 4, 1 <br /><br /> Totale kliks = 4 + 5 + 6 + 10 + 2 = 27 <br /> Totale aankopen = 1 + 3 + 0 + 4 + 1 = 9 <br /><br /> CVR = 9:27 = **33.33%** |
| Resultaatsnelheid nul | Het percentage unieke zoekopdrachten dat geen resultaten retourneert voor het opgegeven datumbereik. De nulresultatenfrequentie is bijvoorbeeld 66,67% als de winkel tweemaal zoekt naar &quot;fjjajfjfjf&quot; (zonder resultaten) en naar &quot;broek&quot; (met resultaten). | **Formule:**<br /> Nul resultaattarief = Unieke onderzoeken met nul resultaten:Totaal uniek onderzoek <br /><br />**Voorbeeld:**<br /> Totaal unieke onderzoeken = 3 <br /> Zoekopdrachten met nul resultaten = 2 <br /><br /> Nul resultaattarief = 2:3 = **66.67%** |
| Gem. klikpositie | De relatieve positie van de gemiddelde doorkliksnelheid op basis van unieke zoekopdrachten voor het opgegeven datumbereik. | **Formule:**<br /> Gemiddelde klik positie = Som van klikposities:Totaal kliks <br /><br />**Voorbeeld:**<br /> klikt op posities: 1, 3, 2 <br /><br /> Gemiddelde klikpositie = (1 + 3 + 2)  **2** |

| Rapporten | Beschrijving |
|--- |--- |
| Unieke zoekopdrachten | Hiermee geeft u de unieke zoekquery&#39;s weer die worden gebruikt tijdens het opgegeven datumbereik. De rapportgegevens worden op dezelfde manier berekend als de unieke gegevens van de onderzoeksmomentopname. Als een verkoper de zelfde onderzoeksvraag tweemaal, maar meer dan een uur uit elkaar typt, wordt het onderzoek beschouwd als twee unieke onderzoeken. <br />**grens van het Rapport:** Hoogste 500 termijnen wanneer het produceren van het Csv- dossier. |
| Resultaten nul | Maakt een lijst van de onderzoeksvragen die geen resultaten en het aantal tijden terugkeren die tijdens de gespecificeerde datumwaaier worden gebruikt. <br />**grens van het Rapport:** Hoogste 500 termijnen wanneer het produceren van het Csv- dossier. |
| Populaire resultaten | Maakt een lijst van de namen van producten die de meeste meningen tijdens de gespecificeerde datumwaaier ontvingen. De populaire resultaten worden berekend gebaseerd op beelden slechts en worden niet beïnvloed door het aantal geklikte of opbrengst. <br />**grens van het Rapport:** Hoogste 500 termijnen wanneer het produceren van het Csv- dossier. |
