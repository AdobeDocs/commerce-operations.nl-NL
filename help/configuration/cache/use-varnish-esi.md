---
title: Varnish ESI-blok
description: Leer meer over Edge Side Includes en hoe u deze kunt gebruiken om webpagina's in te sluiten.
badge: label="Bijgedragen door Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---

# Varnish ESI-blok

Edge Side Includes (ESI) zijn speciale richtlijnen die u kunt gebruiken om webpagina&#39;s op te nemen in andere webpagina&#39;s.

Een voorbeeld:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Varnish haalt inhoud op uit `http://domain.com/index.php/page_cache/block/esi/blocks` en vervangt de `<esi>` hiermee labelen.

## Handel en Varnish ESI

Het kader van de Handel leidt tot een markering ESI wanneer de volgende voorwaarden worden voldaan:

- De toepassing voor het in cache plaatsen is ingesteld op `Varnish Cache`
- Een XML-indeling `block` element wordt toegevoegd met een `ttl` attribute

### Voorbeeld

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

In het bovenstaande voorbeeld wordt `block` element voegt inhoud van toe `esi.phtml` de sjabloon wordt automatisch om de 30 seconden bijgewerkt naar een homepage en Varnish.

## Beperkingen

Op dit moment biedt Varnish geen ondersteuning voor ESI via HTTPS, zodat het automatisch overschakelt naar HTTP.

`Magento\PageCache\Observer\ProcessLayoutRenderElement`:

```php
    private function _wrapEsi(
        \Magento\Framework\View\Element\AbstractBlock $block,
        \Magento\Framework\View\Layout $layout
    ) {
    ....
        // Varnish does not support ESI over HTTPS must change to HTTP
        $url = substr($url, 0, 5) === 'https' ? 'http' . substr($url, 5) : $url;
        return sprintf('<esi:include src="%s" />', $url);
    }
```
