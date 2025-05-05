---
title: Aan de slag met  [!DNL Adobe Commerce as a Cloud Service]
description: Leer hoe te beginnen met  [!DNL Adobe Commerce as a Cloud Service].
role: Admin, Developer, User
exl-id: 58d98b9e-b41d-44db-9666-c924a5b005b3
source-git-commit: 9b90e6f79a394ec0941c9e48aee3859f0bcdedd5
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Aan de slag

{{accs-early-access}}

[!DNL Adobe Commerce as a Cloud Service] biedt de meeste configuratie uit het vak. Nadat u een aantal basisinstallatieprocessen hebt voltooid, wordt uw winkel zo snel mogelijk in bedrijf gesteld. Deze gids begeleidt u door het creëren van en het werken met een instantie.

Klik op de onderstaande tabbladen om workflowoverzichten op hoog niveau weer te geven voor de volgende gebruikerstypen:

* Beheerders
* Merchants
* Ontwikkelaars

>[!BEGINTABS]

>[!TAB  Beheerder en handelaarwerkschema ]

Dit diagram biedt een overzicht op hoog niveau van de manier waarop beheerders en verkopers [!DNL Adobe Commerce as a Cloud Service] -instanties benaderen en beheren. Zie de [ Gids van Adobe Admin Console ](https://helpx.adobe.com/nl/enterprise/admin-guide.html) voor meer informatie over beheerderwerkschema&#39;s.

![[!DNL Adobe Commerce as a Cloud Service] merchant flow diagram ](./assets/merchant-flow.svg){zoomable="yes"}

>[!TAB  werkschema van de Ontwikkelaar ]

Dit diagram biedt een overzicht op hoog niveau van de manier waarop ontwikkelaars integratie maken voor het gebruik van App Builder in [!DNL Adobe Commerce as a Cloud Service] . Zie de [ API documentatie ](https://developer.adobe.com/commerce/services/cloud/) voor meer informatie.

![[!DNL Adobe Commerce as a Cloud Service] Stroomdiagram voor ontwikkelaars ](./assets/developer-flow.svg){zoomable="yes"}

>[!ENDTABS]

## Een instantie maken

>[!NOTE]
>
>Voordat u een instantie kunt maken, moet de productbeheerder van uw organisatie of de systeembeheerder u toevoegen als gebruiker van het [!DNL Adobe Commerce as a Cloud Service] -product. Zie [ gebruikers en beheerders ](./user-management.md#add-users-and-admins) voor meer informatie toevoegen.

[!DNL Adobe Commerce as a Cloud Service] -instanties gebruiken een op krediet gebaseerd systeem. U kunt meerdere instanties maken, maar voor elke instantie is een relatieve hoeveelheid credits vereist. Het bedrag aan kredieten dat u aanvankelijk hebt, is afhankelijk van uw abonnement.

1. Login aan uw [ Adobe Experience Cloud ](https://experience.adobe.com/) rekening.

1. Onder [!UICONTROL Quick access], klik [!UICONTROL **Commerce**] om [!UICONTROL Commerce Cloud Manager] te openen.

   In [!UICONTROL Commerce Cloud Manager] wordt een lijst weergegeven met [!DNL Adobe Commerce as a Cloud Service] -instanties die beschikbaar zijn in uw Adobe IMS-organisatie.

1. Klik [!UICONTROL **toevoegen Instantie**] in de hoger-juiste hoek van het scherm.

   ![ creeer instantie ](./assets/create-instance.png){width="50%" align="center" zoomable="yes"}

1. Selecteer [!UICONTROL **Commerce as a Cloud Service**].

1. Ga a **Naam** en **Beschrijving** voor uw instantie in.

1. Selecteer het gebied waar u uw instantie wilt ontvangen.

   >[!NOTE]
   >
   >Nadat u de instantie hebt gemaakt, kunt u het gebied niet meer wijzigen.

1. Kies het [!UICONTROL **Type van Milieu**] voor uw instantie. U kunt kiezen uit de volgende opties:

   * [!UICONTROL **Sandbox**] - Ideaal voor ontwerp en testende doeleinden. U moet de [!DNL Adobe Commerce as a Cloud Service] -reis beginnen met de sandboxomgeving.
   * [!UICONTROL **Productie**] - voor levende opslag en klant-onder ogen ziet plaatsen.

   >[!NOTE]
   >
   >Sandbox-exemplaren zijn momenteel beperkt tot de regio Noord-Amerika.

1. _(Facultatief)_ als u steekproefproductgegevens voor het testen en het leren doeleinden wilt omvatten, de uitgezochte [!UICONTROL **Opslag van Adobe**] van de [!UICONTROL **gegevens van de Test**] dropdown.

   U kunt deze optie overslaan, maar uw winkel heeft geen producten als u dat doet. U zult uw catalogus [&#128279;](#import-your-catalog) moeten  invoeren om de volledige storefront ervaring te zien.

1. Klik [!UICONTROL **toevoegen Instantie**].

## Een instantie openen

Nadat u een instantie hebt gemaakt, kunt u deze openen vanuit de map [!UICONTROL Commerce Cloud Manager] .

1. Login aan uw [ Adobe Experience Cloud ](https://experience.adobe.com/) rekening.

1. Onder [!UICONTROL Quick access], klik [!UICONTROL **Commerce**] om [!UICONTROL Commerce Cloud Manager] te openen.

   In [!UICONTROL Commerce Cloud Manager] wordt een lijst weergegeven met instanties die beschikbaar zijn in uw Adobe IMS-organisatie.

1. Als u [!UICONTROL Commerce Admin] voor een instantie wilt openen, klikt u op de instantienaam.

>[!TIP]
>
>Klik op het informatiepictogram naast de instantienaam voor informatie over uw instantie, zoals de REST- en GraphQL-eindpunten en de Admin-URL.

## Uw catalogus importeren

Standaard bevatten [!DNL Adobe Commerce as a Cloud Service] -instanties geen productgegevens. U kunt voorbeeldproductgegevens opnemen wanneer u een exemplaar maakt voor test- en leerdoeleinden voordat u uw eigen catalogus importeert.

U kunt uw catalogus op twee manieren importeren in [!DNL Adobe Commerce as a Cloud Service] :

* [**Admin van Commerce** ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/data-transfer/import/data-import) - een gebruikersvriendelijke interface die u toestaat om uw catalogusgegevens in een paar kliks in te voeren.
* [**de Invoer JSON API** ](https://developer.adobe.com/commerce/webapi/rest/modules/import/#import-json-api) - VERTONEN API die u toestaat om uw catalogusgegevens programmatically in te voeren.

<!-- TODO

- Add guidance about how to choose which method to use
- Add guidance for new vs existing customers (cross-reference OR and _include file for migration content)

-->

## De storefront instellen

Nu u een instantie hebt gecreeerd, bent u bereid om [ vestiging ](storefront.md) te werk te gaan uw die Opslag van Commerce door Edge Delivery Services wordt aangedreven.
