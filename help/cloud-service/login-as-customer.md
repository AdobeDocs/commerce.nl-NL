---
title: Aanmelden als klant met eenmalige codes
description: Leer hoe te om Login als eigenschap van de Klant te gebruiken OTC om éénmalige codes voor klantenauthentificatie in  [!DNL Adobe Commerce as a Cloud Service] te produceren.
role: Admin
level: Intermediate
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 160180d9d779514f6faee3c7de46531ebf191c7d
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 0%

---

# Aanmelden als klant

{{accs-sandbox-experimental}}

Met de functie Aanmelden als otc-code voor klant (One-Time Code) kunnen beheerders code voor een klant genereren voor eenmalig gebruik van korte duur. Deze code kan voor een teken van de klantentoegang door GraphQL worden geruild, toelatend wachtwoord **Login als de werkschema&#39;s van de Klant** voor verkoper-gesteunde het winkelen scenario&#39;s.

Aanmelden als klant bestaat uit de volgende componenten:

* **Admin UI** - op de klant geeft pagina uit, kunnen de beheerders om een éénmalige code (OTC) in plaats van direct het programma openen als klant verzoeken.
* **REST API** - een programmatic eindpunt voor OTC generatie, nuttig voor admin manuscripten en derdesintegratie.
* **GraphQL API** - Mutaties die een OTC voor een teken van de klantentoegang voor opslag of headless handelsstromen ruilen.

## Een eenmalige code genereren via de beheerder

De login als OTC van de Klant vervangt standaardlogin als klantenknoop op de klant uitgeeft pagina met a [!UICONTROL **krijgt OTC van de Klant**] knoop Login. De gegenereerde eenmalige code kan vervolgens worden gebruikt met de winkel of GraphQL voor winkelen met hulp van verkopers.

>[!NOTE]
>
>De **Login als Klant** knoop is niet beschikbaar op de Orde, Factuur, Verzending, en de pagina&#39;s van het Memo van de Krediet.

### Vereisten

U moet aan de volgende vereisten voldoen alvorens het login als klanteneigenschap te gebruiken:

* **Admin toestemming** - de admin gebruiker moet de `Magento_LoginAsCustomer::login` toestemming hebben van de Lijst van het Toegangsbeheer (ACL) die in hun admin rol wordt toegelaten om als klant aan te melden.

* **toestemming van de Klant** - de klant moet de `login_as_customer_assistance_allowed` uitbreidingsattributen hebben die aan **worden geplaatst 2**. Dit kan op **worden gevormd geeft Klant** pagina in Admin of door GraphQL uit wanneer het creëren van of het uitgeven van een klant.

  ![ de attributenconfiguratie van de de toestemmingsuitbreiding van de Klant op de Edit pagina van de Klant ](./assets/customer-consent-attribute.png){width="600" zoomable="yes"}

* **Login als toegelaten uitbreiding van de Klant** - login als klantenfunctionaliteit is niet beschikbaar wanneer login als klantenuitbreiding gehandicapt is. Om de uitbreiding te verifiëren wordt toegelaten, navigeer aan [!UICONTROL **Opslag**] > [!UICONTROL **Configuratie**] > [!UICONTROL **Klanten**] > [!UICONTROL **Login als Klant**] > [!UICONTROL **toelaat Uitbreiding**].

### Een eenmalige code aanvragen (OTC)

1. Navigeer aan [!UICONTROL **Klanten**] en selecteer een klant om uit te geven pagina te openen.

1. Voor de Edit pagina van de Klant, klik [!UICONTROL **krijgt de Login OTC van de Klant**].

   ![ krijgt de OTC knoop van de Login van de Klant op de Edit pagina van de Klant ](./assets/get-customer-login-otc-button.png){width="600" zoomable="yes"}

1. Ga a [!UICONTROL **(vereiste) Reden van 0} in en klik**] Verzoek [!UICONTROL **.**]

   ![ OTC verzoek modaal met het gebied van de Reden ](./assets/otc-reason-modal.png){width="600" zoomable="yes"}

   >[!NOTE]
   >
   >Het **gebied van de Reden** wordt vereist. Het wordt overgegaan tot de OTP generatiestroom en is gereserveerd voor gebruik in komende controle en gebeurtenisregistrereneigenschappen.

1. De gegenereerde OTC wordt weergegeven in het modaal. Gebruik deze code met de `generateCustomerToken` - of `exchangeOtpForCustomerToken` GraphQL-mutatie voor toestemming van de klant.

   ![ Gegenereerde OTC die in modaal ](./assets/otc-generated-code.png){width="300" zoomable="yes"} wordt getoond

>[!IMPORTANT]
>
>De gegenereerde One-Time Code OTC is standaard 30 seconden geldig en wordt na één gebruik ongeldig gemaakt. De TTL kan via CPS worden gevormd gebruikend het `customer/otp/ttl_seconds` plaatsen.

Nadat de Eenmalige Code wordt geproduceerd, kunt u het gebruiken door aan uw storefront te navigeren en het programma te openen gebruikend de volgende geloofsbrieven:

* **E-mail**: Het e-mailadres van de klant
* **Wachtwoord**: De geproduceerde Eenmalige Code (OTC)

## Een eenmalige code genereren met de REST API

Het POST `V1/customer/:customerId/otp` eindpunt verstrekt een programmatische manier om een OTC voor een klant te produceren. Dit is handig voor gebruikersinterface&#39;s voor beheerders, scripts of integratie van derden die een consistente OTC-afgifte moeten activeren.

### REST-contract

