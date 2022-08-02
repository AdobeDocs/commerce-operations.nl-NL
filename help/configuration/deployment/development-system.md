---
title: Installatie van ontwikkelsysteem
description: Leer hoe u een ontwikkelingssysteem instelt voor de toepassing Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Installatie van ontwikkelsysteem

U kunt een willekeurig aantal ontwikkelingssystemen hebben, op voorwaarde dat het volgende geldt voor alle systemen:

- Ze hebben allemaal Commerce 2.2 of hoger
- Alle code van de Handel is onder broncontrole in de zelfde bewaarplaats zoals bouw en productiesystemen
- Elk ontwikkelingssysteem moet [standaardmodus](../bootstrap/application-modes.md#default-mode) of [ontwikkelmodus](../bootstrap/application-modes.md#developer-mode)
- De eigenaar en machtigingen van het bestandssysteem zijn ingesteld zoals beschreven in [Vereiste voor uw ontwikkeling, bouw, en productiesystemen](../deployment/technical-details.md).
- Controleer of alle volgende elementen aanwezig zijn: _uitgesloten_ van broncontrole:

   - `vendor` directory (en subdirectory&#39;s)
   - `generated` directory (en subdirectory&#39;s)
   - `pub/static` directory (en subdirectory&#39;s)
   - `app/etc/env.php` file

- Controleer of `app/etc/config.php` is _inbegrepen_ in broncontrole

Als u Git gebruikt, `.gitignore` bevat het grootste deel van het voorgaande bestand. Zie de [`.gitignore` referentie](../reference/config-reference-gitignore.md).
