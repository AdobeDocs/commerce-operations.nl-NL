---
title: '"De [!UICONTROL RabbitMQ] tab"'
description: Meer informatie over de [!UICONTROL RabbitMQ] tabblad van [!DNL Observation for Adobe Commerce].
source-git-commit: 3f2a401bb916fc04405f21ba2acfc42f7defdccb
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 0%

---

# De [!UICONTROL RabbitMQ] tab

De **[!UICONTROL RabbitMQ]** tab bevat informatie waarop de focus ligt [!DNL RabbitMQ] signalen.

## [!UICONTROL RabbitMQ Infrastructure events]

![RabbitMQ Infrastructure-gebeurtenissen](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

De **[!UICONTROL RabbitMQ Infrastructure events]** frame toont infrastructuurgebeurtenissen die betrekking hebben op [!DNL RabbitMQ] die zich tijdens de geselecteerde tijdlijn hebben voorgedaan:

* %response [fout] for node [rabbit@host1]: Onverwachte http-reactie van%&#39;) als &#39;Onverwacht_resp_node1&#39;
* &#39;%response [fout] for node [rabbit@host2]: Onverwachte http-reactie van%&#39;) als &#39;Onverwacht_resp_node2&#39;
* &#39;%response [fout] for node [rabbit@host3]: Onverwachte http-reactie van%&#39;) als &#39;Onverwacht_resp_node3&#39;
* &#39;%response [fout] for node [rabbit@host3]: Ga naar &quot;http://localhost:15672/api/healthchecks/node/rabbit@host3&quot;: contextdeadline overschreden%&#39;) als &#39;node3_timeout_over&#39;
* &#39;%response [fout] for node [rabbit@host1]: Ga naar &quot;http://localhost:15672/api/healthchecks/node/rabbit@host1&quot;: contextdeadline overschreden%&#39;) als &#39;node1_timeout_over
* &#39;%response [fout] for node [rabbit@host2]: Ga naar &quot;http://localhost:15672/api/healthchecks/node/rabbit@host2&quot;: contextdeadline overschreden%&#39;) als &#39;node2_timeout_over&#39;
* &quot;%401 Unauthorised%&quot;) als &quot;401_unauth&quot;
* &#39;%401 Unauthorised%&#39;) als &#39;401_unauth&#39;
* %Service opnieuw gestart: rabbitmq-server%&#39;) als &#39;rmq_service_start&#39;
* &#39;%response [mislukt] for node [rabbit@host1]: nodedown%&#39;) als &#39;rmq_node1_down&#39;
* &#39;%response [mislukt] for node [rabbit@host2]: nodedown%&#39;) als &#39;rmq_node2_down&#39;
* &#39;%response [mislukt] for node [rabbit@host2]: nodedown%&#39;) als &#39;rmq_node2_down&#39;
* &#39;%Entiteit gewijzigd: exchange/bindings.destination%&#39;) als &#39;rmq_entity_modified
* &#39;%Entiteit gewijzigd: exchange/bindings.destination%&#39;) als &#39;rmq_entity_modified
* &#39;%Entiteit gewijzigd: queue/Exclusive%&#39;) als &#39;rmq_entity_created_q_Exclusive&#39;&#39;%Entiteit gewijzigd: queue/auto_delete%&#39;) als &#39;rmq_entity_q_delete&#39;
* &#39;%Entiteit gewijzigd: queue/durable%&#39;) als &#39;rmq_entity_modified_q_durable&#39;
* &#39;%Entiteit gewijzigd: version/management%&#39;) als &#39;rmq_entity_modified_ver_mgt&#39;
* &#39;%Entiteit gewijzigd: version/management%&#39;) als &#39;rmq_entity_modified_ver_mgt&#39;

## [!UICONTROL RabbitMQ service start/stop signals]

