---
title: Gegevens importeren uit configuratiebestanden
description: Leer hoe u Adobe Commerce-configuratie-instellingen uit configuratiebestanden importeert. Ontdek de plaatsings van de pijpleiding en de processen van de gegevensbestandinvoer.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Configuratieinstellingen importeren

{{file-system-owner}}

Wanneer u opstelling een productiesysteem gebruikend Commerce 2.2 [&#x200B; model van de pijpleidingsplaatsing &#x200B;](../deployment/technical-details.md) gebruikt, moet u __ configuratiemontages van de invoer `config.php` en `env.php` in het gegevensbestand.
Deze instellingen zijn onder andere configuratiepaden en -waarden, websites, winkels, winkelweergaven en thema&#39;s.

Nadat u websites, winkels, weergaven en thema&#39;s hebt geïmporteerd, kunt u productkenmerken maken en deze toepassen op websites, winkels en winkelweergaven op het productiesysteem.

>[!INFO]
>
>De opdracht `bin/magento app:config:import` verwerkt geen configuratie die is opgeslagen in omgevingsvariabelen.

## Importeren, opdracht

Voer in uw productiesysteem de volgende opdracht uit om gegevens uit de configuratiebestanden (`config.php` en `env.php` ) te importeren naar de database:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Gebruik de optionele markering `[-n, --no-interaction]` om gegevens te importeren zonder interactie.

Als u `bin/magento app:config:import` zonder de optionele markering invoert, moet u de wijzigingen bevestigen.

Als het configuratiebestand bijvoorbeeld één nieuwe website en één nieuwe winkel bevat, wordt het volgende bericht weergegeven:

```
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Voer `yes` in om door te gaan met importeren.

Als de dossiers van de plaatsingsconfiguratie sommige te importeren gegevens bevatten, wordt een bericht gelijkend op het volgende getoond:

```
Start import:
Some information about importing
```

Als de dossiers van de plaatsingsconfiguratie geen te importeren gegevens bevatten, wordt een bericht gelijkend op het volgende getoond:

```
Start import:
Nothing to import
```

## Wat we importeren

In de volgende secties wordt in detail besproken welke gegevens we importeren.

### Systeemconfiguratie

Commerce gebruikt rechtstreeks waarden in de `system` -array in de `config.php` - of `env.php` -bestanden in plaats van deze in de database te importeren, omdat hiervoor enkele handelingen voor en na de verwerking nodig zijn.

De waarde van het configuratiepad `web/secure/base_url` moet bijvoorbeeld worden gevalideerd met backend-modellen.

#### Achterste modellen

De modellen van de steun zijn het mechanisme om veranderingen in systeemconfiguratie te verwerken.
U definieert backendmodules in `<module_name>/adminhtml/system.xml` .

Alle achterste modellen moeten de [`Magento\Framework\App\Config\Value` &#x200B;](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) klasse uitbreiden.

Wanneer wij achterste modellen invoeren, bewaren wij niet de configuratiewaarden.

### Configuratie van websites, winkels en winkelgroepen

De volgende typen configuraties worden geïmporteerd.
(Deze configuraties staan onder de array `scopes` in `config.php` .)

- `websites`: configuratie van websites
- `groups`: hiermee wordt de gerelateerde configuratie opgeslagen
- `stores`: verwante configuratie van weergaven opslaan

De voorgaande configuraties kunnen in de volgende modi worden geïmporteerd:

- `create`: `config.php` bevat nieuwe entiteiten (`websites` , `groups` , `stores`) die niet aanwezig zijn in de productieomgeving
- `update`: `config.php` bevat entiteiten (`websites` , `groups` , `stores`) die verschillen van de productieomgeving
- `delete`: `config.php` __ bevat geen entiteiten (`websites`, `groups`, `stores`) die op productiemilieu aanwezig zijn

>[!INFO]
>
>We importeren de hoofdcategorie die aan winkels is gekoppeld niet. U moet een hoofdcategorie aan een winkel koppelen met behulp van Commerce Admin.

### Themaconfiguratie

De themaconfiguratie omvat alle thema&#39;s die in uw Commerce-systeem zijn geregistreerd. De gegevens komen rechtstreeks uit de databasetabel `theme` . (Themaconfiguratie bevindt zich in de `themes` -array in `config.php` .)

#### Structuur van themagegevens

De sleutel van de array is het volledige themapad: `area` + `theme path`

Bijvoorbeeld `frontend/Magento/luma` .
`frontend` is een gebied en `Magento/luma` is een themapad.

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
>- _registratie van het Thema_. Als een themagegevens in `config.php` worden gedefinieerd maar de broncode van het thema niet aanwezig is in het bestandssysteem, wordt het thema genegeerd (dat wil zeggen, niet geregistreerd).
>- _verwijdering van het Thema_. Als een thema niet aanwezig is in `config.php` maar de broncode aanwezig is op het bestandssysteem, wordt het thema niet verwijderd.
