---
title: Gedeelde verantwoordelijkheid
description: Leer over de veiligheidstaken van elke partij betrokken bij uw  [!DNL Adobe Commerce as a Cloud Service]  project.
role: Admin, Architect, Leader
exl-id: 424fe5cd-5d54-425d-97ce-024476d18dde
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 34057c1e55ff117ea7aab4407f31548ce826691b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Beveiliging en operationeel model van gedeelde verantwoordelijkheid

{{accs-early-access}}

[!DNL Adobe Commerce as a Cloud Service] is een service op aanvraag die afhankelijk is van een beveiligingsmodel en een operationeel model voor gedeelde verantwoordelijkheid. Deze verantwoordelijkheden worden gedeeld tussen Adobe en klanten. Elke partij draagt een duidelijke verantwoordelijkheid voor de beveiliging en de werking van de Adobe Commerce-toepassing.

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
| Kernfouten corrigeren in [!DNL Adobe Commerce as a Cloud Service] | RA | I |
| [!DNL Adobe Commerce as a Cloud Service] infrastructuurafbeeldingen vrijgeven | RA | |
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
