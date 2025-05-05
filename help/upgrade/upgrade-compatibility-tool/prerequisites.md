---
title: '[!DNL Upgrade Compatibility Tool] requirements'
description: Verifieer dat uw systeem aan de noodzakelijke vereisten voldoet om  [!DNL Upgrade Compatibility Tool]  in een bevel-lijn interface voor uw project van Adobe Commerce in werking te stellen.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Adobe Commerce-toegangssleutels

{{commerce-only}}

U moet [ de toegangssleutels van Adobe Commerce ](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) hebben om [!DNL Upgrade Compatibility Tool] te downloaden en te gebruiken. Voeg uw Adobe Commerce-toegangstoetsen toe aan uw `auth.json` -bestand, dat zich standaard op `~/.composer` bevindt.

>[!NOTE]
>
>Controleer uw **COMPOSER_HOME** milieuvariabele om te zien waar het `auth.json` dossier wordt gevestigd.

De **openbare sleutel** beantwoordt aan _gebruikersbenaming_ terwijl de **privé sleutel** het _wachtwoord_ is:

## Voorbeeld van Adobe Commerce-toegangssleutels

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> Als u niet correct uw **de toegangssleutels van Adobe Commerce** vormt, kunt u niet [!DNL Upgrade Compatibility Tool] downloaden en het `composer create-project` bevel zal ontbreken.

Voer `composer install` uit in uw terminal om afhankelijkheden te installeren.

## Systeemvereisten

De minimumvereisten om [!DNL Upgrade Compatibility Tool] in een bevel-lijn interface te gebruiken zijn:

| **Vereisten** | **Beperkingen** |
|----------------|-----------------|
| PHP-versie | >= 7,3 |
| Composer | geen bekende eis. |
| Node.js | Node.js versies `^12.22.0`, `^14.17.0`, of `>=16.0.0` (zie [ Install Node.js ](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)) |
| Geheugenbeperkingen | minimaal 2 GB RAM. |

[!DNL Upgrade Compatibility Tool] vereist [ PCNTL ](https://www.php.net/manual/en/book.pcntl.php) en andere PHP uitbreidingen voor de uitvoering. Controleer de vereiste PHP-extensies met de opdracht `composer check-platform-reqs` :

```bash
# Example output of `composer check-platform-reqs` command for UCT 2.2.6 and PHP 7.4:

$ composer check-platform-reqs
Checking platform requirements for packages in the vendor dir
ext-ctype     *         success provided by symfony/polyfill-ctype
ext-dom       20031129  success
ext-filter    7.4.30    success
ext-json      7.4.30    success
ext-libxml    7.4.30    success
ext-mbstring  *         success provided by symfony/polyfill-mbstring
ext-openssl   7.4.30    success
ext-pcntl     7.4.30    success
ext-pcre      7.4.30    success
ext-phar      7.4.30    success
ext-simplexml 7.4.30    success
ext-tokenizer 7.4.30    success
ext-xml       7.4.30    success
ext-xmlwriter 7.4.30    success
ext-zip       1.15.6    success
php           7.4.30    success
```

Adobe Commerce wordt alleen ondersteund op Linux-besturingssystemen. U kunt de [!DNL Upgrade Compatibility Tool] uitvoeren in een Linux-besturingssysteem. U hoeft de [!DNL Upgrade Compatibility Tool] niet uit te voeren waar uw Adobe Commerce-instantie zich bevindt.

De [!DNL Upgrade Compatibility Tool] moet toegang hebben tot de broncode van de Adobe Commerce-instantie. U kunt de toepassing bijvoorbeeld op de ene server installeren en deze op de Adobe Commerce-installatie op een andere server plaatsen.

Als u de [!DNL Upgrade Compatibility Tool] uitvoert tegen een Adobe Commerce-instantie met grote modules en bestanden, hebt u wellicht veel RAM-geheugen nodig (ten minste 2 GB).

Stel [!DNL Upgrade Compatibility Tool] van [[!DNL Site-Wide Analysis Tool] in werking ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) voor [ Adobe Commerce op de projecten van de wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} .
