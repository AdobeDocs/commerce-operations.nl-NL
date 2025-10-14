---
title: Berichtenrijen beheren
description: Leer hoe u berichtrijen van de bevellijn voor Adobe Commerce kunt beheren.
exl-id: 619e5df1-39cb-49b6-b636-618b12682d32
source-git-commit: 47525e8d8379061b254bfa90ab46e27a1ee2f524
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Berichtenrijen beheren

U kunt berichtrijen van de bevellijn beheren gebruikend kroonbanen of een externe procesmanager om ervoor te zorgen dat de consumenten berichten terugwinnen. Dit geldt voor alle ondersteunde berichtbrokers, waaronder RabbitMQ (AMQP), Apache ActiveMQ Artemis (STOMP) en MySQL-adapter.

## Procesbeheer

Cron jobs zijn het standaardmechanisme om consumenten opnieuw op te starten. Processen die door `cron` worden gestart, verbruiken het opgegeven aantal berichten en eindigen vervolgens. Als u `cron` opnieuw uitvoert, wordt de gebruiker opnieuw gestart.

In het volgende voorbeeld wordt de `crontab` -configuratie getoond voor het uitvoeren van consumenten:

> /app/code/Magento/MessageQueue/etc/crontab.xml

```xml
...
<job name="consumers_runner" instance="Magento\MessageQueue\Model\Cron\ConsumersRunner" method="run">
    <schedule>* * * * *</schedule>
</job>
...
```

>[!INFO]
>
>Hoe vaak u berichtrijen controleert kan van uw bedrijfslogica en beschikbare systeemmiddelen afhangen. Over het algemeen wilt u wellicht meer controleren op nieuwe klanten en welkomste-mails verzenden dan een proces dat veel resources vergt, zoals het bijwerken van uw catalogus. U moet `cron` planningen definiëren op basis van uw bedrijfsbehoeften.
>
>U kunt deze configuratie configureren in de beheerwinkels > Instellingen > Configuratie > Geavanceerd > Systeem > Cron-configuratieopties voor de groep: consumenten.
>
>Zie [ uitsnede ](../cli/configure-cron-jobs.md) voor meer informatie vormen en in werking stellen over het gebruiken van `cron` met Commerce.

U kunt een procesmanager zoals [ Supervisor ](https://supervisord.readthedocs.io/en/latest/) ook gebruiken om het statuut van processen te controleren. De manager kan de bevellijn gebruiken om de processen opnieuw te beginnen zoals nodig.

## Configuratie

### Gedrag standaard

- Uitsnijdtaak `consumers_runner` is ingeschakeld
- Uitsnijdtaak `consumers_runner` voert alle gedefinieerde consumenten uit
- Elke consument verwerkt 10000 berichten en eindigt dan

>[!INFO]
>
>Als uw Adobe Commerce-winkel op het Cloud-platform wordt gehost, gebruikt u [`CRON_CONSUMERS_RUNNER` ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) om de `consumers_runner` cron-taak te configureren.

### Specifieke configuratie

Bewerk het bestand `/app/etc/env.php` om de uitsnijdtaak te configureren `consumers_runner` .

```php
...
    'cron_consumers_runner' => [
        'cron_run' => false,
        'max_messages' => 20000,
        'consumers' => [
            'consumer1',
            'consumer2',
        ],
        'multiple_processes' => [
            'consumer1' => 4
        ]
    ],
...
```

- `cron_run` - Een Booleaanse waarde die de `consumers_runner` cron-taak in- of uitschakelt (standaardwaarde = `true` ).
- `max_messages` - Het maximum aantal berichten dat elke consument moet verwerken voordat deze wordt beëindigd (standaardwaarde = `10000` ). Hoewel wij het niet adviseren, kunt u 0 gebruiken om de consument te verhinderen te eindigen. Zie [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) om te vormen hoe de consumenten berichten van de berichtrij verwerken.
- `consumers` - Een array van tekenreeksen die aangeven welke consumenten moeten worden uitgevoerd. Een lege serie stelt *alle* consumenten in werking.
- `multiple_processes` - Een array van sleutelwaardeparen die aangeven welke consument moet worden uitgevoerd in hoeveel processen. Ondersteund in Commerce 2.4.4 of hoger.

  >[!INFO]
  >
  >Het wordt niet geadviseerd om veelvoudige consumenten op een MySQL-Bediende rij in werking te stellen. Zie [ het berichtrij van de Verandering van MySQL aan externe makelaars ](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-external-brokers) voor meer informatie over het schakelen naar AMQP (RabbitMQ) of STOMP (ActiveMQ Artemis).

  >[!INFO]
  >
  >Als uw opslag van Adobe Commerce op het platform van de Wolk wordt ontvangen, gebruik [`CONSUMERS_WAIT_FOR_MAX_MESSAGES` ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#consumers_wait_for_max_messages) om te vormen hoe de consumenten berichten van de berichtrij verwerken.

  >[!NOTE]
  >
  >ActiveMQ Artemis (STOMP) werd geïntroduceerd in Adobe Commerce 2.4.6 en latere versies.

Zie [ de gebruikers van de het berichtrij van het Begin ](../cli/start-message-queues.md).
