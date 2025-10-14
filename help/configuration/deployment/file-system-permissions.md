---
title: Toegangsrechten voor bestandssystemen
description: Zie hoe u de eigenaar of eigenaars van het Commerce-toepassingsbestandssysteem instelt voor een ontwikkelings- en productiesysteem.
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Toegangsrechten voor bestandssystemen

In deze sectie wordt besproken hoe u de eigenaar of eigenaars van het Commerce-bestandssysteem kunt instellen voor een ontwikkelings- en productiesysteem. Alvorens u verdergaat, herzie de concepten die in [&#x200B; Overzicht van de eigendom en de toestemmingen van het dossiersysteem &#x200B;](../../installation/prerequisites/file-system/overview.md) worden besproken.

Dit onderwerp is gericht op de ontwikkeling en productiesystemen van Commerce. Als u Commerce installeert, zie [&#x200B; Vastgestelde pre-installatiereigenschap en toestemmingen &#x200B;](../../installation/prerequisites/file-system/configure-permissions.md).

De volgende secties bespreken vereisten voor één of twee eigenaars van bestandssystemen. Dat betekent:

- **Één gebruiker** - typisch noodzakelijk op gedeelde ontvangende leveranciers, die u toestaan om tot slechts één gebruiker op de server toegang te hebben Deze gebruiker kan login, overdrachtdossiers gebruikend FTP, en deze gebruiker stelt ook de Webserver in werking.

- **twee gebruikers** - wij adviseren twee gebruikers als u uw eigen server van Commerce in werking stelt: één om dossiers over te brengen en bevel-lijn nut in werking te stellen, en een afzonderlijke gebruiker voor de software van de Webserver. Dit verdient de voorkeur wanneer dat mogelijk is, omdat het veiliger is.

  In plaats daarvan hebt u verschillende gebruikers:

   - De gebruiker van de Webserver, die Admin en opslag in werking stelt.

   - A _bevel-lijn gebruiker_, die een lokale gebruikersrekening is u aan login aan de server kunt gebruiken. Deze gebruiker voert Commerce-bouwtaken en opdrachtregelprogramma&#39;s uit.

## Eigendom van productiebestandssysteem voor gedeelde hosting (één gebruiker)

Als u de installatie van één eigenaar wilt gebruiken, moet u zich aanmelden bij uw Commerce-server als dezelfde gebruiker die de webserver uitvoert. Dit is standaard voor gedeelde hosting.

Omdat één eigenaar van het bestandssysteem minder veilig is, raden we u aan om Commerce in productie te implementeren op een privéserver in plaats van op gedeelde hosting, indien mogelijk.

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

Om componenten bij te werken, nieuwe componenten te installeren, of de software van Commerce te bevorderen, moeten alle voorafgaande folders read-write zijn.

#### Codebestanden en -mappen alleen-lezen maken

U verwijdert schrijfmachtigingen voor bestanden en mappen uit de gebruikersgroep van de webserver als volgt:

1. Meld u aan bij uw Commerce-server.

1. Ga naar de installatiemap van Commerce.

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

Bestanden en mappen schrijfbaar maken, zodat u onderdelen kunt bijwerken en de Commerce-software kunt upgraden:

1. Meld u aan bij uw Commerce-server.
1. Ga naar de installatiemap van Commerce.
1. Voer de volgende opdrachten in:

   ```bash
   chmod -R u+w .
   ```

### Optioneel instellen `magento_umask`

Zie [&#x200B; naar keuze plaatsen een masker &#x200B;](../../installation/next-steps/set-umask.md) in de _gids van de Installatie_.

## Eigendom van productiebestandssysteem voor privéhosting (twee gebruikers)

Als u uw eigen server gebruikt (inclusief de privéserverinstallatie van een hostprovider), zijn er twee gebruikers:

- De **gebruiker van de Webserver**, die Admin en storefront in werking stelt.

  Linux-systemen bieden doorgaans geen shell voor deze gebruiker. U kunt zich niet aanmelden bij de Commerce-server als of overschakelen naar de webservergebruiker.

- De **bevel-lijn gebruiker**, die u login aan uw server van Commerce als of schakelaar aan.

  Commerce gebruikt deze gebruiker om CLI-opdrachten en uitsnijden uit te voeren.

  >[!INFO]
  >
  >De bevel-lijn gebruiker wordt ook bedoeld als _eigenaar van het dossiersysteem_.

Omdat deze gebruikers toegang tot de zelfde dossiers vereisen, adviseren wij u tot a [&#x200B; gedeelde groep &#x200B;](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) tot welke zij allebei behoren. De volgende procedures gaan ervan uit dat u dit al hebt gedaan.

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

Plaats het [`setgid` &#x200B;](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) beetje op folders zodat erven de toestemmingen altijd van de ouderfolder.

>[!INFO]
>
>`setgid` is slechts op folders van toepassing, _niet_ op dossiers.

Daarnaast moeten de mappen kunnen worden geschreven door de groep met webservers. Omdat de inhoud in deze folders zou kunnen bestaan, voeg recursief de toestemmingen toe.

#### Machtigingen instellen en `setgid`

U kunt als volgt `setgid` en machtigingen voor de modus Ontwikkelaar instellen:

1. Meld u aan bij uw Commerce-server als eigenaar van het bestandssysteem of schakel over naar de eigenaar van het bestandssysteem.
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

1. Meld u aan bij uw Commerce-server.
1. Ga naar de installatiemap van Commerce.
1. Als eigenaar van het bestandssysteem voert u de volgende opdracht in om over te schakelen op de productiemodus:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Voer de volgende opdracht in als een gebruiker met `root` -rechten:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Codebestanden en mappen schrijfbaar maken

Bestanden en mappen schrijfbaar maken, zodat u onderdelen kunt bijwerken en de Commerce-software kunt upgraden:

1. Meld u aan bij uw Commerce-server.
1. Ga naar de installatiemap van Commerce.
1. Voer de volgende opdracht in:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
