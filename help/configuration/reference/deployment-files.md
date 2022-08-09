---
title: Configuratiebestanden voor implementatie
description: Begrijp hoe de configuratiedossiers voor het installeren van de toepassing van de Handel werken.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '513'
ht-degree: 0%

---


# Configuratiebestanden voor implementatie

Adobe Commerce biedt configuratiebestanden waarmee u een component eenvoudig kunt aanpassen en configuratietypen kunt maken om de standaardfunctionaliteit uit te breiden. Het proces van plaatsingsconfiguratie bestaat uit de gedeelde en systeem-specifieke configuratie voor uw installatie. De de plaatsingsconfiguratie van de handel is verdeeld tussen [`app/etc/config.php`](../reference/config-reference-configphp.md) en [`app/etc/env.php`](../reference/config-reference-envphp.md).

- `app/etc/config.php` is de _gedeeld_ configuratiebestand.
Dit bestand bevat een lijst met geïnstalleerde modules, thema&#39;s en taalpakketten. en gedeelde configuratie-instellingen.

   Controleer dit bestand om het te kunnen gebruiken in uw ontwikkelings-, staging- en productiesystemen.

   Vanaf de release van 2.2 kunt u `app/etc/config.php` bestand is geen item meer in het dialoogvenster `.gitignore` bestand.
Dit is gebeurd om [pijplijnimplementatie](../deployment/technical-details.md).

- `app/etc/env.php` bevat instellingen die specifiek zijn voor de installatieomgeving.

Samen, `config.php` en `env.php` worden de &quot;Commerce&quot; genoemd _implementatieconfiguratie_ omdat de bestanden worden gemaakt tijdens de installatie en de toepassing Commerce moet worden gestart.

>[!INFO]
>
>De [!DNL Commerce 2] implementatieconfiguratie vervangt `local.xml` in [!DNL Magento 1.x].

Anders dan andere [moduleconfiguratiebestanden](../reference/module-files.md), wordt de plaatsingsconfiguratie van de Handel geladen in geheugen wanneer tijdens initialisering, niet samengevoegd met andere dossiers, en kan niet worden uitgebreid. (`config.php` en `env.php` worden echter met elkaar samengevoegd.)

## Details over de implementatieconfiguratie

`config.php` en `env.php` zijn PHP-bestanden die een [meerdimensionale associatieve array](https://www.w3schools.com:443/php/php_arrays.asp), wat in feite een hiërarchische rangschikking van configuratieparameters en waarden is.

Op het hoogste niveau van deze array zijn _configuratiesegmenten_. Een segment heeft willekeurige inhoud (een scalaire waarde of een geneste array) die wordt onderscheiden door een willekeurige sleutel. Hierbij worden zowel het sleutelpaar als het waardepaar gedefinieerd door het kader Handel.

[Magento\Framework\App\DeploymentConfig](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/DeploymentConfig.php) verleent slechts toegang tot deze secties maar staat u niet toe om hen uit te breiden.

Op het volgende hiërarchieniveau, worden de punten in elk segment bevolen volgens [module](https://glossary.magento.com/module) Reeksdefinitie, die door de configuratiedossiers van alle modules, behalve gehandicapte modules wordt verkregen samen te voegen.

De volgende secties bespreken de structuur en de inhoud van de plaatsingsconfiguratie:

- Geïnstalleerde modules beheren
- Systeemspecifieke configuratie

## Geïnstalleerde modules beheren

De `config.php` bevat een lijst met geïnstalleerde modules. Adobe Commerce biedt zowel opdrachtregelprogramma&#39;s als hulpprogramma&#39;s voor het beheer van modules (installeren, verwijderen, inschakelen, uitschakelen of upgraden).

Voorbeelden:

- Onderdelen verwijderen: [`bin/magento setup:uninstall`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall.html)
- Status van componenten controleren: [`bin/magento module:status`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#modulestatus)
- Componenten in- of uitschakelen: [`bin/magento module:disable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html#instgde-cli-subcommands-enable-disable), [`bin/magento module:enable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html#instgde-cli-subcommands-enable-disable).

> _config.php_

```php
return array (
  'modules' =>
  array (
    'Magento_Core' => 1,
    'Magento_Store' => 1,
    'Magento_Theme' => 1,
    'Magento_Authorization' => 1,
    'Magento_Directory' => 1,
    'Magento_Backend' => 1,
    'Magento_Backup' => 1,
    'Magento_Eav' => 1,
    'Magento_Customer' => 1,
...
  ),
);
```

De waarde `1` of `0` Hiermee wordt aangegeven of een module is in- of uitgeschakeld.

Uitgeschakelde modules worden niet erkend door de toepassing van de Handel; met andere woorden, zij nemen niet deel aan het samenvoegen van configuraties, aan afhankelijkheidsinjectie, gebeurtenissen, plug-ins, enzovoort. Uitgeschakelde modules wijzigen het [storefront](https://glossary.magento.com/storefront) of [Beheer](https://glossary.magento.com/admin) en beïnvloedt het verpletteren niet.

Het enige praktische verschil tussen een uitgeschakelde module en een afwezige module in de codebasis is dat een uitgeschakelde module door de autoloader wordt gevonden, en zijn klassen en constanten zijn beschikbaar voor hergebruik in andere code.