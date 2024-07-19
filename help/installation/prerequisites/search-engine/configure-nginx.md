---
title: Nginx voor uw zoekmachine configureren
description: Voer de volgende stappen uit om een zoekmachine te configureren met de Nginx-webserver voor installaties in de bedrijfsruimten van Adobe Commerce.
feature: Install, Search
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# Nginx voor uw zoekmachine configureren

{{$include /help/_includes/web-server-communication.md}}

## Een proxy instellen

>[!NOTE]
>
>Ondersteuning voor OpenSearch is toegevoegd in 2.4.4. OpenSearch is een compatibele Elasticsearch. Zie [ Elasticsearch migreren aan OpenSearch ](../../../upgrade/prepare/opensearch-migration.md) voor meer informatie.

Deze sectie bespreekt hoe te om nginx als *onveilige* volmacht te vormen zodat Adobe Commerce een onderzoeksmotor kan gebruiken die op deze server loopt. Deze sectie bespreekt vestigingHTTP Basis geen authentificatie; dat in [ Veilige mededeling met nginx ](#secure-communication-with-nginx) wordt besproken.

>[!NOTE]
>
>De reden dat de proxy in dit voorbeeld niet is beveiligd, is dat het makkelijker is om een proxy in te stellen en te verifiëren. U kunt TLS desgewenst gebruiken met deze proxy. Hiervoor moet u de proxygegevens toevoegen aan de configuratie van het beveiligde serverblok.

### Geef aanvullende configuratiebestanden op in uw algemene configuratie

Zorg ervoor dat uw globale `/etc/nginx/nginx.conf` de volgende regel bevat, zodat de andere configuratiebestanden die in de volgende secties worden besproken, worden geladen:

```conf
include /etc/nginx/conf.d/*.conf;
```

### Index instellen als proxy

In deze sectie wordt besproken hoe u kunt opgeven wie toegang heeft tot de nginx-server.

1. Gebruik een teksteditor om een bestand `/etc/nginx/conf.d/magento_es_auth.conf` met de volgende inhoud te maken:

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Nginx opnieuw starten:

   ```bash
   service nginx restart
   ```

1. Verifieer de volmachtswerken door het volgende bevel in te gaan:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Als uw proxy bijvoorbeeld poort 8080 gebruikt:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Berichten die op de volgende vertoning lijken om op succes te wijzen:

   ```
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Beveiligde communicatie met nginx

Deze sectie bespreekt hoe te opstelling [ de Basisauthentificatie van HTTP ](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) met uw veilige volmacht. Als u TLS en HTTP Basic-verificatie gebruikt, kan niemand communicatie met Elasticsearch of OpenSearch of met uw toepassingsserver onderscheppen.

Omdat nginx nationaal authentificatie steunt van HTTP Basis, adviseren wij het over, bijvoorbeeld, [ de authentificatie van de Samenvatting ](https://www.nginx.com/resources/wiki/modules/auth_digest/), die niet in productie wordt geadviseerd.

Aanvullende bronnen:

* [ hoe te Authentificatie van het Wachtwoord van de opstelling met Nginx op Ubuntu 14.04 (Digitale Oceaan) ](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [ BasisHTTP Authentificatie met Nginx (HowtoForge) ](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [ de Configuraties van Nginx van het Voorbeeld voor Elasticsearch ](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Zie de volgende secties voor meer informatie:

* [Wachtwoorden maken](#create-a-password)
* [Toegang tot nginx instellen](#set-up-access-to-nginx)
* [Een beperkte context instellen voor het zoekprogramma](#set-up-a-restricted-context-for-the-search-engine)
* [Controleren of communicatie veilig is](#secure-communication-with-nginx)

### Een wachtwoord maken

We raden u aan de opdracht Apache `htpasswd` te gebruiken om wachtwoorden te coderen voor een gebruiker met toegang tot Elasticsearch of OpenSearch (genoemd `magento_elasticsearch` in dit voorbeeld).

Een wachtwoord maken:

1. Voer de volgende opdracht in om te bepalen of `htpasswd` al is geïnstalleerd:

   ```bash
   which htpasswd
   ```

   Als een pad wordt weergegeven, wordt dit geïnstalleerd. Als de opdracht geen uitvoer retourneert, wordt `htpasswd` niet geïnstalleerd.

1. Indien nodig installeert u `htpasswd` :

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. Maak een map `/etc/nginx/passwd` waarin wachtwoorden worden opgeslagen:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Om veiligheidsredenen moet `<filename>` verborgen zijn, dat wil zeggen dat het moet beginnen met een punt.

1. *(Optioneel).* Als u nog een gebruiker aan het wachtwoordbestand wilt toevoegen, voert u dezelfde opdracht in zonder de optie `-c` (Maken):

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Controleer of de inhoud van `/etc/nginx/passwd` correct is.

### Toegang tot nginx instellen

In deze sectie wordt besproken hoe u kunt opgeven wie toegang heeft tot de nginx-server.

>[!WARNING]
>
>Het getoonde voorbeeld is voor een *onveilige* volmacht. Als u een veilige proxy wilt gebruiken, voegt u de volgende inhoud (behalve de listen-poort) toe aan uw beveiligde serverblok.

Gebruik een teksteditor om `/etc/nginx/conf.d/magento_es_auth.conf` (onbeveiligd) of het beveiligde serverblok met de volgende inhoud te wijzigen:

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>De luisterpoort van de zoekmachine die in het voorgaande voorbeeld wordt weergegeven, is alleen voorbeelden. Om veiligheidsredenen raden we u aan een niet-standaard listen poort te gebruiken.

### Een beperkte context instellen voor het zoekprogramma

In deze sectie wordt besproken hoe u kunt opgeven wie toegang heeft tot de zoekmachineserver.

1. Ga het volgende bevel in om een folder tot stand te brengen om de authentificatieconfiguratie op te slaan:

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Gebruik een teksteditor om een bestand `/etc/nginx/auth/magento_elasticsearch.conf` met de volgende inhoud te maken:

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. Als u een veilige proxy instelt, verwijdert u `/etc/nginx/conf.d/magento_es_auth.conf` .
1. Start de engine opnieuw en ga verder met de volgende sectie:

   ```bash
   service nginx restart
   ```

#### Verifiëren

{{$include /help/_includes/verify-secure-communication.md}}
