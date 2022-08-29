---
title: Installeer de [!DNL Data Migration Tool]
description: Leer hoe u de [!DNL Data Migration Tool] gegevens tussen Magento 1 en Magento 2 over te dragen.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# Installeer de [!DNL Data Migration Tool]

>[!INFO]
>
>Versies van Magento en [!DNL Data Migration Tool] moet overeenkomen.


Zorg ervoor dat u *dezelfde uitgebrachte versie* van zowel Magento 2 als [!DNL Data Migration Tool]. Voor Magento versie 2.2.0 moet u bijvoorbeeld ook de opdracht [!DNL Data Migration Tool] versie 2.2.0.

## Uw versie controleren

U kunt de volgende methoden gebruiken om uw versie van Magento te verifiëren:

- [Composer](#composer-metapackage)
- [GitHub-opslagplaats](#github-repository)

### Composer-pakket

Als u de Magento-software hebt gedownload met een [Composer](https://glossary.magento.com/composer) de metapack, gaat het volgende bevel in:

```bash
php <magento_root>/bin/magento --version
```

### GitHub-opslagplaats

Als u de Magento 2 bewaarplaats GitHub kloond, ga de volgende bevelen in:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Als u momenteel in `develop` vertakt, moet u in <a href="https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/dev_downgrade.html">vrijgegeven vertakking</a> voordat u verdergaat.

Als u de Magento-software nog niet hebt geïnstalleerd, [nu installeren](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html).
Als u de bewaarplaats GitHub kloont, zorg ervoor u een versiemarkering zoals besproken in controleert [(Medewerker) Clone the Magento repository](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/dev_install.html).

## Gepubliceerde versies van [!DNL Data Migration Tool]

Ga naar de [Uitstoot](https://github.com/magento/data-migration-tool/releases) pagina van de [!DNL Data Migration Tool] De bewaarplaats van GitHub om beschikbare vrijgegeven versies te vinden.

## Installeer de [!DNL Data Migration Tool]

U kunt de [!DNL Data Migration Tool] van:

- [` repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Controleer voordat u gaat installeren of:

- Alle taken die in de [Voorwaarden](prerequisites.md) sectie
- [De versie is geverifieerd](install.md#check-your-version) van de Magento 2-software

### Installeren vanaf `repo.magento.com`

Als u het dialoogvenster [!DNL Data Migration Tool], moet u bijwerken `composer.json` in de hoofdinstallatiemap van de Magento om de locatie van de [!DNL Data Migration Tool] pakket.

1. Meld u aan bij de Magento-server als of schakel over naar de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Wijzigen in hoofdmap van Magento 2.
1. Voer de volgende opdrachten in:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Wanneer `<version>` moet overeenkomen met de versie van de codebase Magento 2.

   Voer bijvoorbeeld voor versie 2.2.0 het volgende in:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Voer desgevraagd uw [verificatietoetsen](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html). Uw openbare sleutel is uw gebruikersnaam; uw persoonlijke sleutel is uw wachtwoord.

### Installeren vanuit GitHub

Als u Magento 2 van de bewaarplaats van GitHub hebt gekloond, volg hieronder de stappen om te installeren [!DNL Data Migration Tool].

1. Meld u aan bij de Magento-server als of schakel over naar de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Wijzigen in hoofdmap van Magento 2.
1. Voer de volgende opdrachten in:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   waar `<version>` moet overeenkomen met de versie van de codebase Magento 2.

   Voer bijvoorbeeld voor versie 2.2.0 het volgende in:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Versie van geïnstalleerde versie controleren [!DNL Data Migration Tool]

1. Wijzigen in uw [!DNL Data Migration Tool] map: `<vendor>/magento/data-migration-tool`.

1. Openen [`composer.json`](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) in een teksteditor.

1. De `version` de vermelding in dat bestand is de versie van het [!DNL Data Migration Tool].
