---
title: Layoutbestanden converteren
description: Leer hoe u XML-lay-outbestanden omzet met behulp van opdrachtregelprogramma's van Adobe Commerce. Ontdek XSLT-stijlpagina-updates en bestandsconversieprocessen.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# XML-indelingsbestanden converteren

{{file-system-owner}}

Gebruik deze opdracht om uw XML-bestanden voor lay-outs bij te werken als u de overeenkomstige XSLT-stijlpagina (Extensible Stylesheet Language Transformations) bijwerkt.

- [ instructies van de Lay-out ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [ de dossiertypes van de Lay-out ](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Opdrachtopties:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Waarbij:

- `{xml file}` - is het volledige pad en de bestandsnaam van een XML-indelingsbestand dat moet worden omgezet (vereist)
- `{xslt stylesheet}` - is het volledige pad en de bestandsnaam van een XSLT-stijlbladbestand dat moet worden gebruikt voor conversie (vereist)
- `-o|--overwrite` - neem deze optie op om het bestaande XML-bestand te overschrijven
