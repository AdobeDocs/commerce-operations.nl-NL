---
title: Gesplitste database verifiëren
description: Leer hoe u kunt controleren of een gesplitste databaseconfiguratie van Commerce goed werkt.
recommendations: noCatalog
exl-id: 36295240-6521-4f3e-9ea3-f35b73de672d
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Gesplitste database verifiëren

{{ee-only}}

{{deprecate-split-db}}

Na configuratie, worden de hoofdgegevensbestanden gevormd als volgt:

- Hoofddatabase van Commerce: 369 tabellen
- Commerce-quotadatabase: 11 tabellen
- Commerce-verkoopdatabase: 55 tabellen

Om te verifiëren dat uw gespleten gegevensbestanden behoorlijk werken, voer de volgende taken uit en verifieer dat het gegeven aan de gegevensbestandlijsten gebruikend een gegevensbestandhulpmiddel zoals [&#x200B; phpmyadmin &#x200B;](../../installation/prerequisites/optional-software.md#phpmyadmin) wordt toegevoegd:

| Te controleren wat | Controleren |
| -------------- | ------------- |
| quotedatabase werkt | Voeg items toe aan een winkelwagentje. Controleer of er rijen zijn toegevoegd aan de tabellen `quote` , `quote_address` en `quote_item` van de aanhalingsdatabase. |
| verkoopdatabase werkt | Een bestelling voltooien (elke betalingsmethode, inclusief cheque/postwissel). Controleer of er rijen zijn toegevoegd aan de tabellen `sales_order_address` , `sales_order_item` en `sales_order_payment` van de database. |

>[!WARNING]
>
>U moet de twee extra gegevensbestandinstanties manueel file. Commerce maakt alleen een back-up van de hoofddatabase-instantie. De opdrachten [`magento setup:backup --db`](../../installation/tutorials/backup.md) en Admin maken geen back-up van de extra tabellen.
