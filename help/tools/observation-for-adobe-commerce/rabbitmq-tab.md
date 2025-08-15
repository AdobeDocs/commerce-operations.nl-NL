---
title: Het tabblad [!UICONTROL [!DNL RabbitMQ]
description: Meer informatie over het tabblad [!UICONTROL [!DNL RabbitMQ] ] van  [!DNL Observation for Adobe Commerce] .
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Het tabblad [!UICONTROL [!DNL RabbitMQ]]

Het tabblad **[!UICONTROL [!DNL RabbitMQ]]** bevat informatie die is toegespitst op [!DNL RabbitMQ] -signalen.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Infrastructuurgebeurtenissen ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

In het frame **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** worden infrastructuurgebeurtenissen weergegeven die betrekking hebben op [!DNL RabbitMQ] en die binnen de geselecteerde tijdlijn zijn opgetreden:

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) als `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) als `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) als `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) als `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) als `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) als `node2_timeout_exceeded`
* `%401 Unauthorized%`) als `401_unauth`
* `%401 Unauthorized%`) als `401_unauth`
* `%Service restarted: rabbitmq-server%`) als `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) als `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) als `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) als `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) als `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) als `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) als `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) als `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) als `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) als `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) als `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] servicestartsignalen/stopsignalen ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

In dit frame worden [!DNL RabbitMQ] service start/stop-signalen weergegeven die tijdens het geselecteerde tijdframe zijn opgetreden:

* `%RabbitMQ is asked to stop...%`) als `rabbitmq_stop`
* `%Starting RabbitMQ%`) als `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] errors ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

In dit frame worden [!DNL RabbitMQ] fouten weergegeven die tijdens het geselecteerde tijdframe zijn opgetreden:

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` as `exit_timeout`
* `%client unexpectedly closed TCP connection%`) als `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) als `undef_exit`
* `%Connection attempt from disallowed node%`) als `disallowed_node`
* `%closing AMQP connection%`) als `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] node status ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) als `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) als `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) als `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) als `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) als `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) als `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] Samenvattingsstatus op hoog niveau van het bericht door Rij ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

De grafiek **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** toont het aantal gepubliceerde berichten door de [!DNL RabbitMQ] wachtrij voor de geselecteerde tijdlijn.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] Overzicht van berichtdetails ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) als `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) als `queue_err`
* `%authenticated and granted access to vhost%`) als `auth`
* `%closing AMQP connection%`) als `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] Wachtrijverbruik MB ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

In de grafiek **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** wordt het aantal bytes weergegeven dat door elke [!DNL RabbitMQ] -wachtrij gedurende de geselecteerde tijdlijn wordt gebruikt.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] Gepubliceerde Berichten door Rij ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

In de grafiek **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** wordt het aantal bytes weergegeven dat door elke [!DNL RabbitMQ] -wachtrij gedurende de geselecteerde tijdlijn wordt gebruikt.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] Gepubliceerde Doorvoer van Bericht door Rij ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

De grafiek van **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** toont het gemiddelde aantal gepubliceerde berichten per seconde door elke [!DNL RabbitMQ] rij over het geselecteerde tijdkader.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Totale Doorvoer van Bericht door Rij ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

De grafiek van **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** toont het gemiddelde totale aantal berichten per seconde door elke [!DNL RabbitMQ] rij over het geselecteerde timeframe.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] Consumenten door Wachtrij ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

In de grafiek **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** wordt het gemiddelde totale aantal gebruikers per [!DNL RabbitMQ] -wachtrij gedurende de geselecteerde tijdlijn weergegeven.
