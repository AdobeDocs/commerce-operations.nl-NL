---
title: CSS- en JS-bronbestanden optimaliseren
description: Leer hoe u CSS- en JavaScript-bestanden (JS) voor Adobe Commerce-projecten kunt samenvoegen en miniaturen via Beheer of de opdrachtregel.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: e6e8a2d7ef059265dbcbfcd6be117828a639f6d6
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Bronbestanden optimaliseren

Voor een meer reagerende plaats van de Handel, optimaliseer CSS en JavaScript (JS) middeldossiers en elimineer render-blokkerende middelen.

- **CSS- en JS-bestanden optimaliseren**—Verminder de tijd die nodig is om CSS- en JavaScript-bestanden (JS) te laden door Adobe Commerce te configureren voor het samenvoegen, miniaturen en bundelen van afzonderlijke bestanden in één bestand.
- **Renderblokkeringsbronnen elimineren**—Overweeg inline kritieke JS- en CSS-functies te leveren en alle niet-kritieke JS/CSS-stijlen uit te stellen. Zie voor richtsnoeren [Renderblokkeringsbronnen elimineren](https://web.dev/render-blocking-resources/).

## Betrokken producten en versies

[Alle ondersteunde versies, 2.3 en hoger](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse
- Magento Open Source

## CSS-bestanden samenvoegen of miniaturen

De tijd die nodig is om CSS- en JavaScript-bestanden (JS) te laden, kan worden verkort door afzonderlijke bestanden samen te voegen, te miniaturen en te bundelen in één bestand.

>[!IMPORTANT]
>
>Adobe Commerce op wolkeninfrastructuur loopt altijd op de wijze van de Productie en het is niet mogelijk om het anders te plaatsen, daarom moet u de bevel-lijn methode gebruiken om het samenvoegen, het minimaliseren, en het bundelen toe te laten.

### Admin gebruiken

Als u CSS samenvoegen of miniaturen wilt inschakelen, gaat u naar de [!UICONTROL **Beheer** > **Winkels** > **Instelling** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **CSS-instellingen**].

### De opdrachtregel gebruiken

CSS samenvoegen in Adobe Commerce inschakelen op cloudinfrastructuur:

1. Deze opdracht lokaal uitvoeren:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Wijzigingen vastleggen in de `app/etc/config.php` bestand en opnieuw implementeren.

CSS-minificatie inschakelen in Adobe Commerce op cloudinfrastructuur:

1. Deze opdracht lokaal uitvoeren:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Wijzigingen vastleggen in de `app/etc/config.php` bestand en opnieuw implementeren.

## JS-bestanden miniaturen

### Admin gebruiken

Op de *Beheer* zijbalk, ga naar **Winkels** > **Instellingen** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **JavaScript-instellingen**.

### De opdrachtregel gebruiken

JS-minificatie in Adobe Commerce inschakelen op cloudinfrastructuur:

1. Deze opdracht lokaal uitvoeren:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Wijzigingen vastleggen in de `app/etc/config.php` bestand en opnieuw implementeren.

## JS-bestanden samenvoegen en bundelen

U kunt samenvoeging of bundeling inschakelen in de Commerce Admin (samenvoeging en bundeling kunnen niet tegelijkertijd worden ingeschakeld): [!UICONTROL **Winkels** > **Instellingen** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **JavaScript-instellingen**].

U kunt ook ingebouwde Adobe Commerce-bundeling (basisbundeling) inschakelen via de opdrachtregel:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Aanvullende informatie

- [Optimalisatie-instellingen aan de clientzijde](../../../performance/configuration.md#client-side-optimization-settings)
- [Handboek: Bronbestanden optimaliseren](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Frontend Developer Guide: Samenvoegen, miniaturen en siteprestaties van CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Geavanceerde JavaScript-bundeling](../../../performance/advanced-js-bundling.md)

