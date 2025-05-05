---
title: Profielrecords
description: Leer welke gegevens een profielrecord vastlegt.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# [!DNL Data Connection] Profielrecords

Hieronder worden de Commerce-profielrecordgegevens beschreven die beschikbaar zijn wanneer u de extensie [!DNL Data Connection] installeert. De gegevens in profielrecords worden naar de Adobe Experience Platform verzonden.

## Profielrecord

De updates van de profielrecord zijn beschikbaar in de Experience Platform wanneer een nieuw profiel wordt gemaakt, bijgewerkt of verwijderd.

### Gegevens verzameld uit profielrecord

Hieronder worden de gegevens beschreven die zijn vastgelegd voor een profielrecord.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/schema/namespaces). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `person` | Bevat informatie over de klant. |
| `person.name` | Bevat informatie over de naam van de klant. |
| `person.name.firstName` | Bevat de voornaam van de klant. |
| `person.name.lastName` | Bevat de achternaam van de klant. |
| `person.birthDate` | Geboortedatum van de verkoopster. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `billingAddress` | Het postadres van de facturering. |
| `billingAddress.street1` | Primaire straatinformatie, appartementnummer, straatnummer en straatnaam. |
| `billingAddress.street2` | Optionele straatinformatie, tweede regel. |
| `billingAddress.city` | De naam van de stad. |
| `billingAddress.state` | De naam van de staat. Dit is een veld met vrije vorm. |
| `billingAddress.country` | De naam van het door de overheid bestuurde gebied. Met uitzondering van `xdm:countryCode` is dit een veld met vrije vorm dat de landnaam in elke taal kan hebben. |
| `billingAddress.primary` | Geeft aan of dit het primaire factureringsadres is. Waarde is altijd `False` . |
| `billingAddressPhone` | Het telefoonnummer dat aan het factuuradres is gekoppeld. |
| `billingAddressPhone.number` | Het telefoonnummer. Het telefoonnummer is een tekenreeks en kan betekenisvolle tekens bevatten, zoals vierkante haakjes `()` , afbreekstreepjes `-` of tekens die als id&#39;s voor subkieslijsten dienen, zoals extensies `x` , bijvoorbeeld `1-353(0)18391111` of `+613 9403600x1234` . |
| `billingAddressPhone.primary` | Geeft aan of dit het primaire telefoonnummer voor het factuuradres is. Waarde is altijd `False` . |
| `shippingAddress` | Het postadres voor verzending. |
| `shippingAddress.street1` | Primaire straatinformatie, appartementnummer, straatnummer en straatnaam. |
| `shippingAddress.street2` | Optionele straatinformatie, tweede regel. |
| `shippingAddress.city` | De naam van de stad. |
| `shippingAddress.state` | De naam van de staat. Dit is een veld met vrije vorm. |
| `shippingAddress.country` | De naam van het door de overheid bestuurde gebied. Met uitzondering van `xdm:countryCode` is dit een veld met vrije vorm dat de landnaam in elke taal kan hebben. |
| `shippingAddress.primary` | Geeft aan of dit het primaire verzendadres is. Waarde is altijd `False` . |
| `shippingAddressPhone` | Het telefoonnummer dat aan het verzendadres is gekoppeld. |
| `shippingAddressPhone.number` | Het telefoonnummer. Het telefoonnummer is een tekenreeks en kan betekenisvolle tekens bevatten, zoals vierkante haakjes `()` , afbreekstreepjes `-` of tekens die als id&#39;s voor subkieslijsten dienen, zoals extensies `x` , bijvoorbeeld `1-353(0)18391111` of `+613 9403600x1234` . |
| `shippingAddressPhone.primary` | Geeft aan of dit het primaire telefoonnummer voor het verzendadres is. Waarde is altijd `False` . |
| `userAccount` | Hiermee geeft u eventuele loyaliteitsdetails, voorkeuren, aanmeldingsprocessen en andere accountvoorkeuren aan. |
| `userAccount.startDate` | De datum waarop het profiel voor het eerst is gemaakt. |

>[!NOTE]
>
>Elk profielverslag omvat ook het [`identityMap` ](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/field-groups/profile/identitymap) gebied, dat het systeem geproduceerde identiteitskaart van de Klant van Commerce als primaire herkenningsteken voor het profiel en een e-mailidentiteitskaart omvat die als secundaire herkenningsteken wordt gebruikt.

Leer hoe te [ een profiel tot stand brengen verslag-specifiek schema ](profile-data.md) dat de gegevens van uw profielverslagen kan opnemen.
