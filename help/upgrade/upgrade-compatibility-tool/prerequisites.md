---
title: '"[!DNL Upgrade Compatibility Tool] Vereisten"'
description: 'Controleer of uw systeem voldoet aan de vereisten die nodig zijn om het [!DNL Upgrade Compatibility Tool] voor uw Adobe Commerce-project. '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] voorwaarden

{{commerce-only}

De minimumvereisten voor het uitvoeren van de [!DNL Upgrade Compatibility Tool] zijn:

| **Vereisten** | **Restricties** |
|----------------|-----------------|
| PHP-versie | >= 7,3 |
| Composer | none |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`, of `>=16.0.0`) |
| Geheugenbeperkingen | Minimaal 2 GB RAM |
| Adobe Commerce Access-toetsen | none |
| Adobe Commerce | none |

U kunt de [!DNL Upgrade Compatibility Tool] in verschillende besturingssystemen (Windows wordt niet ondersteund). U hoeft de [!DNL Upgrade Compatibility Tool] waar uw Adobe Commerce-exemplaar zich bevindt.

Het is noodzakelijk [!DNL Upgrade Compatibility Tool] om toegang te hebben tot de broncode van de instantie Adobe Commerce. U kunt de toepassing bijvoorbeeld op de ene server installeren en deze op de Adobe Commerce-installatie op een andere server plaatsen. Zie de [installeren](../upgrade-compatibility-tool/install.md) voor meer informatie.

Als u de [!DNL Upgrade Compatibility Tool] voor een Adobe Commerce-exemplaar met grote modules en bestanden kan het nodig zijn dat er veel RAM-geheugen beschikbaar is (ten minste 2 GB). U kunt de `[=MODULE-PATH]` in uw opdracht om de modulepadmap op te geven om problemen te voorkomen die te wijten zijn aan een lage geheugenbeperking:

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

Waar de argumenten als volgt zijn:

- `<dir>`: Adobe Commerce-installatiemap.
- `[=MODULE-PATH]`: Specifieke modulepad.
