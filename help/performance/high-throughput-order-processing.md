---
title: Aanbevolen werkwijzen voor afhandelingsprestaties
description: Meer weten over best practices voor afhandelingsprestaties in Adobe Commerce? Ontdek implementatierichtlijnen en optimalisatiestrategieën.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor afhandelingsprestaties

Het [ controle ](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) proces in Adobe Commerce is een kritiek aspect van de storefront ervaring. Het baseert zich op de ingebouwde [ kar ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) en [ controle ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) mogelijkheden.

Prestaties zijn essentieel voor een goede gebruikerservaring. U kunt controleprestaties optimaliseren door de volgende opties voor **verwerking van de hoog-productieorde** te vormen:

- [ AsyncOrder ](#asynchronous-order-placement) - verwerkt asynchroon orden gebruikend een rij.
- [ Uitgestelde Totale Berekening ](#deferred-total-calculation) - verwijder berekeningen voor ordetabellen tot de controle begint.
- [ Controle van de Inventaris op de Lading van de Kar ](#disable-inventory-check) - verkies om inventarisbevestiging van wortelpunten over te slaan.
- [ het in evenwicht brengen van de Lading ](#load-balancing) - laat secundaire verbindingen voor het gegevensbestand MySQL en Redis instantie toe.

De opties AsyncOrder, Uitgestelde Totale Berekening, en de Controle van de Inventaris op de configuratieopties van de Lading van het Kart werken onafhankelijk. U kunt alle drie functies tegelijk gebruiken of de functies in een willekeurige combinatie in- en uitschakelen.

>[!NOTE]
>
>Gebruik geen aangepaste PHP-code om de ingebouwde winkelwagentje- en afrekenmogelijkheden aan te passen. Naast mogelijke prestatieproblemen kan het gebruik van aangepaste PHP-code leiden tot complexe upgrades en onderhoudsuitdagingen. Deze kwesties verhogen uw totale kosten van eigendom. Als op PHP-Gebaseerde kar en controle aanpassing onvermijdbaar is, gebruik [ de Marketplace van Adobe Commerce ](https://commercemarketplace.adobe.com/) - goedgekeurde uitbreidingen slechts. Alle marktplaatsuitbreidingen zijn onderworpen aan [ uitgebreide overzicht ](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) om te verifiëren dat zij de coderingsnormen van Adobe Commerce en beste praktijken ontmoeten.

## Asynchrone orderplaatsing

De _module van de Orde van 0} Async laat asynchrone ordeplaatsing toe, die de orde als_ merkt, plaatst de orde in een rij, en verwerkt orden van de rij op een eerste in-eerste-uit basis. `received` AsyncOrder is **gehandicapt** door gebrek.

Een klant voegt bijvoorbeeld een product toe aan zijn winkelwagentje en selecteert **[!UICONTROL Proceed to Checkout]** . Ze vullen het **[!UICONTROL Shipping Address]** -formulier in, selecteren hun voorkeur **[!UICONTROL Shipping Method]** , selecteren een betalingsmethode en plaatsen de bestelling. Het winkelwagentje wordt gewist, de bestelling wordt gemarkeerd als **[!UICONTROL Received]** , maar het aantal producten wordt nog niet aangepast en er wordt ook geen e-mail naar de klant verzonden. De bestelling wordt ontvangen, maar de gegevens van de bestelling zijn nog niet beschikbaar omdat de bestelling niet volledig is verwerkt. Het blijft in de rij tot de `placeOrderProcess` consument begint, verifieert de orde met de [ eigenschap van de inventariscontrole ](#disable-inventory-check) (die door gebrek wordt toegelaten), en werkt de orde als volgt bij:

- **Beschikbaar Product** - de veranderingen van de ordestatus in __ in afwachting van, wordt de producthoeveelheid aangepast, wordt een e-mail met ordedetails verzonden naar de klant, en de succesvolle ordedetails worden beschikbaar voor het bekijken in de **Orden en Keert** lijst met actionable opties, zoals reorder terug.
- **Product uit voorraad of lage levering** - de ordestatus verandert in _Geweigerd_, wordt de hoeveelheid van het Product niet aangepast, wordt een e-mail met ordedetails over de kwestie verzonden naar de klant, en de verworpen ordedetails worden beschikbaar in de **Orders en Keert** lijst met geen actiegable opties terug.

Gebruik de bevel-lijn interface om deze eigenschappen toe te laten, of geef het `app/etc/env.php` dossier volgens de overeenkomstige dossiers uit README die in de [_Gids van de Verwijzing van de Module_ ](https://developer.adobe.com/commerce/php/module-reference/) worden bepaald.

**om AsyncOrder** toe te laten:

U kunt AsyncOrder inschakelen via de opdrachtregelinterface:

```bash
bin/magento setup:config:set --checkout-async 1
```

Met de opdracht `set` schrijft u het volgende naar het `app/etc/env.php` -bestand:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Zie [ AsyncOrder ](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) in de _Gids van de Verwijzing van de Module_.

**om AsyncOrder** onbruikbaar te maken:

>[!WARNING]
>
>Alvorens de module AsyncOrder onbruikbaar te maken, moet u verifiëren dat _alle_ asynchrone ordeprocessen volledig zijn.

U kunt AsyncOrder uitschakelen via de opdrachtregelinterface:

```bash
bin/magento setup:config:set --checkout-async 0
```

Met de opdracht `set` schrijft u het volgende naar het `app/etc/env.php` -bestand:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibiliteit van AsyncOrder

AsyncOrder ondersteunt een beperkt aantal Adobe Commerce-functies.

| Categorie | Ondersteunde functie |
|------------------|--------------------------------------------------------------------------|
| Afhandelingstypen | ÉénPagina Afhandeling <br> StandaardAfhandeling <br> B2B Negotiable Citaat |
| Betalingsmethoden | Controle/Geldorde <br> Geld op Levering <br> Braintree <br> PayPal PayPal Pro |
| Verzendmethoden | Alle verzendmethoden worden ondersteund. |

De volgende eigenschappen worden **niet** gesteund door AsyncOrder, maar blijven synchroon werken:

- Betalingsmethoden zijn niet opgenomen in de lijst met ondersteunde functies
- Uitchecken van meerdere adressen
- Maken van beheerdervolgorde

#### Ondersteuning voor web-API

Wanneer de module AsyncOrder is ingeschakeld, worden de volgende REST-eindpunten en GraphQL-mutaties asynchroon uitgevoerd:

**REST:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQL biedt geen ondersteuning voor het asynchroon plaatsen van verhandelbare aanhalingstekens.

#### Uitgezonderd betalingsmethoden

Ontwikkelaars kunnen bepaalde betaalmethoden expliciet uitsluiten van asynchrone orderplaatsing door deze aan de array `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` toe te voegen. Orders die gebruikmaken van uitgesloten betalingsmethoden worden synchroon verwerkt.

### Negotiable Quote Async Order

De _Negotiable Volgorde van het Citaat Async_ B2B module laat u toe om orde punten asynchroon voor de `NegotiableQuote` functionaliteit te bewaren. U moet AsyncOrder en NegotiableQuote toegelaten hebben.

## Uitgestelde totale berekening

De _Uitgestelde Totale module van de Berekening_ optimaliseert het controleproces door de totale berekening uit te stellen tot het voor het winkelwagentje of tijdens de definitieve controlestappen wordt gevraagd. Wanneer toegelaten, slechts berekent subtotal als klant producten aan het het winkelwagentje toevoegt.

Uitgestelde Totale Berekening is **gehandicapt** door gebrek. Gebruik de bevel-lijn interface om deze eigenschappen toe te laten, of geef het `app/etc/env.php` dossier volgens de overeenkomstige dossiers uit README die in de [_Gids van de Verwijzing van de Module_ ](https://developer.adobe.com/commerce/php/module-reference/) worden bepaald.

**om DeferredTotalCalcalculation** toe te laten:

U kunt DeferredTotalCalcalculation toelaten gebruikend de bevel-lijn interface:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

Met de opdracht `set` schrijft u het volgende naar het `app/etc/env.php` -bestand:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**om DeferredTotalCalcalculation** onbruikbaar te maken:

U kunt DeferredTotalCalcalculation onbruikbaar maken gebruikend de bevel-lijn interface:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

Met de opdracht `set` schrijft u het volgende naar het `app/etc/env.php` -bestand:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Zie [ DeferredTotalCalculating ](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) in de _Gids van de Verwijzing van de Module_.

### Vaste productbelasting

Als Uitgestelde totale berekening is ingeschakeld, wordt de Vaste productbelasting (Vaste productbelasting) niet opgenomen in de productprijs en het subtotaal van de karretjes van de minikaart nadat het product aan het winkelwagentje is toegevoegd. De FPT-berekening wordt uitgesteld wanneer een product aan de minikaart wordt toegevoegd. Het FPT wordt correct weergegeven in het winkelwagentje nadat de laatste afhandeling is uitgevoerd.

## Inventariscontrole uitschakelen

_laat Overzicht op de Lading van de Kar_ toe het globale plaatsen bepaalt of om een inventariscontrole uit te voeren wanneer het laden van een product in de kar. Als u het voorraadcontroleproces uitschakelt, worden de prestaties voor alle afhandelingsstappen verbeterd, met name wanneer u werkt met bulkproducten in het winkelwagentje.

Indien uitgeschakeld, wordt de inventariscontrole niet uitgevoerd wanneer een product aan het winkelwagentje wordt toegevoegd. Als deze inventariscontrole wordt overgeslagen, zouden sommige uit-van-voorraadscenario&#39;s andere soorten fouten kunnen werpen. Een inventariscontrole _komt altijd voor_ bij de stap van de ordeplaatsing, zelfs wanneer onbruikbaar gemaakt.

**laat de Controle van de Inventaris op de Lading van de Kunst toe** wordt toegelaten (reeks aan ja) door gebrek. Om de inventariscontrole onbruikbaar te maken wanneer het laden van de kar, plaats **[!UICONTROL Enable Inventory Check On Cart Load]** aan `No` in Admin UI **Opslag** > **Configuratie** > **Catalogus** > **Voorraad** > **sectie van de Opties van de Beeld 11}.** Zie [ Globale Opties ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) en [ Inventaris van de Catalogus ](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) in de _Gids van de Gebruiker_ vormen.

## Taakverdeling

U kunt helpen lading over verschillende knopen in evenwicht brengen door secundaire verbindingen voor het gegevensbestand MySQL en instantie Redis toe te laten.

Adobe Commerce kan meerdere databases of Redis-instanties asynchroon lezen. Als u Commerce op wolkeninfrastructuur gebruikt, kunt u de secundaire verbindingen vormen door de [ waarden MYSQL_USE_SLAVE_CONNECTION ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) en [ REDIS_USE_SLAVE_CONNECTION ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) in het `.magento.env.yaml` dossier uit te geven. Slechts één knoop moet read-write verkeer behandelen, zodat leidt het plaatsen van de variabelen aan `true` tot het creëren van een secundaire verbinding voor read-only verkeer. Stel de waarden in op `false` als u een bestaande alleen-lezen verbindingsarray uit het `env.php` -bestand wilt verwijderen.

Voorbeeld van het bestand `.magento.env.yaml` :

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
