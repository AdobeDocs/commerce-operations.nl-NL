---
title: Migratieoverzicht
description: Leer hoe u begint met het migreren van gegevens van Magento 1 naar Magento 2 met de [!DNL Data Migration Tool].
exl-id: b775ede1-9d1d-49d5-ad0f-763404b48278
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Migratieoverzicht

Voordat u de migratie start, moet u alle Magento 1-banen voor kronen stoppen.

Volg tijdens het migratieproces de volgende algemene regels voor een geslaagde migratie:

1. **Niet gebruiken** Breng wijzigingen aan in de Magento 1 Admin, behalve voor orderbeheer (verzending, het maken van facturen en creditnota&#39;s).
1. **Niet gebruiken** elke code wijzigen
1. **Niet gebruiken** wijzigingen aanbrengen in de Magento 2 Admin en storefront

>[!TIP]
>
>Alle bewerkingen in de opslagruimte Magento 1 zijn toegestaan.

## Voer de [!DNL Data Migration Tool]

In deze sectie ziet u hoe u de [!DNL Data Migration Tool] om instellingen, gegevens of incrementele wijzigingen te migreren.

### Eerste stappen

1. Meld u aan bij de toepassingsserver of schakel over naar een gebruiker met schrijfmachtigingen naar het bestandssysteem. Zie [schakelen naar de eigenaar van het bestandssysteem](../../../installation/prerequisites/file-system/overview.md).

   Als u bash shell gebruikt, kunt u de volgende syntaxis gebruiken om aan de eigenaar van het dossiersysteem over te schakelen en het bevel tezelfdertijd in te gaan:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Als de eigenaar van het bestandssysteem geen aanmeldingen toestaat, kunt u het volgende doen:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Als u Magento-opdrachten vanuit een willekeurige map wilt uitvoeren, voegt u `<magento_root>/bin` op uw systeem `PATH`.

   Omdat de syntaxis van schelpen verschilt, raadpleegt u een referentie zoals [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Voorbeeld van bash-shell voor CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   U kunt de opdrachten optioneel op de volgende manieren uitvoeren:

   - `cd <magento_root>/bin` en uitvoeren als `./magento <command name>`
   - `<magento_root>/bin/magento <command name>`
   - `<magento_root>` is een submap van de hoofdmap van de webserver.

### Opdrachtsyntaxis

Hieronder ziet u een typisch opdrachtvoorbeeld:

```bash
bin/magento migrate:<mode> [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Waar:

- `<mode>` kan: [`settings`](settings.md), [`data`](data.md), of [`delta`](delta.md)
- `[-r|--reset]` is een optioneel argument dat de migratie vanaf het begin start. U kunt dit argument gebruiken voor het testen van migratie.
- `[-a|--auto]` is een optioneel argument dat voorkomt dat de migratie stopt wanneer integriteitscontroles worden uitgevoerd.
- `{<path to config.xml>}` is het absolute pad van het bestandssysteem naar `config.xml`; dit argument is vereist .

>[!NOTE]
>
>Logbestanden worden geschreven naar de `<magento_root>/var/` directory.


## Migratievolgorde

Toen wij [!DNL Data Migration Tool]We hebben de volgende gegevensoverdrachtsequentie gebruikt:

1. [Instellingen](settings.md)
1. [Gegevens](data.md)
1. [Wijzigingen](delta.md)

We raden u ten zeerste aan gegevens in dezelfde volgorde te migreren.
