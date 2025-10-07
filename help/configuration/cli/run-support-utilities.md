---
title: Voer de hulpprogramma's voor ondersteuning uit
description: Leer hoe u hulpprogramma's voor ondersteuning kunt uitvoeren om uw Adobe Commerce-project op te lossen. Ontdek ingebouwde diagnose- en ondersteuningstools.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Voer de hulpprogramma&#39;s voor ondersteuning uit

{{ee-only}}

{{file-system-owner}}

Het nut-ook wordt bedoeld van de Steun van Adobe Commerce als [ Collector van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/support#data-collector) - laat gebruikers toe om het oplossen van problemeninformatie over uw systeem te verzamelen die door ons team van de Steun kan worden gebruikt.

Adobe Commerce gebruikt deze steunen, die ook als _worden bedoeld dumps_, om kwesties te analyseren die toegang tot uw code vereisen. Een typisch scenario volgt:

1. Er is een probleem met uw Commerce-winkel. Neem contact op met de ondersteuning van Adobe Commerce.
1. De steun bepaalt zij moeten uw code of gegevensbestand zien om de kwestie te reproduceren.
1. U maakt een back-up van de code naar een `.tar.gz` -bestand.

   Met deze back-up _worden uw mediabestanden uitgesloten om het proces te versnellen en een veel kleiner bestand te maken.

1. U maakt een back-up van de database naar een `.tar.gz` -bestand.

   Standaard worden gevoelige gegevens gehasht wanneer de back-up wordt gemaakt.

1. U uploadt uw back-ups naar een service voor het delen van bestanden.
1. De steun analyseert uw kwesties zonder uw ontwikkeling of productiemilieu te beïnvloeden.

Het kan enkele minuten duren voordat de hulpprogramma&#39;s zijn voltooid.

## Een back-up van een code maken

Met deze opdracht maakt u een back-up van code en comprimeert u deze in `tar.gz` -indeling.

{{tip-backup-command}}

Opdrachtopties:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Waarbij:

- **`--name`** geeft de naam van het dump-bestand op (optioneel). Als u deze parameter weglaat, is het dumpdossier tijd en datum-gestempeld.
- **`-o|--output=<path>`** is het absolute pad van het bestandssysteem voor het opslaan van de back-up (vereist).
- **`-l|--logs`** bevat logbestanden (optioneel).

Als u bijvoorbeeld een back-up van een code wilt maken met de naam `/var/www/html/magento2/var/log/mycodebackup.tar.gz` :

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Nadat het bevel voltooit, verstrek de codesteun aan de Steun van Adobe Commerce.

## Een back-up van een database maken

Met deze opdracht maakt u een back-up van de Commerce-database en comprimeert u deze in `tar.gz` -indeling.

{{tip-backup-command}}

Opdrachtopties:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Waarbij:

- **`--name`** geeft de naam van het dump-bestand op (optioneel). Als u deze parameter weglaat, is het dumpdossier tijd en datum-gestempeld.
- ** `-o|--output=<path>` is de absolute weg van het dossiersysteem om (vereiste) steun op te slaan.
- **`-l|--logs`** bevat logbestanden (optioneel).
- **`-i|--ignore-sanitize`** betekent dat de gegevens behouden blijven; laat de vlag weg om gevoelige gegevens te hakken die in het gegevensbestand worden opgeslagen wanneer het creëren van de steun (facultatief).

De gevoelige gegevens omvatten klanteninformatie van de volgende gegevensbestandlijsten:

```
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

```
Utility lsof not found
```

Voer de volgende opdrachten uit in de volgorde waarin de paden worden weergegeven naar de toepassingen die worden gebruikt door de hulpprogramma&#39;s en gegevensverzamelaar:

1. Ga naar de installatiemap van Commerce.

   Bijvoorbeeld: `cd /var/www/magento2`

   >[!INFO]
   >
   >De bevelen stellen behoorlijk _slechts_ van uw installatiemap in werking.

1. `bin/magento support:utility:paths` maakt `<magento_root>/var/support/Paths.php` , waarin de paden naar alle toepassingen worden weergegeven die door het hulpprogramma worden gebruikt.
1. `bin/magento support:utility:check` geeft de paden van het bestandssysteem weer.

Hieronder volgt een monster:

```
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

Als u problemen met het uitvoeren van de programma&#39;s wilt oplossen, moet u ervoor zorgen dat deze toepassingen zijn geïnstalleerd en zich in de omgevingsvariabele `$PATH` van de gebruiker van de webserver bevinden.
