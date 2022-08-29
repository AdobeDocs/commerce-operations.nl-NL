---
title: Instellingen voor gegevensmigratie
description: Leer hoe u begint met het migreren van instellingen van Magento 1 naar Magento 2 met de opdracht [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Instellingen voor gegevensmigratie

De `Settings` de wijze migreert winkels, websites, en systeemconfiguratie zoals verschepen, betaling, en belastingmontages. Volgens onze gegevensmigratie [bestellen](overview.md#migration-order), moet u eerst instellingen migreren.

Voer de volgende stappen uit om voor te bereiden voordat u begint:

1. Meld u aan bij de server met uw Magento 2-instantie als [de eigenaar van het bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Wijziging in de Magento 2 `/bin` of zorg ervoor het aan uw systeemPATH wordt toegevoegd.

>[!NOTE]
>
>Zorg ervoor dat Magento 2 wordt geïmplementeerd in `default` in. In de ontwikkelmodus kunnen validatiefouten optreden in het migratiehulpprogramma.


Zie de [eerste stappen](overview.md#first-steps) voor meer informatie.

## De opdracht Instellingen migreren uitvoeren

Voer de volgende handelingen uit om de migratie-instellingen te starten:

```bash
bin/magento migrate:settings [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Waar:

* `[-r|--reset]` is een optioneel argument dat de migratie vanaf het begin start. U kunt dit argument gebruiken voor het testen van migratie

* `[-a|--auto]` is een optioneel argument dat voorkomt dat de migratie stopt wanneer integriteitscontroles worden uitgevoerd.

* `{<path to config.xml>}` is het absolute pad van het bestandssysteem naar het migratiehulpprogramma [`config.xml`](../configure.md#configure-migration-in-vendor-folder) bestand; dit argument is vereist .

>[!NOTE]
>
>Dit bevel migreert niet alle configuratiemontages. Alle instellingen in de Magento 2 controleren [Beheer](https://glossary.magento.com/admin) voordat u verdergaat.


De `Migration completed` bericht wordt weergegeven nadat de instellingen zijn overgebracht.

## Aangepaste migratieregels configureren

U kunt de systeemconfiguraties negeren, hernoemen of wijzigen tijdens het migreren van instellingen. Hiervoor geeft u uw aangepaste regels op in het dialoogvenster `settings.xml` bestand.

1. Meld u aan bij de server met uw Magento 2-instantie als of schakel over naar de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Ga naar de volgende map:

   ```bash
   cd <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<edition-to-edition>
   ```

   Als bijvoorbeeld Magento 2 is geïnstalleerd in `/var/www/html`de `settings.xml.dist` Het bestand bevindt zich in een van de volgende mappen:

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/commerce-to-commerce`

   * `/var/www/html/vendor/magento/data-migration-tool/etc/opensource-to-opensource`

1. Als u een `settings.xml` bestand uit het opgegeven voorbeeld, voert u uit:

   ```bash
   cp settings.xml.dist settings.xml
   ```

1. Breng uw wijzigingen aan in `settings.xml`.

1. Als u de nieuwe naam wilt opgeven van het instellingenbestand voor toewijzing, wijzigt u de optie `<settings_map_file>` in de `path/to/config.xml` bestand.

Zie voor meer informatie de [Modus voor migratie van instellingen](../technical-specification.md#settings-migration-mode) van het gereedschap [specificatie](../technical-specification.md).

## Volgende migratie

* [Gegevens migreren](data.md)
