---
title: URN-markering
description: Leer hoe te opstellingsURN het benadrukken in uw winde.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Overzicht van de URN-markering

{{file-system-owner}}

De codeverwijzingen van Commerce alle XSD schema&#39;s als [ Uniform Namen van het Middel (URNs) ](https://www.ietf.org/rfc/rfc2141.txt). Als u code ontwikkelt en XSDs moet van verwijzingen voorzien, vormt dit bevel uw geïntegreerde ontwikkelaarmilieu (winde) om URNs te erkennen en te benadrukken. Dit maakt ontwikkeling gemakkelijker.

Door gebrek, wordt IDE als PhpStorm niet gevormd om URNs te erkennen en, dientengevolge, tonen zij als volgt in rode tekst:

![ PhpStorm niet gevormd om URN ](../../assets/configuration/urn-before.png) te erkennen

Het `bin/magento dev:urn-catalog:generate` bevel laat uw winde (momenteel, slechts PhpStorm en de Code van Visual Studio) toe om URNs als het volgende te erkennen en te benadrukken:

![ laat winde toe om URN ](../../assets/configuration/urn-after.png) te erkennen

Specifiek, leidt dit bevel tot de volgende configuratie PhpStorm:

![ PhpStorm configuratievoorbeeld ](../../assets/configuration/urn-settings.png)

## Vorm uw winde

Momenteel, slechts worden PhpStorm en de Code van Visual Studio gesteund.

Command syntaxis:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Waar `<path>` het pad naar het PHPStorm `misc.xml` -bestand is, bevindt zich ten opzichte van de hoofdmap van het project. Doorgaans is `<path>` `.idea/misc.xml` .

>[!INFO]
>
>Als u uw schema&#39;s en DTD&#39;s up-to-date wilt houden, voert u de opdracht `dev:urn-catalog:generate` uit telkens wanneer u Commerce 2-modules met `*.xsd` -bestanden toevoegt, wijzigt of verwijdert.
