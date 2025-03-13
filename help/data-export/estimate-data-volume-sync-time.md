---
title: Gegevensvolume en verzendingstijd schatten
description: Leer om het gegevensvolume en de transmissietijd te schatten die voor het  [!DNL data export]  wordt vereist hulpmiddel om voedergegevens tussen Adobe Commerce en de verbonden diensten te synchroniseren.
role: Admin, Developer
exl-id: 787d05d6-fc2f-4f23-8ea7-ef54330e1f37
source-git-commit: 86f7473e994348d81c0a8f71548bb7a8d3923a21
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Gegevensvolume en zendtijd schatten voor gegevenssynchronisatie

Adobe raadt u aan het gegevensvolume en de synchronisatietijd te schatten voordat u de synchronisatie van de gegevensinvoer start, zodat de planning soepel verloopt en verstoring van de sitebewerkingen wordt voorkomen. Deze schatting is belangrijk bij de planning voor initiële syncs of grootschalige catalogusupdates, zoals wijzigingen in de massaprijs.

Standaard verwerkt het gereedschap voor het exporteren van gegevens gegevens gegevens in de modus Eén thread met een standaardbatch. Met de standaardconfiguratie, is er geen parallellisatie van het proces van de voedervoorlegging. Bovendien accepteert deze component aanvragen per seconde (RPS) die als volgt worden vertaald:

- Tot 10.000 producten per minuut wanneer een product een SKU met eigenschappen in een specifieke opslagvoorproef is
- Tot 50.000 prijzen per minuut

De volgende factoren beïnvloeden de tijd van de gegevenstransmissie tijdens synchronisatie.

- Het aantal threads is ingesteld op 1 (standaard)
- De grootte van de partij wordt geplaatst aan _100_ voor alle voer behalve het `prices` voer, waar het aan _500_ wordt geplaatst.
- De acceptatiesnelheid van het voer is 2 aanvraag per seconde.
- Alle producten worden toegewezen aan alle bestaande websites
- Voor de prijsberekeningsscenario&#39;s zijn aan alle producten speciale en gegroepeerde prijzen toegewezen


## Gegevensoverdracht per feed berekenen

Gebruik de waarden en formules in de volgende tabel om het gegevensvolume en de synchronisatietijd voor elke gegevensfeed te berekenen.

>[!NOTE]
>
>Deze berekeningen zijn gebaseerd op een transmissietarief van 2 verzoeken per seconde. De snelheid is gebaseerd op de tijd die nodig is voor gegevensverzameling en gegevensverzending. De werkelijke transmissiesnelheid varieert afhankelijk van de grootte van de lading van de aanvraag en de huidige lading op de Commerce-toepassingsserver.

| Feed | Gegevensvoorbeeld | Formule voor het berekenen van records | Voorspeld aantal aanvragen | Voorspelde synchronisatietijd |
| --- | --- | --- | --- | --- |
| Producten | Producten (P): 10000, Winkelweergaven (SV): 4 | P * SV = 40000 | 40000 / Batchgrootte (100) = 400 verzoeken | (400 verzoeken * 0,5 seconden per aanvraag) / 60 = 3,3 minuten |
| Categorieën | Categorieën (C): 500, Winkelweergaven (SV): 4 | C * SV = 2000 | 2000 / Batchgrootte (100) = 20 verzoeken | (20 verzoeken * 0,5 seconden per verzoek) / 60 = 0,1 minuten (4 seconden) |
| Prijzen | Producten (P): 10000, Klantengroepen (CG): 6 (bijvoorbeeld unieke prijs in gedeelde catalogus), Websites (WS): 2 | P \* WS * CG = 120000 | 120000 / Batchgrootte (500) = 240 verzoeken | (240 verzoeken * 0,5 seconden per aanvraag) / 60 = 2 minuten |
| Productoverschrijvingen | Producten met machtigingen of in gedeelde catalogus (P): 10000, Betrokken Klantengroepen (CG): 5, Toegewezen websites: 2 | P \* WS * CG = 100000 | 100000 / Batchgrootte (100) = 1000 verzoeken | (1000 verzoeken * 0,5 seconden per aanvraag) / 60 = 8,3 minuten |
| Productvarianten | Varianten (onderliggende producten) toegewezen aan configureerbare producten (PV): 100000 | PV = 100000 | 100000 / Batchgrootte (100) = 1000 verzoeken | (1000 verzoeken * 0,5 seconden per aanvraag) / 60 = 8,3 minuten |
| Categoriemachtigingen | Aantal van alle Toestemmingen van de Categorie + 4 reserveverslagen (CP): 10000 | CP = 10000 | 10000 / Batchgrootte (100) = 100 verzoeken | (100 verzoeken * 0,5 seconden per verzoek) / 60 = 0,8 minuten (50 seconden) |
| Status voorraad | Producten (P): 10000, Voorraadproducten toegewezen aan (S): 5 (ervan uitgaande dat elk product aan elke voorraad wordt toegewezen) | P * S = 50000 | 50000 / Batchgrootte (100) = 500 verzoeken | (500 verzoeken * 0,5 seconden per aanvraag) / 60 = 4,2 minuten |
| Verkooporders | Alle transactiebestanden (inclusief facturen, verzendingen, enzovoort) (SO): 10000 | SO = 10000 | 10000 / Batchgrootte (100) = 100 verzoeken | (100 verzoeken * 0,5 seconden per verzoek) / 60 = 0,8 minuten (50 seconden) |
