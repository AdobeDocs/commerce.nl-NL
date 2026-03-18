---
title: IMS-gebruikersmachtigingen configureren voor de AEM Assets-integratie
description: Leer hoe u met IMS-identiteits- en Admin Console-profielen toegang tot AEM Assets-levering, de velden Asset Selector en automatisch gevulde Commerce-configuratievelden inschakelt.
feature: CMS, Media, Configuration
source-git-commit: 0fd98bf86555c914f7a5b1e177c31c37764dbf84
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 0%

---

# Gebruikersmachtigingen en IMS

**IMS** (het Systeem van Adobe Identity Management) is de authentificatielaag. Voor Adobe Commerce as a Cloud Service is IMS-verificatie standaard ingeschakeld in Admin. Voor Adobe Commerce op wolk of op-gebouw, is IMS facultatief;[&#x200B; toelatend IMS voor Commerce &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/ims/adobe-ims-config.html?lang=nl-NL){target=_blank} verstrekt een verbeterde configuratie UI (de Selecteur van Activa, auto-bevolkte dropdowns), maar u kunt de integratie zonder IMS vormen door **identiteitskaart van het Programma** manueel in te gaan, en **identiteitskaart van het Milieu**.

De integratie van AEM Assets vereist ook specifieke **het productprofielen van Adobe Admin Console** wanneer het gebruiken van IMS. De gebruikers die de integratie in Commerce Admin vormen hebben de **gebruikers OpenAPI van AEM Assets DM - levering** productprofiel, of het **auteur** productprofiel als reserve nodig. Dit wordt beheerd via Admin Console-productprofielen in de IMS-organisatie van de gebruiker en schakelt het volgende in:

* **de Selecteur van Activa** staat toe om beelden van AEM Assets te selecteren wanneer het beheren van categoriebeelden of de inhoud van de Bouwer van de Pagina.
* **Auto-bevolkte configuratiegebieden** zoals **identiteitskaart van het Programma**, **identiteitskaart van het Milieu**, en **Punten van de in kaart brengende van het Domein** die waarden van de zitting trekken IMS van de gebruiker die op hun het productprofielen van Admin Console (levering of auteur) wordt gebaseerd.

Zonder de juiste machtigingen is de Asset Selector niet beschikbaar en worden deze velden leeg weergegeven of is handmatige invoer vereist.
>[!BEGINSHADEBOX]

**hoe IMS en toestemmingen samen** werken

Adobe IMS verstrekt de de gebruikersidentiteit en organisatiecontext, terwijl Adobe Admin Console bepaalt welke **productprofielen** (toestemmingen) het heeft. Bij de AEM Assets-integratie wordt gebruikgemaakt van de IMS-details plus het toegewezen profiel om te bepalen of configuratievelden automatisch kunnen worden ingevuld en of de Asset Selector kan worden ingeschakeld.

>[!ENDSHADEBOX]

## Waarom productprofielen zijn vereist

De integratie kan alleen domeinen laden die zijn toegewezen aan een profiel. Daarom kunnen gebruikers de volgende productprofielen hebben:

* **AEM het profiel van het leveringsproduct**. Vereist voor de UI voor het selecteren en configureren van bedrijfsmiddelen wanneer de gebruiker zowel auteur- als leveringsprofielen heeft. De integratie gebruikt het AEM-leveringsproductprofiel indien beschikbaar.

* **het productprofiel van de Auteur**. Vereist voor toegang tot de gebruikersinterface van AEM Assets. Deze functie fungeert ook als fallback voor de interface voor het selecteren en configureren van bedrijfsmiddelen wanneer de gebruiker niet beschikt over het AEM-profiel voor het leveringsproduct in zijn Admin Console.

Domeinen (inclusief programma-id, omgeving-id en domeintoewijzing) worden toegewezen aan het AEM-productprofiel voor levering. De integratie laadt domeinen van het **de leveringsproductprofiel van AEM** wanneer beschikbaar, of valt terug naar het **profiel van het auteursproduct** wanneer het de leveringsproductprofiel van AEM niet in Admin Console van de gebruiker is. Gebruikers hebben een van de volgende profielen nodig:

* Vul **identiteitskaart van het Programma**, **identiteitskaart van het Milieu**, en **Mapporterende van het Domein** dropdowns in de configuratie van Commerce Admin.
* Gebruik de Asset Selector om te bladeren naar elementen in AEM Assets en deze te selecteren.

Als geen van beide profiel wordt gevormd, kunnen de gebruikers **identiteitskaart van het Programma** en **identiteitskaart van het Milieu** manueel ingaan, maar de Selecteur van Activa zal niet beschikbaar zijn.

## Rechten verlenen per implementatietype

>[!BEGINTABS]

>[!TAB  Adobe Commerce as a Cloud Service ]

[!BADGE &#x200B; slechts SaaS &#x200B;]{type=Positive tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."}

IMS-verificatie is standaard ingeschakeld. Voeg de gebruiker aan de **AEM Assets DM OpenAPI Gebruikers toe - levering** productprofiel in [&#x200B; Adobe Admin Console &#x200B;](https://adminconsole.adobe.com/), of aan het **auteur** productprofiel (bijvoorbeeld, `<environment-name> - author - <program-id> - <environment-id>`) als reserve wanneer de gebruiker niet het profiel van het de leveringsproduct van AEM in hun Admin Console heeft.

>[!NOTE]
>
> Gebruikers moeten ook aan Commerce en AEM Assets worden toegevoegd. Zie [&#x200B; een gebruiker aan AEM Assets of de Visuals van het Product &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/cloud-service/user-management#add-a-user-to-aem-assets-or-product-visuals){target=_blank} in de _Gebruiker en Identity Management_ gids voor de volledige opstelling toevoegen.

![&#x200B; het productprofiel van Admin Console voor levering AEM Assets &#x200B;](../assets/aem-assets-delivery-product-profile.png){width="600" zoomable="yes"}

>[!TAB  Adobe Commerce op wolk of op-gebouw ]

[!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative tooltip="Alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur)."}

De **identiteitskaart van de Cliënt IMS** wordt vereist voor PaaS om de Selecteur van Activa toe te laten. Zie [&#x200B; het project van AEM Assets &#x200B;](configure-aem.md#prerequisites) voor eerste vereisten vormen, die omvatten hoe te om identiteitskaart van de Cliënt IMS te verkrijgen wanneer het toelaten van Dynamische Media met OpenAPI.

Om de selecteur van Activa en auto-bevolkte configuratievelden (Programma ID, Milieu identiteitskaart, de afbeelding van het Domein) te gebruiken:

1. [&#x200B; laat Adobe IMS voor Commerce &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/start/admin/ims/adobe-ims-config.html?lang=nl-NL){target=_blank} toe zodat Commerce Admin IMS authentificatie gebruikt en de het productprofielen van Admin Console van de gebruiker kan lezen.

1. [&#x200B; Open een kaartje van de Steun &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#support-cases) om een identiteitskaart van de Cliënt van douaneIMS voor de Selecteur van Activa te verzoeken.

1. Van [&#x200B; Adobe Admin Console &#x200B;](https://adminconsole.adobe.com/), voeg de gebruiker aan **AEM Assets DM OpenAPI Gebruikers toe - levering** productprofiel, of aan het **auteur** productprofiel (bijvoorbeeld, `<environment-name> - author - <program-id> - <environment-id>`) als reserve wanneer de gebruiker niet het profiel van het de leveringsproduct van AEM in hun Admin Console heeft.

Zonder IMS, kunt u de integratie nog vormen door Programma ID en Milieu ID in Commerce Admin manueel in te gaan.

>[!ENDTABS]

## Gerelateerde documentatie

* [&#x200B; vorm IMS gebruikerstoestemmingen voor de Integratie van AEM Assets &#x200B;](setup-synchronization.md) - verbind Commerce met AEM Assets en vorm passende regels.
* [&#x200B; de Handmatige selectie van activa &#x200B;](../synchronize/asset-selector-integration.md) - gebruik de Selector van Activa voor categoriebeelden en de Bouwer van de Pagina.
* [&#x200B; voeg een gebruiker aan AEM Assets toe of visuals van het Product &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce/cloud-service/user-management#add-a-user-to-aem-assets-or-product-visuals){target=_blank} - voor ACCS, voeg gebruikers aan Commerce en AEM Cloud Manager (Bedrijfs Eigenaar, Manager van de Plaatsing) eerst toe. Het **AEM Assets DM OpenAPI Gebruikers - levering** profiel (of **auteur** profiel als reserve) is een extra vereiste voor de Selecteur van Activa en auto-bevolkt eigenschappen.
* [&#x200B; wijs teamleden aan de leveringslaag van AEM &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem#add-team-members){target=_blank} toe. AEM-documentatie voor toegang tot levering.
