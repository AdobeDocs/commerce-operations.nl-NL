---
title: Een upgrade uitvoeren
description: Volg deze stappen om plaatsingen op-gebouw van Adobe Commerce te bevorderen.
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---


# Een upgrade uitvoeren

U kunt een upgrade uitvoeren _ter plaatse_ implementaties van de Adobe Commerce-toepassing vanaf de opdrachtregel als u de software hebt geïnstalleerd door:

- Het pakket Composer-metagegevens downloaden met de opdracht `composer create-project` gebruiken.
- Het gecomprimeerde archief installeren.

>[!NOTE]
>
>- Voor Adobe Commerce over infrastructuurprojecten in de cloud gaat u naar [Versie voor upgradeopdracht](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) in de Cloud Guide.
>- Gebruik deze methode niet om te bevorderen als u de bewaarplaats GitHub kloond. Zie [Een op een git gebaseerde installatie upgraden](../developer/git-installs.md).

De volgende instructies tonen u hoe te om te bevorderen gebruikend Composer pakketmanager. Adobe Commerce 2.4.2 introduceerde ondersteuning voor Composer 2. Als u probeert om van &lt;2.4.1 te bevorderen, moet u eerst aan een versie bevorderen die met Composer 2 (bijvoorbeeld, 2.4.2) compatibel is gebruikend Composer 1 _voor_ upgrade naar Composer 2 voor >2.4.2 upgrades. Bovendien moet u een [ondersteunde versie](../../installation/system-requirements.md) van PHP.

>[!WARNING]
>
>De procedure voor de modernisering van Adobe Commerce is gewijzigd. U moet een nieuwe versie van `magento/composer-root-update-plugin` pakket (zie [voorwaarden](../prepare/prerequisites.md)). Bovendien zijn de opdrachten voor de upgrade gewijzigd van `composer require magento/<package_name>` tot `composer require-commerce magento/<package_name>`.

## Voordat u begint

U moet de opdracht [upgradevoorwaarden](../prepare/prerequisites.md) om uw omgeving voor te bereiden voordat het upgradeproces wordt gestart.

## Pakketten beheren

>[!NOTE]
>
>Zie de voorbeelden aan het einde van deze sectie voor hulp bij het opgeven van verschillende releaseniveaus. Bijvoorbeeld kwaliteitspatches en beveiligingspatches. Neem contact op met Adobe Commerce Support als u deze pakketten niet kunt vinden in Composer.

1. Schakel over naar de onderhoudsmodus om toegang tot uw winkel tijdens het upgradeproces te voorkomen.

   ```bash
   bin/magento maintenance:enable
   ```

   Zie [Onderhoudsmodus in- of uitschakelen](../../installation/tutorials/maintenance-mode.md) voor extra opties. U kunt desgewenst een [aangepaste onderhoudsmodus, pagina](../troubleshooting/maintenance-mode-options.md).

1. De aanvang van het verbeteringsproces terwijl de asynchrone processen, zoals de consumenten van de berichtrij, lopen kan gegevenscorruptie veroorzaken. Schakel alle snijtaken uit om gegevensbeschadiging te voorkomen.

   _Adobe Commerce op cloudinfrastructuur:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. Start handmatig alle gebruikers in de wachtrij met berichten om ervoor te zorgen dat alle berichten worden verbruikt.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   Wacht tot de uitsnijdtaak is voltooid. U kunt de status van de taak controleren met een procesviewer of door het `ps aux | grep 'bin/magento queue'` meerdere keren gebruiken totdat alle processen zijn voltooid.

1. Maak een back-up van de `composer.json` bestand.

   ```bash
   cp composer.json composer.json.bak
   ```

