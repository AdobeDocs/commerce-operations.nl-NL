---
title: Amazon-berichtenwachtrij instellen
description: Leer hoe te om Handel te vormen om de dienst van AWS MQ te gebruiken.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Amazon-berichtenwachtrij instellen

Vanaf Handel 2.4.3, is de Rij van het Bericht van Amazon (MQ) beschikbaar als wolkklaar vervanging voor op-gebouw instanties van de berichtrij.

Als u een wachtrij met berichten in AWS wilt maken, raadpleegt u [Amazon MQ instellen](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) in de _AWS-documentatie_.

## Handel configureren voor AWS MQ

Voor verbinding met de AWS MQ-service configureert u de `queue.amqp` object in het `env.php` bestand.
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

Waar:

- `host`—de URL voor het AMQP-eindpunt; beschikbaar door op de naam van de makelaar in AWS te klikken (verwijder &quot;https://&quot; en het laatste poortnummer)
- `user`—De gebruikersnaam die wordt ingevoerd bij het maken van de AWS MQ-broker
- `password`—De wachtwoordwaarde die wordt ingevoerd bij het maken van de AWS MQ-broker

>[!INFO]
>
>Amazon MQ ondersteunt alleen TLS-verbindingen. Peer-verificatie wordt niet ondersteund.

Nadat u de `env.php` bestand, voert u de volgende opdracht uit om de installatie te voltooien:

```bash
bin/magento setup:upgrade
```

## Hoe de Handel de dienst van AWS MQ gebruikt

De `async.operations.all` de consument van de berichtrij gebruikt de verbinding van AMQP.

Deze consument leidt om het even welke onderwerpnaam vooraf bepaald met `async` via de AWS MQ-verbinding.

Bijvoorbeeld in `InventoryCatalog` er zijn :

```text
async.V1.inventory.bulk-product-source-assign.POST
async.V1.inventory.bulk-product-source-unassign.POST
async.V1.inventory.bulk-product-source-transfer.POST
```

De standaardconfiguratie voor `InventoryCatalog` publiceert geen berichten naar RabbitMQ; het standaardgedrag moet de actie in de zelfde gebruikersdraad uitvoeren. Als u `InventoryCatalog` om berichten te publiceren, laat toe `cataloginventory/bulk_operations/async`. Ga vanuit de beheerder naar **Winkels** > Configuratie > **Catalogus** > **Inventaris** > bulkbewerkingen beheren en instellen  `Run asynchronously`tot **Ja**.

## De wachtrij met berichten testen

Om bericht te testen dat van Handel naar RabbitMQ wordt verzonden:

1. Meld u aan bij de RabbitMQ-webconsole in AWS om wachtrijen te controleren.
1. Maak een product in Admin.
1. Maak een inventarisbron.
1. Inschakelen **Winkels** > Configuratie > **Catalogus** > **Inventaris** > Beheer bulkbewerkingen > asynchroon uitvoeren.
1. Ga naar **Catalogus** > Producten. Selecteer het hierboven gemaakte product in het raster en klik op **Inventarisbron toewijzen**.
1. Klikken **Opslaan en sluiten** om het proces te voltooien.

   De berichten worden nu weergegeven in de RabbitMQ-webconsole.

1. Start de `async.operations.all` de consument van de berichtrij.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Het bericht in de wachtrij wordt nu verwerkt in de RabbitMQ-webconsole.
Controleer of de inventarisbronnen op het product in de Admin zijn gewijzigd.
