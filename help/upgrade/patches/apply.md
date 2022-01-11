---
title: Patches toepassen
description: Leer hoe u patches kunt toepassen op een Adobe Commerce- of Magento Open Source-project.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Patches toepassen

U kunt patches op een van de volgende manieren toepassen:

- [Kwaliteitspatches](https://devdocs.magento.com/quality-patches/tool.html)
- [Opdrachtregel](../patches/apply.md#command-line)
- [Composer](../patches/apply.md#composer)

## Composer

>[!IMPORTANT]
>
>Als u officiële kwaliteitspatches wilt toepassen, gebruikt u de optie [Kwaliteitspatches](https://devdocs.magento.com/quality-patches/tool.html). Voer altijd uitgebreide tests uit voordat u een aangepaste patch implementeert.

Een aangepaste patch toepassen met Composer:

1. Open de opdrachtregeltoepassing en navigeer naar de projectmap.
1. Voeg de `cweagans/composer-patches` insteekmodule voor de `composer.json` bestand.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Bewerk de `composer.json` en voeg de volgende sectie toe om op te geven:
   - **Module:** *\&quot;magento/module-payment\&quot;*
   - **Titel:** *\&quot;MAGETWO-56934: Afhandelingspagina loopt vast bij bestellen met Authorize.net met ongeldige creditcard\&quot;*
   - **Pad naar patch:** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   Bijvoorbeeld:

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   Als een patch van invloed is op meerdere modules, moet u meerdere patchbestanden maken voor meerdere modules.

1. Breng de pleister aan. Gebruik de `-v` optie slechts als u het zuiveren informatie wilt zien.

   ```bash
   composer -v install
   ```

1. Werk de `composer.lock` bestand. In het vergrendelingsbestand wordt bijgehouden welke patches zijn toegepast op elk Composer-pakket in een object.

   ```bash
   composer update --lock
   ```

## Opdrachtregel

Patches toepassen vanaf de opdrachtregel:

1. Het lokale bestand uploaden naar het `<Magento_root>` directory op de server die FTP, SFTP, SSH, of uw normale vervoermethode gebruikt.
1. Aanmelden bij de server als de [beheerder](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli.html#config-install-cli-first) en controleert u of het bestand zich in de juiste map bevindt.
1. Voer in de opdrachtregelinterface de volgende opdrachten uit volgens de patchextensie:

   ```bash
   patch < patch_file_name.patch
   ```

   De opdracht gaat ervan uit dat het bestand dat moet worden gerepareerd, zich ten opzichte van het patchbestand bevindt.

   >[!NOTE]
   >
   >Als de opdrachtregel het volgende weergeeft: `File to patch:`, betekent dit dat het bedoelde bestand niet kan worden gevonden, zelfs niet als het pad juist lijkt. In de doos die in de bevel-lijn terminal wordt getoond, toont de eerste lijn het te patchen dossier. Kopieer het bestandspad en plak het in de `File to patch:` vragen en drukken `Enter` en de pleister moet volledig zijn.

1. Vernieuw de cache in Admin onder om de wijzigingen door te voeren **Systeem** > Gereedschappen > **Cachebeheer**.

   Alternatief, kan het flard plaatselijk met het zelfde bevel worden toegepast, dan begaan en normaal gedrukt.
