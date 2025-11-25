---
title: Nginx
description: Voer de volgende stappen uit om de Nginx-webserver te installeren en te configureren voor installaties in het bedrijf van Adobe Commerce.
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 0%

---

# Nginx

Adobe Commerce steunt nginx 1.x (of de [&#x200B; recentste belangrijkste belangrijkste versie &#x200B;](https://nginx.org/en/linux_packages.html#mainline)). U moet ook de nieuwste versie van `php-fpm` installeren.

De installatie-instructies variëren afhankelijk van het besturingssysteem dat u gebruikt. Zie [&#x200B; PHP &#x200B;](../php-settings.md) voor informatie.

## Ubuntu

In de volgende sectie wordt beschreven hoe u Adobe Commerce 2.x op Ubuntu kunt installeren met nginx, PHP en MySQL.

### Nginx installeren

```bash
sudo apt -y install nginx
```

U kunt [&#x200B; ook bouwen nginx van bron &#x200B;](https://www.armanism.com/blog/install-nginx-on-ubuntu)

Na de voltooiing van de volgende secties en het installeren van de toepassing, zullen wij een dossier van de steekproefconfiguratie gebruiken om [&#x200B; te vormen nginx &#x200B;](#configure-nginx).

### Pfp-fpm installeren en configureren

Adobe Commerce vereist verscheidene [&#x200B; PHP uitbreidingen &#x200B;](../php-settings.md) om behoorlijk te functioneren. Naast deze extensies moet u ook de extensie `php-fpm` installeren en configureren als u nginx gebruikt.

U installeert en configureert `php-fpm` als volgt:

1. Installeren `php-fpm` en `php-cli` :

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >Deze opdracht installeert de nieuwste beschikbare versie van PHP 7.2.X. Zie [&#x200B; systeemvereisten &#x200B;](../../system-requirements.md) voor gesteunde PHP versies.

1. Open de `php.ini` bestanden in een editor:

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. Bewerk beide bestanden om deze af te stemmen op de volgende regels:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >We raden u aan de geheugenlimiet in te stellen op 2 G wanneer u Adobe Commerce test. Verwijs naar [&#x200B; Vereiste PHP montages &#x200B;](../php-settings.md) voor meer informatie.

1. Sla de editor op en sluit deze af.

1. Start de service `php-fpm` opnieuw:

   ```bash
   systemctl restart php7.2-fpm
   ```

### MySQL installeren en configureren

Verwijs naar [&#x200B; MySQL &#x200B;](../database/mysql.md) voor meer informatie.

### Installeren en configureren

U kunt Adobe Commerce op verschillende manieren downloaden, waaronder:

* [De Composer-metapakket ophalen](../../composer.md)

* [&#x200B; Kloon de git bewaarplaats &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

In dit voorbeeld ziet u een op composers gebaseerde installatie die de opdrachtregel gebruikt.

1. Als [&#x200B; eigenaar van het dossiersysteem &#x200B;](../file-system/overview.md), login aan uw toepassingsserver.

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

   Wanneer ertoe aangezet, ga uw [&#x200B; authentificatietoetsen &#x200B;](../authentication-keys.md) in. Uw _openbare sleutel_ is uw gebruikersbenaming; uw _privé sleutel_ is uw wachtwoord.

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

1. Installeer van de [&#x200B; bevellijn &#x200B;](../../advanced.md). In dit voorbeeld wordt ervan uitgegaan dat de installatiemap de naam `magento2ee` heeft, `db-host` zich op dezelfde computer bevindt (`localhost`) en `db-name` , `db-user` en `db-password` alle `magento` zijn:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. Overschakelen naar de modus Ontwikkelaar:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Nginx configureren

We raden u aan om nginx te configureren met behulp van het configuratiebestand van `nginx.conf.sample` dat beschikbaar is in de installatiemap en de virtuele nginx-host.

In deze instructies wordt ervan uitgegaan dat u de standaardlocatie Ubuntu voor de virtuele nginx-host (bijvoorbeeld `/etc/nginx/sites-available` ) en de standaarddocroot Ubuntu (bijvoorbeeld `/var/www/html` ) gebruikt, maar u kunt deze locaties aanpassen aan uw omgeving.

1. Maak een nieuwe virtuele host voor uw site:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Voeg de volgende configuratie toe:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
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

Open Webbrowser en navigeer aan basis URL van uw plaats om [&#x200B; de installatie &#x200B;](../../next-steps/verify.md) te verifiëren.

## CentOS 7

In de volgende sectie wordt beschreven hoe u Adobe Commerce 2.x op CentOS 7 kunt installeren met nginx, PHP en MySQL.

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

Na de voltooiing van de volgende secties en het installeren van de toepassing, zullen wij een dossier van de steekproefconfiguratie gebruiken om nginx te vormen.

### Pfp-fpm installeren en configureren

Adobe Commerce vereist verscheidene [&#x200B; PHP &#x200B;](../php-settings.md) uitbreidingen om behoorlijk te functioneren. Naast deze extensies moet u ook de extensie `php-fpm` installeren en configureren als u nginx gebruikt.

1. Installeren `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. Open het `/etc/php.ini` -bestand in een editor.

1. Verwijder de commentaarmarkering van de regel `cgi.fix_pathinfo` en wijzig de waarde in `0` .

1. Bewerk het bestand zodat dit overeenkomt met de volgende regels:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >We raden u aan de geheugenlimiet in te stellen op 2 G wanneer u Adobe Commerce test. Verwijs naar [&#x200B; Vereiste PHP montages &#x200B;](../php-settings.md) voor meer informatie.

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

1. Maak een map voor het PHP-sessiepad en wijzig de eigenaar in `apache` user and group:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. Maak een map voor het PHP-sessiepad en wijzig de eigenaar in `apache` user and group:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
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

Verwijs naar [&#x200B; MySQL &#x200B;](..//database/mysql.md) voor meer informatie.

### Installeren en configureren

U kunt de Adobe Commerce op verschillende manieren downloaden, waaronder:

* [De Composer-metapakket ophalen](../../composer.md)

* [&#x200B; Kloon de git bewaarplaats &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

In dit voorbeeld ziet u een op composers gebaseerde installatie die de opdrachtregel gebruikt.

1. Als [&#x200B; eigenaar van het dossiersysteem &#x200B;](../file-system/overview.md), login aan uw toepassingsserver.

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

   Wanneer ertoe aangezet, ga uw [&#x200B; authentificatietoetsen &#x200B;](../authentication-keys.md) in. Uw _openbare sleutel_ is uw gebruikersbenaming; uw _privé sleutel_ is uw wachtwoord.

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

1. Installeer van de [&#x200B; bevellijn &#x200B;](../../advanced.md). In dit voorbeeld wordt ervan uitgegaan dat de installatiemap de naam `magento2ee` heeft, `db-host` zich op dezelfde computer bevindt (`localhost`) en `db-name` , `db-user` en `db-password` alle `magento` zijn:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Overschakelen naar de modus Ontwikkelaar:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Nginx configureren

We raden u aan om nginx te configureren met behulp van het configuratiebestand van `nginx.conf.sample` dat beschikbaar is in de installatiemap en de virtuele nginx-host.

In deze instructies wordt ervan uitgegaan dat u de standaardlocatie van CentOS voor de virtuele nginx-host (bijvoorbeeld `/etc/nginx/conf.d` ) en de standaarddocroot (bijvoorbeeld `/usr/share/nginx/html` ) gebruikt, maar u kunt deze locaties aanpassen aan uw omgeving.

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

### SELinux en Firewalld configureren

SELinux is standaard ingeschakeld in CentOS 7. Gebruik het volgende bevel om te zien of loopt het:

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

Open Webbrowser en navigeer aan basis URL van uw plaats om [&#x200B; de installatie &#x200B;](../../next-steps/verify.md) te verifiëren.
