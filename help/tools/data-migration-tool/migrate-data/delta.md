---
title: Wijzigingen migreren
description: Leer hoe u alleen gegevens kunt migreren die zijn gewijzigd sinds de laatste Magento 1-gegevensmigratie met de [!DNL Data Migration Tool].
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# Wijzigingen migreren

Met het gereedschap Incrementele migratie installeert u catalogustabellen (met voorvoegsel) `m2_cl_*`) en triggers (voor het bijhouden van wijzigingen) in de Magento 1-database tijdens de [migratie van gegevens](data.md). Deze overzichtstabellen en trekkers zijn essentieel om ervoor te zorgen dat u slechts de veranderingen migreert die in Magento 1 worden aangebracht sinds de laatste tijd u gegevens migreerde. Deze wijzigingen zijn:

* Gegevens die klanten hebben toegevoegd via [storefront](https://glossary.magento.com/storefront) (gemaakte bestellingen, revisies en wijzigingen in klantprofielen)

* Alle bewerkingen met bestellingen, producten en categorieën in de [Beheer](https://glossary.magento.com/magento-admin) deelvenster

>[!NOTE]
>
>Alle andere nieuwe of bijgewerkte entiteiten die via de beheerder worden ingevoerd, zoals kenmerken of CMS-pagina&#39;s, worden niet opgenomen in de incrementele migratie en worden niet gemigreerd.


Voer de volgende stappen uit om voor te bereiden voordat u begint:

1. Aanmelden bij de toepassingsserver als [de eigenaar van het bestandssysteem](../../../installation/prerequisites/file-system/overview.md).
1. Wijzigen in de `/bin` of zorg ervoor dat het aan uw systeem wordt toegevoegd `PATH`.

Zie de [eerste stappen](overview.md#first-steps) voor meer informatie.

## De opdracht Incrementele migratie uitvoeren

Voer de volgende handelingen uit om de migratie van incrementele wijzigingen te starten:

```bash
bin/magento migrate:delta [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Waar:

* `[-r|--reset]` is een optioneel argument dat de migratie vanaf het begin start. U kunt dit argument gebruiken voor het testen van migratie.

* `[-a|--auto]` is een optioneel argument dat voorkomt dat de migratie stopt wanneer integriteitscontroles worden uitgevoerd.

* `{<path to config.xml>}` is het absolute pad van het bestandssysteem naar `config.xml`; dit argument is vereist .

>[!NOTE]
>
>Incrementele migratie is een continu proces; deze start automatisch om de 5 seconden opnieuw op. Gebruik CTRL-C om het migratieproces af te breken.


## Gegevens migreren die door externe extensies zijn gemaakt

In de `Delta` de [!DNL Data Migration Tool] migreert gegevens die slechts door Magento-modules worden gecreeerd en is niet verantwoordelijk voor de code of de uitbreidingen die door derdeontwikkelaars worden gemaakt. Als deze uitbreidingen gegevens in het storefront gegevensbestand creeerden en de handelaar deze gegevens in Magento 2 willen hebben — config dossiers van [!DNL Data Migration Tool] moeten worden gecreëerd en dienovereenkomstig worden gewijzigd.

Als een [extension](https://glossary.magento.com/extension) heeft zijn eigen lijsten, en u moet hun veranderingen voor delta migratie volgen, deze stappen volgen:

1. Voeg de te volgen tabellen toe aan de `deltalog.xml` file
1. Maak een extra delta-klasse die de `Migration\App\Step\AbstractDelta`
1. Voeg de naam van de nieuwe klasse toe aan de sectie deltamodus van `config.xml`
