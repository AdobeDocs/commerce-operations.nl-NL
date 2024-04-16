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

Commerce heeft één bevel-lijn interface (CLI)—`<magento_root>/bin/magento`—dat installatie- en configuratietaken uitvoert, waaronder:

- Commerce installeren (en verwante taken zoals het databaseschema bijwerken, een implementatieconfiguratie maken)
- De cache wissen
- Indexen beheren, inclusief opnieuw indexeren
- Vertaalwoordenboeken en vertaalpakketten maken
- Het produceren van niet bestaande klassen zoals fabrieken en interceptors voor stop-ins, die de configuratie van de gebiedsinjectie voor de objecten manager produceren
- Statische weergavebestanden gebruiken
- CSS maken van minder

De extra voordelen omvatten:

- Eén opdracht (`<magento_root>/bin/magento list`) bevat een lijst met alle beschikbare installatie- en configuratieopdrachten.
- Consistente gebruikersinterface gebaseerd op Symfony.
- CLI is verlengbaar zodat kunnen de derdeontwikkelaars &quot;binnen&quot;aan het &quot;stoppen. Dit heeft het extra voordeel om de het leren kromme van gebruikers te elimineren.
- Opdrachten voor uitgeschakelde modules worden niet weergegeven.

Dit onderwerp bespreekt het vormen van de software van Adobe Commerce gebruikend CLI. Voor informatie over het installeren van Commerce raadpleegt u [Installatiestroom](../../installation/overview.md) in de _Installatiehandleiding_.

## Vereisten

Voordat u begint met het gebruik van de CLI, moet u ervoor zorgen dat:

1. Uw systeem voldoet aan de vereisten die worden besproken in [Systeemvereisten](../../installation/system-requirements.md) in de _Installatiehandleiding_.
1. U hebt alle vereiste taken uitgevoerd die zijn besproken in [Vereisten](../../installation/prerequisites/overview.md) in de _Installatiehandleiding_.
1. Nadat u zich hebt aangemeld bij de Commerce-server, schakelt u over naar een gebruiker die gemachtigd is om naar het Commerce-bestandssysteem te schrijven. Zie [schakelen naar de eigenaar van het bestandssysteem](../../installation/prerequisites/file-system/overview.md) in de _Installatiehandleiding_.

## Opdrachten uitvoeren

Voor bash shell, gebruik de volgende syntaxis om aan de eigenaar van het dossiersysteem over te schakelen en het bevel tezelfdertijd in te gaan:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Als de eigenaar van het bestandssysteem geen aanmeldingen toestaat, kunt u het volgende gebruiken:

```bash
sudo -u <file system owner> <command>
```

**CLI-opdrachten vanuit elke directory uitvoeren**:

Toevoegen `<magento_root>/bin` op uw systeem `PATH`.

Voorbeeld van bash-shell voor CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

U kunt desgewenst het volgende uitvoeren:

- `cd <magento_root>/bin` en uitvoeren als `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` is een submap van de webserverhoofdmap
