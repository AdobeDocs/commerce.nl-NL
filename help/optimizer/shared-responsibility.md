---
title: Gedeelde verantwoordelijkheid
description: Leer over de veiligheidstaken van elke partij betrokken bij uw  [!DNL Adobe Commerce Optimizer]  project.
role: Admin, Architect, Leader
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is op Adobe Commerce as a Cloud Service en  [!DNL Adobe Commerce Optimizer]  slechts projecten (Adobe-Beheerde infrastructuur SaaS) van toepassing."
exl-id: 9e09790f-832d-43ab-b2df-6389ad52b43d
source-git-commit: c7c21df464685783b5fae1c99d60ca91e0c334d2
workflow-type: tm+mt
source-wordcount: '271'
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
| Dynamiek openen voor [!DNL Adobe Commerce Optimizer] | R | C |
| Problemen met de beveiliging van back-end klanten oplossen | RA | I |
| Oplossen van CDN-beveiligingsproblemen met back-end | RA | |
| Adobe helpen met veiligheidsonderzoek (scans/audits) | RA | |
| PCI ASV-scans uitvoeren | RA | I |
| [!DNL Adobe Commerce Optimizer] infrastructuur-PCI-scans herstellen | R | |
| Besturings- en platformgeheimen beheren | RA | |
| Bewaking van beveiligingslogboeken voor back-endbestanden | RA | |
| Klantenondersteuning en toegang beheren | A | R |
| Jaarlijkse tests en documentatie van noodherstelplan en back-up en herstel van Adobe | RA | |
| Jaarlijkse tests en documentatie van het noodherstelplan | RA | |
| Foutopsporing en probleemoplossing | R | R |
| Tijdige ondersteuning voor foutopsporing en probleemoplossingsproces | R | R |
| Updates en patches installeren op [!DNL Adobe Commerce Optimizer] | RA | I |
| Kwaliteit van de kerntoepassing [!DNL Adobe Commerce Optimizer] | RA | |
