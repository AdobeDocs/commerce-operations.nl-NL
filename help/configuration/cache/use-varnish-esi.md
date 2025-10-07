---
title: Varnish ESI-blok
description: Leer meer over Varnish Edge Side Includes (ESI) en hoe u webpagina's voor Adobe Commerce kunt insluiten. Ontdek ESI-blokimplementatie en -optimalisatie.
badge: label="Bijgedragen door Konstantin G." type="Informative" url="https://github.com/goivvy" tooltip="Konstantin G."
feature: Configuration, Cache
exl-id: 7dccafa5-df79-4690-be5c-ff774c66bb2a
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 0%

---

# Varnish ESI-blok

Edge Side Includes (ESI) zijn speciale richtlijnen waarmee u webpagina&#39;s kunt opnemen in andere webpagina&#39;s.

Een voorbeeld:

```html
<div>
  <esi:include src="http://domain.com/index.php/page_cache/block/esi/blocks"/>
</div>
```

Varnish haalt inhoud van `http://domain.com/index.php/page_cache/block/esi/blocks` op en vervangt de `<esi>` -tag hiermee.

## Commerce en Varnish ESI

Het Commerce-framework maakt een ESI-tag wanneer aan de volgende voorwaarden wordt voldaan:

- De toepassing voor het in cache plaatsen is ingesteld op `Varnish Cache`
- Een XML-lay-outelement `block` wordt toegevoegd met een `ttl` -kenmerk

### Voorbeeld

`cms_index_index.xml`:

```xml
  <referenceContainer name="content">
      <block class="Magento\Framework\View\Element\Template" template="Magento_Paypal::esi.phtml" ttl="30"/>
   </referenceContainer>
```

In het bovenstaande voorbeeld voegt het element `block` inhoud van de `esi.phtml` -sjabloon toe aan een homepage en werkt Varnish deze automatisch om de 30 seconden bij.

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
