---
title: Nginx installeren voor implementaties op locatie
description: Leer hoe u de Nginx-webserver installeert en configureert voor Adobe Commerce-implementaties op locatie. Stel PHP-FPM en uw virtuele host in.
feature: Install, Configuration
badgePaas: label="In de bedrijfsruimten" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Alleen van toepassing op Adobe Commerce-projecten ter plaatse."
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# Nginx installeren voor implementaties op locatie {#nginx}

Deze gids begeleidt u door het installeren van Nginx voor Adobe Commerce op-gebouw plaatsingen en het vormen van de montages van Nginx die Commerce vereist. Het bevat besturingssysteemspecifieke procedures voor Ubuntu en CentOS, samen met richtlijnen voor het configureren van PHP-FPM. Adobe raadt u aan de configuratie-instructies in deze handleiding op te volgen om zowel de functionaliteit als de beveiliging van de Commerce-toepassing te behouden.

Adobe steunt de versies van Nginx die in de [ systeemvereisten ](../../system-requirements.md) voor uw versie van Adobe Commerce worden vermeld. Ondersteunde versies verschillen per release. Nginx vereist ook een ondersteunde PHP-FPM configuratie. Voor verwante PHP vereisten, zie [ PHP ](../php-settings.md).

## Installeren op Ubuntu

Gebruik deze sectie om Adobe Commerce op Ubuntu met Nginx, PHP en MySQL te installeren.

### Nginx installeren

```bash
sudo apt -y install nginx
```

