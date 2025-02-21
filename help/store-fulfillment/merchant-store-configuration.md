---
title: Configuratie van Merchant Stores
description: Uitgebreide Inventory management-bronnen instellen als winkels.
role: Admin
level: Experienced
feature: Shipping/Delivery, Inventory, Configuration
source-git-commit: cb69e11cd54a3ca1ab66543c4f28526a3cf1f9e1
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 0%

---

# Configuratie van Merchant Stores (Source)

Deze oplossing verbetert de native Inventory management-mogelijkheden door voorraadbronnen uit te breiden met op activiteiten gerichte functies voor handelaren.

- Geografische coördinaten toevoegen voor de opslaglocatie
- Wijs de bron aan als een [!DNL Store Pickup Location] en geef de beschikbare verzendmogelijkheden op (Verzenden naar winkel, Verzenden vanuit winkel)
- Geef beschikbare ophaalopties op (in-store of curbside), aangepaste ophaalinstructies en andere informatie om informatie over het ophalen van gegevens en instructies aan klanten door te geven

De termijnen _bron_ en _handelaarplaats_ worden gebruikt onderling verwisselbaar. Alle verslagen zijn inventarisbronnen, maar de bronnen kunnen ook winkelplaatsen, afhankelijk van de configuratiemontages zijn.

De configuratie Merchant Stores beheren vanuit de beheerfunctie: **[!UICONTROL Stores > Inventory > Sources >  Edit Source]** .

>[!NOTE]
>
>Tijdens het opstellingsproces, zou het noodzakelijk kunnen zijn om het geheime voorgeheugen te spoelen nadat u bronnen creeert of bestaande bronnen bijwerkt.

## **Algemeen**

<table>
<tbody>
<tr>
<th>Veld</th>
<th>Beschrijving</th>
<th>Toepassingsgebied</th>
<th>Vereist</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Coördinaat in de lengterichting van de locatie van de winkel. Deze vereiste informatie wordt gebruikt in plaatsonderzoek en kaartplaatsing op de storefront ervaring. De waarde moet exact overeenkomen met het adres van de winkel om de validatie te kunnen doorstaan.</td>
<td>Algemeen</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Lengtegraadcoördinaat van de locatie van de winkel. Deze vereiste informatie wordt gebruikt in plaatsonderzoek en kaartplaatsing op de storefront ervaring. De waarde moet exact overeenkomen met het adres van de winkel om de validatie te kunnen doorstaan.</td>
<td>Algemeen</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Wijs de bron aan als beschikbare ophaallocatie voor de winkel. Deze instelling bepaalt of de bron wordt gesynchroniseerd en aan bezoekers wordt weergegeven.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>Vorm schip-aan-opslagmogelijkheden op het bronniveau. Zie de optie [Algemene configuratie](enable-general.md) <strong>[!UICONTROL Enable Ship To Store] voor meer informatie
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Coördinaat in de lengterichting van de locatie van de winkel. Deze vereiste informatie wordt gebruikt in plaatsonderzoek en kaartplaatsing op de storefront ervaring. De waarde moet exact overeenkomen met het adres van de winkel om de validatie te kunnen doorstaan.</td>
<td>Algemeen</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Lengtegraadcoördinaat van de locatie van de winkel. Deze vereiste informatie wordt gebruikt in plaatsonderzoek en kaartplaatsing op de storefront ervaring. De waarde moet exact overeenkomen met het adres van de winkel om de validatie te kunnen doorstaan.</td>
<td>Algemeen</td>
<td>Ja</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Wijs de bron aan als beschikbare ophaallocatie voor de winkel. Deze instelling bepaalt of de bron wordt gesynchroniseerd en aan bezoekers wordt weergegeven.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>Vorm schip-aan-opslagmogelijkheden op het bronniveau. Zie de optie [Algemene configuratie](enable-general.md) <strong>[!UICONTROL Enable Ship To Store]</strong> voor meer informatie.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>Vorm schip-van-opslag mogelijkheden op het bronniveau. Zie de optie [Algemene configuratie](enable-general.md) [!UICONTROL Enable Ship From Store] voor meer informatie.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td>Algemeen</td>
<td>Nee</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
<td>Vorm schip-van-opslag mogelijkheden op het bronniveau. Zie de optie [Algemene configuratie](enable-general.md) [!UICONTROL Enable Ship From Store] voor meer informatie.</td>
<td>Algemeen</td>
<td>Nee</td>
</tr>
</tbody>
</table>



