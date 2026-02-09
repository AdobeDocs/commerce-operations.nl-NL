---
title: Systeemvereisten
description: Meer informatie over softwareafhankelijkheden en systeemvereisten voor Adobe Commerce. Ontdek geteste configuraties om ervoor te zorgen dat deze compatibel zijn met uw implementatieomgeving.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 939f9612d243084fc7bf84bfc48d7596a1e028c0
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 0%

---

# Systeemvereisten

Hieronder volgt een overzicht van softwareafhankelijkheden en services die zijn getest voor Adobe Commerce.

Er zijn enkele verschillen in de afhankelijkheden voor Commerce op Cloud. Serviceversie en compatibiliteitsondersteuning voor Adobe Commerce op Cloud worden bepaald door services die zijn getest en geïmplementeerd in de gehoste cloud-omgevingen en verschillen soms van versies die worden ondersteund door Adobe Commerce-implementaties op locatie. Elasticsearch 7.17 wordt bijvoorbeeld ondersteund voor Commerce 2.4.4 voor on-premise implementaties, maar OpenSearch 1 wordt ondersteund voor 2.4.4 Adobe Commerce op Cloud.

>[!NOTE]
>
>De systeemvereisten gelden alleen voor vrijgegeven versies van Adobe Commerce. Beta of eerdere versies voor toegang zijn niet inbegrepen. Zie de [&#x200B; versienota&#39;s &#x200B;](../release/release-notes/overview.md) om meer over de recentste vrijgegeven versies van Adobe Commerce te leren.

In de volgende tabellen worden versies weergegeven van softwareafhankelijkheden van derden die Adobe heeft getest met specifieke Adobe Commerce-releases.

Adobe ondersteunt alleen de combinatie van systeemvereisten die in de volgende tabellen wordt beschreven. 2.4.5 wordt bijvoorbeeld volledig getest met MariaDB 10.4. Adobe raadt u aan een upgrade naar MariaDB 10.4 uit te voeren voordat u de upgrade uitvoert naar versie 2.4.5.

Adobe raadt u aan de RabbitMQ-versies incrementeel te upgraden om een soepel upgradeproces te garanderen en implementatiefouten te voorkomen. Als u bijvoorbeeld een upgrade uitvoert van versie 3.8 naar 4.1, moet u eerst een upgrade uitvoeren van 3.8 naar 3.9, vervolgens van 3.9 naar 3.10, enzovoort. Pas na het bereiken van versie 3.13 kunt u doorgaan met de upgrade naar versie 4.1.

>[!BEGINTABS]

>[!TAB  Commerce op Wolk ]

[&#x200B; Commerce op het malplaatje van de Wolk &#x200B;](https://github.com/magento/magento-cloud) verstrekt een standaardconfiguratie voor de diensten compatibel met een specifieke versie van Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

De diensten en de versies worden bepaald in [&#x200B; het `services.yaml` dossier &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Hier volgt de standaardserviceconfiguratie voor Commerce 2.4.6 op Cloud-infrastructuur:

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

Zie [&#x200B; de diensten &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html?lang=nl-NL) in _Commerce op de gids van de Infrastructuur van de Wolk_ vormen.

>[!TAB  Commerce op-gebouw ]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP-instellingen

Er zijn bepaalde PHP-configuratie-instellingen, zoals de `memory_limit` -instelling, die u kunnen helpen veelvoorkomende problemen te voorkomen bij het gebruik van Adobe Commerce. Zie [&#x200B; Vereiste PHP montages &#x200B;](prerequisites/php-settings.md).

Voor de configuratiebegeleiding van de Wolk, zie [&#x200B; PHP montages &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html?lang=nl-NL) in _Commerce op de gids van de Infrastructuur van de Wolk_.

### PHP OPcache

Men adviseert dat u verifieert dat [&#x200B; PHP OPcache &#x200B;](https://www.php.net/manual/en/intro.opcache.php) om prestatiesredenen wordt toegelaten. De OPcache is in veel PHP distributies ingeschakeld. De extensie `opcache` wordt standaard geïnstalleerd in de Commerce-infrastructuur voor de cloud.

Voor op-gebouw, verifieer dat PHP OPcache geïnstalleerd is, zie [&#x200B; PHP montages &#x200B;](prerequisites/php-settings.md). Of voor specifieke begeleiding op prestatiesmontages, zie de softwareaanbevelingen voor [&#x200B; PHP montages &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html?lang=nl-NL#php-settings) in de _Beste praktijken van Prestaties_ gids.

Als u OPcache afzonderlijk moet installeren, zie de [&#x200B; documentatie PHP OPcache &#x200B;](https://www.php.net/manual/en/opcache.setup.php).

### PHP Process Control

{{php-process-control}}

### PHPUnit

PHPUnit v9 (als opdrachtregelprogramma).

### PHP-extensies

De [&#x200B; PHP installatieinstructies &#x200B;](prerequisites/php-settings.md) omvatten een stap voor het installeren van deze uitbreidingen.

>[!TIP]
>
>Voor PHP uitbreidingen in de infrastructuur van de Wolk, zie [&#x200B; PHP uitbreidingen &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html?lang=nl-NL#enable-extensions) in _Commerce op de gids van de Infrastructuur van de Wolk_ toelaten.

>[!BEGINTABS]

>[!TAB  Commerce op Wolk ]

In de volgende tabel worden de ondersteunde PHP-extensies weergegeven wanneer Adobe Commerce wordt geïmplementeerd op het Cloud-platform.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB  Commerce op-gebouw ]

{{$include /help/_includes/templated/php-extensions.md}}

Verwijs naar [&#x200B; officiële PHP documentatie &#x200B;](https://www.php.net/manual/en/extensions.php) voor installatiedetails.

>[!ENDTABS]

## Overige

In deze sectie worden de ondersteuning en compatibiliteit voor alle andere typen vereiste en optionele software beschreven.

>[!NOTE]
>
>De volgende vereisten gelden voor de nieuwste patchrelease van Adobe Commerce met 2.4.x. Indien van toepassing, wordt Commerce on Cloud-infrastructuuradvies gegeven.

### Browsers

Storefront en Admin:

- Microsoft Edge (nieuwste en vorige hoofdversie)
- Firefox (nieuwste en vorige hoofdversie; elk besturingssysteem)
- Chrome (nieuwste en vorige hoofdversie; elk besturingssysteem)
- Safari (nieuwste en vorige hoofdversie; alleen macOS)
- Safari voor iOS (nieuwste en vorige hoofdversie, voor winkel)
- Chrome for Android (nieuwste en vorige hoofdversie, voor winkel)

### E-mailserver

De Agent van de Overdracht van de post (MTA) of een server SMTP. Commerce op de infrastructuur van de Wolk gebruikt de [&#x200B; SendGrid e-maildienst &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html?lang=nl-NL).

### Geheugen

Voor het upgraden van de toepassingen en extensies die u van de Commerce Marketplace en andere bronnen ontvangt, is maximaal 2 GB RAM vereist. Als u een systeem met minder dan 2 GB van RAM gebruikt, creeer a [&#x200B; wisseldossier &#x200B;](https://support.magento.com/hc/en-us/articles/360032980432); anders, zou uw verbetering kunnen ontbreken.

### Besturingssystemen (Linux x86-64)

Linux-distributies, zoals RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian en dergelijke.

Microsoft Windows en macOS worden **niet** gesteund.

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
- TLS (Transport Layer Security)-vereiste - zowel PayPal als `repo.magento.com` vereisen TLS 1.2 of hoger.

Voor Commerce op de infrastructuur van de Wolk, zie [&#x200B; Snelle configuratie &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL) in _Commerce op de gids van de Infrastructuur van de Wolk_.

### Xdebug

Voor Adobe Commerce, gebruik [&#x200B; php_xdebug 2.5.x &#x200B;](https://xdebug.org/download) of recenter (ontwikkelomgevingen slechts; kan een negatief effect op prestaties hebben).

Voor Adobe Commerce op Cloud, zie [&#x200B; Xdebug &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html?lang=nl-NL) in _Commerce op de gids van de Infrastructuur van de Wolk_ vormen.

>[!NOTE]
>
>Er is een bekend probleem met `xdebug` dat invloed kan hebben op Adobe Commerce-installaties of op de toegang tot de winkel of beheerder na de installatie. Zie [&#x200B; Bekende kwestie die `xdebug` installatie &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html?lang=nl-NL) in de _Kennisbank van de Steun van Commerce_ beïnvloedt.


<!-- Last updated from includes: 2026-01-16 17:09:37 -->
