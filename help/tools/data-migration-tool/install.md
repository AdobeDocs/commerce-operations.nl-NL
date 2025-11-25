---
title: Installeer  [!DNL Data Migration Tool]
description: Leer hoe te om  [!DNL Data Migration Tool]  te installeren om gegevens tussen Magento 1 en Magento 2 over te brengen.
exl-id: 5f57067b-3ce8-4b51-b9ae-f60ae089c4ba
topic: Commerce, Migration
feature: Configuration, Install
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# De [!DNL Data Migration Tool] installeren

>[!INFO]
>
>Versies van Magento en [!DNL Data Migration Tool] moeten overeenkomen.


Zorg ervoor u *de zelfde vrijgegeven versie* van zowel Magento 2 als [!DNL Data Migration Tool] gebruikt. Voor Magento versie 2.2.0 moet u bijvoorbeeld ook [!DNL Data Migration Tool] versie 2.2.0 gebruiken.

## Uw versie controleren

U kunt de volgende methoden gebruiken om uw versie van Magento te verifiëren:

- [Composer](#composer-metapackage)
- [GitHub-opslagplaats](#github-repository)

### Composer-pakket

Als u de Magento-software hebt gedownload met een Composer-metapakket, voert u de volgende opdracht in:

```bash
php <magento_root>/bin/magento --version
```

### GitHub-opslagplaats

Als u Magento 2 GitHub bewaart bewaart, ga de volgende bevelen in:

```bash
cd <your Magento 2 clone directory>
```

```bash
git branch
```

Als u momenteel in de `develop` tak bent, moet u in a [&#x200B; vrijgegeven tak &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/change-version) veranderen alvorens u verdergaat.

Als u de software van Adobe Commerce nog niet hebt geïnstalleerd, [&#x200B; installeert het nu &#x200B;](../../installation/prerequisites/commerce.md).
Als u de bewaarplaats GitHub kloont, zorg ervoor u een versiemarkering zoals besproken in [&#x200B; (Medewerker) kloon de bewaarplaats GitHub &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository) controleert.

## Uitgebrachte versies van [!DNL Data Migration Tool] zoeken

Ga naar de [&#x200B; Versies &#x200B;](https://github.com/magento/data-migration-tool/releases) pagina van de [!DNL Data Migration Tool] bewaarplaats GitHub om beschikbare vrijgegeven versies te vinden.

## De [!DNL Data Migration Tool] installeren

U kunt de [!DNL Data Migration Tool] installeren vanaf:

- [` repo.magento.com`](#install-from-repomagentocom)
- [GitHub](#install-from-github)

Controleer voordat u gaat installeren of:

- Voltooid alle die taken in de [&#x200B; worden vermeld Voorwaarden &#x200B;](prerequisites.md) sectie
- [&#x200B; verifieerde de versie &#x200B;](install.md#check-your-version) van Magento 2 software

### Installeren vanuit `repo.magento.com`

Als u [!DNL Data Migration Tool] wilt installeren, moet u `composer.json` in de Magento-hoofdinstallatiemap bijwerken om de locatie van het [!DNL Data Migration Tool] -pakket op te geven.

1. Login aan uw toepassingsserver als, of schakelaar aan, de [&#x200B; eigenaar van het dossiersysteem &#x200B;](../../installation/prerequisites/file-system/overview.md).
1. Wijzig de hoofdmap van de toepassing.
1. Voer de volgende opdrachten in:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   Waar `<version>` moet overeenkomen met de versie van de Magento 2-codebase.

   Voer bijvoorbeeld voor versie 2.2.0 het volgende in:

   ```bash
   composer config repositories.magento composer https://repo.magento.com
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

1. Wanneer ertoe aangezet, ga uw [&#x200B; authentificatietoetsen &#x200B;](../../installation/prerequisites/authentication-keys.md) in. Uw openbare sleutel is uw gebruikersnaam; uw persoonlijke sleutel is uw wachtwoord.

### Installeren vanuit GitHub

Als u de gegevensopslagplaats GitHub hebt gekloond, volg de stappen hieronder om [!DNL Data Migration Tool] te installeren.

1. Login aan uw toepassingsserver als, of schakelaar aan, de [&#x200B; eigenaar van het dossiersysteem &#x200B;](../../installation/prerequisites/file-system/overview.md).
1. Wijzig de hoofdmap van de toepassing.
1. Voer de volgende opdrachten in:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   waarbij `<version>` moet overeenkomen met de versie van de Magento 2-codebase.

   Voer bijvoorbeeld voor versie 2.2.0 het volgende in:

   ```bash
   composer config repositories.data-migration-tool git https://github.com/magento/data-migration-tool
   ```

   ```bash
   composer require magento/data-migration-tool:2.2.0
   ```

### Versie van geïnstalleerd [!DNL Data Migration Tool] controleren

1. Ga naar de map [!DNL Data Migration Tool] : `<vendor>/magento/data-migration-tool` .

1. Open [`composer.json` &#x200B;](https://github.com/magento/data-migration-tool/blob/2.4/composer.json) in een tekstredacteur.

1. De vermelding `version` in dat bestand is de versie van [!DNL Data Migration Tool] .
