---
title: Referentie aangepaste uitsnijdtaak en uitsnijdgroep
description: Leer hoe u crons aanpast met gebruik van uitsnijdgroepen.
source-git-commit: 24f6d30fb42c2bed6dbb85a4ce7acf9145a74162
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---


# Referentie voor curven aanpassen

Dit onderwerp helpt u opstellings manuscripten en naar keuze bouwgroepen voor douanemodules. Als uw [module](https://glossary.magento.com/module) moet taken periodiek plannen, moet u opstelling een contab voor die module. A _crontab_ is een uitsnijdtaakconfiguratie.

U kunt desgewenst een aangepaste groep instellen, waarmee u onder andere snijtaken die in die groep zijn gedefinieerd, onafhankelijk van andere snijtaken kunt uitvoeren.

Voor een stapsgewijze zelfstudie raadpleegt u [Aangepaste uitsnijdtaken en uitsnijdgroepen configureren (zelfstudie)](custom-cron-tutorial.md).

Zie voor een overzicht van cron-taken [Cron-taken configureren](../cli/configure-cron-jobs.md).

## Cron-groepen configureren

In deze sectie wordt beschreven hoe u desgewenst een uitsnijdgroep voor een aangepaste module kunt maken. Als u dit niet hoeft te doen, gaat u verder met de volgende sectie.

A _uitsnijdgroep_ is een logische groep waarmee u de uitsnede eenvoudig voor meerdere processen tegelijk kunt uitvoeren. De meeste modules van de Handel gebruiken `default` kroongroep; sommige modules gebruiken `index` groep.

Als u een uitsnede voor een aangepaste module implementeert, kunt u ervoor kiezen om de `default` groep of een andere groep.

**Om een hulpgroep voor uw module te vormen**:

Een `crontab.xml` bestand in uw modulemap:

```text
<your component base dir>/<vendorname>/module-<name>/etc/crontab.xml
```

Voor één groep moet het bestand de volgende inhoud hebben:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="<group_name>">
        <job name="<job_name>" instance="<classpath>" method="<method>">
            <schedule><time></schedule>
        </job>
    </group>
</config>
```

Waar:

| Waarde | Beschrijving |
|---|---|
| `group_name` | Naam van de uitsnijdgroep. De groepsnaam hoeft niet uniek te zijn. U kunt de bewerking voor één groep tegelijk uitvoeren. |
| `job_name` | Unieke id voor deze uitsnijdtaak. |
| `classpath` | Klasse die moet worden geïnstantieerd (klassenpad). |
| `method` | Methode in `classpath` om te bellen. |
| `time` | Plan in de vorm van een uitsnede. Laat deze parameter weg als het programma in het gegevensbestand van de Handel of andere opslag wordt bepaald. |

Het resultaat `crontab.xml` twee groepen kunnen er als volgt uitzien :

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="<job_1_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_2_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
    <group id="index">
        <job name="<job_3_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
        <job name="<job_4_name>" instance="<classpath>" method="<method_name>">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

Zie als voorbeeld [Magento_Customer crontab.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Opties voor de groep Uitsnijden opgeven

U kunt een nieuwe groep declareren en de configuratieopties ervan opgeven (die allemaal worden uitgevoerd) [winkelweergave](https://glossary.magento.com/store-view) bereik) via de `cron_groups.xml` bestand, bevindt zich in:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

Hieronder ziet u een voorbeeld van het `cron_groups.xml` bestand:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
    <group id="<group_name>">
        <schedule_generate_every>1</schedule_generate_every>
        <schedule_ahead_for>4</schedule_ahead_for>
        <schedule_lifetime>2</schedule_lifetime>
        <history_cleanup_every>10</history_cleanup_every>
        <history_success_lifetime>60</history_success_lifetime>
        <history_failure_lifetime>600</history_failure_lifetime>
        <use_separate_process>1</use_separate_process>
    </group>
</config>
```

Waar:

| Option | Beschrijving |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | Frequentie (in minuten) die planningen worden geschreven naar de `cron_schedule` tabel. |
| `schedule_ahead_for` | Tijdstip (in minuten) van tevoren dat de schema&#39;s naar de `cron_schedule` tabel. |
| `schedule_lifetime` | Tijdsvenster (in minuten) waarin een uitsnijdtaak moet worden gestart of waarin de uitsnijdtaak als gemist wordt beschouwd (te laat om te worden uitgevoerd). |
| `history_cleanup_every` | Tijd (in minuten) waarop de uitsnijdgeschiedenis in de database wordt bewaard. |
| `history_success_lifetime` | Tijd (in minuten) waarop de record van voltooide snijtaken in de database wordt opgeslagen. |
| `history_failure_lifetime` | Tijd (in minuten) waarop de record van mislukte snijtaken in de database wordt opgeslagen. |
| `use_separate_process` | De taken van deze uitsnijdgroep uitvoeren in een afzonderlijk php-proces |

## Een uitsnijdtaak uitschakelen

Cron-taken hebben geen `disable` functie zoals we die hebben voor [waarnemers](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers). Een uitsnijdtaak kan echter met de volgende techniek worden uitgeschakeld: `schedule` een tijdstip dat een datum bevat die nooit zal plaatsvinden.

Schakel bijvoorbeeld de opdracht `visitor_clean` snijtaak die is gedefinieerd in `Magento_Customer` module:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Om het `visitor_clean` taak uitsnijden, een aangepaste module maken en de `visitor_clean` snijtaak `schedule`:

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

De `visitor_clean` de bouwbaan is ingesteld om 00:00 op 30 februari - op de datum die nooit zal plaatsvinden.
