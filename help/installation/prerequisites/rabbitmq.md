---
title: Berichtenmakelaar (RabbitMQ)
description: Volg deze stappen om vereiste software van de berichtmakelaar (zoals  [!DNL RabbitMQ]) voor op-gebouw installaties van Adobe Commerce te installeren en te vormen.
exl-id: ae6200d6-540f-46b3-92ba-7df7f6bb6fae
source-git-commit: 73faaa2a3b9ce773e9a381d103735403966f568b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---

# Berichtenmakelaar (RabbitMQ)

Adobe Commerce gebruikt de open-source berichtbroker van [!DNL RabbitMQ] . Het biedt een betrouwbaar, hoogst beschikbaar, scalable, en draagbaar overseinensysteem aan.

De rijen van het bericht verstrekken een asynchroon communicatie mechanisme waarin de afzender en de ontvanger van een bericht niet elkaar contacteren. Noch moeten zij met de berichtrij tezelfdertijd communiceren. Wanneer een afzender een bericht in een rij plaatst, wordt het opgeslagen tot de ontvanger hen ontvangt.

Het systeem van de berichtrij moet worden gevestigd alvorens u Adobe Commerce installeert. De basisvolgorde is:

1. Installeer [!DNL RabbitMQ] en eventuele voorwaarden.
1. Verbind [!DNL RabbitMQ] met Adobe Commerce.

>[!NOTE]
>
>U kunt MySQL of [!DNL RabbitMQ] gebruiken voor de verwerking van de berichtwachtrij. Voor details bij vestiging het systeem van de berichtrij, zie [&#x200B; een rij van het Bericht overzicht &#x200B;](https://developer.adobe.com/commerce/php/development/components/message-queues/). Als u de Bulk-API met Adobe Commerce gebruikt, wordt de systeemconfiguratie van de wachtrij voor berichten standaard ingesteld op het gebruik van [!DNL RabbitMQ] als de berichtenbroker. Zie [&#x200B; de gebruikers van de het berichtrij van het Begin &#x200B;](../../configuration/cli/start-message-queues.md) voor meer informatie.

## [!DNL RabbitMQ] installeren op Ubuntu

Als u [!DNL RabbitMQ] op Ubuntu 16 wilt installeren, voert u de volgende opdracht in:

```bash
sudo apt install -y rabbitmq-server
```

Deze opdracht installeert ook de vereiste Erlang-pakketten.

Als u een oudere versie van Ubuntu hebt, raadt [!DNL RabbitMQ] u aan het pakket vanaf hun website te installeren.

1. Download het .deb pakket van [&#x200B; rabbitmq-server &#x200B;](https://www.rabbitmq.com/download.html).
1. Installeer het pakket met `dpkg` .

Verwijs naar [&#x200B; het Installeren op Debian/Ubuntu &#x200B;](https://www.rabbitmq.com/install-debian.html) voor meer informatie.

## [!DNL RabbitMQ] installeren op CentOS

### Installeren Erlang

[!DNL RabbitMQ] is geschreven met de programmeertaal Erlang, die op hetzelfde systeem moet worden geïnstalleerd als [!DNL RabbitMQ] .

Zie [&#x200B; Handmatige installatie &#x200B;](https://www.erlang-solutions.com/downloads/) voor meer informatie.

Raadpleeg de [[!DNL RabbitMQ] /Erlang-versiematrix &#x200B;](https://www.rabbitmq.com/which-erlang.html) om de juiste versie te installeren.

### Installeren [!DNL RabbitMQ]

De [!DNL RabbitMQ] -server wordt opgenomen in CentOS, maar de versie is vaak oud. [!DNL RabbitMQ] raadt u aan het pakket vanaf hun website te installeren.

Raadpleeg de installatiepagina van [!DNL RabbitMQ] voor de nieuwste ondersteunde versie. Adobe Commerce 2.3 en 2.4 ondersteunen [!DNL RabbitMQ] 3.8.x.

Verwijs naar [&#x200B; het Installeren op op RPM-Gebaseerde Linux &#x200B;](https://www.rabbitmq.com/install-rpm.html) voor meer informatie.

## Configureren [!DNL RabbitMQ]

Controleer de officiële [!DNL RabbitMQ] -documentatie om [!DNL RabbitMQ] te configureren en te beheren. Let op het volgende:

* Omgevingsvariabelen
* Poorttoegang
* Standaardgebruikersaccounts
* Starten en stoppen van de makelaar
* Systeemlimieten

## Installeren met [!DNL RabbitMQ] en verbinding maken

Als u Adobe Commerce _na_ installeert u [!DNL RabbitMQ] installeert, voeg de volgende bevel-lijn parameters tijdens installatie toe:

```bash
--amqp-host="<hostname>" --amqp-port="5672" --amqp-user="<user_name>" --amqp-password="<password>" --amqp-virtualhost="/"
```

Waarbij:

| Parameter | Beschrijving |
|--- |--- |
| `--amqp-host` | De hostnaam waar [!DNL RabbitMQ] is geïnstalleerd. |
| `--amqp-port` | De poort die moet worden gebruikt om verbinding te maken met [!DNL RabbitMQ] . De standaardwaarde is `5672` . |
| `--amqp-user` | De gebruikersnaam voor het verbinden met [!DNL RabbitMQ] . Gebruik de standaardgebruiker `guest` niet. |
| `--amqp-password` | Het wachtwoord voor het maken van verbinding met [!DNL RabbitMQ] . Gebruik het standaardwachtwoord niet `guest` . |
| `--amqp-virtualhost` | De virtuele host voor verbinding met [!DNL RabbitMQ]. De standaardwaarde is `/` . |
| `--amqp-ssl` | Geeft aan of verbinding moet worden gemaakt met [!DNL RabbitMQ] . De standaardwaarde is `false` . Als u de waarde aan waar plaatst, zie SSL voor meer informatie vormen. |

## Verbinden [!DNL RabbitMQ]

Als Adobe Commerce al op uw computer is geïnstalleerd en u wilt deze verbinden met [!DNL RabbitMQ] , voegt u een `queue` -sectie toe in het `<install_directory>/app/etc/env.php` -bestand, zodat deze sectie op de volgende manieren wordt weergegeven:

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

U kunt ook configuratiewaarden voor [!DNL RabbitMQ] instellen met de opdracht `bin/magento setup:config:set` :

```bash
bin/magento setup:config:set --amqp-host="rabbitmq.example.com" --amqp-port="11213" --amqp-user="magento" --amqp-password="magento" --amqp-virtualhost="/"
```

Nadat u de opdracht hebt uitgevoerd of het `<install_directory>/app/etc/env.php` -bestand met AMQP-configuratiewaarden hebt bijgewerkt, voert u `bin/magento setup:upgrade` uit om de wijzigingen toe te passen en de vereiste wachtrijen en uitwisselingen te maken in [!DNL RabbitMQ] .

## SSL configureren

Als u ondersteuning voor SSL wilt configureren, bewerkt u de parameters `ssl` en `ssl_options` in het `<install_directory>/app/etc/env.php` -bestand, zodat deze op het volgende lijken:

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

Nadat u Adobe Commerce en [!DNL RabbitMQ] hebt verbonden, moet u de gebruikers van de berichtrij beginnen. Zie [&#x200B; berichtrijen &#x200B;](../../configuration/cli/start-message-queues.md) voor details vormen.
