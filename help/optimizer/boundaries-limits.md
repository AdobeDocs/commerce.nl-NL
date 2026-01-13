---
title: Grenswaarden en grenzen
description: Begrijp  [!DNL Adobe Commerce Optimizer]  grenzen en grenzen om capaciteit te plannen en prestatieskwesties te verhinderen.
role: Admin, Developer
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: 58d94da9-8d48-4513-8b6a-8e8c7c27a2a5
source-git-commit: f9ac230d448f071e6e8e6368b940f0c415abb02b
workflow-type: tm+mt
source-wordcount: '1350'
ht-degree: 0%

---

# Grenswaarden en grenzen

[!DNL Adobe Commerce Optimizer] heeft twee typen limieten:

- **de grenzen van de Vergunning** - Gebaseerd op uw gekochte capaciteit; kan worden uitgebreid door extra pakketten te kopen.
- **grenzen van het Systeem** - Vaste grenzen die systeemmiddelen beschermen en betrouwbare prestaties voor alle gebruikers verzekeren.

Uw gebruik moet binnen deze grenzen blijven. Als u deze overschrijdt, kan de latentie toenemen en kan de snelheid van de aanvraag toenemen.

## Aanvullende capaciteit aanvragen

De grenzen van de vergunning kunnen worden verhoogd door de vergunningspakketten te kopen die in de [&#x200B; grenzen van de Vergunning en systeemgrenzen &#x200B;](#license-limits-and-system-boundaries) sectie worden beschreven, of door douanevergunning voor unieke gebruiksgevallen te bespreken. Neem contact op met uw Adobe-accountvertegenwoordiger om uw vereisten te bespreken.

Voor vragen over systeemgrenzen, contacteer [&#x200B; de Steun van Adobe &#x200B;](https://experienceleague.adobe.com/home?lang=en#support).

## Prestatieproblemen voorkomen

Volg deze beste praktijken om binnen grenzen te blijven en operationele kwesties te vermijden:

- **herzie uw grenzen** - begrijp uw [&#x200B; capaciteitsgrenzen &#x200B;](#license-limits-and-system-boundaries) alvorens nieuwe storefronts of campagnes te lanceren.
- **spoor uw gebruik** - Gebruik ingebouwde metrieke dashboards of CDN logboeken.

## Licentielimieten en systeemgrenzen

De volgende tabellen geven een overzicht van de licentiegrenzen en systeemgrenzen per capaciteitsgebied en bevatten informatie over het toevoegen van aanvullende licenties om de capaciteit waar van toepassing uit te breiden.

### Omgevingslimieten

| **Milieu** | **Beschrijving** | **Basis toewijzing** | **uitbreidbaar?** |
| --- | --- | --- | --- |
| **het milieu van Sandbox** | Het aantal sandboxomgevingen dat is opgenomen | 2 per instantie | Ja<p>Een extra omgevingslicentie per instantie toevoegen</p> |
| **het milieu van de Productie** | Het aantal productieomgevingen inbegrepen | 1 per instantie | Licentie<p>Een extra omgevingslicentie per instantie toevoegen</p> |

{style="table-layout:auto"}

### Catalogus

| **Capability** | **Beschrijving** | **Basis toewijzing** | **uitbreidbaar?** |
| --- | --- | --- | --- |
| Inname-snelheid van product | Het aantal gemaakte of bijgewerkte producten | 1.000 updates per minuut<p>Maximaal 100.000 updates per dag</p> | Ja<p>Eén licentiepakket toevoegen:</p><ul><li>5.000 updates per minuut <br> een maximum van 500K updates per dag</li> <li>10K updates per minuut <br> A maximum van 1M updates per dag</li></ul><p>De maximale capaciteit voor gegevensinvoer is 1M updates per dag.</p> |
| Grootte van productlading | De maximale hoeveelheid gegevens die is toegestaan bij het maken, bijwerken of invoeren van productinformatie met de API | 200 kB | Nee |
| Catalogusvariaties | Het aantal weergaven van een catalogus dat beschikbaar is voor winkelgebruikers.<p>die als (*Aantal de Kijken van de Catalogus × Aantal Boeken van de Prijs*) worden geteld</p> | 100 variaties | Ja<p>Licentiepakket voor 100 catalogusvariaties toevoegen</p> |
| Producten in één catalogusbron | SKU&#39;s die worden ondersteund in de catalogus | 250.000 SKU&#39;s | Ja<p>SKU-licentiepakket van 100 kbps toevoegen</p> |
| Varianten per product | Het aantal toegestane productvarianten (grootte, kleurcombinaties) per product | 10 K | Nee |
| Catalogusbronnen | Het aantal contexten met catalogusgegevens (bijvoorbeeld landinstellingen of gegevensbronnen zoals PIM en ERP) | 50 | Nee |

{style="table-layout:auto"}

### Prijsboeken

| **Capability** | **Beschrijving** | **Basis toewijzing** | **uitbreidbaar?** |
| --- | --- | --- | --- |
| Prijsboeken | Het aantal toegestane prijzenboeken per geval | Gebaseerd op het aantal [&#x200B; variaties van de Catalogus &#x200B;](#catalog) | Ja <br> de catalogusvariaties van de verhoging |
| Kortingen per prijsnotering | Het aantal kortingen dat op een productprijs binnen één enkel prijzenboek kan worden toegepast | 10 | Nee |

{style="table-layout:auto"}

### Productvisa van AEM Assets

| **Capability** | **Beschrijving** | **Basis toewijzing** | **uitbreidbaar?** |
| --- | --- | --- | --- |
| Productvisuele producten Energiegebruikers | Gebruikersnaam met licentie met volledige mogelijkheden voor beheer van digitale middelen, waaronder AI-tools, Adobe Express/Firefly-integratie en delen van Content Hub, het verwerken van belangrijke DAM-taken en geavanceerde cloud-native functies voor optimale efficiëntie. | 2 | Ja<p>Upgrade uitvoeren naar AEM Assets-licentie</p> |
| Gebruikers van Collaborant voor productvisa | Toegang tot en werk met middelen via de AEM Commerce-integratie, maak en bewerk inhoud met Adobe Express en Firefly en gebruik (indien ingeschakeld) goedgekeurde middelen via de Content Hub-portal. | 2 | Ja<p>Upgrade uitvoeren naar AEM Assets-licentie</p> |
| Opslag van productvisa | Toegewezen opslagruimte voor elementen | 1 TB opslag | Nee |
| Dynamisch mediagebruik | Toegestaan voor dynamische mediaverwerkingsbewerkingen, waaronder:<ul><li>Afbeeldingen leveren</li><li>Slimme afbeeldingen</li><li>Videolevering</li></ul><p>Voor details, zie *Dynamisch gebruik van Media berekenen* hieronder. | Gebaseerd op GMV<p>Minimumtoewijzing: 5 miljoen transacties/maand</p> | Ja<ul><li>Licentie aanschaffen voor extra bewerkingen</li><li>Upgrade uitvoeren naar AEM Assets-licentie</li></ul> |
| Video-levering | Toegestaan voor het afleveren of downloaden van video | 300 video&#39;s, 1 minuut per video | Ja<p>Upgrade uitvoeren naar AEM Assets-licentie</p> |
| Middelen genereren | Toegang tot generatieve AI voor Adobe Express en Adobe Firefly voor het maken van afbeeldingen | Geen | Algemene AI-kredieten afzonderlijk aanschaffen |

{style="table-layout:auto"}


>[!NOTE]
>
>**Gebruikers van de Macht** kunnen tot Adobe Express direct of binnen Adobe Commerce Optimizer toegang hebben. **de Gebruikers van de Medewerker** kunnen tot de toepassing van Adobe Express direct toegang hebben. Het gebruik wordt geregeerd door [&#x200B; Adobe Express met de Specifieke het Vergunningsvoorwaarden van het Product van Firefly &#x200B;](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/PSLT-AdobeExpressWFirefly-WW-2025v1.pdf).


>[!BEGINSHADEBOX  &quot;Bereken Dynamisch gebruik van Media&quot;]

Met Dynamic Media-gebruik worden API-aanvragen bijgehouden die in de componenten Product Visuals in Adobe Commerce Optimizer worden binnengebracht om een van de volgende handelingen mogelijk te maken:

- **de levering van het Beeld verbruikt één dynamische media verrichting** voor elk voorkomen van het volgende:
   - **basisbeeldtransformatie** van een digitaal middel, bijvoorbeeld resize, schaal, formaatomzetting, compressie, of gewassenverrichtingen.
   - **statische beeldlevering of download** van genoemde digitale activa of digitale activavertoning (buiten video)
- **de Slimme levering van het Beeld verbruikt 20 Dynamische Verrichtingen van Media** voor elke geoptimaliseerde levering van één enkel digitaal element door de meest aangewezen beeldvertoning voor het apparaat en browser van een eindgebruiker automatisch te produceren.
- **de Videolevering verbruikt 20 Dynamische Verrichtingen van Media** voor één enkele levering of download van een video, of een getransformeerde variant van een video.

>[!ENDSHADEBOX]


### Weergaven en beleid van catalogi

| **Capability** | **Beschrijving** | **Basis toewijzing** | **uitbreidbaar?** |
| --- | --- | --- | --- |
| Catalogusweergaven | Aantal configureerbare subsets van uw hoofdcatalogus | Gebaseerd op het aantal [&#x200B; variaties van de Catalogus &#x200B;](#catalog) | Ja <br> de catalogusvariaties van de verhoging |
| Beleid per catalogusweergave | Aantal toegestane gegevensfilters | 10 | Nee |
| Kenmerkwaarden in een beleid | Aantal productkenmerken die voor het filtreren kunnen worden gevormd | 100 | Nee |

{style="table-layout:auto"}

### Catalog storefront

De basistoewijzing voor opslagmogelijkheden voor catalogi wordt bepaald op basis van de GMV-laag. De tabel geeft de minimale toewijzing voor elk vermogen aan.

| **Capability** | **Beschrijving** | **Basis toewijzing** | **uitbreidbaar?** |
| --- | --- | --- | --- |
| Ophaalsnelheid van catalogus | Het aantal keren dat een API voor een catalogus per maand wordt aangeroepen door een systeem (winkel, transactiesysteem, ERP of andere) om gegevens uit de catalogus op te halen | Gebaseerd op GMV-laag<p>Minimumtoewijzing: 10 MB/maand</p> | Ja<p>1M-aanvragen per maand licentiepakketten toevoegen</p> |
| Inhoudsaanvragen | Aanvragen bij Commerce Storefront voor HTML-paginaweergaven of JSON API-aanroepen. Wordt geteld als weergave van 1 pagina of 5 API-aanroepen. | Gebaseerd op GMV-laag<p>Minimumtoewijzing: 2 MB/maand</p> | Ja<p>1 M per maandpakket licenties toevoegen</p> |
| Storefront GenAI-variaties | Toegestaan voor het genereren van op tekst gebaseerde inhoud | Gebaseerd op GMV-laag<p>Minimumtoewijzing: 1.000 variaties/maand</p> | Ja<p>Algemene AI-kredieten afzonderlijk aanschaffen</p> |

{style="table-layout:auto"}

>[!NOTE]
>
>Voor het genereren van afbeeldingen is een Adobe Firefly-licentie vereist die is ingericht op dezelfde IMS org als Adobe Commerce Optimizer.


### Productdetectie

| **Capability** | **Beschrijving** | **Basis toewijzing** | **uitbreidbaar?** |
| --- | --- | --- | --- |
| Producten per zoekaanvraag | Het maximumaantal producten dat per pagina wordt geretourneerd in zoekresultaten | 100 | Nee |
| Filterbare kenmerken | Het aantal productkenmerken (zoals kleur, grootte, merk of materiaal) dat kan worden ingeschakeld voor gelaagde navigatie en facetten | 200 | Nee |
| Doorzoekbare kenmerken | Het aantal productkenmerken dat voor gebruik met de de onderzoekdienst van de productcatalogus kan worden gevormd | 200 | Nee |
| Sorteerbare kenmerken | Het aantal productkenmerken dat kan worden geconfigureerd voor het bepalen van de volgorde van waarden voor zoekresultaten | 50 | Nee |
| Zoekpagindiepte | Het maximumaantal producten dat toegankelijk is via paginering (bijvoorbeeld pagina 100 × 100 producten/pagina) | 10 K | Nee |
| Facetten | Het aantal filterbare productkenmerken (zoals merk, kleur, grootte, prijs) die kunnen worden geconfigureerd om kopers te helpen zoekresultaten te verfijnen en door categorieën te bladeren | 100<p>Moet filterbare kenmerken hebben</p> | Nee |
| Opties per facet | Het aantal filterbare productkenmerkwaarden (zoals &quot;Rood&quot;, &quot;Blauw&quot; voor Kleur, &quot;Klein&quot;, &quot;Medium&quot; voor Grootte) die gebruikers in een lijst kunnen selecteren | 100 | Ja<p>Kan worden vergroot via supportverzoek</p> |

{style="table-layout:auto"}

### Aanbevelingen

De volgende mogelijkheden zijn beschikbaar voor productaanbevelingen. Sommige functies die beschikbaar zijn in andere Adobe Commerce-producten, worden niet ondersteund in [!DNL Adobe Commerce Optimizer] .

| **Capability** | **Beschrijving** | **Basis toewijzing** | **uitbreidbaar?** |
| --- | --- | --- | --- |
| Actieve aanbevelingen | Aantal actieve aanbevelingen voor componenten in uw winkel (zoals &quot;Klanten ook bekeken&quot; of &quot;Je kunt het ook leuk vinden&quot;) | 50 | Nee |
| Invoegingen/uitsluitingen voor categorieën of kenmerken | Producten filteren op een specifieke set die in aanmerking komt voor aanbevelingen | Niet ondersteund | |
| Aanbevelingen voor voorvertoning | Een voorvertoning weergeven van de aanbevelingen in de winkel voordat deze worden gepubliceerd | Niet ondersteund | |

{style="table-layout:auto"}

### Uitbreidbaarheid

| **Capability** | **Beschrijving** | **Basis toewijzing** | **uitbreidbaar?** | **Nota&#39;s** |
| --- | --- | --- | --- | --- |
| Adobe Developer App Builder | Capaciteit voor het bouwen van cloud-native extensies en integratie | Gebaseerd op GMV-laag<p>Minimumtoewijzing: 1 verpakking/jaar</p> | Ja<p>Extra pakketten toevoegen</p> | Voor de per verpakking vastgestelde limieten, zie:<ul><li>[&#x200B; App Builder productbeschrijving &#x200B;](https://helpx.adobe.com/legal/product-descriptions/adobe-developer-app-builder.html) voor grenzen die per pak worden bepaald.</li><li>[&#x200B; de Montages en de beperkingen van het Systeem &#x200B;](https://developer.adobe.com/app-builder/docs/guides/runtime_guides/system-settings) in de *Runtime van App Builder Gidsen*.</li><li>[&#x200B; de vereisten van de Opslag van App Builder &#x200B;](https://developer.adobe.com/app-builder/docs/guides/app_builder_guides/storage/)</li></ul> |

{style="table-layout:auto"}

<!--## How to size your solution

Ask your Adobe representative for a list of available packages to determine which most closely matches your project

To accurately size your Adobe Commerce Optimizer solution, follow these steps:

1. Review the available packages, and start with a package that most closely matches your requirements.
1. Review the capabilities and metrics to ensure they align with your business requirements.
1. Purchase add-on packages for any metrics where you require additional capacity.

This approach ensures your solution is accurately sized for your business needs.

### Example use cases

1. **Seasonal Catalog Expansion**

   * Need: +20K SKUs
   * Add-On: 2 × SKU Packs (10K each)

1. **High Traffic Surge**

   * Need: +3M content requests/month
   * Add-On: 3 × content request packs (1M each)

1. **Global Presence**

   * Need: Additional environments for testing
   * Add-On: +1 Production, +2 Sandbox instances

1. **GenAI or Media Needs**

   * Need: +10M dynamic media ops/month
   * Add-On: 10 × dynamic media packs (1M each) -->
