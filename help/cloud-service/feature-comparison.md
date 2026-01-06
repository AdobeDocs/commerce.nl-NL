---
title: Adobe Commerce SaaS versus PaaS vergelijking
description: Vergelijk Adobe Commerce SaaS met PaaS modellen om de beste implementatiebenadering voor uw bedrijfsbehoeften te bepalen.
feature: App Builder, GraphQL, Integration, Saas
role: Developer, Admin, Leader
level: Intermediate
exl-id: c8c9a0b4-f47c-46ec-bc9d-39dee9641f59
source-git-commit: 3fe22d47b6fd6cf1077cbd4644ffad08f55826ca
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 0%

---

# Functievergelijking

Adobe Commerce biedt drie implementatiemodellen:

- [!BADGE &#x200B; SaaS slechts &#x200B;]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce as a Cloud Service- en Adobe Commerce Optimizer-projecten (door Adobe beheerde SaaS-infrastructuur)."} [&#x200B; Adobe Commerce as a Cloud Service &#x200B;](overview.md) (SaaS)
- [!BADGE &#x200B; PaaS slechts &#x200B;]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."} [&#x200B; Adobe Commerce op Wolk &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/overview) (PaaS)
- [&#x200B; Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/overview) (op-gebouw)

Deze vergelijking richt zich op de verschillen tussen software-als-a-dienst (SaaS) en platform-als-a-dienst (PaaS) modellen. Deze modellen bieden verschillende niveaus van aanpassing, uitbreidbaarheid en controle over uw Commerce-implementatie.

>[!NOTE]
>
>Het op-gebouw model deelt gelijkaardige mogelijkheden met het model PaaS, zodat is deze vergelijking ook van toepassing wanneer het overwegen van SaaS tegenover op-gebouw implementaties.

## Functies voor opslagbeheer

[&#x200B; Commerce Admin UI &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/guide-overview) is de primaire interface voor de toegang tot van eigenschappen om achterste opslagverrichtingen, inventaris, tarifering, promoties, en klanteninteractie te beheren. [!DNL Adobe Commerce as a Cloud Service] biedt echter unieke oplossingen die sommige bekende functies in [!DNL Adobe Commerce on Cloud] en in projecten op locatie vervangen.

In de volgende tabel worden de functies en vervangende oplossingen beschreven die beschikbaar zijn in [!DNL Adobe Commerce as a Cloud Service] :

<table>
    <thead>
        <tr>
            <th>Het model van PaaS [!BADGE PaaS slechts]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions"tooltip="van toepassing is op Adobe Commerce op de projecten van de Wolk (de infrastructuur van Adobe-Beheerde PaaS) en op-gebouw slechts projecten."}</th>
            <th>SaaS model [!BADGE SaaS slechts]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions"tooltip="van toepassing is op Adobe Commerce as a Cloud Service en de projecten van Adobe Commerce Optimizer slechts (Adobe-beheerde infrastructuur SaaS)."}</th>
            <th>Details</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/wysiwyg/gallery/media-gallery-asset-management">Digitaal middelenbeheer</a></td>
            <td><a href="../aem-assets-integration/overview.md">AEM Assets-integratie</a></td>
            <td>Een krachtig DAM-systeem (Digital Asset Management) dat kan worden geïntegreerd met Adobe Experience Manager voor het beheer van rich media-inhoud. De standaard functie voor digitaal bestand- en middelenbeheer biedt ook de standaardfuncties voor middelenbeheer voor het opslaan en beheren van digitale elementen.</td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/guide-overview">Inhoudsbeheersysteem (CMS)</a></td>
            <td rowspan="3"><a href="https://experienceleague.adobe.com/developer/commerce/storefront/merchants/get-started/">Storefront Builder</a></td>
            <td rowspan="3">Een CMS die gebruikers toestaat om storefront inhoud tot stand te brengen en te beheren gemakkelijk gebruikend document creatie of Visuele Redacteur en omvat inheemse experimenteringsmogelijkheden.</td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/guide-overview">Page Builder</a></td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/seo/url-rewrites/url-rewrite">URL herschrijft</a></td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging">Inhoud stapelen</a></td>
            <td rowspan="2"><a href="../catalog-service/overview.md">Catalogusservice</a></td>
            <td rowspan="2">Een uitgebreide weergave-model (alleen-lezen) service voor het beheer van catalogusgegevens en het renderen van productgerelateerde winkelervaringen.</td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/marketing/merchandising/visual-merch/visual-merchandiser">Visual Merchandiser</a></td>
        </tr>
        <tr>
            <td><a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/payments/payments">Betalingen</a></td>
            <td><a href="../payment-services/guide-overview.md">Betalingsdiensten</a></td>
            <td>Een geïntegreerde betalingsdienst die veilige en efficiënte transacties vergemakkelijkt.</td>
        </tr>
    </tbody>
</table>

## Uitbreidbaarheid en platformkenmerken

In de volgende tabel worden de mogelijkheden en uitbreidbaarheidskenmerken van het platform vergeleken om u te helpen inzicht te krijgen in de verschillen en te bepalen welk model het beste aansluit bij uw bedrijfsvereisten voordat u een implementatie start.

<table>
    <thead>
        <tr>
            <th>Functie</th>
            <th>Het model van PaaS [!BADGE PaaS slechts]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions"tooltip="van toepassing is op Adobe Commerce op de projecten van de Wolk (de infrastructuur van Adobe-Beheerde PaaS) en op-gebouw slechts projecten."}</th>
            <th>SaaS model [!BADGE SaaS slechts]{type=Positive url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions"tooltip="van toepassing is op Adobe Commerce as a Cloud Service en de projecten van Adobe Commerce Optimizer slechts (Adobe-beheerde infrastructuur SaaS)."}</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Platformcapaciteiten</strong></td>
        </tr>
        <tr>
            <td>B2B-functionaliteit</td>
            <td>Volledige B2B-mogelijkheden na installatie beschikbaar</td>
            <td>Vooraf geïnstalleerd met kernB2B eigenschappen <sup> 1 </sup></td>
        </tr>
        <tr>
            <td>Experimentatie</td>
            <td>Invoegtoepassing voor bepaalde lagen</td>
            <td>A/B-tests om betrokkenheid en conversie te optimaliseren</td>
        </tr>
        <tr>
            <td>Functie- en beveiligingsupdates</td>
            <td>Vereist handmatige upgrade en patches</td>
            <td>Automatisch geïmplementeerd</td>
        </tr>
        <tr>
            <td>Hostinfrastructuur</td>
            <td>Eén huurder</td>
            <td>Meerdere gebruikers</td>
        </tr>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Aanpassing Commerce Admin</strong></td>
        </tr>
        <tr>
            <td>Extensible core Admin screens</td>
            <td>Volledige aanpassing van layout en functionaliteit</td>
            <td>Vooraf ingestelde filters, zichtbaarheidsbesturingselementen</td>
        </tr>
        <tr>
            <td>Uitbreidbare nieuwe Admin-schermen</td>
            <td>Standaard integratie van Admin UI en externe toepassing (Admin UI SDK)</td>
            <td>Externe app-injectie (Admin UI SDK)</td>
        </tr>
        <tr>
            <td>Aanpasbaar thema Admin</td>
            <td>Uitbreidbaar themaframework</td>
            <td>Geen themaframework</td>
        </tr>
        <tr>
            <td colspan="3" style="background:lightgray;"><strong>Uitbreidbaarheid</strong></td>
        </tr>
        <tr>
            <td>Uitbreidingsmodel</td>
            <td>In-process (PHP-aanpassing) en out-of-process (API's, events, App Builder)</td>
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
            <td>De attributen van de douane voor kern en B2B entiteiten <sup> 2 </sup></td>
        </tr>
        <tr>
            <td>Technologieën</td>
            <td>CSS, CLI, HTML, JS, PHP, XML</td>
            <td>CSS, CLI, HTML, JS, Node</td>
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
            <td>De staatsbibliotheek van App Builder (dossier slechts) <sup>  </sup></td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="3">
                <sup> 1 </sup> Kern <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/guide-overview"> B2B eigenschappen </a>, als bedrijfbeheer en het citeren, zijn beschikbaar uit-van-de-doos in SaaS. Voor industriespecifieke aanpassingen kunnen echter aanvullende implementatieoverwegingen nodig zijn.
                <br><br>
                <sup> 2 </sup> de modelrekbaarheid van Gegevens in SaaS steunt <a href="https://developer.adobe.com/commerce/webapi/graphql/schema/attributes/mutations/"> uitbreidend kernentiteiten </a> voorbij product en klant, met inbegrip van B2B entiteiten. Nochtans, industrie-specifieke gegevensmodellen (bijvoorbeeld, dealer-specifieke attributen) zouden extra architecturale overwegingen kunnen vereisen.
                <br><br>
                <sup> 3 </sup> Adobe werkt actief de integratie van DB van het Document om blijvende opslagbehoeften voor SaaS te richten. Op dit moment moeten implementaties die langdurige gegevensopslag vereisen, mogelijk extra infrastructuur aanleggen en onderhouden.
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
