---
title: Voer de hulpprogramma's voor ondersteuning uit
description: Los uw project van de Handel problemen op gebruikend het ingebouwde steunnut.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Voer de hulpprogramma&#39;s voor ondersteuning uit

{{ee-only}}

{{file-system-owner}}

De hulpprogramma&#39;s voor Adobe Commerce-ondersteuning worden ook wel de [Gegevensverzameling](https://docs.magento.com/user-guide/system/support-data-collector.html)—laat gebruikers toe om het oplossen van problemeninformatie over uw systeem te verzamelen die door ons team van de Steun kan worden gebruikt.

Adobe Commerce gebruikt deze back-ups, ook wel _dumpen_,om problemen te analyseren die toegang tot uw code vereisen. Een typisch scenario volgt:

1. Je hebt een probleem met je winkel voor Koophandel en je neemt contact op met Adobe Commerce Support.
1. De steun bepaalt zij moeten uw code of gegevensbestand zien om de kwestie te reproduceren.
1. U maakt een back-up van de code naar een `.tar.gz` bestand.

   Met deze back-up _worden uw mediabestanden uitgesloten om het proces te versnellen en een veel kleiner bestand te maken.

1. U maakt een back-up van de database in een `.tar.gz` bestand.

   Standaard worden gevoelige gegevens gehasht wanneer de back-up wordt gemaakt.

1. U uploadt uw back-ups naar een service voor het delen van bestanden.
1. De steun analyseert uw kwesties zonder uw ontwikkeling of productiemilieu te beïnvloeden.

Het kan enkele minuten duren voordat de hulpprogramma&#39;s zijn voltooid.

## Een back-up van een code maken

Met deze opdracht maakt u een back-up van code en comprimeert u deze in `tar.gz` gebruiken.

{{tip-backup-command}}

Opdrachtopties:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Waarbij:

- **`--name`** geeft de naam van het dump-bestand op (optioneel). Als u deze parameter weglaat, is het dumpdossier tijd en datum-gestempeld.
- **`-o|--output=<path>`** is het absolute pad van het bestandssysteem voor het opslaan van de back-up (vereist).
- **`-l|--logs`** bevat logbestanden (optioneel).

Als u bijvoorbeeld een back-up van een code wilt maken met de naam `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Nadat het bevel voltooit, verstrek de codesteun aan de Steun van Adobe Commerce.

## Een back-up van een database maken

Dit bevel steunt het gegevensbestand van de Handel en perst het binnen `tar.gz` gebruiken.

{{tip-backup-command}}

Opdrachtopties:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Waarbij:

- **`--name`** geeft de naam van het dump-bestand op (optioneel). Als u deze parameter weglaat, is het dumpdossier tijd en datum-gestempeld.
- **`-o|--output=<path>` is het absolute pad van het bestandssysteem voor het opslaan van de back-up (vereist).
- **`-l|--logs`** bevat logbestanden (optioneel).
- **`-i|--ignore-sanitize`** betekent dat gegevens behouden blijven; laat de vlag weg om gevoelige gegevens te hakken die in het gegevensbestand worden opgeslagen wanneer het creëren van de steun (facultatief).

De gevoelige gegevens omvatten klanteninformatie van de volgende gegevensbestandlijsten:

```terminal
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

Nadat het bevel voltooit, verstrek de gegevensbestandsteun aan de Steun van Adobe Commerce.

## Problemen oplossen: hulpprogramma&#39;s en paden weergeven

Wij verstrekken bevelen die wegen aan nut tonen die door de Collector van Gegevens en de bevellijn worden vereist. U kunt deze opdrachten bijvoorbeeld gebruiken als er fouten optreden zoals in de volgende weergave in Beheer of op de opdrachtregel:

```terminal
Utility lsof not found
```

Voer de volgende opdrachten uit in de volgorde waarin de paden worden weergegeven naar de toepassingen die worden gebruikt door de hulpprogramma&#39;s en gegevensverzamelaar:

1. Verandering in uw de installatiemap van de Handel.

   Bijvoorbeeld: `cd /var/www/magento2`

   >[!INFO]
   >
   >De opdrachten worden correct uitgevoerd _alleen_ in uw installatiemap.

1. `bin/magento support:utility:paths` create `<magento_root>/var/support/Paths.php`, waarin de paden naar alle toepassingen worden weergegeven die door het hulpprogramma worden gebruikt.
1. `bin/magento support:utility:check` geeft de paden van het bestandssysteem weer.

Hieronder volgt een monster:

```terminal
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

Als u problemen met het uitvoeren van de programma&#39;s wilt oplossen, moet u ervoor zorgen dat deze toepassingen zijn geïnstalleerd en zich in de gebruikersinterface van de webserver bevinden `$PATH` omgevingsvariabele.
