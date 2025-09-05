---
title: Cookie-beperkingen verwerken
description: Leer hoe de Aanbevelingen van het Product koekjesbeperkingen en privacynaleving behandelen.
exl-id: 7e7342db-b903-4105-93c0-e4022c81673b
source-git-commit: dbb36b9fa800e128f1aea795a891ffbfb751aa76
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Cookie-beperkingen verwerken

Zowel Adobe Commerce als Magento Open Source vragen om toestemming voordat gegevens in browsercookies worden opgeslagen. Voor meer informatie, verwijs naar [ de beperkingswijze van het Koekje ](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

## Hoe de Aanbevelingen van het Product koekjesbeperkingen behandelen

Wanneer u de `magento/product-recommendations` module aan productie opstelt, begint het inzamelen van de gebeurtenissen van de winkelinteractie op uw storefront. Deze gegevens kunnen worden opgeslagen in browsercookies of lokale opslag voor het inschakelen van aanbevelingen.

>[!IMPORTANT]
>
>De aanbevelingen van het product respecteren nu de beperkingswijze van het koekje door geen gegevens in koekjes of lokale opslag te verzamelen of op te slaan wanneer de koekjesbeperkingen worden toegelaten. Dit omvat gedragsgegevens die voor gepersonaliseerde aanbevelingen worden gebruikt.

### Gegevens waarop cookies zijn ingesteld

De volgende productaanbevelingen worden niet verzameld wanneer de beperkingsmodus voor cookies is ingeschakeld:

- **Gedragsgegevens**: De meningen van het product, toe:voegen-aan-kart acties, aankopen, en andere winkelinteractie.
- **gegevens van de Zitting**: De informatie van de de zittingszitting en de interacties van de aanbeveling van de aanbevelingseenheid.
- **gegevens van Personalization**: Gegevens die voor aanbevelingen worden gebruikt types zoals &quot;onlangs bekeken&quot;en &quot;het meest aangekocht&quot;.

### Gevolgen voor soorten aanbevelingen

Wanneer de beperkingsmodus voor cookies is ingeschakeld en kopers cookies niet hebben geaccepteerd, worden bepaalde soorten aanbevelingen mogelijk niet weergegeven of geven ze een beperkt resultaat:

- **onlangs bekeken producten**: Vereist zittingsgegevens die in koekjes/lokale opslag worden opgeslagen.
- **geadviseerd voor u**: Vereist gedragsgegevens voor verpersoonlijking.
- **kocht dit, kocht dat**: Vereist de gegevens van de aankoopgeschiedenis.

>[!NOTE]
>
>De types van aanbeveling die niet op gedragsgegevens, zoals &quot;het meest bekeken&quot;en &quot;Visuele gelijkenis&quot;baseren zullen normaal zelfs met toegelaten koekjesbeperkingen blijven werken.

## Oplossingen voor cookie van andere leveranciers

Aanbevelingen voor producten kunnen niet automatisch worden geïntegreerd met oplossingen voor cookies van derden. Het is de verantwoordelijkheid van de handelaar om ervoor te zorgen dat de gegevensverzameling in overeenstemming is met de toepasselijke privacywetten en -voorschriften.

Als u een oplossing van de douanekoekjestoestemming gebruikt, kunt u het do-not-track koekjesmechanisme uitvoeren om gegevensinzameling te controleren.

### Cookies niet bijhouden implementeren

Met het cookie `mg_dnt` kunt u de gegevensverzameling programmatisch beheren:

#### Naam cookie

```javascript
const DNT_COOKIE = "mg_dnt";
```

#### Gegevensverzameling uitschakelen

Stel de niet-bijgehouden cookie in wanneer gebruikers cookies weigeren:

```javascript
$.mage.cookies.set(DNT_COOKIE, true);
```

#### Gegevensverzameling inschakelen

Wis het niet-bijhouden cookie wanneer gebruikers cookies accepteren:

```javascript
$.mage.cookies.clear(DNT_COOKIE);
```

## Modus voor het testen van cookie

Om te testen hoe de Aanbevelingen van het Product met koekjesbeperkingen gedraagt:

1. Schakel de beperkingsmodus voor cookies in uw Adobe Commerce-configuratie in.
1. Bezoek je winkel zonder cookies te accepteren.
1. Verifieer dat de aanbevelingen de aangewezen reserve inhoud tonen.
1. Accepteer cookies en controleer of de aanbevelingen beginnen met het verzamelen van gegevens.

## Privacynaleving

Gegevensverzameling van productaanbevelingen omvat geen persoonlijk identificeerbare informatie (PII). Alle gebruikers-id&#39;s, zoals cookie-id&#39;s en IP-adressen, worden geanonimiseerd. Voor meer informatie, zie het [ Beleid van de Privacy van Adobe ](https://www.adobe.com/privacy/policy.html).

>[!TIP]
>
>Voor gezondheidszorgklanten die de uitbreiding van HIPAA van de Diensten van Gegevens gebruiken, kan de extra configuratie worden vereist. Zie [ Gereedheid van HIPAA ](../data-connection/hipaa-readiness.md) voor meer informatie.
