---
title: Migratieoverzicht
description: Leer hoe te beginnen migrerend gegevens van Magento 1 aan Magento 2 met  [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Migratieoverzicht

Voordat u de migratie start, moet u alle Magento 1-taken voor uitsnijden stoppen.

Volg tijdens het migratieproces de volgende algemene regels voor een geslaagde migratie:

1. **maak geen** veranderingen in Magento 1 Admin, behalve ordebeheer (het verschepen, het creëren van factuur, en creditmemo&#39;s)
1. **verander geen code**
1. **maak geen** veranderingen in Magento 2 Admin en storefront aan

>[!TIP]
>
>Alle bewerkingen in de Magento 1 storefront zijn toegestaan.

## Voer de [!DNL Data Migration Tool] uit

In deze sectie ziet u hoe u de [!DNL Data Migration Tool] uitvoert om instellingen, gegevens of incrementele wijzigingen te migreren.

### Eerste stappen

1. Meld u aan bij de toepassingsserver of schakel over naar een gebruiker met schrijfmachtigingen naar het bestandssysteem. Zie [ schakelaar aan de eigenaar van het dossiersysteem ](../../../installation/prerequisites/file-system/overview.md).

   Als u bash shell gebruikt, kunt u de volgende syntaxis gebruiken om aan de eigenaar van het dossiersysteem over te schakelen en het bevel tezelfdertijd in te gaan:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Als de eigenaar van het bestandssysteem geen aanmeldingen toestaat, kunt u het volgende doen:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Als u Magento-opdrachten vanuit een willekeurige map wilt uitvoeren, voegt u `<magento_root>/bin` toe aan uw systeem `PATH` .

   Omdat de cellen verschillende syntaxis hebben, raadpleeg een verwijzing als [ unix.stackexchange.com ](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Voorbeeld van bash-shell voor CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   U kunt de opdrachten optioneel op de volgende manieren uitvoeren:

   - `cd <magento_root>/bin` en voer ze als `./magento <command name>` uit
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` is een submap van de hoofdmap van de webserver.

### Opdrachtsyntaxis

Hieronder ziet u een typisch opdrachtvoorbeeld:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Waarbij:

- `<mode>` may be: [`settings`](settings.md) , [`data`](data.md) of [`delta`](delta.md)
- `[-r|--reset]` is een optioneel argument dat de migratie vanaf het begin start. U kunt dit argument gebruiken voor het testen van migratie.
- `[-a|--auto]` is een optioneel argument dat voorkomt dat de migratie stopt wanneer integriteitscontroles worden uitgevoerd.
- `{<path to config.xml>}` is het absolute bestandsysteempad naar `config.xml` . Dit argument is vereist.

>[!NOTE]
>
>Logbestanden worden naar de map `<magento_root>/var/` geschreven.


## Migratievolgorde

Toen wij [!DNL Data Migration Tool] creeerden, veronderstelden wij de volgende opeenvolging van de gegevensoverdracht:

1. [Instellingen](settings.md)
1. [Gegevens](data.md)
1. [Wijzigingen](delta.md)

We raden u ten zeerste aan gegevens in dezelfde volgorde te migreren.
