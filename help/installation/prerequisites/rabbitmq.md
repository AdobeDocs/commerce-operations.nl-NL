---
title: Berichtenmakelaar
description: Voer de volgende stappen uit om de vereiste berichtbrokersoftware (zoals RabbitMQ) voor installaties in de bedrijfsruimten van Adobe Commerce en Magento Open Source te installeren en te configureren.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---


# Berichtenmakelaar

Adobe Commerce gebruikt de open-source berichtbroker RabbitMQ. Het biedt een betrouwbaar, hoogst beschikbaar, scalable, en draagbaar overseinensysteem aan.

De rijen van het bericht verstrekken een asynchroon communicatie mechanisme waarin de afzender en de ontvanger van een bericht niet elkaar contacteren. Noch moeten zij met de berichtrij tezelfdertijd communiceren. Wanneer een afzender een bericht in een rij plaatst, wordt het opgeslagen tot de ontvanger hen ontvangt.

Het systeem van de berichtrij moet worden gevestigd alvorens u Adobe Commerce of Magento Open Source installeert. De basisvolgorde is:

1. Installeer RabbitMQ en alle voorwaarden.
1. Sluit RabbitMQ aan op Adobe Commerce of Magento Open Source.

>[!NOTE]
>
>U kunt MySQL of RabbitMQ voor de verwerking van de berichtrij gebruiken. Voor details bij vestiging het systeem van de berichtrij, zie [Overzicht van wachtrij met berichten](https://developer.adobe.com/commerce/php/development/components/message-queues/). Als u het Bulk API met Adobe Commerce gebruikt, blijft de configuratie van het systeem van de berichtrij aan het gebruiken van RabbitMQ als berichtbroker in gebreke. Zie [Gebruikers in de wachtrij met berichten starten](../../configuration/cli/start-message-queues.md) voor meer informatie .

## RabbitMQ installeren op Ubuntu

Als u RabbitMQ op Ubuntu 16 wilt installeren, voert u de volgende opdracht in:

```bash
sudo apt install -y rabbitmq-server
```

Met deze opdracht installeert u ook de vereiste Erlang-pakketten.

Als u een oudere versie van Ubuntu hebt, raadt RabbitMQ u aan het pakket vanaf hun website te installeren.

1. Download het .deb-pakket van [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Het pakket installeren met `dpkg`.

Zie [Installeren op Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) voor meer informatie .

## RabbitMQ installeren op CentOS

### Installeren Erlang

RabbitMQ is geschreven met de programmeertaal Erlang, die op hetzelfde systeem moet worden geïnstalleerd als RabbitMQ.

Zie [Handmatige installatie](https://www.erlang-solutions.com/downloads/) voor meer informatie .

Zie de [RabbitMQ/Erlang-versiematrix](https://www.rabbitmq.com/which-erlang.html) om de juiste versie te installeren.

### RabbitMQ installeren

De RabbitMQ-server is opgenomen in CentOS, maar de versie is vaak oud. RabbitMQ raadt u aan het pakket vanaf hun website te installeren.

Raadpleeg de RabbitMQ-installatiepagina voor de nieuwste ondersteunde versie. Adobe Commerce en Magento Open Source 2.3 en 2.4 ondersteunen RabbitMQ 3.8.x.

Zie [Installeren op Linux op basis van RPM](https://www.rabbitmq.com/install-rpm.html) voor meer informatie .

## RabbitMQ configureren

Controleer de officiële documentatie van RabbitMQ om RabbitMQ te configureren en te beheren. Let op het volgende:

* Omgevingsvariabelen
* Poorttoegang
* Standaardgebruikersaccounts
* Starten en stoppen van de makelaar
* Systeemlimieten

## Installeren met RabbitMQ en verbinding maken

Als u Adobe Commerce of Magento Open Source installeert _na_ als u RabbitMQ installeert, voegt u tijdens de installatie de volgende opdrachtregelparameters toe:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Waar:

| Parameter | Beschrijving |
|--- |--- |
| `--amqp-host` | De hostnaam waar RabbitMQ is geïnstalleerd. |
| `--amqp-port` | De poort die moet worden gebruikt om verbinding te maken met RabbitMQ. De standaardwaarde is `5672`. |
| `--amqp-user` | De gebruikersnaam voor verbinding met RabbitMQ. De standaardgebruiker niet gebruiken `guest`. |
| `--amqp-password` | Het wachtwoord voor verbinding met RabbitMQ. Het standaardwachtwoord niet gebruiken `guest`. |
| `--amqp-virtualhost` | De virtuele host voor verbinding met RabbitMQ. De standaardwaarde is `/`. |
| `--amqp-ssl` | Geeft aan of verbinding moet worden gemaakt met RabbitMQ. De standaardwaarde is `false`. Als u de waarde aan waar plaatst, zie SSL voor meer informatie vormen. |

## Connect RabbitMQ

Als u Adobe Commerce of Magento Open Source al hebt geïnstalleerd en u wilt deze koppelen aan RabbitMQ, voegt u een `queue` in de `<install_directory>/app/etc/env.php` bestand, zodat deze vergelijkbaar is met het volgende:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/'
     ),
  ),
```

U kunt de configuratiewaarden van RabbitMQ ook instellen met de `bin/magento setup:config:set` opdracht:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Nadat u de opdracht hebt uitgevoerd of de opdracht hebt bijgewerkt `<install_directory>/app/etc/env.php` bestand met AMQP-configuratiewaarden, uitvoeren `bin/magento setup:upgrade` om de veranderingen toe te passen en de vereiste rijen en uitwisselingen in RabbitMQ tot stand te brengen.

## SSL configureren

Als u ondersteuning voor SSL wilt configureren, bewerkt u de `ssl` en `ssl_options` in de `<install_directory>/app/etc/env.php` bestand, zodat deze vergelijkbaar zijn met het volgende:

```php
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' =>  '/etc/pki/tls/certs/DigiCertCA.crt',
            'certfile' => '/path/to/magento/app/etc/ssl/test-rabbit.crt',
            'keyfile' => '/path/to/magento/app/etc/ssl/test-rabbit.key'
       ],
     ),
  ),
```

## Gebruikers in de wachtrij met berichten starten

Nadat u Adobe Commerce en RabbitMQ hebt verbonden, moet u de gebruikers van de berichtrij beginnen. Zie [Berichtenrijen configureren](../../configuration/cli/start-message-queues.md) voor meer informatie.
