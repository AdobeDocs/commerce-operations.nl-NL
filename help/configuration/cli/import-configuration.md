---
title: Gegevens importeren uit configuratiebestanden
description: Adobe Commerce-configuratie-instellingen importeren uit configuratiebestanden.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Configuratieinstellingen importeren

{{file-system-owner}}

Wanneer u een productiesysteem instelt met behulp van Commerce 2.2 [implementatiemodel voor pijpleidingen](../deployment/technical-details.md), moet u _import_ configuratie-instellingen van `config.php` en `env.php` in de database.
Deze instellingen zijn onder andere configuratiepaden en -waarden, websites, winkels, winkelweergaven en thema&#39;s.

Nadat u websites, winkels, weergaven en thema&#39;s hebt geïmporteerd, kunt u productkenmerken maken en deze toepassen op websites, winkels en winkelweergaven op het productiesysteem.

>[!INFO]
>
>De `bin/magento app:config:import` het bevel verwerkt geen configuratie die in omgevingsvariabelen wordt opgeslagen.

## Importeren, opdracht

Voer op uw productiesysteem de volgende opdracht uit om gegevens uit de configuratiebestanden te importeren (`config.php` en `env.php`) aan de database:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

De optionele `[-n, --no-interaction]` markering voor het importeren van gegevens zonder interactie.

Als u `bin/magento app:config:import` zonder de optionele markering moet u de wijzigingen bevestigen.

Als het configuratiebestand bijvoorbeeld één nieuwe website en één nieuwe winkel bevat, wordt het volgende bericht weergegeven:

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Als u wilt doorgaan met importeren, voert u `yes`.

Als de dossiers van de plaatsingsconfiguratie sommige te importeren gegevens bevatten, wordt een bericht gelijkend op het volgende getoond:

```terminal
Start import:
Some information about importing
```

Als de dossiers van de plaatsingsconfiguratie geen te importeren gegevens bevatten, wordt een bericht gelijkend op het volgende getoond:

```terminal
Start import:
Nothing to import
```

## Wat we importeren

In de volgende secties wordt in detail besproken welke gegevens we importeren.

### Systeemconfiguratie

De handel gebruikt direct waarden in `system` in de `config.php` of `env.php` bestanden in plaats van deze in de database te importeren, omdat hiervoor enkele handelingen voor en na de verwerking nodig zijn.

De waarde van het configuratiepad `web/secure/base_url` moet worden gevalideerd met backend-modellen.

#### Achterste modellen

De modellen van de steun zijn het mechanisme om veranderingen in systeemconfiguratie te verwerken.
U definieert backendmodules in `<module_name>/adminhtml/system.xml`.

Alle backend-modellen moeten de [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) klasse.

Wanneer wij achterste modellen invoeren, bewaren wij niet de configuratiewaarden.

### Configuratie van websites, winkels en winkelgroepen

De volgende typen configuraties worden geïmporteerd.
(Deze configuraties staan onder de `scopes` array in `config.php`.)

- `websites`: Configuratie met betrekking tot websites
- `groups`: hiermee wordt de gerelateerde configuratie opgeslagen
- `stores`: verwante configuratie van weergaven opslaan

De voorgaande configuraties kunnen in de volgende modi worden geïmporteerd:

- `create`: `config.php` bevat nieuwe entiteiten (`websites`, `groups`, `stores`) die ontbreken in de productieomgeving
- `update`: `config.php` bevat entiteiten (`websites`, `groups`, `stores`) die verschillen van de productieomgeving
- `delete`: `config.php` doet _niet_ bevatten entiteiten (`websites`, `groups`, `stores`) die aanwezig zijn in de productieomgeving

>[!INFO]
>
>We importeren de hoofdcategorie die aan winkels is gekoppeld niet. U moet een wortelcategorie met een opslag associëren gebruikend Commerce Admin.

### Themaconfiguratie

De themaconfiguratie omvat alle thema&#39;s die in uw systeem van de Handel worden geregistreerd; de gegevens komen direct uit `theme` databasetabel. (Themaconfiguratie bevindt zich in de `themes` array in `config.php`.)

#### Structuur van themagegevens

De sleutel van serie is volledig themaweg: `area` + `theme path`

Bijvoorbeeld, `frontend/Magento/luma`.
`frontend` is gebied en `Magento/luma` is themapad.

De waarde van een array is gegevens over thema: code, titel, pad, bovenliggende id

Volledig voorbeeld:

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _Themaregistratie_. Als een themagegevens zijn gedefinieerd in `config.php` maar de broncode van het thema is niet aanwezig in het bestandssysteem, het thema wordt genegeerd (dat wil zeggen, niet geregistreerd).
>- _Thema verwijderen_. Als een thema niet aanwezig is in `config.php` maar de broncode staat in het bestandssysteem, het thema wordt niet verwijderd.
