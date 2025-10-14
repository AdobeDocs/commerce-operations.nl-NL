---
title: Apache
description: Voer de volgende stappen uit om de Apache-webserver voor installaties op locatie van Adobe Commerce te installeren en te configureren.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: f8c5d714a4e96d0508f745d1b7617696c8cc94a7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerce ondersteunt Apache 2.4.x.

## Vereiste richtlijnen Apache

1. Stel `AllowEncodedSlashes` in de serverconfiguratie (globaal) of in de virtuele hostconfiguraties in om te voorkomen dat de gecodeerde schuine strepen worden gedecodeerd die problemen kunnen veroorzaken voor URL&#39;s. Wanneer u bijvoorbeeld via de API producten met een schuine streep ophaalt in de SKU, wilt u dat die niet converteren. Het voorbeeldblok is niet compleet en andere richtlijnen zijn vereist.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache herschrijft en opent

Dit onderwerp bespreekt hoe te om Apache 2.4 toe te laten herschrijft en specificeert het plaatsen voor het [&#x200B; verdeelde configuratiedossier, `.htaccess` &#x200B;](https://github.com/magento/magento2/blob/2.4-develop/.htaccess.sample).

Adobe Commerce gebruikt herschrijvingen op de server en `.htaccess` voor instructies op directoryniveau voor Apache. De volgende instructies zijn ook inbegrepen in alle andere secties in dit onderwerp.

Gebruik deze sectie om Apache 2.4 toe te laten herschrijft en specificeert het plaatsen voor het [&#x200B; verdeelde configuratiedossier, `.htaccess` &#x200B;](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce gebruikt herschrijvingen op de server en `.htaccess` voor instructies op directoryniveau voor Apache.

>[!NOTE]
>
>Als u deze instellingen niet inschakelt, worden er gewoonlijk geen stijlen weergegeven op uw winkel of in Admin.

1. Schakel de module voor het herschrijven van Apache in:

   ```bash
   a2enmod rewrite
   ```

1. Om de toepassing toe te laten om het verdeelde `.htaccess` configuratiedossier te gebruiken, zie de richtlijnen in [&#x200B; Apache 2.4 documentatie &#x200B;](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >In Apache 2.4 is het standaardsiteconfiguratiebestand van de server `/etc/apache2/sites-available/000-default.conf` .

   U kunt bijvoorbeeld het volgende toevoegen aan het einde van `000-default.conf` :

   ```
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Soms zijn aanvullende parameters vereist. Voor meer informatie, zie [&#x200B; Apache 2.4 documentatie &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Als u Apache-instellingen hebt gewijzigd, start u Apache opnieuw:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Als u een upgrade uitvoert vanaf een eerdere Apache-versie, zoekt u eerst naar `<Directory "/var/www/html">` of `<Directory "/var/www">` in `000-default.conf` .
   >- U moet de waarde van `AllowOverride` wijzigen in de instructie voor de map waarin u de Adobe Commerce-software wilt installeren. Als u bijvoorbeeld wilt installeren in de webserverhoofdmap, bewerkt u de instructie in `<Directory /var/www>` .

>[!NOTE]
>
>Als u deze instellingen niet inschakelt, worden stijlen meestal niet weergegeven in de winkel of in Admin.

## Vereiste modules voor Apache

Adobe Commerce vereist de installatie van de volgende Apache-modules:

- [&#x200B; mod_deflate.c &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [&#x200B; mod_expired.c &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [&#x200B; mod_headers.c &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [&#x200B; mod_rewrite.c &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [&#x200B; mod_security.c &#x200B;](https://modsecurity.org)
- [&#x200B; mod_ssl.c &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## De Apache-versie verifiëren

Voer de volgende gegevens in om te controleren welke Apache-versie u momenteel gebruikt:

```bash
apache2 -v
```

Het resultaat lijkt op het volgende:

```
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Als Apache *niet* geïnstalleerd is, zie:
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

   ```
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Schakel [&#x200B; herschrijft en `.htaccess`](#apache-rewrites-and-htaccess) in.

### Apache bijwerken op Ubuntu

Ga als volgt te werk om bij te werken naar Apache 2.4:

1. Voeg de `ppa:ondrej` -opslagplaats toe, die Apache 2.4 heeft:

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
   >Als &quot;apt-get installeert&quot;bevel wegens onontmoet gebiedsdelen ontbreekt, raadpleeg een middel zoals [&#x200B; https://askubuntu.com/ &#x200B;](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Controleer de installatie.

   ```bash
   apache2 -v
   ```

   Berichten die op het volgende lijken, moeten worden weergegeven:

   ```
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Schakel [&#x200B; herschrijft en `.htaccess`](#apache-rewrites-and-htaccess) in.

## Apache installeren op CentOS

Adobe Commerce vereist herschrijven van Apache-server. U moet ook het type instructies opgeven dat in `.htaccess` kan worden gebruikt. De toepassing gebruikt deze om herschrijfregels op te geven.

Het installeren en configureren van Apache is in feite een proces in drie stappen: de software installeren, herschrijven inschakelen en `.htaccess` instructies opgeven.

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

   ```
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Ga verder met de volgende sectie.

   >[!NOTE]
   >
   >Zelfs als Apache 2.4 standaard wordt voorzien van CentOS, zie de volgende sectie om het te vormen.

### Herschrijven en .htaccess inschakelen voor CentOS

1. Open `/etc/httpd/conf/httpd.conf` -bestand voor bewerking:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Zoek het blok dat begint met:

   ```conf
   <Directory "/var/www/html">
   ```

1. Wijzig de waarde van `AllowOverride` in `All` .

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
   >De voorafgaande waarden voor `Order` werken mogelijk niet in alle gevallen. Voor meer informatie, zie de documentatie Apache ([&#x200B; 2.4 &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Sla het bestand op en sluit de teksteditor af.

1. Start Apache opnieuw om Apache-instellingen toe te passen.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Als u deze instellingen niet inschakelt, worden er gewoonlijk geen stijlen weergegeven op uw winkel of in Admin.

### Herschrijven en .htaccess voor Ubuntu inschakelen

1. Open `/etc/apache2/sites-available/default` -bestand voor bewerking:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Zoek het blok dat begint met:

   `<Directory "/var/www/html">`

1. Wijzig de waarde van `AllowOverride` in `All` .

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

1. Configureer Apache voor gebruik van de module `mod_rewrite` :

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

Om websitebezoekers toe te laten om tot uw plaats toegang te hebben, gebruik één van [&#x200B; vereisen richtlijnen &#x200B;](https://httpd.apache.org/docs/2.4/howto/access.html).

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
>De voorafgaande waarden voor `Order` werken mogelijk niet in alle gevallen. Voor meer informatie, zie de [&#x200B; documentatie Apache &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
