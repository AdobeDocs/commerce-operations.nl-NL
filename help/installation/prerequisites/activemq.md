---
title: Berichtenmakelaar (ActiveMQ Artemis)
description: Voer de volgende stappen uit om Apache ActiveMQ Artemis berichtbroker voor installaties in de bedrijfsruimten van Adobe Commerce te installeren en te configureren.
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Berichtenmakelaar (ActiveMQ Artemis)

Adobe Commerce ondersteunt ook de open-source berichtbroker van ActiveMQ Artemis via het Simple Text Oriented Messaging Protocol (STOMP). Het levert een betrouwbaar en scalable overseinensysteem, dat flexibiliteit voor op STOMP-Gebaseerde integratie biedt.


>[!NOTE]
>
>ActiveMQ Artemis is geïntroduceerd in Adobe Commerce 2.4.5 en latere versies. Voor details bij het installeren van Artemis ActiveMQ in Adobe Commerce op de projecten van de wolkeninfrastructuur, zie &lbrace;de dienst ActiveMQ van de Opstelling [&#x200B; in &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/activemq) Commerce op de Gids van de Wolk *.*

De rijen van het bericht verstrekken een asynchroon communicatie mechanisme waarin de afzender en de ontvanger van een bericht niet elkaar contacteren. Noch moeten zij met de berichtrij tezelfdertijd communiceren. Wanneer een afzender een bericht in een rij plaatst, wordt het opgeslagen tot de ontvanger hen ontvangt.

Het systeem van de berichtrij moet worden gevestigd alvorens u Adobe Commerce installeert. De basisvolgorde is:

1. Installeer Apache ActiveMQ Artemis en alle voorwaarden.
1. ActiveMQ verbinden met Adobe Commerce.

>[!NOTE]
>
>U kunt MySQL, ActiveMQ of [!DNL RabbitMQ] gebruiken voor de verwerking van een wachtrij met berichten. Voor details bij vestiging het systeem van de berichtrij, zie [&#x200B; een rij van het Bericht overzicht &#x200B;](https://developer.adobe.com/commerce/php/development/components/message-queues/). Als u de Bulk-API met Adobe Commerce gebruikt, wordt de systeemconfiguratie van de wachtrij voor berichten standaard ingesteld op het gebruik van [!DNL RabbitMQ] als de berichtenbroker. Zie [&#x200B; de gebruikers van de het berichtrij van het Begin &#x200B;](../../configuration/cli/start-message-queues.md) voor meer informatie.

>[!TIP]
>
>Controleer altijd de [&#x200B; Apache ActiveMQ Artemis downloadpagina &#x200B;](https://activemq.apache.org/components/artemis/download/) voor de recentste stabiele versie vóór installatie. In de voorbeelden in dit document wordt versie 2.42.0 gebruikt. Dit was de meest recente stabiele release in september 2025.


## Apache ActiveMQ Artemis installeren

U kunt ActiveMQ-artemis installeren met Docker (aanbevolen voor ontwikkeling) of met de hand (aanbevolen voor productie).

### Optie 1: Docker-installatie (aanbevolen voor ontwikkeling)

#### Vereisten

Controleer of Docker op uw systeem is geïnstalleerd en wordt uitgevoerd.

>[!TIP]
>
>Voor meer informatie over het officiële beeld van het Docker van ActiveMQ Artemis, zie de [&#x200B; Apache ActiveMQ Artemis de pagina van de Hub van de Doopper van Docker Artemis &#x200B;](https://hub.docker.com/r/apache/activemq-artemis).

#### Installatiestappen

1. Voer ActiveMQ-artemis uit met de officiële Docker-afbeelding:

   ```bash
   # Run with default configuration
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     apache/activemq-artemis:2.42.0
   ```

1. Uitvoeren met aangepaste referenties:

   ```bash
   # Run with custom username/password
   docker run --detach \
     --name artemis \
     --publish 8161:8161 \
     --publish 61613:61613 \
     --publish 5672:5672 \
     --env ARTEMIS_USER=magento \
     --env ARTEMIS_PASSWORD=magento \
     apache/activemq-artemis:2.42.0
   ```

#### Opdrachten voor Docker-beheer

```bash
# Check container status
docker ps | grep artemis

# View logs
docker logs artemis

# Stop the container
docker stop artemis

# Start the container
docker start artemis

# Remove the container
docker rm artemis
```

#### Toegang tot diensten

Zodra de container van de Dokker loopt, kunt u tot:

- **console van het Web**: http://localhost :8161/console (standaardgeloofsbrieven: artemis/artemis)
- **STOMP haven**: localhost :61613 (voor de verbinding van Adobe Commerce)

>[!NOTE]
>
>De Docker-installatie wordt aanbevolen voor ontwikkeling en testen. Voor productie, denk na gebruikend de handinstallatie met juiste veiligheidsconfiguraties.

### Optie 2: Handmatige installatie op Ubuntu/CentOS

#### Vereisten

Controleer of Java 17 of hoger is geïnstalleerd (vereist voor ActiveMQ Artemis 2.42.0+).

### Installatiestappen

1. Download en installeer de recentste versie van de [&#x200B; Apache ActiveMQ Artemis website &#x200B;](https://activemq.apache.org/components/artemis/download/). Vanaf september 2025 is de meest recente stabiele versie 2.42.0:

   ```bash
   sudo mkdir -p /opt/artemis
   cd /opt/artemis
   sudo curl -O https://downloads.apache.org/activemq/activemq-artemis/2.42.0/apache-artemis-2.42.0-bin.tar.gz
   sudo tar -xzf apache-artemis-2.42.0-bin.tar.gz --strip-components=1
   sudo rm apache-artemis-2.42.0-bin.tar.gz
   ```

1. Maak de `artemis` -gebruiker en stel de eigendom in:

   ```bash
   # Create artemis user and set ownership
   sudo useradd -r -s /bin/false artemis 2>/dev/null || true
   sudo chown -R artemis:artemis /opt/artemis
   ```

1. Een makelaarinstantie maken:

   ```bash
   sudo /opt/artemis/bin/artemis create /var/lib/artemis-instance --user artemis --password artemis --allow-anonymous
   sudo chown -R artemis:artemis /var/lib/artemis-instance
   ```

1. Start de makelaar:

   ```bash
   # Start in foreground (for testing)
   sudo /var/lib/artemis-instance/bin/artemis run
   
   # Start as background service
   sudo /var/lib/artemis-instance/bin/artemis-service start
   
   # Stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service stop
   
   # Restart the broker
   sudo /var/lib/artemis-instance/bin/artemis-service restart
   
   # Force stop the broker
   sudo /var/lib/artemis-instance/bin/artemis-service force-stop
   
   # Check broker status
   sudo /var/lib/artemis-instance/bin/artemis-service status
   ```

## ActiveMQ-artemis configureren

Controleer de officiële documentatie van de Artemis ActiveMQ om de makelaar te vormen en te beheren. Let op het volgende:

- Omgevingsvariabelen
- Poorttoegang (STOMP-protocol)
- Standaardgebruikersaccounts en -referenties
- Starten en stoppen van de makelaar
- Systeemlimieten en resourceaanpassing

### Belangrijkste configuratiebestanden

- `/var/lib/artemis-instance/etc/broker.xml` - Configuratie hoofdmakelaar
- `/var/lib/artemis-instance/etc/artemis-users.properties` - Gebruikersverificatie
- `/var/lib/artemis-instance/etc/artemis-roles.properties` - Gebruikersrollen
- `/var/lib/artemis-instance/etc/bootstrap.xml` - Bootstrap-configuratie

### STOMP-protocol inschakelen

Controleer `/var/lib/artemis-instance/etc/broker.xml` om te controleren of de STOMP-acceptor is geconfigureerd:

```xml
<acceptors>
   <acceptor name="artemis">tcp://0.0.0.0:61616?tcpSendBufferSize=1048576;tcpReceiveBufferSize=1048576;amqpMinLargeMessageSize=102400;protocols=CORE,AMQP,STOMP,HORNETQ,MQTT,OPENWIRE;useEpoll=true;amqpCredits=1000;amqpLowCredits=300;amqpDuplicateDetection=true</acceptor>
   <acceptor name="stomp">tcp://0.0.0.0:61613?protocols=STOMP</acceptor>
   <acceptor name="stomp-ssl">tcp://0.0.0.0:61617?protocols=STOMP;sslEnabled=true;keyStorePath=/path/to/keystore.jks;keyStorePassword=password</acceptor>
</acceptors>
```

Als u SSL wilt inschakelen bij STOMP, moet u de `stomp-ssl` -acceptor expliciet toevoegen.

## Installeren met ActiveMQ-arrays en verbinding maken

Als u Adobe Commerce _na_ installeert u Artemis ActiveMQ, voeg de volgende bevel-lijn parameters tijdens installatie toe:

```bash
--stomp-host="<hostname>" --stomp-port="61613" --stomp-user="<user_name>" --stomp-password="<password>"
```

Waarbij:

| Parameter | Beschrijving |
|--- |--- |
| `--stomp-host` | De hostnaam waar ActiveMQ is geïnstalleerd. |
| `--stomp-port` | De poort die moet worden gebruikt voor verbinding met ActiveMQ. De standaardwaarde is `61613` . |
| `--stomp-user` | De gebruikersnaam voor het verbinden met ActiveMQ. Gebruik de standaardgebruiker `artemis` niet. |
| `--stomp-password` | Het wachtwoord voor verbinding maken met ActiveMQ. Gebruik het standaardwachtwoord niet `artemis` . |
| `--stomp-ssl` | Geeft aan of verbinding moet worden gemaakt met ActiveMQ. De standaardwaarde is `false` . Als u de waarde aan waar plaatst, zie SSL voor meer informatie vormen. |

## Connect ActiveMQ-artemis

Als het `<install_directory>/app/etc/env.php` -bestand al een Adobe Commerce-instantie bevat met de configuratie RabbitMQ (AMQP) en u wilt deze verbinding maken met ActiveMQ, vervangt u de sectie `queue` door STOMP, zodat deze op het volgende lijkt:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

U kunt ActiveMQ-configuratiewaarden ook instellen met de opdracht `bin/magento setup:config:set` (verwijder de AMQP-configuratie als deze bestaat in het `app/etc/env.php` -bestand):

```bash
bin/magento setup:config:set --stomp-host="activemq.example.com" --stomp-port="61613" --stomp-user="magento" --stomp-password="magento"
```

Nadat u de opdracht hebt uitgevoerd of het `<install_directory>/app/etc/env.php` -bestand met STOMP-configuratiewaarden hebt bijgewerkt, voert u `bin/magento setup:upgrade` uit om de wijzigingen toe te passen en de vereiste wachtrijen in ActiveMQ te maken.

## SSL configureren

Als u ondersteuning voor SSL wilt configureren, bewerkt u de parameters `ssl` en `ssl_options` in het `<install_directory>/app/etc/env.php` -bestand, zodat deze op het volgende lijken:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61617',  // SSL STOMP port (default 61617, non-SSL is 61613)
      'user' => 'magento',
      'password' => 'magento',
      'ssl' => 'true',
      'ssl_options' => [
            'cafile' => '/etc/pki/tls/certs/DigiCertCA.crt',
            'local_cert' => '/path/to/magento/app/etc/ssl/test-activemq.crt', // Optional: Client certificate for mutual SSL
            'local_pk' => '/path/to/magento/app/etc/ssl/test-activemq.key', // Optional: Client private key for mutual SSL
            'passphrase' => 'client_key_password', // Optional: Passphrase for client private key
            'verify_peer' => true,
            'verify_peer_name' => true,
            'allow_self_signed' => false
       ],
      // Performance tuning options
      'heartbeat_send' => 10000,     // 10 seconds // Optional
      'heartbeat_receive' => 10000,  // 10 seconds // Optional
      'read_timeout' => 250000       // 250ms // Optional
     ),
  ),
```

### SSL-configuratieopties

| Optie | Beschrijving | Standaard |
|--- |--- |--- |
| `verify_peer` | Het SSL-certificaat van de makelaar verifiëren | `true` |
| `verify_peer_name` | Controleren of de hostnaam van de makelaar overeenkomt met het certificaat | `true` |
| `allow_self_signed` | Zelfondertekende certificaten toestaan | `false` |
| `cafile` | Pad naar CA-certificaatbestand voor brokerverificatie | Vereist voor SSL |
| `certfile` | Pad naar clientcertificaatbestand (voor wederzijdse SSL) | Optioneel |
| `keyfile` | Pad naar privésleutelbestand van client (voor wederzijdse SSL) | Optioneel |
| `passphrase` | Passphrase voor cliënt privé sleutel | Optioneel |

### SSL-configuratie voor ontwikkeling

Voor ontwikkelomgevingen kunt u ontspannen SSL-instellingen gebruiken:

```php
'ssl_options' => [
    'verify_peer' => false,
    'verify_peer_name' => false,
    'allow_self_signed' => true
]
```

## Prestaties afstemmen

ActiveMQ Artemis biedt verschillende opties voor het afstemmen van prestaties:

```php
'queue' =>
  array (
    'stomp' =>
    array (
      'host' => 'activemq.example.com',
      'port' => '61613',
      'user' => 'artemis',
      'password' => 'artemis',
      // Performance options
      'heartbeat_send' => 10000,      // Send heartbeat every 10 seconds
      'heartbeat_receive' => 10000,   // Expect heartbeat every 10 seconds
      'read_timeout' => 250000,       // 250ms read timeout
     ),
  ),
```

## Toezicht en beheer

### Webconsole

ActiveMQ Artemis biedt een webgebaseerde beheerconsole die toegankelijk is op:
- URL: `http://localhost:8161/console`
- Standaardreferenties: `artemis/artemis`

## Problemen oplossen

### Algemene kwesties

1. **Verweigerde Verbinding**: Verzeker Artemis ActiveMQ loopt en de accepteerder van STOMP wordt gevormd.
1. **Ontbroken Authentificatie**: Controle gebruikersbenaming/wachtwoord in zowel makelaarconfiguratie als het `env.php` dossier.
1. **ontbroken SSL handshake**: Verifieer SSL certificaten en configuratie.




### STOMP-verbinding controleren

STOMP-verbinding testen met Telnet:

```bash
telnet localhost 61613
```

Er moet een verbinding tot stand worden gebracht. Testen met een STOMP-opdracht:

```bash
# Test basic STOMP connection
echo -e "CONNECT\nhost:localhost\n\n\x00" | telnet localhost 61613
```

De verwachte output zou verbinding gevestigd en STOMP protocolreactie moeten tonen.

## Gebruikers in de wachtrij met berichten starten

Nadat u Adobe Commerce en ActiveMQ Artemis hebt aangesloten, moet u de gebruikers van de berichtrij beginnen. Zie [&#x200B; berichtrijen &#x200B;](../../configuration/cli/start-message-queues.md) voor details vormen.

