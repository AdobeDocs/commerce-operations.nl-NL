---
title: CSS- en JS-bronbestanden optimaliseren
description: Leer hoe u CSS- en JavaScript-bestanden (JS) voor Adobe Commerce-projecten kunt samenvoegen en miniaturen via Beheer of de opdrachtregel.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: a08560eb307638a36fdc52224c41bdf2c5d47763
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Bronbestanden optimaliseren

Voor een meer responsieve Commerce-site optimaliseert u CSS- en JavaScript-bronbestanden (JS) en elimineert u bronnen voor het blokkeren van renderbestanden.

- **optimaliseer CSS en JS dossiers** - verklein de tijd die wordt vereist om CSS en de dossiers van JavaScript (JS) te laden door Adobe Commerce te vormen om dossiers te miniaturen en te bundelen.
- **elimineer renderen-blokkerende middelen** - overweeg het leveren van kritieke eigenschappen JS en CSS inline en het uitstellen van alle niet-kritieke stijlen JS/CSS. Voor begeleiding, zie [&#x200B; teruggeven-blokkerende middelen &#x200B;](https://web.dev/render-blocking-resources/) elimineren.

## Betrokken producten en versies

[&#x200B; Alle gesteunde versies, 2.3 en later &#x200B;](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## CSS-bestanden samenvoegen of beperken

De tijd die nodig is om CSS- en JavaScript-bestanden (JS) te laden, kan worden verkort door afzonderlijke bestanden samen te voegen, te miniaturen en te bundelen in één bestand.

>[!IMPORTANT]
>
>Adobe Commerce op wolkeninfrastructuur loopt altijd op de wijze van de Productie en het is niet mogelijk om het anders te plaatsen, daarom moet u de bevel-lijn methode gebruiken om het samenvoegen, het minimaliseren, en het bundelen toe te laten.

Voeg of bundel geen dossiers samen als uw plaatsing HTTP/2 gebruikt. HTTP/2 downloadt statische bestanden asynchroon. Browsers moeten een volledig samengevoegd bestand downloaden voordat de bestandsinhoud kan worden verwerkt.

### Admin gebruiken

Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL CSS Settings]** om samenvoegen of miniaturen van CSS in te schakelen.

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

### [!UICONTROL Admin] gebruiken

Ga op de zijbalk van [!UICONTROL Admin] naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]** .

### De opdrachtregel gebruiken

JS-minificatie in Adobe Commerce inschakelen op cloudinfrastructuur:

1. Deze opdracht lokaal uitvoeren:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Wijzigingen vastleggen in het `app/etc/config.php` -bestand en opnieuw implementeren.

## JS-bestanden bundelen

U kunt bundeling inschakelen in de Commerce [!UICONTROL Admin] : **[!UICONTROL Stores]** > * **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]** .

>[!NOTE]
>
>Samenvoegen en bundelen kunnen niet tegelijkertijd worden ingeschakeld.

U kunt ook ingebouwde Adobe Commerce-bundeling (basisbundeling) inschakelen via de opdrachtregel:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## JS-bestanden samenvoegen (niet aanbevolen) {#merge-js-files}

>[!WARNING]
>
>We raden u niet aan **[!UICONTROL Merge JavaScript Files]** in te schakelen. Deze instelling is alleen ontworpen voor JavaScript die synchroon is geladen in de sectie **[!UICONTROL HEAD]** van de pagina en kan ertoe leiden dat het maken van pakketten en [!DNL RequireJS] -logica onjuist werken. Het wordt behouden voor achterwaartse verenigbaarheid slechts en verstrekt geen prestatiesvoordeel wanneer HTTP/2 wordt toegelaten.
>
>Als u **[!UICONTROL Merge JavaScript Files]** hebt ingeschakeld en problemen ondervindt, schakelt u deze uit voordat u patches toepast. Zie [&#x200B; ACSD-67908 &#x200B;](../../../tools/quality-patches-tool/patches-available-in-qpt/v1-1-73/acsd-67908.md) als u het samenvoegen niet kunt onbruikbaar maken.

## Aanvullende informatie

- [Optimalisatie-instellingen aan de clientzijde](../../../performance/configuration.md#client-side-optimization-settings)
- [&#x200B; het Bundelen uiteinden &#x200B;](../../../performance/configuration.md#bundling-tips) in *beste praktijken van de Configuratie* - derde het bundelen hulpmiddelen, HTTP/2, en begeleiding op afgekeurde JS en CSS samenvoegen
- [&#x200B; Gids van de Gebruiker: Het optimaliseren van middeldossiers &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [&#x200B; Voorste Gids van de Ontwikkelaar: CSS het samenvoegen, minificatie, en plaatsprestaties &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Geavanceerde JavaScript-pakketten](../../../performance/advanced-js-bundling.md)
