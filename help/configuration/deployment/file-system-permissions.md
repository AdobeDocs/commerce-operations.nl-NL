---
title: Toegangsrechten voor bestandssystemen
description: Zie hoe u de eigenaar of eigenaars van het bestandssysteem voor de toepassing Commerce instelt voor een ontwikkelings- en productiesysteem.
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# Toegangsrechten voor bestandssystemen

In deze sectie wordt beschreven hoe u de eigenaar of eigenaars van het bestandssysteem Commerce voor een ontwikkelings- en productiesysteem instelt. Voordat u verdergaat, bekijkt u de in [Overzicht van eigendom en machtigingen van bestandssystemen](../../installation/prerequisites/file-system/overview.md).

Dit onderwerp richt zich op de ontwikkeling en de productiesystemen van de handel. Als u Handel installeert, zie [Eigendom en machtigingen vóór de installatie instellen](../../installation/prerequisites/file-system/configure-permissions.md).

De volgende secties bespreken vereisten voor één of twee eigenaars van bestandssystemen. Dat betekent:

- **Eén gebruiker**—Gewoonlijk is dit vereist voor gedeelde hostingproviders, waarmee u slechts toegang hebt tot één gebruiker op de server. Deze gebruiker kan zich aanmelden, bestanden overdragen via FTP en deze gebruiker kan ook de webserver uitvoeren.

- **Twee gebruikers**—Wij adviseren twee gebruikers als u uw eigen server van de Handel in werking stelt: één om dossiers over te brengen en bevel-lijn nut in werking te stellen, en een afzonderlijke gebruiker voor de software van de Webserver. Dit verdient de voorkeur wanneer dat mogelijk is, omdat het veiliger is.

  In plaats daarvan hebt u verschillende gebruikers:

   - De gebruiker van de Webserver, die Admin en opslag in werking stelt.

   - A _opdrachtregelgebruiker_ Dit is een lokale gebruikersaccount waarmee u zich kunt aanmelden bij de server. Deze gebruiker stelt de bouwbanen van de Handel en bevel-lijn nut in werking.

## Eigendom van productiebestandssysteem voor gedeelde hosting (één gebruiker)

Als u de installatie van één eigenaar wilt gebruiken, moet u zich aanmelden bij uw Commerce-server als dezelfde gebruiker die de webserver uitvoert. Dit is standaard voor gedeelde hosting.

Omdat het hebben van één eigenaar van het dossiersysteem minder veilig is, adviseren wij u om Handel in productie op een privé server in plaats van op gedeelde het ontvangen op te stellen, indien mogelijk.

### Eén eigenaar instellen voor de standaard- of ontwikkelmodus

In de standaard- of ontwikkelaarsmodus moet de gebruiker de volgende mappen schrijven:

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- Andere statische bronnen
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

U kunt deze machtigingen instellen via de opdrachtregel of via een toepassing voor bestandsbeheer die wordt geleverd door uw gedeelde hostingprovider.

### Eén eigenaar instellen voor de productiemodus

Als u klaar bent om uw site te implementeren voor productie, moet u voor betere beveiliging schrijftoegang verwijderen uit bestanden in de volgende directory&#39;s:

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Andere statische bronnen
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Om componenten bij te werken, nieuwe componenten te installeren, of de software van de Handel te bevorderen, moeten alle voorafgaande folders read-write zijn.

#### Codebestanden en -mappen alleen-lezen maken

U verwijdert schrijfmachtigingen voor bestanden en mappen uit de gebruikersgroep van de webserver als volgt:

1. Meld u aan bij uw commerciële server.

1. Verandering in uw de installatiemap van de Handel.

1. Overschakelen naar productiemodus.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Verwijder schrijfmachtigingen naar de volgende directory&#39;s.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Maak het bevel-lijn hulpmiddel uitvoerbaar.

   ```bash
   chmod u+x bin/magento
   ```

#### Codebestanden en mappen schrijfbaar maken

Bestanden en mappen schrijfbaar maken, zodat u componenten kunt bijwerken en de software voor de handel kunt upgraden:

1. Meld u aan bij uw commerciële server.
1. Verandering in uw de installatiemap van de Handel.
1. Voer de volgende opdrachten in:

   ```bash
   chmod -R u+w .
   ```

### Optioneel ingesteld `magento_umask`

Zie [Optioneel een masker instellen](../../installation/next-steps/set-umask.md) in de _Installatiehandleiding_.

## Eigendom van productiebestandssysteem voor privéhosting (twee gebruikers)

Als u uw eigen server gebruikt (inclusief de privéserverinstallatie van een hostprovider), zijn er twee gebruikers:

- De **webservergebruiker**, die de beheerfunctie en de storefront uitvoert.

  De systemen van Linux verstrekken typisch geen shell voor deze gebruiker; u kunt niet login aan de server van de Handel als, of schakelaar aan, de gebruiker van de Webserver.

- De **opdrachtregelgebruiker**, die u bij uw server van de Handel als of schakelaar aan login.

  De handel gebruikt deze gebruiker om CLI bevelen en kromme in werking te stellen.

  >[!INFO]
  >
  >De opdrachtregelgebruiker wordt ook wel de _eigenaar van bestandssysteem_.

Omdat deze gebruikers toegang tot de zelfde dossiers vereisen, adviseren wij u tot een [gedeelde groep](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) waartoe zij beide behoren. De volgende procedures gaan ervan uit dat u dit al hebt gedaan.

Zie een van de volgende secties:

- Twee eigenaars van bestandssystemen in de ontwikkelings- of standaardmodus
- Twee eigenaars van bestandssystemen in de productiemodus

### Twee eigenaars instellen voor de standaard- of ontwikkelmodus

Bestanden in de volgende mappen moeten door beide gebruikers in de ontwikkelaar- en de standaardmodus kunnen worden geschreven:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Stel de [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) bit op mappen, zodat machtigingen altijd overerven van de bovenliggende map.

>[!INFO]
>
>`setgid` alleen van toepassing is op directory&#39;s; _niet_ naar bestanden.

Daarnaast moeten de mappen kunnen worden geschreven door de groep met webservers. Omdat de inhoud in deze folders zou kunnen bestaan, voeg recursief de toestemmingen toe.

#### Machtigingen en `setgid`

In te stellen `setgid` en machtigingen voor de ontwikkelingsmodus:

1. Meld u aan bij de Commerce-server als of schakel over naar de eigenaar van het bestandssysteem.
1. Voer de volgende opdrachten in de getoonde volgorde in:

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### Twee eigenaars van bestandssystemen in de productiemodus

Als u klaar bent om uw site te implementeren voor productie, moet u voor betere beveiliging schrijftoegang verwijderen uit bestanden in de volgende directory&#39;s:

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- Andere statische bronnen
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### Codebestanden en -mappen alleen-lezen maken

U verwijdert schrijfbare machtigingen voor bestanden en mappen uit de gebruikersgroep van de webserver als volgt:

1. Meld u aan bij uw commerciële server.
1. Verandering in uw de installatiemap van de Handel.
1. Als eigenaar van het bestandssysteem voert u de volgende opdracht in om over te schakelen op de productiemodus:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Voer de volgende opdracht in als een gebruiker met `root` rechten:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Codebestanden en mappen schrijfbaar maken

Bestanden en mappen schrijfbaar maken, zodat u componenten kunt bijwerken en de software voor de handel kunt upgraden:

1. Meld u aan bij uw commerciële server.
1. Verandering in uw de installatiemap van de Handel.
1. Voer de volgende opdracht in:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