1. Voeg specifieke pakketten toe of verwijder deze op basis van uw behoeften.

   Als u bijvoorbeeld een upgrade uitvoert van de Magento Open Source naar Adobe Commerce, verwijdert u het pakket Magento Open Source.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   U kunt voorbeeldgegevens ook bijwerken.

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
     ```

   - _Magento Open Source:_

     ```bash
     composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
     ```

1. Voer een upgrade uit op uw exemplaar met behulp van het volgende `composer require-commerce` opdrachtsyntaxis:

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   Opdrachtopties zijn:

   - `<product>` —(Vereist) Het pakket dat moet worden bijgewerkt. Voor installaties ter plaatse moet deze waarde ofwel `product-community-edition` of `product-enterprise-edition`.

   - `<version>` —(Vereist) De versie van Adobe Commerce waarnaar u een upgrade uitvoert. Bijvoorbeeld: `2.4.3`.

   - `--no-update` — (Vereist) maakt de automatische update van de gebiedsdelen onbruikbaar.

   - `--interactive-root-conflicts` — (Optioneel) Hiermee kunt u op interactieve wijze verouderde waarden uit eerdere versies of aangepaste waarden die niet overeenkomen met de versie waarnaar u de upgrade uitvoert, weergeven en bijwerken.

   - `--force-root-updates` —(Optioneel) Hiermee worden alle conflicterende aangepaste waarden genegeerd met de verwachte Commerce-waarden.

   - `--help` —(Optioneel) Bevat gebruiksgegevens voor de plug-in.

   Als geen van beide `--interactive-root-conflicts` noch `--force-root-updates` opgegeven, behoudt de opdracht de bestaande waarden in conflict en geeft een waarschuwingsbericht weer. Raadpleeg voor meer informatie over de plug-in de [README voor gebruik van insteekmodule](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. Werk de gebiedsdelen bij.

   ```bash
   composer update
   ```

### Voorbeeld - beschikbare versies weergeven

De volledige lijst met beschikbare 2.4.x-versies weergeven:

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### Voorbeeld - Kwaliteitspatch

Kwaliteitspatches bevatten voornamelijk functionele _en_ beveiligingsoplossingen. Soms kunnen ze echter wel nieuwe, achterwaartse compatibele functies bevatten. Gebruik Composer om een kwaliteitspatch te downloaden.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### Voorbeeld - Beveiligingspatch

Beveiligingspatches bevatten alleen beveiligingsoplossingen. Ze zijn ontworpen om het upgradeproces sneller en eenvoudiger te maken. Beveiligingspatches gebruiken de naamgevingsconventie van Composer `2.4.x-px`.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## Metagegevens bijwerken

1. Werk de `"name"`, `"version"`, en `"description"` in de `composer.json` bestand naar wens.

   >[!NOTE]
   >
   >De metagegevens in het dialoogvenster `composer.json` bestand is volledig oppervlakkig, niet functioneel.

1. Updates toepassen.

   ```bash
   composer update
   ```

1. Wis de `var/` en `generated/` submappen:

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >Als u een geheim voorgeheugenopslag buiten het filesystem, zoals Redis of Geheugen gebruikt, moet u het geheime voorgeheugen ook daar manueel ontruimen.

1. Werk het databaseschema en de gegevens bij.

   ```bash
   bin/magento setup:upgrade
   ```

1. Onderhoudsmodus uitschakelen.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(Optioneel)_ Start Varnish opnieuw.

   Als u Varnish gebruikt voor het in cache plaatsen van pagina&#39;s, begin het opnieuw:

   ```bash
   service varnish restart
   ```

## Uw werk controleren

Als u wilt controleren of de upgrade is gelukt, opent u de URL van de winkel in een webbrowser. Als de upgrade is mislukt, wordt de winkel niet correct geladen.

Als de toepassing met een  `We're sorry, an error has occurred while generating this email.` fout:

1. Herstellen [eigendom van het bestandssysteem en machtigingen](../../installation/prerequisites/file-system/configure-permissions.md) als een gebruiker met `root` rechten.
1. Wis de volgende directory&#39;s:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Controleer de winkel opnieuw in uw webbrowser.
