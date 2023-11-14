---
title: '''[!DNL Upgrade Compatibility Tool] vereisten"'
description: Controleer of uw systeem voldoet aan de vereisten om het [!DNL Upgrade Compatibility Tool] in een opdrachtregelinterface voor uw Adobe Commerce-project.
exl-id: b8af2e07-3d28-4937-bb88-b0a1c88a2938
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Adobe Commerce-toegangssleutels

{{commerce-only}}

U moet [Adobe Commerce-toegangssleutels](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/#access-keys) om de [!DNL Upgrade Compatibility Tool]. Voeg je Adobe Commerce toegangstoetsen toe aan je `auth.json` bestand, dat zich bevindt op `~/.composer` standaard.

>[!NOTE]
>
>Controleer uw **COMPOSER_HOME** omgevingsvariabele om te zien waar de `auth.json` bestand is gevonden.

De **openbare sleutel** komt overeen met de _gebruikersnaam_ overwegende dat de **persoonlijke sleutel** is de _password_:

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
> Als u uw **Adobe Commerce-toegangssleutels**, kunt u de [!DNL Upgrade Compatibility Tool] en de `composer create-project` de opdracht mislukt.

Uitvoeren `composer install` in uw terminal om gebiedsdelen te installeren.

## Systeemvereisten

De minimumeisen voor het gebruik van de [!DNL Upgrade Compatibility Tool] in een bevel-lijn interface zijn:

| **Vereisten** | **Restricties** |
|----------------|-----------------|
| PHP-versie | >= 7.3 |
| Composer | geen bekende eis. |
| Node.js | Node.js-versies `^12.22.0`, `^14.17.0`, of `>=16.0.0` (zie [Node.js installeren](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs)) |
| Geheugenbeperkingen | minimaal 2 GB RAM. |

[!DNL Upgrade Compatibility Tool] vereist [PCNTL](https://www.php.net/manual/en/book.pcntl.php) en andere PHP extensies voor de uitvoering. Controleer de vereiste PHP extensies met `composer check-platform-reqs` opdracht:

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

Adobe Commerce wordt alleen ondersteund op Linux-besturingssystemen. U kunt de [!DNL Upgrade Compatibility Tool] in een Linux-besturingssysteem. U hoeft de [!DNL Upgrade Compatibility Tool] waar uw Adobe Commerce-exemplaar zich bevindt.

Het is noodzakelijk [!DNL Upgrade Compatibility Tool] om toegang te hebben tot de broncode van de Adobe Commerce-instantie. U kunt de toepassing bijvoorbeeld op de ene server installeren en deze op de Adobe Commerce-installatie op een andere server plaatsen.

Als u de [!DNL Upgrade Compatibility Tool] voor een Adobe Commerce-exemplaar met grote modules en bestanden kan het nodig zijn dat er veel RAM-geheugen beschikbaar is (ten minste 2 GB).

Voer de [!DNL Upgrade Compatibility Tool] van de [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) for [Adobe Commerce over cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} projecten.
