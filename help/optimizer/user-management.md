---
title: Gebruikersbeheer
description: Leer hoe te om gebruikers in  [!DNL Adobe Commerce Optimizer] te beheren.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
source-git-commit: 02758aa5cc14af6d46bfc4bb7865fa37a787d4cb
workflow-type: tm+mt
source-wordcount: '458'
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

1. Navigeer aan de [ console Admin ](https://adminconsole.adobe.com), en teken binnen met uw Adobe ID.

1. Selecteer uw organisatie.

1. Op het [!UICONTROL **lusje van Producten**], onder [!UICONTROL **Producten en de Diensten**], selecteer [!UICONTROL **Adobe Commerce as a Cloud Service - Achterste**] product.

   ![ uitgezocht product ](../cloud-service/assets/backend.png){width="600" zoomable="yes"}

1. Selecteer [!UICONTROL **Admins**] tabel.

1. Klik [!UICONTROL **Admin**] toevoegen.

1. Ga de gebruikersbenaming of e-mailadres van de gebruikers in u als beheerders wilt toevoegen en [!UICONTROL **sparen**] klikken.

## Gebruikers, ontwikkelaars en beheerders van productprofielen toevoegen

>[!BEGINSHADEBOX  &quot;Eerste vereisten&quot;]
>
>De volgende provisioning is vereist voor gebruikersbeheer:

- IMS-organisatie ingericht voor [!DNL Adobe Commerce Optimizer]
- Een Adobe Experience Cloud-account in dezelfde IMS-organisatie met de systeem- of productbeheerrol

>[!ENDSHADEBOX]

Gebruik de volgende instructies om gebruikers en ontwikkelaars toe te voegen aan [!DNL Commerce Cloud Manager] , waar u uw Commerce-instanties beheert.

1. Navigeer aan [ Adobe Admin Console ](https://adminconsole.adobe.com) en teken binnen met uw Adobe ID.

1. Selecteer uw organisatie.

1. Op het [!UICONTROL **lusje van Producten**], onder [!UICONTROL **Producten en de Diensten**], selecteer [!UICONTROL **Adobe Commerce as a Cloud Service - Achterste**] product.

   ![ uitgezocht product ](../cloud-service/assets/backend.png){width="600" zoomable="yes"}

1. Klik het [!UICONTROL **Gebrek - het productprofiel van Cloud Manager**].

1. Selecteer de [!UICONTROL **Gebruikers**], [!UICONTROL **Ontwikkelaars**], of [!UICONTROL **Admins**] lusje en klik [!UICONTROL **voegt Gebruikers**] toe of [!UICONTROL **voegt Ontwikkelaars**] toe of [!UICONTROL **voegt Admins**] toe.

   Admins die van dit scherm worden toegevoegd worden toegewezen aan de [ groep van het productprofiel admins ](#understanding-roles).

   ![ uitgezochte lusje ](../cloud-service/assets/tab-select.png){width=600 zoomable="yes"}

1. Ga de gebruikersbenaming of e-mailadres van de gebruikers in u als beheerders wilt toevoegen en [!UICONTROL **sparen**] klikken.

## Bulkgebruikersbeheer

U kunt meerdere gebruikers efficiënter toevoegen met een van de volgende methoden:

- Gebruik **voegt Gebruikers door CSV** eigenschap in Adobe Admin Console toe om a [ bulkCSV uit te voeren uploadt ](https://helpx.adobe.com/enterprise/using/bulk-upload-users.html){target="_blank"}.
- Voeg veelvoudige gebruikers aan een rol toe door a [ gebruikersgroep ](https://helpx.adobe.com/enterprise/using/user-groups.html){target="_blank"} te creëren. Dan, voeg [!UICONTROL **Adobe Commerce as a Cloud Service toe - steun**] product aan de gebruikersgroep.

