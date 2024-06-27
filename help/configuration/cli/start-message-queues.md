---
title: Gebruikers in de wachtrij met berichten starten
description: Leer hoe u een consument in een wachtrij met berichten kunt starten.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: cdd752532d17e1168e0aa7d354ec283089d98be3
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---

# Gebruikers in de wachtrij met berichten starten

{{file-system-owner}}

U moet een [berichtwachtrijconsument](../queues/consumers.md) om asynchrone bewerkingen mogelijk te maken, zoals Inventory management-massaacties en REST-bulkobjecten en asynchrone eindpunten. Om B2B functionaliteit toe te laten, moet u veelvoudige consumenten beginnen. De modules van de derde zouden ook kunnen vereisen dat u een douaneconsument begint.

Een lijst met alle consumenten weergeven:

```bash
bin/magento queue:consumers:list
```

Gebruikers in de wachtrij met berichten starten:

```bash
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Na het verbruiken van alle beschikbare berichten, eindigt het bevel. U kunt de opdracht opnieuw handmatig of met een uitsnijdtaak uitvoeren. U kunt ook meerdere instanties van het dialoogvenster `magento queue:consumers:start` bevel om grote berichtrijen te verwerken. U kunt bijvoorbeeld `&` aan het bevel om het op de achtergrond in werking te stellen, aan een herinnering terug te keren, en bevelen te blijven uitvoeren:

```bash
bin/magento queue:consumers:start <consumer_name> &
```

Zie [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) in het Commerce-gedeelte van het dialoogvenster _Verwijzing naar opdrachtregelprogramma&#39;s_ voor details over de bevelopties, parameters, en waarden.

>[!INFO]
>
>De `--multi-process` is aanwezig in het dialoogvenster `queue:consumers:start` , maar om consumenten met parallelle processen te laten werken, configureert u de [`multiple_processes`](../queues/manage-message-queues.md#configuration) optie in `/app/etc/env.php`. Anders, als `queue:consumers:start` wordt aangeroepen met de `--multi-process` werkt het alleen met één thread.
