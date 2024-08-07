---
title: Gereedschap Command-lijn
description: Gebruik het bevel-lijn van Commerce hulpmiddel om installatie en configuratietaken in werking te stellen.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Gereedschap Command-lijn

Commerce heeft één bevel-lijn interface (CLI) - `<magento_root>/bin/magento` - die installatie en configuratietaken in werking stelt, die omvatten:

- Commerce installeren (en verwante taken zoals het databaseschema bijwerken, een implementatieconfiguratie maken)
- De cache wissen
- Indexen beheren, inclusief opnieuw indexeren
- Vertaalwoordenboeken en vertaalpakketten maken
- Het produceren van niet bestaande klassen zoals fabrieken en interceptors voor stop-ins, die de configuratie van de gebiedsinjectie voor de objecten manager produceren
- Statische weergavebestanden gebruiken
- CSS maken van minder

De extra voordelen omvatten:

- Één enkel bevel (`<magento_root>/bin/magento list`) maakt een lijst van alle beschikbare installatie en configuratiebevelen.
- Consistente gebruikersinterface gebaseerd op Symfony.
- CLI is verlengbaar zodat kunnen de derdeontwikkelaars &quot;binnen&quot;aan het &quot;stoppen. Dit heeft het extra voordeel om de het leren kromme van gebruikers te elimineren.
- Opdrachten voor uitgeschakelde modules worden niet weergegeven.

Dit onderwerp bespreekt het vormen van de software van Adobe Commerce gebruikend CLI. Voor informatie over het installeren van Commerce, zie [ stroom van de Installatie ](../../installation/overview.md) in de _gids van de Installatie_.

## Vereisten

Voordat u begint met het gebruik van de CLI, moet u ervoor zorgen dat:

1. Uw systeem voldoet aan de vereisten die in [ Vereisten van het Systeem ](../../installation/system-requirements.md) in de _gids van de Installatie_ worden besproken.
1. U voltooide alle in de eerste plaats vereiste die taken in [ worden besproken Eerste vereisten ](../../installation/prerequisites/overview.md) in de _gids van de Installatie_.
1. Nadat u zich hebt aangemeld bij de Commerce-server, schakelt u over naar een gebruiker die gemachtigd is om naar het Commerce-bestandssysteem te schrijven. Zie [ schakelaar aan de eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md) in de _gids van de Installatie_.

## Opdrachten uitvoeren

Voor bash shell, gebruik de volgende syntaxis om aan de eigenaar van het dossiersysteem over te schakelen en het bevel tezelfdertijd in te gaan:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Als de eigenaar van het bestandssysteem geen aanmeldingen toestaat, kunt u het volgende gebruiken:

```bash
sudo -u <file system owner> <command>
```

**om bevelen CLI van om het even welke folder** in werking te stellen:

Voeg `<magento_root>/bin` toe aan uw systeem `PATH` .

Voorbeeld van bash-shell voor CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

U kunt desgewenst het volgende uitvoeren:

- `cd <magento_root>/bin` en voer ze als `./magento <command name>` uit
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` is een submap van de webserverhoofdmap
