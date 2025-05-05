---
title: Gebruikersbeheer
description: Leer hoe te om gebruikers in  [!DNL Adobe Commerce as a Cloud Service] te beheren.
source-git-commit: 25a0d658776ea95fcae07f6390abeeb559642613
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# Gebruikersbeheer

{{accs-early-access}}

Als u gebruikers tot Admin in [!DNL Adobe Commerce as a Cloud Service] wilt toegang hebben, moet u hen als gebruikers in uw organisatie toevoegen en ervoor zorgen zij toegang tot het product van Cloud Service in [ Adobe Admin Console ](https://adminconsole.adobe.com){target="_blank"}  hebben.

Voor dit proces is een IMS-organisatie met toegang tot [!DNL Adobe Commerce as a Cloud Service] vereist. Alleen een systeembeheerder of productbeheerder voor de organisatie kan deze processen uitvoeren.

>[!TIP]
>
>Om veelvoudige gebruikers gelijktijdig toe te voegen, kunt u a [ bulkupload CSV ](https://helpx.adobe.com/nl/enterprise/using/bulk-upload-users.html){target="_blank"} uitvoeren .
> 
> U kunt veelvoudige gebruikers aan een rol ook toevoegen door a [ gebruikersgroep ](https://helpx.adobe.com/nl/enterprise/using/user-groups.html){target="_blank"}  te creëren. Dan kunt u [!UICONTROL **Adobe Commerce as a Cloud Service toevoegen - 1&rbrace; product van de Achtergrond aan de gebruikersgroep.**]

## Rollen begrijpen

De volgende rollen zijn beschikbaar voor [!DNL Adobe Commerce as a Cloud Service]. Om deze rollen te bekijken of uit te geven, in Commerce Admin navigeert aan **Systeem** > **Toestemmingen** > **Rollen van de Gebruiker**.

* **Gebruikers** - de gebruikers hebben toegang Admin tot Commerce Admin, maar kunnen toegang op productniveau in Admin Console niet beheren. De gebruikers kunnen credits ook gebruiken om [ instanties ](./getting-started.md#create-an-instance) in [!DNL Commerce Cloud Manager] tot stand te brengen.

* [**Ontwikkelaars** ](https://helpx.adobe.com/nl/enterprise/using/manage-developers.html#Adddevelopers){target="_blank"}  de Ontwikkelaars hebben gebruikerstoestemmingen en aan de instantie van Commerce als ontwikkelaarsgebruiker toegevoegd. Dit betekent zij [ Admin UI SDK ](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/){target="_blank"}  kunnen gebruiken, [ vormen gebeurtenissen ](https://developer.adobe.com/commerce/extensibility/events/){target="_blank"} , en [ creëren webhooks ](https://developer.adobe.com/commerce/extensibility/webhooks/){target="_blank"} .

* Beheerders - Er zijn drie verschillende typen beheerders:
   * [ beheert het Systeem ](https://helpx.adobe.com/nl/enterprise/using/admin-roles.html){target="_blank"}  - het systeem admin heeft toegang tot alle producten en productprofielen in de organisatie door Admin Console.
   * [ Admins van het Product ](#add-a-product-admin) - de beheerders van het Product kunnen [ gebruikers, rollen, en toestemmingen voor het product ](#add-users-and-admins) in [!DNL Adobe Admin Console] beheren en [ gebruikers in Commerce beheren Admin ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/user-accounts/permissions-users-all#create-a-user){target="_blank"} .
   * [ het profielbeheerders van het Product ](#add-users-developers-and-product-profile-admins) - de profielbeheerders van het Product hebben geen toegang tot Adobe Commerce Admin, maar kunnen gebruikers voor het product in [!DNL Adobe Admin Console] beheren.

Voor gedetailleerde informatie over de toestemmingen die aan elke rol binnen Adobe Commerce worden verleend, verwijs naar [ gebruikerstoestemmingen ](#user-permissions).

## Een productbeheerder toevoegen

1. Ga naar https://adminconsole.adobe.com en meld u aan met uw Adobe ID.

1. Selecteer uw organisatie.

1. Op het [!UICONTROL **lusje van Producten**], onder [!UICONTROL **Producten en de Diensten**], selecteer [!UICONTROL **Adobe Commerce as a Cloud Service - Achterste**] product.

   ![ uitgezocht product ](./assets/backend.png){width="600" zoomable="yes"}

1. Selecteer [!UICONTROL **Admins**] tabel.

1. Klik [!UICONTROL **Admin**] toevoegen.

1. Ga de gebruikersbenaming of e-mailadres van de gebruikers in u als beheerders wilt toevoegen en [!UICONTROL **sparen**] klikken.

## Gebruikers, ontwikkelaars en beheerders van productprofielen toevoegen

De volgende instructies geven informatie over het toevoegen van gebruikers en ontwikkelaars aan de [!DNL Commerce Cloud Manager] en Commerce Admin. Met de interface van [!DNL Commerce Cloud Manager] kunt u Commerce-instanties maken en beheren.

>[!NOTE]
>
>Alleen productbeheerders en systeembeheerders kunnen gebruikers en ontwikkelaars toevoegen aan het Adobe Commerce as a Cloud Service-product.

1. Ga naar https://adminconsole.adobe.com en meld u aan met uw Adobe ID.

1. Selecteer uw organisatie.

1. Op het [!UICONTROL **lusje van Producten**], onder [!UICONTROL **Producten en de Diensten**], selecteer [!UICONTROL **Adobe Commerce as a Cloud Service - Achterste**] product.

   ![ uitgezocht product ](./assets/backend.png){width="600" zoomable="yes"}

1. Klik het [!UICONTROL **Gebrek - het productprofiel van Cloud Manager**].

1. Selecteer de [!UICONTROL **Gebruikers**], [!UICONTROL **Ontwikkelaars**], of [!UICONTROL **Admins**] lusje en klik [!UICONTROL **voegt Gebruikers**] toe of [!UICONTROL **voegt Ontwikkelaars**] toe of [!UICONTROL **voegt Admins**] toe.

   >[!NOTE]
   >
   >Admins die van dit scherm worden toegevoegd zijn [ productprofielbeheerders ](#understanding-roles) en hebben geen toegang tot Commerce Admin.

   ![ lusje uitgezocht ](./assets/tab-select.png){width=600 zoomable= &quot;ja&quot;}

1. Ga de gebruikersbenaming of e-mailadres van de gebruikers in u als beheerders wilt toevoegen en [!UICONTROL **sparen**] klikken.

## Rolresources

In de volgende lijst worden de bronnen beschreven waartoe standaardrollen toegang hebben binnen Adobe Commerce Admin. Om de standaardtoestemmingen voor elke rol uit te geven, navigeer aan **Systeem** > **Toestemmingen** > **Rollen van de Gebruiker** in Commerce Admin.

**Gebruikers**

* Catalogus
   * Inventaris
      * Producten
         * Productprijs lezen

**Ontwikkelaars**

* Catalogus
   * Inventaris
      * Producten
         * Productprijs lezen
* Systeem
   * Gegevensoverdracht
      * Historie importeren
* Adobe IO Events Configuration
   * Configuratiecontrole
   * Gebeurtenisprovider maken
   * Configuratie-update
   * Gebeurtenissen synchroniseren
   * Lijst met gebeurtenisproviders ophalen
* Eindkader
   * Gebeurtenislijst
   * Verbinding met gebeurtenis testen
   * Abonneren op een gebeurtenis
   * Abonnement op een gebeurtenis opzeggen
   * Status van gebeurtenis
   * API om gebeurtenisabonnementen op te halen
   * Gebruikersinterface voor abonnementen op gebeurtenissen weergeven
   * Gebruikersinterface voor beheerder van abonnementen voor gebeurtenissen maken
   * Nieuwe interface voor gebeurtenisbeheer aanvragen
* Webhaken
   * Webhooks digitale handtekening
      * Instellingen voor webhooks digitale handtekening
      * Webhaks Digital Signature Generate Keys
   * Webhakbeheer
      * Webhakenraster
      * Webhooks bewerken
      * Webhaken testen
      * API-abonnement op webhaak
      * API-abonnement van webhaak
      * Webhakenlijst
      * Nieuwe webhaak aanvragen
      * Webhooks Logs
      * Lijst met webhaken ophalen

**Admins**

Beheerders hebben toegang tot alle machtigingen.
