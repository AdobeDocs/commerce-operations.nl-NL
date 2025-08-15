---
title: Onderhoudsmodus in- of uitschakelen
description: Voer de volgende stappen uit om aan te passen wat klanten zien wanneer uw Adobe Commerce-implementatie niet beschikbaar is voor onderhoud.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: a5dbefda6b77d993756143ef0e7270425f824c44
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Onderhoudsmodus in- of uitschakelen

De volgende handleiding verwijst naar een pagina voor de standaardonderhoudsmodus. Als u een pagina van het douaneonderhoud moet gebruiken, zie [ het onderwerp van de pagina van het douaneonderhoud ](../../upgrade/troubleshooting/maintenance-mode-options.md) creëren.

Adobe Commerce gebruikt [ onderhoudswijze ](../../configuration/bootstrap/application-modes.md#maintenance-mode) om bootstrapping onbruikbaar te maken. Het uitschakelen van bootstrapping is handig als u uw site onderhoudt, bijwerkt of opnieuw configureert.

De toepassing detecteert de onderhoudsmodus als volgt:

* Als `var/.maintenance.flag` bestaat, is de onderhoudsmodus ingeschakeld en retourneert de toepassing een onderhoudspagina van 503.
* Als `var/.maintenance.ip` bestaat en de client-IP overeenkomt met een van de IP-adresitems in dit bestand, wordt de onderhoudspagina genegeerd voor de aanvraag.

## De toepassing installeren

Alvorens u dit bevel gebruikt om onderhoudswijze toe te laten of onbruikbaar te maken, moet u [ de toepassing ](../advanced.md) installeren.

## Onderhoudsmodus in- of uitschakelen

Gebruik het `magento maintenance` CLI bevel om onderhoudswijze in of onbruikbaar te maken.

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

De optie `--ip=<ip address>` is een IP-adres dat wordt vrijgesteld van de onderhoudsmodus (bijvoorbeeld ontwikkelaars die het onderhoud uitvoeren). Om meer dan één IP adres in het zelfde bevel vrij te stellen, gebruik de optie veelvoudige tijden.

>[!NOTE]
>
>Als u `--ip=<ip address>` gebruikt met `magento maintenance:disable` , wordt de lijst met IP&#39;s opgeslagen zodat u deze later kunt gebruiken. Om de lijst van vrijgestelde IPs te ontruimen, gebruik `magento maintenance:enable --ip=none` of zie [ de lijst van vrijgestelde IP adressen ](#maintain-the-list-of-exempt-ip-addresses) handhaven.

De opdracht `bin/magento maintenance:status` geeft de status van de onderhoudsmodus weer.

Bijvoorbeeld, om onderhoudswijze zonder IP adresvrijstellingen toe te laten:

```bash
bin/magento maintenance:enable
```

De onderhoudsmodus inschakelen voor alle clients behalve 192.0.2.10 en 192.0.2.11 :

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Nadat u de toepassing op onderhoudswijze plaatst, moet u alle processen van de berichtrij van de consument tegenhouden.
U kunt deze processen vinden door de opdracht `ps -ef | grep queue:consumers:start` uit te voeren en vervolgens de opdracht `kill <process_id>` voor elke consument uit te voeren. In een veelvoudige knoopmilieu, herhaal deze taak op elke knoop.

## Handhaaf de lijst van vrijgestelde IP adressen

Als u de lijst met vrijgestelde IP-adressen wilt bijhouden, kunt u de optie `[--ip=<ip list>]` in de voorafgaande opdrachten gebruiken of het volgende gebruiken:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

De syntaxis van `<ip address> .. <ip address>` is een optionele lijst met door spaties gescheiden IP-adressen die moet worden vrijgesteld.

Met de optie `--none` wist u de lijst.

## Instellingen voor meerdere winkels

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Als u meerdere winkels wilt instellen, elk met een andere indeling en gelokaliseerde inhoud, geeft u de parameter `$_GET['skin']` door aan de bedoelde processor.

In het volgende voorbeeld gebruiken we een `503` sjabloonbestand voor typefouten, waarvoor gelokaliseerde inhoud is vereist.

De constructor van de klasse `Error_Processor` accepteert een GET-parameter `skin` om de lay-out te wijzigen:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Dit kan ook worden toegevoegd aan een herschrijfregel in het `.htaccess` -bestand dat een `skin` -parameter aan de URL toevoegt.

### $_GET [ &quot;skin&quot;] parameter

De parameter `skin` gebruiken:

1. Controleer of `.maintenance.flag` bestaat.
1. Maak een notitie van het hostadres, dat verwijst naar `HTTP_HOST` of een andere variabele, zoals ENV-variabelen.
1. Controleer of de parameter `skin` bestaat.
1. Stel de parameter in met de onderstaande herschrijfregels.

   Hier volgen enkele voorbeelden van herschrijfregels:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [ NC ]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [ L ]

1. Kopieer de volgende bestanden:

   * `pub/errors/default/503.phtml` t/m `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` t/m `pub/errors/sub/styles.css`

1. Bewerk deze bestanden om gelokaliseerde inhoud in het `503.phtml` -bestand en aangepaste opmaak in het `styles.css` -bestand te bieden.

   Zorg ervoor dat de paden naar de map `errors` verwijzen. De mapnaam moet overeenkomen met de URL-parameter die in `RewriteRule` wordt aangegeven. In het vorige voorbeeld wordt de map `sub` gebruikt. Deze is opgegeven als een parameter in de map `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>[ nginx ](../../configuration/multi-sites/ms-nginx.md) het plaatsen moet voor multi-store montages worden toegevoegd.
