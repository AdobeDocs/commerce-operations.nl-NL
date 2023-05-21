---
title: Systeemvereisten
description: Gebruik deze naslaggids om vereiste softwareafhankelijkheden te identificeren die zijn getest met Adobe Commerce- en Magento Open Source-releases.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Systeemvereisten

Deze lijst toont versies van derdesoftwaregebiedsdelen die Adobe met specifieke versies van Adobe Commerce en van Magento Open Source heeft getest. Adobe ondersteunt alleen de combinatie van systeemvereisten die in de volgende tabel wordt beschreven.

2.4.5 wordt bijvoorbeeld volledig getest met MariaDB 10.4. Adobe raadt u aan een upgrade naar MariaDB 10.4 uit te voeren voordat u de upgrade uitvoert naar versie 2.4.5.

{{$include /help/_includes/templated/system-requirements-table.md}}

## Diversen

In deze sectie worden de ondersteuning en compatibiliteit voor alle andere typen vereiste en optionele software beschreven.

>[!NOTE]
>
>De volgende vereisten gelden voor de nieuwste 2.4.x patch-release van Adobe Commerce en Magento Open Source.

### E-mailserver

De Agent van de Overdracht van de post (MTA) of een server SMTP

### Besturingssystemen (Linux x86-64)

Linux-distributies, zoals RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian en dergelijke. Microsoft Windows en macOS worden niet ondersteund.

### PHP-extensies

>[!NOTE]
>
>De [Installatie-instructies voor PHP](prerequisites/php-settings.md) Neem een stap op voor het installeren van deze extensies.

{{$include /help/_includes/templated/php-extensions.md}}

Zie [officiële PHP-documentatie](https://php.net/manual/en/extensions.php) voor installatiegegevens.

### PHP OPcache

We raden u aan te controleren dat [PHP OPcache](https://php.net/manual/en/intro.opcache.php) is ingeschakeld om redenen van prestaties. De OPcache is in veel PHP distributies ingeschakeld. Als u wilt controleren of het programma is geïnstalleerd, raadpleegt u onze [PHP-documentatie](prerequisites/php-settings.md).

Als u de software afzonderlijk moet installeren, raadpleegt u de [PHP OPcache-documentatie](https://php.net/manual/en/opcache.setup.php).

### PHP-instellingen

We raden specifieke PHP configuratie-instellingen aan, zoals `memory_limit`, die algemene problemen bij het gebruik van Adobe Commerce en Magento Open Source kan voorkomen.

Zie voor meer informatie [Vereiste PHP-instellingen](prerequisites/php-settings.md).

### PHPUnit

PHPUnit (als opdrachtregelprogramma) 9.0.0

### RAM

Voor het upgraden van de toepassingen en extensies die u van de Commerce Marketplace en andere bronnen ontvangt, is maximaal 2 GB RAM vereist. Als u een systeem met minder dan 2 GB RAM gebruikt, adviseren wij u tot een [wisselbestand](https://support.magento.com/hc/en-us/articles/360032980432); anders, zou uw verbetering kunnen ontbreken.

### Systeemafhankelijkheden

Voor sommige bewerkingen zijn voor Adobe Commerce en Magento Open Source de volgende systeemgereedschappen vereist:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- Een geldig beveiligingscertificaat is vereist voor HTTPS.
- Zelfondertekende SSL-certificaten worden niet ondersteund.
- Vereiste voor TLS (Transport Layer Security) - PayPal en `repo.magento.com` beide vereisen TLS 1.2 of hoger.

### Ondersteunde browsers

Storefront en Admin:

- Microsoft Edge (nieuwste en vorige hoofdversie)
- Firefox (nieuwste en vorige hoofdversie); elk besturingssysteem)
- Chrome (laatste en vorige hoofdversie) elk besturingssysteem)
- Safari (meest recente en vorige hoofdversie); alleen macOS)
- Safari Mobile voor iPad 2, iPad Mini, iPad met Retina Display (iOS 12 of hoger), voor desktopopslag
- Safari Mobile voor iPhone 6 of hoger; iOS 12 of hoger, voor mobiele winkel
- Chrome voor mobiele apparaten (nieuwste en vorige hoofdversie) [Android 4 of hoger] voor mobiele winkel)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) of later (alleen ontwikkelomgevingen; kan een negatief effect hebben op de prestaties)

>[!NOTE]
>
>Er is een bekend probleem met `xdebug` die van invloed kunnen zijn op Adobe Commerce of Magento Open Source, of op de toegang tot de winkel of beheerder na de installatie. Zie voor meer informatie [Bekend probleem met Xdebug](https://support.magento.com/hc/en-us/articles/360034242212).
