---
title: De bewerkingsmodus instellen
description: Lees meer over het instellen van de Adobe Commerce-bewerkingsmodi.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# De bewerkingsmodus instellen

{{file-system-owner}}

Om veiligheid en gemak-van-gebruik te verbeteren, hebben wij een bevel toegevoegd dat [ toepassingswijzen ](../bootstrap/application-modes.md) van ontwikkelaar aan productie en vice versa schakelt.

De productiemodus biedt betere prestaties omdat statische weergavebestanden worden gevuld in de map `pub/static` en vanwege de codecompilatie.

>[!INFO]
>
>In versie 2.0.6 en hoger stelt Commerce niet expliciet bestands- of mapmachtigingen in wanneer u schakelt tussen de standaardmodus, de ontwikkelmodus en de productiemodus. In tegenstelling tot andere modi worden de ontwikkelaar- en productiemodi ingesteld in het `env.php` -bestand. Adobe Commerce on cloud Infrastructure ondersteunt alleen productie- en onderhoudsmodi.
>
>Zie [ Commerce eigendom en toestemmingen in ontwikkeling en productie ](../deployment/file-system-permissions.md).

Wanneer u in ontwikkelaar of productiemodus verandert, ontruimen wij de inhoud van volgende folders:

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Uitzonderingen:

- `.htaccess` bestanden worden niet verwijderd
- `pub/static` bevat een bestand dat de versie van statische inhoud opgeeft; dit bestand wordt niet verwijderd

>[!INFO]
>
>Standaard gebruikt Commerce de mappen van `var` om de cache, logbestanden en gecompileerde code op te slaan. U kunt deze map aanpassen, maar in deze handleiding wordt ervan uitgegaan dat dit `var` is.

## De huidige modus weergeven

De gemakkelijkste manier om dat te doen is dit bevel als [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md) in werking te stellen. Als u een gedeelde host hebt, is dit de gebruiker die uw provider u geeft om u aan te melden bij de server. Als u een privéserver hebt, is dit doorgaans een lokale gebruikersaccount op de Commerce-server.

Opdrachtgebruik:

```bash
bin/magento deploy:mode:show
```

Een bericht dat lijkt op de volgende vertoningen:

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

waarbij:

- **`{mode}`** kan `default` , `developer` of `production` zijn

## Modus wijzigen

Opdrachtgebruik:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

waarbij:

- **`{mode}`** is vereist. Dit kan `developer` of `production` zijn

- **`--skip-compilation`** is een facultatieve parameter u kunt gebruiken om [ codecompilatie ](../cli/code-compiler.md) over te slaan wanneer u in productiemodus verandert.

Hieronder volgen voorbeelden.

### Verandering in de productiemodus

```bash
bin/magento deploy:mode:set production
```

Berichten die lijken op de volgende weergave:

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or Sass files
CSS deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### Wijzigen in modus voor ontwikkelaars

Wanneer u van productie aan ontwikkelaarwijze verandert, zou u geproduceerde klassen en de entiteiten van de Manager van Objecten zoals volmachten moeten ontruimen om onverwachte fouten te verhinderen. Hierna kunt u de modi wijzigen. Voer de volgende stappen uit:

1. Als u overschakelt van productiemodus naar ontwikkelmodus, verwijdert u de inhoud van de mappen `generated/code` en `generated/metadata` :

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Stel de modus in:

   ```bash
   bin/magento deploy:mode:set developer
   ```

   Het volgende bericht wordt weergegeven:

   ```terminal
   Enabled developer mode.
   ```

### Wijzigen in standaardmodus

```bash
bin/magento deploy:mode:set default
```

Het volgende bericht wordt weergegeven:

```terminal
Enabled default mode.
```

### CLI-opdrachten overal uitvoeren

[ Lijn CLI bevelen van overal ](../cli/config-cli.md#config-install-cli-first) in werking.

Als u `<Commerce-install-directory>/bin` niet aan uw systeem `PATH` hebt toegevoegd, kunt u een fout verwachten wanneer het runnen van het bevel door zich.
