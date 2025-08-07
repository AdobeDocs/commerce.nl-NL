---
title: Aangepaste kenmerken toevoegen aan profielen
description: Leer hoe u aangepaste kenmerken aan klantprofielen kunt toevoegen.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 5489910382edc70eea5d7c0ca94da41c653b577d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---


# Aangepaste kenmerken toevoegen aan profielen

Met aangepaste profielkenmerken kunt u de identificatie van uw klantprofiel in Experience Platform verbeteren door aanvullende id&#39;s te gebruiken die verdergaan dan de standaardinstellingen `customerId` en `emailId` . Deze extra id&#39;s maken een preciezere klantmatching en verbeterde gegevensintegratie tussen het Commerce-platform en Experience Platform mogelijk.

>[!NOTE]
>
>Leer hoe u douaneattributen [ aan orden kunt ](custom-attributes.md) toevoegen.

## Voordelen

- Gebruik meerdere id&#39;s voor een betere overeenkomst met de klant.
- Wijs aangepaste velden toe aan identiteitskenmerken op basis van uw bedrijfsbehoeften.
- Dubbele profielen reduceren en de nauwkeurigheid van klantgegevens verbeteren.
- Gerichte ervaringen met klanten mogelijk maken.

## Vereisten

Voordat u aangepaste identiteitskenmerken implementeert, moet u controleren of:

