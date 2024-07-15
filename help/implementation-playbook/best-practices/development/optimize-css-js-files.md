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

Voor een meer responsieve Commerce-site optimaliseert u CSS- en JavaScript-bronbestanden (JS) en elimineert u bronnen voor het blokkeren van renderbestanden.

- **optimaliseer CSS en JS dossiers** - verklein de tijd die wordt vereist om CSS en de dossiers van JavaScript (JS) te laden door Adobe Commerce te vormen om, afzonderlijke dossiers in één enkel dossier samen te voegen, te minimaliseren en te bundelen.
- **elimineer renderen-blokkerende middelen** - overweeg het leveren van kritieke eigenschappen JS en CSS inline en het uitstellen van alle niet-kritieke stijlen JS/CSS. Voor begeleiding, zie [ teruggeven-blokkerende middelen ](https://web.dev/render-blocking-resources/) elimineren.

## Betrokken producten en versies

[ Alle gesteunde versies, 2.3 en later ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## CSS-bestanden samenvoegen of beperken

De tijd die nodig is om CSS- en JavaScript-bestanden (JS) te laden, kan worden verkort door afzonderlijke bestanden samen te voegen, te miniaturen en te bundelen in één bestand.

>[!IMPORTANT]
>
>Adobe Commerce op wolkeninfrastructuur loopt altijd op de wijze van de Productie en het is niet mogelijk om het anders te plaatsen, daarom moet u de bevel-lijn methode gebruiken om het samenvoegen, het minimaliseren, en het bundelen toe te laten.

Voeg of bundel geen dossiers samen als uw plaatsing HTTP/2 gebruikt. HTTP/2 downloadt statische bestanden asynchroon. Browsers moeten een volledig samengevoegd bestand downloaden voordat de bestandsinhoud kan worden verwerkt.

### Admin gebruiken

Om CSS samen te voegen of minificatie toe te laten, ga in [!UICONTROL **Admin** > **Slaat** > **Vestigend** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **CSS Montages**].

### De opdrachtregel gebruiken

CSS samenvoegen in Adobe Commerce inschakelen op cloudinfrastructuur:

1. Deze opdracht lokaal uitvoeren:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Wijzigingen vastleggen in het `app/etc/config.php` -bestand en opnieuw implementeren.

CSS-minificatie inschakelen in Adobe Commerce op cloudinfrastructuur:

1. Deze opdracht lokaal uitvoeren:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Wijzigingen vastleggen in het `app/etc/config.php` -bestand en opnieuw implementeren.

## JS-bestanden miniaturen

### Admin gebruiken

Op *Admin* sidebar, ga **Opslag** > **Montages** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **de Montages van JavaScript**.

### De opdrachtregel gebruiken

JS-minificatie in Adobe Commerce inschakelen op cloudinfrastructuur:

1. Deze opdracht lokaal uitvoeren:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Wijzigingen vastleggen in het `app/etc/config.php` -bestand en opnieuw implementeren.

## JS-bestanden samenvoegen en bundelen

U kunt het samenvoegen of het bundelen in Commerce Admin (het samenvoegen en het bundelen kunnen niet tezelfdertijd worden toegelaten) aanzetten: [!UICONTROL **Slaat** > **Montages** > **Configuratie** > **Geavanceerd** > **Ontwikkelaar** > **Montages van JavaScript**].

U kunt ook ingebouwde Adobe Commerce-bundeling (basisbundeling) inschakelen via de opdrachtregel:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Aanvullende informatie

- [Optimalisatie-instellingen aan de clientzijde](../../../performance/configuration.md#client-side-optimization-settings)
- [ Gids van de Gebruiker: Het optimaliseren van middeldossiers ](https://docs.magento.com/user-guide/system/file-optimization.html)
- [ Voorste Gids van de Ontwikkelaar: CSS het samenvoegen, minificatie, en plaatsprestaties ](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Geavanceerde JavaScript-pakketten](../../../performance/advanced-js-bundling.md)
