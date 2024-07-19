---
title: Symlinks naar LESS-bestanden maken
description: Leer hoe u symlinks naar LESS-bestanden maakt.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Symlinks naar LESS-bestanden maken

{{file-system-owner}}

Symbolen maken met LESS-bestanden:

Opdrachtopties:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Tijdens de ontwikkeling maakt deze opdracht symlinks naar LESS-bestanden in de mappen `var/view_preprocessed` en `pub/static` . Tijdens dit proces worden LESS-bestanden niet in CSS-bestanden gecompileerd.

De volgende lijst verklaart de parameters en de waarden van dit bevel.

| Parameter | Waarde | Vereist? |
| --------- | ----- | --------- |
| `--type` | Type van brondossiers: [ minder ] (gebrek: &quot;minder&quot;) <br> momenteel, is LESS het enige gesteunde dossiertype. | Nee |
| `--locale` | Landcode.<br> Voer `bin/magento info:language:list` in om de lijst met landinstellingscodes weer te geven | Nee |
| `--area` | Gebied (`adminhtml` voor het beheergebied, `frontend` voor de winkelier). | Nee |
| `--theme` | Themanaam in `<VendorName>/<theme-name>` -indeling. Bijvoorbeeld `Magento/blank` of `Magento/backend` . | Nee |
| `<file>` | Lijst met door spaties gescheiden CSS-bestanden die zonder de CSS-extensie naar LESS moeten worden geconverteerd. (De standaardwaarde is `css/styles-m css/styles-l` voor adminhtml-type `css/styles css/styles-old` ) | Nee |

Als u bijvoorbeeld LESS-bestanden wilt maken voor het voorste thema met de naam `VendorName/themeName` in de `en_US` -landinstelling met behulp van een CSS-bestand met de naam `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css` , voert u de volgende opdracht in:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

De volgende berichten tonen om succes te bevestigen:

```
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

LESS-bestanden maken voor de beheerder:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
