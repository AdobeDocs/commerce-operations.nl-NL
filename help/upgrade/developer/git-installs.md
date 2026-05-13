---
title: Een upgrade uitvoeren van een op een kit gebaseerde installatie
description: Voer een upgrade uit van een Adobe Commerce-installatie die u hebt gekloond vanuit een it-opslagplaats.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 87302734f3ff91f0403beac283ff21925d89318d
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---

# Een op een git gebaseerde installatie upgraden

Dit onderwerp bespreekt hoe een bijdragende ontwikkelaar Adobe Commerce kan bijwerken zonder het opnieuw te installeren. Als u geen bijdragende ontwikkelaar bent, zie [&#x200B; een verbetering &#x200B;](../implementation/perform-upgrade.md) uitvoeren.

U kunt als volgt upgraden als u een ontwikkelaar bent die bijdraagt:

{{$include /help/_includes/server-login.md}}

1. Sla eventuele wijzigingen op die u in het `composer.json` -bestand hebt aangebracht, omdat deze in de volgende stappen worden overschreven.

1. Maak een back-up van uw `composer.json` -bestand.

   ```shell
   cp composer.json composer.json.old
   ```

1. Werk uw lokale opslagplaats bij voor de nieuwste code:

   ```shell
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Als `git pull origin develop` ontbreekt, zie [&#x200B; het oplossen van problemen &#x200B;](https://support.magento.com/hc/en-us/articles/360034229872).

1. Verdeel het `composer.json.old` -bestand en voeg het samen met het `composer.json` -bestand.

1. Los gebiedsdelen op en schrijf nauwkeurige versies aan het `composer.lock` dossier.

   ```shell
   composer update
   ```

1. De database bijwerken:

   ```shell
   bin/magento setup:upgrade
   ```

1. De cache reinigen:

   ```shell
   bin/magento cache:clean
   ```

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
