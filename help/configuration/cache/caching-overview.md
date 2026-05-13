---
title: Overzicht en configuratieopties in cache plaatsen
description: Leer over caching in Adobe Commerce, met inbegrip van backend opslag, frontend configuratie, en volledige paginaconcering met Varnish, Redis, Valkey, en L2 geheime voorgeheugen.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 9cd0f2a84772e2d68fd15a00651216abfa9ec91c
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Overzicht en configuratieopties van caching

Adobe Commerce vertrouwt op een architectuur met meerdere lagen voor caching om databasebelasting te verminderen, redundante verwerking tot een minimum te beperken en de levering van pagina&#39;s te versnellen. Op het toepassingsniveau, handhaaft Commerce meer dan een dozijn [ geheim voorgeheugentypes ](../cli/manage-cache.md#clean-and-flush-cache-types) - zoals configuratie, lay-out, blok HTML, en inzameling-elk waarvan u aan een specifieke opslagsteun zoals [ kunt leiden Redis ](config-redis.md) of [ Valkey ](config-valkey.md). Voor volledig-pagina caching, adviseert Adobe sterk [ Varnish ](config-varnish.md), een accelerator van HTTP die caching pagina&#39;s van geheugen direct dient. De extra lagen zoals [ L2 caching ](level-two-cache.md) en [ statische inhoud die ](static-content-signing.md) ondertekenen verbeteren prestaties voor hoog-verkeer, multi-knoopplaatsingen verder.

Deze gids verklaart hoe elke caching laag werkt en toont u hoe te om voorkanten, achtergronden, en geavanceerde opties te vormen om uw plaatsingsvereisten aan te passen.

## Voorkanten in cache plaatsen

Een cachefront is een interface tussen Commerce en de back-end van de cacheopslag. U kunt veelvoudige frontends, elk met verschillende achterste montages bepalen, en dan specifieke [ geheim voorgeheugentypes ](../cli/manage-cache.md#clean-and-flush-cache-types) toewijzen aan elk front.  Voor configuratiedetails, zie [ cache vooraf instelt ](cache-types.md).

## Achtergronden in cache plaatsen

Een cache-backend is het onderliggende opslagmechanisme voor gegevens in de cache. Commerce biedt een standaard back-end voor het bestandssysteem, maar u kunt andere back-endbestanden, zoals Redis of Valkey, configureren voor betere prestaties en schaalbaarheid. Voor details op de beschikbare opties, zie [ achterste opties van het Geheime voorgeheugen ](cache-options.md).

## Volledige caching met Varnish

[ Vernis Geheime voorgeheugen ](config-varnish.md) is een accelerator van HTTP die volledige pagina&#39;s in geheugen in cache plaatst. Adobe raadt Varnish ten zeerste aan voor productieomgevingen omdat het aanzienlijk sneller is dan de ingebouwde cache van volledige pagina&#39;s.

>[!NOTE]
>
>Varnish werkt als een reverse-proxy vóór uw webserver en vereist geen wijzigingen in de Commerce cache-backendconfiguratie.

## L2-caching (twee niveaus)

[ L2 geheime voorgeheugen ](level-two-cache.md) slaat geheim voorgeheugengegevens op elke Webknoop terwijl het gebruiken van een ver geheime voorgeheugen (Redis of Valkey) als bron van waarheid op. Dit vermindert netwerkverkeer tussen uw Webknopen en het verre geheime voorgeheugen, dat prestaties voor hoge verkeersplaatsen verbetert.

## Statische inhoud in cache plaatsen

[ Statische inhoud die ](static-content-signing.md) ondertekent ongeldig het browser geheime voorgeheugen voor statische middelen (CSS, JavaScript, beelden) door een plaatsingsversie in dossier URLs in te bedden.

## Caching terminologie

[!DNL Commerce] gebruikt de volgende terminologie in cache:

- **Frontend** — Een interface of een gateway om opslag in het voorgeheugen onder te brengen, die door [ Magento\Framework\Cache\Frontend ](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend) wordt uitgevoerd.
- **types van Geheime voorgeheugen** — Één van de ingebouwde types die van [!DNL Commerce] worden voorzien (zoals `config`, `layout`, `block_html`, `full_page`) of a [ douanetype ](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Achtergrond** — Specificeert de details van [ geheim voorgeheugenopslag ](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), die door [ Magento\Framework\Cache\Backend ](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend) wordt uitgevoerd.
- **dubbel-vlakke achterste** — Slaat geheim voorgeheugenverslagen in twee achtergronden op: een lokale (snelle) cache en een externe (gedeelde) cache. Zie [ L2 geheim voorgeheugenconfiguratie ](level-two-cache.md).

## Configuratieopties

Cacheconfiguratie wordt opgeslagen in twee bestanden:

- `<magento_root>/app/etc/di.xml` — De algemene configuratie voor injectie van afhankelijkheid. Wijzig dit bestand om het cachevooreinde van `default` te wijzigen.
- `<magento_root>/app/etc/env.php` — Omgevingsspecifieke configuratie. Wijzig dit bestand om de voorkanten van de aangepaste cache te configureren. Dit bestand negeert de equivalente configuratie in `di.xml` .

Voor details op frontend-aan-type afbeelding en de syntaxis van de geheim voorgeheugenconfiguratie, zie:

- [ vorm geheim voorhoede van het geheime voorgeheugen ](cache-types.md) - associeer een geheim voorhoede met specifieke geheim voorgeheugentypes
- [ de achterste van het Geheime voorgeheugen opties ](cache-options.md) - de optieverwijzing van de achterkant van de achterkant van het achtereind
