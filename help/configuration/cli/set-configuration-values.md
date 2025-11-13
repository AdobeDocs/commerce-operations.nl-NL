---
title: Configuratiewaarden instellen
description: Leer hoe u configuratiewaarden instelt en vergrendelde beheerwaarden wijzigt in Adobe Commerce. Ontdek geavanceerde configuratiebevelen en technieken.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 2672c696d672ad72bef7537570ed630bc33c41b4
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 0%

---

# Configuratiewaarden instellen

{{file-system-owner}}

Dit onderwerp bespreekt geavanceerde configuratiebevelen die u kunt gebruiken aan:

- Een configuratieoptie instellen via de opdrachtregel
- Optioneel elke configuratieoptie vergrendelen zodat de waarde ervan niet kan worden gewijzigd in de beheerfunctie
- Een configuratieoptie wijzigen die is vergrendeld in Beheer

Met deze opdrachten kunt u de Commerce-configuratie handmatig instellen of scripts gebruiken. U plaatst configuratieopties gebruikend de weg van de a _configuratie_, die a `/` - afgebakend koord is dat uniek die configuratieoptie identificeert. U kunt configuratiepaden vinden in de volgende verwijzingen:

- [Verwijzing naar gevoelige en systeemspecifieke configuratiepaden](../reference/config-reference-sens.md)
- [Verwijzing naar betalingspaden](../reference/config-reference-payment.md)
- [Verwijzing naar algemene configuratiepaden](../reference/config-reference-general.md)
- [Referentie voor configuratiepaden voor Commerce Enterprise B2B-extensies](../reference/config-reference-b2b.md)

U kunt waarden instellen op de volgende tijdstippen:

- Voordat u Commerce installeert, kunt u configuratiewaarden alleen voor het standaardbereik instellen, omdat dit het enige geldige bereik is.

- Nadat u Commerce hebt geïnstalleerd, kunt u configuratiewaarden instellen voor elke website of elk weergavebereik van de winkel.

Gebruik de volgende opdrachten:

- `bin/magento config:set` stelt elke niet-vertrouwelijke configuratiewaarde in volgens het configuratiepad
- `bin/magento config:sensitive:set` stelt elke gevoelige configuratiewaarde in volgens het configuratiepad
- `bin/magento config:show` geeft opgeslagen configuratiewaarden weer; waarden van gecodeerde instellingen worden weergegeven als sterretjes

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
- [Referentie voor configuratiepaden voor Commerce Enterprise B2B-extensies](../reference/config-reference-b2b.md)

### De bereikcode zoeken

U kunt de bereikcode vinden in de Commerce-database of in Commerce Admin.

**om de werkingsgebiedcode in Admin** te vinden:

1. Meld u aan bij de beheerder als een gebruiker die websites kan bekijken en weergaven kan opslaan.
1. Klik op **[!UICONTROL Stores]** > Instellingen > **[!UICONTROL All Stores]** .
1. Klik in het rechterdeelvenster op de naam van de website- of opslagweergave om de bijbehorende code weer te geven.

   In de volgende afbeelding ziet u een voorbeeldcode voor de website.

   ![ krijg een website of opslag meningscode van Admin ](../../assets/configuration/website-code.png)

