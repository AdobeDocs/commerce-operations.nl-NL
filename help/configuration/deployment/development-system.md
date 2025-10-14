---
title: Installatie van ontwikkelsysteem
description: Leer hoe u een ontwikkelingssysteem instelt voor de Commerce-toepassing.
exl-id: 242e9a38-2eb2-4090-8f59-3fd588f7ad3a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Installatie van ontwikkelsysteem

U kunt een willekeurig aantal ontwikkelingssystemen hebben, op voorwaarde dat het volgende geldt voor alle systemen:

- Ze werken allemaal met Commerce 2.2 of hoger
- Alle Commerce-code staat onder broncontrole in dezelfde opslagplaats als de bouw- en productiesystemen
- Elk ontwikkelingssysteem zou of [&#x200B; standaardwijze &#x200B;](../bootstrap/application-modes.md#default-mode) of [&#x200B; ontwikkelaarwijze &#x200B;](../bootstrap/application-modes.md#developer-mode) moeten gebruiken
- Het heeft bezit van het dossiersysteem en toestemmingen die zoals in [&#x200B; worden besproken Vereiste voor uw ontwikkeling, bouwt, en productiesystemen &#x200B;](../deployment/technical-details.md).
- Zorg ervoor elk van het volgende __ van broncontrole wordt uitgesloten:

   - `vendor` map (en submappen)
   - `generated` map (en submappen)
   - `pub/static` map (en submappen)
   - `app/etc/env.php` -bestand

- Zorg ervoor `app/etc/config.php` _inbegrepen_ in broncontrole is

Als u Git gebruikt, bevat het bestand `.gitignore` het grootste deel van de voorgaande bestanden. Zie [`.gitignore` verwijzing &#x200B;](../reference/config-reference-gitignore.md).
