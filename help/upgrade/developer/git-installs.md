---
title: Een upgrade uitvoeren van een op een kit gebaseerde installatie
description: Voer een upgrade uit van een Adobe Commerce-installatie die u hebt gekloond vanuit een it-opslagplaats.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Een op een git gebaseerde installatie upgraden

Dit onderwerp bespreekt hoe een bijdragende ontwikkelaar Adobe Commerce kan bijwerken zonder het opnieuw te installeren. Als u geen bijdragende ontwikkelaar bent, zie [ een verbetering ](../implementation/perform-upgrade.md) uitvoeren.

U kunt als volgt upgraden als u een ontwikkelaar bent die bijdraagt:

{{$include /help/_includes/server-login.md}}

1. Sla eventuele wijzigingen op die u in het `composer.json` -bestand hebt aangebracht, omdat deze in de volgende stappen worden overschreven.

1. Maak een back-up van uw `composer.json` -bestand.

   ```bash
   cp composer.json composer.json.old
   ```

1. Werk uw lokale opslagplaats bij voor de nieuwste code:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Als `git pull origin develop` ontbreekt, zie [ het oplossen van problemen ](https://support.magento.com/hc/en-us/articles/360034229872).

1. Verdeel het `composer.json.old` -bestand en voeg het samen met het `composer.json` -bestand.

1. Los gebiedsdelen op en schrijf nauwkeurige versies aan het `composer.lock` dossier.

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
