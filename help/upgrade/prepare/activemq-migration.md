---
title: Migreren van RabbitMQ naar ActiveMQ
description: Leer over het vervangen van de broker van de berichtrij die voor op-gebouw installaties van Adobe Commerce wordt gebruikt.
feature: Services, Configuration
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 0%

---

# Migreren naar ActiveMQ

ActiveMQ (Apache ActiveMQ Artemis) is een krachtige, multi-protocol berichtmakelaar die een alternatief voor RabbitMQ voor de behandeling van berichtrijen in Adobe Commerce verstrekt.

Vanaf 2.4.8-p3, 2.4.7-p8, 2.4.6-p13 en 2.4.5-p16, steunt Adobe Commerce ActiveMQ als broker van de berichtrij. Dit verstrekt extra flexibiliteit voor installaties op-gebouw om tussen RabbitMQ en ActiveMQ te kiezen die op hun infrastructuurvereisten en deskundigheid wordt gebaseerd.

## Voordat u begint

Controleer voordat u de migratie start het volgende:

1. Controleer de huidige configuratie van RabbitMQ in `app/etc/env.php` .
1. Maak een volledige back-up van de database en de codebase.
1. Controleer of uw installatie voldoet aan de systeemvereisten voor ActiveMQ.
1. Plan een onderhoudsvenster om de migratie te voltooien.

## Migratiepad

Het migreren naar ActiveMQ is een eenvoudig proces, maar het is essentieel om ervoor te zorgen dat alle lopende berichten worden verwerkt alvorens van makelaars te veranderen.

Bij deze migratieinstructies wordt ervan uitgegaan dat Adobe Commerce de enige toepassing is die de berichtenwachtrij-broker gebruikt.

### Stap 1: Plaats de site in de onderhoudsmodus

