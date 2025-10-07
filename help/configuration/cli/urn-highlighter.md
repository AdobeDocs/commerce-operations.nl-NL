---
title: URN-markering
description: Leer hoe u URL-markering kunt instellen in uw IDE for Adobe Commerce-ontwikkeling. Ontdek de configuratie en optimalisering van het XSD-schema.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 0%

---

# Overzicht van de URN-markering

{{file-system-owner}}

De codeverwijzingen van Commerce alle XSD schema&#39;s als [&#x200B; Uniform Namen van het Middel (URNs) &#x200B;](https://www.ietf.org/rfc/rfc2141.txt). Als u code ontwikkelt en XSDs moet van verwijzingen voorzien, vormt dit bevel uw geïntegreerde ontwikkelaarmilieu (winde) om URNs te erkennen en te benadrukken. Dit maakt ontwikkeling gemakkelijker.

Door gebrek, wordt IDE als PhpStorm niet gevormd om URNs te erkennen en, dientengevolge, tonen zij als volgt in rode tekst:

![&#x200B; PhpStorm niet gevormd om URN &#x200B;](../../assets/configuration/urn-before.png) te erkennen

Het `bin/magento dev:urn-catalog:generate` bevel laat uw winde (momenteel, slechts PhpStorm en de Code van Visual Studio) toe om URNs als het volgende te erkennen en te benadrukken:

![&#x200B; laat winde toe om URN &#x200B;](../../assets/configuration/urn-after.png) te erkennen

Specifiek, leidt dit bevel tot de volgende configuratie PhpStorm:

![&#x200B; PhpStorm configuratievoorbeeld &#x200B;](../../assets/configuration/urn-settings.png)

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
