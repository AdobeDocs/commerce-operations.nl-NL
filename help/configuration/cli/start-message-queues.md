---
title: Gebruikers in de wachtrij met berichten starten
description: Leer hoe u gebruikers in de wachtrij met berichten kunt starten voor asynchrone bewerkingen in Adobe Commerce. Ontdek consumentenbeheer en B2B-functionaliteit.
exl-id: fd6edb24-8ebe-4b67-8a03-6cc759b60fa8
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Gebruikers in de wachtrij met berichten starten

{{file-system-owner}}

U moet de consument van de a [ rij van de berichtrij ](../queues/consumers.md) beginnen om asynchrone verrichtingen zoals de massaacties van Inventory management en REST bulkgoederen en asynchrone eindpunten toe te laten. Om B2B functionaliteit toe te laten, moet u veelvoudige consumenten beginnen. De modules van de derde zouden ook kunnen vereisen dat u een douaneconsument begint.

Een lijst met alle consumenten weergeven:

```shell
bin/magento queue:consumers:list
```

Gebruikers in de wachtrij met berichten starten:

```shell
bin/magento queue:consumers:start [--max-messages=<value>] [--batch-size=<value>] [--single-thread] [--area-code=<value>] [--multi-process=<value>] <consumer_name>
```

Na het verbruiken van alle beschikbare berichten, eindigt het bevel. U kunt de opdracht opnieuw handmatig of met een uitsnijdtaak uitvoeren. U kunt ook meerdere instanties van de opdracht `magento queue:consumers:start` uitvoeren om grote rijen berichten te verwerken. U kunt bijvoorbeeld `&` aan de opdracht toevoegen om deze op de achtergrond uit te voeren, terug te keren naar een vraag en door te gaan met het uitvoeren van opdrachten:

```shell
bin/magento queue:consumers:start <consumer_name> &
```

Zie [`queue:consumers:start`](../../tools/reference/commerce-on-premises.md#queueconsumersstart) in de sectie van Commerce van de _bevel-lijn hulpmiddelen verwijzing_ voor details over de bevelopties, de parameters, en de waarden.

>[!INFO]
>
>De optie `--multi-process` is aanwezig in de opdracht `queue:consumers:start` , maar als u consumenten met parallelle processen wilt uitvoeren, configureert u de optie [`multiple_processes`](../queues/manage-message-queues.md#configuration) in `/app/etc/env.php` . Als `queue:consumers:start` echter wordt aangeroepen met de optie `--multi-process` , werkt dit alleen met één thread.
