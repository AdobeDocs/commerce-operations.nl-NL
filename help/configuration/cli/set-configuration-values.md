---
title: Configuratiewaarden instellen
description: Leer hoe u configuratiewaarden instelt en waarden wijzigt die zijn vergrendeld in Beheer.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---


# Configuratiewaarden instellen

{{file-system-owner}}

Dit onderwerp bespreekt geavanceerde configuratiebevelen die u kunt gebruiken aan:

- Een configuratieoptie instellen via de opdrachtregel
- Optioneel elke configuratieoptie vergrendelen zodat de waarde ervan niet kan worden gewijzigd in de beheerfunctie
- Een configuratieoptie wijzigen die is vergrendeld in de beheerfunctie

U kunt deze bevelen gebruiken om de configuratie van de Handel manueel te plaatsen of manuscripten te gebruiken. U stelt configuratieopties in met een _configuratiepad_, die `/`-delimited string die uniek die configuratieoptie identificeert. U kunt configuratiepaden vinden in de volgende verwijzingen:

- [Verwijzing naar gevoelige en systeemspecifieke configuratiepaden](../reference/config-reference-sens.md)
- [Verwijzing naar betalingspaden](../reference/config-reference-payment.md)
- [Verwijzing naar algemene configuratiepaden](../reference/config-reference-general.md)
- [Bron voor configuratiepaden van de extensie Commerce Enterprise B2B](../reference/config-reference-b2b.md)

U kunt waarden instellen op de volgende tijdstippen:

- Alvorens u Handel installeert, kunt u configuratiewaarden voor het standaardwerkingsgebied slechts plaatsen, omdat het het enige geldige werkingsgebied is.

