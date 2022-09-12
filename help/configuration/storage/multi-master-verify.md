---
title: Gesplitste database verifiëren
description: Leer hoe te om te verifiëren dat een gespleten van de Handel gegevensbestandconfiguratie behoorlijk werkt.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# Gesplitste database verifiëren

{{ee-only}}

{{deprecate-split-db}}

Na configuratie, worden de master gegevensbestanden gevormd als volgt:

- Hoofddatabase voor handel: 369 tabellen
- Handel [aanhalingsteken](https://glossary.magento.com/quote) database: 11 tabellen
- Database van de handel: 55 tabellen

Om te verifiëren dat uw gesplitste gegevensbestanden behoorlijk werken, voer de volgende taken uit en verifieer dat het gegeven aan de gegevensbestandlijsten gebruikend een gegevensbestandhulpmiddel als wordt toegevoegd [fpmyadmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

| Te controleren wat | Controleren |
| -------------- | ------------- |
| quotedatabase werkt | Voeg items toe aan een winkelwagentje. Controleren of er rijen zijn toegevoegd aan de aanhalingsdatabase `quote`, `quote_address`, en `quote_item` tabellen. |
| verkoopdatabase werkt | Een bestelling voltooien (elke betalingsmethode, inclusief cheque/postwissel). Controleer of er rijen zijn toegevoegd aan de verkoopdatabase `sales_order_address`, `sales_order_item`, en `sales_order_payment` tabellen. |

>[!WARNING]
>
>U moet de twee extra gegevensbestandinstanties manueel file. De handel steunt slechts de belangrijkste gegevensbestandinstantie. De [`magento setup:backup --db`](../../installation/tutorials/backup.md) geen back-up maken van de extra tabellen.