- [De extensie Gegevensverbinding installeren](install.md)
- [Verbinding maken met Adobe Experience Platform](connect-data.md)
- [Klantprofielgegevens verzenden](connect-data.md#send-customer-profile-data)

## Stap 1: Experience Platform-schema configureren

1. Meld u aan bij Adobe Experience Platform en selecteer het Commerce-schema.
1. [ voeg de gebieden van de douanetechniek ](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/ui/resources/schemas?lang=en#custom-fields-for-standard-groups) op het wortelniveau toe:
   - `hashedPID` (String) - Primaire identiteitshash
   - `hashedSID` (String) - Secundaire identiteitshash
   - `primaryID` (String) - Naam van primair identiteitsveld
   - `secondaryID` (String) - Naam van secundair identiteitsveld

![ de Configuratie van het Schema van Experience Platform ](./assets/aep-schema-configuration.png)

>[!NOTE]
>
>U kunt de exacte veldnamen op basis van uw vereisten aanpassen. In het voorbeeld worden `hashedPID` en `hashedSID` gebruikt als identiteitsvelden.

## Stap 2: Processorklassen maken

Maak de volgende PHP processorklassen in je aangepaste module:

### AddressCustomHashedId, klasse

Deze processor hashes `parent_id` en `entity_id` voor klantadressen.

```php
<?php declare(strict_types=1);

namespace Magento\AepCustomerCustomAttributes\Event;
use Magento\AdobeCommerceEventsClient\Event\Event;
use Magento\AdobeCommerceEventsClient\Event\Processor\EventDataProcessorInterface;

class AddressCustomHashedId implements EventDataProcessorInterface
{
    public function process(Event $event, array $eventData): array
    {
        $pid = $eventData['parent_id'] ?? '';
        $sid = $eventData['entity_id'] ?? '';

        $eventData['profileAttributes']['hashedPID'] = hash('sha256', (string)$pid);
        $eventData['profileAttributes']['hashedSID'] = hash('sha256', (string)$sid);
        return $eventData;
    }
}
```

### AddressCustomId-klasse

Deze verwerker plaatst de primaire en secundaire gebiedsnamen van identiteitskaart voor adresgebeurtenissen.

```php
<?php declare(strict_types=1);

namespace Magento\AepCustomerCustomAttributes\Event;
use Magento\AdobeCommerceEventsClient\Event\Event;
use Magento\AdobeCommerceEventsClient\Event\Processor\EventDataProcessorInterface;

class AddressCustomId implements EventDataProcessorInterface
{
    public function process(Event $event, array $eventData): array
    {
        $eventData['profileAttributes']['primaryID'] = 'hashedPID';
        $eventData['profileAttributes']['secondaryID'] = 'hashedSID';

        // Ensure both IDs are present, otherwise, Commerce will default primary to customerId and secondary to emailId
        if (empty($eventData['profileAttributes']['primaryID']) || empty($eventData['profileAttributes']['secondaryID'])) {
            $eventData['profileAttributes']['primaryID'] = $eventData['customerId'] ?? '';
            $eventData['profileAttributes']['secondaryID'] = $eventData['email'] ?? '';
        }

        return $eventData;
    }
}
```

### CustomHashedId-klasse

Deze processor hashes `entity_id` en `email` voor klantprofielen.

```php
<?php declare(strict_types=1);

namespace Magento\AepCustomerCustomAttributes\Event;
use Magento\AdobeCommerceEventsClient\Event\Event;
use Magento\AdobeCommerceEventsClient\Event\Processor\EventDataProcessorInterface;

class CustomHashedId implements EventDataProcessorInterface
{
    public function process(Event $event, array $eventData): array
    {
        $pid = $eventData['entity_id'] ?? '';
        $sid = $eventData['email'] ?? '';

        $eventData['profileAttributes']['hashedPID'] = hash('sha256', (string)$pid);
        $eventData['profileAttributes']['hashedSID'] = hash('sha256', (string)$sid);
        return $eventData;
    }
}
```

### CustomId-klasse

Deze processor stelt de namen van primaire en secundaire id-velden in voor profielgebeurtenissen.

```php
<?php declare(strict_types=1);

namespace Magento\AepCustomerCustomAttributes\Event;
use Magento\AdobeCommerceEventsClient\Event\Event;
use Magento\AdobeCommerceEventsClient\Event\Processor\EventDataProcessorInterface;

class CustomId implements EventDataProcessorInterface
{
    public function process(Event $event, array $eventData): array
    {
        $eventData['profileAttributes']['primaryID'] = 'hashedPID';
        $eventData['profileAttributes']['secondaryID'] = 'hashedSID';

        // Ensure both IDs are present, otherwise, Commerce will default primary to customerId and secondary to emailId
        if (empty($eventData['profileAttributes']['primaryID']) || empty($eventData['profileAttributes']['secondaryID'])) {
            $eventData['profileAttributes']['primaryID'] = $eventData['customerId'] ?? '';
            $eventData['profileAttributes']['secondaryID'] = $eventData['email'] ?? '';
        }

        return $eventData;
    }
}
```

>[!NOTE]
>Zorg ervoor dat zowel `primaryID` als `secondaryID` in de gebeurtenisgegevens worden verzonden. Als een van beide ontbreekt, wordt Commerce standaard ingesteld op:
>
>- primaryID = customerId
>- secundairID = emailId

>[!BEGINSHADEBOX]

Nadat u deze twee stappen voltooit:

- Met uw Commerce-schema in Experience Platform kunt u op de juiste wijze aangepaste identiteiten voor uw profielgebeurtenisgegevens invoeren.
- Processorklassen in uw Commerce PHP-code verzamelen aangepaste identificatiegegevens van profielgebeurtenissen.

Alle profielgebeurtenisgegevens die door Commerce worden verzonden, bevatten nu uw aangepaste id-gegevens.

>[!ENDSHADEBOX]

## Voorbeelden van gegevensindelingen

In de volgende voorbeelden wordt de verwachte JSON-structuur voor aangepaste identiteitskenmerken getoond in zowel profielkenmerken als volledige gegevensindelingen voor klantprofielen.

### Profielkenmerkindeling

```json
{
  "profileAttributes": {
    "hashedPID": "d80eae6e96d148b3b2abbbc6760077b66c4ea071f847dab573d507a32c4d99a5",
    "hashedSID": "fa7359e288ce3104bd4317a4fb75f08c4a5feec472de2e415b8260fb3567ebe6",
    "warehousecode": "1256",
    "method": "ina2354",
    "source": "commerce",
    "primaryID": "hashedPID",
    "secondaryID": "hashedSID"
  }
}
```

### Klantprofielstructuur voltooien

```json
{
  "id": 137,
  "entity_id": "137",
  "created_at": "2025-02-10 20:10:30",
  "updated_at": "2022-02-10 20:10:31",
  "email": "customer@example.com",
  "firstname": "John",
  "lastname": "Doe",
  "dob": "2007-10-01 00:00:00",
  "profileAttributes": {
    "hashedPID": "d80eae6e96d148b3b2abbbc6760077b66c4ea071f847dab573d507a32c4d99a5",
    "hashedSID": "fa7359e288ce3104bd4317a4fb75f08c4a5feec472de2e415b8260fb3567ebe6",
    "primaryID": "137",
    "secondaryID": "customer@example.com"
  },
  "_metadata": {
    "commerceEdition": "Adobe Commerce",
    "commerceVersion": "2.4.6",
    "eventsClientVersion": "1.9.0",
    "storeId": "1",
    "websiteId": "1",
    "storeGroupId": "1",
    "websiteCode": "base",
    "storeCode": "default",
    "storeViewCode": "main_website_store"
  }
}
```

## Problemen oplossen

### primaire id of secundaire id ontbreekt

- **Symptom:** De gebreken van Gegevens aan customerId/emailId in plaats van douanewaarden.
- **Oplossing:** verzeker zowel `primaryID` als `secondaryID` in het `profileAttributes` voorwerp worden geplaatst.

### Ongeldige hashwaarden

- **Symptom:** de waarden van de knoeiboel zijn leeg of misvormd.
- **Oplossing:** verifieer de brongebieden (`parent_id`, `entity_id`, `email`) bevatten geldige gegevens alvorens te hakken.

### Processors niet uitvoeren

- **Symptom:** de attributen van de Douane verschijnen niet in gebeurtenisgegevens.
- **Oplossing:** Controle dat de bewerkers behoorlijk binnen `events.xml` worden geregistreerd en de module wordt toegelaten.

### Experience Platform-schema komt niet overeen

- **Symptom:** de Gegevens verschijnen niet in de fouten van de Experience Platform of schemabevestiging.
- **Oplossing:** zorg ervoor dat het schema van Experience Platform de gebieden van de douaneidentiteit met correcte gegevenstypes omvat.
