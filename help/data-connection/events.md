---
title: Gedragsgebeurtenissen
description: Leer welke gegevens elke gedraggebeurtenis vastlegt.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: bcabccc9-8a2e-4045-9306-1d999bb75624
source-git-commit: 1750aee715946d3a871e021cbbee687f54d1ff09
workflow-type: tm+mt
source-wordcount: '4528'
ht-degree: 0%

---

# [!DNL Data Connection] Gedragsgebeurtenissen

In het volgende voorbeeld worden de Commerce-gedragsgebeurtenissen weergegeven die beschikbaar zijn wanneer u de extensie [!DNL Data Connection] installeert. De gegevens die deze gebeurtenissen verzamelen, worden naar de Adobe Experience Platform verzonden. U kunt [ douanegebeurtenissen ](custom-events.md) ook tot stand brengen om extra gegevens te verzamelen die niet uit de doos worden verstrekt.

Naast de gegevens verzamelen de volgende gebeurtenissen zich, krijgt u ook [ andere gegevens ](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html?lang=nl-NL) die door het Web SDK van Adobe Experience Platform worden verstrekt.

De gedragsgebeurtenissen verzamelen geanonimiseerde gedragsgegevens van uw kopers wanneer ze door uw site bladeren. U kunt de gegevens die deze gebeurtenissen verzamelen gebruiken om promoties en campagnes te maken voor een specifieke groep kopers.

>[!NOTE]
>
>Alle gedragsgebeurtenissen omvatten het [`identityMap` ](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html?lang=nl-NL) gebied, dat het e-mailadres van de verkoopster, indien beschikbaar, en ECID omvat.

## Gebeurtenissen van Storefront