- Nadat u Commerce hebt geïnstalleerd, kunt u configuratiewaarden instellen voor elke website of [winkelweergave](https://glossary.magento.com/store-view) bereik.

Gebruik de volgende opdrachten:

- `bin/magento config:set` plaatst om het even welke niet gevoelige configuratiewaarde door zijn configuratiepad
- `bin/magento config:sensitive:set` plaatst om het even welke gevoelige configuratiewaarde door zijn configuratiepad
- `bin/magento config:show` toont opgeslagen configuratiewaarden; waarden van gecodeerde instellingen worden weergegeven als sterretjes

## Vereisten

Om een configuratiewaarde te plaatsen, moet u minstens één van het volgende weten:

- Het configuratiepad
- Om een configuratiewaarde voor een bepaald werkingsgebied te plaatsen, moet u de werkingsgebiedcode kennen.

   Om een configuratiewaarde voor het standaardwerkingsgebied te plaatsen, te hoeven u om het even wat niet te doen.

### Het configuratiepad zoeken

Zie de volgende verwijzingen:

- [Verwijzing naar gevoelige en systeemspecifieke configuratiepaden](../reference/config-reference-sens.md)
- [Verwijzing naar betalingspaden](../reference/config-reference-payment.md)
- [Verwijzing naar andere configuratiepaden](../reference/config-reference-general.md)
- [Bron voor configuratiepaden van de extensie Commerce Enterprise B2B](../reference/config-reference-b2b.md)

### De bereikcode zoeken

U kunt de werkingsgebiedcode of in het gegevensbestand van de Handel of in Admin van de Handel vinden.

**De bereikcode vinden in Admin**:

1. Meld u aan bij de beheerder als een gebruiker die websites kan bekijken en weergaven kan opslaan.
1. Klikken **[!UICONTROL Stores]** > Instellingen > **[!UICONTROL All Stores]**.
1. Klik in het rechterdeelvenster op de naam van de website- of opslagweergave om de bijbehorende code weer te geven.

   In de volgende afbeelding ziet u een voorbeeldcode voor de website.

   ![Een website ophalen of weergavetode opslaan via de beheerder](../../assets/configuration/website-code.png)

1. Doorgaan met [Waarden instellen](#set-values).

**De bereikcode zoeken in de database**:

De codes van het werkingsgebied voor websites en opslagmeningen worden opgeslagen in het gegevensbestand van de Handel in `store_website` en `store` tabellen, respectievelijk.

1. Maak verbinding met de Commerce-database.

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. Voer de volgende opdrachten in:

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   Hieronder volgt een voorbeeldresultaat:

   ```terminal
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Gebruik de waarde in het dialoogvenster `code` kolom.

1. Ga verder met de volgende sectie.

## Waarden instellen

**Systeemspecifieke configuratiewaarden instellen**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Om gevoelige configuratiewaarden te plaatsen**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

In de volgende tabel worden de `set` opdrachtparameters:

| Parameter | Beschrijving |
| --- | --- |
| `--scope` | Het bereik van de configuratie. De mogelijke waarden zijn: `default`, `website`, of `store`. De standaardwaarde is `default`. |
| `--scope-code` | De bereikcode van de configuratie (code van de website of van de opslagmening) |
| `-le or --lock-env` | Hiermee vergrendelt u de waarde zodat deze niet kan worden bewerkt in de beheerfunctie of wijzigt u een instelling die al is vergrendeld in de beheerfunctie. De opdracht schrijft de waarde naar de `<Commerce base dir>/app/etc/env.php` bestand. |
| `-lc or --lock-config` | Hiermee vergrendelt u de waarde zodat deze niet kan worden bewerkt in de beheerfunctie of wijzigt u een instelling die al is vergrendeld in de beheerfunctie. De opdracht schrijft de waarde naar de `<Commerce base dir>/app/etc/config.php` bestand. De `--lock-config` optie overschrijft `--lock-env` als u beide opties opgeeft. |
| `path` | _Vereist_. Het configuratiepad |
| `value` | _Vereist_. De waarde van de configuratie |

>[!INFO]
>
>Vanaf 2.2.4 `--lock-env` en `--lock-config` vervangen de opties `--lock` optie.
>
>Als u het `--lock-env` of `--lock-config` als u een waarde wilt instellen of wijzigen, moet u de optie [`bin/magento app:config:import` command](../cli/import-configuration.md) om de instelling te importeren voordat u toegang krijgt tot Admin of Storage.

Als u een onjuist configuratiepad invoert, retourneert deze opdracht een fout

```text
The "wrong/config/path" does not exist
```

Zie een van de volgende secties voor meer informatie:

- [Configuratiewaarden instellen die kunnen worden bewerkt in de beheerder](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Configuratiewaarden instellen die niet kunnen worden bewerkt in de beheerder](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Configuratiewaarden instellen die kunnen worden bewerkt in de beheerder

Gebruiken `bin/magento config:set` _zonder_ `--lock-env` of `--lock-config` om de waarde naar de database te schrijven. Waarden die u op deze manier instelt, kunt u bewerken in de beheerfunctie.

Hier volgen enkele voorbeelden voor het instellen van de basis-URL van de winkel:

Stel de basis-URL in voor het standaardbereik:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Stel de basis-URL in voor de `base` website:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Stel de basis-URL in voor de `test` winkelweergave:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Configuratiewaarden instellen die niet kunnen worden bewerkt in de beheerder

Als u het `--lock-env`  optie als volgt, bewaart het bevel de configuratiewaarde in `<Commerce base dir>/app/etc/env.php` en schakelt het veld voor het bewerken van deze waarde in Admin uit.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

U kunt de `--lock-env` optie om configuratiewaarden in te stellen als de Handel niet geïnstalleerd is. U kunt echter alleen waarden instellen voor het standaardbereik.

>[!INFO]
>
>De `env.php` bestand is systeemspecifiek. Breng het niet over naar een ander systeem. U kunt het gebruiken om configuratiewaarden van het gegevensbestand te beschrijven. Bijvoorbeeld, kunt u een gegevensbestandstortplaats van een ander systeem nemen en beschrijven `base_url` en andere waarden, zodat u de database niet hoeft te wijzigen.

Als u het `--lock-config` optie als volgt: de configuratiewaarde wordt opgeslagen in `<Commerce base dir>/app/etc/config.php`. Het veld voor het bewerken van deze waarde in Admin is uitgeschakeld.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

U kunt `--lock-config` om configuratiewaarden in te stellen als de Handel niet geïnstalleerd is. U kunt echter alleen waarden instellen voor het standaardbereik.

>[!INFO]
>
>U kunt `config.php` naar een ander systeem om dezelfde configuratiewaarden daar te gebruiken. Als u bijvoorbeeld een testsysteem hebt, gebruikt u hetzelfde `config.php` betekent dat u niet dezelfde configuratiewaarden opnieuw hoeft in te stellen.

## De waarde van configuratie-instellingen weergeven

Opdrachtopties:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

waar

- `--scope` is het bereik van de configuratie (standaard, website, winkel). De standaardwaarde is `default`
- `--scope-code` is de bereikcode van de configuratie (code van de website of van de opslagmening)
- `path` is het configuratiepad in de notatie first_part/second_part/third_part/etc (_vereist_)

>[!INFO]
>
>De `bin/magento config:show` geeft de waarden van alle [gecodeerde waarden](../reference/config-reference-sens.md) als een reeks asterisken: `******`.

### Voorbeelden

**Alle opgeslagen configuraties weergeven**:

```bash
bin/magento config:show
```

Resultaat:

```terminal
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Alle opgeslagen configuraties weergeven voor de `base` website**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Resultaat:

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**De basis-URL voor het standaardbereik weergeven**:

```bash
bin/magento config:show web/unsecure/base_url
```

Resultaat:

```terminal
web/unsecure/base_url - http://example.com/
```

**Als u de basis-URL voor de `base` website**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Resultaat:

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**Als u de basis-URL voor de `default` winkel**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Resultaat:

```terminal
web/unsecure/base_url - http://example-for-store.com/
```
