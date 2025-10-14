---
source-git-commit: dbb758dd76fd9ea2f2e2e64fb87ea03d1c426263
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---
# Adobe Commerce-releaseopmerkingen (v2.4.9-alpha3)

## Hooglichten in v2.4.9-alpha3

De volgende markeringen zijn van toepassing op de Adobe Commerce 2.4.9-alpha3-release.

### Braintree

#### Google betalen via het accountgebied wordt automatisch berekend

In Magento 2.4.9-alpha3 kunnen klanten nu hun Google Pay-kaarten via het accountgebied bewaren wanneer Google Pay Vault in Braintree is ingeschakeld. Geëxtraheerde kaarten worden weergegeven onder opgeslagen betalingsmethoden, kunnen worden gebruikt voor toekomstige aankopen bij afhandeling en kunnen door de klant worden verwijderd. Dit breidt de factureringsondersteuning uit van kaarten en PayPal naar Google Pay.

_BUNDLE-3459_

#### Magento-bestelling koppelen aan Braintree Portal Order

In Magento 2.4.9-alpha3 wordt nu een Braintree Portal-koppeling toegevoegd aan de ordergegevens in Magento Admin. Als u op de koppeling klikt, wordt de bijbehorende transactie geopend in de Braintree Portal (op een nieuw tabblad) met de Merchant ID en de Transactie ID van de Magento-order. Dit staat directe kruisverwijzing toe zonder het registreren in beide systemen afzonderlijk.

_BUNDLE-3461_

#### Real Time Account Updater (RTAU)

De functie Real Time Account Updater (RTAU) in Magento 2.4.9-alpha3 voor Braintree zorgt ervoor dat de gegevens van een in licentie gegeven Visa-, Mastercard- en Discover-kaart automatisch worden bijgewerkt wanneer kaarten verlopen of worden vervangen. Hierdoor worden mislukte betalingen geminimaliseerd, blijft Magento Vault actueel en worden niet-ondersteunde typen (prepaid, Apple Pay, Google Pay) zonder fouten overgeslagen.

_BUNDLE-3462_

#### Ondersteuning voor ELO-kaarttypen voor Braintree Card Payments

In Magento 2.4.9-alpha3 is ondersteuning voor het type ELO-kaart toegevoegd aan Braintree Payments. Beheerders kunnen nu ELO inschakelen in de creditcardconfiguratie en klanten kunnen met succes bestellingen plaatsen met ELO-kaarten bij het afrekenen, zodat transacties probleemloos verlopen via Braintree.

_BUNDLE-3464_

### Kader

#### Migratie van RabbitMQ naar Apache ActiveMQ

_AC-14558_

#### De afhankelijkheid van Chart.js van de verbetering aan de recentste versie

De afhankelijkheid van chart.js wordt bevorderd tot de recentste versie 4.5.0

_AC-15133 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/657f983e)_

#### Migratie van Laminas MVC

Adobe Commerce heeft een native MVC-implementatie geïntroduceerd, die de verouderde Laminas MVC vervangt, om te zorgen voor compatibiliteit en stabiliteit op lange termijn boven PHP 8.5. Deze wijziging versterkt de prestaties, vermindert de externe afhankelijkheden en biedt een meer toekomstbestendige basis voor Commerce

_AC-15160_

### Beveiliging

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [&#x200B; Bulletin van de Veiligheid van Adobe APSB25-94 &#x200B;](https://helpx.adobe.com/security/products/magento/apsb25-94.html).

{{$include /help/_includes/release-notes/highlights/security-2025-10.md}}