1. Plaats de plaats in [&#x200B; Wijze van het Onderhoud &#x200B;](../../installation/tutorials/maintenance-mode.md):

   ```bash
   bin/magento maintenance:enable
   ```

1. Controleren of de onderhoudsmodus is ingeschakeld:

   ```bash
   bin/magento maintenance:status
   ```

### Stap 2: Telling van RabbitMQ-berichten controleren

Controleer voordat u verdergaat of alle berichten in RabbitMQ zijn verwerkt. Gebruik een van de volgende methoden:

#### Methode A: Het beheerdashboard van Konijn gebruiken

1. Open de beheerinterface van RabbitMQ op `http://<host>:15672`
1. Standaardreferenties: `guest/guest`
1. Navigeer aan het **lusje van de Opsommingen**
1. Verifieer alle rijen tonen **0 berichten**

   ![&#x200B; RabbitMQ Management Dashboard &#x200B;](../../assets/upgrade-guide/rabbitmq_mgmt_dashboard.png)

#### Methode B: gebruik van de opdrachtregel rabbitmqctl

1. Controleer alle rijen en hun berichttellingen:

   ```bash
   rabbitmqctl list_queues name messages consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl.png" alt="RabbitMQ CLI Output" width="500" />

1. Gedetailleerde rijgegevens controleren:

   ```bash
   rabbitmqctl list_queues name messages messages_ready messages_unacknowledged consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl_detailed.png" alt="CLI Gedetailleerde uitvoer van RabbitMQ" width="500" />

### Stap 3: Verwerken van lopende berichten

Als de berichten in om het even welke rijen in behandeling zijn, proces hen alvorens te werk te gaan.

1. Bekijk de lijst met beschikbare consumenten:

   ```bash
   bin/magento queue:consumers:list
   ```

1. Consumenten verwerken als groep of per wachtrij met afzonderlijke berichten:

   - **de consumenten van het Proces als groep**

     ```bash
     bin/magento cron:run --group=consumers
     ```

     >[!NOTE]
     >
     >Als de uitsnede al op uw systeem wordt uitgevoerd, hoeft u `bin/magento cron:run --group=consumers` niet handmatig uit te voeren. In plaats daarvan, verifieer dat de berichten door de berichttellingen te controleren gebruikend de bevelen van Stap 2 worden verwerkt.

   - **Proces een specifieke berichtrij**

     ```bash
     bin/magento queue:consumers:start <consumer_name> --max-messages=<number>
     ```

     Bijvoorbeeld om asynchrone bewerkingen te verwerken:

     ```bash
     bin/magento queue:consumers:start async.operations.all --max-messages=1000
     ```

     >[!NOTE]
     >
     >De parameter `--max-messages` beperkt het aantal berichten dat moet worden verwerkt voordat de consument stopt. Pas deze waarde aan op basis van de grootte van de wachtrij.

   - **het berichtverwerking van de Monitor**

     Ononderbroken tellen van het controlebericht tot alle rijen leeg zijn:

     ```bash
     # Check every few seconds until 0 messages remain
     watch -n 5 "rabbitmqctl list_queues name messages | grep -v '^Listing' | grep -v '0$'"
     ```

### Stap 4: controleer of alle berichten zijn verwerkt

Alvorens aan de volgende stap te werk te gaan, zorg **alle rijen tonen 0 berichten**. Voer de verificatieopdrachten opnieuw uit vanuit Stap 2.

>[!WARNING]
>
>Ga niet verder met de volgende stap als er berichten onverwerkt blijven. Het gegevensverlies kan voorkomen als u makelaars schakelt terwijl de berichten nog in behandeling zijn.

### Stap 5: stoppen van consumenten en banen in de bouwsector

1. Alle actieve gebruikers in de wachtrij met berichten stoppen:

   ```bash
   # If using supervisor
   supervisorctl stop all
   
   # Or manually kill consumer processes
   pkill -f "queue:consumers:start"
   ```

1. Snijtaken uitschakelen:

   ```bash
   bin/magento cron:remove
   ```

1. Controleren of snijtaken zijn verwijderd:

   ```bash
   crontab -l
   ```

### Stap 6: Back-up maken van huidige configuratie

Maak een back-up van uw huidige configuratie:

```bash
cp app/etc/env.php app/etc/env.php.backup.rabbitmq
```

### Stap 7: Optioneel verwijderen van RabbitMQ

U kunt RabbitMQ verwijderen als dit niet meer nodig is.

### Stap 8: ActiveMQ installeren en configureren in Adobe Commerce

Om installatie ActiveMQ en configuratietaken zoals het vormen van het protocol van STOMP te voltooien en de verbinding te verifiëren, zie de [&#x200B; Gids van de Installatie en van de Configuratie &#x200B;](../../installation/prerequisites/activemq.md).

### Stap 9: Cron-taken opnieuw installeren

1. Nadat de tests met succes zijn voltooid, installeert u de snijtaken opnieuw:

   ```bash
   bin/magento cron:install
   ```

1. Controleren of uitsnijdtaken zijn gepland:

   ```bash
   crontab -l
   ```

### Stap 10: Onderhoudsmodus uitschakelen

1. Nadat u hebt gecontroleerd of alles correct werkt, schakelt u de onderhoudsmodus uit:

   ```bash
   bin/magento maintenance:disable
   ```

1. Controleren of de onderhoudsmodus is uitgeschakeld:

   ```bash
   bin/magento maintenance:status
   ```

### Stap 11: Het systeem bewaken

Controleer uw systeem 24-48 uur na migratie om ervoor te zorgen dat alle rijverrichtingen correct functioneren:

- Controleer regelmatig de Console van het Web ActiveMQ voor berichtproductie
- Toepassingslogboeken controleren op fouten met betrekking tot wachtrijen
- Verifieer dat de asynchrone verrichtingen (config bewaart, uitvoert, etc.) werken
- Snijlogboeken controleren om ervoor te zorgen dat consumenten actief zijn

```bash
# Monitor system logs for queue activity
tail -f var/log/system.log | grep -i queue

# Monitor cron logs
tail -f var/log/cron.log

# Check running consumer processes
ps aux | grep "queue:consumers:start"
```

## Terugdraaien

Als er problemen optreden tijdens of na de migratie, kunt u terugdraaien naar RabbitMQ:

1. Onderhoudsmodus inschakelen:

   ```bash
   bin/magento maintenance:enable
   ```

1. Stop alle consumenten en schakel de kroon uit:

   ```bash
   pkill -f "queue:consumers:start"
   bin/magento cron:remove
   ```

1. De vorige configuratie herstellen:

   ```bash
   cp app/etc/env.php.backup.rabbitmq app/etc/env.php
   ```

1. RabbitMQ starten (indien gestopt):

   ```bash
   sudo systemctl start rabbitmq-server
   ```

1. Cache wissen:

   ```bash
   bin/magento cache:flush
   ```

1. Uitsnijden opnieuw installeren:

   ```bash
   bin/magento cron:install
   ```

1. Onderhoudsmodus uitschakelen:

   ```bash
   bin/magento maintenance:disable
   ```

Na het voltooien van de migratie zijn geen verdere wijzigingen in de configuratiewaarde nodig.

