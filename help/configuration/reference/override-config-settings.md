---
title: Configuratie-instellingen overschrijven
description: Leer hoe te om omgevingsvariabelen te gebruiken om configuratiemontages met voeten te treden.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---


# Configuratie-instellingen overschrijven

Dit onderwerp bespreekt hoe te om een milieu veranderlijke naam af te leiden die een configuratiepad kent. U kunt de configuratie-instellingen van Adobe Commerce overschrijven met behulp van omgevingsvariabelen. U kunt bijvoorbeeld de waarde van de live URL van een betalingsprocessor overschrijven op uw productiesysteem.

U kunt de waarde van _alle_ configuratie-instelling met behulp van omgevingsvariabelen; Adobe raadt u echter aan consistente instellingen te behouden met behulp van het gedeelde configuratiebestand, `config.php`en het systeemspecifieke configuratiebestand, `env.php`, zoals besproken in [Algemeen overzicht van implementatie](../deployment/overview.md).

>[!TIP]
>
>Kijk uit de [Omgevingen configureren](https://devdocs.magento.com/cloud/env/variables-intro.html) in het _Commerce Cloud-hulplijn_ voor meer informatie over het werken met variabelen in Adobe Commerce over cloudinfrastructuur.

## Omgevingsvariabelen

Een omgevingsvariabele naam bestaat uit het bereik gevolgd door het configuratiepad in een bepaalde indeling. De volgende secties bespreken hoe te om een veranderlijke naam in detail te bepalen.

U kunt variabelen voor om het even welk van het volgende gebruiken:

- [Gevoelige waarden](config-reference-sens.md) moet worden ingesteld met behulp van omgevingsvariabelen of de [`magento config:sensitive:set`](../cli/set-configuration-values.md) gebruiken.
- Systeemspecifieke waarden moeten worden ingesteld met:

   - Omgevingsvariabelen
   - De [`magento config:set`](../cli/set-configuration-values.md) command
   - De beheerder, gevolgd door de [`magento app:config:dump` command](../cli/export-configuration.md)

De wegen van de configuratie kunnen in worden gevonden:

- [Verwijzing naar gevoelige en systeemspecifieke configuratiepaden](config-reference-sens.md)
- [Verwijzing naar betalingspaden](config-reference-payment.md)
- [Referentie voor de configuratiepaden van B2B-extensie voor handel](config-reference-b2b.md)
- [Verwijzing naar andere configuratiepaden](config-reference-general.md)

### Namen van variabelen

De algemene indeling van namen van systeeminstellingenvariabelen is als volgt:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` kunnen:

- Globaal bereik (dat wil zeggen de globale instelling voor _alles_ bereik)

   Algemene bereikvariabelen hebben de volgende indeling:

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Een specifiek bereik (de instelling heeft alleen invloed op een opgegeven winkelweergave of website)

   De variabelen van het het meningswerkingsgebied van de opslag, bijvoorbeeld, hebben het volgende formaat:

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   Zie voor meer informatie over het bereik:

   - [Stap 1: De waarde van het bereik van de website- of winkelweergave zoeken](#step-1-find-the-website-or-store-view-scope-value)
   - [Onderwerp van de Handleiding voor handel in bereik](https://docs.magento.com/user-guide/configuration/scope.html)
   - [Snelle naslaggids voor bereik](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` is het configuratiepad met dubbele onderstrepingstekens die worden vervangen door `/`. Zie voor meer informatie [Stap 2: Systeemvariabelen instellen](#step-2-set-global-website-or-store-view-variables).

### Variabele-indeling

`<SCOPE>` wordt gescheiden van `<SYSTEM__VARIABLE__NAME>` met twee onderstrepingstekens.

`<SYSTEM__VARIABLE__NAME>` is afgeleid van een configuratie die plaatsen _configuratiepad_, die `/` afgebakende tekenreeks die een bepaalde instelling uniek identificeert. Elke vervangen `/` in het configuratiepad met twee onderstrepingstekens om de systeemvariabele te maken.

Als een configuratiepad een onderstrepingsteken bevat, blijft het onderstrepingsteken in de variabele.

Een volledige lijst met configuratiepaden vindt u in:

- [Verwijzing naar gevoelige en systeemspecifieke configuratiepaden](config-reference-sens.md)
- [Verwijzing naar betalingspaden](config-reference-payment.md)
- [Bron voor configuratiepaden van de extensie Commerce Enterprise B2B](config-reference-b2b.md)
- [Verwijzing naar andere configuratiepaden](config-reference-general.md)

## Stap 1: De waarde van het bereik van de website- of winkelweergave zoeken

Deze sectie bespreekt hoe u de waarden van de systeemconfiguratie per kunt vinden en plaatsen _bereik_ (Winkelweergave of website). Zie voor het instellen van globale bereikvariabelen [Stap 2: Algemene weergavevariabelen, websites of opslagruimten instellen](#step-2-set-global-website-or-store-view-variables).

De waarden voor het bereik zijn afkomstig van `store`, `store_group`, en `store_website` tabellen.

- De `store` table specificeert de namen van de opslagmening en codes
- De `store_website` tabel geeft websitenamen en -codes op

U kunt de codewaarden ook vinden gebruikend Admin.

Hoe de tabel te lezen:

- `Path in Admin` kolom

   Waarden vóór de komma zijn paden in de beheerdersnavigatie. Waarden na de komma zijn opties in het rechterdeelvenster.

- `Variable name` kolom is de naam van de overeenkomstige omgevingsvariabele.

   U kunt desgewenst systeemwaarden voor deze configuratieparameters opgeven als omgevingsvariabelen.

   - De volledige variabelenaam is altijd ALL CAPS
   - Een variabelenaam starten met `CONFIG__` (twee onderstrepingstekens)
   - U kunt de `<STORE_VIEW_CODE>` of `<WEBSITE_CODE>` gedeelte van een veranderlijke naam in of Admin of het gegevensbestand van de Handel, zoals die in de volgende secties wordt vermeld.
   - U kunt zoeken `<SYSTEM__VARIABLE__NAME>` zoals besproken in [Stap 2: Algemene weergavevariabelen, websites of opslagruimten instellen](#step-2-set-global-website-or-store-view-variables).

### Een website of weergavebereik van de winkel zoeken in Admin

In de volgende tabel ziet u hoe u naar een website kunt zoeken of de weergavewaarde kunt opslaan in Admin.

| Beschrijving | Pad in Admin | Naam variabele |
|--------------|--------------|----------------------|
| Winkelweergaven maken, bewerken en verwijderen | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Websites maken, bewerken en verwijderen | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Als u bijvoorbeeld een website wilt zoeken of een waarde voor het weergavebereik wilt opslaan in Admin:

1. Meld u aan bij de beheerder als een gebruiker die geautoriseerd is om websites te bekijken.
1. Klikken **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Klik op de naam van een website- of opslagweergave.

   Het rechterdeelvenster wordt op vergelijkbare wijze weergegeven als het volgende.

   ![Websitecode zoeken](../../assets/configuration/website-code.png)

1. De bereiknaam wordt weergegeven in het dialoogvenster **[!UICONTROL Code]** veld.
1. Doorgaan met [Stap 2: Algemene weergavevariabelen, websites of opslagruimten instellen](#step-2-set-global-website-or-store-view-variables).

### Een website zoeken of weergavebereik in de database opslaan

Deze waarden ophalen uit de database:

1. Meld u aan bij uw ontwikkelsysteem als de [eigenaar van bestandssysteem](https://glossary.magento.com/magento-file-system-owner) als u dat nog niet hebt gedaan.
1. Voer de volgende opdracht in:

   ```bash
   mysql -u <database-username> -p
   ```

1. Bij de `mysql>` vraag, ga de volgende bevelen in de getoonde orde in:

   ```shell
   use <database-name>;
   ```

1. Gebruik de volgende SQL-query&#39;s om de relevante waarden te zoeken:

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   Hieronder volgt een monster:

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. Gebruik de waarde van de `code` kolom als de bereiknaam, niet de `name` waarde.

   Als u bijvoorbeeld een configuratievariabele wilt instellen voor Testwebsite, gebruikt u de volgende indeling:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   waar `<SYSTEM__VARIABLE__NAME>` komt uit de volgende sectie.

## Stap 2: Algemene weergavevariabelen, websites of opslagruimten instellen

In deze sectie wordt besproken hoe systeemvariabelen moeten worden ingesteld.

- Als u waarden wilt instellen voor het algemene bereik (dat wil zeggen alle websites, winkels en winkelweergaven), start u de variabelenaam met `CONFIG__DEFAULT__`.

- Als u een waarde voor een bepaalde winkelweergave of website wilt instellen, start u de variabelenaam zoals beschreven in [Stap 1: De bereikwaarde zoeken](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- Het laatste deel van de variabelenaam is de configuratiepad, die uniek is voor elke configuratie-instelling.

[Zie enkele voorbeelden](#examples).

In de volgende tabel staan enkele voorbeeldvariabelen.

| Beschrijving | Pad in Admin (weglaten) **Winkels** > **Instellingen** > **Configuratie**) | Naam variabele |
|--------------|--------------|----------------------|
| hostnaam Elasticsearch-server | Catalogus > **Catalogus**, **Hostnaam Elasticsearch-server** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Elasticsearch-serverpoort | Catalogus > **Catalogus**, **Elasticsearch-serverpoort** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Oorsprong land van verzending | Verkoop > **Verzendinstellingen** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| Aangepaste beheerdersURL | Geavanceerd > **Beheer** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Aangepast beheerpad | Geavanceerd > **Beheer** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Voorbeelden

In deze sectie ziet u hoe u waarden van bepaalde voorbeeldvariabelen kunt vinden.

### hostnaam Elasticsearch-server

U kunt als volgt de variabelenaam zoeken voor globale minificatie van HTML:

1. Bepaal het bereik.

   Het is het algemene bereik, dus de naam van de variabele begint met `CONFIG__DEFAULT__`

1. De rest van de variabelenaam is `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Resultaat**: De variabelenaam is `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Oorsprong land van verzending

U kunt als volgt de variabelenaam zoeken voor de oorsprong van het verzendland:

1. Bepaal het bereik.

   Zoek het bereik in het dialoogvenster [database](#find-a-website-or-store-view-scope-in-the-database) zoals besproken in Stap 1: Zoek de waarde van het bereik van de website- of winkelweergave. (U kunt de waarde ook vinden in Admin zoals weergegeven in het dialoogvenster [tabel in stap 2: Algemene weergavevariabelen, websites of opslagruimten instellen](#step-2-set-global-website-or-store-view-variables).

   Het bereik kan bijvoorbeeld `CONFIG__WEBSITES__DEFAULT`.

1. De rest van de variabelenaam is `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Resultaat**: De variabelenaam is `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Omgevingsvariabelen gebruiken

Configuratiewaarden instellen als variabelen met PHP&#39;s [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) associatieve array. U kunt de waarden in om het even welk PHP manuscript plaatsen dat loopt wanneer de Handel loopt.

>[!TIP]
>
>Variabelewaarden instellen in `index.php` of `pub/index.php` werkt niet altijd zoals verwacht, aangezien verschillende ingangspunten van de toepassing afhankelijk van de configuratie van de Webserver kunnen worden gebruikt. Door `$_ENV` in de `app/bootstrap.php` bestand, ongeacht de verschillende ingangspunten van de toepassing, de `$_ENV` instructies worden altijd uitgevoerd sinds de `app/bootstrap.php` bestanden worden geladen als onderdeel van de architectuur Commerce.

Een voorbeeld van het instellen van twee `$_ENV` waarden:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Een stapsgewijs voorbeeld wordt getoond in [Configuratiewaarden instellen met omgevingsvariabelen](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- De waarden gebruiken die u instelt in het dialoogvenster `$_ENV` array, u moet instellen `variables_order = "EGPCS"`(Environment, Get, Post, Cookie, and Server) in uw `php.ini` bestand. Zie voor meer informatie [PHP-documentatie](https://www.php.net/manual/en/ini.core.php).
>
>- Voor Adobe Commerce op cloudinfrastructuur geldt dat als u probeert de configuratie-instellingen te overschrijven met de opdracht [Projectwebinterface](https://devdocs.magento.com/cloud/project/project-webint-basic.html#project-conf-env-var), moet u de variabelenaam vooraf aan `env:`. Bijvoorbeeld:
>
>![Voorbeeld van de variabele Environment](https://devdocs.magento.com/common/images/cloud/cloud_env_var_example.png)
