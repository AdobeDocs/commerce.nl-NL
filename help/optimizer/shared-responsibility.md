---
title: Gedeelde verantwoordelijkheid
description: Leer over de veiligheidstaken van elke partij betrokken bij uw  [!DNL Adobe Commerce Optimizer]  project.
role: Admin, Architect, Leader
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 7c407bfc2becfb0ba6babe5958bcb790c178f406
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 0%

---

# Beveiliging en operationeel model van gedeelde verantwoordelijkheid

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
| Patches toepassen op ondersteunende services | RA | |
| WAF-regels voor achterwaartse oorsprong definiëren | RA | |
| WAF-regels voor backend CDN definiëren | RA | |
| WAF-regels voor back-endplatforms implementeren | RA | |
| WAF-regels voor back-end implementeren | RA | |
| Fouten corrigeren in [!DNL Adobe Commerce Optimizer] | RA | I |
| Het vrijgeven van [!DNL Adobe Commerce Optimizer] infrastructuurflarden | RA | |
| Schalen (infrastructuur) | RA | I |
| Externe toepassingen integreren | | RA |
| App Builder-toepassingen installeren | | RA |
| Testprestaties voor alle App Builder-apps | | RA |
| Thema en ontwerp van aangepaste App Builder-apps | | RA |
| Het vormen achterste DNS | RA |  |
| On-boarding backend CDN | RA |  |
| Ondersteuning voor back-end CDN | RA |  |
| Een omgekeerde DNS-provider verkrijgen | RA | |
| Productie- en sandboxomgevingen | A | R |
| Dynamiek openen voor Adobe Commerce Optimizer | R | C |
| Problemen met de beveiliging van back-end klanten oplossen | RA | I |
| Oplossen van CDN-beveiligingsproblemen met back-end | RA | |
| Adobe helpen met veiligheidsonderzoek (scans/audits) | RA | |
| PCI ASV-scans uitvoeren | RA | I |
| Adobe Commerce Optimizer-infrastructuurafbeeldingen in PCI herstellen | R | |
| Besturings- en platformgeheimen beheren | RA | |
| Bewaking van beveiligingslogboeken voor back-endbestanden | RA | |
| Klantenondersteuning en toegang beheren | A | R |
| Jaarlijkse tests en documentatie van noodherstelplan en back-up en herstel van Adobe | RA | |
| Jaarlijkse tests en documentatie van het noodherstelplan | RA | |
| Foutopsporing en probleemoplossing | R | R |
| Tijdige ondersteuning voor foutopsporing en probleemoplossingsproces | R | R |
| Updates en patches installeren op Adobe Commerce Optimizer | RA | I |
| Kwaliteit Adobe Commerce Optimizer-toepassing | RA | |
