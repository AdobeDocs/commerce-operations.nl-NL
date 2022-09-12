---
title: De bewerkingsmodus instellen
description: Lees meer over het instellen van de Adobe Commerce-bewerkingsmodi.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# De bewerkingsmodus instellen

{{file-system-owner}}

Om veiligheid en gebruiksgemak te verbeteren, hebben wij een bevel toegevoegd dat schakelaars [toepassingsmodi](../bootstrap/application-modes.md) van ontwikkelaar tot productie en omgekeerd.

De productiemodus biedt betere prestaties omdat statische weergavebestanden worden gevuld in het dialoogvenster `pub/static` en vanwege codecompilatie.

>[!INFO]
>
>In versie 2.0.6 en recenter, plaatst de Handel niet uitdrukkelijk dossier of foldertoestemmingen wanneer u tussen gebrek, ontwikkelt, en productiemodi schakelt. In tegenstelling tot andere modi worden de ontwikkelaar- en productiemodus ingesteld in de `env.php` bestand. Adobe Commerce op cloudinfrastructuur ondersteunt alleen productie- en onderhoudsmodi.
>
>Zie [Eigendom en machtigingen van de handel in ontwikkeling en productie](../deployment/file-system-permissions.md).

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
- `pub/static` bevat een bestand dat de versie van statische inhoud aangeeft; dit bestand is niet verwijderd

>[!INFO]
>
>Standaard wordt bij Handel de optie `var` mappen voor het opslaan van de cache, logbestanden en gecompileerde code. U kunt deze map aanpassen, maar in deze handleiding wordt ervan uitgegaan dat `var`.

## De huidige modus weergeven

De eenvoudigste manier om dat te doen is deze opdracht als de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md). Als u een gedeelde host hebt, is dit de gebruiker die uw provider u geeft om u aan te melden bij de server. Als u een privé server hebt, is het typisch een lokale gebruikersrekening op de server van de Handel.

Opdrachtgebruik:

```bash
bin/magento deploy:mode:show
```

Een bericht dat lijkt op de volgende vertoningen:

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

waarbij:

- **`{mode}`** kan `default`, `developer`, of `production`

## Wijzigingsmodi

Opdrachtgebruik:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

waarbij:

- **`{mode}`** is vereist; het kan `developer` of `production`

- **`--skip-compilation`** is een optionele parameter die u kunt gebruiken om over te slaan [codecompilatie](../cli/code-compiler.md) wanneer u overschakelt naar de productiemodus.

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
Successfully processed LESS and/or [Sass](https://glossary.magento.com/sass) files
[CSS](https://glossary.magento.com/css) deployment complete
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

1. Als u van productiemodus aan ontwikkelaarwijze verandert, schrap de inhoud van `generated/code` en `generated/metadata` mappen:

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

[CLI-opdrachten overal uitvoeren](../cli/config-cli.md#config-install-cli-first).

Als u nog geen `<Commerce-install-directory>/bin` op uw systeem `PATH`, dan kunt u een fout verwachten wanneer het runnen van het bevel op zich.
