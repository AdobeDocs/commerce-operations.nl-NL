---
title: Wijzigingen migreren
description: Leer hoe te om slechts gegevens te migreren die sinds uw laatste Magento 1 gegevensmigratie met  [!DNL Data Migration Tool] zijn veranderd.
exl-id: c300c567-77d3-4c25-8b28-a7ae4ab0092e
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Wijzigingen migreren

Het stijgende migratiehulpmiddel installeert lijstlijsten (met prefix `m2_cl_*`) en trekkers (voor het volgen van veranderingen) in Magento 1 gegevensbestand tijdens de [&#x200B; migratie van gegevens &#x200B;](data.md). Deze overzichtstabellen en triggers zijn essentieel om ervoor te zorgen dat u alleen de wijzigingen migreert die u hebt aangebracht in Magento 1 sinds de laatste keer dat u gegevens hebt gemigreerd. Deze wijzigingen zijn:

* Gegevens die klanten via winkel hebben toegevoegd (bestellingen, revisies en wijzigingen in klantprofielen)

* Alle bewerkingen met bestellingen, producten en categorieën in het deelvenster Beheer

>[!NOTE]
>
>Alle andere nieuwe of bijgewerkte entiteiten die via de beheerfunctie worden ingevoerd, zoals kenmerken of CMS-pagina&#39;s, worden niet opgenomen in de incrementele migratie en worden niet gemigreerd.


Voer de volgende stappen uit om voor te bereiden voordat u begint:

1. Login aan de toepassingsserver als [&#x200B; de eigenaar van het dossiersysteem &#x200B;](../../../installation/prerequisites/file-system/overview.md).
1. Wijzig de map `/bin` of zorg ervoor dat deze aan uw systeem wordt toegevoegd `PATH` .

Zie de [&#x200B; eerste stappen &#x200B;](overview.md#first-steps) sectie voor meer details.

## De opdracht Incrementele migratie uitvoeren

Voer de volgende handelingen uit om de migratie van incrementele wijzigingen te starten:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Waarbij:

* `[-r|--reset]` is een optioneel argument dat de migratie vanaf het begin start. U kunt dit argument gebruiken voor het testen van migratie.

* `[-a|--auto]` is een optioneel argument dat voorkomt dat de migratie stopt wanneer integriteitscontroles worden uitgevoerd.

* `{<path to config.xml>}` is het absolute bestandsysteempad naar `config.xml` . Dit argument is vereist.

>[!NOTE]
>
>De stijgende migratie is een ononderbroken proces; het begint automatisch om de 5 seconden opnieuw. Gebruik CTRL-C om het migratieproces af te breken.


## Gegevens migreren die door externe extensies zijn gemaakt

In de modus `Delta` migreert [!DNL Data Migration Tool] gegevens die alleen door Magento eigen modules zijn gemaakt en is deze  niet verantwoordelijk voor de code of extensies die door andere ontwikkelaars zijn gemaakt. Als deze extensies gegevens in de storefront-database hebben gemaakt en de handelaar deze gegevens in Magento 2 wil opnemen, moeten configuratiebestanden van de [!DNL Data Migration Tool] dienovereenkomstig worden gemaakt en gewijzigd.

Als een extensie eigen tabellen heeft en u de wijzigingen voor deltabigratie moet bijhouden, voert u de volgende stappen uit:

1. Voeg de tabellen die moeten worden bijgehouden toe aan het `deltalog.xml` -bestand
1. Een extra delta-klasse maken die de `Migration\App\Step\AbstractDelta` uitbreidt
1. Voeg de naam van de nieuwe klasse toe aan de sectie deltamodus van `config.xml`
