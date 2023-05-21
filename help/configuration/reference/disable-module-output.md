---
title: Uitvoer van module uitschakelen
description: Leer hoe u de uitvoer van de module uitschakelt.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Uitvoer van module uitschakelen

Door gebrek, worden alle modules gevormd zodat de moduleoutput aan een mening kan worden geschreven. Als u uitvoer uitschakelt, kunt u een module uitschakelen die niet kan worden uitgeschakeld vanwege harde afhankelijkheden.

De `Customer` is afhankelijk van de `Review` -module, zodat de `Review` kan niet worden uitgeschakeld. Als u echter niet wilt dat klanten revisies leveren, kunt u de uitvoer uitschakelen via het dialoogvenster `Review` module.

>[!INFO]
>
>Als een handelaar de Admin gebruikte om moduleoutput in een vorige versie onbruikbaar te maken, moet u het systeem manueel vormen om deze montages te migreren.

Uitschakelen van uitvoer wordt uitgevoerd in de volgende klassen:

- [\Magento\Framework\View\Element\AbstractBlock:toHTML](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>Als u de uitvoer van de module uitschakelt, wordt de module niet uitgeschakeld. De module blijft ingeschakeld en werkt, maar er worden geen blok, pagina of veld op de voorkant of achterkant gerenderd.

## Maak moduleoutput in een pijpleidingsplaatsing onbruikbaar

Om moduleoutput in de pijpleidingsplaatsing of een andere plaatsing, met veelvoudige instanties van de toepassing van de Handel onbruikbaar te maken:

1. Bewerk de `Backend` module `config.xml` bestand.
1. Exporteer de configuratiewijzigingen.

### Bewerk de `Backend` module `config.xml` file

1. Het origineel archiveren `config.xml` bestand.
1. Voeg lijnen toe gelijkend op het volgende `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` rechtstreeks onder de `<default>` element:

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   Hier:

   - `<modules_disable_output>` bevat een lijst met modules.
   - `<Magento_Newsletter></Magento_Newsletter>` Hiermee geeft u op voor welke module uitvoer moet worden uitgeschakeld.
   - `1` is de vlag die output voor de `Magento_Newsletter` module.

Als voorbeeldresultaat van deze configuratie kunnen klanten zich niet meer aanmelden voor nieuwsbrieven.

### De configuratiewijzigingen exporteren

Voer het volgende bevel in werking om de configuratieveranderingen uit te voeren:

```bash
bin/magento app:config:dump
```

De resultaten worden geschreven naar de `<Magento_install_dir>/app/etc/config.php` bestand.

Wis vervolgens de cache om de nieuwe instelling in te schakelen:

```bash
bin/magento cache:clean config
```

Zie [De configuratie exporteren](../cli/export-configuration.md).

## Module-uitvoer uitschakelen in een eenvoudige implementatie

De procedure om moduleoutput op één enkel geval van Handel onbruikbaar te maken is gemakkelijker omdat de veranderingen niet moeten worden verdeeld.

1. Het origineel archiveren `<Magento_install_dir>/app/etc/config.php` bestand.
1. Voeg de `advanced` en `modules_disable_output` secties aan `config.php` bestand (als deze niet bestaan):

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

In dit voorbeeld wordt de uitvoer voor de `Magento_Review` is uitgeschakeld en klanten kunnen producten niet meer controleren.
Als u uitvoer opnieuw wilt inschakelen, stelt u de waarde in op `0`.
