---
title: Onderhoudsmodus in- of uitschakelen
description: Voer de volgende stappen uit om aan te passen wat klanten zien wanneer uw Adobe Commerce- of Magento Open Source-implementatie niet beschikbaar is voor onderhoud.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Onderhoudsmodus in- of uitschakelen

De volgende handleiding verwijst naar een pagina voor de standaardonderhoudsmodus. Als u een aangepaste onderhoudspagina moet gebruiken, raadpleegt u [De aangepaste onderhoudspagina maken](../../upgrade/troubleshooting/maintenance-mode-options.md) onderwerp.

Adobe Commerce gebruikt [onderhoudsmodus](../../configuration/bootstrap/application-modes.md#maintenance-mode) om bootstrapping uit te schakelen. Het uitschakelen van bootstrapping is handig als u uw site onderhoudt, bijwerkt of opnieuw configureert.

De toepassing detecteert de onderhoudsmodus als volgt:

* Indien `var/.maintenance.flag` bestaat niet, de onderhoudsmodus is uitgeschakeld en de toepassing werkt normaal.
* Anders is de onderhoudsmodus ingeschakeld, tenzij `var/.maintenance.ip` bestaat.

  `var/.maintenance.ip` kan een lijst van IP adressen bevatten. Als een ingangspunt wordt betreden gebruikend HTTP en het cliëntIP adres beantwoordt aan één van de ingangen in die lijst, dan is de onderhoudswijze weg.

## De toepassing installeren

Voordat u deze opdracht gebruikt om de onderhoudsmodus in of uit te schakelen, moet u [de toepassing installeren](../advanced.md).

## Onderhoudsmodus in- of uitschakelen

Gebruik de `magento maintenance` CLI bevel om onderhoudswijze in of onbruikbaar te maken.

Opdrachtgebruik:

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

De `--ip=<ip address>` is een IP-adres dat wordt vrijgesteld van de onderhoudsmodus (bijvoorbeeld ontwikkelaars die het onderhoud uitvoeren). Om meer dan één IP adres in het zelfde bevel vrij te stellen, gebruik de optie veelvoudige tijden.

>[!NOTE]
>
>Gebruiken `--ip=<ip address>` with `magento maintenance:disable` Slaat de lijst van IPs voor later gebruik op. Om de lijst van vrijgestelde IPs te ontruimen, gebruik `magento maintenance:enable --ip=none` of zie [Handhaaf de lijst van vrijgestelde IP adressen](#maintain-the-list-of-exempt-ip-addresses).

De `bin/magento maintenance:status` geeft de status van de onderhoudsmodus weer.

Bijvoorbeeld, om onderhoudswijze zonder IP adresvrijstellingen toe te laten:

```bash
bin/magento maintenance:enable
```

Onderhoudsmodus inschakelen voor alle clients behalve 192.0.2.10 en 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Nadat u de toepassing op onderhoudswijze plaatst, moet u alle processen van de berichtrij van de consument tegenhouden.
Eén manier om deze processen te vinden is het uitvoeren van de `ps -ef | grep queue:consumers:start` en voert u vervolgens de opdracht `kill <process_id>` voor elke consument. In een veelvoudige knoopmilieu, herhaal deze taak op elke knoop.

## Handhaaf de lijst van vrijgestelde IP adressen

Om de lijst van vrijgestelde IP adressen te handhaven, kunt u of gebruiken `[--ip=<ip list>]` in de voorafgaande opdrachten of u kunt het volgende gebruiken:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

De `<ip address> .. <ip address>` syntaxis is een optionele lijst met IP-adressen die door spaties worden gescheiden.

De `--none` Hiermee wist u de lijst.

## Instellingen voor meerdere winkels

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Als u meerdere winkels wilt instellen, elk met een andere indeling en gelokaliseerde inhoud, geeft u de opdracht `$_GET['skin']` aan de bedoelde verwerker.

In het volgende voorbeeld gebruiken we een `503` type foutsjabloonbestand, waarvoor gelokaliseerde inhoud is vereist.

De constructor van de `Error_Processor` klasse accepteert een `skin` GET om de lay-out te wijzigen:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Dit kan ook worden toegevoegd aan een herschrijfregel in het dialoogvenster `.htaccess` bestand dat een `skin` aan de URL.

### $_GET[&#39;skin&#39;] parameter

Als u de opdracht `skin` parameter:

1. Controleer of de `.maintenance.flag` bestaat.
1. Neem nota van het gastheeradres, dat naar het verwijst `HTTP_HOST`of een andere variabele zoals ENV-variabelen.
1. Controleer of de `skin` parameter bestaat.
1. Stel de parameter in met de onderstaande herschrijfregels.

   Hier volgen enkele voorbeelden van herschrijfregels:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Kopieer de volgende bestanden:

   * `pub/errors/default/503.phtml` tot `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` tot `pub/errors/sub/styles.css`

1. Bewerk deze bestanden om gelokaliseerde inhoud te leveren in het dialoogvenster `503.phtml` bestand en aangepaste opmaak in het dialoogvenster `styles.css` bestand.

   Zorg ervoor dat de paden naar uw `errors` directory. De mapnaam moet overeenkomen met de URL-parameter die in het dialoogvenster `RewriteRule`. In het vorige voorbeeld wordt `sub` wordt gebruikt, die als parameter in `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>De [nginx](../../configuration/multi-sites/ms-nginx.md) Deze instelling moet worden toegevoegd voor instellingen voor meerdere winkels.
