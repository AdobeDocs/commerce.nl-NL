---
title: Gebruiker en Identity Management
description: Leer om gebruikers tot stand te brengen en te beheren en gebruikersrollen voor  [!DNL Adobe Commerce Optimizer] toe te wijzen.
badgeSaas: label="Alleen SaaS" type="Positive" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."
exl-id: 9ab2118d-b7e3-4e2e-adac-8f3950fe1824
source-git-commit: 423d6f3fb544fb33b8e4e689fdfbbb3cf5b700f3
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---

# Gebruikersbeheer

Om toegang tot [!DNL Adobe Commerce Optimizer] toe te laten, voeg gebruikers van [&#x200B; Adobe Admin Console &#x200B;](https://adminconsole.adobe.com){target="_blank"} toe en zorg ervoor dat zij toegang tot het product van Commerce hebben.

U kunt gebruikers aan om het even welke volgende rollen toewijzen:

- **Gebruiker** - de gebruikers hebben toegang tot [!DNL Adobe Commerce Optimizer] UI om catalogusmeningen en het verhandelen regels te bekijken en te beheren, en prestatiesmetriek te volgen.

- [**Ontwikkelaar** &#x200B;](https://helpx.adobe.com/nl/enterprise/using/manage-developers.html#Adddevelopers){target="_blank"} - de Ontwikkelaars hebben gebruikerstoestemmingen en toegang tot Adobe Developer Console. Dit betekent dat zij projecten kunnen maken en referenties kunnen configureren voor het gebruik van ontwikkelaarsgereedschappen zoals de API&#39;s en SDK&#39;s van [!DNL Adobe Commerce Optimizer] en uitbreidbaarheidsprogramma&#39;s van Adobe, zoals App Builder en API Mesh.

- **Admin** - er zijn drie verschillende soorten admin rollen:
   - [&#x200B; beheerders van het Systeem &#x200B;](https://helpx.adobe.com/nl/enterprise/using/admin-roles.html){target="_blank"} - het systeemadmin heeft toegang tot alle producten en productprofielen in de organisatie door Adobe Admin Console.
   - [&#x200B; Admins van het Product &#x200B;](#add-a-product-admin) - de beheerders van het Product kunnen [&#x200B; gebruikers, rollen, en toestemmingen voor het product &#x200B;](#add-users-and-admins) in [!DNL Adobe Admin Console] beheren.
   - [&#x200B; het profielbeheerders van het Product &#x200B;](#add-users-developers-and-product-profile-admins) - de profielbeheerders van het Product kunnen gebruikers voor het product in [!DNL Adobe Admin Console] beheren.

## Een productbeheerder toevoegen

>[!BEGINTABS]

>[!NOTE]
>
>Wijs product toe beheert de [&#x200B; rol van de Gebruiker &#x200B;](#add-users) alvorens hen als productbeheerders toe te voegen. De gebruikersrol is vereist voor eenvoudige Commerce-machtigingen.

Er zijn twee verschillende manieren om gebruikers van productbeheer aan Adobe Commerce Optimizer toe te voegen op basis van het tijdstip waarop uw organisatie is ingericht. In vroege toegangsorganisaties, heeft elke gebruiker die de product admin rol wordt toegewezen toestemming om alle instanties in de organisatie te beheren. In organisaties voor algemene beschikbaarheid (GA) die na 13 oktober 2025 zijn ingericht, kunt u een gebruiker toewijzen als productbeheerder voor specifieke instanties. Wanneer de gebruiker van de productbeheerder zich aanmeldt, kunnen deze alleen de instanties zien die hij of zij mag beheren.

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

   ![&#x200B; uitgezocht product &#x200B;](/help/cloud-service/assets/backend.png){width="600" zoomable="yes"}

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

   ![&#x200B; uitgezocht product &#x200B;](/help/cloud-service//assets/backend.png){width="600" zoomable="yes"}

1. Klik het [!UICONTROL **Gebrek - het productprofiel van Cloud Manager**].

1. Selecteer het [!UICONTROL **lusje van Gebruikers**] en klik [!UICONTROL **toevoegen Gebruikers**].

   ![&#x200B; uitgezochte lusje &#x200B;](/help/cloud-service/assets/tab-select.png){width=600 zoomable="yes"}

1. Ga de gebruikersbenaming of e-mailadres van de gebruikers in u [!UICONTROL **sparen**] wilt toevoegen en klikken.

>[!ENDTABS]

### Ontwikkelaars en beheerders van productprofielen toevoegen

Om ontwikkelaars en productprofielbeheerders toe te voegen, herhaal [&#x200B; gebruikers &#x200B;](#add-users) proces toevoegen, maar selecteer [!UICONTROL **Ontwikkelaars**] of [!UICONTROL **Admins**] lusje in plaats van het [!UICONTROL **Gebruikers**] lusje.

>[!NOTE]
>
>Wijs ontwikkelaars de rol van de Gebruiker toe alvorens hen als ontwikkelaars toe te voegen. De gebruikersrol is vereist voor eenvoudige Commerce-machtigingen.

![&#x200B; uitgezochte lusje &#x200B;](/help//cloud-service/assets/tab-select.png){width=600 zoomable="yes"}

## Bulkgebruikersbeheer

U kunt meerdere gebruikers efficiënter toevoegen met een van de volgende methoden:

- Gebruik **voegt Gebruikers door CSV** eigenschap in Adobe Admin Console toe om a [&#x200B; bulkCSV uit te voeren uploadt &#x200B;](https://helpx.adobe.com/nl/enterprise/using/bulk-upload-users.html){target="_blank"}.
- Voeg veelvoudige gebruikers aan een rol toe door a [&#x200B; gebruikersgroep &#x200B;](https://helpx.adobe.com/nl/enterprise/using/user-groups.html){target="_blank"} te creëren. Vervolgens kunt u de juiste producten aan de gebruikersgroep toevoegen.

## Identiteitsbeheer en Single Sign-On configuratie

{{ims-identity-and-sso-config}}