| Item | Waarde |
|---|---|
| **Methode** | POST |
| **URL** | `/rest/V1/customer/:customerId/otp` |
| **Authentificatie** | Admin-token (Drager). Vereiste ACL: `Magento_LoginAsCustomer::login`. |
| **het lichaam van het Verzoek** | JSON met optioneel veld `reason` . Wordt gebruikt voor controle en registratie. |
| **de reactie van het Succes** | HTTP 200, JSON met `otp` (hexadecimale tekenreeks van 32 tekens). |
| **Reacties van de Fout** | Standaard Web API-fouten (bijvoorbeeld 401, 403). Als de aanmelding als hulp van de klant is uitgeschakeld, kan deze de waarde 500 of een toegewezen uitzondering hebben. |

### Voorbeeld aanvragen

```text
POST /rest/V1/customer/:customerId/otp
Content-Type: application/json
```

```json
{"reason": "Support session"}
```

### Voorbeeld van reactie

```json
{"otp": "a1b2c3d4e5f6789012345678abcdef01"}
```

## Een eenmalige code uitwisselen voor een klanttoken met GraphQL

Nadat u een OTC hebt gegenereerd (via de interface van Admin of de REST-API), gebruikt u een van de volgende GraphQL-mutaties om deze uit te wisselen voor een token voor klanttoegang.

### `generateCustomerToken` mutatie

De mutatie `generateCustomerToken(email, password)` retourneert een klanttoken. Het argument `password` wordt in de volgende volgorde geëvalueerd:

1. **het wachtwoord van de Klant (gebrek)** - het de rekeningswachtwoord van de klant.
1. **Token van het Wachtwoord van het Terugstellen van de Klant (eenmalig gebruik)** - Een geldig teken van **vergeten wachtwoord** (bijvoorbeeld, de `requestPasswordResetEmail` mutatie). Verbruid bij eerste gebruik.
1. **Admin-Gegenereerde OTC (éénmalige code)** - een code die door admin voor de klant door REST API of Admin UI wordt geproduceerd. Eenmalig gebruik, kort (standaard 30 seconden).

**Schema:**

```graphql
type Mutation {
  generateCustomerToken(email: String!, password: String!): CustomerToken
}

type CustomerToken {
  token: String!
}
```

**Voorbeeld: login met admin OTC**

```graphql
mutation GenerateCustomerToken($email: String!, $password: String!) {
  generateCustomerToken(email: $email, password: $password) {
    token
  }
}
```

Variabelen (gebruik de OTC als `password`):

```json
{
  "email": "customer@example.com",
  "password": "<admin-generated-OTC>"
}
```

**Voorbeeld: login met wachtwoord**

```graphql
mutation GenerateCustomerToken($email: String!, $password: String!) {
  generateCustomerToken(email: $email, password: $password) {
    token
  }
}
```

Variabelen:

```json
{
  "email": "customer@example.com",
  "password": "CustomerPassword123"
}
```

**Voorbeeld: login met het teken van het wachtwoordterugstellen**

Nadat de klant om het opnieuw instellen van het wachtwoord heeft gevraagd (bijvoorbeeld `requestPasswordResetEmail` ), kan het terugstellingstoken dat via de e-mailkoppeling is ontvangen, worden gebruikt als `password` in `generateCustomerToken` (eenmalig gebruik).

```graphql
mutation GenerateCustomerToken($email: String!, $password: String!) {
  generateCustomerToken(email: $email, password: $password) {
    token
  }
}
```

Variabelen (gebruik de hersteltoken als `password`):

```json
{
  "email": "customer@example.com",
  "password": "<reset-password-token-from-email-link>"
}
```

**reactie van het Voorbeeld:**

```json
{
  "data": {
    "generateCustomerToken": {
      "token": "<customer-access-token>"
    }
  }
}
```

### `exchangeOtpForCustomerToken` mutatie

De `exchangeOtpForCustomerToken` mutatie ruilt een teken van het wachtwoordterugstellings of OTP die door admin voor een teken van de klantentoegang wordt geproduceerd. OTP wordt ongeldig gemaakt na succesvolle uitwisseling (eenmalig gebruik). Dit eindpunt eerbiedigt de configuratie reCAPTCHA.

**Schema:**

```graphql
type Mutation {
  exchangeOtpForCustomerToken(
    email: String!
    otp: String!
  ): CustomerToken
}

type CustomerToken {
  token: String!
}
```

**Verzoek van het Voorbeeld:**

```graphql
mutation ExchangeOtpForCustomerToken($email: String!, $otp: String!) {
  exchangeOtpForCustomerToken(email: $email, otp: $otp) {
    token
  }
}
```

Variabelen:

```json
{
  "email": "customer@example.com",
  "otp": "<one-time-password>"
}
```

**reactie van het Voorbeeld:**

```json
{
  "data": {
    "exchangeOtpForCustomerToken": {
      "token": "<customer-access-token>"
    }
  }
}
```

### Samenvatting van de mutatie

| Mutatie | Hoofdletters gebruiken |
|---|---|
| `generateCustomerToken(email, password)` | Eén ingangspunt: klantwachtwoord, Wachtwoord opnieuw instellen token, Admin OTC of OTP (geprobeerd na wachtwoord/reset). |
| `exchangeOtpForCustomerToken(email, otp)` | OTP of de Symbolische uitwisseling van het Wachtwoord van het Terugstellen. OTP (of het Token van het Wachtwoord van het Terugstellen) wordt verbruikt na gebruik. |

Token voor opnieuw instellen van wachtwoorden en OTC voor beheer worden beide doorgegeven als het argument `password` aan `generateCustomerToken` . De oplosser detecteert het tokentype en valideert dienovereenkomstig.
