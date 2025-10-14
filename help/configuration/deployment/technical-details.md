---
title: Technische details
description: Lees over de technische details van pijpleidingsplaatsing, types van configuraties, en geadviseerde werkschema's.
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Technische details

Dit onderwerp bespreekt technische implementatiedetails over pijpleidingsplaatsing in Commerce 2.2 en later. De verbeteringen kunnen in de volgende gebieden worden verdeeld:

- [Configuratiebeheer](#configuration-management)
- [Wijzigingen in de beheerder](#changes-in-the-admin)
- [Uitsnede installeren en verwijderen](#install-and-remove-cron)

Dit onderwerp bespreekt ook het [&#x200B; geadviseerde werkschema &#x200B;](#recommended-workflow) voor pijpleidingsplaatsing en verstrekt sommige voorbeelden om u te helpen begrijpen hoe het werkt.

Alvorens u begonnen wordt, herzie de [&#x200B; Vereisten voor uw ontwikkeling, bouwt, en productiesystemen &#x200B;](../deployment/prerequisites.md).

## Configuratiebeheer

Om u toe te laten om de configuratie van uw ontwikkeling en productiesystemen te synchroniseren en te handhaven, gebruik de volgende met voeten getreden regeling.

![&#x200B; Hoe de waarden van de configuratievariabele worden bepaald &#x200B;](../../assets/configuration/override-flow-diagram.png)

Zoals het diagram toont, worden de configuratiewaarden gebruikt in de volgende orde:

1. Omgevingsvariabelen, indien aanwezig, overschrijven alle andere waarden.
1. Uit de gedeelde configuratiebestanden `env.php` en `config.php` . Waarden in `env.php` overschrijven waarden in `config.php` .
1. Uit waarden die zijn opgeslagen in de database.
1. Als geen waarde in om het even welke die bronnen bestaat, wordt de standaardwaarde of ONGELDIG gebruikt.

### De gedeelde configuratie beheren

De gedeelde configuratie wordt opgeslagen in `app/etc/config.php`, die in broncontrole zou moeten zijn.

Plaats de gedeelde configuratie in Admin in uw ontwikkeling (of Adobe Commerce op de integratie van de wolkeninfrastructuur __) systeem en schrijf de configuratie aan `config.php` gebruikend het [`magento app:config:dump` bevel &#x200B;](../cli/export-configuration.md).

### De systeemspecifieke configuratie beheren

De systeem-specifieke configuratie wordt opgeslagen in `app/etc/env.php`, die _niet_ in broncontrole zou moeten zijn.

Plaats de systeem-specifieke configuratie in Admin in uw ontwikkelings (of Adobe Commerce op de integratie van de wolkeninfrastructuur) systeem en schrijf de configuratie aan `env.php` gebruikend [`magento app:config:dump` bevel &#x200B;](../cli/export-configuration.md).

Met deze opdracht worden ook gevoelige instellingen naar `env.php` geschreven.

### De vertrouwelijke configuratie beheren

De gevoelige configuratie wordt ook opgeslagen in `app/etc/env.php`.

U kunt de gevoelige configuratie op om het even welke volgende manieren beheren:

- Omgevingsvariabelen
- Sparen de gevoelige configuratie in `env.php` op uw productiesysteem gebruikend het [`magento config:set:sensitive` bevel &#x200B;](../cli/set-configuration-values.md)

### Configuratie-instellingen vergrendeld in de beheerder

Configuratie-instellingen in `config.php` of `env.php` zijn vergrendeld in de beheerfunctie. Deze instellingen kunnen dus niet worden gewijzigd in de beheerdersinstelling.
Gebruik de opdracht [`magento config:set` of `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) om de instellingen in de `config.php` - of `env.php` -bestanden te wijzigen.

## Commerce Admin

Admin vertoont het volgende gedrag terwijl in productiemodus:

- U kunt cavetypen niet in- of uitschakelen in Beheer
- De montages van de ontwikkelaar zijn niet beschikbaar (**Slaat** > Montages > **Configuratie** > Geavanceerd > **Ontwikkelaar**), die omvatten:

   - CSS, JavaScript en HTML miniaturen
   - CSS en JavaScript samenvoegen
   - LESS-compilatie op server- of clientzijde
   - Inline-vertalingen
   - Zoals eerder is besproken, is elke configuratie-instelling in `config.php` of `env.php` vergrendeld en kan deze niet worden bewerkt in de beheerfunctie.
   - U kunt de beheerlandinstelling alleen wijzigen in talen die worden gebruikt door geïmplementeerde thema&#39;s

     Het volgende cijfer toont een voorbeeld van de **Plaatsende Rekening** > **Lijst van de Plaats van de Interface** in Admin die slechts twee opgestelde scènes tonen:

     ![&#x200B; u kunt de beheerderscène slechts veranderen in opgestelde scènes &#x200B;](../../assets/configuration/split-deploy-admin-locale.png)

- U kunt de configuratie van de landinstelling voor geen enkel bereik wijzigen met de beheerfunctie.

  Wij adviseren makend deze veranderingen alvorens op de wijze van de Productie over te schakelen.

  U kunt de landinstelling nog steeds configureren met behulp van omgevingsvariabelen of de opdracht `config:set` CLI met behulp van het pad `general/locale/code` .

## Uitsnede installeren en verwijderen

In versie 2.2 voor het eerst, helpen wij u opstelling uw kroonbaan door het [`magento cron:install` bevel &#x200B;](../cli/configure-cron-jobs.md) te verstrekken. Met deze opdracht stelt u een tab in als de gebruiker die de opdracht uitvoert.

U kunt ook de tab verwijderen met de opdracht `magento cron:remove` .

## Aanbevolen workflow voor distributie van pijpleidingen

Het volgende diagram toont hoe wij u aanbevelen pijpleidingsplaatsing te gebruiken om de configuratie te beheren.

![&#x200B; Aanbevolen werkschema van de pijpleidingsplaatsing &#x200B;](../../assets/configuration/split-deploy-workflow.png)

### Ontwikkelingssysteem

Op uw ontwikkelingssysteem, brengt u configuratieveranderingen in Admin aan en produceert de gedeelde configuratie, `app/etc/config.php` en de systeem-specifieke configuratie, `app/etc/env.php`. Controleer de code van Commerce en de gedeelde configuratie in broncontrole en duw het aan de bouwstijlserver.

U moet ook extensies installeren en de Commerce-code op het ontwikkelingssysteem aanpassen.

Op uw ontwikkelingssysteem:

1. Stel de configuratie in de beheerfunctie in.

1. Gebruik de opdracht `magento app:config:dump` om de configuratie naar het bestandssysteem te schrijven.

   - `app/etc/config.php` is de gedeelde configuratie, die alle montages _behalve_ gevoelige en systeem-specifieke montages bevat. Dit bestand moet zich in de broncontrole bevinden.
   - `app/etc/env.php` is de systeemspecifieke configuratie, die montages bevat die aan een bepaald systeem (bijvoorbeeld, hostnames en havenaantallen) uniek zijn. Dit dossier zou __ niet in broncontrole moeten zijn.

1. Voeg uw gewijzigde code en de gedeelde configuratie aan broncontrole toe.

1. Voer de volgende opdrachten uit om gegenereerde php-code en statische elementbestanden tijdens de ontwikkeling te verwijderen:

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Nadat Commerce de opdrachten heeft uitgevoerd om de elementen te wissen, worden werkbestanden gegenereerd.

>[!WARNING]
>
>Wees voorzichtig met de bovenstaande aanpak. Als u het `.htacces` -bestand verwijdert in de map `generated` of `pub` , kunnen er problemen optreden.

### Systeem bouwen

Het bouwstijlsysteem compileert code en produceert statische meningsdossiers voor thema&#39;s die in Commerce worden geregistreerd. Er is geen verbinding met de Commerce-database nodig, maar alleen met de Commerce-codebase.

Op uw bouwstijlsysteem:

1. Trek het gedeelde configuratiedossier van broncontrole.
1. Gebruik de opdracht `magento setup:di:compile` om code te compileren.
1. Gebruik de opdracht `magento setup:static-content:deploy -f` om statische bestanden in de weergave bij te werken.
1. Controleer de updates in broncontrole.

>[!INFO]
>
>Zie [&#x200B; strategieën van de Plaatsing voor statische meningsdossiers &#x200B;](../cli/static-view-file-strategy.md).

### Productiesysteem

Op uw productiesysteem (namelijk uw levende opslag) trekt u geproduceerde activa en codeupdates van broncontrole en plaatst systeem-specifieke en gevoelige configuratiemontages gebruikend de bevellijn of milieuvariabelen.

Op uw productiesysteem:

1. Start de onderhoudsmodus.
1. Trek code en configuratietoepassingen van broncontrole.
1. Als u Adobe Commerce gebruikt, stop wachtrijarbeiders.
1. Gebruik de opdracht `magento app:config:import` om configuratiewijzigingen in het productiesysteem te importeren.
1. Als u componenten hebt geïnstalleerd die het databaseschema hebben gewijzigd, voert u `magento setup:upgrade --keep-generated` uit om het databaseschema en de gegevens bij te werken, waarbij gegenereerde statische bestanden behouden blijven.
1. Gebruik de opdracht `magento config:set` of omgevingsvariabelen om systeemspecifieke instellingen in te stellen.
1. Gebruik de opdracht `magento config:sensitive:set` of omgevingsvariabelen om gevoelige instellingen in te stellen.
1. Schoon (die ook als _wordt bedoeld flush_) het geheime voorgeheugen.
1. Eindonderhoudsmodus.

## Opdrachten voor configuratiebeheer

Wij verstrekken de volgende bevelen om u te helpen de configuratie beheren:

- [`magento app:config:dump`](../cli/export-configuration.md) om beheerdersconfiguratie-instellingen naar `config.php` en `env.php` te schrijven (behalve voor gevoelige instellingen)
- [`magento config:set`](../cli/set-configuration-values.md) om de waarden van systeemspecifieke instellingen in te stellen op het productiesysteem.

  Gebruik de optionele optie `--lock` om de optie in Beheer te vergrendelen (de instelling kan dus niet worden bewerkt). Als een instelling al is vergrendeld, wijzigt u de instelling met de optie `--lock` .

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) om de waarden van gevoelige instellingen in te stellen op het productiesysteem.
- [`magento app:config:import`](../cli/import-configuration.md) om configuratiewijzigingen van `config.php` en `env.php` in het productiesysteem te importeren.

## Configuratiebeheervoorbeelden

In deze sectie worden voorbeelden weergegeven van het beheer van de configuratie, zodat u kunt zien hoe wijzigingen worden aangebracht in `config.php` en `env.php` .

### De standaardlandinstelling wijzigen

Deze sectie toont de verandering die aan `config.php` wordt aangebracht wanneer u de eenheid van het standaardgewicht gebruikend Admin (**wordt aangebracht Slaat** > Montages > **Configuratie** > Algemeen > **Algemeen** > **de Opties van de Landinstelling**).

Nadat u de wijziging in Beheer hebt aangebracht, voert u `bin/magento app:config:dump` uit om de waarde naar `config.php` te schrijven. De waarde wordt naar de array `general` onder `locale` geschreven, zoals in het volgende fragment uit `config.php` wordt getoond:

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

- Het toevoegen van een website, opslag, en opslagmening (**Slaat** > Montages > **Alle Sporen**) op
- Het veranderen van het standaard e-maildomein (**Slaat** > Montages > **Configuratie** > Klanten > **Configuratie van de Klant**) op
- Het plaatsen van de Gebruikersnaam en het API wachtwoord van PayPal API (**opslag** > Montages > **Configuratie** > Verkoop > **de Methoden van de Betaling** > **PayPal** > **Vereiste Montages PayPal**)

Nadat u de wijziging in Admin hebt aangebracht, voert u `bin/magento app:config:dump` uit op uw ontwikkelingssysteem. Dit keer worden niet al uw wijzigingen naar `config.php` geschreven. In feite worden alleen de website-, opslag- en winkelweergave naar dat bestand geschreven zoals in de volgende fragmenten wordt getoond.

### config.php

`config.php` bevat:

- Wijzigingen in de website-, opslag- en winkelweergave.
- Niet-systeemspecifieke zoekmachineinstellingen
- Niet-gevoelige PayPal-instellingen
- Opmerkingen die u informeren over gevoelige instellingen die zijn weggelaten uit `config.php`

`websites` -array:

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

`groups` -array:

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

`stores` -array:

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

`payment` -array:

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

De standaardinstelling voor de systeemspecifieke configuratie van het e-maildomein wordt geschreven naar `app/etc/env.php` .

De PayPal-instellingen worden naar geen van beide bestanden geschreven, omdat de opdracht `bin/magento app:config:dump` geen gevoelige instellingen schrijft. U moet de PayPal-instellingen op het productiesysteem instellen met de volgende opdrachten:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
