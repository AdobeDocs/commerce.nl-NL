---
title: HIPAA Gereedheid voor  [!DNL Commerce]  Diensten
description: Leer hoe u de  [!DNL Data Connection]  uitbreiding kunt gebruiken om  [!DNL Commerce]  gegevens met Experience Platform te delen en naleving te handhaven HIPAA.
role: Admin, Leader
feature: Security, Compliance
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# HIPAA-gereedheid voor [!DNL Commerce] Services

Met de extensie [!DNL Data Connection] kunt u [!DNL Commerce] back office-gebeurtenisgegevens delen met Experience Platform en de HIPAA-compatibiliteit behouden.

>[!IMPORTANT]
>
>Omdat storefront de gebeurtenissen cliënt-kant worden geproduceerd, is het de verantwoordelijkheid van de handelaar [ niet om storefront gebeurtenisgegevens ](connect-data.md#data-collection) naar Experience Platform te verzenden.

In dit artikel leert u:

- Installeren
- Hoe te om gegevens te verzekeren die naar Experience Platform worden verzonden is HIPAA-klaar
- Gegevensversleuteling in [!DNL Commerce]

## Installatie

Als u toe:voegen-op van de gezondheidszorg voor Adobe [!DNL Commerce] kocht, installeerde u zeer waarschijnlijk reeds de [ HIPAA-Klaar uitbreiding ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/compliance/hipaa-ready-service/overview#installation). Om ervoor te zorgen dat uw [!DNL Commerce] gegevens van de achterkantoorgebeurtenis HIPAA-klaar zijn, moet u ook de [!DNL Data Connection] uitbreiding met de extra **3&rbrace; uitbreiding van HIPAA van de Diensten van Gegevens installeren &lbrace;.** De **uitbreiding van HIPAA van de Diensten van Gegevens** zorgt ervoor dat om het even welke achterkantoorgegevens u naar Experience Platform verzendt HIPAA-klaar is. Leer [ hoe te om de uitbreiding ](install.md#install-the-data-services-hipaa-extension) te installeren.

>[!IMPORTANT]
>
>Wanneer u de **uitbreiding van HIPAA van de Diensten van Gegevens** installeert, worden de gegevens van de storefront gebeurtenis die door Levend Onderzoek en de Aanbevelingen van het Product wordt gebruikt niet meer gevangen. Dit komt doordat gebeurtenisgegevens voor storefront op de client worden gegenereerd. Om storefront gebeurtenisgegevens te blijven vangen en verzenden, re-enable gebeurtenisinzameling voor deze diensten. Zie [ algemene configuratie ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/general.html#data-services) om meer te leren.

## Hoe te om gegevens te verzekeren die naar Experience Platform worden verzonden is HIPAA-klaar

Alle gegevens van de backoffice-gebeurtenis die de [!DNL Data Connection] -extensie naar Experience Platform verzendt, worden binnen [!DNL Commerce] als gevoelig beschouwd. Het is echter de verantwoordelijkheid van de handelaar om gegevensgebruikslabels toe te passen op zijn [!DNL Commerce] -schema in Experience Platform om bepaalde gegevens expliciet als gevoelig aan te duiden. Wanneer u de etiketten van het gegevensgebruik rechtstreeks op een schema toepast, worden die etiketten verspreid aan alle bestaande en toekomstige datasets die op dat schema gebaseerd zijn.

Voor een overzicht van de etiketten van het gegevensgebruik en hun rol binnen het kader van het Beleid van Gegevens, zie het [ overzicht van de etiketten van het gegevensgebruik ](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) in de documentatie van Experience Platform.

### Gegevensgebruikslabels toepassen op [!DNL Commerce] -velden

Volg de stappen in [ leiden de etiketten van het gegevensgebruik voor een schema ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/labels) leerprogramma leren hoe te om etiketten op uw [!DNL Commerce] schema toe te passen.

Zie de [ verklarende woordenlijst van gevoelige etiketten ](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/reference#sensitive) over de beschikbare etiketten leren u op de gebieden in uw [!DNL Commerce] schema kunt toepassen. Zo identificeert het label `RHD` bijvoorbeeld Protected Health Information (PHI) of informatie over een patiënt die u contractueel door Adobe mag uploaden.

Wanneer uw [!DNL Commerce] -gegevens als gevoelig worden gelabeld, kunt u beleid toepassen om gegevensbewerkingen te voorkomen die beleidsovertredingen vormen. Leer meer over [ beleidshandhaving ](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview) in Experience Platform.

## Gegevenscodering in Commerce

Adobe [!DNL Commerce] gebruikt codering op blokniveau. Voor opslag gebruikt [!DNL Commerce] Amazon Elastic Block Store (EBS). Alle EBS-volumes worden gecodeerd met het algoritme AES-256, wat betekent dat de gegevens in rust worden gecodeerd. [!DNL Commerce] gegevens in doorvoer worden uitgevoerd over beveiligde, gecodeerde verbindingen die HTTPS [ TLS v1.2 ](https://datatracker.ietf.org/doc/html/rfc5246) gebruiken.

>[!IMPORTANT]
>
>Commerce biedt geen ondersteuning voor codering of codering op kolom- of rijniveau wanneer de gegevens niet in rust zijn of niet worden verzonden tussen servers.

### Gegevenscodering in Experience Platform

Wanneer handelaren hun gegevens naar Experience Platform verzenden, worden die gegevens verzonden met HTTPS TLS v1.2. Leer meer over hoe [ Experience Platform ](https://experienceleague.adobe.com/en/docs/experience-platform/landing/governance-privacy-security/encryption) gegevens codeert.

## Hoe [!DNL Commerce] privacyverzoeken verwerkt

Leer hoe [!DNL Commerce] [ privacyverzoeken ](handle-privacy-request.md) behandelt.
