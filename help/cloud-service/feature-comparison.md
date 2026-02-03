---
title: Adobe Commerce SaaS versus PaaS vergelijking
description: Vergelijk Adobe Commerce SaaS met PaaS modellen om de beste implementatiebenadering voor uw bedrijfsbehoeften te bepalen.
feature: App Builder, GraphQL, Integration, Saas
role: Developer, Admin, Leader
level: Intermediate
exl-id: c8c9a0b4-f47c-46ec-bc9d-39dee9641f59
source-git-commit: e8e0c9f6a14232abc1332b48df7ae8bc3b955900
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---

# Functievergelijking

Adobe Commerce biedt drie implementatiemodellen:

- [!BADGE &#x200B; SaaS slechts &#x200B;]{type=Positive url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."} [&#x200B; Adobe Commerce as a Cloud Service &#x200B;](overview.md) (SaaS)
- [!BADGE &#x200B; PaaS slechts &#x200B;]{type=Informative url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."} [&#x200B; Adobe Commerce op Wolk &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/overview) (PaaS)
- [&#x200B; Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/overview) (op-gebouw)

Deze vergelijking richt zich op de verschillen tussen software-als-a-dienst (SaaS) en platform-als-a-dienst (PaaS) modellen. Deze modellen bieden verschillende niveaus van aanpassing, uitbreidbaarheid en controle over uw Commerce-implementatie.

>[!NOTE]
>
>Het op-gebouw model deelt gelijkaardige mogelijkheden met het model PaaS, zodat is deze vergelijking ook van toepassing wanneer het overwegen van SaaS tegenover op-gebouw implementaties.

## Functies voor opslagbeheer

[&#x200B; Commerce Admin UI &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/guide-overview) is de primaire interface voor de toegang tot van eigenschappen om achterste opslagverrichtingen, inventaris, tarifering, promoties, en klanteninteractie te beheren. [!DNL Adobe Commerce as a Cloud Service] biedt echter unieke oplossingen die sommige bekende functies in [!DNL Adobe Commerce on Cloud] en in projecten op locatie vervangen.

In de volgende tabel worden de functies en vervangende oplossingen beschreven die beschikbaar zijn in [!DNL Adobe Commerce as a Cloud Service] :

<table>
    <thead>
        <tr>
            <th>Functie</th>
            <th>Het model van PaaS [!BADGE PaaS slechts]{type=Informative url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions"tooltip="van toepassing is op Adobe Commerce op de projecten van de Wolk (de infrastructuur van Adobe-Beheerde PaaS) en op-gebouw slechts projecten."}</th>
            <th>SaaS model [!BADGE SaaS slechts]{type=Positive url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions"tooltip="van toepassing is op Adobe Commerce as a Cloud Service en de projecten van Adobe Commerce Optimizer slechts (Adobe-beheerde infrastructuur SaaS)."}</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Digitaal middelenbeheer</td>
            <td><a href="https://experienceleague.adobe.com/nl/docs/commerce-admin/content-design/wysiwyg/gallery/media-gallery-asset-management">Medialerie</a></td>
            <td><a href="../aem-assets-integration/overview.md">Productvisa</a></td>
        </tr>
        <tr>
            <td>Inhoudsbeheer</td>
            <td><a href="https://experienceleague.adobe.com/nl/docs/commerce-admin/content-design/guide-overview"> het Systeem van het Beheer van de Inhoud (CMS) </a>, <a href="https://experienceleague.adobe.com/nl/docs/commerce-admin/page-builder/guide-overview"> Bouwer van de Pagina </a>, <a href="https://experienceleague.adobe.com/nl/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite"> URL herschrijft </a></td>
            <td><a href="https://experienceleague.adobe.com/developer/commerce/storefront/merchants/get-started/?lang=nl-NL">Storefront Builder</a></td>
        </tr>
        <tr>
            <td>Catalogusverkoop</td>
            <td><a href="https://experienceleague.adobe.com/nl/docs/commerce-admin/content-design/staging/content-staging"> Inhoud die </a> staging, <a href="https://experienceleague.adobe.com/nl/docs/commerce-admin/marketing/merchandising/visual-merch/visual-merchandiser"> Visuele Merchandiser </a></td>
            <td><a href="../catalog-service/overview.md">Catalogusservice</a></td>
        </tr>
        <tr>
            <td>Betalingen</td>
            <td><a href="https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/payments/payments">Betalingsoplossingen</a></td>
            <td><a href="../payment-services/guide-overview.md">Betalingsdiensten</a></td>
        </tr>
        <tr>
            <td>B2B-functionaliteit</td>
            <td>Volledige B2B-mogelijkheden na installatie beschikbaar</td>
            <td>Vooraf geïnstalleerd met kernB2B eigenschappen <sup> 1 </sup></td>
        </tr>
        <tr>
            <td>Experimentatie</td>
            <td>Invoegtoepassing voor bepaalde lagen</td>
            <td>Systeemeigen A/B-tests om betrokkenheid en conversie te optimaliseren</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="3">
                <sup> 1 </sup> Kern <a href="https://experienceleague.adobe.com/nl/docs/commerce-admin/b2b/guide-overview"> B2B eigenschappen </a>, als bedrijfbeheer en het citeren, zijn beschikbaar uit-van-de-doos in SaaS. Voor industriespecifieke aanpassingen kunnen echter aanvullende implementatieoverwegingen nodig zijn.
            </td>
        </tr>
    </tfoot>
</table>

## Uitbreidbaarheid en platformkenmerken

In de volgende tabel worden de mogelijkheden en uitbreidbaarheidskenmerken van het platform vergeleken om u te helpen inzicht te krijgen in de verschillen en te bepalen welk model het beste aansluit bij uw bedrijfsvereisten voordat u een implementatie start.

<table>
    <thead>
        <tr>
            <th>Functie</th>
            <th>Het model van PaaS [!BADGE PaaS slechts]{type=Informative url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions"tooltip="van toepassing is op Adobe Commerce op de projecten van de Wolk (de infrastructuur van Adobe-Beheerde PaaS) en op-gebouw slechts projecten."}</th>
            <th>SaaS model [!BADGE SaaS slechts]{type=Positive url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions"tooltip="van toepassing is op Adobe Commerce as a Cloud Service en de projecten van Adobe Commerce Optimizer slechts (Adobe-beheerde infrastructuur SaaS)."}</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Platformcapaciteiten</strong></td>
        </tr>
        <tr>
            <td>Functie- en beveiligingsupdates</td>
            <td>Vereist handmatige upgrade en patching. Zes pleisters en één kleine afgifte per jaar.</td>
            <td>Automatisch geüpgraded door Adobe via een versieloze SaaS-model</td>
        </tr>
        <tr>
            <td>Hostinfrastructuur</td>
            <td>Eén huurder</td>
            <td>Meerdere gebruikers</td>
        </tr>
        <tr>
            <td>Prestaties en schaalbaarheid</td>
            <td>Horizontale automatische schaling voor geschaalde architectuur. Verticale automatische schaling voor weblaag die in een vroeg stadium toegankelijk wordt gemaakt voor alle handelaren, inclusief niet-geschaalde architectuur.</td>
            <td>Meerdere gebruikers als cloud-native toepassing met volledige automatische schaling over de stapel</td>
        </tr>
        <tr>
            <td>Waarneming</td>
            <td>[!DNL New Relic] toegang voor klanten om milieu te controleren en te beheren</td>
            <td>Adobe beheerd. Klanten kunnen [!DNL OpenTelemetry] gebruiken voor [!DNL App Builder] -apps en RUM-dashboards voor storefront. [!DNL New Relic] -licentie niet inbegrepen. Klanten kunnen [!DNL API Mesh] en [!DNL App Builder] zodanig configureren dat gegevens naar hun eigen [!DNL New Relic] -account worden verzonden.</td>
        </tr>
        <tr>
            <td>CDN</td>
            <td>[!DNL Fastly] inbegrepen</td>
            <td>Volledig beheerde Edge CDN nauw gekoppeld aan Commerce Storefront. BYO-CDN wordt ook ondersteund.</td>
        </tr>
        <tr>
            <td>Beveiliging en naleving</td>
            <td>SOC2, PCI, ISO-certificeringen per hostingprovider, HIPAA</td>
            <td>SOC2, PCI, ISO, GDPR. HIPAA momenteel niet beschikbaar.</td>
        </tr>
        <tr>
            <td>Noodherstel en SLA's</td>
            <td>99,99% infrastructuur, 99,9% toepassing (Managed Services)</td>
            <td>99,9% (infrastructuur en toepassing), snellere RPO/RTO</td>
        </tr>
        <tr>
            <td>Ontvangende gebieden</td>
            <td>Azure (24 locaties), AWS (22 locaties), GCP (8 locaties, niet standaard)</td>
            <td>Wereldwijd beschikbaar. Voor informatie over productieomgevingen in uw regio neemt u contact op met een medewerker van de klantenservice. Op basis van de vraag zijn extra locaties opgestart.</td>
        </tr>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Aanpassing Commerce Admin</strong></td>
        </tr>
        <tr>
            <td>Uitbreidbaarheid beheerconsole</td>
            <td>PHP-aanpassing en -thema, App Builder-uitbreidbaarheid (aanbevolen)</td>
            <td>Uitbreidbaarheid App Builder</td>
        </tr>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Uitbreidbaarheid</strong></td>
        </tr>
        <tr>
            <td>Uitbreidingsmodel</td>
            <td>In-process (PHP-aanpassing) en out-of-process (aanbevolen:API's, gebeurtenissen, App Builder)</td>
            <td>Alleen buiten proces (API's, gebeurtenissen, App Builder)</td>
        </tr>
        <tr>
            <td>Uitbreidbare web-API's</td>
            <td>Native REST/GraphQL-uitbreidbaarheid en API-net met aangepaste oplosmiddelen</td>
            <td>API-net met aangepaste oplosmiddelen</td>
        </tr>
        <tr>
            <td>Uitbreidbaarheid gegevensmodel</td>
            <td>Volledige aanpassing gegevensmodel</td>
            <td>De attributen van de douane voor kern en B2B entiteiten <sup> 1 </sup></td>
        </tr>
        <tr>
            <td>Technologieën</td>
            <td>CSS, CLI, HTML, JS, PHP, XML</td>
            <td>CSS, CLI, HTML, JS, Node</td>
        </tr>
        <tr>
            <td>App Marketplace</td>
            <td>[Magento Marketplace](https://marketplace.magento.com/) (PHP-extensies) en [Exchange Marketplace](https://commercemarketplace.adobe.com) voor [!DNL App Builder] apps (aanbevolen)</td>
            <td>[!DNL App Builder] apps van [[!DNL Exchange Marketplace]](https://commercemarketplace.adobe.com)</td>
        </tr>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Gegevens en opslag</strong></td>
        </tr>
        <tr>
            <td>Indexaanpassingen zoeken</td>
            <td>Aanpassing van eigen zoekopdracht</td>
            <td>Vereist oplossingen van derden</td>
        </tr>
        <tr>
            <td>Aangepaste e-mailtypen</td>
            <td>Volledige aanpassing van e-mail</td>
            <td>Alleen standaard e-mailsjablonen</td>
        </tr>
        <tr>
            <td>Aangepaste gegevensopslag</td>
            <td>DB, bestand, cache, wachtrij</td>
            <td>De staatsbibliotheek van App Builder (dossier slechts) <sup> 2 - {de Opslag van het 1} Gegevensbestand voor App Builder <a href="https://developer.adobe.com/app-builder/docs/guides/app_builder_guides/storage/database"> is momenteel in Vroege Toegang.</a></sup></td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="3">
                <sup> 1 </sup> de modelrekbaarheid van Gegevens in SaaS steunt <a href="https://developer.adobe.com/commerce/webapi/graphql/schema/attributes/mutations/"> uitbreidend kernentiteiten </a> voorbij product en klant, met inbegrip van B2B entiteiten. Nochtans, industrie-specifieke gegevensmodellen (bijvoorbeeld, dealer-specifieke attributen) zouden extra architecturale overwegingen kunnen vereisen.
                <br><br>
                <sup> 2 </sup> Adobe werkt actief de integratie van DB van het Document om blijvende opslagbehoeften voor SaaS te richten. Op dit moment moeten implementaties die langdurige gegevensopslag vereisen, mogelijk extra infrastructuur aanleggen en onderhouden.
            </td>
        </tr>
    </tfoot>
</table>

>[!NOTE]
>
>Bij het overwegen van migratie naar SaaS raadt Adobe u aan:
>
>- Verplaats waar mogelijk geschikte functionaliteit naar uitbreidbaarheid buiten het proces.
>- Verminder het oppervlak dat een overgang vereist.
>- Neem [!DNL API Mesh] in overweging om de API-functionaliteit uit te breiden.
>- Bewaking van de Adobe-ontwikkelingen op het huidige platform en van de nieuwe capaciteitsuitbreidingen.
>- Evalueer industriespecifieke gegevensmodelvereisten tegen beschikbare rekbaarheidsopties.
>- Overweeg het goedkeuren van [&#x200B; Merchandising de Diensten die door de Weergaven en het Beleid van de Catalogus worden aangedreven &#x200B;](../optimizer/setup/catalog-view.md).
