---
title: Gebruikersinstelling
description: Uitgebreide Inventory management-bronnen instellen als winkels ter ondersteuning van de oplossing Winkelafhandeling voor Adobe Commerce.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, User Account, Tools and External Services
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Gebruikersinstelling

App-gebruikers voor winkelassistentie worden beheerd in Adobe Commerce. Deze gebruikers communiceren echter niet rechtstreeks met Adobe Commerce. Het gebruikersbeheer is geconfigureerd in Adobe Commerce om veilige verbindingen tussen Adobe Commerce en de app mogelijk te maken.

Het gebruikersmodel van de App van de Afhandeling van de Opslag wordt gescheiden van andere gebruikersmodellen van Adobe Commerce. De toepassing behoudt zijn eigen machtigingsmodel via gebruikersrollen en gebruikers die aan alle of specifieke locaties kunnen worden toegewezen. De volgende machtigingen worden ondersteund: Volgorde selecteren, Volgorde verzenden en Kwaliteitsreductie item (en annuleren).

>[!TIP]
>
>Voor beste resultaten, [ vorm uw verbinding ](connect-set-up-service.md) alvorens u gebruikers en toestemmingen voor de Vennoten van de Opslag toevoegt die de App van de Hulp van de Opslag gebruiken.

## Store Assist App - Gebruikersrollen

Tijdens de eerste gebruikersinstelling voor de app Winkelassistentie maakt u gebruikersrollen om gebruikersmachtigingen aan te passen aan de app Winkelassistentie. Bijvoorbeeld, kunt u verschillende rollen voor opslagmanagers en opslagvennoten tot stand brengen en verschillende rolmiddelen toewijzen om toestemmingen voor elk type van gebruiker te beheren.

Gebruikersrollen configureren vanuit **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]** .

### Rolinformatie

| **Gebied** | **Beschrijving** | **Reikwijdte** | **Vereist** |
|----------------------------|-------------------------|-----------|--------------|
| **[!UICONTROL Role Name]** | Schakel de gebruiker in of uit. | Algemeen | Ja |

### Rolresources

| **Gebied** | **Beschrijving** | **Reikwijdte** | **Vereist** |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Resource Access]** | Maak een lijst van de beschikbare toestemmingsgroepen die aan een gebruikersrol kunnen worden toegewezen. Op dit ogenblik, heeft de Oplossing van de Afhandeling van de Opslag geen verschillende toestemmingsniveaus die voor middelrollen worden bepaald. Alle gebruikersrollen hebben de zelfde middeltoegang. | Algemeen | Ja |

## Winkelassistentie - Gebruikersgegevens

Gebruikersprofielen voor winkelassistentie-apps beheren op basis van de beheersysteeminstellingen: **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]** .

| **Gebied** | **Beschrijving** | **Reikwijdte** | **Vereist** |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL is Active]** | Schakel de gebruiker in of uit. | Algemeen | Ja |
| **[!UICONTROL User Name]** | Gebruikersnaam gekoppeld aan gebruiker | Algemeen | Ja |
| **[!UICONTROL First Name]** | Voornaam gekoppeld aan gebruiker | Algemeen | Nee |
| **[!UICONTROL Last Name]** | Achternaam die aan de gebruiker is gekoppeld | Algemeen | Nee |
| **[!UICONTROL Role]** | Rol die aan de gebruiker is gekoppeld | Algemeen | Nee |
| **[!UICONTROL Access to all locations]** | Wijs gebruikers toegang tot alle winkels toe of selecteer afzonderlijke winkels. | Algemeen | Nee |
| **Landinstelling van de Interface** | Als uw winkel meerdere talen heeft, stelt u Interfacelocatie in op de taal die u wilt gebruiken voor de beheerinterface. | Algemeen | Nee |
| **Actief van** | Als u een begindatum wilt instellen, selecteert u het kalenderpictogram. | Algemeen | Nee |
| **Actief aan** | Stel de vervaldatum in door het kalenderpictogram te selecteren. Het instellen van een vervaldatum is handig als u tijdelijke gebruikers- of rolinwijzingen wilt instellen. Na de vervaldatum verandert de status van de gebruikersaccount in `Inactive` , maar de account kan nog steeds zo nodig worden bijgewerkt. | Algemeen | Nee |
