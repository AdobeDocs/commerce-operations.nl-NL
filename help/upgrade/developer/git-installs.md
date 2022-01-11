---
title: Een upgrade uitvoeren van een op een kit gebaseerde installatie
description: Voer een upgrade uit van een Adobe Commerce- of Magento Open Source-installatie die u hebt gekloond vanuit een it-opslagplaats.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Een op een git gebaseerde installatie upgraden

Dit onderwerp bespreekt hoe een bijdragende ontwikkelaar Adobe Commerce of Magento Open Source kan bijwerken zonder het opnieuw te installeren. Als u geen bijdragende ontwikkelaar bent, zie [Een upgrade uitvoeren](../implementation/perform-upgrade.md).

U kunt als volgt upgraden als u een ontwikkelaar bent die bijdraagt:

1. Meld u aan bij uw server.

1. Naar de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Ga naar de map waarin u de toepassing hebt gekloond. Bijvoorbeeld:

   ```bash
   cd /var/www/magento2
   ```

1. Sla de wijzigingen op die u in het dialoogvenster `composer.json` omdat de volgende stappen dit overschrijven.

1. Maak een back-up van uw `composer.json` bestand.

   ```bash
   cp composer.json composer.json.old
   ```

1. Werk uw lokale opslagplaats bij voor de nieuwste code:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Indien `git pull origin develop` mislukt, zie [problemen oplossen](https://support.magento.com/hc/en-us/articles/360034229872).

1. Diff en voeg uw samen `composer.json.old` met de `composer.json` bestand.

1. Los gebiedsdelen op en schrijf nauwkeurige versies aan `composer.lock` bestand.

   ```bash
   composer update
   ```

1. De database bijwerken:

   ```bash
   bin/magento setup:upgrade
   ```

1. De cache reinigen:

   ```bash
   bin/magento cache:clean
   ```
