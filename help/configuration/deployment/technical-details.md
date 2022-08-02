---
title: Technische details
description: Lees over de technische details van pijpleidingsplaatsing, types van configuraties, en geadviseerde werkschema's.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---


# Technische details

Dit onderwerp bespreekt technische implementatiedetails over pijpleidingsplaatsing in Handel 2.2 en later. De verbeteringen kunnen in de volgende gebieden worden verdeeld:

- [Configuratiebeheer](#configuration-management)
- [Wijzigingen in de beheerder](#changes-in-the-admin)
- [Uitsnede installeren en verwijderen](#install-and-remove-cron)

Dit onderwerp bespreekt ook het [aanbevolen workflow](#recommended-workflow) voor pijpleidingsplaatsing en verstrekt sommige voorbeelden om u te helpen begrijpen hoe het werkt.

Voordat u aan de slag gaat, bekijkt u de [Vereisten voor uw ontwikkeling, bouw, en productiesystemen](../deployment/prerequisites.md).

## Configuratiebeheer

Om u toe te laten om de configuratie van uw ontwikkeling en productiesystemen te synchroniseren en te handhaven, gebruik de volgende met voeten getreden regeling.

![Hoe de waarden van configuratievariabelen worden bepaald](../../assets/configuration/override-flow-diagram.png)

Zoals het diagram toont, worden de configuratiewaarden gebruikt in de volgende orde:

1. Omgevingsvariabelen, indien aanwezig, overschrijven alle andere waarden.
1. Uit de gedeelde configuratiebestanden `env.php` en `config.php`. Waarden in `env.php` waarden overschrijven in `config.php`.
1. Uit waarden die zijn opgeslagen in de database.
1. Als geen waarde in om het even welke die bronnen bestaat, wordt de standaardwaarde of ONGELDIG gebruikt.

### De gedeelde configuratie beheren

De gedeelde configuratie is opgeslagen in `app/etc/config.php`, die onder broncontrole moeten staan.

Stel de gedeelde configuratie in de beheerdersconfiguratie in uw ontwikkeling in (of Adobe Commerce in de cloud-infrastructuur) _integratie_) en schrijft de configuratie naar `config.php` met de [`magento app:config:dump` command](../cli/export-configuration.md).

### De systeemspecifieke configuratie beheren

De systeem-specifieke configuratie wordt opgeslagen in `app/etc/env.php`, die _niet_ in broncontrole zijn.

Stel de systeemspecifieke configuratie in het beheersysteem in uw ontwikkelsysteem (of Adobe Commerce op integratie van de cloud-infrastructuur) in en schrijf de configuratie naar `env.php` met de [`magento app:config:dump` command](../cli/export-configuration.md).

Met deze opdracht schrijft u ook gevoelige instellingen naar `env.php`.

### De vertrouwelijke configuratie beheren

De gevoelige configuratie wordt ook opgeslagen in `app/etc/env.php`.

U kunt de gevoelige configuratie op om het even welke volgende manieren beheren:

- Omgevingsvariabelen
- Sla de vertrouwelijke configuratie op in `env.php` op uw productiesysteem met behulp van de [`magento config:set:sensitive` command](../cli/set-configuration-values.md)

### Configuratie-instellingen vergrendeld in de beheerder

Willekeurige configuratie-instellingen in `config.php` of `env.php` zijn vergrendeld in de beheerder; Dat wil zeggen dat deze instellingen niet kunnen worden gewijzigd in Admin.
Gebruik de [`magento config:set` of `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) om de instellingen in het dialoogvenster `config.php` of `env.php` bestanden.

## Admin Commerce

Admin vertoont het volgende gedrag terwijl in productiemodus:

- U kunt cavetypen niet in- of uitschakelen in Beheer
- Ontwikkelinstellingen zijn niet beschikbaar (**Winkels** > Instellingen > **Configuratie** > Geavanceerd > **Ontwikkelaar**), met inbegrip van:

   - CSS, JavaScript en HTML miniaturen
   - CSS en JavaScript samenvoegen
   - LESS-compilatie op server- of clientzijde
   - Inline-vertalingen
   - Zoals eerder besproken, elke configuratie die in `config.php` of `env.php` is vergrendeld en kan niet worden bewerkt in Beheer.
   - U kunt de beheerlandinstelling alleen wijzigen in talen die worden gebruikt door geïmplementeerde thema&#39;s

      In de volgende afbeelding ziet u een voorbeeld van de **Accountinstelling** > **Landinstelling interface** lijst in Admin die slechts twee opgestelde scènes toont:

      ![U kunt de beheerlandinstelling alleen wijzigen in geïmplementeerde landinstellingen](../../assets/configuration/split-deploy-admin-locale.png)

- U kunt de configuratie van de landinstelling voor een bereik niet wijzigen met de beheerfunctie.

   Wij adviseren makend deze veranderingen alvorens op de wijze van de Productie over te schakelen.

   U kunt de landinstelling nog steeds configureren met behulp van omgevingsvariabelen of de `config:set` CLI-opdracht met het pad `general/locale/code`.

## Uitsnede installeren en verwijderen

In versie 2.2 helpen we u voor het eerst uw snijtaak in te stellen door de [`magento cron:install` command](../cli/configure-cron-jobs.md). Met deze opdracht stelt u een tab in als de gebruiker die de opdracht uitvoert.

U kunt ook de tab verwijderen met de `magento cron:remove` gebruiken.

## Aanbevolen workflow voor distributie van pijpleidingen

Het volgende diagram toont hoe wij u aanbevelen pijpleidingsplaatsing te gebruiken om de configuratie te beheren.

![Aanbevolen workflow voor distributie van pijpleidingen](../../assets/configuration/split-deploy-workflow.png)

### Ontwikkelingssysteem

Op uw ontwikkelingssysteem, brengt u configuratieveranderingen in Admin aan en produceert de gedeelde configuratie, `app/etc/config.php` en de systeemspecifieke configuratie, `app/etc/env.php`. De code van de Handel van de controle en de gedeelde configuratie in broncontrole en duw het aan de bouwstijlserver.

U zou uitbreidingen ook moeten installeren en de code van de Handel op het ontwikkelingssysteem aanpassen.

Op uw ontwikkelingssysteem:

1. Stel de configuratie in de beheerder in.

1. Gebruik de `magento app:config:dump` bevel om de configuratie aan het dossiersysteem te schrijven.

   - `app/etc/config.php` is de gedeelde configuratie, die alle montages bevat _behalve_ gevoelige en systeemspecifieke instellingen. Dit bestand moet zich in de broncontrole bevinden.
   - `app/etc/env.php` is de systeem-specifieke configuratie, die montages bevat die aan een bepaald systeem (bijvoorbeeld, hostnames en havenaantallen) uniek zijn. Dit bestand moet _niet_ in broncontrole zijn.

1. Voeg uw gewijzigde code en de gedeelde configuratie aan broncontrole toe.

1. Voer de volgende opdrachten uit om gegenereerde php-code en statische elementbestanden tijdens de ontwikkeling te verwijderen:

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Nadat de bevelen in werking stellen om de activa te ontruimen, produceert de Handel werkende dossiers.

>[!WARNING]
>
>Wees voorzichtig met de bovenstaande aanpak. Het verwijderen van `.htacces`s bestand in de `generated` of `pub` kan problemen veroorzaken.

### Systeem bouwen

Het bouwstijlsysteem compileert code en produceert statische meningsdossiers voor thema&#39;s die in Handel worden geregistreerd. Er is geen verbinding met de gegevensbank Handel nodig; zij heeft alleen de handelscodebase nodig.

Op uw bouwstijlsysteem:

1. Trek het gedeelde configuratiedossier van broncontrole.
1. Gebruik de `magento setup:di:compile` gebruiken om code te compileren.
1. Gebruik de `magento setup:static-content:deploy -f` gebruiken om statische bestanden bij te werken.
1. Controleer de updates in broncontrole.

>[!INFO]
>
>Zie [Implementatiestrategieën voor statische weergavebestanden](../cli/static-view-file-strategy.md).

### Productiesysteem

Op uw productiesysteem (namelijk uw levende opslag) trekt u geproduceerde activa en codeupdates van broncontrole en plaatst systeem-specifieke en gevoelige configuratiemontages gebruikend de bevellijn of milieuvariabelen.

Op uw productiesysteem:

1. Start de onderhoudsmodus.
1. Trek code en configuratietoepassingen van broncontrole.
1. Als u Adobe Commerce gebruikt, stop wachtrijarbeiders.
1. Gebruik de `magento app:config:import` bevel om configuratieveranderingen in het productiesysteem in te voeren.
1. Als u componenten installeerde die het gegevensbestandschema veranderden, looppas `magento setup:upgrade --keep-generated` om het databaseschema en de gegevens bij te werken, met behoud van gegenereerde statische bestanden.
1. Als u systeemspecifieke instellingen wilt instellen, gebruikt u de `magento config:set` commando- of omgevingsvariabelen.
1. Als u vertrouwelijke instellingen wilt instellen, gebruikt u de `magento config:sensitive:set` commando- of omgevingsvariabelen.
1. Reiniging (ook aangeduid als _flush_) de cache.
1. Eindonderhoudsmodus.

## Opdrachten voor configuratiebeheer

Wij verstrekken de volgende bevelen om u te helpen de configuratie beheren:

- [`magento app:config:dump`](../cli/export-configuration.md) om beheerinstellingen te schrijven naar `config.php` en `env.php` (behalve voor gevoelige instellingen)
- [`magento config:set`](../cli/set-configuration-values.md) om de waarden van systeemspecifieke instellingen op het productiesysteem in te stellen.

   De optionele `--lock` Hiermee vergrendelt u de optie in Beheer (de instelling kan dus niet worden bewerkt). Als een instelling al is vergrendeld, gebruikt u de opdracht `--lock` om de instelling te wijzigen.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) om de waarden van gevoelige montages op het productiesysteem te plaatsen.
- [`magento app:config:import`](../cli/import-configuration.md) om configuratiewijzigingen te importeren van `config.php` en `env.php` aan het productiesysteem.

## Configuratiebeheervoorbeelden

Deze sectie toont voorbeelden van het beheren van de configuratie zodat kunt u zien hoe de veranderingen in worden aangebracht `config.php` en `env.php`.

### De standaardlandinstelling wijzigen

In dit gedeelte wordt de wijziging weergegeven die is aangebracht in `config.php` wanneer u de standaardgewichtseenheid wijzigt met Admin (**Winkels** > Instellingen > **Configuratie** > Algemeen > **Algemeen** > **Landinstellingen**).

Nadat u de wijziging hebt aangebracht in Beheer, voert u deze uit `bin/magento app:config:dump` om de waarde te schrijven waarnaar `config.php`. De waarde wordt geschreven naar de `general` array onder `locale` als het volgende fragment uit `config.php` toont:

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### Verschillende configuratie-instellingen wijzigen

Deze sectie bespreekt het aanbrengen van de volgende configuratieveranderingen:

- Een website-, winkel- en winkelweergave toevoegen (**Winkels** > Instellingen > **Alle winkels**)
- Het standaard-e-maildomein wijzigen (**Winkels** > Instellingen > **Configuratie** > Klanten > **Klantconfiguratie**)
- Gebruikersnaam en API-wachtwoord voor PayPal-API instellen (**Winkels** > Instellingen > **Configuratie** > Verkoop > **Betalingsmethoden** > **PayPal** > **Vereiste PayPal-instellingen**)

Nadat u de wijziging hebt aangebracht in Beheer, voert u deze uit `bin/magento app:config:dump` op uw ontwikkelingssysteem. Deze keer worden niet al uw wijzigingen doorgevoerd in `config.php`; in feite worden alleen de website-, opslag- en winkelweergave naar dat bestand geschreven, zoals in de volgende fragmenten wordt getoond.

### config.php

`config.php` bevat:

- Wijzigingen in de website-, opslag- en winkelweergave.
- Niet-systeemspecifieke zoekmachineinstellingen
- Niet-gevoelige PayPal-instellingen
- Opmerkingen die u informeren over gevoelige instellingen die zijn weggelaten uit `config.php`

`websites` array:

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups` array:

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores` array:

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment` array:

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

De standaardinstelling voor de systeemspecifieke configuratie van het e-maildomein waarnaar wordt geschreven `app/etc/env.php`.

De PayPal-instellingen worden naar geen van beide bestanden geschreven omdat de `bin/magento app:config:dump` schrijft geen gevoelige instellingen. U moet de PayPal-instellingen op het productiesysteem instellen met de volgende opdrachten:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
