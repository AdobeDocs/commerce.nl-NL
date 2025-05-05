---
title: Back Office-gebeurtenissen
description: Leer welke gegevens elke achterkantoorgebeurtenis vangt.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '3606'
ht-degree: 0%

---

# [!DNL Data Connection] Back Office-gebeurtenissen

Hieronder ziet u een lijst met Commerce-back office-gebeurtenissen die beschikbaar zijn wanneer u de extensie [!DNL Data Connection] installeert. De gegevens die deze gebeurtenissen verzamelen, worden naar de Adobe Experience Platform verzonden. U kunt [ douanegebeurtenissen ](custom-events.md) ook tot stand brengen om extra gegevens te verzamelen die niet uit de doos worden verstrekt.

Naast de gegevens verzamelen de volgende gebeurtenissen zich, krijgt u ook [ andere gegevens ](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) die door het Web SDK van Adobe Experience Platform worden verstrekt.

De gebeurtenissen van het achterkantoor bevatten server-zijgegevens. Dit gegeven bestaat uit [ de status van de orde ](#order-status) informatie zoals als een orde werd geplaatst, geannuleerd, terugbetaald, verscheept, of voltooid. De server-zijgegevens omvatten ook [&#128279;](#customer-profile-events) informatie van de de klantenprofielgebeurtenissen van 0&rbrace; &lbrace;, zoals als een rekening werd gecreeerd, bijgewerkt, of geschrapt.

>[!NOTE]
>
>Alle achterkantoorgebeurtenissen omvatten het [`identityMap` ](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) gebied, dat het e-mailadres van de verkoopster, indien beschikbaar, en ECID omvat.

## Status van bestelling

De de statusgegevens van de orde tonen een 360 mening van de verkooporde. Deze weergave helpt handelaren om bij het ontwikkelen van marketingcampagnes de gehele orderstatus beter te bepalen of te analyseren. U kunt bijvoorbeeld trends waarnemen in bepaalde productcategorieën die goed presteren op verschillende momenten van het jaar. Bijvoorbeeld winterkleding die beter verkoopt tijdens koudere maanden of bepaalde productkleuren waarin consumenten in de loop der jaren geïnteresseerd zijn. Bovendien kunnen de gegevens van de ordestatus u helpen de waarde van de levenklant berekenen door de neiging van een klant te begrijpen om op vorige orden gebaseerd om te zetten.

### orderPlaced

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier een bestelling plaatst. | `commerce.backofficeOrderPlaced` |

#### Gegevens verzameld van orderPlaced

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `commerce.order` | Bevat informatie over de orde. |
| `commerce.order.purchaseID` | De unieke id die door de verkoper is toegewezen voor deze aankoop of dit contract. Er is geen garantie dat de id uniek is. |
| `commerce.order.payments` | De lijst met betalingen voor deze bestelling. |
| `commerce.order.payments.paymentTransactionID` | Unieke identificatiecode voor deze betalingstransactie. |
| `commerce.order.payments.paymentAmount` | De waarde van de betaling. |
| `commerce.order.payments.paymentType` | De betalingsmethode voor deze bestelling. Geladen, aangepaste waarden toegestaan. |
| `commerce.order.payments.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `commerce.order.taxAmount` | Het belastingbedrag dat de koper in het kader van de eindbetaling heeft betaald. |
| `commerce.order.discountAmount` | Geeft het kortingsbedrag aan dat op de hele volgorde wordt toegepast. |
| `commerce.order.createdDate` | De tijd en de datum waarop een nieuwe orde in het handelssysteem wordt gecreeerd. Bijvoorbeeld `2022-10-15T20:20:39+00:00` . |
| `commerce.order.currencyCode` | De ISO 4217-valutacode die wordt gebruikt voor de totalen van de orders. |
| `commerce.shipping` | Verzendgegevens voor een of meer producten. |
| `commerce.shipping.shippingMethod` | De door de klant gekozen verzendmethode, zoals standaardlevering, versnelde levering, ophaalservice, enzovoort. |
| `commerce.shipping.shippingAmount` | Het bedrag dat de klant voor de verzending moest betalen. |
| `commerce.shipping.currencyCode` | De ISO 4217-valutacode die wordt gebruikt voor het verzendende totaal. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `commerce.billing.address` | Postadres facturering. |
| `commerce.billing.address.street1` | Informatie op straat, appartementnummer, straatnummer en straatnaam |
| `commerce.billing.address.street2` | Extra veld voor straatinformatie. |
| `commerce.billing.address.city` | De naam van de stad. |
| `commerce.billing.address.state` | De naam van de staat. Dit is een veld met vrije vorm. |
| `commerce.billing.address.postalCode` | De postcode van de locatie. Postcodes zijn niet voor alle landen beschikbaar. In sommige landen zal dit slechts een deel van de postcode bevatten. |
| `commerce.billing.address.country` | De naam van het door de overheid bestuurde gebied. Met uitzondering van `xdm:countryCode` is dit een veld met vrije vorm dat de landnaam in elke taal kan hebben. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `productListItems` | Een array van producten in de volgorde. |
| `productListItems.id` | The line item identifier for this product entry. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |
| `productListItems.categories` | Bevat informatie over de categorie van een product. |
| `productListItems.categories.id` | De unieke id van de categorie. |
| `productListItems.categories.name` | De naam van de categorie. |
| `productListItems.categories.path` | Het pad naar de categorie. |
| `productListItems.productImageUrl` | URL van hoofdafbeelding van het product. |

### orderInvoice

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een handelaar een factuur indient om betaling aan te vragen. | `commerce.backofficeOrderInvoiced` |

#### Gegevens verzameld bij orderInvoice

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `commerce.order` | Bevat informatie over de orde. |
| `commerce.order.purchaseID` | De unieke id die door de verkoper is toegewezen voor deze aankoop of dit contract. Er is geen garantie dat de id uniek is. |
| `commerce.order.priceTotal` | De totale prijs van deze bestelling nadat alle kortingen en belastingen zijn toegepast. |
| `commerce.order.currencyCode` | De ISO 4217-valutacode die wordt gebruikt voor de totalen van de orders. |
| `commerce.order.purchaseOrderNumber` | Unieke identificatiecode die door de koper voor deze aankoop of dit contract is toegekend. |
| `commerce.order.payments` | De lijst met betalingen voor deze bestelling. |
| `commerce.order.payments.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `commerce.order.payments.paymentType` | De betalingsmethode voor deze bestelling. Geladen, aangepaste waarden toegestaan. |
| `commerce.order.payments.paymentAmount` | De waarde van de betaling. |
| `commerce.shipping` | Verzendgegevens voor een of meer producten. |
| `commerce.shipping.shippingMethod` | De door de klant gekozen verzendmethode, zoals standaardlevering, versnelde levering, ophaalservice, enzovoort. |
| `commerce.shipping.shippingAmount` | Het bedrag dat de klant voor de verzending moest betalen. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `productListItems` | Een array van producten in de volgorde. |
| `productListItems.id` | The line item identifier for this product entry. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.categories` | Bevat informatie over de categorie van een product. |
| `productListItems.categories.id` | De unieke id van de categorie. |
| `productListItems.categories.name` | De naam van de categorie. |
| `productListItems.categories.path` | Het pad naar de categorie. |

### orderItemsShipped

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een bestelling wordt verzonden. | `commerce.backofficeOrderItemsShipped` |

#### Gegevens verzameld van orderItemsShipped

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `commerce.order` | Bevat informatie over de orde. |
| `commerce.order.purchaseID` | De unieke id die door de verkoper is toegewezen voor deze aankoop of dit contract. Er is geen garantie dat de id uniek is. |
| `commerce.order.payments` | De lijst met betalingen voor deze bestelling. |
| `commerce.order.payments.paymentTransactionID` | Unieke identificatiecode voor deze betalingstransactie. |
| `commerce.order.payments.paymentAmount` | De waarde van de betaling. |
| `commerce.order.payments.paymentType` | De betalingsmethode voor deze bestelling. Geladen, aangepaste waarden toegestaan. |
| `commerce.order.payments.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `commerce.order.priceTotal` | De totale prijs van deze bestelling nadat alle kortingen en belastingen zijn toegepast. |
| `commerce.order.purchaseOrderNumber` | Unieke identificatiecode die door de koper voor deze aankoop of dit contract is toegekend. |
| `commerce.order.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `commerce.order.lastUpdatedDate` | Het tijdstip waarop een bepaalde orderrecord voor het laatst is bijgewerkt in het handelssysteem. |
| `commerce.shipping` | Verzendgegevens voor een of meer producten. |
| `commerce.shipping.shippingMethod` | De door de klant gekozen verzendmethode, zoals standaardlevering, versnelde levering, ophaalservice, enzovoort. |
| `commerce.shipping.shippingAmount` | Het bedrag dat de klant voor de verzending moest betalen. |
| `commerce.shipping.address` | Het fysieke verzendadres. |
| `commerce.shipping.address.street1` | Primaire straatinformatie, appartementnummer, straatnummer en straatnaam. |
| `commerce.shipping.address.street2` | Optionele straatinformatie, tweede regel. |
| `commerce.shipping.address.city` | De naam van de stad. |
| `commerce.shipping.address.state` | De naam van de staat. Dit is een veld met vrije vorm. |
| `commerce.shipping.address.postalCode` | De postcode van de locatie. Postcodes zijn niet voor alle landen beschikbaar. In sommige landen zal dit slechts een deel van de postcode bevatten. |
| `commerce.shipping.address.country` | De naam van het door de overheid bestuurde gebied. Met uitzondering van `xdm:countryCode` is dit een veld met vrije vorm dat de landnaam in elke taal kan hebben. |
| `commerce.shipping.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `commerce.shipping.trackingNumber` | Het trackingnummer dat door de verzendende maatschappij is opgegeven voor een verzending van een bestelartikel. |
| `commerce.shipping.trackingURL` | De URL waarmee de verzendstatus van een orderitem wordt gevolgd. |
| `commerce.shipping.shipDate` | De datum waarop een of meer items van een bestelling worden verzonden. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `commerce.billing.address` | Postadres facturering. |
| `commerce.billing.address.street1` | Informatie op straat, appartementnummer, straatnummer en straatnaam |
| `commerce.billing.address.street2` | Extra veld voor straatinformatie. |
| `commerce.billing.address.city` | De naam van de stad. |
| `commerce.billing.address.state` | De naam van de staat. Dit is een veld met vrije vorm. |
| `commerce.billing.address.postalCode` | De postcode van de locatie. Postcodes zijn niet voor alle landen beschikbaar. In sommige landen zal dit slechts een deel van de postcode bevatten. |
| `commerce.billing.address.country` | De naam van het door de overheid bestuurde gebied. Met uitzondering van `xdm:countryCode` is dit een veld met vrije vorm dat de landnaam in elke taal kan hebben. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `productListItems` | Een array van producten in de volgorde. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |
| `productListItems.categories` | Bevat informatie over de categorie van een product. |
| `productListItems.categories.id` | De unieke id van de categorie. |
| `productListItems.categories.name` | De naam van de categorie. |
| `productListItems.categories.path` | Het pad naar de categorie. |

### orderCanceled

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier een bestelling annuleert. | `commerce.backofficeOrderCancelled` |

#### Gegevens verzameld van orderCanceled

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `commerce.order` | Bevat informatie over de orde. |
| `commerce.order.purchaseID` | De unieke id die door de verkoper is toegewezen voor deze aankoop of dit contract. Er is geen garantie dat de id uniek is. |
| `commerce.order.purchaseOrderNumber` | Unieke identificatiecode die door de koper voor deze aankoop of dit contract is toegekend. |
| `commerce.order.cancelDate` | De datum en tijd waarop een winkelier een bestelling annuleert. |
| `commerce.order.lastUpdatedDate` | Het tijdstip waarop een bepaalde orderrecord voor het laatst is bijgewerkt in het handelssysteem. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |

### orderLineItemRefunded

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier voor een geretourneerd item wordt terugbetaald. | `commerce.backofficeCreditMemoIssued` |

#### Gegevens verzameld van orderLineItemRefunded

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `commerce.order` | Bevat informatie over de orde. |
| `commerce.order.purchaseID` | De unieke id die door de verkoper is toegewezen voor deze aankoop of dit contract. Er is geen garantie dat de id uniek is. |
| `commerce.order.lastUpdatedDate` | Het tijdstip waarop een bepaalde orderrecord voor het laatst is bijgewerkt in het handelssysteem. |
| `commerce.order.purchaseOrderNumber` | Unieke identificatiecode die door de koper voor deze aankoop of dit contract is toegekend. |
| `commerce.refunds` | De lijst van terugbetalingen voor deze bestelling. |
| `commerce.refunds.transactionID` | Unieke identificatiecode voor deze restitutie. |
| `commerce.refunds.refundAmount` | De waarde van de restitutie. |
| `commerce.refunds.refundPaymentType` | De betalingsmethode voor deze bestelling. Geladen, aangepaste waarden toegestaan. |
| `commerce.refunds.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `productListItems` | Een array van producten in de volgorde. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |
| `productListItems.categories` | Bevat informatie over de categorie van een product. |
| `productListItems.categories.id` | De unieke id van de categorie. |
| `productListItems.categories.name` | De naam van de categorie. |
| `productListItems.categories.path` | Het pad naar de categorie. |

### orderItemsReturnInitiated

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier een item wil retourneren. | `commerce.backofficeOrderItemsReturnInitiated` |

#### Gegevens verzameld bij orderItemsReturnInitiated

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `commerce.order` | Bevat informatie over de orde. |
| `commerce.order.purchaseID` | De unieke id die door de verkoper is toegewezen voor deze aankoop of dit contract. Er is geen garantie dat de id uniek is. |
| `commerce.order.returns` | De RMA-informatie (Return Merchandise Authorization) voor deze bestelling. |
| `commerce.order.returns.returnID` | De unieke id voor deze RMA (Return Merchandise Authorization). |
| `commerce.order.returns.returnStatus` | De status van RMA (Return Merchandise Authorization), zoals In behandeling, Gesloten enzovoort. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `productListItems` | Een array van producten in de volgorde. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |
| `productListItems.categories` | Bevat informatie over de categorie van een product. |
| `productListItems.categories.id` | De unieke id van de categorie. |
| `productListItems.categories.name` | De naam van de categorie. |
| `productListItems.categories.path` | Het pad naar de categorie. |
| `productListItems.returnItem` | De RMA-informatie (Return Merchandise Authorization) voor dit onderdeel. |
| `productListItems.returnItem.returnStatus` | De status van het geretourneerde item, zoals In behandeling, Goedgekeurd enzovoort. |
| `productListItems.returnItem.returnReason` | De reden waarom er voor dit object om retournering wordt gevraagd. |
| `productListItems.returnItem.returnItemCondition` | De voorwaarde van het item waarvoor de return wordt aangevraagd. |
| `productListItems.returnItem.returnResolution` | De gevraagde resolutie van het item dat wordt geretourneerd, zoals Restitutie, Exchange enzovoort. |
| `productListItems.returnItem.returnQuantityRequested` | Het aantal van dit object dat de verkoper heeft aangevraagd. |
| `productListItems.returnItem.returnQuantityAuthorized` | Het nummer van dit object dat mag worden geretourneerd. |
| `productListItems.returnItem.eturnQuantityReceived` | Het aantal geretourneerde objecten dat is ontvangen. |
| `productListItems.returnItem.returnQuantityApproved` | Het nummer van dit onderdeel met volledige retournering en goedkeuring. |

### orderItemReturnCompleted

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een object is voltooid dat een winkelier heeft aangevraagd om te retourneren. | `commerce.backofficeOrderItemsReturnCompleted` |

#### Gegevens verzameld van orderItemReturnCompleted

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `commerce.order` | Bevat informatie over de orde. |
| `commerce.order.purchaseID` | De unieke id die door de verkoper is toegewezen voor deze aankoop of dit contract. Er is geen garantie dat de id uniek is. |
| `commerce.order.returns` | De RMA-informatie (Return Merchandise Authorization) voor deze bestelling. |
| `commerce.order.returns.returnID` | De unieke id voor deze RMA (Return Merchandise Authorization). |
| `commerce.order.returns.returnStatus` | De status van RMA (Return Merchandise Authorization), zoals In behandeling, Gesloten enzovoort. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `productListItems` | Een array van producten in de volgorde. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |
| `productListItems.categories` | Bevat informatie over de categorie van een product. |
| `productListItems.categories.id` | De unieke id van de categorie. |
| `productListItems.categories.name` | De naam van de categorie. |
| `productListItems.categories.path` | Het pad naar de categorie. |
| `productListItems.returnItem` | De RMA-informatie (Return Merchandise Authorization) voor dit onderdeel. |
| `productListItems.returnItem.returnStatus` | De status van het geretourneerde item, zoals In behandeling, Goedgekeurd enzovoort. |
| `productListItems.returnItem.returnReason` | De reden waarom er voor dit object om retournering wordt gevraagd. |
| `productListItems.returnItem.returnItemCondition` | De voorwaarde van het item waarvoor de return wordt aangevraagd. |
| `productListItems.returnItem.returnResolution` | De gevraagde resolutie van het item dat wordt geretourneerd, zoals Restitutie, Exchange enzovoort. |
| `productListItems.returnItem.returnQuantityRequested` | Het aantal van dit object dat de verkoper heeft aangevraagd. |
| `productListItems.returnItem.returnQuantityAuthorized` | Het nummer van dit object dat mag worden geretourneerd. |
| `productListItems.returnItem.eturnQuantityReceived` | Het aantal geretourneerde objecten dat is ontvangen. |
| `productListItems.returnItem.returnQuantityApproved` | Het nummer van dit onderdeel met volledige retournering en goedkeuring. |

### orderShipmentCompleted

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een transport is voltooid. | `commerce.backofficeOrderShipmentCompleted` |

#### Gegevens verzameld bij orderShipmentCompleted

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `commerce.order` | Bevat informatie over de orde. |
| `commerce.order.purchaseID` | De unieke id die door de verkoper is toegewezen voor deze aankoop of dit contract. Er is geen garantie dat de id uniek is. |
| `commerce.order.payments` | De lijst met betalingen voor deze bestelling. |
| `commerce.order.payments.paymentTransactionID` | Unieke identificatiecode voor deze betalingstransactie. |
| `commerce.order.payments.paymentAmount` | De waarde van de betaling. |
| `commerce.order.payments.paymentType` | De betalingsmethode voor deze bestelling. Geladen, aangepaste waarden toegestaan. |
| `commerce.order.payments.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `commerce.order.taxAmount` | Het belastingbedrag dat de koper in het kader van de eindbetaling heeft betaald. |
| `commerce.order.createdDate` | De tijd en de datum waarop een nieuwe orde in het handelssysteem wordt gecreeerd. Bijvoorbeeld `2022-10-15T20:20:39+00:00` . |
| `commerce.shipping` | Verzendgegevens voor een of meer producten. |
| `commerce.shipping.shippingMethod` | De door de klant gekozen verzendmethode, zoals standaardlevering, versnelde levering, ophaalservice, enzovoort. |
| `commerce.shipping.shippingAmount` | Het bedrag dat de klant voor de verzending moest betalen. |
| `commerce.shipping.shipDate` | De datum waarop een of meer items van een bestelling worden verzonden. |
| `commerce.shipping.address` | Het fysieke verzendadres. |
| `commerce.shipping.address.street1` | Primaire straatinformatie, appartementnummer, straatnummer en straatnaam. |
| `commerce.shipping.address.street2` | Optionele straatinformatie, tweede regel. |
| `commerce.shipping.address.city` | De naam van de stad. |
| `commerce.shipping.address.state` | De naam van de staat. Dit is een veld met vrije vorm. |
| `commerce.shipping.address.postalCode` | De postcode van de locatie. Postcodes zijn niet voor alle landen beschikbaar. In sommige landen zal dit slechts een deel van de postcode bevatten. |
| `commerce.shipping.address.country` | De naam van het door de overheid bestuurde gebied. Met uitzondering van `xdm:countryCode` is dit een veld met vrije vorm dat de landnaam in elke taal kan hebben. |
| `commerce.billing.address` | Postadres facturering. |
| `commerce.billing.address.street1` | Informatie op straat, appartementnummer, straatnummer en straatnaam |
| `commerce.billing.address.street2` | Extra veld voor straatinformatie. |
| `commerce.billing.address.city` | De naam van de stad. |
| `commerce.billing.address.state` | De naam van de staat. Dit is een veld met vrije vorm. |
| `commerce.billing.address.postalCode` | De postcode van de locatie. Postcodes zijn niet voor alle landen beschikbaar. In sommige landen zal dit slechts een deel van de postcode bevatten. |
| `commerce.billing.address.country` | De naam van het door de overheid bestuurde gebied. Met uitzondering van `xdm:countryCode` is dit een veld met vrije vorm dat de landnaam in elke taal kan hebben. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `productListItems` | Een array van producten in de volgorde. |
| `productListItems.SKU` | Stock Keeping Unit. De unieke id voor het product. |
| `productListItems.name` | De weergavenaam of leesbare naam van het product. |
| `productListItems.priceTotal` | De totale prijs voor het item van de productlijn. |
| `productListItems.quantity` | Het aantal eenheden van het product in de kar. |
| `productListItems.discountAmount` | Geeft de toegepaste disconteringswaarde aan. |
| `productListItems.currencyCode` | De [ ISO 4217 ](https://en.wikipedia.org/wiki/ISO_4217) gebruikte muntcode, zoals `USD` of `EUR`. |
| `productListItems.selectedOptions` | Veld voor een configureerbaar product. |
| `productListItems.selectedOptions.attribute` | Identificeert een kenmerk van het configureerbare product, zoals `size` of `color` . |
| `productListItems.selectedOptions.value` | Hiermee wordt de waarde van het kenmerk aangegeven, zoals `small` of `black` . |
| `productListItems.categories` | Bevat informatie over de categorie van een product. |
| `productListItems.categories.id` | De unieke id van de categorie. |
| `productListItems.categories.name` | De naam van de categorie. |
| `productListItems.categories.path` | Het pad naar de categorie. |

## Klantprofielgebeurtenissen

Profielgebeurtenissen die vanaf de server zijn vastgelegd, bevatten accountinformatie, zoals `accountCreated` , `accountUpdated` en `accountDeleted` . Deze gegevens worden gebruikt om belangrijke klantendetails te bevolken die nodig zijn om segmenten beter te bepalen of marketing campagnes, zoals het verzenden van aanbiedingen van de inschrijvingskorting, bevestigingen van de rekeningsverandering, etc. uitvoeren. Er zijn gelijkaardige profielgebeurtenissen die van [ worden gevangen storefront ](events.md#customer-profile-events).

>[!NOTE]
>
>Elke gebeurtenis van het klantenprofiel omvat ook het [`identityMap` ](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) gebied, dat het systeem geproduceerde identiteitskaart van de Klant van Commerce als primaire herkenningsteken voor het profiel en een e-mailidentiteitskaart omvat die als secundaire herkenningsteken wordt gebruikt.

### accountCreated

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een winkelier een account probeert te maken. | `userAccount.backofficeCreateProfile` |

#### Gegevens verzameld van accountCreated

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `person` | Bevat informatie over de klant. |
| `person.name` | Bevat informatie over de naam van de klant. |
| `person.name.firstName` | Bevat de voornaam van de klant. |
| `person.name.lastName` | Bevat de achternaam van de klant. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |

### accountUpdated

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een gebruiker een account probeert te bewerken. | `userAccount.backofficeUpdateProfile` |

#### Gegevens verzameld van accountBijgewerkt

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `person` | Bevat informatie over de klant. |
| `person.name` | Bevat informatie over de naam van de klant. |
| `person.name.firstName` | Bevat de voornaam van de klant. |
| `person.name.lastName` | Bevat de achternaam van de klant. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |

### accountDelted

| Beschrijving | XDM-gebeurtenisnaam |
|---|---|
| Wordt geactiveerd wanneer een gebruiker probeert een account te verwijderen. | `userAccount.backofficeDeleteProfile` |

#### Gegevens verzameld van accountVerwijderd

In de volgende tabel worden de gegevens beschreven die voor deze gebeurtenis zijn verzameld.

| Veld | Beschrijving |
|---|---|
| `person` | Bevat informatie over de klant. |
| `person.name` | Bevat informatie over de naam van de klant. |
| `person.name.firstName` | Bevat de voornaam van de klant. |
| `person.name.lastName` | Bevat de achternaam van de klant. |
| `personalEmail` | Een persoonlijk e-mailadres. |
| `personalEmail.address` | Het technische adres, bijvoorbeeld, `name@domain.com` zoals algemeen bepaald in RFC2822 en verdere normen. |
| `commerce.commerceScope` | Hiermee geeft u aan waar een gebeurtenis heeft plaatsgevonden (weergave, winkel, website, enzovoort). |
| `commerce.commerceScope.environmentID` | De milieu-id. Een alfanumerieke id van 32 cijfers, gescheiden door afbreekstreepjes. |
| `commerce.commerceScope.storeCode` | De unieke opslagcode. U kunt veel winkels per website hebben. |
| `commerce.commerceScope.storeViewCode` | De unieke code van de archiefmening. U kunt per winkel veel weergaven van uw winkel bekijken. |
| `commerce.commerceScope.websiteCode` | De unieke websitecode. U kunt veel websites in een omgeving hebben. |
