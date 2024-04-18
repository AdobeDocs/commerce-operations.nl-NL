---
title: CSS- en JS-bronbestanden optimaliseren
description: Leer hoe u CSS- en JavaScript-bestanden (JS) voor Adobe Commerce-projecten kunt samenvoegen en miniaturen via Beheer of de opdrachtregel.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Bronbestanden optimaliseren

Voor een meer responsieve Commerce-site optimaliseert u CSS- en JavaScript-bronbestanden (JS) en elimineert u bronnen voor het blokkeren van renderingen.

- **CSS- en JS-bestanden optimaliseren**—Verminder de tijd die nodig is om CSS- en JavaScript-bestanden (JS) te laden door Adobe Commerce te configureren voor het samenvoegen, miniaturen en bundelen van afzonderlijke bestanden in één bestand.
- **Renderblokkeringsbronnen elimineren**—Overweeg inline kritieke JS- en CSS-functies te leveren en alle niet-kritieke JS/CSS-stijlen uit te stellen. Voor richtsnoeren, zie [Renderblokkeringsbronnen elimineren](https://web.dev/render-blocking-resources/).

## Betrokken producten en versies

[Alle ondersteunde versies, 2.3 en hoger](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## CSS-bestanden samenvoegen of beperken

De tijd die nodig is om CSS- en JavaScript-bestanden (JS) te laden, kan worden verkort door afzonderlijke bestanden samen te voegen, te miniaturen en te bundelen in één bestand.

>[!IMPORTANT]
>
>Adobe Commerce op wolkeninfrastructuur loopt altijd op de wijze van de Productie en het is niet mogelijk om het anders te plaatsen, daarom moet u de bevel-lijn methode gebruiken om het samenvoegen, het minimaliseren, en het bundelen toe te laten.

Voeg of bundel geen dossiers samen als uw plaatsing HTTP/2 gebruikt. HTTP/2 downloadt statische bestanden asynchroon. Browsers moeten een volledig samengevoegd bestand downloaden voordat de bestandsinhoud kan worden verwerkt.

### Admin gebruiken

Als u CSS samenvoegen of miniaturen wilt inschakelen, gaat u naar de [!UICONTROL **Beheerder** > **Winkels** > **Instelling** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **CSS-instellingen**].

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

Op de *Beheerder* zijbalk, ga naar **Winkels** > **Instellingen** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **JavaScript-instellingen**.

### De opdrachtregel gebruiken

JS-minificatie in Adobe Commerce inschakelen op cloudinfrastructuur:

1. Deze opdracht lokaal uitvoeren:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Wijzigingen vastleggen in de `app/etc/config.php` bestand en opnieuw implementeren.

## JS-bestanden samenvoegen en bundelen

U kunt samenvoeging of bundeling inschakelen in Commerce Admin (samenvoeging en bundeling kunnen niet tegelijkertijd worden ingeschakeld): [!UICONTROL **Winkels** > **Instellingen** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **JavaScript-instellingen**].

U kunt ook ingebouwde Adobe Commerce-bundeling (basisbundeling) inschakelen via de opdrachtregel:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Aanvullende informatie

- [Optimalisatie-instellingen aan de clientzijde](../../../performance/configuration.md#client-side-optimization-settings)
- [Gebruikershandleiding: Bronbestanden optimaliseren](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Frontend Developer Guide: CSS samenvoegen, miniaturen en siteprestaties](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Geavanceerde JavaScript-bundeling](../../../performance/advanced-js-bundling.md)
