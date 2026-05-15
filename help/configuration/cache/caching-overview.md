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

Adobe Commerce vertrouwt op een architectuur met meerdere lagen voor caching om databasebelasting te verminderen, redundante verwerking tot een minimum te beperken en de levering van pagina&#39;s te versnellen. Op het toepassingsniveau, handhaaft Commerce meer dan een dozijn [&#x200B; geheim voorgeheugentypes &#x200B;](../cli/manage-cache.md#clean-and-flush-cache-types) - zoals configuratie, lay-out, blok HTML, en inzameling-elk waarvan u aan een specifieke opslagsteun zoals [&#x200B; kunt leiden Redis &#x200B;](config-redis.md) of [&#x200B; Valkey &#x200B;](config-valkey.md). Voor volledig-pagina caching, adviseert Adobe sterk [&#x200B; Varnish &#x200B;](config-varnish.md), een accelerator van HTTP die caching pagina&#39;s van geheugen direct dient. De extra lagen zoals [&#x200B; L2 caching &#x200B;](level-two-cache.md) en [&#x200B; statische inhoud die &#x200B;](static-content-signing.md) ondertekenen verbeteren prestaties voor hoog-verkeer, multi-knoopplaatsingen verder.

Deze gids verklaart hoe elke caching laag werkt en toont u hoe te om voorkanten, achtergronden, en geavanceerde opties te vormen om uw plaatsingsvereisten aan te passen.

## Voorkanten in cache plaatsen

Een cachefront is een interface tussen Commerce en de back-end van de cacheopslag. U kunt veelvoudige frontends, elk met verschillende achterste montages bepalen, en dan specifieke [&#x200B; geheim voorgeheugentypes &#x200B;](../cli/manage-cache.md#clean-and-flush-cache-types) toewijzen aan elk front.  Voor configuratiedetails, zie [&#x200B; cache vooraf instelt &#x200B;](cache-types.md).

## Achtergronden in cache plaatsen

Een cache-backend is het onderliggende opslagmechanisme voor gegevens in de cache. Commerce biedt een standaard back-end voor het bestandssysteem, maar u kunt andere back-endbestanden, zoals Redis of Valkey, configureren voor betere prestaties en schaalbaarheid. Voor details op de beschikbare opties, zie [&#x200B; achterste opties van het Geheime voorgeheugen &#x200B;](cache-options.md).

## Volledige caching met Varnish

[&#x200B; Vernis Geheime voorgeheugen &#x200B;](config-varnish.md) is een accelerator van HTTP die volledige pagina&#39;s in geheugen in cache plaatst. Adobe raadt Varnish ten zeerste aan voor productieomgevingen omdat het aanzienlijk sneller is dan de ingebouwde cache van volledige pagina&#39;s.

>[!NOTE]
>
>Varnish werkt als een reverse-proxy vóór uw webserver en vereist geen wijzigingen in de Commerce cache-backendconfiguratie.

## L2-caching (twee niveaus)

[&#x200B; L2 geheime voorgeheugen &#x200B;](level-two-cache.md) slaat geheim voorgeheugengegevens op elke Webknoop terwijl het gebruiken van een ver geheime voorgeheugen (Redis of Valkey) als bron van waarheid op. Dit vermindert netwerkverkeer tussen uw Webknopen en het verre geheime voorgeheugen, dat prestaties voor hoge verkeersplaatsen verbetert.

## Statische inhoud in cache plaatsen

[&#x200B; Statische inhoud die &#x200B;](static-content-signing.md) ondertekent ongeldig het browser geheime voorgeheugen voor statische middelen (CSS, JavaScript, beelden) door een plaatsingsversie in dossier URLs in te bedden.

## Caching terminologie

[!DNL Commerce] gebruikt de volgende terminologie in cache:

- **Frontend** — Een interface of een gateway om opslag in het voorgeheugen onder te brengen, die door [&#x200B; Magento\Framework\Cache\Frontend &#x200B;](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend) wordt uitgevoerd.
- **types van Geheime voorgeheugen** — Één van de ingebouwde types die van [!DNL Commerce] worden voorzien (zoals `config`, `layout`, `block_html`, `full_page`) of a [&#x200B; douanetype &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Achtergrond** — Specificeert de details van [&#x200B; geheim voorgeheugenopslag &#x200B;](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), die door [&#x200B; Magento\Framework\Cache\Backend &#x200B;](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend) wordt uitgevoerd.
- **dubbel-vlakke achterste** — Slaat geheim voorgeheugenverslagen in twee achtergronden op: een lokale (snelle) cache en een externe (gedeelde) cache. Zie [&#x200B; L2 geheim voorgeheugenconfiguratie &#x200B;](level-two-cache.md).

## Configuratieopties

Cacheconfiguratie wordt opgeslagen in twee bestanden:

- `<magento_root>/app/etc/di.xml` — De algemene configuratie voor injectie van afhankelijkheid. Wijzig dit bestand om het cachevooreinde van `default` te wijzigen.
- `<magento_root>/app/etc/env.php` — Omgevingsspecifieke configuratie. Wijzig dit bestand om de voorkanten van de aangepaste cache te configureren. Dit bestand negeert de equivalente configuratie in `di.xml` .

Voor details op frontend-aan-type afbeelding en de syntaxis van de geheim voorgeheugenconfiguratie, zie:

- [&#x200B; vorm geheim voorhoede van het geheime voorgeheugen &#x200B;](cache-types.md) - associeer een geheim voorhoede met specifieke geheim voorgeheugentypes
- [&#x200B; de achterste van het Geheime voorgeheugen opties &#x200B;](cache-options.md) - de optieverwijzing van de achterkant van de achterkant van het achtereind
