---
title: Gereedschap Command-lijn
description: Leer hoe u het Adobe Commerce-opdrachtregelprogramma kunt gebruiken voor installatie- en configuratietaken. Ontdek CLI bevelen en administratieve functies.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '304'
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

Dit onderwerp bespreekt het vormen van de software van Adobe Commerce gebruikend CLI. Voor informatie over het installeren van Commerce, zie [&#x200B; stroom van de Installatie &#x200B;](../../installation/overview.md) in de _gids van de Installatie_.

## Vereisten

Voordat u begint met het gebruik van de CLI, moet u ervoor zorgen dat:

1. Uw systeem voldoet aan de vereisten die in [&#x200B; Vereisten van het Systeem &#x200B;](../../installation/system-requirements.md) in de _gids van de Installatie_ worden besproken.
1. U voltooide alle in de eerste plaats vereiste die taken in [&#x200B; worden besproken Eerste vereisten &#x200B;](../../installation/prerequisites/overview.md) in de _gids van de Installatie_.
1. Nadat u zich hebt aangemeld bij de Commerce-server, schakelt u over naar een gebruiker die gemachtigd is om naar het Commerce-bestandssysteem te schrijven. Zie [&#x200B; schakelaar aan de eigenaar van het dossiersysteem &#x200B;](../../installation/prerequisites/file-system/overview.md) in de _gids van de Installatie_.

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