![Start/stop-signalen van de RabbitMQ-service](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Dit frame toont [!DNL RabbitMQ] de de dienstbegin/stopsignalen die tijdens het geselecteerde tijdkader voorkwamen:

* &#39;%RabbitMQ wordt gevraagd te stoppen...%&#39;) als &#39;rabbitmq_stop&#39;
* &#39;%startkonijnMQ%&#39;) als &#39;rabbitmq_start&#39;

## [!UICONTROL RabbitMQ errors]

![RabbitMQ-fouten](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Dit frame toont [!DNL RabbitMQ] fouten die tijdens de geselecteerde tijdlijn zijn opgetreden:

* &#39;%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_health checks%&#39;} as &#39;exit_timeout&#39;
* &#39;%client onverwachts gesloten TCP connection%&#39;) als &#39;client_closed_tcp_conn&#39;
* &#39;%at undefined exit with reason shutdown in context shutdown_error%&#39;) as &#39;undef_exit&#39;
* &#39;%Connection try from disallowed node%&#39;) as &#39;disallowed_node&#39;
* &#39;%closing AMQP connection%&#39;) als &#39;rmq_err_amqp_conn&#39;

## [!UICONTROL RabbitMQ node status]

![Status van RabbitMQ-knooppunt](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* &#39;%konbit op knooppunt rabbit@host1 down%&#39;) als &#39;rmq_node1_down&#39;
* &#39;%konbit op knooppunt rabbit@host2 down%&#39;) als &#39;rmq_node2_down&#39;
* &#39;%konbit op knooppunt rabbit@host3 down%&#39;) als &#39;rmq_node3_down&#39;
* &#39;%rabbit op knooppunt rabbit@host1 up%&#39;) als &#39;rmq_node1_up&#39;
* &#39;%rabbit op knooppunt rabbit@host2 up%&#39;) als &#39;rmq_node2_up&#39;
* &#39;%rabbit op knooppunt rabbit@host3 up%&#39;) als &#39;rmq_node3_up&#39;

## [!UICONTROL RabbitMQ Message High-Level Summary status by Queue]

![De status van de Samenvatting van het Bericht op hoog niveau van RabbitMQ door Rij](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

De **[!UICONTROL RabbitMQ Message High-Level Summary status by Queue]** grafiek toont het aantal gepubliceerde berichten door [!DNL RabbitMQ] wachtrij voor het geselecteerde tijdframe.

## [!UICONTROL RabbitMQ Message Detail Summary]

![Overzicht van MQ-berichtgegevens voor konijn](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* &#39;%rapport.ERROR: Cron Job consumer_runner heeft een fout: NOT_FOUND - no queue%&#39;) als &#39;queue_err&#39;
* &#39;%rapport.ERROR: Cron Job consumer_runner heeft een fout: NOT_FOUND - no queue%&#39;) als &#39;queue_err&#39;
* &#39;%authenticated and allowed access to vhost%&#39;) as &#39;auth&#39;
* &#39;%closing AMQP connection%&#39;) als &#39;close_conn&#39;

## [!UICONTROL RabbitMQ Queue Consumption MB]

![RabbitMQ Queue Consumption MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

De **[!UICONTROL RabbitMQ Queue Consumption MB]** grafiek toont het aantal bytes dat door elk wordt verbruikt [!DNL RabbitMQ] een wachtrij over het geselecteerde tijdkader.

## [!UICONTROL RabbitMQ Published Messages by Queue]

![Gepubliceerde Berichten van RabbitMQ door Rij](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

De **[!UICONTROL RabbitMQ Published Messages by Queue]** grafiek toont het aantal bytes dat door elk wordt verbruikt [!DNL RabbitMQ] een wachtrij over het geselecteerde tijdkader.

## [!UICONTROL RabbitMQ Published Message Throughput by Queue]

![Door Wachtrij gepubliceerde berichtendoorvoer van RabbitMQ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

De **[!UICONTROL RabbitMQ Published Message Throughput by Queue]** grafiek geeft het gemiddelde aantal gepubliceerde berichten per seconde weer [!DNL RabbitMQ] een wachtrij over het geselecteerde tijdkader.

## [!UICONTROL RabbitMQ Total Message Throughput by Queue]

![De Totale Doorvoer van het Bericht van RabbitMQ door Rij](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

De **[!UICONTROL RabbitMQ Total Message Throughput by Queue]** grafiek toont het gemiddelde totale aantal berichten per seconde [!DNL RabbitMQ] een wachtrij over het geselecteerde tijdkader.

## [!UICONTROL RabbitMQ Consumers by Queue]

![RabbitMQ Consumenten per wachtrij](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

De **[!UICONTROL RabbitMQ Consumers by Queue]** grafiek geeft het gemiddelde totale aantal consumenten per [!DNL RabbitMQ] een wachtrij over het geselecteerde tijdkader.
