---
title: De oplossing voor winkelvervulling aansluiten
description: Bepaal de verbindingen tussen Adobe Commerce en de oplossing van de Behandeling van de Opslag. Maak een Adobe Commerce-integratie en autoriseer deze en voeg de gegevens van de opslagtegoedaccount toe aan de Adobe Commerce-serviceconfiguratie.
role: Admin, Developer
level: Intermediate
feature: Shipping/Delivery, Install, Configuration, User Account, Tools and External Services
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# De oplossing voor winkelvervulling aansluiten

Connect Store Fulfillment Services met Adobe Commerce door de vereiste verificatiereferenties en verbindingsgegevens toe te voegen aan Adobe Commerce Admin.

- **[vorm [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)** - creeer een integratie van Adobe Commerce voor de diensten van de Afhandeling van de Opslag en produceer de toegangstokens om inkomende verzoeken van de servers van de Afhandeling van de Opslag voor authentiek te verklaren.

- **[vormt rekeningsgeloofsbrieven voor de Diensten van de Afhandeling van de Opslag](#configure-store-fulfillment-account-credentials)** - voeg uw geloofsbrieven toe om Adobe Commerce met uw rekening van de Afhandeling van de Opslag te verbinden.

>[!NOTE]
>
>Voltooi de verbindingsconfiguratie en bevestig de verbinding met succes alvorens u begint te testen.

## Een Adobe Commerce-integratie maken

Als u Adobe Commerce wilt integreren met de service Afhandeling van winkel, maakt u een integratie met Commerce en genereert u toegangstokens die kunnen worden gebruikt voor het verifiëren van aanvragen van de servers van Store Fulfillment. U moet ook de Adobe Commerce [!UICONTROL Consumer Settings] -opties bijwerken om `The consumer isn't authorized to access %resources.` -responsfouten te voorkomen bij aanvragen van Adobe Commerce naar [!DNL Store Fulfillment] -services.

1. Creëer in de beheerfunctie de integratie voor winkeluitvoering.

   - De extensie een naam geven
   - Voer uw e-mailadres in
   - Wachtwoord voor beheerdersaccount invoeren

1. Vorm de toestemmingen van de Toegang van het Middel API voor de integratie met het volgende:

   - Verkoop > BOPIS Order-update
   - Systeem > Toepassingsmachtigingen opslaan

1. Genereer de toegangstokens voor verificatie door de integratie op te slaan en te activeren.

1. Kopieer en sla de toegangstokens op een veilige, gecodeerde locatie op.

1. Werk samen met uw accountmanager om de configuratie aan de kant Opslaan van tegoeden te voltooien en de integratie te autoriseren.

1. Schakel de optie Adobe Commerce [!UICONTROL Consumer Settings] in op [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] .

   - Ga vanuit de beheerfunctie naar **[!UICONTROL Stores]** > [!UICONTROL Configuration] > **[!UICONTROL Services]** > **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - Stel de optie [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] in op **[!UICONTROL Yes]** .

>[!IMPORTANT]
>
> Het integratietoken is specifiek voor de omgeving. Als u de database voor een omgeving herstelt met de brongegevens uit een andere omgeving (bijvoorbeeld het herstellen van productiegegevens uit een testomgeving), sluit u de tabel `oauth_token` uit van de databaseexport, zodat de details van het integratietoken tijdens de terugzetbewerking niet worden overschreven.


## Geef de gegevens van de opslagaccount op

Nadat u het innameformulier hebt ingevuld, wordt voor u een account gemaakt voor het ophalen van een Walmart-winkel. U ontvangt de volgende referenties wanneer deze beschikbaar zijn:

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (doorgaans hetzelfde als de bovenstaande configuratie)

Deze geloofsbrieven worden vereist om de Afhandeling van de Opslag te vormen en te gebruiken.

>[!NOTE]
>
>Het maken van een account kan enige tijd duren. Terwijl u op geloofsbrieven wacht, [ overzicht en vorm andere montages voor de oplossing van de Afhandeling van de Opslag ](service-config-settings-overview.md).

### Referenties toevoegen om verbinding te maken met Afhandeling van winkel

1. Vorm [ rekeningsgeloofsbrieven ](enable-general.md) voor de milieu&#39;s van de Productie en van Sandbox.

1. Ga vanuit Beheer naar **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. Voer de accountgegevens in die voor de **[!UICONTROL Production environment]** zijn opgegeven. Alle velden zijn verplicht.

1. Selecteer **[!UICONTROL Save Config]** .

1. Test de verbinding door **[!UICONTROL Validate Credentials]** te selecteren.

>[!NOTE]
>
>Als de geloofsbrieven ongeldig zijn, verifieer dat u de correcte waarden voor elke milieu inging en revalidate. Neem contact op met uw accountvertegenwoordiger als er nog steeds verbindingsproblemen zijn.
