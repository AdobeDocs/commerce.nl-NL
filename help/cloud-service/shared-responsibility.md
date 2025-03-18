---
title: Gedeelde verantwoordelijkheid
description: Leer meer over de beveiligingsverantwoordelijkheden van elke partij die betrokken is bij uw Adobe Commerce as a Cloud Service-project.
role: Admin, Architect, Leader
source-git-commit: 19c49b2b9d630898353addd778e062d3208505c1
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---


# Beveiliging en operationeel model van gedeelde verantwoordelijkheid

Adobe Commerce as a Cloud Service is een service op aanvraag die afhankelijk is van een beveiliging en operationeel model met gedeelde verantwoordelijkheid. Deze verantwoordelijkheden worden gedeeld tussen Adobe en klanten. Elke partij draagt een duidelijke verantwoordelijkheid voor de beveiliging en de werking van de Adobe Commerce-toepassing.

>[!BEGINSHADEBOX]

In de volgende overzichtstabellen wordt het RACI-model gebruikt om de beveiligingsverantwoordelijkheden weer te geven die worden gedeeld tussen Adobe en klanten.

**R** — Verantwoordelijk
**A** — Verantwoordelijk
**C** — Geconsulteerd
**I** — Informed

>[!ENDSHADEBOX]

| Taak | Adobe | Klant |
| --- | --- | --- |
| Adobe Commerce-infrastructuurpatches toepassen | RA | |
| Patches toepassen op ondersteunende services (bijvoorbeeld Nginx of MySQL) | RA | |
| WAF-regels voor achterwaartse oorsprong definiëren | RA | |
| WAF-regels voor backend CDN definiëren | RA | |
| WAF-regels voor back-endplatforms implementeren | RA | |
| WAF-regels voor back-end implementeren | RA | |
| Problemen met kernfouten in Adobe Commerce as a Cloud Service verhelpen | RA | I |
| Adobe Commerce as a Cloud Service-infrastructuurpatches vrijgeven | RA | |
| Schalen (infrastructuur) | RA | |
| Schalen (kerntoepassing) | RA | |
| Externe toepassingen integreren | | RA |
| App Builder-toepassingen installeren | | RA |
| Testprestaties voor alle App Builder-apps | | RA |
| Thema en ontwerp van aangepaste App Builder-apps | | RA |
| Het vormen achterste DNS | RA | I |
| On-boarding backend CDN | RA | I |
| Ondersteuning voor back-end CDN | RA | I |
| Een omgekeerde DNS-provider verkrijgen | RA | |
| Productie- en sandboxomgevingen | A | R |
| Dynamiek openen voor Adobe Commerce op cloudinfrastructuur | R | C |
| Problemen met de beveiliging van back-end klanten oplossen | RA | I |
| Oplossen van CDN-beveiligingsproblemen met back-end | RA | |
| Adobe helpen met veiligheidsonderzoek (scans/audits) | RA | |
| PCI ASV-scans uitvoeren | RA | I |
| Adobe Commerce-infrastructuurafbeeldingen in PCI herstellen | R | |
| Besturings- en platformgeheimen beheren | RA | |
| Bewaking van beveiligingslogboeken voor back-endbestanden | RA | |
| Klantenondersteuning en toegang beheren | A | R |
| Jaarlijkse tests en documentatie van noodherstelplan en back-up en herstel van Adobe | RA | |
| Jaarlijkse tests en documentatie van het noodherstelplan | RA | |
| Foutopsporing en probleemoplossing | R | R |
| Tijdige ondersteuning voor foutopsporing en probleemoplossingsproces | R | R |
| Updates en patches publiceren naar Adobe Commerce Core | RA | I |
| Updates en patches installeren op Adobe Commerce Core | RA | I |
| Kwaliteit Adobe Commerce-toepassing | RA | |
