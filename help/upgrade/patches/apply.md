---
title: Patches toepassen
description: Leer hoe u patches kunt toepassen op een Adobe Commerce-project.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Patches toepassen

U kunt patches op een van de volgende manieren toepassen:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL){target="_blank"}
- [Opdrachtregel](../patches/apply.md#command-line)
- [Composer](../patches/apply.md#composer)


>[!TIP]
>
>Zie [ beste praktijken ](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) voor informatie over gecentraliseerde het opsluiten voor Adobe Commerce bij ondernemingsschaal.

## Composer

>[!IMPORTANT]
>
>Gebruik [[!DNL Quality Patches Tool] ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL){target="_blank"} om officiële kwaliteitspatches toe te passen. Voer altijd uitgebreide tests uit voordat u een aangepaste patch implementeert.

Een aangepaste patch toepassen met Composer:

1. Open de opdrachtregeltoepassing en navigeer naar de projectmap.
1. Voeg de `cweagans/composer-patches` -plug-in toe aan het `composer.json` -bestand.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Bewerk het `composer.json` -bestand en voeg de volgende sectie toe om op te geven:
   - **Module:** *\ &quot;magento/module-payment\&quot;*
   - **Titel:** *\ &quot;MAGETWO-56934: De pagina van de Afhandeling bevriest wanneer het opdracht geven tot met Authorize.net met ongeldige creditcard \&quot;*
   - **Weg aan flard:** *\ &quot;patches/composer/github-issue-6474.diff \&quot;*

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

1. Breng de pleister aan. Gebruik de optie `-v` alleen als u foutopsporingsinformatie wilt zien.

   ```bash
   composer -v install
   ```

1. Werk het `composer.lock` bestand bij. In het vergrendelingsbestand wordt bijgehouden welke patches zijn toegepast op elk Composer-pakket in een object.

   ```bash
   composer update --lock
   ```

## Opdrachtregel

Patches toepassen vanaf de opdrachtregel:

1. Upload het lokale bestand naar de map `<Magento_root>` op de server met behulp van FTP, SFTP, SSH of uw normale transportmethode.
1. Logboek in de server als [ admin gebruiker ](../../configuration/cli/config-cli.md#prerequisites) en verifieert dat het dossier in de correcte folder is.
1. Voer in de opdrachtregelinterface de volgende opdrachten uit volgens de patchextensie:

   ```bash
   patch < patch_file_name.patch
   ```

   De opdracht gaat ervan uit dat het bestand dat moet worden gerepareerd, zich ten opzichte van het patchbestand bevindt.

   >[!NOTE]
   >
   >Als op de opdrachtregel het volgende wordt weergegeven: `File to patch:` , betekent dit dat het bedoelde bestand niet kan worden gevonden, zelfs niet als het pad juist lijkt. In de doos die in de bevel-lijn terminal wordt getoond, toont de eerste lijn het te patchen dossier. Kopieer het bestandspad en plak het in de `File to patch:` prompt en druk op `Enter` . De patch moet dan zijn voltooid.

1. Voor de veranderingen die moeten worden weerspiegeld, vernieuw het geheime voorgeheugen in Admin onder **Systeem** > Hulpmiddelen > **het Beheer van het Geheime voorgeheugen**.

   Alternatief, kan het flard plaatselijk met het zelfde bevel worden toegepast, dan begaan en normaal gedrukt.
