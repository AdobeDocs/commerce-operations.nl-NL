---
title: Amazon-berichtenwachtrij instellen
description: Leer hoe te om Handel te vormen om de dienst van AWS MQ te gebruiken.
exl-id: 463e513f-e8d4-4450-845e-312cbf00d843
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Amazon-berichtenwachtrij instellen

Vanaf Handel 2.4.3, is de Rij van het Bericht van Amazon (MQ) beschikbaar als wolkklaar vervanging voor op-gebouw instanties van de berichtrij.

Als u een wachtrij met berichten in AWS wilt maken, raadpleegt u [Amazon MQ instellen](https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/amazon-mq-setting-up.html) in de _AWS-documentatie_.

## Handel configureren voor AWS MQ

Als u verbinding wilt maken met de AWS MQ-service, configureert u de `queue.amqp` object in het `env.php` bestand.
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

- `host`—De URL voor het AMQP-eindpunt; beschikbaar door op de naam van de makelaar in AWS te klikken (verwijder &quot;https://&quot; en het volgpoortnummer)
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

De standaardconfiguratie voor `InventoryCatalog` publiceert geen berichten naar [!DNL RabbitMQ]; het standaardgedrag is dat de handeling in dezelfde gebruikersthread wordt uitgevoerd. Als u `InventoryCatalog` om berichten te publiceren, laat toe `cataloginventory/bulk_operations/async`. Ga vanuit de beheerder naar **Winkels** > Configuratie > **Catalogus** > **Inventaris** > bulkbewerkingen beheren en instellen  `Run asynchronously`tot **Ja**.

## De wachtrij met berichten testen

Om het bericht te testen dat van de Handel naar [!DNL RabbitMQ]:

1. Aanmelden bij de [!DNL RabbitMQ] webconsole in AWS voor het controleren van wachtrijen.
1. Maak een product in Admin.
1. Maak een inventarisbron.
1. Inschakelen **Winkels** > Configuratie > **Catalogus** > **Inventaris** > Beheer bulkbewerkingen > asynchroon uitvoeren.
1. Ga naar **Catalogus** > Producten. Selecteer het hierboven gemaakte product in het raster en klik op **Inventarisbron toewijzen**.
1. Klikken **Opslaan en sluiten** om het proces te voltooien.

   U moet nu berichten zien in het dialoogvenster [!DNL RabbitMQ] webconsole.

1. Start de `async.operations.all` de consument van de berichtrij.

   ```bash
   bin/magento queue:consumers:start async.operations.all
   ```

Het bericht in de wachtrij wordt nu verwerkt in het dialoogvenster [!DNL RabbitMQ] webconsole.
Controleer of de inventarisbronnen op het product in de Admin zijn gewijzigd.
