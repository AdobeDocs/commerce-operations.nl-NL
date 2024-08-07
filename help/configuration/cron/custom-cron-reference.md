---
title: Referentie aangepaste uitsnijdtaak en uitsnijdgroep
description: Leer hoe u crons aanpast met gebruik van uitsnijdgroepen.
exl-id: 16e342ff-aa94-4e31-8c75-dfea1ef02706
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Referentie voor curven aanpassen

Dit onderwerp helpt u opstellings manuscripten en naar keuze bouwgroepen voor douanemodules. Als uw douanemodule taken periodiek moet plannen, moet u opstelling een contab voor die module. A _crontab_ is een configuratie van de cron baan.

U kunt desgewenst een aangepaste groep instellen, waarmee u onder andere snijtaken die in die groep zijn gedefinieerd, onafhankelijk van andere snijtaken kunt uitvoeren.

Voor een stap-voor-stap leerprogramma, zie [ de banen van de douanecurn en de kantelgroepen (leerprogramma) vormen ](custom-cron-tutorial.md).

Voor een overzicht over kroonbanen, zie [ cron banen ](../cli/configure-cron-jobs.md) vormen.

## Cron-groepen configureren

In deze sectie wordt beschreven hoe u desgewenst een uitsnijdgroep voor een aangepaste module kunt maken. Als u dit niet hoeft te doen, gaat u verder met de volgende sectie.

A _gewassengroep_ is een logische groep die u toelaat om kroon voor meer dan één proces tegelijkertijd gemakkelijk in werking te stellen. De meeste Commerce-modules gebruiken de `default` cron-groep. Sommige modules gebruiken de `index` -groep.

Als u een uitsnede implementeert voor een aangepaste module, kunt u de `default` -groep of een andere groep gebruiken.

**om een gewassengroep voor uw module** te vormen:

Maak een `crontab.xml` -bestand in de modulemap:

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

Waarbij:

| Waarde | Beschrijving |
|---|---|
| `group_name` | Naam van de uitsnijdgroep. De groepsnaam hoeft niet uniek te zijn. U kunt de bewerking voor één groep tegelijk uitvoeren. |
| `job_name` | Unieke id voor deze uitsnijdtaak. |
| `classpath` | Klasse die moet worden geïnstantieerd (klassenpad). |
| `method` | Aanroepmethode in `classpath` . |
| `time` | Plan in de vorm van een uitsnede. Laat deze parameter weg als het programma in het gegevensbestand van Commerce of andere opslag wordt bepaald. |

De resulterende `crontab.xml` met twee groepen kan er als volgt uitzien:

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

Als voorbeeld, zie [ Magento_Customer crontab.xml ](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/crontab.xml).

### Opties voor de groep Uitsnijden opgeven

U kunt een nieuwe groep declareren en de configuratieopties ervan opgeven (die allemaal worden uitgevoerd in het bereik van de winkelweergave) via het `cron_groups.xml` -bestand in:

```text
<your component base dir>/<vendorname>/module-<name>/etc/cron_groups.xml
```

Hieronder ziet u een voorbeeld van het bestand `cron_groups.xml` :

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

Waarbij:

| Optie | Beschrijving |
| -------------------------- | ------------------------------------------------------------------------------------------------------ |
| `schedule_generate_every` | Frequentie (in minuten) die planningen worden geschreven naar de `cron_schedule` tabel. |
| `schedule_ahead_for` | Tijd (in minuten) van tevoren waarop planningen naar de `cron_schedule` -tabel worden geschreven. |
| `schedule_lifetime` | Tijdsvenster (in minuten) waarin een uitsnijdtaak moet worden gestart of waarin de uitsnijdtaak als gemist wordt beschouwd (te laat om te worden uitgevoerd). |
| `history_cleanup_every` | Tijd (in minuten) waarop de uitsnijdgeschiedenis in de database wordt bewaard. |
| `history_success_lifetime` | Tijd (in minuten) waarop de record van voltooide snijtaken in de database wordt opgeslagen. |
| `history_failure_lifetime` | Tijd (in minuten) waarop de record van mislukte snijtaken in de database wordt opgeslagen. |
| `use_separate_process` | De taken van deze uitsnijdgroep uitvoeren in een afzonderlijk php-proces |

## Een uitsnijdtaak uitschakelen

De banen van de kroon hebben geen a `disable` eigenschap zoals wij voor [ waarnemers ](https://developer.adobe.com/commerce/php/development/components/events-and-observers/#observers) hebben. Een uitsnijdtaak kan echter met de volgende techniek worden uitgeschakeld: `schedule` een tijd die een datum bevat die nooit zal voorkomen.

Schakel bijvoorbeeld de `visitor_clean` -snijtaak uit die is gedefinieerd in de module `Magento_Customer` :

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 * * *</schedule>
    </job>
</group>
...
```

Als u de `visitor_clean` uitsnijdtaak wilt uitschakelen, maakt u een aangepaste module en herschrijft u de `visitor_clean` uitsnijdtaak `schedule` :

```xml
...
<group id="default">
    <job name="visitor_clean" instance="Magento\Customer\Model\Visitor" method="clean">
        <schedule>0 0 30 2 *</schedule>
    </job>
</group>
...
```

De `visitor_clean` cron-taak is nu ingesteld op 00:00 op 30 februari - op de datum die nooit zal plaatsvinden.
