---
title: Uitvoer van module uitschakelen
description: Leer hoe u uitvoer van modules uitschakelt.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: fee09845777e23717e618ac57df4158d6b172d4f
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Uitvoer van module uitschakelen

Door gebrek, worden alle modules gevormd zodat de moduleoutput aan een mening kan worden geschreven. Als u uitvoer uitschakelt, kunt u een module uitschakelen die niet kan worden uitgeschakeld vanwege harde afhankelijkheden.

De module `Customer` is bijvoorbeeld afhankelijk van de module `Review` , zodat de module `Review` niet kan worden uitgeschakeld. Als u echter niet wilt dat klanten revisies leveren, kunt u de uitvoer uitschakelen in de module `Review` .

>[!INFO]
>
>Als een handelaar de Admin gebruikte om moduleoutput in een vorige versie onbruikbaar te maken, moet u het systeem manueel vormen om deze montages te migreren.

Uitschakelen van uitvoer wordt uitgevoerd in de volgende klassen:

- [ \Magento\Framework\View\Element\AbstractBlock::toHtml ](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [ \Magento\Backend\Block\Template::isOutputEnabled ](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>Als u de uitvoer van de module uitschakelt, wordt de module niet uitgeschakeld. De module blijft ingeschakeld en werkt, maar er worden geen blok, pagina of veld op de voorzijde of achterzijde weergegeven.

## Maak moduleoutput in een pijpleidingsplaatsing onbruikbaar

Om moduleoutput in de pijpleidingsplaatsing of een andere plaatsing, met veelvoudige instanties van de toepassing van Commerce onbruikbaar te maken:

1. Bewerk het bestand `Backend` van de module `config.xml` .
1. Exporteer de configuratiewijzigingen.

### Het bestand `Backend` module `config.xml` bewerken

1. Archiveer het oorspronkelijke `config.xml` bestand.
1. Voeg lijnen gelijkend op het volgende aan het `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` dossier, direct onder het `<default>` element toe:

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   Hier:

   - `<modules_disable_output>` bevat een lijst met modules.
   - `<Magento_Newsletter></Magento_Newsletter>` geeft aan voor welke module uitvoer moet worden uitgeschakeld.
   - `1` is de vlag die output voor de `Magento_Newsletter` module onbruikbaar maakt.

Als voorbeeldresultaat van deze configuratie kunnen klanten zich niet meer aanmelden voor nieuwsbrieven.

### De configuratiewijzigingen exporteren

Voer het volgende bevel in werking om de configuratieveranderingen uit te voeren:

```bash
bin/magento app:config:dump
```

De resultaten worden naar het `<Magento_install_dir>/app/etc/config.php` -bestand geschreven.

Wis vervolgens de cache om de nieuwe instelling in te schakelen:

```bash
bin/magento cache:clean config
```

Zie [ de configuratie ](../cli/export-configuration.md) uitvoeren.

## Module-uitvoer uitschakelen in een eenvoudige implementatie

De procedure voor het onbruikbaar maken van moduleoutput op één enkel geval van Commerce is gemakkelijker omdat de veranderingen niet moeten worden verdeeld.

1. Archiveer het oorspronkelijke `<Magento_install_dir>/app/etc/config.php` bestand.
1. Voeg de secties `advanced` en `modules_disable_output` toe aan het `config.php` -bestand (als deze niet bestaan):

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

In dit voorbeeld is de uitvoer voor de module `Magento_Review` uitgeschakeld en kunnen klanten geen producten meer controleren.

### Moduleuitvoer opnieuw inschakelen

Als u de uitvoer weer wilt inschakelen, stelt u de waarde voor de module in op `0` of verwijdert u de regel of module uit het `config.php` -bestand.
