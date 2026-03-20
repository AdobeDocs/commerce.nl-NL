---
title: E-mailactivering via REST
description: Leer hoe te om transactie e-mails op bestelling teweeg te brengen gebruikend REST API door een malplaatjeidentiteitskaart, ontvankelijke e-mail, en malplaatjevariabelen voor  [!DNL Adobe Commerce as a Cloud Service] te specificeren.
role: Admin
level: Experienced
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 9661e368f7a0dc85edcd3e52a67ae2a98355d8b5
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# E-mailactivering via de REST API

Eerder kon u alleen e-mailberichten verzenden wanneer gebeurtenissen werden gestart, zoals tijdens de registratie van klanten of de aankoop van bestellingen. In [!DNL Adobe Commerce as a Cloud Service] kunt u e-mailberichten verzenden via de REST API op verzoek door een sjabloon-id, een e-mailbericht voor ontvangers en sjabloonvariabelen op te geven.

>[!NOTE]
>
>Momenteel kunnen alleen nieuwe, aangepaste sjablonen worden verzonden. Vooraf gedefinieerde en systeemsjablonen worden niet ondersteund.

Het `V1/custom-email/send` eindpunt staat **derdesystemen**, zoals integratie en de externe diensten toe, om e-mail op bestelling te verzenden door te specificeren:

- **identiteitskaart van het Malplaatje** - E-mail malplaatjeidentiteitskaart
- **Ontvankelijke e-mail** - het doel e-mailadres voor dit verzoek.
- **Variabelen** - (Facultatieve) Gedefinieerde sleutel-waarde paren om in het malplaatje, zoals `customer_name` of `order_id` te injecteren.

>[!NOTE]
>
>E-mail wordt verzonden synchroon gebruikend het huidige opslagwerkingsgebied en het gebrek **Van** e-mailadres of het e-mailadres dat voor malplaatjes wordt bepaald.

## REST-contract

In de volgende sectie wordt uitgelegd hoe u transactie-e-mails op aanvraag kunt verzenden met de REST API.

### Endpoint

- **URL** - `POST /rest/V1/custom-email/send`
- **Vergunning** - slechts **de dienst-aan-dienst vergunning IMS** wordt gesteund. De bezoeker moet toegang tot **hebben verzendt Eigen E-mail van de Douane via API** (`Magento_CustomEmailSend::send_custom_email`) middel. Verwijs naar [&#x200B; authentificatie van het REST &#x200B;](https://developer.adobe.com/commerce/webapi/rest/authentication/) voor meer informatie.
- **gebruik Async** (geadviseerd) - hoewel dit eindpunt synchroon wordt uitgevoerd, adviseren wij roepend het gebruikend **asynchrone REST API** zodat het verzoek een rij wordt gevormd en door een consument wordt verwerkt, vermijdend de verbindingen van lang-levend HTTP. In [!DNL Adobe Commerce as a Cloud Service] kunt u de route gebruiken met `/async` after `V1` , bijvoorbeeld: `POST https://<server>.api.commerce.adobe.com/<tenant-id>/V1/async/custom-email/send` .

  Verwijs naar [&#x200B; Asynchrone Webeindpunten (SaaS) &#x200B;](https://developer.adobe.com/commerce/webapi/rest/use-rest/asynchronous-web-endpoints/) voor meer informatie.

### Aanvragingsinstantie

- **templateId** (interger, vereist) - E-mail malplaatjeidentiteitskaart zoals die in Admin onder [!UICONTROL **wordt bepaald Marketing**] > [!UICONTROL _Mededelingen_] > [!UICONTROL **E-mailMalplaatjes**].

- **receivingEmail** (koord, vereist) - het doel e-mailadres. Dit moet een geldige e-mailindeling zijn. Bij ontbrekende of lege waarden treedt een validatiefout op.
- **variabelen** (voorwerp, facultatief) - sleutel-waarde kaart die in het malplaatje als `UnstructuredArray` wordt ingespoten.

  Wanneer u geen variabelen gebruikt, geeft u een leeg object door of laat u dit weg. Gebruik in de hoofdtekst en het onderwerp van de e-mailsjabloon de syntaxis van de variabele om naar een variabele te verwijzen, bijvoorbeeld `var order_id` . Het onderwerp steunt ook de zelfde douanevariabelen en syntaxis die in [&#x200B; worden beschreven Gesteunde malplaatjescenario&#39;s &#x200B;](#supported-template-scenarios).

### Succesreactie (HTTP 200)

De API retourneert HTTP 200 bij succesvol verzenden.

### Foutreacties

- **HTTP 400 - de fout van de Bevestiging**

  De integratie moet voor elke aanvraag een geldige waarde `templateId` en `recipientEmail` opgeven.

   - `"message": "Invalid recipient email format"` - ongeldig of onjuist geadresseerd adres
   - `"message": "Recipient email is required."` - ontbreekt of is leeg `recipientEmail`
   - `"message": "Template ID must be a positive integer."` - ontbreekt, nul of ongeldig `templateId`

- **HTTP 404 - Malplaatje niet gevonden**

  Voorbeeld: `"message": "Email template with ID \"999\" does not exist."`

## Ondersteunde sjabloonscenario&#39;s

De volgende malplaatjeeigenschappen worden gesteund in zowel het **e-maillichaam** als het **malplaatjeonderwerp**:

>[!NOTE]
>
>Het sjabloononderwerp ondersteunt ook aangepaste variabelen. Gebruik `var variableName` en andere syntaxis zoals beschreven in de volgende sectie.

- **omvat richtlijn** - om andere ontwerpmalplaatjes, zoals een e-mailkopbal te omvatten.

  ```javascript
  {{template config_path="design/email/header_template"}}
  ```

- **Eenvoudige variabelen** - gebruik `var variableName`, bijvoorbeeld `var order_id` of `var g`.

  ```javascript
  {{var order.test}}
  {{var g}}
  {{var order_id}}
  ```

- **Geneste/stipaantekening** - voor genestelde sleutels die in het verzoek `variables` worden overgegaan, in vertalingen gebruiken dollar-vooraf vastgestelde namen, zoals `$order_data.customer_name`, `$order.increment_id`, of `$order_data.frontend_status_label`.

  ```javascript
  {{trans "%name," name=$order_data.customer_name}}
  {{trans "Your order #%increment_id has been updated with a status of **%order_status**." increment_id=$order.increment_id order_status=$order_data.frontend_status_label |raw}}
  ```

- **Vertaling (trans)** - de parameters bepaalde tekst, multi-line vertalingen met veelvoudige placeholders en de markeringen van HTML.

  ```javascript
  {{trans "%name," name=$order_data.customer_name}}
  {{trans "Your order #%increment_id has been updated with a status of **%order_status**." increment_id=$order.increment_id order_status=$order_data.frontend_status_label |raw}}
  ```

- **Ruwe output** - gebruik de `|raw` filter wanneer de vertaalde of veranderlijke inhoud HTML (bijvoorbeeld, `<strong>` of `<a>`) bevat.

  ```javascript
  {{trans "Your order #%increment_id has been updated with a status of **%order_status**." increment_id=$order.increment_id order_status=$order_data.frontend_status_label |raw}}
  ```

- **hulp URL** - voor opslag URLs binnen vertalingen.

  ```javascript
  {{trans 'You can check the status of your order by [logging into your account](%account_url).' account_url=$this.getUrl($store,'customer/account/',[_nosid:1]) |raw}}
  ```
