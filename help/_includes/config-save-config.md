---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# De gedeelde configuratie bijwerken

**om de configuratie** bij te werken:

1. Meld u aan bij uw ontwikkelsysteem als of schakel over naar de eigenaar van het bestandssysteem.

1. Verandering in de toepassingswortel en stel het dumpbevel in werking.

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Als Commerce bijvoorbeeld is geïnstalleerd in `/var/www/html/magento2` , voert u het volgende in:

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Controleer of `app/etc/config.php` is bijgewerkt.

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
   >Verzend __ geen veranderingen in `generated`, `pub/media`, of `pub/static` folders aan broncontrole. U genereert deze bestanden op uw buildsysteem. Het ontwikkelingssysteem heeft waarschijnlijk code, thema&#39;s, enzovoort, die niet klaar zijn voor gebruik op het productiesysteem.

1. Controleer uw wijzigingen in `app/etc/config.php` alleen om broncontrole te verkrijgen.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
