---
title: Systeemvereisten
description: Gebruik deze verwijzing om vereiste softwaregebiedsdelen te identificeren die met de versies van Adobe Commerce zijn getest.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Systeemvereisten

Hieronder volgt een overzicht van softwareafhankelijkheden en services die zijn getest voor Adobe Commerce.

Er zijn enkele verschillen in de afhankelijkheid van de handel op de infrastructuur van de cloud. Serviceversie en compatibiliteitsondersteuning voor Adobe Commerce op cloudinfrastructuur worden bepaald door services die worden getest en geïmplementeerd in de gehoste cloudomgevingen, en verschillen soms van versies die worden ondersteund door Adobe Commerce-implementaties op locatie. Bijvoorbeeld, wordt Elasticsearch 7.17 gesteund voor Handel 2.4.4 voor plaatsingen op-gebouw, maar OpenSearch 1.2 wordt gesteund voor Handel 2.4.4 op de infrastructuur van de Wolk.

De volgende lijsten tonen versies van derdesoftwaregebiedsdelen die de Adobe met specifieke versies van Adobe Commerce heeft getest.

Adobe ondersteunt alleen de combinatie van systeemvereisten die in de volgende tabellen wordt beschreven. 2.4.5 wordt bijvoorbeeld volledig getest met MariaDB 10.4. Adobe raadt u aan een upgrade naar MariaDB 10.4 uit te voeren voordat u de upgrade uitvoert naar versie 2.4.5.

>[!BEGINTABS]

>[!TAB Handel in Cloud]

De [Commerce op Cloud-sjabloon](https://github.com/magento/magento-cloud) verstrekt een standaardconfiguratie voor de diensten compatibel met een specifieke versie van de Handel.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

De services en versies zijn gedefinieerd in [de `services.yaml` file](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Hier volgt de standaardserviceconfiguratie voor Handel 2.4.6 op Cloud-infrastructuur:

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

Zie [Services configureren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) in de _Handel in Cloud-infrastructuur_ hulplijn.

>[!TAB Handel in verkoopruimten]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP-instellingen

Er zijn bepaalde PHP configuratie montages, zoals `memory_limit` Deze instelling kan u helpen algemene problemen te voorkomen bij het gebruik van Adobe Commerce. Zie [Vereiste PHP-instellingen](prerequisites/php-settings.md).

Voor hulp bij de configuratie van de cloud raadpleegt u [PHP-instellingen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) in de _Handel in Cloud-infrastructuur_ hulplijn.

### PHP OPcache

U wordt aangeraden te controleren of [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) is ingeschakeld om redenen van prestaties. De OPcache is in veel PHP distributies ingeschakeld. De `opcache` De extensie wordt standaard geïnstalleerd in de infrastructuur Commerce on Cloud.

Controleer voor on-premesis of PHP OPcache is geïnstalleerd, zie [PHP-instellingen](prerequisites/php-settings.md). Voor specifieke richtlijnen over prestatiesmontages, zie de softwareaanbevelingen voor [PHP-instellingen](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) in de _Aanbevolen werkwijzen voor prestaties_ hulplijn.

Als u OPcache afzonderlijk moet installeren, raadpleegt u de [PHP OPcache-documentatie](https://www.php.net/manual/en/opcache.setup.php).

### PHP Process Control

{{php-process-control}}

### PHPUnit

PHPUnit v9 (als opdrachtregelprogramma).

### PHP-extensies

De [Installatie-instructies voor PHP](prerequisites/php-settings.md) Neem een stap op voor het installeren van deze extensies.

>[!TIP]
>
>Zie voor PHP-extensies in de Cloud-infrastructuur [PHP-extensies inschakelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) in de _Handel in Cloud-infrastructuur_ hulplijn.

>[!BEGINTABS]

>[!TAB Handel in Cloud]

In de volgende tabel worden de ondersteunde PHP-extensies weergegeven wanneer Adobe Commerce wordt geïmplementeerd op het Cloud-platform.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Handel in verkoopruimten]

{{$include /help/_includes/templated/php-extensions.md}}

Zie [officiële PHP-documentatie](https://www.php.net/manual/en/extensions.php) voor installatiegegevens.

>[!ENDTABS]

## Overige

In deze sectie worden de ondersteuning en compatibiliteit voor alle andere typen vereiste en optionele software beschreven.

>[!NOTE]
>
>De volgende vereisten gelden voor de nieuwste patchrelease van Adobe Commerce met 2.4.x. Indien van toepassing, wordt de leidraad voor handel in de infrastructuur van de cloud verstrekt.

### Browsers

Storefront en Admin:

- Microsoft Edge (nieuwste en vorige hoofdversie)
- Firefox (nieuwste en vorige hoofdversie; elk besturingssysteem)
- Chrome (nieuwste en vorige hoofdversie; elk besturingssysteem)
- Safari (nieuwste en vorige hoofdversie; alleen macOS)
- Safari voor iOS (nieuwste en vorige hoofdversie, voor winkel)
- Chrome voor Android (nieuwste en vorige hoofdversie, voor winkel)

### E-mailserver

De Agent van de Overdracht van de post (MTA) of een server SMTP. Handel in Cloud-infrastructuur gebruikt de [E-mailservice SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Geheugen

Voor het upgraden van de toepassingen en extensies die u van de Commerce Marketplace en andere bronnen krijgt, is maximaal 2 GB RAM vereist. Als u een systeem met minder dan 2 GB RAM gebruikt, creeer een [wisselbestand](https://support.magento.com/hc/en-us/articles/360032980432); anders, zou uw verbetering kunnen ontbreken.

### Besturingssystemen (Linux x86-64)

Linux-distributies, zoals RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian en dergelijke. Microsoft Windows en macOS worden niet ondersteund.

Adobe Commerce heeft voor bepaalde bewerkingen de volgende systeemgereedschappen nodig:

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

Voor Handel in Cloud-infrastructuur raadpleegt u [Snelle configuratie](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) in de _Handel in Cloud-infrastructuur_ hulplijn.

### Xdebug

Voor Adobe Commerce: gebruiken [php_xdebug 2.5.x](https://xdebug.org/download) of later (alleen ontwikkelomgevingen; kan een negatief effect hebben op de prestaties).

Voor Adobe Commerce on Cloud raadpleegt u [Xdebug configureren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) in de _Handel in Cloud-infrastructuur_ hulplijn.

>[!NOTE]
>
>Er is een bekend probleem met `xdebug` die invloed kunnen hebben op Adobe Commerce-installaties of op de toegang tot de winkel of beheerder na de installatie. Zie [Bekend probleem dat `xdebug` installatie](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) in de _Kennisbank handelsondersteuning_.
