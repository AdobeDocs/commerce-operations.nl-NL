---
title: Back-up maken van het bestandssysteem, de media en de database en deze terugdraaien
description: Ga als volgt te werk om een back-up te maken van uw Adobe Commerce-toepassing en deze te herstellen.
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Back-up maken van het bestandssysteem, de media en de database en deze terugdraaien

Met deze opdracht kunt u back-ups maken:

* Het bestandssysteem (behalve `var` - en `pub/static` -mappen)
* De map `pub/media`
* De database

Back-ups worden opgeslagen in de map `var/backups` en kunnen op elk gewenst moment worden hersteld met de opdracht [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) .

Na het steunen, kunt u [ terugschroeven van prijzen ](#rollback) later.

>[!TIP]
>
>Voor Adobe Commerce op de projecten van de wolkeninfrastructuur, zie [ Momentopnamen en reservebeheer ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) in de _gids van de Wolk_.

## Back-ups inschakelen

De back-upfunctie is standaard uitgeschakeld. Om toe te laten, ga het volgende CLI bevel in:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Bericht van de Verdringing:**
>>Back-upfunctionaliteit is vanaf 2.1.16, 2.2.7 en 2.3.0 verouderd. We raden u aan aanvullende back-uptechnologieën en binaire back-uptools (zoals Percona XtraBackup) te onderzoeken.

## Limiet voor geopende bestanden instellen

Terugdraaien naar een vorige back-up kan zonder toezicht mislukken, wat ertoe leidt dat onvolledige gegevens naar het bestandssysteem of de database worden geschreven met de opdracht [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) .

Soms, veroorzaakt een lange vraagkoord de toegewezen geheugenruimte van de gebruiker om uit geheugen wegens teveel recursieve vraag te lopen.

## Openen van bestanden instellen `ulimit`

Wij adviseren plaatsend de open dossiers [`ulimit` ](https://ss64.com/bash/ulimit.html) voor de gebruiker van het dossiersysteem aan een waarde van `65536` of meer.

U kunt dit doen of op de bevellijn of u kunt het een permanent het plaatsen voor de gebruiker door hun shell manuscript uit te geven maken.

Alvorens u verdergaat, als u dit nog niet hebt gedaan, schakelaar aan de [ eigenaar van het dossiersysteem ](../prerequisites/file-system/overview.md).

Opdracht:

```bash
ulimit -s 65536
```

Indien nodig kunt u dit wijzigen in een hogere waarde.

>[!NOTE]
>
>De syntaxis voor geopende bestanden `ulimit` is afhankelijk van de UNIX-shell die u gebruikt. De voorgaande instelling werkt alleen met CentOS en Ubuntu met de Bash-shell. Voor macOS is de juiste instelling echter `ulimit -S 65532` . Raadpleeg een hoofdpagina of referentie van het besturingssysteem voor meer informatie.

U kunt als volgt de waarde in de Bash-shell van de gebruiker instellen:

1. Als u dit nog niet hebt gedaan, schakelaar aan de [ eigenaar van het dossiersysteem ](../prerequisites/file-system/overview.md).
1. Open `/home/<username>/.bashrc` in een teksteditor.
1. Voeg de volgende regel toe:

   ```bash
   ulimit -s 65536
   ```

1. Sla de wijzigingen in `.bashrc` op en sluit de teksteditor af.

>[!WARNING]
>
>We raden u aan geen waarde in te stellen voor [`pcre.recursion_limit` ](https://www.php.net/manual/en/pcre.configuration.php) in het `php.ini` -bestand, omdat dit kan resulteren in onvolledige terugdraaiversies zonder foutmelding.

## Back-up maken

Opdrachtgebruik:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

De opdracht voert de volgende taken uit:

1. Hiermee plaatst u de winkel in de onderhoudsmodus.
1. Voert een van de volgende opdrachtopties uit.

   | Optie | Betekenis | Back-upbestandsnaam en -locatie |
   |--- |--- |--- |
   | `--code` | Hiermee maakt u een back-up van het bestandssysteem (behalve directory&#39;s var en pub/static). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Maak een back-up van de map pub/media. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Maak een back-up van de database. | `var/backups/<timestamp>/_db.sql` |

1. Neemt de opslag uit onderhoudswijze.

Als u bijvoorbeeld een back-up wilt maken van het bestandssysteem en de database,

```bash
bin/magento setup:backup --code --db
```

Berichten die lijken op de volgende weergave:

```
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## Terugdraaien

In deze sectie wordt beschreven hoe u een back-up kunt maken die u eerder hebt gemaakt. U moet de bestandsnaam weten van het back-upbestand dat u wilt herstellen.

Voer de volgende gegevens in om de naam van uw back-ups te zoeken:

```bash
bin/magento info:backups:list
```

De eerste tekenreeks in de naam van het back-upbestand is de tijdstempel.

Als u wilt terugdraaien naar een vorige reservekopie, voert u het volgende in:

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

Als u bijvoorbeeld een back-up van een medium met de naam `1440611839_filesystem_media.tgz` wilt herstellen, voert u

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Berichten die lijken op de volgende weergave:

```
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
