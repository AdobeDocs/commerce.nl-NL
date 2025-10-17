---
title: Gebruiker en Identity Management
description: Leer om gebruikers tot stand te brengen en te beheren en gebruikersrollen voor  [!DNL Adobe Commerce Optimizer] toe te wijzen.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: 9ab2118d-b7e3-4e2e-adac-8f3950fe1824
source-git-commit: b88406169191cb9d4f0d2b5ef113703f5afcd589
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---

# Gebruikersbeheer

Om toegang tot [!DNL Adobe Commerce Optimizer] toe te laten, voeg gebruikers van [ Adobe Admin Console ](https://adminconsole.adobe.com){target="_blank"} toe en zorg ervoor dat zij toegang tot het product van Commerce hebben.

U kunt gebruikers aan om het even welke volgende rollen toewijzen:

- **Gebruiker** - de gebruikers hebben toegang tot [!DNL Adobe Commerce Optimizer] UI om catalogusmeningen en het verhandelen regels te bekijken en te beheren, en prestatiesmetriek te volgen.

- [**Ontwikkelaar** ](https://helpx.adobe.com/enterprise/using/manage-developers.html#Adddevelopers){target="_blank"} - de Ontwikkelaars hebben gebruikerstoestemmingen en toegang tot Adobe Developer Console. Dit betekent dat zij projecten kunnen maken en referenties kunnen configureren voor het gebruik van ontwikkelaarsgereedschappen zoals de API&#39;s en SDK&#39;s van [!DNL Adobe Commerce Optimizer] en uitbreidbaarheidsprogramma&#39;s van Adobe, zoals App Builder en API Mesh.

- **Admin** - er zijn drie verschillende soorten admin rollen:
   - [ beheerders van het Systeem ](https://helpx.adobe.com/enterprise/using/admin-roles.html){target="_blank"} - het systeemadmin heeft toegang tot alle producten en productprofielen in de organisatie door Adobe Admin Console.
   - [ Admins van het Product ](#add-a-product-admin) - de beheerders van het Product kunnen [ gebruikers, rollen, en toestemmingen voor het product ](#add-users-and-admins) in [!DNL Adobe Admin Console] beheren.
   - [ het profielbeheerders van het Product ](#add-users-developers-and-product-profile-admins) - de profielbeheerders van het Product kunnen gebruikers voor het product in [!DNL Adobe Admin Console] beheren.

## Een productbeheerder toevoegen

>[!BEGINTABS]

>[!NOTE]
>
>Wijs product toe beheert de [ rol van de Gebruiker ](#add-users) alvorens hen als productbeheerders toe te voegen. De gebruikersrol is vereist voor eenvoudige Commerce-machtigingen.

>[!TAB  GA (die na 13 oktober, 2025 wordt voorzien) ]

1. Navigeer naar <https://adminconsole.adobe.com> en meld u aan met uw Adobe ID.

1. Selecteer uw organisatie.

1. Selecteer de [!UICONTROL **Gebruikers**] tabel.

1. Selecteer de [!UICONTROL **Beheerders**] tabel.

1. Klik [!UICONTROL **Admin**] toevoegen.

1. Ga de gebruikersbenaming of e-mailadres van de gebruikers in u als beheerders wilt toevoegen en [!UICONTROL **daarna**] klikken.

1. Selecteer de [!UICONTROL **rol van de de profielbeheerder van het Product**].

1. Klik op **+** om producten toe te voegen.

1. Selecteer de bestaande Commerce Optimizer-instantie waaraan u de beheerder wilt toevoegen. Commerce Optimizer-instanties gebruiken de volgende indeling: `Adobe Commerce - <instance-name> - ACO - <environment-type> - <tenant-id>`.

1. Selecteer het productprofiel.

1. Klik [!UICONTROL **toepassen**].

1. Klik [!UICONTROL **sparen**].

>[!TAB  Vroege toegang (die vóór 13 Oktober, 2025 wordt voorzien) ]

1. Navigeer naar <https://adminconsole.adobe.com> en meld u aan met uw Adobe ID.

1. Selecteer uw organisatie.

1. Op het [!UICONTROL **lusje van Producten**], onder [!UICONTROL **Producten en de Diensten**], selecteer [!UICONTROL **Adobe Commerce - de Manager van Commerce Cloud**] product.

   ![ uitgezocht product ](/help/cloud-service/assets/backend.png){width="600" zoomable="yes"}

1. Selecteer [!UICONTROL **Admins**] tabel.

1. Klik [!UICONTROL **Admin**] toevoegen.

1. Ga de gebruikersbenaming of e-mailadres van de gebruikers in u als beheerders wilt toevoegen en [!UICONTROL **sparen**] klikken.

>[!ENDTABS]

## Gebruikers toevoegen

De volgende instructies geven informatie over het toevoegen van gebruikers aan de [!DNL Commerce Cloud Manager] en de Commerce Optimizer. Met de interface van [!DNL Commerce Cloud Manager] kunt u Commerce Optimizer-instanties maken en beheren. Dit proces is vereist voor alle gebruikers, inclusief ontwikkelaars en beheerders.

>[!NOTE]
>
>Alleen productbeheerders en systeembeheerders kunnen gebruikers en ontwikkelaars toevoegen aan het Adobe Commerce Optimizer-product.

>[!BEGINTABS]

>[!TAB  GA (die na 13 oktober, 2025 wordt voorzien) ]

1. Navigeer naar <https://adminconsole.adobe.com> en meld u aan met uw Adobe ID.

1. Selecteer uw organisatie.

1. Selecteer de [!UICONTROL **Producten**] tabel.

1. Selecteer het [!UICONTROL **Adobe Commerce**] product.

1. Selecteer het Commerce Cloud Manager-product als u de gebruiker wilt toevoegen aan de interface van de cloud Manager, waar ze Commerce Optimizer-instanties kunnen maken en beheren, of selecteer de bestaande Commerce Optimizer-instantie waaraan de gebruiker moet worden toegevoegd. Commerce Optimizer-instanties gebruiken de volgende indeling: `Adobe Commerce - <instance-name> - ACO - <environment-type> - <tenant-id>`.

1. Selecteer het [!UICONTROL **lusje van Gebruikers**] en klik [!UICONTROL **toevoegen Gebruikers**].

1. Ga de gebruikersbenaming of e-mailadres van de gebruikers in u [!UICONTROL **sparen**] wilt toevoegen en klikken.

1. Selecteer het gewenste productprofiel.

1. Klik [!UICONTROL **toepassen**].

1. Klik [!UICONTROL **sparen**].

>[!TAB  Vroege toegang (die vóór 13 Oktober, 2025 wordt voorzien) ]

1. Navigeer naar <https://adminconsole.adobe.com> en meld u aan met uw Adobe ID.

1. Selecteer uw organisatie.

1. Op het [!UICONTROL **lusje van Producten**], onder [!UICONTROL **Producten en de Diensten**], selecteer [!UICONTROL **Adobe Commerce - de Manager van Commerce Cloud**] product.

   ![ uitgezocht product ](/help/cloud-service//assets/backend.png){width="600" zoomable="yes"}

1. Klik het [!UICONTROL **Gebrek - het productprofiel van Cloud Manager**].

1. Selecteer het [!UICONTROL **lusje van Gebruikers**] en klik [!UICONTROL **toevoegen Gebruikers**].

   ![ uitgezochte lusje ](/help/cloud-service/assets/tab-select.png){width=600 zoomable="yes"}

1. Ga de gebruikersbenaming of e-mailadres van de gebruikers in u [!UICONTROL **sparen**] wilt toevoegen en klikken.

>[!ENDTABS]

### Ontwikkelaars en beheerders van productprofielen toevoegen

Om ontwikkelaars en productprofielbeheerders toe te voegen, herhaal [ gebruikers ](#add-users) proces toevoegen, maar selecteer [!UICONTROL **Ontwikkelaars**] of [!UICONTROL **Admins**] lusje in plaats van het [!UICONTROL **Gebruikers**] lusje.

>[!NOTE]
>
>Wijs ontwikkelaars de rol van de Gebruiker toe alvorens hen als ontwikkelaars toe te voegen. De gebruikersrol is vereist voor eenvoudige Commerce-machtigingen.

![ uitgezochte lusje ](/help//cloud-service/assets/tab-select.png){width=600 zoomable="yes"}

## Bulkgebruikersbeheer

U kunt meerdere gebruikers efficiënter toevoegen met een van de volgende methoden:

- Gebruik **voegt Gebruikers door CSV** eigenschap in Adobe Admin Console toe om a [ bulkCSV uit te voeren uploadt ](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html){target="_blank"}.
- Voeg veelvoudige gebruikers aan een rol toe door a [ gebruikersgroep ](https://helpx.adobe.com/enterprise/using/user-groups.html){target="_blank"} te creëren. Dan, voeg [!UICONTROL **Adobe Commerce toe - de Manager van Commerce Cloud**] product aan de gebruikersgroep.

## Identiteitsbeheer en Single Sign-On configuratie

{{ims-identity-and-sso-config}}
