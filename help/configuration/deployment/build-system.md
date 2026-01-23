---
title: System Setup (Systeeminstellingen) bouwen
description: Leer hoe u Commerce in een build-systeem kunt implementeren.
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Systeeminstellingen samenstellen

U kunt één bouwstijlsysteem hebben dat aan de volgende vereisten voldoet:

- Alle Commerce-code staat onder broncontrole in dezelfde opslagplaats als de ontwikkelings- en productiesystemen
- Zorg ervoor elk van het volgende _inbegrepen_ in broncontrole is:

   - `app/etc/config.php`
   - `generated` map (en submappen)
   - `pub/media` directory
   - `pub/media/wysiwyg` map (en submappen)
   - `pub/static` map (en submappen)

- Hiervoor moet een compatibele PHP-versie zijn geïnstalleerd
- Composer moet zijn geïnstalleerd
- Het heeft bezit van het dossiersysteem en toestemmingen die zoals in [&#x200B; worden besproken Vereiste voor uw ontwikkeling, bouwt, en productiesystemen &#x200B;](../deployment/technical-details.md).
- Voor het constructiesysteem hoeft Commerce niet te worden geïnstalleerd, maar de code moet wel beschikbaar zijn.

>[!WARNING]
>
>De gegevensbestandverbinding wordt niet vereist als het reeds in `config.php` bevat is; zie [&#x200B; de configuratie &#x200B;](../cli/export-configuration.md) uitvoeren. Anders is de databaseverbinding vereist.

>[!INFO]
>
>De bouwstijlmachine kan op zijn eigen gastheer of op de zelfde gastheer zijn zoals een geïnstalleerd systeem van Commerce.

## De ontwikkelcomputer configureren

De volgende secties bespreken hoe te om de bouwstijlmachine te vormen.

### Composer installeren

Controleer eerst of Composer al is geïnstalleerd:

Voer een van de volgende opdrachten in voor een opdrachtprompt:

- `composer --help`
- `composer list --help`

Als de hulp van het bevel vertoningen, Composer reeds geïnstalleerd is.

Als er een fout wordt weergegeven, voert u de volgende stappen uit om Composer te installeren.

Composer installeren:

1. Wijzig of maak een lege map op uw Commerce-server.

1. Voer de volgende opdrachten in:

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Voor extra installatieopties, zie de [&#x200B; documentatie van de de installatieinstallatie van Composer &#x200B;](https://getcomposer.org/download/).

### PHP installeren

Installeer PHP op [&#x200B; CentOS &#x200B;](https://wiki.centos.org/HowTos/php7) of [&#x200B; Ubuntu &#x200B;](https://help.ubuntu.com/lts/serverguide/php.html).

### Het constructiesysteem instellen

Het constructiesysteem instellen:

1. Meld u aan bij het constructiesysteem als of schakel over naar de eigenaar van het bestandssysteem.
1. Haal de Commerce-code op van het bronbesturingselement.

   Gebruik de volgende opdracht als u Git gebruikt:

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Ga naar de Commerce-hoofdmap en voer de volgende gegevens in:

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
1. Begin elk van de volgende regels met een `#` -teken om er opmerkingen over te maken:

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Sla de wijzigingen in `.gitignore` op en sluit de teksteditor af.
1. Als u Git gebruikt, gebruik de volgende bevelen om de verandering vast te leggen:

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Zie [`.gitignore` verwijzing &#x200B;](../reference/config-reference-gitignore.md) voor meer informatie.

1. Het bouwstijlsysteem zou [&#x200B; standaardwijze &#x200B;](../bootstrap/application-modes.md#default-mode) of [&#x200B; ontwikkelaarwijze &#x200B;](../bootstrap/application-modes.md#developer-mode) moeten gebruiken:

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` is vereist. Dit kan `default` of `developer` zijn.

