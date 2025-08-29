---
source-git-commit: 39977196f322cac571ecdb0219f006970aff3575
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 5%

---
# Technische documentatie van Adobe Commerce

We verwelkomen de bijdragen van de gemeenschap en van Adobe-medewerkers van buiten de documentatieteams.

## Adobe Open Source-gedragscode

Dit project heeft de [Adobe-gedragscode voor open source](code-of-conduct.md) of de [.NET Foundation-gedragscode](https://dotnetfoundation.org/code-of-conduct) overgenomen. Zie het artikel [Bijdragen](contributing.md) voor meer informatie.

## Over je bijdragen aan Adobe-inhoud

Zie de [ Gids van de Medewerker van de Docent van Adobe ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Hoe u een bijdrage levert, hangt af van wie u bent en van het soort veranderingen dat u wilt bijdragen:

### Kleine wijzigingen

Als u minder belangrijke updates bijdraagt, bezoek het artikel en klik het terugkoppelen gebied dat bij de bodem van het artikel verschijnt, klik **Gedetailleerde terugkoppelt opties**, en klik dan **Voorstellen en** uitgeven om naar het prijsonderdrukkingsbrondossier op GitHub te gaan. Gebruik GitHub UI om uw updates te maken. Zie de algemene [ de contributorgids van Adobe Docs ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) voor meer informatie.

Kleine correcties of verduidelijkingen die u ter documentatie en codevoorbeelden in dit antwoord aanbrengt, worden behandeld in de gebruiksvoorwaarden van Adobe.

### Belangrijke wijzigingen of nieuwe artikelen van leden van de gemeenschap

Als u deel uitmaakt van de Adobe-community en u een nieuw artikel wilt maken of belangrijke wijzigingen wilt indienen, gebruikt u het tabblad Problemen in de Git-opslagplaats om een uitgave in te dienen die een gesprek met het documentatieteam kan starten. Zodra u met een plan hebt ingestemd, zult u met een werknemer moeten werken helpen die nieuwe inhoud door een combinatie van het werk in de openbare en privé bewaarplaatsen brengen.

### Belangrijke wijzigingen van werknemers van Adobe

Als u een technisch schrijver, programmamanager, of ontwikkelaar van het productteam voor een oplossing van Adobe Experience Cloud bent en het uw baan is om aan of auteur technische artikelen bij te dragen, zou u de privé bewaarplaats bij `https://git.corp.adobe.com/AdobeDocs` moeten gebruiken.

## Gereedschappen en instellen

Communautaire contribuanten kunnen GitHub UI voor basishet uitgeven of vork gebruiken het repo om belangrijke bijdragen te leveren.

Zie de [ Gids van de Medewerker van de Docent van Adobe ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) voor details.

## Hoe te om Markdown te gebruiken om uw onderwerp te formatteren

Alle artikelen in deze repository gebruiken GitHub gearomatiseerde Markdown. Als u niet vertrouwd bent met Markeringen, zie:

- [ Grondbeginselen van de Prijsverlaging ](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
- [ Afdrukbare prijsdaling ](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Koppelingen vooraf toewijzen voor optimalisatie van afbeeldingen

Deze opslagplaats omvat geautomatiseerde haken die vooraf worden vastgelegd en die afbeeldingen optimaliseren voordat ze worden vastgelegd. **Alle contribuanten zouden deze haken** moeten toelaten om verenigbare beeldoptimalisering en verminderde bewaarplaatsgrootte te verzekeren.

### Snelle installatie

Nadat u de opslagplaats hebt gekloond, voert u het volgende uit:

```bash
.githooks/setup-hooks.sh
```

### Wat de haken doen

- Gelaagde afbeeldingsbestanden automatisch detecteren (PNG, JPG, JPEG, GIF, SVG)
- `image_optim` uitvoeren om afbeeldingen te comprimeren en te optimaliseren
- Geoptimaliseerde afbeeldingen automatisch opnieuw plaatsen
- Zorg ervoor dat alle toegewezen images correct zijn geoptimaliseerd

### Voordelen

- Beperkte grootte opslagplaats
- Snellere paginabelasting voor documentatie
- Consistente beeldkwaliteit voor alle contribuanten
- Geen handmatige optimalisatie vereist

Zie [`.githooks/README.md`](.githooks/README.md) voor gedetailleerde installatie-instructies, probleemoplossing en configuratie.
