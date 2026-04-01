---
title: Apache installeren voor implementaties op locatie
description: Leer Apache installeren en configureren voor Adobe Commerce-implementaties op locatie. Vereiste modules inschakelen, herschrijven en &grave;.htaccess&grave;-instellingen.
feature: Install, Configuration
badgePaas: label="In de bedrijfsruimten" type="Informative" url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce-projecten ter plaatse."
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# Apache installeren voor implementaties op locatie {#apache}

Deze handleiding begeleidt u bij het installeren van Apache voor Adobe Commerce-implementaties op locatie en bij het configureren van de Apache-instellingen die Commerce nodig heeft. Dit omvat gedeelde Apache-vereisten en specifieke procedures voor het besturingssysteem voor Ubuntu en CentOS. Adobe raadt u aan de configuratie-instructies in deze handleiding op te volgen om zowel de functionaliteit als de beveiliging van de Commerce-toepassing te behouden.

Adobe steunt de versies Apache die in de [&#x200B; systeemvereisten &#x200B;](../../system-requirements.md) voor uw versie van Adobe Commerce worden vermeld. Ondersteunde versies verschillen per release. Voor Apache is ook een ondersteunde PHP-configuratie vereist. Voor verwante PHP vereisten, zie [&#x200B; PHP montages &#x200B;](../php-settings.md).

Begin met de sectie die uw milieu aanpast:

- Als Apache reeds geïnstalleerd is, begin met [&#x200B; de vereisten van Apache van het Overzicht &#x200B;](#review-apache-requirements).
- Als u Apache op Ubuntu moet installeren of bevorderen, ga [&#x200B; installeren of bevorderen Apache op Ubuntu &#x200B;](#installing-or-upgrading-apache-on-ubuntu).
- Als u Apache op CentOS moet installeren, ga [&#x200B; installeren Apache op CentOS &#x200B;](#installing-apache-on-centos).

## Apache-vereisten bekijken

Voltooi deze vereisten op elke Apache-server waarop Adobe Commerce wordt gehost.

### Verplichte instructies configureren

Stel `AllowEncodedSlashes` in de serverconfiguratie (globaal) of in de virtuele hostconfiguraties in om te voorkomen dat de gecodeerde schuine strepen worden gedecodeerd die problemen voor URL&#39;s kunnen veroorzaken. Wanneer u bijvoorbeeld via de API producten met een schuine streep ophaalt in de SKU, wilt u niet dat de schuine streep wordt omgezet. Het volgende voorbeeldblok is niet volledig en andere richtlijnen zijn vereist.

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### Herschrijvingen en .htaccess configureren {#apache-rewrites-and-htaccess}

Gebruik deze sectie om Apache toe te laten herschrijft en vormt het [&#x200B; verdeelde `.htaccess` dossier &#x200B;](https://httpd.apache.org/docs/current/howto/htaccess.html). Adobe Commerce gebruikt herschrijvingen op de server en `.htaccess` voor instructies op directoryniveau voor Apache.

>[!IMPORTANT]
>
>Als u deze instellingen niet inschakelt, worden er gewoonlijk geen stijlen weergegeven op uw winkel of in Admin. Hierdoor kan ook worden voorkomen dat Apache de in `.htaccess` gedefinieerde Adobe Commerce-beveiligingsinstellingen toepast.

1. Schakel de module voor het herschrijven van Apache in:

   ```bash
   a2enmod rewrite
   ```

1. Laat de toepassing toe om het verdeelde `.htaccess` configuratiedossier te gebruiken.

   1. Bewerk `/etc/apache2/sites-available/000-default.conf` in Ubuntu. Voor andere lay-outs Apache of als de extra parameters worden vereist, zie de [&#x200B; documentatie van Apache &#x200B;](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) en de [&#x200B; documentatie van de de toegangscontrole van Apache &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

   1. Voeg de aanwijzing `AllowOverride` toe of werk deze bij voor de map waarin u Adobe Commerce wilt installeren.

   Als u bijvoorbeeld Adobe Commerce in de standaard `docroot` installeert, voegt u het volgende blok toe aan `000-default.conf` :

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Als u een upgrade uitvoert vanaf een eerdere Apache-versie, zoekt u eerst naar een bestaand `<Directory "/var/www/html">` - of `<Directory "/var/www">` -blok in `000-default.conf` . Als u Adobe Commerce in een andere `docroot` installeert, werkt u het overeenkomende `<Directory>` -blok voor dat pad bij.

1. Start Apache opnieuw om uw wijzigingen toe te passen:

   ```bash
   service apache2 restart
   ```

### Vereiste modules installeren

Adobe Commerce vereist de installatie van de volgende Apache-modules:

- [&#x200B; mod_deflate.c &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [&#x200B; mod_expired.c &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [&#x200B; mod_headers.c &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [&#x200B; mod_rewrite.c &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [&#x200B; mod_security.c &#x200B;](https://modsecurity.org)
- [&#x200B; mod_ssl.c &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Controleren of Apache is geïnstalleerd

Voer de volgende gegevens in om te controleren of Apache is geïnstalleerd en de huidige versie te bekijken:

```bash
apache2 -v
```

Het resultaat geeft ongeveer de volgende informatie weer:

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- Als Apache *niet* geïnstalleerd is, zie:
   - [Apache installeren of upgraden op Ubuntu](#installing-or-upgrading-apache-on-ubuntu)
   - [Apache installeren op CentOS](#installing-apache-on-centos)

## Apache installeren of upgraden op Ubuntu {#installing-or-upgrading-apache-on-ubuntu}

Apache installeren en configureren op Ubuntu is een proces in drie stappen:

1. De software installeren.
1. Herschrijven inschakelen.
1. Geef `.htaccess` instructies op.

Wanneer u Apache-serverherschrijvingen configureert, moet u het type instructies opgeven dat in `.htaccess` kan worden gebruikt. De toepassing gebruikt deze om herschrijfregels en beveiliging op te geven.

### Apache installeren op Ubuntu

1. Installeer Apache als u dat nog niet hebt gedaan:

   ```bash
   apt-get -y install apache2
   ```

1. Controleer de installatie:

   ```bash
   apache2 -v
   ```

   Berichten die lijken op de volgende weergave om te bevestigen dat de installatie is gelukt:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Ga verder met de volgende sectie.

   >[!NOTE]
   >
   >Zelfs als Apache door gebrek met Ubuntu wordt verstrekt, zie de volgende sectie om het te vormen.

### Upgrade van Apache op Ubuntu

Als Apache al is geïnstalleerd en u een eerdere versie dan `2.4` gebruikt, voert u een upgrade uit naar Apache `2.4` of naar de meest recente versie die wordt ondersteund door de Adobe Commerce-versie die u hebt geïmplementeerd. Zie [&#x200B; systeemvereisten &#x200B;](../../system-requirements.md).

1. Pakketgegevens bijwerken:

   ```bash
   apt-get -y update
   ```

1. Voeg desgewenst een opslagplaats toe die een ondersteunde Apache-versie voor uw omgeving biedt.

1. Apache installeren of upgraden:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Als de opdracht `apt-get install` mislukt als gevolg van onvervulde afhankelijkheden, raadpleegt u de documentatie bij het besturingssysteem of de ondersteuningsbronnen voor de distributie.

1. Controleer de installatie:

   ```bash
   apache2 -v
   ```

1. Bevestig dat de geïnstalleerde versie de versie aanpast die voor uw versie van Adobe Commerce in [&#x200B; systeemvereisten &#x200B;](../../system-requirements.md) wordt gesteund.

1. Laat [&#x200B; toe herschrijft en `.htaccess` voor Ubuntu &#x200B;](#enable-rewrites-and-htaccess-for-ubuntu).

### Herschrijven en .htaccess voor Ubuntu inschakelen

1. Open het `/etc/apache2/sites-available/000-default.conf` -bestand voor bewerking:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Zoek het blok dat begint met:

   ```conf
   <Directory "/var/www/html">
   ```

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

>[!IMPORTANT]
>
>Als u deze instellingen niet inschakelt, worden er gewoonlijk geen stijlen weergegeven op uw winkel of in Admin. Hierdoor kan ook worden voorkomen dat Apache de in `.htaccess` gedefinieerde Adobe Commerce-beveiligingsinstellingen toepast.

## Apache installeren op CentOS {#installing-apache-on-centos}

Apache installeren en configureren op CentOS bestaat uit drie stappen:

1. De software installeren
2. Herschrijven inschakelen
3. Geef `.htaccess` instructies op.

Wanneer u Apache-serverherschrijvingen configureert, moet u het type instructies opgeven dat in `.htaccess` kan worden gebruikt. De toepassing gebruikt deze om herschrijfregels en beveiliging op te geven.

### Apache installeren

1. Installeer Apache als u dat nog niet hebt gedaan.

   ```bash
   yum -y install httpd
   ```

1. Controleer de installatie:

   ```bash
   httpd -v
   ```

   Berichten die lijken op de volgende weergave om te bevestigen dat de installatie is gelukt:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Ga verder met de volgende sectie.

   >[!NOTE]
   >
   >Zelfs als Apache door gebrek met CentOS wordt verstrekt, zie de volgende sectie om het te vormen.

### Herschrijven en .htaccess inschakelen voor CentOS

1. Open het `/etc/httpd/conf/httpd.conf` -bestand voor bewerking:

   ```bash
   vim /etc/httpd/conf/httpd.conf
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
   >De voorafgaande waarden voor `Order` werken mogelijk niet in alle gevallen. Voor meer informatie, zie de [&#x200B; documentatie Apache &#x200B;](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order).

1. Sla het bestand op en sluit de teksteditor af.

1. Start Apache opnieuw om de Apache-instellingen toe te passen.

   ```bash
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>Als u deze instellingen niet inschakelt, worden er gewoonlijk geen stijlen weergegeven op uw winkel of in Admin. Hierdoor kan ook worden voorkomen dat Apache de in `.htaccess` gedefinieerde Adobe Commerce-beveiligingsinstellingen toepast.

## 403 (Verboden) fouten oplossen

Als u 403 Verboden fouten tegenkomt bij het openen van de site, kunt u uw Apache-configuratie of uw virtuele hostconfiguratie bijwerken om bezoekers in te schakelen voor de site:

### 403 Verboden fouten voor Apache oplossen

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