Storefront-gebeurtenissen leggen gegevens vast van de interacties van kopers op de site en bevatten gebeurtenissen zoals [`addToCart`](#addtocart) , [`pageView`](#pageview) , [`createAccount`](#createaccount) , [`editAccount`](#editaccount) , [`startCheckout`](#startcheckout) , [`completeCheckout`](#completecheckout) , [`signIn`](#signin) , [`signOut`](#signout) , enzovoort. De gebeurtenissen van het winkelfront zijn op eenvoudige en configureerbare slechts producten van toepassing.

### addToCart

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een product aan het winkelwagentje wordt toegevoegd of wanneer de hoeveelheid van een product in het winkelwagentje wordt verhoogd. | `commerce.productListAdds` |

#### Gegevens verzameld van addToCart

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.productListAdds` | Geeft aan of een product aan een winkelwagentje is toegevoegd. De waarde `1` geeft aan dat een product is toegevoegd. |
| `commerce.cart.cartID` | De unieke id die het winkelwagentje van de klant identificeert. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `productListItems` | Een reeks producten die aan het winkelwagentje zijn toegevoegd. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.productImageUrl` | URL van hoofdafbeelding van het product. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |

### openCart

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een nieuw winkelwagentje wordt gemaakt, dat wil zeggen wanneer een product aan een leeg winkelwagentje wordt toegevoegd. | `commerce.productListOpens` |

#### Gegevens verzameld van openCart

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.productListOpens` | Geeft aan of een winkelwagentje is gemaakt. De waarde `1` geeft aan dat een winkelwagentje is gemaakt. |
| `commerce.cart.cartID` | De unieke id die het winkelwagentje van de klant identificeert. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `productListItems` | Een reeks producten die aan het winkelwagentje zijn toegevoegd. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.productImageUrl` | URL van hoofdafbeelding van het product. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |

### removeFromCart

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Deze activering wordt telkens uitgevoerd wanneer een product wordt verwijderd of telkens wanneer de hoeveelheid van een product in het winkelwagentje wordt verlaagd. | `commerce.productListRemovals` |

#### Gegevens verzameld uit removeFromCart

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.productListRemovals` | Geeft aan of een product uit het winkelwagentje is verwijderd. De waarde `1` geeft aan dat een product uit het winkelwagentje is verwijderd. |
| `commerce.cart.cartID` | De unieke id die het winkelwagentje van de klant identificeert. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `productListItems` | Een reeks producten die aan het winkelwagentje zijn toegevoegd. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.productImageUrl` | URL van hoofdafbeelding van het product. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |

### shoppingCartView

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelwagenpagina wordt geladen. | `commerce.productListViews` |

#### Gegevens verzameld bij shoppingCartView

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.productListViews` | Geeft aan of een productlijst is weergegeven. |
| `commerce.cart.cartID` | De unieke id die het winkelwagentje van de klant identificeert. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `commerce.order` | Bevat informatie over de in behandeling zijnde orde voor één of meerdere producten. |
| `commerce.order.discountAmount` | Geeft het kortingsbedrag aan dat op de hele volgorde wordt toegepast. |
| `productListItems` | Een reeks producten die aan het winkelwagentje zijn toegevoegd. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.productImageUrl` | URL van hoofdafbeelding van het product. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |

### pageView

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een pagina wordt geladen. | `web.webpagedetails.pageViews` |

#### Gegevens verzameld van pageView

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `web.webPageDetails.pageViews` | Geeft aan of een pagina is geladen. Een `value` van `1` geeft aan dat de pagina is geladen. |
| `web.webPageDetails.URL` | De normatieve of gebruikelijke URL van de webpagina. Dit kan de werkelijke URL zijn die wordt gebruikt om de pagina te bereiken. Deze URL wordt opgenomen met `Web Link` . |
| `web.webPageDetails.name` | De normatieve naam van de webpagina. Deze naam is niet noodzakelijkerwijs de paginatitel of is rechtstreeks gekoppeld aan pagina-inhoud, maar wordt gebruikt om de pagina&#39;s van een site te ordenen voor classificatiedoeleinden. |
| `web.webReferrer.URL` | De URL van de webpagina die een winkel heeft bezocht voordat deze op een koppeling naar uw site heeft geklikt. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |

### productPageView

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een productpagina wordt geladen. | `commerce.productViews` |

#### Gegevens verzameld bij productPageView

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.productViews` | Geeft aan of het product is weergegeven. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `productListItems` | Een reeks producten die aan het winkelwagentje zijn toegevoegd. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.productImageUrl` | URL van hoofdafbeelding van het product. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |

### startCheckout

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer de gebruiker op een uitcheckknop klikt. | `commerce.checkouts` |

#### Gegevens verzameld van startCheckout

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.checkouts` | Hiermee wordt aangegeven of een actie is uitgevoerd tijdens het uitcheckproces. |
| `commerce.cart.cartID` | De unieke id die het winkelwagentje van de klant identificeert. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `productListItems` | Een reeks producten die aan het winkelwagentje zijn toegevoegd. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.productImageUrl` | URL van hoofdafbeelding van het product. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |

### completeCheckout

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer de gebruiker een bestelling plaatst. | `commerce.purchases` |

#### Gegevens verzameld bij completeCheckout

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.purchases` | Geeft aan of een bestelling is geaccepteerd. |
| `commerce.order` | Bevat informatie over de geplaatste order voor een of meer producten. |
| `commerce.order.purchaseID` | De unieke id die door de verkoper is toegewezen voor deze aankoop of dit contract. Er is geen garantie dat de id uniek is. |
| `commerce.order.payments` | De lijst met betalingen voor deze bestelling. |
| `commerce.order.payments.paymentTransactionID` | Unieke identificatiecode voor deze betalingstransactie. |
| `commerce.order.payments.paymentAmount` | De waarde van de betaling. |
| `commerce.order.payments.paymentType` | De betalingsmethode voor deze bestelling. De volgende opties zijn beschikbaar: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` . |
| `commerce.order.payments.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `commerce.order.taxAmount` | Het belastingbedrag dat de koper in het kader van de eindbetaling heeft betaald. |
| `commerce.order.discountAmount` | Geeft het kortingsbedrag aan dat op de hele volgorde wordt toegepast. |
| `commerce.order.createdDate` | De tijd en de datum waarop een nieuwe orde in het handelssysteem wordt gecreeerd. Bijvoorbeeld `2022-10-15T20:20:39+00:00` . |
| `commerce.shipping` | Verzendgegevens voor een of meer producten. |
| `commerce.shipping.shippingMethod` | De door de klant gekozen verzendmethode, zoals standaardlevering, versnelde levering, ophaalservice, enzovoort. |
| `commerce.shipping.shippingAmount` | Het bedrag dat de klant voor de verzending moest betalen. |  | `shipping` | Verzendgegevens voor een of meer producten. |
| `commerce.shipping.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `productListItems` | Een reeks producten die aan het winkelwagentje zijn toegevoegd. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.productImageUrl` | URL van hoofdafbeelding van het product. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |

## Klantprofielgebeurtenissen

Profielgebeurtenissen die zijn vastgelegd vanuit de storefront, bevatten accountinformatie, zoals `signIn` , `signOut` , `createAccount` en `editAccount` . Deze gegevens worden gebruikt om belangrijke klantendetails te bevolken die nodig zijn om segmenten beter te bepalen of marketing campagnes, zoals het verzenden van aanbiedingen van de inschrijvingskorting, bevestigingen van de rekeningsverandering, etc. uitvoeren. Er zijn gelijkaardige profielgebeurtenissen die van [ server-kant ](events-backoffice.md#customer-profile-events) worden gevangen.

>[!NOTE]
>
>[ Leer ](custom-identities.md) hoe te om de attributen van de douanetidentity tot stand te brengen om de identificatie van het klantenprofiel te verbeteren.

### signIn

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier zich aanmeldt. | `userAccount.login` |

>[!NOTE]
>
> Deze gebeurtenis wordt geactiveerd wanneer de specifieke actie wordt uitgevoerd. Het geeft niet aan dat de actie succesvol was.

#### Gegevens verzameld van signIn

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `person` | Een individuele actor, contactpersoon of eigenaar. |
| `person.accountID` | Hiermee legt u de gebruikersnaam van de gebruikersaccount vast. |
| `person.accountType` | Hiermee legt u het type gebruikersaccount vast, bijvoorbeeld `Personal` of `Company` , indien van toepassing. |
| `person.personalEmailID` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `personalEmail` | Leg contactgegevens vast - een e-mail en bijbehorende informatie. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `userAccount` | Hiermee geeft u eventuele loyaliteitsdetails, voorkeuren, aanmeldingsprocessen en andere accountvoorkeuren aan. |
| `userAccount.login` | Geeft aan of een bezoeker zich heeft aangemeld. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |

### signOut

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier zich afmeldt. | `userAccount.logout` |

>[!NOTE]
>
> Deze gebeurtenis wordt geactiveerd wanneer de specifieke actie wordt uitgevoerd. Het geeft niet aan dat de actie succesvol was.

#### Gegevens verzameld uit signOut

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `userAccount` | Hiermee geeft u eventuele loyaliteitsdetails, voorkeuren, aanmeldingsprocessen en andere accountvoorkeuren aan. |
| `userAccount.logout` | Geeft aan of een bezoeker zich heeft afgemeld. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |

### createAccount

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier een account probeert te maken. | `userAccount.createProfile` |

>[!NOTE]
>
> Deze gebeurtenis wordt geactiveerd wanneer de specifieke actie wordt uitgevoerd. Het geeft niet aan dat de actie succesvol was.

#### Gegevens verzameld van createAccount

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `person` | Een individuele actor, contactpersoon of eigenaar. |
| `person.accountID` | Hiermee legt u de gebruikersnaam van de gebruikersaccount vast. |
| `person.accountType` | Hiermee legt u het type gebruikersaccount vast, bijvoorbeeld `Personal` of `Company` , indien van toepassing. |
| `person.personalEmailID` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `personalEmail` | Leg contactgegevens vast - een e-mail en bijbehorende informatie. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `userAccount` | Hiermee geeft u eventuele loyaliteitsdetails, voorkeuren, aanmeldingsprocessen en andere accountvoorkeuren aan. |
| `userAccount.updateProfile` | Hiermee geeft u aan of een gebruiker zijn accountprofiel heeft bijgewerkt. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |

### editAccount

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een gebruiker een account probeert te bewerken. | `userAccount.updateProfile` |

>[!NOTE]
>
> Deze gebeurtenis wordt geactiveerd wanneer de specifieke actie wordt uitgevoerd. Het geeft niet aan dat de actie succesvol was.

#### Gegevens verzameld van editAccount

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `person` | Een individuele actor, contactpersoon of eigenaar. |
| `person.accountID` | Hiermee legt u de gebruikersnaam van de gebruikersaccount vast. |
| `person.accountType` | Hiermee legt u het type gebruikersaccount vast, bijvoorbeeld `Personal` of `Company` , indien van toepassing. |
| `person.personalEmailID` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `personalEmail` | Leg contactgegevens vast - een e-mail en bijbehorende informatie. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `userAccount` | Hiermee geeft u eventuele loyaliteitsdetails, voorkeuren, aanmeldingsprocessen en andere accountvoorkeuren aan. |
| `userAccount.updateProfile` | Hiermee geeft u aan of een gebruiker zijn accountprofiel heeft bijgewerkt. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |

## Zoeken in gebeurtenissen

De zoekgebeurtenissen bevatten gegevens die relevant zijn voor de intentie van de klant. Met insight in de intentie van een winkelier kunnen verkopers zien hoe kopers objecten zoeken, waarop ze klikken en op termijn kopen of verlaten. Een voorbeeld van hoe u deze gegevens kunt gebruiken is als u bestaande kopers wilt richten die naar uw topproduct zoeken, maar nooit het product kopen. U moet de extensie [[!DNL Live Search]](../live-search/install.md) installeren om toegang te krijgen tot deze gebeurtenissen.

Gebruik de velden `searchRequest.id` en `searchResponse.id` in de gebeurtenissen `searchRequestSent` en `searchResponseReceived` om een zoekaanvraag te doorverwijzen naar de corresponderende zoekreactie.

### searchRequestSent

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Teweeggebracht door de volgende gebeurtenissen in het &quot;onderzoek aangezien u&quot;popover typt:<br><br> Pers gaat binnen, klik _Mening allen_<br><br> teweeggebracht door de volgende gebeurtenissen op de pagina&#39;s van onderzoeksresultaten:<br><br> selecteer een filter, verander de soortorde (_Soort door_), verander de soortrichting (het stijgen of aflopend), verander het aantal resultaten per pagina (_toont # per pagina_), navigeer naar de volgende pagina, ga naar de vorige pagina, ga naar een andere pagina | `searchRequest` |

>[!NOTE]
>
>Zoekgebeurtenissen worden niet ondersteund op een Adobe Commerce Enterprise Edition met de B2B-extensie geïnstalleerd.

#### Gegevens verzameld van searchRequestSent

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `searchRequest` | Geeft aan of een zoekaanvraag is verzonden. |
| `searchRequest.id` | De unieke id voor deze zoekopdracht. |
| `searchRequest.value` | De kwantificeerbare waarde van het verzoek. |
| `siteSearch` | Bevat informatie over de zoekopdracht. |
| `siteSearch.filter` | Geeft aan of er filters zijn toegepast om de zoekresultaten te beperken. |
| `siteSearch.filter.attribute` (filter) | De facet van een item dat wordt gebruikt om te bepalen of het moet worden opgenomen in zoekresultaten. |
| `siteSearch.filter.isRange` | Wanneer waar, wijzen de waarden op eindpunten van een aanvaardbare waaier van waarden. |
| `siteSearch.filter.value` | Kenmerkwaarde die wordt gebruikt om te bepalen welke items worden opgenomen in de zoekresultaten. |
| `siteSearch.sort` | Geeft aan hoe de zoekresultaten moeten worden gesorteerd. |
| `siteSearch.sort.attribute` (sorteren) | An attribute used to sort items in search results. |
| `siteSearch.sort.order` | De volgorde waarin de zoekresultaten moeten worden geretourneerd. |
| `siteSearch.query` | De zoektermen. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |

### searchResponseReceived

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer Live zoeken resultaten oplevert voor de popover- of zoekresultatenpagina &quot;Zoeken zoals u typt&quot;. | `searchResponse` |

>[!NOTE]
>
>Zoekgebeurtenissen worden niet ondersteund op een Adobe Commerce Enterprise Edition met de B2B-extensie geïnstalleerd.

#### Gegevens verzameld van searchResponseReceived

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `searchResponse` | Geeft aan of een zoekreactie is ontvangen. |
| `searchResponse.id` | De unieke id voor deze specifieke zoekreactie. |
| `searchResponse.value` | De kwantificeerbare waarde van de respons. |
| `siteSearch.numberOfResults` | Het aantal geretourneerde producten. |
| `siteSearch.suggestions` | Een array van tekenreeksen met de namen van producten en categorieën die in de catalogus staan en die vergelijkbaar zijn met de zoekquery. |
| `productListItems` | Een reeks producten die aan het winkelwagentje zijn toegevoegd. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.productImageUrl` | URL van hoofdafbeelding van het product. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |

## B2B-gebeurtenissen

![ B2B voor Adobe Commerce ](../assets/b2b.svg) voor B2B handelaren, moet u [&#128279;](install.md#install-the-b2b-extension) de `experience-platform-connector-b2b` uitbreiding installeren om tot deze gebeurtenissen toegang te hebben.

De B2B gebeurtenissen bevatten [ informatie van de 0&rbrace; verzoeklijst &lbrace;, zoals als een verzoeklijst werd gecreeerd, aan, of geschrapt van werd toegevoegd. ](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html?lang=nl-NL) Door gebeurtenissen te volgen specifiek voor aanvraaglijsten, kunt u zien welke producten uw klanten vaak kopen en campagnes tot stand brengen die op die gegevens worden gebaseerd.

### createRequisitionList

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier een aanvraaglijst maakt. | `commerce.requisitionListOpens` |

#### Gegevens verzameld uit createRequisitionList

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.requisitionListOpens` | Geeft initialisatie van een nieuwe aanvraaglijst aan. |
| `commerce.requisitionList` | De eigenschappen van de aanvraaglijst die door de klant is gemaakt. |
| `commerce.requisitionList.ID` | Unieke id van de aanvraaglijst. |
| `commerce.requisitionList.name` | Naam van de aanvraaglijst die door de klant is opgegeven. |
| `commerce.requisitionList.description` | Beschrijving van de door de klant opgegeven aanvraaglijst. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |

### addToRequisitionList

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier een product aan een bestaande aanvraaglijst toevoegt of wanneer een lijst wordt gemaakt. | `commerce.requisitionListAdds` |

#### Gegevens verzameld uit addToRequisitionList

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.requisitionListAdds` | Hiermee wordt de toevoeging van een of meer producten aan een aanvraaglijst aangegeven. |
| `commerce.requisitionList` | De eigenschappen van de aanvraaglijst die door de klant is gemaakt. |
| `commerce.requisitionList.ID` | Unieke id van de aanvraaglijst. |
| `commerce.requisitionList.name` | Naam van de aanvraaglijst die door de klant is opgegeven. |
| `commerce.requisitionList.description` | Beschrijving van de door de klant opgegeven aanvraaglijst. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `productListItems` | Een array met producten die aan de aanvraaglijst zijn toegevoegd. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |

### removeFromRequisitionList

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier een product uit een aanvraaglijst verwijdert. | `commerce.requisitionListRemovals` |

#### Gegevens verzameld uit removeFromRequisitionList

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.requsitionListRemovals` | Geeft aan of een of meer producten uit een aanvraaglijst zijn verwijderd. |
| `commerce.requisitionList` | De eigenschappen van de aanvraaglijst die door de klant is gemaakt. |
| `commerce.requisitionList.ID` | Unieke id van de aanvraaglijst. |
| `commerce.requisitionList.name` | Naam van de aanvraaglijst die door de klant is opgegeven. |
| `commerce.requisitionList.description` | Beschrijving van de door de klant opgegeven aanvraaglijst. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `productListItems` | Een array met producten die aan de aanvraaglijst zijn toegevoegd. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |

### deleteRequisitionList

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier een aanvraaglijst verwijdert. | `commerce.requisitionListDeletes` |

#### Gegevens verzameld uit deleteRequisitionList

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `channel` | Bevat informatie over de bron van de gegevens. Zowel `_id` als `_type` bevatten [ namespaced waarden ](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html?lang=nl-NL). |
| `channel._id` | De unieke id van het kanaal, zoals `"https://ns.adobe.com/xdm/channels/web"` . |
| `channel._type` | Identificeert de bron van de kanaalgegevens, zoals `"https://ns.adobe.com/xdm/channel-types/web"` . |
| `commerce.requisitionListDeletes` | Geeft aan dat een aanvraaglijst is verwijderd. |
| `commerce.requisitionList` | De eigenschappen van de aanvraaglijst die door de klant is gemaakt. |
| `commerce.requisitionList.ID` | Unieke id van de aanvraaglijst. |
| `commerce.requisitionList.name` | Naam van de aanvraaglijst die door de klant is opgegeven. |
| `commerce.requisitionList.description` | Beschrijving van de door de klant opgegeven aanvraaglijst. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
