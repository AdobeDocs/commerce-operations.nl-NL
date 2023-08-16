---
title: Toepassingsserver voor GraphQL API's
description: Volg deze instructies voor het inschakelen van de toepassingsserver voor GraphQL API's in uw Adobe Commerce-implementatie.
badgeCoreBeta: label="2.4.7-bèta1" type="informative"
exl-id: 346cc722-131e-4ed0-bc8c-23c3a1e58258
source-git-commit: f085c0a77fe59ff3b2d76abbd6965b6bc8ee69db
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Toepassingsserver voor GraphQL API&#39;s

Met de Commerce Application Server voor GraphQL API&#39;s kan Adobe Commerce de status handhaven tussen de Commerce GraphQL API-aanvragen en wordt de bootstrappingtijd voor elke aanvraag verminderd. Door de status van toepassingen te delen tussen processen, worden API-aanvragen aanzienlijk efficiënter.

Deze bètaversie van Application Server is alleen beschikbaar voor implementaties op locatie met PHP 8.1 of 8.2. Implementaties op basis van cloud&#39;s worden niet ondersteund. B2B GraphQL-functionaliteit wordt nog niet ondersteund. GraphQL-aanvragen werken mogelijk niet zoals wordt verwacht in implementaties op locatie wanneer deze versie van de PHP-toepassingsserver is geconfigureerd.

## Wie kan de Server van de Toepassing gebruiken?

De Server van de toepassing is beschikbaar voor de plaatsingen van de Handel op-gebouw slechts.

## Toepassingsserver inschakelen voor GraphQL API&#39;s

De `ApplicationServer` module (`Magento/ApplicationServer/`) schakelt Application Server voor GraphQL API&#39;s in.

De lopende Server van de Toepassing vereist installatie van de Open uitbreiding van de Steekproef en een kleine verandering in het de configuratiedossier van Nginx van uw plaatsing om deze toepassingsserver plaatselijk in werking te stellen.

### Voordat u begint

Voltooi deze twee taken voordat u de `ApplicationServer` module:

* Nginx configureren

* De v22-extensie Open Swoole installeren en configureren

### Nginx configureren

Uw specifieke plaatsing van de Handel bepaalt hoe te om Nginx te vormen. In het algemeen wordt het Nginx-configuratiebestand standaard benoemd `nginx.conf` en wordt in een van deze directory&#39;s geplaatst: `/usr/local/nginx/conf`, `/etc/nginx`, of `/usr/local/etc/nginx`. Zie [Beginnerengids](http://nginx.org/en/docs/beginners_guide.html) voor meer informatie over het configureren van Nginx.

Voorbeeld-Nginxconfiguratie:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Open switch installeren en configureren

Als u de toepassingsserver lokaal wilt uitvoeren, installeert u de extensie Open SWOLE v22. Deze extensie kan op meerdere manieren worden geïnstalleerd.

## Toepassingsserver uitvoeren

Start de toepassingsserver:

```bash
bin/magento server:run
```

Deze opdracht start een HTTP-poort op 9501. Zodra de Server van de Toepassing lanceert, wordt haven 9501 een volmachtsserver van HTTP voor alle vragen van GraphQL.

## Voorbeeld: Open SWOX (OSX) installeren

Deze procedure laat zien hoe u de Open Swoole extensie installeert op PHP 8.2 voor OSX-systemen. Het is een van de verschillende manieren om de extensie Open Swoole te installeren.

U kunt zowel de Open Swoole uitbreiding voor PHP (v22) als de Composer pakketten installeren die deze uitbreiding met één bevel vereist.

### Open-wisselaar installeren

Enter:

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
```

Tijdens de installatie geeft Adobe Commerce aanwijzingen weer om ondersteuning voor `openssl`, `mysqlnd`, `sockets`, `http2`, en `postgres`. Enter `yes` voor alle opties behalve `postgres`.

### Installatie van open kolom bevestigen

Uitvoeren `php -m | grep openswoole` om te bevestigen dat de extensie is ingeschakeld.

### Algemene fouten met de installatie van Open Swoole

Eventuele fouten die optreden tijdens de installatie van OpenSwool treden doorgaans op tijdens de `pecl` installatiefase. Tot de standaardfouten behoren ontbrekende `openssl.h` en `pcre2.h` bestanden. U lost deze fouten op door ervoor te zorgen dat deze twee pakketten op uw lokale systeem zijn geïnstalleerd.

* Locatie controleren van `openssl` door uitvoering:

```bash
openssl version -d
```

Met deze opdracht wordt het pad getoond waar `openssl` is geïnstalleerd.

* Locatie controleren van `pcre2` door uitvoering:

```bash
pcre2-config --prefix 
```

Gebruik Homebrew om de ontbrekende pakketten te installeren als de opdrachtuitvoer aangeeft dat bestanden ontbreken:

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### Problemen met openssl oplossen

Om problemen op te lossen met betrekking tot `openssl`, run:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Bevestig dat u het pad vanaf uw lokale computer gebruikt `dev` milieu.

#### Bevestigen van oplossing voor openssl-gerelateerde kwesties

U kunt de volgende opdracht opnieuw uitvoeren om te controleren of aan opensels gerelateerde problemen zijn opgelost:

```bash
pecl install openswoole-22.0.0
```

#### Problemen met pcre2.h oplossen

Om problemen op te lossen met betrekking tot `pcre2.h`, de `pcre2.h` pad naar de geïnstalleerde map voor PHP-extensies. Uw specifieke geïnstalleerde versie van PHP en `pcr2.h` bepaalt de specifieke versie van het bevel dat u zou moeten gebruiken.