| **Gebied** | **Beschrijving** | **Reikwijdte** | **Vereist** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | Coördinaat in de lengterichting van de locatie van de winkel. Deze vereiste informatie wordt gebruikt in plaatsonderzoek en kaartplaatsing op de storefront ervaring. De waarde moet exact overeenkomen met het adres van de winkel om de validatie te kunnen doorstaan. | Algemeen | Ja |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | Lengtegraadcoördinaat van de locatie van de winkel. Deze vereiste informatie wordt gebruikt in plaatsonderzoek en kaartplaatsing op de storefront ervaring. De waarde moet exact overeenkomen met het adres van de winkel om de validatie te kunnen doorstaan. | Algemeen | Ja |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | Wijs de bron aan als beschikbare ophaallocatie voor de winkel. Deze instelling bepaalt of de bron wordt gesynchroniseerd en aan bezoekers wordt weergegeven. | Algemeen | Nee |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | Vorm schip-aan-opslagmogelijkheden op het bronniveau. Voor meer informatie, zie de ](enable-general.md) optie van de Configuratie 0} Algemene **[!UICONTROL Enable Ship To Store]**.[ | Algemeen | Nee |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | Vorm schip-van-opslag mogelijkheden op het bronniveau. Voor meer informatie, zie de ](enable-general.md) optie van de Configuratie 0} Algemene [!UICONTROL Enable Ship From Store][ | Algemeen | Nee |

{style="table-layout:auto"}

## Configuratie van ophaallocatie

| **Gebied** | **Beschrijving** | **Reikwijdte** | **Vereist** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | Een van de twee ophaalopties. [!DNL In-Store Pickup] verwijst naar de mogelijkheid voor een klant om de locatie in de winkel te betreden waar deze zijn bestelling kan ophalen. </br></br> wanneer toegelaten, zou deze optie aan de klant tijdens controle kunnen worden voorgesteld. </br></br> Deze optie treedt ook de globale configuratie aan [!UICONTROL Enable In-store Pickup] met voeten die op [!UICONTROL Delivery Method] voor [!UICONTROL In-store Pickup] werd gevormd | Algemeen | Nee |
| **In-Store instructies van de Bestelwagen**</br>`Extension Attribute: store_pickup_instructions` | Een klantgericht bericht dat aan de klant in **wordt geleverd Orde Klaar voor Bestelwagen in het e-mailbericht van de Opslag**. | Algemeen | Nee |
| **sta Krullen**</br>`Extension Attribute: curbside_enabled` toe | Een van de twee ophaalopties. Met de curbside-levering kan een klant zijn voertuig op een bepaalde plaats in de winkel parkeren. In dit scenario, wordt de orde geleverd aan de klant door een opslagvennoot. </br></br> Wanneer toegelaten, kan deze optie aan de klant tijdens controle worden voorgesteld. Tijdens het inchecken kan de klant ook worden gevraagd om zijn voertuig en parkeerplaats te beschrijven. </br></br> Deze optie treedt ook de globale configuratie aan **toe laat Bestelwagen Curbside** die op de **Methode van de Levering** voor **In-store Bestelwagen** werd gevormd | Algemeen | Nee |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | Een aanpasbaar bericht dat in het e-mailbericht van [!UICONTROL Order Ready For Pickup in Store] aan de klant wordt geleverd. | Algemeen | Nee |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | Het aantal minuten dat is vereist voordat een bestelling wordt ontvangen, opgepakt en klaar is om te worden opgepakt. </br></br> Deze informatie wordt gebruikt vertoning geschat tijden voor orderopname aan klanten op de website.</br></br> het plaatsen van deze optie treedt de globale configuratie voor **Geschatte Tijd van het Lood van de Bestelwagen** met voeten die voor de **Methode van de Levering** in de **In-store configuratie van de Bestelwagen** wordt gevormd. | Algemeen | Nee |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | Label dat het aantal minuten weergeeft totdat een bestelling klaar is om te worden opgepakt.</br></br> wanneer het aanpassen van dit etiket, kunt u code %1 gebruiken om uw **Geschatte Tijd van de Lood van de Bestelwagen** op te nemen.</br></br> Als u deze optie instelt, wordt de algemene configuratie voor [!UICONTROL Estimated Pickup Time Label] geconfigureerd voor de [!UICONTROL Delivery Method] in de [!UICONTROL In-store Pickup] vervangen. | Algemeen | Nee |

### **het Openen Uren**

| **Gebied** | **Beschrijving** | **Reikwijdte** | **Vereist** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | The timezone of the merchant store location. Stel voor elke dag de openings- en sluitingstijden in.</br></br> deze montages worden gebruikt om geschatte inzamelingstijden, en in uitvoeringsdienst rapportering te optimaliseren. | Algemeen | Ja |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | De openingstijden voor de locatie van de winkel. </br></br> Deze informatie kan worden gebruikt om geschatte inzamelingstijden, en in uitvoeringsdienst rapportering te optimaliseren. | Algemeen | Ja |

### Interfaceopties voor Inchecken van ervaring configureren



| **Gebied** | **Beschrijving** | **Reikwijdte** | **Vereist** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | Geef op of de locatie van de winkel parkeerplaatsen voor curbside heeft. </br></br> wanneer toegelaten, kunt u beschikbare parkeerplaatsen vormen. | Algemeen | Nee |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | Geef tijdens het winkelen aan of parkeerplaatsidentificatie vereist is voor klanten.</br></br> Indien toegelaten, wordt de klant ertoe aangezet om hun parkeerplaats bij aankomst te specificeren. Als deze optie is uitgeschakeld, kan de klant deze invoer overslaan. | Algemeen | Nee |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | De beschikbare parkeerplaatsen beschikbaar op deze winkelplaats van de koophandel voor krullende bestelwagen. Gebruik de opgegeven interface om elke vlek een naam te geven.</br></br> U hoeft niet elke parkeerplaats een naam te geven, alleen de plaatsen die zijn toegewezen aan de rand. U hebt bijvoorbeeld rijen A-G voor parkeren beschikbaar, maar alleen de eerste 8 punten van rij A zijn bedoeld voor ophalen op de rand. In dit scenario kunt u 8 punten definiëren, bijvoorbeeld A1, A2, A3, enzovoort. | Algemeen | Nee |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | Als deze instelling is ingeschakeld, kan de klant zijn parkeerplaats tijdens inchecken beschrijven. | Algemeen | Nee |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | Geef op of de verzameling van voertuigkleuren door de klant tijdens de inchecken moet worden ondersteund. </br></br> de beschikbare selecties voor [!UICONTROL Car Color] worden gevormd in Admin [ systeemmontages voor de Controle-binnen Ervaring ](check-in-experience-setup.md). | Algemeen | Nee |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | Geef tijdens het inchecken op of voor klanten kleuridentificatie van het voertuig is vereist.</br></br> Indien toegelaten, wordt de klant ertoe aangezet om de kleur van hun voertuig bij aankomst te specificeren. Als deze optie is uitgeschakeld, kan de klant deze invoer overslaan. | Algemeen | Nee |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | Geef aan of de verzameling van voertuigproducten van de klant tijdens de inchecken moet worden ondersteund.</br></br> de beschikbare selecties voor [!UICONTROL Car Make] worden gevormd in Admin [ systeemmontages voor de Controle-binnen Ervaring ](check-in-experience-setup.md). | Algemeen | Nee |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | Geef tijdens het inchecken aan of identificatie van het voertuig vereist is voor klanten.</br></br> Indien toegelaten, wordt de klant ertoe aangezet om het merk van hun voertuig bij aankomst te specificeren. Als deze optie is uitgeschakeld, kan de klant deze invoer overslaan. | Algemeen | Nee |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | Specificeer of om inzameling van extra informatie van de klant tijdens Controle-binnen te steunen. | Algemeen | Nee |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | Geef tijdens het inchecken op of er aanvullende informatie nodig is voor klanten. </br></br> Indien toegelaten, wordt de klant ertoe aangezet om extra informatie op aankomst in te gaan. Als deze optie is uitgeschakeld, kan de klant deze invoer overslaan. | Algemeen | Nee |
