---
title: Systeemvereisten
description: Meer informatie over softwareafhankelijkheden en systeemvereisten voor Adobe Commerce. Zie geteste configuraties voor compatibiliteit met uw implementatieomgeving.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 77981e3078ddfb87c40419f435086c7e173528b1
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 0%

---

# Systeemvereisten

De volgende informatie geeft een overzicht van softwareafhankelijkheden en services die zijn getest voor Adobe Commerce.

Er zijn enkele verschillen in de afhankelijkheden voor Commerce op Cloud. Serviceversie en compatibiliteitsondersteuning voor Adobe Commerce op Cloud worden bepaald door services die zijn getest en geïmplementeerd in de gehoste cloud-omgevingen en verschillen soms van versies die worden ondersteund door Adobe Commerce-implementaties op locatie.

>[!IMPORTANT]
>
>De tabellen met systeemvereisten bevatten een overzicht van de Adobe Commerce-versies waarop ze van toepassing zijn, inclusief releases die zijn gelabeld als bèta of vroege toegang.
>Zie de [&#x200B; versienota&#39;s &#x200B;](../release/release-notes/overview.md) voor de recentste gepubliceerde versies van Commerce.
>
>Wanneer uw serviceversies niet overeenkomen met de ondersteunde configuratie voor uw Commerce-versie, kan het gedrag afwijken van wat Adobe kan reproduceren tijdens het testen. Adobe Support kan u vragen uw omgeving uit te lijnen met een ondersteunde configuratie voordat u het gerapporteerde gedrag gaat onderzoeken, oplossen of valideren. Nadat u uw omgeving hebt uitgelijnd, kan Adobe Support het onderzoek voortzetten.

In de volgende tabellen worden versies weergegeven van softwareafhankelijkheden van derden die Adobe heeft getest met specifieke Adobe Commerce-releases.

Adobe ondersteunt alleen de systeemvereisten die in de volgende tabellen worden vermeld. Adobe valideert of ondersteunt geen configuraties die niet overeenkomen met een vermelde combinatie. Adobe Commerce 2.4.9 wordt bijvoorbeeld getest met MariaDB 12.3. Voer een upgrade uit naar MariaDB 12.3 voordat u een upgrade uitvoert naar 2.4.9.

## Systeemvereisten voor de nieuwste Commerce-releaseversies

In de volgende tabellen wordt een overzicht gegeven van de systeemvereisten voor de meest recente versie van alle ondersteunde Commerce-versies. Adobe raadt alle klanten aan een upgrade naar deze versies uit te voeren.

>[!BEGINTABS]

>[!TAB  Commerce op Wolk ]

[&#x200B; Commerce op het malplaatje van de Wolk &#x200B;](https://github.com/magento/magento-cloud) verstrekt een standaardconfiguratie voor de diensten compatibel met een specifieke versie van Commerce.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Voor standaardconfiguratie, worden de diensten en de versies bepaald in [&#x200B; het `services.yaml` dossier &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Voor meer details, verwijs naar [&#x200B; de diensten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) in *Commerce op de gids van de Infrastructuur van de Wolk* vormen.

>[!TAB  Commerce op-gebouw ]

{{$include /help/_includes/templated/system-requirements-table.md}}

**MySQL 8.0 bereikte Einde van Steun (EOS) op 30 April, 2026.**
Na deze datum bieden Adobe Commerce 2.4.7, 2.4.6, 2.4.5 en 2.4.4 geen compatibiliteit of
ondersteuning voor MySQL-versies die worden uitgebracht na MySQL 8.0. Adobe zal niet
valideer of verstrek ondersteuning voor nieuwere MySQL belangrijke versies op deze Adobe
Commerce releaselijn.
Alle Adobe Commerce-klanten die versies 2.4.7, 2.4.6, 2.4.5 en 2.4.4 uitvoeren, zijn sterk
adviseerde om hun gegevensbestandservers aan een compatibele versie te migreren MariaDB.

**Elasticsearch 7.17 bereikte Einde van Steun (EOS) op 15 Januari, 2026.**
Na deze datum bieden Adobe Commerce 2.4.6, 2.4.5 en 2.4.4 geen compatibiliteit of
ondersteuning voor alle Elasticsearch-versies die na Elasticsearch 7 worden uitgebracht. Adobe zal niet
Validatie of ondersteuning bieden voor nieuwere Elasticsearch-versies van het hoogste niveau op deze Adobe
Commerce releaselijn.
Alle Adobe Commerce-klanten die versies 2.4.6, 2.4.5, 2.4.4 uitvoeren zijn sterk
adviseerde om hun onderzoeksinfrastructuur aan een compatibele versie te migreren OpenSearch.

>[!ENDTABS]

>[!AVAILABILITY]
>
><sup> 1 </sup> Verenigbaarheid tussen MariaDB 12.3 en Adobe Commerce 2.4.9 zal na de officiële versie van MariaDB 12.3 worden bevestigd, die in mei-Juni timeframe wordt voorzien.

## Systeemvereisten voor eerdere Commerce-releases

In de volgende tabellen worden de systeemvereisten voor Adobe Commerce-releases vermeld, inclusief die voor uitgebreide ondersteuning. Deze tabellen worden uitsluitend ter referentie verstrekt. Adobe raadt het gebruik van niet-ondersteunde versies van softwareafhankelijkheden niet aan en de ondersteuning vereist dat u uw omgeving uitlijnt op een ondersteunde configuratie voordat wij het gerapporteerde gedrag kunnen onderzoeken, oplossen of valideren.

>[!NOTE]
>
>De tabel wordt samengevouwen om de lengte van dit artikel te minimaliseren. Selecteer de koptekst om deze uit te vouwen.

+++Voorschriften voor eerdere introducties

>[!BEGINTABS]

>[!TAB  Commerce op Wolk ]

[&#x200B; Commerce op het malplaatje van de Wolk &#x200B;](https://github.com/magento/magento-cloud) verstrekt een standaardconfiguratie voor de diensten compatibel met een specifieke versie van Commerce.

{{$include /help/_includes/templated/cloud-requirements-table-old-releases.md}}

Voor standaardconfiguratie, worden de diensten en de versies bepaald in [&#x200B; het `services.yaml` dossier &#x200B;](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml).
Voor meer details, verwijs naar [&#x200B; de diensten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) in *Commerce op de gids van de Infrastructuur van de Wolk* vormen.

>[!TAB  Commerce op-gebouw ]

{{$include /help/_includes/templated/system-requirements-table-old-releases.md}}

**MySQL 8.0 bereikte Einde van Steun (EOS) op 30 April, 2026.**
Na deze datum bieden Adobe Commerce 2.4.7, 2.4.6, 2.4.5 en 2.4.4 geen compatibiliteit of
ondersteuning voor MySQL-versies die worden uitgebracht na MySQL 8.0. Adobe zal niet
valideer of verstrek ondersteuning voor nieuwere MySQL belangrijke versies op deze Adobe
Commerce releaselijn.
Alle Adobe Commerce-klanten die versies 2.4.7, 2.4.6, 2.4.5 en 2.4.4 uitvoeren, zijn sterk
adviseerde om hun gegevensbestandservers aan een compatibele versie te migreren MariaDB.

**Elasticsearch 7.17 bereikte Einde van Steun (EOS) op 15 Januari, 2026.**
Na deze datum bieden Adobe Commerce 2.4.6, 2.4.5 en 2.4.4 geen compatibiliteit of
ondersteuning voor alle Elasticsearch-versies die na Elasticsearch 7 worden uitgebracht. Adobe zal niet
Validatie of ondersteuning bieden voor nieuwere Elasticsearch-versies van het hoogste niveau op deze Adobe
Commerce releaselijn.
Alle Adobe Commerce-klanten die versies 2.4.6, 2.4.5, 2.4.4 uitvoeren zijn sterk
adviseerde om hun onderzoeksinfrastructuur aan een compatibele versie te migreren OpenSearch.

>[!ENDTABS]

+++

## PHP-instellingen

Er zijn bepaalde PHP-configuratie-instellingen, zoals de `memory_limit` -instelling, die u kunnen helpen veelvoorkomende problemen te voorkomen bij het gebruik van Adobe Commerce. Zie [&#x200B; Vereiste PHP montages &#x200B;](prerequisites/php-settings.md).

Voor de configuratiebegeleiding van de Wolk, zie [&#x200B; PHP montages &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure/app/php-settings) in *Commerce op de gids van de Infrastructuur van de Wolk*.

### PHP OPcache

Adobe adviseert dat u verifieert dat [&#x200B; PHP OPcache &#x200B;](https://www.php.net/manual/en/book.opcache.php) om prestatiesredenen wordt toegelaten. De OPcache is in veel PHP distributies ingeschakeld.

- **voor Adobe Commerce op de infrastructuurplaatsingen van de Wolk**, wordt de `opcache` uitbreiding geïnstalleerd door gebrek.
- **voor Adobe Commerce op-gebouw plaatsingen:**
   - [&#x200B; verifieer dat de PHP OPcache uitbreiding &#x200B;](prerequisites/php-settings.md#verify-php-is-installed) geïnstalleerd is.
   - Voor specifieke begeleiding op prestatiesmontages, zie de softwareaanbevelingen voor [&#x200B; PHP montages &#x200B;](../performance/software.md#php-settings) in de *Beste praktijken van Prestaties* gids.


Als u OPcache afzonderlijk moet installeren, zie de [&#x200B; documentatie PHP OPcache &#x200B;](https://www.php.net/manual/en/opcache.setup.php).

### PHP Process Control

{{php-process-control}}

### PHPUnit

De ondersteunde belangrijkste PHPUnit-versie is afhankelijk van de Adobe Commerce-versie. Adobe test 2.4.9 met PHPUnit 12, 2.4.8-p5 met PHPUnit 10, en 2.4.7-p10 door 2.4.4-p18 met PHPUnit 9. Installeer PHPUnit als een opdrachtregelprogramma in de hoofdversie die overeenkomt met door Adobe geteste configuraties voor uw release.

### PHP-extensies

De [&#x200B; PHP installatieinstructies &#x200B;](prerequisites/php-settings.md) omvatten een stap voor het installeren van deze uitbreidingen.

>[!TIP]
>
>Voor PHP uitbreidingen in de infrastructuur van de Wolk, zie [&#x200B; PHP uitbreidingen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure/app/php-settings#enable-extensions) in _Commerce op de gids van de Infrastructuur van de Wolk_ toelaten.

>[!BEGINTABS]

>[!TAB  Commerce op Wolk ]

In de volgende tabel worden de ondersteunde PHP-extensies weergegeven wanneer Adobe Commerce wordt geïmplementeerd op het Cloud-platform.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB  Commerce op-gebouw ]

{{$include /help/_includes/templated/php-extensions.md}}

Verwijs naar [&#x200B; officiële PHP documentatie &#x200B;](https://www.php.net/manual/en/extensions.php) voor installatiedetails.

>[!ENDTABS]

## Overige softwarevereisten

In deze sectie worden de ondersteuning en compatibiliteit voor alle andere typen vereiste en optionele software beschreven.

>[!NOTE]
>
>De volgende vereisten gelden voor de nieuwste patchrelease van Adobe Commerce met 2.4.x. Indien van toepassing, wordt Commerce on Cloud-infrastructuuradvies gegeven.

### Browsers

Storefront en Admin:

- Microsoft Edge (nieuwste en vorige hoofdversie)
- Firefox (nieuwste en vorige hoofdversie op elk besturingssysteem)
- Chrome (nieuwste en vorige hoofdversie op elk besturingssysteem)
- Safari (alleen de nieuwste en vorige hoofdversie op macOS)
- Safari voor iOS (nieuwste en vorige hoofdversie voor de winkel)
- Chrome for Android (nieuwste en vorige hoofdversie voor de winkel)

### E-mailserver

De Agent van de Overdracht van de post (MTA) of een server SMTP. Commerce op de infrastructuur van de Wolk gebruikt de [&#x200B; SendGrid e-maildienst &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/project/sendgrid).

### Geheugen

Voor het upgraden van de toepassingen en extensies die u van de Commerce Marketplace en andere bronnen ontvangt, is maximaal 2 GB RAM vereist. Als u een systeem met minder dan 2 GB van RAM gebruikt, creeer a [&#x200B; wisseldossier &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/installation-and-upgrade/out-of-memory-error-during-install-or-upgrade). Anders, zou uw verbetering kunnen ontbreken.

### Besturingssystemen (Linux x86-64)

Linux-distributies, zoals Red Hat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian en dergelijke.

Microsoft Windows en macOS worden **niet** gesteund.

Adobe Commerce heeft voor bepaalde bewerkingen de volgende systeemgereedschappen nodig:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gnu.org/software/gzip/manual/gzip.html)
- [[!DNL lsof]](https://lsof.readthedocs.io/en/stable/manpage/)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.4/en/mysqldump.html)
- [[!DNL nice]](https://www.gnu.org/s/coreutils/manual/html_node/nice-invocation.html)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://www.gnu.org/software/tar/manual/tar.html)

### SSL

- Een geldig beveiligingscertificaat is vereist voor HTTPS.
- Zelfondertekende SSL-certificaten worden niet ondersteund.
- TLS (Transport Layer Security)-vereiste - zowel PayPal als `repo.magento.com` vereisen TLS 1.2 of hoger.

Voor Commerce op de infrastructuur van de Wolk, zie [&#x200B; Snelle configuratie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration) in *Commerce op de gids van de Infrastructuur van de Wolk*.

### Xdebug

Voor Adobe Commerce, gebruik [&#x200B; php_xdebug 2.5.x &#x200B;](https://xdebug.org/download) of later (ontwikkelomgevingen slechts); kan een negatief effect hebben op de prestaties).

Voor Adobe Commerce op Cloud, zie [&#x200B; Xdebug &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/develop/test/debug) in *Commerce op de gids van de Infrastructuur van de Wolk* vormen.

>[!NOTE]
>
>Er is een bekend probleem met `xdebug` dat invloed kan hebben op Adobe Commerce-installaties of op de toegang tot de winkel of beheerder na de installatie. Zie [&#x200B; Bekende kwestie die `xdebug` installatie &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation) in de _Kennisbank van de Steun van Commerce_ beïnvloedt.

<!-- Last updated from includes: 2026-05-11 20:38:54 -->
