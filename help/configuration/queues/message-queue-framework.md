---
title: Overzicht berichtenrijen
description: Lees meer over het framework voor de wachtrij van berichten en hoe dit werkt met de Adobe Commerce-toepassing.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Overzicht van wachtrij met berichten

Het Kader van de Rij van het Bericht (MQF) is een systeem dat een module toestaat om berichten aan rijen te publiceren. Het bepaalt ook de [ consumenten ](consumers.md) die de berichten asynchroon zullen ontvangen. MQF gebruikt [[!DNL RabbitMQ] ](https://www.rabbitmq.com) als overseinenmakelaar, die een scalable platform voor het verzenden van en het ontvangen van berichten verstrekt. Het omvat ook een mechanisme voor het opslaan van niet-geleverde berichten. [!DNL RabbitMQ] is gebaseerd op de Geavanceerde specificatie 0.9.1 van het een rij vormen van het Bericht van het Protocol (AMQP).

Het volgende diagram illustreert het Kader van de Rij van het Bericht:

![ Kader van de Rij van het Bericht ](../../assets/configuration/mq-framework.png)

- Een uitgever is een component die berichten naar een uitwisseling verzendt. Het weet aan welke uitwisseling te publiceren aan en het formaat van de berichten het verzendt.

- Een uitwisseling ontvangt berichten van uitgevers en verzendt hen naar rijen. Hoewel [!DNL RabbitMQ] veelvoudige types van uitwisseling steunt, gebruikt Commerce onderwerpuitwisseling slechts. Een onderwerp omvat een verpletterende sleutel, die tekstkoorden bevat die door punten worden gescheiden. De indeling voor een onderwerpnaam is `string1.string2` : bijvoorbeeld `customer.created` of `customer.sent.email` .

  De makelaar staat u toe om vervangingen te gebruiken wanneer het plaatsen van regels voor het door:sturen van berichten. U kunt een asterisk (`*`) gebruiken om _één_ koord of een pond teken (`#`) te vervangen om 0 of meer koorden te vervangen. `customer.*` filtert bijvoorbeeld op `customer.create` en `customer.delete` , maar niet `customer.sent.email` . `customer.#` filtert echter op `customer.create` , `customer.delete` en `customer.sent.email` .

- Een wachtrij is een buffer die berichten opslaat.

- Een consument ontvangt berichten. Het weet welke rij te verbruiken is. Het kan bewerkers van het bericht aan een specifieke rij in kaart brengen.

Een basissysteem voor een wachtrij met berichten kan ook worden ingesteld zonder [!DNL RabbitMQ] te gebruiken. In dit systeem slaat een MySQL-adapter berichten op in de database. Drie databasetabellen (`queue`, `queue_message` en `queue_message_status` ) beheren de werkbelasting van de wachtrij met berichten. Cron jobs zorgen ervoor dat de consumenten berichten kunnen ontvangen. Deze oplossing is niet erg schaalbaar. [!DNL RabbitMQ] moet indien mogelijk worden gebruikt.
