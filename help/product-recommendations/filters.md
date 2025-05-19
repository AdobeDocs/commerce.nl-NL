---
title: Filterproducten
description: Bepaal voorwaarden die of producten van worden gebruikt als aanbevelingen omvatten of uitsluiten.
exl-id: 140bf047-4f6a-48da-b536-d96e78ae3d17
source-git-commit: 59aa4ae67a1a8a853b72d78cd65a6cc44a6bc662
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---

# Filterproducten

Adobe Commerce past automatisch niet-configureerbare standaardfilters op aanbevelingen toe. Als u meerdere aanbevelingen-eenheden op een pagina hebt geïmplementeerd, filtert Adobe Commerce alle producten uit die in de eenheden worden herhaald. Alleen de eerste verwijzing naar een herhaald product wordt gebruikt om ruimte te maken voor andere producten die kunnen worden aanbevolen. Adobe Commerce filtert ook alle eerder aangeschafte producten en producten die zich in de winkelwagen bevinden.

Wanneer u [&#128279;](create.md) creeert een aanbeveling eenheid, kunt u filters bepalen die controleren welke producten in aanbevelingen kunnen worden getoond. Deze filters zijn gebaseerd op een reeks opname- of uitsluitingsvoorwaarden die u definieert. In aanbevelingen worden alleen producten weergegeven die aan alle inclusiemogelijkheden voldoen. Producten die aan een van de uitsluitingsvoorwaarden voldoen, worden niet aanbevolen.

U kunt veelvoudige filters vormen en slechts die toelaten u wilt door de knevel op elke filterpagina te selecteren. Op deze manier kunt u concepten van filters maken voor toekomstig gebruik. Het aantal ingeschakelde filters wordt weergegeven op elk tabblad.

## Voorwaarden

De voorwaarden kunnen statisch of dynamisch zijn.

- Een statische voorwaarde gebruikt bestaande productkenmerken om te bepalen welke producten in de eenheid kunnen verschijnen. U kunt bijvoorbeeld opgeven dat alleen producten in voorraad met een prijs hoger dan € 25 in de eenheid worden weergegeven. Statische voorwaarden zijn beschikbaar op alle paginatypen.

- Een dynamische voorwaardensleutel van de huidige context van een winkelier, zoals de momenteel bekeken categorie of het product. Wanneer u bijvoorbeeld een productaanbeveling maakt die moet worden geïmplementeerd op pagina&#39;s met productdetails, kunt u een voorwaarde maken om alleen producten aan te bevelen die binnen een relatief prijsbereik van het momenteel weergegeven product vallen. Dynamische voorwaarden zijn beschikbaar voor elk paginatype, behalve voor de startpagina en op pagina&#39;s met aanbevelingen die bij de Page Builder zijn geplaatst.

### Logische operatoren

De logische operatoren `AND` en `OR` worden gebruikt om meerdere voorwaarden samen te voegen. Als zowel insluitings- als uitsluitingsfilters worden gebruikt, worden de insluitingen eerst geëvalueerd om te bepalen welke producten kunnen worden aanbevolen, waarna producten die overeenkomen met eventuele uitsluitingsfilters uit de lijst worden verwijderd.

- `AND` - Sluit aan bij twee insluitingsfiltervoorwaarden
- `OR` - Voegt twee uitsluitingsfiltervoorwaarden samen

>[!NOTE]
>
> De uitsluitings- en insluitingsfilters vervangen de uitsluitingen van oudere categorieën in versie 3.2.2 en hoger van de module `magento/product-recommendations` . Zie de [ versienota&#39;s ](release-notes.md) om meer over de versies van Adobe Commerce te leren.

## Filtertypen {#filtertypes}

![ Filters ](assets/rec-conditions.png)

### Categorie

[!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."}

Filtert producten op basis van hun categorie. Het categoriefilter gebruikt directe categorietoewijzingen en hun subcategorieën. Als u bijvoorbeeld een uitsluitingsvoorwaarde inschakelt voor categorie `Gear` , worden producten die zijn toegewezen aan `Gear` en alle bijbehorende subcategorieën, zoals `Gear/Bags` of `Gear/Fitness Equipment` , uitgesloten. Hetzelfde geldt voor een inclusiefilter op een categorie. Als u bijvoorbeeld een inclusievoorwaarde voor categorie `Gear` inschakelt, worden producten opgenomen die zijn toegewezen aan `Gear` en alle bijbehorende subcategorieën, zoals `Gear/Bags` of `Gear/Fitness Equipment` .

In het categorieveld worden categorieën weergegeven die bij de huidige voorvertoning horen.

>[!NOTE]
>
>Voor kooplieden B2B, blijft het filter van de Categorie aan om het even welke [ klant-specifieke productcategorieën ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html) u hebt gevormd.

Adobe Commerce raadt u aan de volgende configuratie voor categoriefilters te gebruiken wanneer u aanbevelingen op uw paginatypen toepast:

| Pagina | Filteren op |
|---|---|
| Home | Filtreer geen producten. |
| Categorie | Filterproducten in de specifieke categorie. |
| Productgegevens | Producten in dezelfde categorieën filteren. |
| Kar | Filtreer de productcategorieën in het winkelwagentje. |
| Bevestiging van bestelling | Filtercategorieën van aangekochte producten. |

### Product

Productfilters geven aan welke specifieke producten in aanmerking komen of niet in aanmerking komen om in aanbevelingen te worden weergegeven. U kunt geen producten selecteren die gehandicapt of niet individueel zichtbaar zijn omdat die producten nooit in aanbevelingen kunnen verschijnen.

>[!NOTE]
>
>De producten van het kind van een configureerbaar product worden niet getoond in een aanbeveling eenheid omdat die kindproducten het zicht van _hebben individueel niet Zichtbaar_.

### Type

[!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."}

Een filter op basis van het producttype omvat of sluit alle producten van een specifiek type uit. De gesteunde types omvatten _eenvoudig_, _configureerbaar_, _virtueel_, _downloadbaar_, of _geschenkkaart_. _Bundel_, _gegroepeerde_, en de types van douaneproduct worden niet gesteund.

### Zichtbaarheid

[!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."}

De producten van filters die op zicht, zoals worden gebaseerd: _Catalogus_, _Onderzoek_, of allebei.

### Prijs

Een filter op basis van de productprijs gebruikt de uiteindelijke prijs om de vergelijking uit te voeren. De uiteindelijke prijs omvat alle kortingen of speciale prijzen die beschikbaar zijn voor anonieme kopers. Voor kooplieden B2B, wijst de getoonde prijs op de [ klant-specifieke groepsprijzen ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) u hebt gevormd.

### Status van voorraad

De volgende uitsluitingsfilters kunnen worden gebruikt om producten te filteren op basis van de voorraadstatus:

- Niet in voorraad - (alleen Uitsluiting) Omvat geen producten die niet in voorraad zijn.
- Lage voorraad - (Uitsluiting alleen) Omvat geen producten die weinig voorraad hebben. De lage voorraadstatus is gebaseerd op _slechts X verlaten de waarde van de Drempel_ in [ configuratie van de Inventaris ](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/inventory.html).
