---
title: Installeer de [!DNL Data Migration Tool]
description: Leer hoe u de [!DNL Data Migration Tool] gegevens tussen Magento 1 en Magento 2 over te dragen.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '378'
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

Als u momenteel in `develop` vertakt, moet u in [vrijgegeven vertakking](https://developer.adobe.com/commerce/contributor/guides/install/change-version/) voordat u verdergaat.

Als u de Adobe Commerce- of Magento Open Source-software nog niet hebt geïnstalleerd, [nu installeren](../../installation/prerequisites/commerce.md).
Als u de bewaarplaats GitHub kloont, zorg ervoor u een versiemarkering zoals besproken in controleert [(Medewerker) Kloon de GitHub-opslagplaats](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/).

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

1. Meld u aan bij de toepassingsserver als of schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. Wijzig de hoofdmap van de toepassing.
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

1. Voer desgevraagd uw [verificatietoetsen](../../installation/prerequisites/authentication-keys.md). Uw openbare sleutel is uw gebruikersnaam; uw persoonlijke sleutel is uw wachtwoord.

### Installeren vanuit GitHub

Als u de bewaarplaats GitHub hebt gekloond, volg de stappen hieronder om te installeren [!DNL Data Migration Tool].

1. Meld u aan bij de toepassingsserver als of schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. Wijzig de hoofdmap van de toepassing.
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
