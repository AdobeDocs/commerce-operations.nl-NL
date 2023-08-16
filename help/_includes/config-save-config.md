---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# De gedeelde configuratie bijwerken

**De configuratie bijwerken**:

1. Meld u aan bij uw ontwikkelsysteem als of schakel over naar de eigenaar van het bestandssysteem.

1. Verandering in de toepassingswortel en stel het dumpbevel in werking.

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Bijvoorbeeld als de Handel geïnstalleerd in is `/var/www/html/magento2`, voert u in:

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Bevestig dat `app/etc/config.php` is bijgewerkt.

   ```bash
   git status
   ```

   Monsterrespons:

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >Do _niet_ brengt wijzigingen aan in de `generated`, `pub/media`, of `pub/static` directory&#39;s aan broncontrole. U genereert deze bestanden op uw buildsysteem. Het ontwikkelingssysteem heeft waarschijnlijk code, thema&#39;s, enzovoort, die niet klaar zijn voor gebruik op het productiesysteem.

1. Breng uw wijzigingen aan in `app/etc/config.php` alleen aan broncontrole.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
