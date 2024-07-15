---
title: Amazon-berichtenwachtrij instellen
description: Leer hoe u Commerce configureert voor gebruik van de AWS MQ-service.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Amazon-berichtenwachtrij instellen

Vanaf Commerce 2.4.3 is de Rij van het Bericht van Amazon (MQ) beschikbaar als wolkklaar vervanging voor op-gebouw instanties van de berichtrij.

Om een berichtrij op AWS tot stand te brengen, zie [ Vestiging Amazon MQ ](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) in de _documentatie van AWS_.

## Commerce voor AWS MQ configureren

Als u verbinding wilt maken met de AWS MQ-service, configureert u het `queue.amqp` -object in het `env.php` -bestand.
AWS Message Queue vereist een SSL/TLS-verbinding.

```php
'queue' => [
    'amqp' => [
        'host' => '[host]', //example: c-bf4kk1c5-5gcc-4b43-9b9e-8f5b54d234.mq.us-west-3.amazonaws.com
        'port' => 5671,
        'user' => 'yourusername',
        'password' => 'yourpassword',
        'virtualhost' => '/',

        // AWS fields to add
        'ssl' => 'true'
    ]
],
```

Waarbij:

- `host` - De URL voor het AMQP-eindpunt; beschikbaar door op de naam van de makelaar in AWS te klikken (verwijder &quot;https://&quot; en het navolgende poortnummer)
- `user`—De gebruikersnaam die is ingevoerd bij het maken van de AWS MQ-broker
- `password`—De wachtwoordwaarde die wordt ingevoerd bij het maken van de AWS MQ-broker

>[!INFO]
>
>Amazon MQ ondersteunt alleen TLS-verbindingen. Peer-verificatie wordt niet ondersteund.

Nadat u het `env.php` -bestand hebt bewerkt, voert u de volgende opdracht uit om de installatie te voltooien:

```bash
bin/magento setup:upgrade
```

## Hoe Commerce de AWS MQ-service gebruikt

De gebruiker van de `async.operations.all` berichtenwachtrij gebruikt de AMQP-verbinding.

Deze gebruiker leidt elke onderwerpnaam die vooraf aan `async` via de AWS MQ-verbinding staat.

In `InventoryCatalog` zijn er bijvoorbeeld:

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

In de standaardconfiguratie voor `InventoryCatalog` worden geen berichten naar [!DNL RabbitMQ] gepubliceerd. Standaard wordt de handeling in dezelfde gebruikersthread uitgevoerd. Schakel `cataloginventory/bulk_operations/async` in als u wilt weten dat `InventoryCatalog` berichten moet publiceren. Van admin, ga **> Configuratie >** Catalogus **>** Inventaris **> de bulkverrichtingen van Admin `Run asynchronously` aan** ja **plaatsen.**

## De wachtrij met berichten testen

Om het verzenden van berichten van Commerce naar [!DNL RabbitMQ] te testen:

1. Meld u aan bij de [!DNL RabbitMQ] webconsole in AWS om wachtrijen te controleren.
1. Maak een product in Admin.
1. Maak een inventarisbron.
1. Laat **Opslag** > Configuratie > **Catalogus** > **Voorraad** toe > de bulkverrichtingen Admin > asynchroon Looppas.
1. Ga naar **Catalogus** > Producten. Van het net, selecteer het product hierboven wordt gecreeerd en klik **Voorraad Source** toewijzen.
1. Klik **sparen &amp; Sluiten** om het proces te voltooien.

   De berichten worden nu weergegeven in de webconsole van [!DNL RabbitMQ] .

1. Start de consument van de `async.operations.all` wachtrij met berichten.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Het bericht in de wachtrij wordt nu verwerkt in de [!DNL RabbitMQ] -webconsole.
Controleer of de inventarisbronnen op het product in de Admin zijn gewijzigd.
