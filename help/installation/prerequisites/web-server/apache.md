---
title: Apache
description: Voer de volgende stappen uit om de Apache-webserver voor installaties op locatie van Adobe Commerce te installeren en te configureren.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Apache

Adobe Commerce ondersteunt Apache 2.4.x.

## Vereiste richtlijnen Apache

1. Set `AllowEncodedSlashes` in de serverconfiguratie (globaal) of in de virtuele gastheerconfiguraties om het decoderen van de gecodeerde schuine strepen te vermijden die kwesties voor URLs kunnen veroorzaken. Wanneer u bijvoorbeeld via de API producten met een schuine streep ophaalt in de SKU, wilt u dat die niet converteren. Het voorbeeldblok is niet compleet en andere richtlijnen zijn vereist.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache herschrijft en opent

Dit onderwerp bespreekt hoe te om Apache 2.4 toe te laten herschrijft en het plaatsen voor te specificeren [gedistribueerd configuratiebestand, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe Commerce gebruikt herschrijvingen op de server en `.htaccess` instructies op directoryniveau voor Apache te geven. De volgende instructies zijn ook inbegrepen in alle andere secties in dit onderwerp.

Gebruik deze sectie om herschrijvingen van Apache 2.4 in te schakelen en een instelling voor de [gedistribueerd configuratiebestand, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce gebruikt herschrijvingen op de server en `.htaccess` instructies op directoryniveau voor Apache te geven.

>[!NOTE]
>
>Als u deze instellingen niet inschakelt, worden er gewoonlijk geen stijlen weergegeven op uw winkel of in Admin.

1. Schakel de module voor het herschrijven van Apache in:

   ```bash
   a2enmod rewrite
   ```

1. Om de toepassing toe te laten om verdeelde te gebruiken `.htaccess` configuratiebestand, zie de richtlijnen in het dialoogvenster [Documentatie Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >In Apache 2.4 is het standaard siteconfiguratiebestand van de server `/etc/apache2/sites-available/000-default.conf`.

   U kunt bijvoorbeeld het volgende toevoegen aan het einde van `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Soms zijn aanvullende parameters vereist. Zie de klasse [Documentatie Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Als u Apache-instellingen hebt gewijzigd, start u Apache opnieuw:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Als u een upgrade hebt uitgevoerd vanaf een eerdere Apache-versie, zoekt u eerst naar `<Directory "/var/www/html">` of `<Directory "/var/www">` in `000-default.conf`.
   >- U moet de waarde wijzigen van `AllowOverride` in de instructie voor de directory waarin u de Adobe Commerce- of Magento Open Source-software wilt installeren. Als u bijvoorbeeld wilt installeren in de webserverhoofdmap, bewerkt u de instructie in `<Directory /var/www>`.

>[!NOTE]
>
>Als u deze instellingen niet inschakelt, worden stijlen meestal niet weergegeven in de winkel of in Admin.

## Vereiste modules voor Apache

Adobe Commerce vereist de installatie van de volgende Apache-modules:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expired.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## De Apache-versie verifiëren

Voer de volgende gegevens in om te controleren welke Apache-versie u momenteel gebruikt:

```bash
apache2 -v
```

Het resultaat lijkt op het volgende:

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Als Apache *niet* geïnstalleerd, zie:
   - [Apache installeren of upgraden op Ubuntu](#installing-apache-on-ubuntu)
   - [Apache installeren op CentOS](#installing-apache-on-centos)

## Apache installeren of upgraden op Ubuntu

In de volgende secties wordt besproken hoe u Apache kunt installeren of upgraden:

- Apache installeren
- Upgrade naar Apache 2.4 op Ubuntu om PHP 7.4 te gebruiken.

### Apache installeren op Ubuntu

De standaardversie van Apache installeren:

1. Apache installeren

   ```bash
   apt-get -y install apache2
   ```

1. Controleer de installatie.

   ```bash
   apache2 -v
   ```

   Het resultaat lijkt op het volgende:

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Inschakelen [herschrijft en `.htaccess`](#apache-rewrites-and-htaccess).

### Apache bijwerken op Ubuntu

Ga als volgt te werk om bij te werken naar Apache 2.4:

1. Voeg de `ppa:ondrej` gegevensopslagruimte, met Apache 2.4:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. Installeer Apache 2.4:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Als de opdracht &#39;apt-get install&#39; mislukt als gevolg van niet-vervulde afhankelijkheden, raadpleegt u een bron zoals [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Controleer de installatie.

   ```bash
   apache2 -v
   ```

   Berichten die op het volgende lijken, moeten worden weergegeven:

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Inschakelen [herschrijft en `.htaccess`](#apache-rewrites-and-htaccess).

## Apache installeren op CentOS

Adobe Commerce vereist herschrijven van Apache-server. U moet ook het type instructies opgeven waarin u `.htaccess`, die de toepassing gebruikt om herschrijfregels op te geven.

Het installeren en configureren van Apache is in principe een proces in drie stappen: de software installeren, herschrijven inschakelen en opgeven `.htaccess` richtlijnen.

### Apache installeren

1. Installeer Apache 2.4 als u dat nog niet hebt gedaan.

   ```bash
   yum -y install httpd
   ```

1. Controleer de installatie:

   ```bash
   httpd -v
   ```

   Berichten die lijken op de volgende weergave om te bevestigen dat de installatie is gelukt:

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Ga verder met de volgende sectie.

   >[!NOTE]
   >
   >Zelfs als Apache 2.4 standaard wordt voorzien van CentOS, zie de volgende sectie om het te vormen.

### Herschrijven en .htaccess inschakelen voor CentOS

1. Openen `/etc/httpd/conf/httpd.conf` bestand voor bewerking:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Zoek het blok dat begint met:

   ```conf
   <Directory "/var/www/html">
   ```

1. De waarde wijzigen van `AllowOverride` tot `All`.

   Bijvoorbeeld:

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >De voorgaande waarden voor `Order` werkt mogelijk niet in alle gevallen. Raadpleeg de Apache-documentatie ([2,4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Sla het bestand op en sluit de teksteditor af.

1. Start Apache opnieuw om Apache-instellingen toe te passen.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Als u deze instellingen niet inschakelt, worden er gewoonlijk geen stijlen weergegeven op uw winkel of in Admin.

### Herschrijven en .htaccess voor Ubuntu inschakelen

1. Openen `/etc/apache2/sites-available/default` bestand voor bewerking:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Zoek het blok dat begint met:

   `<Directory "/var/www/html">`

1. De waarde wijzigen van `AllowOverride` tot `All`.

   Bijvoorbeeld:

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. Sla het bestand op en sluit de teksteditor af.

1. Apache configureren voor het gebruik van de `mod_rewrite` module:

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. Start Apache opnieuw om de wijzigingen toe te passen:

   ```bash
   service apache2 restart
   ```

## 403 (Verboden) fouten oplossen

Als u 403 Verboden fouten tegenkomt bij het openen van de site, kunt u uw Apache-configuratie of uw virtuele hostconfiguratie bijwerken om bezoekers in te schakelen voor de site:

### 403 Verboden fouten voor Apache 2.4 oplossen

Als u websitebezoekers toegang tot uw site wilt geven, gebruikt u een van de [Richtlijnen vereisen](https://httpd.apache.org/docs/2.4/howto/access.html).

Bijvoorbeeld:

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>De voorgaande waarden voor `Order` werkt mogelijk niet in alle gevallen. Zie de klasse [Apache-documentatie](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
