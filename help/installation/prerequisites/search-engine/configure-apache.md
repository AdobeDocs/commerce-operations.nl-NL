---
title: Apache configureren voor uw zoekmachine
description: Voer de volgende stappen uit om een zoekmachine te configureren met de Apache-webserver voor installaties in de bedrijfsruimten van Adobe Commerce en Magento Open Source.
feature: Install, Search
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Apache configureren voor uw zoekmachine

{{$include /help/_includes/web-server-communication.md}}

## Een proxy instellen

>[!NOTE]
>
>Ondersteuning voor OpenSearch is toegevoegd in 2.4.4. OpenSearch is een compatibele Elasticsearch. Zie [Elasticsearch migreren naar OpenSearch](../../../upgrade/prepare/opensearch-migration.md) voor meer informatie .

In deze sectie wordt besproken hoe u Apache als een *onveilig* zodat Adobe Commerce een zoekprogramma kan gebruiken dat op deze server wordt uitgevoerd. In deze sectie wordt het instellen van de HTTP Basic-verificatie niet besproken. Dit wordt besproken in [Beveiligde communicatie met Apache](#secure-communication-with-apache).

>[!NOTE]
>
>De reden dat de proxy in dit voorbeeld niet is beveiligd, is dat het makkelijker is om een proxy in te stellen en te verifiëren. U kunt TLS met deze proxy gebruiken. Als u dit wenst, zorg ervoor u de volmachtsinformatie aan uw veilige virtuele gastheerconfiguratie toevoegt.

### Een proxy instellen voor Apache 2.4

Deze sectie bespreekt hoe te om een volmacht te vormen gebruikend een virtuele gastheer.

1. Inschakelen `mod_proxy` als volgt:

   ```bash
   a2enmod proxy_http
   ```

1. Een teksteditor gebruiken om te openen `/etc/apache2/sites-available/000-default.conf`
1. Voeg de volgende instructie boven aan het bestand toe:

   ```conf
   Listen 8080
   ```

1. Voeg het volgende toe onder aan het bestand:

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. Apache opnieuw starten:

   ```bash
   service apache2 restart
   ```

1. Verifieer de volmachtswerken door het volgende bevel in te gaan:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Als u bijvoorbeeld Elasticsearch gebruikt en uw proxy poort 8080 gebruikt:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Berichten die op de volgende vertoning lijken om op succes te wijzen:

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Beveiligde communicatie met Apache

In deze sectie wordt besproken hoe u communicatie tussen Apache en de zoekmachine kunt beveiligen met [HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617) verificatie met Apache. Raadpleeg een van de volgende bronnen voor meer opties:

* [Zelfstudie over verificatie en autorisatie voor Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

Zie een van de volgende secties:

* [Een wachtwoordbestand maken](#create-a-password)
* [Uw veilige virtuele host configureren](#secure-communication-with-apache)

### Een wachtwoord maken

Uit veiligheidsoverwegingen kunt u het wachtwoordbestand overal vinden, behalve in de hoofdmap van de webserver. In dit voorbeeld wordt getoond hoe u het wachtwoordbestand opslaat in een nieuwe map.

#### Indien nodig htpassword installeren

Ga eerst na of je de Apache hebt `htpasswd` Het hulpprogramma wordt als volgt geïnstalleerd:

1. Voer de volgende opdracht in om te bepalen of `htpasswd` is al geïnstalleerd:

   ```bash
   which htpasswd
   ```

   Als een pad wordt weergegeven, wordt het geïnstalleerd; als de opdracht geen uitvoer retourneert, `htpasswd` is niet geïnstalleerd.

1. Indien nodig, installeren `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### Een wachtwoordbestand maken

Voer de volgende opdrachten in als een gebruiker met `root` rechten:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

Wanneer

* `<username>` kan:

   * Uitsnijden instellen: de gebruiker van de webserver of een andere gebruiker.

  In dit voorbeeld gebruiken wij de gebruiker van de Webserver, maar de keus van gebruiker is aan u.

   * Elasticsearch instellen: de gebruiker krijgt de naam `magento_elasticsearch` in dit voorbeeld

* `<password file name>` moet een verborgen bestand zijn (begint met `.`) en moet de naam van de gebruiker weerspiegelen. Zie de voorbeelden verderop in deze sectie voor meer informatie.

Volg de aanwijzingen op het scherm om een wachtwoord voor de gebruiker te maken.

#### Voorbeelden

**Voorbeeld 1: uitsnijden**
U moet verificatie instellen voor slechts één gebruiker voor uitsnijden; in dit voorbeeld gebruiken we de gebruiker van de webserver. Voer de volgende opdrachten in om een wachtwoordbestand voor de gebruiker van de webserver te maken:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**Voorbeeld 2: Elasticsearch**
U moet authentificatie voor twee gebruikers instellen: met toegang tot nginx en met toegang tot Elasticsearch. Voer de volgende opdrachten in om wachtwoordbestanden voor deze gebruikers te maken:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### Extra gebruikers toevoegen

Als u nog een gebruiker aan het wachtwoordbestand wilt toevoegen, voert u de volgende opdracht in als een gebruiker met `root` rechten:

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Beveiligde communicatie met Apache

In deze sectie wordt beschreven hoe u de installatie instelt [HTTP Basic-verificatie](https://httpd.apache.org/docs/2.2/howto/auth.html). Als u TLS en HTTP Basic-verificatie gebruikt, kan niemand communicatie met Elasticsearch of OpenSearch of met uw toepassingsserver onderscheppen.

In deze sectie wordt besproken hoe u kunt opgeven wie toegang heeft tot de Apache-server.

1. Gebruik een tekstverwerker om de volgende inhoud aan uw veilige virtuele host toe te voegen.

   * Apache 2.4: Bewerken `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. Als u het voorgaande hebt toegevoegd aan uw beveiligde virtuele host, verwijdert u `Listen 8080` en de `<VirtualHost *:8080>` aanwijzingen die u eerder hebt toegevoegd aan uw onveilige virtuele host.

1. Sla uw wijzigingen op, sluit de teksteditor af en start Apache opnieuw:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### Verifiëren

{{$include /help/_includes/verify-secure-communication.md}}
