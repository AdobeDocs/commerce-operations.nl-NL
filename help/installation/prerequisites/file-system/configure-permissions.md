---
title: Eigendom en machtigingen van bestanden configureren
description: Voer de volgende stappen uit om bestandssysteemmachtigingen te configureren voor installaties op locatie van Adobe Commerce.
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# Eigendom en machtigingen van bestanden configureren

Dit onderwerp bespreekt hoe te om lees-schrijf toestemmingen voor de groep van de Webserver te plaatsen alvorens u Adobe Commerce installeert. Dit is nodig, zodat de opdrachtregel bestanden naar het bestandssysteem kan schrijven.

De procedure u gebruikt is verschillend, afhankelijk van of u [ gedeelde het ontvangen ](#set-permissions-for-one-user-on-shared-hosting) gebruikt en één gebruiker hebt of als u a [ privé server ](#set-ownership-and-permissions-for-two-users) gebruikt en twee gebruikers hebt.

## Machtigingen instellen voor één gebruiker bij gedeelde hosting

In deze sectie wordt beschreven hoe u machtigingen voor de installatie instelt als u zich aanmeldt bij de toepassingsserver als dezelfde gebruiker die ook de webserver uitvoert. Dit type installatie komt veel voor in gedeelde hostomgevingen.

U kunt als volgt machtigingen instellen voordat u de toepassing installeert:

1. Meld u aan bij uw toepassingsserver.
1. Gebruik een toepassing voor bestandsbeheer die wordt geleverd door uw gedeelde hostingprovider om te controleren of schrijfmachtigingen zijn ingesteld voor de volgende mappen:

   * `vendor` (Composer of gecomprimeerde archiefinstallatie)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * Andere statische bronnen

1. Als u bevel-lijn toegang hebt, ga de volgende bevelen in de getoonde orde in:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   Als u desgewenst alle opdrachten op één regel wilt invoeren, voert u het volgende in, ervan uitgaande dat de toepassing is geïnstalleerd in `/var/www/html/magento2` :

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Als u dit nog niet hebt gedaan, kunt u de toepassing op een van de volgende manieren ophalen:

   * [Composer-pakket](../../composer.md)
   * [ Kloon de bewaarplaats (bijdragende ontwikkelaars slechts) ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Nadat u de eigendom en de toestemmingen van het dossiersysteem hebt geplaatst, [ installeert de toepassing ](../../advanced.md)

>[!NOTE]
>
>Om toestemmingen na het installeren van de toepassing verder te beperken, kunt u [ een masker ](../../next-steps/set-umask.md) vormen.

## Eigendom en machtigingen voor twee gebruikers instellen

In deze sectie wordt besproken hoe u het eigendom en de machtigingen voor uw eigen server of een persoonlijke hostinginstelling kunt instellen. In dit type van opstelling, kunt u typisch *niet* login als, of schakelaar aan, de gebruiker van de Webserver. Meestal meldt u zich aan als één gebruiker en voert u de webserver uit als een andere gebruiker.

U stelt als volgt de eigendom en machtigingen in voor een systeem met twee gebruikers:

Voltooi de volgende taken in de getoonde orde:

* [Informatie over de gedeelde groep](#about-the-shared-group)
* [De eigenaar van het bestandssysteem maken en de gebruiker een sterk wachtwoord geven](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [De gebruikersgroep van de webserver zoeken](#find-the-web-server-user-group)
* [De eigenaar van het bestandssysteem in de webservergroep plaatsen](#put-the-file-system-owner-in-the-web-server-group)
* [De software ophalen](#get-the-software)
* [Eigendom en machtigingen voor de gedeelde groep instellen](#set-ownership-and-permissions-for-the-shared-group)

### Informatie over de gedeelde groep

Om de Webserver toe te laten om dossiers en folders in het dossiersysteem te schrijven maar ook *eigendom* door de eigenaar van het dossiersysteem te handhaven, moeten beide gebruikers in de zelfde groep zijn. Dit is nodig, zodat beide gebruikers toegang kunnen delen tot bestanden (inclusief bestanden die zijn gemaakt met de beheerfunctie of andere hulpprogramma&#39;s op het web).

In deze sectie wordt besproken hoe u een eigenaar van een bestandssysteem kunt maken en deze gebruiker in de groep van de webserver kunt plaatsen. U kunt desgewenst een bestaande gebruikersaccount gebruiken. Om veiligheidsredenen raden we de gebruiker aan een sterk wachtwoord in te voeren.

>[!NOTE]
>
>Skip aan [ vind de de gebruikersgroep van de Webserver ](#find-the-web-server-user-group) als u op het gebruiken van een bestaande gebruikersrekening van plan bent.

### De eigenaar van het bestandssysteem maken en de gebruiker een sterk wachtwoord geven

In deze sectie wordt besproken hoe u de eigenaar van het bestandssysteem kunt maken. (de eigenaar van het dossiersysteem is een andere termijn voor *bevel-lijn gebruiker*.)

Als u een gebruiker wilt maken op CentOS of Ubuntu, voert u de volgende opdracht in als een gebruiker met `root` -rechten:

```bash
adduser <username>
```

Als u de gebruiker een wachtwoord wilt geven, voert u de volgende opdracht in als een gebruiker met `root` -rechten:

```bash
passwd <username>
```

Volg de aanwijzingen op het scherm om een wachtwoord voor de gebruiker te maken.

>[!WARNING]
>
>Als u geen `root` bevoegdheden hebt op uw toepassingsserver, kunt u een andere lokale gebruikersaccount gebruiken. Zorg ervoor dat de gebruiker een sterk wachtwoord heeft en met [ verdergaat zet de eigenaar van het dossiersysteem in de groep van de Webserver ](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Als u bijvoorbeeld een gebruiker met de naam `magento_user` wilt maken en de gebruiker een wachtwoord wilt geven, voert u het volgende in:

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Omdat het punt om deze gebruiker te creëren extra veiligheid moet verstrekken, zorg ervoor u a [ sterk wachtwoord ](https://en.wikipedia.org/wiki/Password_strength) creeert.

### De gebruikersgroep van de webserver zoeken

De gebruikersgroep van de webserver zoeken:

* CentOS:

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  of

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

Doorgaans zijn de naam van de gebruiker en de groep beide `apache` .

* Ubuntu: `ps aux | grep apache` om de Apache-gebruiker te zoeken en `groups <apache user>` om de groep te zoeken.

Doorgaans zijn de gebruikersnaam en de groepsnaam allebei `www-data` .

### De eigenaar van het bestandssysteem in de webservergroep plaatsen

Als u de eigenaar van het bestandssysteem in de primaire groep van de webserver wilt plaatsen (uitgaande van de typische Apache-groepsnaam voor CentOS en Ubuntu), voert u de volgende opdracht in als een gebruiker met `root` -bevoegdheden:

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>De `-a -G` opties zijn belangrijk omdat zij `apache` of `www-data` als a *secundaire* groep aan de gebruikersrekening toevoegen, die de 5&rbrace; primaire *groep van de gebruiker &lbrace;bewaart.* Het toevoegen van een secundaire groep aan een hulp van de gebruikersrekening [ beperkt dossiereigendom en toestemmingen ](#set-ownership-and-permissions-for-two-users) om leden van een gedeelde groep slechts toegang tot bepaalde dossiers te verzekeren.

Als u bijvoorbeeld de gebruiker `magento_user` wilt toevoegen aan de `apache` primaire groep op CentOS:

```bash
sudo usermod -a -G apache magento_user
```

Om te bevestigen dat uw gebruiker lid van de groep van de Webserver is, ga het volgende bevel in:

```bash
groups magento_user
```

Het volgende steekproefresultaat toont de primaire (`magento`) en secundaire (`apache`) groepen van de gebruiker.

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>Meestal zijn de gebruikersnaam en de primaire groepsnaam hetzelfde.

Start de webserver opnieuw om de taak te voltooien:

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### De software ophalen

Als u dit nog niet hebt gedaan, kunt u de software op een van de volgende manieren ophalen:

* [Composer-pakket](../../composer.md)
* [ Kloon de bewaarplaats (bijdragende ontwikkelaars slechts) ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Eigendom en machtigingen voor de gedeelde groep instellen

U stelt de eigendom en machtigingen in voordat u de toepassing installeert:

1. Meld u aan bij uw toepassingsserver als eigenaar van het bestandssysteem of schakel over naar de eigenaar van het bestandssysteem.
1. Voer de volgende opdrachten in de getoonde volgorde in:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

Als u desgewenst alle opdrachten op één regel wilt invoeren, voert u het volgende in, ervan uitgaande dat de toepassing is geïnstalleerd in `/var/www/html/magento2` en dat de naam van de webservergroep `apache` is:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Als de systeemmachtigingen voor het gebeurtenisbestand onjuist zijn ingesteld en niet kunnen worden gewijzigd door de eigenaar van het bestandssysteem, kunt u de opdracht invoeren als een gebruiker met `root` -bevoegdheden:

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## Overschakelen naar de eigenaar van het bestandssysteem

Nadat u de andere taken in dit onderwerp hebt uitgevoerd, ga één van de volgende bevelen in om aan die gebruiker te schakelen:

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

Bijvoorbeeld:

```bash
su magento_user
```