U kunt ook [ Nginx van bron ](https://www.armanism.com/blog/install-nginx-on-ubuntu) bouwen.

Nadat u de volgende secties voltooit en de toepassing installeert, gebruik het dossier van de steekproefconfiguratie om [ te vormen Nginx ](#configure-nginx). Bij deze aanbevolen configuratie blijven zowel de functionaliteit als de beveiliging van de Commerce-toepassing behouden.

### PHP-FPM installeren en configureren

Adobe Commerce vereist verscheidene [ PHP uitbreidingen ](../php-settings.md) om behoorlijk te functioneren. Naast deze extensies moet u ook de extensie `php-fpm` installeren en configureren als u Nginx gebruikt.

U installeert en configureert `php-fpm` als volgt:

1. Installeer de pakketten `php-fpm` en `php-cli` voor de PHP-versie die door de Adobe Commerce-versie wordt ondersteund. Bij Ubuntu volgen de pakketnamen doorgaans het volgende patroon:

   ```bash
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >Vervang `<php-version>` met gesteunde PHP minder belangrijke die versie in [ systeemvereisten ](../../system-requirements.md) voor de versie van Adobe Commerce wordt vermeld u installeert. Gebruik in de volgende stappen dezelfde waarde in de bestandspaden, de servicenaam en het socketpad.

1. Open de `php.ini` bestanden in een editor:

   ```bash
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```bash
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. Bewerk beide bestanden om deze af te stemmen op de volgende regels:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe raadt u aan de geheugenlimiet in te stellen op 2 GB wanneer u Adobe Commerce test. Verwijs naar [ Vereiste PHP montages ](../php-settings.md) voor meer informatie.

1. Sla de editor op en sluit deze af.

1. Start de service `php-fpm` opnieuw:

   ```bash
   systemctl restart php<php-version>-fpm
   ```

### MySQL installeren en configureren

Verwijs naar [ MySQL ](../database/mysql.md) voor meer informatie.

### Adobe Commerce installeren

U kunt Adobe Commerce op verschillende manieren downloaden:

* [De Composer-metapakket ophalen](../../composer.md)

* [ Kloon de git bewaarplaats ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

In dit voorbeeld ziet u een op composers gebaseerde installatie die de opdrachtregel gebruikt.

1. Als [ eigenaar van het dossiersysteem ](../file-system/overview.md), login aan uw toepassingsserver.

1. Wijzig de hoofdmap van de webserver of een map die u hebt geconfigureerd als een virtueel hoofddocument van de host. In dit voorbeeld gebruiken we de standaardinstelling Ubuntu `/var/www/html` .

   ```bash
   cd /var/www/html
   ```

1. Composer wereldwijd installeren. Composer moet afhankelijkheden bijwerken voordat Adobe Commerce kan worden geïnstalleerd:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Maak een Composer-project met het Adobe Commerce-metapakket.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Wanneer ertoe aangezet, ga uw [ authentificatietoetsen ](../authentication-keys.md) in. Uw _openbare sleutel_ is uw gebruikersbenaming; uw _privé sleutel_ is uw wachtwoord.

1. Stel lees- en schrijfmachtigingen in voor de webservergroep voordat u de toepassing installeert. Dit is nodig, zodat de opdrachtregel bestanden naar het bestandssysteem kan schrijven.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installeer van de [ bevellijn ](../../advanced.md). In dit voorbeeld wordt ervan uitgegaan dat de installatiemap `magento2ee` heet en dat de databasehost zich op dezelfde computer bevindt (`localhost`):

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >Gebruik de `--search-engine` -waarde en overeenkomende host-/poortopties die zijn vereist voor de Adobe Commerce-release die u installeert. Voor versies ouder dan 2.4.6 gebruikt u `elasticsearch7` met de `--elasticsearch-*` -opties voor Elasticsearch 7 of OpenSearch. Voor versie 2.4.6 en later, gebruik de waarde van de onderzoeksmotor en de overeenkomstige CLI opties die door die versie worden gesteund.

1. Overschakelen naar de modus Ontwikkelaar:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Nginx configureren

Adobe raadt u aan om Nginx te configureren met behulp van het `nginx.conf.sample` -configuratiebestand in de installatiemap en uw Nginx Virtual Host-configuratie, zodat zowel de functionaliteit als de beveiliging van de Commerce-toepassing behouden blijven.

>[!IMPORTANT]
>
>Het `nginx.conf.sample` dossier verstrekt vereiste toepassing verpletterend evenals veiligheid-verhardende regels. Het beperkt bijvoorbeeld de uitvoering van schadelijke scripts die naar de server worden geüpload. Als u dit dossier niet gebruikt of zijn regels wijzigt, bent u verantwoordelijk voor het uitvoeren van gelijkwaardige veiligheidscontroles in uw configuratie van douanenx.

In deze instructies wordt ervan uitgegaan dat u de standaardlocatie Ubuntu voor de virtuele Nginx-host gebruikt, zoals `/etc/nginx/sites-available` , en de standaarddocroot Ubuntu, zoals `/var/www/html` . U kunt deze locaties aanpassen aan uw omgeving.

1. Maak een nieuwe virtuele host voor uw site:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Voeg de volgende configuratie toe:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >De instructie `include` moet verwijzen naar het voorbeeldconfiguratiebestand voor nginx in de installatiemap.

1. Vervang `www.magento-dev.com` door uw domeinnaam. Dit moet overeenkomen met de basis-URL die u hebt opgegeven bij de installatie van Adobe Commerce.

1. Sla de editor op en sluit deze af.

1. Activeer de nieuwe virtuele host door er een symlink naar te maken in de map `/etc/nginx/sites-enabled` :

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Controleer of de syntaxis correct is:

   ```bash
   nginx -t
   ```

1. Nginx opnieuw starten:

   ```bash
   systemctl restart nginx
   ```

### De installatie controleren

Als u de installatie wilt controleren, opent u een webbrowser en navigeert u naar de basis-URL van uw site. Voor meer informatie, zie [ de installatie ](../../next-steps/verify.md) verifiëren.

## Installeren op CentOS 7

Gebruik deze sectie om Adobe Commerce te installeren op CentOS 7 met Nginx, PHP en MySQL.

### Nginx installeren

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

Start nginx nadat de installatie is voltooid en configureer deze om te starten op het moment van opstarten:

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

Nadat u de volgende secties voltooit en de toepassing installeert, gebruik een dossier van de steekproefconfiguratie om Nginx te vormen.

### PHP-FPM installeren en configureren

Adobe Commerce vereist verscheidene [ PHP ](../php-settings.md) uitbreidingen om behoorlijk te functioneren. Naast deze extensies moet u ook de extensie `php-fpm` installeren en configureren als u Nginx gebruikt.

1. Installeren `php-fpm`:

   ```bash
   yum -y install <php-fpm-package>
   ```

1. Open het `/etc/php.ini` -bestand in een editor.

   >[!NOTE]
   >
   >Installeer het pakket met `php-fpm` de PHP-versie die wordt ondersteund door de Adobe Commerce-versie die u installeert. Pakketnamen variëren per opslagplaats en besturingssysteem. Zie [ systeemvereisten ](../../system-requirements.md).

1. Verwijder de commentaarmarkering van de regel `cgi.fix_pathinfo` en wijzig de waarde in `0` .

1. Bewerk het bestand zodat dit overeenkomt met de volgende regels:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe raadt u aan de geheugenlimiet in te stellen op 2 GB wanneer u Adobe Commerce test. Verwijs naar [ Vereiste PHP montages ](../php-settings.md) voor meer informatie.

1. Verwijder de commentaarmarkering van de map met het sessiepad en stel het pad in:

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Sla de editor op en sluit deze af.

1. Open `/etc/php-fpm.d/www.conf` in een editor.

1. Bewerk het bestand zodat dit overeenkomt met de volgende regels:

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Verwijder de commentaarmarkering van de omgevingsregels:

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Sla de editor op en sluit deze af.

1. Maak een map voor het PHP-sessiepad en wijzig de eigenaar in `nginx` user and group:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R nginx:nginx /var/lib/php/
   ```

1. Maak een directory voor de PHP-FPM socket en verander de eigenaar in de `nginx` user and group:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R nginx:nginx /run/php-fpm/
   ```

1. Start de `php-fpm` -service en configureer deze zo dat deze op het moment van opstarten start:

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Controleer of de service `php-fpm` wordt uitgevoerd:

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### MySQL installeren en configureren

Verwijs naar [ MySQL ](../database/mysql.md) voor meer informatie.

### Adobe Commerce installeren

U kunt Adobe Commerce op verschillende manieren downloaden:

* [De Composer-metapakket ophalen](../../composer.md)

* [ Kloon de git bewaarplaats ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

In dit voorbeeld ziet u een op composers gebaseerde installatie die de opdrachtregel gebruikt.

1. Als [ eigenaar van het dossiersysteem ](../file-system/overview.md), login aan uw toepassingsserver.

1. Wijzig de hoofdmap van de webserver of een map die u hebt geconfigureerd als een virtueel hoofddocument van de host. In dit voorbeeld gebruikt u de CentOS-standaardinstelling `/usr/share/nginx/html` .

   ```bash
   cd /usr/share/nginx/html
   ```

1. Composer wereldwijd installeren. Composer moet afhankelijkheden bijwerken voordat Adobe Commerce kan worden geïnstalleerd:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Maak een Composer-project met het Adobe Commerce-metapakket.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Wanneer ertoe aangezet, ga uw [ authentificatietoetsen ](../authentication-keys.md) in. Uw _openbare sleutel_ is uw gebruikersbenaming; uw _privé sleutel_ is uw wachtwoord.

1. Stel lees- en schrijfmachtigingen in voor de webservergroep voordat u de toepassing installeert. Dit is nodig, zodat de opdrachtregel bestanden naar het bestandssysteem kan schrijven.

   ```bash
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :nginx . # CentOS
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installeer van de [ bevellijn ](../../advanced.md). In dit voorbeeld wordt ervan uitgegaan dat de installatiemap `magento2ee` heet en dat de databasehost zich op dezelfde computer bevindt (`localhost`):

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Overschakelen naar de modus Ontwikkelaar:

   ```bash
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Nginx configureren

We raden u aan om Nginx te configureren met behulp van het `nginx.conf.sample` -bestand in de installatiemap en uw Nginx virtuele hostconfiguratie.

>[!IMPORTANT]
>
>Het `nginx.conf.sample` dossier verstrekt vereiste toepassing verpletterend evenals veiligheid-verhardende regels. Het beperkt bijvoorbeeld de uitvoering van schadelijke scripts die naar de server worden geüpload. Als u dit dossier niet gebruikt of zijn regels wijzigt, bent u verantwoordelijk voor het uitvoeren van gelijkwaardige veiligheidscontroles in uw configuratie van douanenx.

In deze instructies wordt ervan uitgegaan dat u de standaardlocatie van CentOS voor de virtuele Nginx-host gebruikt, zoals `/etc/nginx/conf.d` , en de standaarddocroot, zoals `/usr/share/nginx/html` . U kunt deze locaties aanpassen aan uw omgeving.

1. Maak een nieuwe virtuele host voor uw site:

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. Voeg de volgende configuratie toe:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >De instructie `include` moet verwijzen naar het voorbeeldconfiguratiebestand voor nginx in de installatiemap.

1. Vervang `www.magento-dev.com` door uw domeinnaam.

1. Sla de editor op en sluit deze af.

1. Controleer of de syntaxis correct is:

   ```bash
   nginx -t
   ```

1. Nginx opnieuw starten:

   ```bash
   systemctl restart nginx
   ```

### SELinux en firewalld configureren

SELinux is standaard ingeschakeld in CentOS 7. Gebruik de volgende opdracht om te bevestigen dat deze wordt uitgevoerd:

```bash
sestatus
```

Om SELinux en firewalld te vormen:

1. SELinux-beheertools installeren:

   ```bash
   yum -y install policycoreutils-python
   ```

1. Voer de volgende opdrachten uit om de beveiligingscontext voor de installatiemap te wijzigen:

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. Installeer het firewalld-pakket:

   ```bash
   yum -y install firewalld
   ```

1. Start de firewallservice en configureer deze zo dat deze op het moment van opstarten start:

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. Voer de volgende opdrachten uit om poorten voor HTTP en HTTPS te openen, zodat u de basis-URL vanuit een webbrowser kunt openen:

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### De installatie controleren

Als u de installatie wilt controleren, opent u een webbrowser en navigeert u naar de basis-URL van uw site. Voor meer informatie, zie [ de installatie ](../../next-steps/verify.md) verifiëren.
