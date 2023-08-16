---
title: URN-markering
description: Leer hoe te opstellingsURN het benadrukken in uw winde.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Overzicht van de URN-markering

{{file-system-owner}}

Commerce-code verwijst naar alle XSD-schema&#39;s [Uniform Resource Names (URNs)](https://www.ietf.org/rfc/rfc2141.txt). Als u code ontwikkelt en XSDs moet van verwijzingen voorzien, vormt dit bevel uw geïntegreerde ontwikkelaarmilieu (winde) om URNs te erkennen en te benadrukken. Dit maakt ontwikkeling gemakkelijker.

Door gebrek, wordt IDE als PhpStorm niet gevormd om URNs te erkennen en, dientengevolge, tonen zij als volgt in rode tekst:

![PhpStorm is niet geconfigureerd om URN te herkennen](../../assets/configuration/urn-before.png)

De `bin/magento dev:urn-catalog:generate` het bevel laat uw winde (momenteel, slechts Code PhpStorm en Visual Studio) toe om URNs als het volgende te erkennen en te benadrukken:

![IDE inschakelen om URN te herkennen](../../assets/configuration/urn-after.png)

Specifiek, leidt dit bevel tot de volgende configuratie PhpStorm:

![PHPStorm-configuratievoorbeeld](../../assets/configuration/urn-settings.png)

## Vorm uw winde

Momenteel, slechts worden PhpStorm en de Code van Visual Studio gesteund.

Command syntaxis:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Wanneer `<path>` is het pad naar uw PHPStorm `misc.xml` bestand, dat zich ten opzichte van de hoofdmap van het project bevindt. Doorgaans `<path>` is `.idea/misc.xml`.

>[!INFO]
>
>Als u uw &quot;Schema&#39;s en DTD&#39;s&quot; up-to-date wilt houden, voert u de opdracht `dev:urn-catalog:generate` bevel telkens als u toevoegt, wijzigt of verwijdert Handel 2 modules die `*.xsd` bestanden.
