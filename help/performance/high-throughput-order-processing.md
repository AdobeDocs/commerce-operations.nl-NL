---
title: Verwerking van bestellingen met hoge doorvoer
description: Optimaliseer de plaatsing van bestellingen en het afrekenen van bestellingen voor uw Adobe Commerce- of Magento Open Source-implementatie.
source-git-commit: 0a902d7fe967bbcee5019fea83e5be66ce2aefd0
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 0%

---


# Bestelverwerking met hoge doorvoer

U kunt de plaatsing van de bestelling en de kassa optimaliseren door de volgende reeks modules te configureren voor **verwerking van bestellingen met hoge doorvoer**:

- [AsyncOrder](#asynchronous-order-placement)—Verwerkt asynchroon orden gebruikend een rij.
- [NegotiableQuoteAsyncOrder](#negotiable-quote-asyn-order)—Verwerkt asynchroon NegotiableQuote orde sparen punten.
- [UitgesteldeTotaleBerekening](#deferred-total-calculation)—Definieert berekeningen voor ordertotalen tot het afrekenen begint.

Alle functies werken onafhankelijk. U kunt alle functies tegelijk gebruiken of functies in een willekeurige combinatie in- en uitschakelen.

Gebruik de opdrachtregelinterface om deze functies in te schakelen of bewerk de interface `app/etc/env.php` bestand volgens de overeenkomstige README-bestanden die zijn gedefinieerd in het dialoogvenster [_Referentiehandleiding module_][mrg].

## Asynchrone orderplaatsing

De _Async-volgorde_ de module laat asynchrone orde plaatsing toe, die de orde als merkt `received`, plaatst de orde in een rij, en verwerkt orden van de rij op een eerste-in-eerste-uit basis. AsyncOrder is **uitgeschakeld** standaard.

Een klant voegt bijvoorbeeld een product toe aan zijn winkelwagentje en selecteert **[!UICONTROL Proceed to Checkout]**. Ze vullen de **[!UICONTROL Shipping Address]** formulier, selecteert u de gewenste **[!UICONTROL Shipping Method]**, selecteert u een betalingsmethode en plaatst u de bestelling. Het winkelwagentje wordt gewist, de bestelling wordt gemarkeerd als **[!UICONTROL Received]**, maar het aantal producten wordt nog niet aangepast en er wordt ook geen e-mail naar de klant gestuurd. De bestelling wordt ontvangen, maar de gegevens van de bestelling zijn nog niet beschikbaar omdat de bestelling niet volledig is verwerkt. Het blijft in de rij tot de `placeOrderProcess` de consument begint, verifieert de orde met [inventariscontrole](#disable-inventory-check) (standaard ingeschakeld) en werkt de volgorde als volgt bij:

- **Product beschikbaar**—de orderstatus verandert in _In behandeling_, wordt het productaantal aangepast, wordt een e-mail met bestelgegevens naar de klant verzonden en worden de gegevens van de succesvolle bestelling beschikbaar voor weergave in het **Orders en retourzendingen** lijst met opties voor handelingen, zoals herschikken.
- **Product uit voorraad of lage voorraad**—de orderstatus verandert in _Geweigerd_, wordt het aantal producten niet aangepast, wordt een e-mail met bestelgegevens over de uitgave naar de klant gestuurd en worden de gegevens van de geweigerde bestelling beschikbaar in de **Orders en retourzendingen** lijst zonder opties voor handelingen.

AsyncOrder inschakelen:

U kunt AsyncOrder inschakelen via de opdrachtregelinterface:

```bash
bin/magento setup:config:set --checkout-async 1
```

De `set` opdracht schrijft het volgende naar de `app/etc/env.php` bestand:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Zie [AsyncOrder] in de _Referentiehandleiding module_.

AsyncOrder uitschakelen:

>[!WARNING]
>
>Voordat u de module AsyncOrder uitschakelt, moet u controleren of _alles_ asynchrone ordeprocessen zijn voltooid.

U kunt AsyncOrder uitschakelen via de opdrachtregelinterface:

```bash
bin/magento setup:config:set --checkout-async 0
```

De `set` opdracht schrijft het volgende naar de `app/etc/env.php` bestand:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibiliteit van AsyncOrder

AsyncOrder ondersteunt een beperkte set [!DNL Commerce] functies.

| Categorie | Ondersteunde functie |
|---------------- | -----------------------|
| Afhandelingstypen | Afhandeling van één pagina<br>Standaard uitchecken<br>B2B-onderhandelbare offerte |
| Betalingsmethoden | Cheque/postwissel<br>Onder rembours<br>Braintree<br>PayPal PayFlow Pro |
| Verzendmethoden | Alle verzendmethoden worden ondersteund. |

De volgende functies zijn **niet** ondersteund door AsyncOrder, maar blijft synchroon werken:

- Betalingsmethoden zijn niet opgenomen in de lijst met ondersteunde functies
- Uitchecken van meerdere adressen
- Maken van beheerdervolgorde

#### Ondersteuning voor web-API

Wanneer de module AsyncOrder wordt toegelaten, de volgende REST eindpunten en de mutaties GraphQL asynchroon lopen:

**REST:**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL biedt geen ondersteuning voor het asynchroon plaatsen van verhandelbare aanhalingstekenorders.

#### Uitgezonderd betalingsmethoden

Ontwikkelaars kunnen bepaalde betaalmethoden expliciet uitsluiten van Asynchronous Order-plaatsing door deze toe te voegen aan de `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` array. Orders die gebruikmaken van uitgesloten betalingsmethoden worden synchroon verwerkt.

## Negotiable Quote Async Order

De _Negotiable Quote Async Order_ In de B2B-module kunt u volgorde-items asynchroon opslaan voor de `NegotiableQuote` functionaliteit. U moet AsyncOrder en NegotiableQuote toegelaten hebben.

## Uitgestelde totale berekening

De _Uitgestelde totale berekening_ optimaliseert het afrekenproces door de totale berekening uit te stellen tot deze voor het winkelwagentje of tijdens de laatste afrekenstappen wordt aangevraagd. Wanneer toegelaten, slechts berekent subtotal als klant producten aan het het winkelwagentje toevoegt.

UitgesteldeTotaleBerekening is **uitgeschakeld** standaard.

UitgesteldeTotaleBerekening inschakelen:

U kunt DeferredTotalCalcalculation toelaten gebruikend de bevel-lijn interface:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

De `set` opdracht schrijft het volgende naar de `app/etc/env.php` bestand:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

UitgesteldeTotalCalcalculation uitschakelen:

U kunt DeferredTotalCalcalculation onbruikbaar maken gebruikend de bevel-lijn interface:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

De `set` opdracht schrijft het volgende naar de `app/etc/env.php` bestand:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Zie [UitgesteldeTotaalBerekenen] in de _Referentiehandleiding module_.

### Vaste productbelasting

Wanneer UitgesteldeTotaleBerekening is ingeschakeld, wordt de Vaste Productbelasting (FPT) niet opgenomen in de productprijs en het subtotaal van de karretjes van de minikart nadat het product aan het winkelwagentje is toegevoegd. De FPT-berekening wordt uitgesteld wanneer een product aan de minikaart wordt toegevoegd. Het FPT wordt correct weergegeven in het winkelwagentje nadat de laatste afhandeling is uitgevoerd.

## Inventariscontrole uitschakelen

De _Inventaris bij laden van winkelwagentje inschakelen_ globale instelling bepaalt of een inventariscontrole moet worden uitgevoerd wanneer een product in de winkelwagen wordt geladen. Als u het voorraadcontroleproces uitschakelt, worden de prestaties voor alle afhandelingsstappen verbeterd, met name wanneer u werkt met bulkproducten in het winkelwagentje.

Indien uitgeschakeld, wordt de inventariscontrole niet uitgevoerd wanneer een product aan het winkelwagentje wordt toegevoegd. Als deze inventariscontrole wordt overgeslagen, zouden sommige uit-van-voorraadscenario&#39;s andere soorten fouten kunnen werpen. Een inventariscontrole _altijd_ komt bij de stap van de ordeplaatsing voor, zelfs wanneer onbruikbaar gemaakt.

Inventaris bij laden van winkelwagentje inschakelen is **enabled** standaard.

Als u de inventariscontrole tijdens het laden van het winkelwagentje wilt uitschakelen, stelt u **[!UICONTROL Enable Inventory Check On Cart Load]** tot `No` in de beheerinterface. Zie [Globale opties configureren][global] en [Catalogusoverzicht][inventory] in de _Handboek_.

<!-- link definitions -->

[Apply patches]: https://devdocs.magento.com/cloud/project/project-patch.html
[global]: https://docs.magento.com/user-guide/catalog/inventory-options-global.html
[inventory]: https://docs.magento.com/user-guide/configuration/catalog/inventory.html
[Install extensions]: https://devdocs.magento.com/extensions/install/
[cloud-extensions]: https://devdocs.magento.com/cloud/howtos/install-components.html

[mrg]: https://devdocs.magento.com/guides/v2.4//mrg/intro.html
[AsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-async-order.html
[UitgesteldeTotaalBerekenen]: https://devdocs.magento.com/guides/v2.4/mrg/module-deferred-total-calculating.html
[NegotiableQuoteAsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-negotiable-quote-async-order.html
