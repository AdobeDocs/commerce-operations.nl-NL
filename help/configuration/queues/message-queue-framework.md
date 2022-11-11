---
title: Overzicht berichtenrijen
description: Lees meer over het framework voor de wachtrij van berichten en hoe dit werkt met de Adobe Commerce- en Magento Open Source-toepassing.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Overzicht van wachtrij met berichten

Het Kader van de Rij van het Bericht (MQF) is een systeem dat een [module](https://glossary.magento.com/module) om berichten aan rijen te publiceren. Het bepaalt ook de consumenten die de berichten asynchroon zullen ontvangen. Het MQF-gebruik [KonijnMQ](https://www.rabbitmq.com) als overseinenmakelaar, die een scalable platform voor het verzenden van en het ontvangen van berichten verstrekt. Het omvat ook een mechanisme voor het opslaan van niet-geleverde berichten. RabbitMQ is gebaseerd op de Advanced Message Queuing Protocol (AMQP) 0.9.1 specificatie.

Het volgende diagram illustreert het Kader van de Rij van het Bericht:

![Message Queue Framework](../../assets/configuration/mq-framework.png)

- A [uitgever](https://glossary.magento.com/publisher-subscriber-pattern) is een component die berichten naar een uitwisseling verzendt. Het weet aan welke uitwisseling te publiceren aan en het formaat van de berichten het verzendt.

- Een uitwisseling ontvangt berichten van uitgevers en verzendt hen naar rijen. Hoewel RabbitMQ veelvoudige soorten uitwisselingen steunt, gebruikt de Handel onderwerpuitwisselingen slechts. Een onderwerp omvat een verpletterende sleutel, die tekstkoorden bevat die door punten worden gescheiden. De indeling voor een onderwerpnaam is `string1.string2`: bijvoorbeeld: `customer.created` of `customer.sent.email`.

   De makelaar staat u toe om vervangingen te gebruiken wanneer het plaatsen van regels voor het door:sturen van berichten. U kunt een sterretje gebruiken (`*`) te vervangen _één_ tekenreeks of hekje (`#`) om 0 of meer tekenreeksen te vervangen. Bijvoorbeeld: `customer.*` zou filteren op `customer.create` en `customer.delete`, maar niet `customer.sent.email`. Niettemin `customer.#` zou filteren op `customer.create`,  `customer.delete`, en `customer.sent.email`.

- Een wachtrij is een buffer die berichten opslaat.

- Een consument ontvangt berichten. Het weet welke rij te verbruiken is. Het kan bewerkers van het bericht aan een specifieke rij in kaart brengen.

Een basissysteem voor een wachtrij met berichten kan ook worden ingesteld zonder RabbitMQ te gebruiken. In dit systeem, een MySQL [adapter](https://glossary.magento.com/adapter) slaat berichten in het gegevensbestand op. Drie databasetabellen (`queue`, `queue_message`, en `queue_message_status`) de werkbelasting van de wachtrij met berichten beheren. Cron jobs zorgen ervoor dat de consumenten berichten kunnen ontvangen. Deze oplossing is niet erg schaalbaar. RabbitMQ dient waar mogelijk te worden gebruikt.
