---
title: Installatie van ontwikkelsysteem
description: Leer hoe u een ontwikkelingssysteem instelt voor de toepassing Commerce.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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

   - `vendor` map (en submappen)
   - `generated` map (en submappen)
   - `pub/static` map (en submappen)
   - `app/etc/env.php` file

- Controleer of `app/etc/config.php` is _inbegrepen_ in broncontrole

Als u Git gebruikt, `.gitignore` bevat het grootste deel van het voorgaande bestand. Zie de [`.gitignore` referentie](../reference/config-reference-gitignore.md).
