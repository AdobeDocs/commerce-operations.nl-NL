---
title: Layoutbestanden converteren
description: XML-indelingsbestanden converteren.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# XML-indelingsbestanden converteren

{{file-system-owner}}

Gebruik deze opdracht om uw XML-bestanden voor lay-outs bij te werken als u de overeenkomstige XSLT-stijlpagina (Extensible Stylesheet Language Transformations) bijwerkt.

- [Layout-instructies](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/xml-instructions.html)
- [Bestandstypen layout](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-types.html)

Opdrachtopties:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Waar:

- `{xml file}`—is het volledige pad en de bestandsnaam van een XML-indelingsbestand dat moet worden omgezet (vereist)
- `{xslt stylesheet}`—is het volledige pad en de bestandsnaam van een XSLT-stijlbladbestand dat moet worden gebruikt voor conversie (vereist)
- `-o|--overwrite`—neem deze optie op om het bestaande XML-bestand te overschrijven
