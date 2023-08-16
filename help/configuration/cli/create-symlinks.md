---
title: Symlinks naar LESS-bestanden maken
description: Leer hoe u symlinks naar LESS-bestanden maakt.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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
>Tijdens de ontwikkeling, leidt dit bevel tot symlinks voor LESS- dossiers in `var/view_preprocessed` en `pub/static` mappen. Tijdens dit proces worden LESS-bestanden niet in CSS-bestanden gecompileerd.

De volgende lijst verklaart de parameters en de waarden van dit bevel.

| Parameter | Waarde | Vereist? |
| --------- | ----- | --------- |
| `--type` | Type bronbestanden: [minder] (standaard: &quot;less&quot;)<br>Momenteel wordt alleen LESS ondersteund. | Nee |
| `--locale` | Landcode.<br>Als u de lijst met landinstellingscodes wilt weergeven, voert u `bin/magento info:language:list` | Nee |
| `--area` | Gebied (`adminhtml` voor het administratieve gebied, `frontend` voor de opslagplaats). | Nee |
| `--theme` | Themanaam in `<VendorName>/<theme-name>` gebruiken. Bijvoorbeeld: `Magento/blank` of `Magento/backend`. | Nee |
| `<file>` | Lijst met door spaties gescheiden CSS-bestanden die zonder de CSS-extensie naar LESS moeten worden geconverteerd. (Standaard is `css/styles-m css/styles-l`, voor adminhtml type `css/styles css/styles-old`) | Nee |

Als u bijvoorbeeld LESS-bestanden wilt maken voor het voorste thema met de naam `VendorName/themeName` in de `en_US` landinstelling die een CSS-bestand gebruikt met de naam `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`voert u de volgende opdracht in:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

De volgende berichten tonen om succes te bevestigen:

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

LESS-bestanden maken voor de beheerder:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