1. Ga met [ Vastgestelde waarden ](#set-values) verder.

**om de werkingsgebiedcode in het gegevensbestand** te vinden:

Toepassingscodes voor websites en winkelweergaven worden opgeslagen in de Commerce-database in respectievelijk de tabellen `store_website` en `store` .

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

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Gebruik de waarde in de kolom `code` .

1. Ga verder met de volgende sectie.

## Waarden instellen

**om systeem-specifieke configuratiewaarden** te plaatsen:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**om gevoelige configuratiewaarden** te plaatsen:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path
```

In de volgende tabel worden de opdrachtparameters `set` beschreven:

| Parameter | Beschrijving |
| --- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--scope` | Het bereik van de configuratie. De mogelijke waarden zijn `default` , `website` of `store` . De standaardwaarde is `default` . |
| `--scope-code` | De bereikcode van de configuratie (code van de website of van de opslagmening) |
| `-e or --lock-env` | Hiermee vergrendelt u de waarde zodat deze niet kan worden bewerkt in de beheerfunctie of wijzigt u een instelling die al is vergrendeld in de beheerfunctie. De opdracht schrijft de waarde naar het `<Commerce base dir>/app/etc/env.php` -bestand. |
| `-c or --lock-config` | Hiermee vergrendelt u de waarde zodat deze niet kan worden bewerkt in de beheerfunctie of wijzigt u een instelling die al is vergrendeld in de beheerfunctie. De opdracht schrijft de waarde naar het `<Commerce base dir>/app/etc/config.php` -bestand. De optie `--lock-config` overschrijft `--lock-env` als u beide opties opgeeft. |
| `path` | _Vereiste_. Het configuratiepad |
| `value` | _Vereiste_. De waarde van de configuratie. Hoewel het als afzonderlijk argument in een CLI bevel kan worden overgegaan, adviseert Adobe dat u het niet in het originele bevel specificeert. Voer in plaats daarvan de opdracht uit zonder de waarde en voer vervolgens de waarde in wanneer hierom wordt gevraagd. Het gebruiken van deze methode verhindert het schrijven van gevoelige toegangswaarden aan bash_history, die de veiligste manier is om config te plaatsen. |

>[!INFO]
>
>Vanaf Commerce 2.2.4 vervangen de opties `--lock-env` en `--lock-config` de optie `--lock` .
>
>Als u `--lock-env` of `--lock-config` optie gebruikt om een waarde te plaatsen of te veranderen, moet u het [`bin/magento app:config:import` bevel ](../cli/import-configuration.md) gebruiken om het plaatsen in te voeren alvorens u tot Admin of opslag toegang hebt.

Als u een onjuist configuratiepad invoert, retourneert deze opdracht een fout

```text
The "wrong/config/path" does not exist
```

Zie een van de volgende secties voor meer informatie:

- [Configuratiewaarden instellen die kunnen worden bewerkt in de beheerder](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Configuratiewaarden instellen die niet kunnen worden bewerkt in de beheerder](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Configuratiewaarden instellen die kunnen worden bewerkt in de beheerder

Gebruik `bin/magento config:set` _zonder_ `--lock-env` of `--lock-config` om de waarde aan het gegevensbestand te schrijven. Waarden die u op deze manier instelt, kunt u bewerken in de beheerfunctie.

Hier volgen enkele voorbeelden voor het instellen van de basis-URL van de winkel:

Stel de basis-URL in voor het standaardbereik:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Stel de basis-URL voor de `base` -website in:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Stel de basis-URL in voor de opslagweergave van `test` :

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Configuratiewaarden instellen die niet kunnen worden bewerkt in de beheerder

Als u de optie `--lock-env` als volgt gebruikt, slaat de opdracht de configuratiewaarde op in `<Commerce base dir>/app/etc/env.php` en schakelt het veld voor het bewerken van deze waarde in de beheerfunctie uit.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Met de optie `--lock-env` kunt u configuratiewaarden instellen als Commerce niet is geïnstalleerd. U kunt echter alleen waarden instellen voor het standaardbereik.

>[!INFO]
>
>Het bestand `env.php` is systeemspecifiek. Breng het niet over naar een ander systeem. U kunt het gebruiken om configuratiewaarden van het gegevensbestand te beschrijven. Bijvoorbeeld, kunt u een gegevensbestandstortplaats van een ander systeem nemen en `base_url` en andere waarden beschrijven zodat moet u niet het gegevensbestand wijzigen.

Als u de optie `--lock-config` als volgt gebruikt, wordt de configuratiewaarde opgeslagen in `<Commerce base dir>/app/etc/config.php` . Het veld voor het bewerken van deze waarde in Admin is uitgeschakeld.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Met `--lock-config` kunt u configuratiewaarden instellen als Commerce niet is geïnstalleerd. U kunt echter alleen waarden instellen voor het standaardbereik.

>[!INFO]
>
>U kunt `config.php` naar een ander systeem overbrengen om daar dezelfde configuratiewaarden te gebruiken. Als u bijvoorbeeld een testsysteem hebt en dezelfde methode gebruikt `config.php` , hoeft u niet opnieuw dezelfde configuratiewaarden in te stellen.

## De waarde van configuratie-instellingen weergeven

Opdrachtopties:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

waar

- `--scope` is het bereik van de configuratie (standaard, website, winkel). De standaardwaarde is `default`
- `--scope-code` is de bereikcode van de configuratie (code van de website of van de opslagmening)
- `path` is de configuratiepad in formaat first_part/second_part/third_part/etc (_vereist_)

>[!INFO]
>
>Het `bin/magento config:show` bevel toont de waarden van om het even welke [ gecodeerde waarden ](../reference/config-reference-sens.md) als reeks asterisken: `******`.

### Voorbeelden

**om alle bewaarde configuraties** te tonen:

```bash
bin/magento config:show
```

Resultaat

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**om alle opgeslagen configuraties voor de `base` website** te tonen:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Resultaat

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**om basis URL voor het standaardwerkingsgebied** te tonen:

```bash
bin/magento config:show web/unsecure/base_url
```

Resultaat

```
web/unsecure/base_url - http://example.com/
```

**om basis URL voor de `base` website** te tonen:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Resultaat

```
web/unsecure/base_url - http://example-for-website.com/
```

**om basis URL voor de `default` opslag** te tonen:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Resultaat

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>De bereikcode kan alleen letters (a-z of A-Z), getallen (0-9) en onderstrepingstekens (_) bevatten. Het eerste teken moet ook een letter zijn. Als hoofdletters of hoofdletters worden gebruikt bij het maken van een website- of winkelweergave, is de overeenkomst intern niet hoofdlettergevoelig voor overschrijvingen van configuratie-instellingen via omgevingsvariabelen. Zie [ het omgevingsvariabelen van het Gebruik om configuratiemontages ](../reference/override-config-settings.md#environment-variables) met voeten te treden.

