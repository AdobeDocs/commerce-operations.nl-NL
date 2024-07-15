---
title: Instellingen voor gegevensmigratie
description: Leer hoe te beginnen migrerend montages van Magento 1 aan Magento 2 met  [!DNL Data Migration Tool].
exl-id: 6fc8285a-9f26-48a5-9034-49a6a1b66b40
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Instellingen voor gegevensmigratie

De modus `Settings` migreert winkels, websites en systeemconfiguratie zoals de instellingen voor verzending, betaling en belasting. Volgens onze gegevensmigratie [ orde ](overview.md#migration-order), zou u montages eerst moeten migreren.

Voer de volgende stappen uit om voor te bereiden voordat u begint:

1. Login aan de toepassingsserver als [ eigenaar van het dossiersysteem ](../../../installation/prerequisites/file-system/overview.md).

1. Wijzig de map `/bin` of zorg ervoor dat deze aan uw systeem wordt toegevoegd `PATH` .

>[!NOTE]
>
>Controleer of Magento 2 is geïmplementeerd in de `default` -modus. In de ontwikkelmodus kunnen validatiefouten optreden in het migratiehulpprogramma.


Zie de [ eerste stappen ](overview.md#first-steps) sectie voor meer details.

## De opdracht Instellingen migreren uitvoeren

Voer de volgende handelingen uit om de migratie-instellingen te starten:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Waarbij:

* `[-r|--reset]` is een optioneel argument dat de migratie vanaf het begin start. U kunt dit argument gebruiken voor het testen van migratie

* `[-a|--auto]` is een optioneel argument dat voorkomt dat de migratie stopt wanneer integriteitscontroles worden uitgevoerd.

* `{<path to config.xml>}` is het absolute bestandsysteempad naar het [`config.xml`](../configure.md#configure-migration-in-vendor-folder) -bestand van het migratiehulpprogramma. Dit argument is vereist.

>[!NOTE]
>
>Dit bevel migreert niet alle configuratiemontages. Controleer alle instellingen in Magento 2 Admin voordat u verdergaat.


Het `Migration completed` -bericht wordt weergegeven nadat de instellingen zijn overgebracht.

## Aangepaste migratieregels configureren

U kunt de systeemconfiguraties negeren, hernoemen of wijzigen tijdens het migreren van instellingen. Hiervoor geeft u uw aangepaste regels op in het `settings.xml` -bestand.

1. Login aan de toepassingsserver als, of schakelaar aan, de [ eigenaar van het dossiersysteem ](../../../installation/prerequisites/file-system/overview.md).

1. Ga naar de volgende map:

   ```bash
   cd <your application 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Als de toepassing bijvoorbeeld is geïnstalleerd in `/var/www/html` , bevindt het bestand `settings.xml.dist` zich in een van de volgende mappen:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Voer de volgende handelingen uit om een `settings.xml` -bestand te maken op basis van het opgegeven voorbeeld:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Breng de gewenste wijzigingen aan in `settings.xml` .

1. Als u de nieuwe naam wilt opgeven van het instellingenbestand voor toewijzing, wijzigt u de tag `<settings_map_file>` in het `path/to/config.xml` -bestand.

Voor meer details, zie de [ de migratiewijze van Montages ](../technical-specification.md#settings-migration-mode) sectie van de 2} specificatie van het Hulpmiddel ](../technical-specification.md).[

## Volgende migratie

* [Gegevens migreren](data.md)
