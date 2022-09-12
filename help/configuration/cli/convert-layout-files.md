---
title: Layoutbestanden converteren
description: XML-indelingsbestanden converteren.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# XML-indelingsbestanden converteren

{{file-system-owner}}

Gebruik deze opdracht om uw XML-bestanden voor lay-outs bij te werken als u de overeenkomstige XSLT-stijlpagina (Extensible Stylesheet Language Transformations) bijwerkt.

- [Layout-instructies](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Bestandstypen layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Opdrachtopties:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Waar:

- `{xml file}`—is het volledige pad en de bestandsnaam van een XML-indelingsbestand dat moet worden omgezet (vereist)
- `{xslt stylesheet}`—is het volledige pad en de bestandsnaam van een XSLT-stijlbladbestand dat moet worden gebruikt voor conversie (vereist)
- `-o|--overwrite`—neem deze optie op om het bestaande XML-bestand te overschrijven
