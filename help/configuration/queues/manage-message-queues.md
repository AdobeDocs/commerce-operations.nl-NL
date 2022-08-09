---
title: Berichtenrijen beheren
description: Leer hoe u berichtrijen van de bevellijn voor Adobe Commerce kunt beheren.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Berichtenrijen beheren

U kunt berichtrijen van de bevellijn beheren gebruikend kroonbanen of een externe procesmanager om ervoor te zorgen dat de consumenten berichten terugwinnen.

## Procesbeheer

Cron jobs zijn het standaardmechanisme om consumenten opnieuw op te starten. Processen gestart door `cron` consume het gespecificeerde aantal berichten en eindig dan. Herbergen `cron` start de consument opnieuw op.

In het volgende voorbeeld wordt het `crontab` configuratie voor het runnen van consumenten:

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
>Hoe vaak u berichtrijen controleert hangt van uw bedrijfslogica en beschikbare systeemmiddelen af. Over het algemeen wilt u wellicht meer controleren op nieuwe klanten en welkomste-mails verzenden dan een proces dat veel resources vergt, zoals het bijwerken van uw catalogus. U moet `cron` programma&#39;s volgens uw bedrijfsbehoeften.
>
>U kunt deze configuratie configureren in de beheerderwinkels > Instellingen > Configuratie > Geavanceerd > Systeem > Cron-configuratieopties voor de groep: consumenten.
>
>Zie [Uitsnede configureren en uitvoeren](../cli/configure-cron-jobs.md) voor meer informatie over het gebruik `cron` met Commerce.

U kunt ook procesbeheer gebruiken, zoals [Supervisor](http://supervisord.org/index.html) de status van processen te controleren. De manager kan de bevellijn gebruiken om de processen opnieuw te beginnen zoals nodig.

## Configuratie

### Gedrag standaard

- Uitsnijdtaak `consumers_runner` is ingeschakeld
- Uitsnijdtaak `consumers_runner` alle gedefinieerde consumenten
- Elke consument verwerkt 10000 berichten en eindigt dan

>[!INFO]
>
>Als uw Adobe Commerce-winkel op het Cloud-platform wordt gehost, gebruikt u de [`CRON_CONSUMERS_RUNNER`](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) om het `consumers_runner` snijtaak.

### Specifieke configuratie

Bewerk de `/app/etc/env.php` bestand om de uitsnijdtaak te configureren `consumers_runner`.

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

- `cron_run` - Een Booleaanse waarde die de `consumers_runner` uitsnijdtaak (standaard = `true`).
- `max_messages` - Het maximumaantal berichten dat elke consument moet verwerken voordat deze wordt beëindigd (standaardwaarde = `10000`). Hoewel wij het niet adviseren, kunt u 0 gebruiken om de consument te verhinderen te eindigen. Zie [`consumers_wait_for_messages`](../reference/config-reference-envphp.md#consumerswaitformessages) om te vormen hoe de consumenten berichten van de berichtrij verwerken.
- `consumers` - Een array van tekenreeksen die aangeven welke consumenten moeten worden uitgevoerd. Een lege array wordt uitgevoerd *alles* consumenten.
- `multiple_processes` - Een array van sleutelwaardeparen die aangeven welke consument moet werken in hoeveel processen.

   >[!INFO]
   >
   >Het wordt niet geadviseerd om veelvoudige consumenten op een MySQL-Bediende rij in werking te stellen. Zie [Berichtwachtrij wijzigen van MySQL in AMQP](https://developer.adobe.com/commerce/php/development/components/message-queues/#change-message-queue-from-mysql-to-amqp) voor meer informatie .

   >[!INFO]
   >
   >Als uw Adobe Commerce-winkel op het Cloud-platform wordt gehost, gebruikt u de [`CONSUMERS_WAIT_FOR_MAX_MESSAGES`](https://devdocs.magento.com/cloud/env/variables-deploy.html#consumers_wait_for_max_messages) om te vormen hoe de consumenten berichten van de berichtrij verwerken.

Zie [Gebruikers in de wachtrij met berichten starten](../cli/start-message-queues.md).