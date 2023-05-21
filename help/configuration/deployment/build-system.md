---
title: Systeeminstellingen samenstellen
description: Leer hoe te om Handel in een bouwstijlsysteem op te stellen.
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Systeeminstellingen samenstellen

U kunt één bouwstijlsysteem hebben dat aan de volgende vereisten voldoet:

- Alle code van de Handel is onder broncontrole in de zelfde bewaarplaats zoals de ontwikkeling en productiesystemen
- Controleer of alle volgende elementen aanwezig zijn: _inbegrepen_ bij broncontrole:

   - `app/etc/config.php`
   - `generated` directory (en subdirectory&#39;s)
   - `pub/media` directory
   - `pub/media/wysiwyg` directory (en subdirectory&#39;s)
   - `pub/static` directory (en subdirectory&#39;s)

- Hiervoor moet een compatibele PHP-versie zijn geïnstalleerd
- Composer moet zijn geïnstalleerd
- De eigenaar en machtigingen van het bestandssysteem zijn ingesteld zoals beschreven in [Vereiste voor uw ontwikkeling, bouw, en productiesystemen](../deployment/technical-details.md).
- Het bouwstijlsysteem vereist geen Handel om worden geïnstalleerd, maar de code moet aan het beschikbaar zijn.

>[!WARNING]
>
>De databaseverbinding is niet vereist als deze al in `config.php`; zie [De configuratie exporteren](../cli/export-configuration.md). Anders is de databaseverbinding vereist.

>[!INFO]
>
>De bouwstijlmachine kan op zijn eigen gastheer of op de zelfde gastheer zijn zoals een geïnstalleerd systeem van de Handel.

## De ontwikkelcomputer configureren

De volgende secties bespreken hoe te om de bouwstijlmachine te vormen.

### Composer installeren

Controleer eerst of Composer al is geïnstalleerd:

Voer een van de volgende opdrachten in voor een opdrachtprompt:

- `composer --help`
- `composer list --help`

Als de hulp van het bevel vertoningen, Composer reeds geïnstalleerd is.

Als een fout wordt weergegeven, voert u de volgende stappen uit om Composer te installeren.

Composer installeren:

1. Verandering in of creeer een lege folder op uw server van de Handel.

1. Voer de volgende opdrachten in:

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Voor extra installatieopties raadpleegt u de [Installatiedocumentatie van composer][composer].

### PHP installeren

PHP installeren op [CentOS] of [Ubuntu].

### Het constructiesysteem instellen

Het constructiesysteem instellen:

1. Meld u aan bij het constructiesysteem als of schakel over naar de eigenaar van het bestandssysteem.
1. Haal de code van de Handel van broncontrole terug.

   Gebruik de volgende opdracht als u Git gebruikt:

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Ga naar de hoofdmap van de handel en voer de volgende gegevens in:

   ```bash
   composer install
   ```

1. Wacht op gebiedsdelen om bij te werken.
1. Eigendom instellen:

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Bijvoorbeeld:

   ```bash
   chown -R commerce-username:apache .
   ```

1. Als u Git gebruikt, opent u `.gitignore` in een teksteditor.
1. Begin elk van de volgende lijnen met a `#` teken om opmerkingen toe te voegen:

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Sla uw wijzigingen op in `.gitignore` en sluit de teksteditor af.
1. Als u Git gebruikt, gebruik de volgende bevelen om de verandering vast te leggen:

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Zie de [`.gitignore` referentie](../reference/config-reference-gitignore.md) voor meer informatie .

1. Het constructiesysteem moet [standaardmodus](../bootstrap/application-modes.md#default-mode) of [ontwikkelmodus](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` is vereist. Het kan `default` of `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
