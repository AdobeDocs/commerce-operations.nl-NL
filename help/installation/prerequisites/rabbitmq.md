---
title: Berichtenmakelaar
description: Voer de volgende stappen uit om de vereiste berichtbrokersoftware (zoals [!DNL RabbitMQ]) voor installaties in Adobe Commerce.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# Berichtenmakelaar

Adobe Commerce gebruikt de [!DNL RabbitMQ] open-source berichtenmakelaar. Het biedt een betrouwbaar, hoogst beschikbaar, scalable, en draagbaar overseinensysteem aan.

De rijen van het bericht verstrekken een asynchroon communicatie mechanisme waarin de afzender en de ontvanger van een bericht niet elkaar contacteren. Noch moeten zij met de berichtrij tezelfdertijd communiceren. Wanneer een afzender een bericht in een rij plaatst, wordt het opgeslagen tot de ontvanger hen ontvangt.

Het systeem van de berichtrij moet worden gevestigd alvorens u Adobe Commerce of Magento Open Source installeert. De basisvolgorde is:

1. Installeren [!DNL RabbitMQ] en eventuele voorwaarden.
1. Verbinden [!DNL RabbitMQ] naar Adobe Commerce of Magento Open Source.

>[!NOTE]
>
>U kunt MySQL of [!DNL RabbitMQ] voor verwerking van wachtrij met berichten. Voor details bij vestiging het systeem van de berichtrij, zie [Overzicht van wachtrij met berichten](https://developer.adobe.com/commerce/php/development/components/message-queues/). Als u de Bulk API met Adobe Commerce gebruikt, wordt de systeemconfiguratie van de berichtrij standaard gebruikt [!DNL RabbitMQ] als de berichtenmakelaar. Zie [Gebruikers in de wachtrij met berichten starten](../../configuration/cli/start-message-queues.md) voor meer informatie .

## Installeren [!DNL RabbitMQ] over Ubuntu

Om te installeren [!DNL RabbitMQ] Voer op Ubuntu 16 de volgende opdracht in:

```bash
sudo apt install -y rabbitmq-server
```

Deze opdracht installeert ook de vereiste Erlang-pakketten.

Als u een oudere versie van Ubuntu hebt, [!DNL RabbitMQ] raadt u aan het pakket vanaf hun website te installeren.

1. Download het .deb-pakket van [rabbitmq-server](https://www.rabbitmq.com/download.html).
1. Het pakket installeren met `dpkg`.

Zie [Installeren op Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html) voor meer informatie .

## Installeren [!DNL RabbitMQ] op CentOS

### Installeren Erlang

[!DNL RabbitMQ] is geschreven met de programmeertaal Erlang, die op hetzelfde systeem moet worden geïnstalleerd als [!DNL RabbitMQ].

Zie [Handmatige installatie](https://www.erlang-solutions.com/downloads/) voor meer informatie .

Zie de [[!DNL RabbitMQ]/Erlang version matrix](https://www.rabbitmq.com/which-erlang.html) om de juiste versie te installeren.

### Installeren [!DNL RabbitMQ]

De [!DNL RabbitMQ] server is opgenomen in CentOS, maar de versie is vaak oud. [!DNL RabbitMQ] raadt u aan het pakket vanaf hun website te installeren.

Zie de [!DNL RabbitMQ] installeer pagina om de nieuwste ondersteunde versie op te halen. Adobe Commerce 2.3- en 2.4-ondersteuning [!DNL RabbitMQ] 3.8.x.

Zie [Installeren op Linux op basis van RPM](https://www.rabbitmq.com/install-rpm.html) voor meer informatie .

## Configureren [!DNL RabbitMQ]

De ambtenaar controleren [!DNL RabbitMQ] documentatie om te vormen en te beheren [!DNL RabbitMQ]. Let op het volgende:

* Omgevingsvariabelen
* Poorttoegang
* Standaardgebruikersaccounts
* Starten en stoppen van de makelaar
* Systeemlimieten

## Installeren met [!DNL RabbitMQ] en verbinden

Als u Adobe Commerce of Magento Open Source installeert _na_ u installeert [!DNL RabbitMQ]voegt u tijdens de installatie de volgende opdrachtregelparameters toe:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Waarbij:

| Parameter | Beschrijving |
|--- |--- |
| `--amqp-host` | De hostnaam waarbij [!DNL RabbitMQ] is geïnstalleerd. |
| `--amqp-port` | De poort waarmee verbinding moet worden gemaakt [!DNL RabbitMQ]. De standaardwaarde is `5672`. |
| `--amqp-user` | De gebruikersnaam waarmee verbinding wordt gemaakt [!DNL RabbitMQ]. De standaardgebruiker niet gebruiken `guest`. |
| `--amqp-password` | Het wachtwoord voor verbinding maken met [!DNL RabbitMQ]. Het standaardwachtwoord niet gebruiken `guest`. |
| `--amqp-virtualhost` | De virtuele host voor verbinding met [!DNL RabbitMQ]. De standaardwaarde is `/`. |
| `--amqp-ssl` | Geeft aan of verbinding moet worden gemaakt [!DNL RabbitMQ]. De standaardwaarde is `false`. Als u de waarde aan waar plaatst, zie SSL voor meer informatie vormen. |

## Verbinden [!DNL RabbitMQ]

Als Adobe Commerce of Magento Open Source al op uw computer is geïnstalleerd en u er verbinding mee wilt maken [!DNL RabbitMQ], voegt u een `queue` in de `<install_directory>/app/etc/env.php` bestand, zodat deze vergelijkbaar is met het volgende:

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

U kunt ook instellen [!DNL RabbitMQ] configuratiewaarden gebruiken `bin/magento setup:config:set` opdracht:

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Nadat u de opdracht hebt uitgevoerd of de opdracht hebt bijgewerkt `<install_directory>/app/etc/env.php` bestand met AMQP-configuratiewaarden, uitvoeren `bin/magento setup:upgrade` om de veranderingen toe te passen en de vereiste rijen en de uitwisselingen tot stand te brengen binnen [!DNL RabbitMQ].

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

Nadat u verbinding hebt gemaakt met Adobe Commerce en [!DNL RabbitMQ], moet u de berichtrij consumenten beginnen. Zie [Berichtenrijen configureren](../../configuration/cli/start-message-queues.md) voor meer informatie.
