---
title: Profielen inschakelen
description: Meer informatie over het inschakelen van de MAGE Profiler om met uw analysehulpmiddelen te gebruiken.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# Profielen inschakelen

Met Commerce-profielen kunt u:

- Een ingebouwde analyse inschakelen.

  U kunt een ingebouwde analyse met Commerce gebruiken om taken uit te voeren zoals het analyseren van prestaties. De aard van het profileren hangt van de analytische hulpmiddelen af die u gebruikt. We ondersteunen meerdere indelingen, waaronder HTML. Wanneer u de analyse inschakelt, genereert een `var/profiler.flag` -bestand dat aangeeft dat de analyse is ingeschakeld en dat er configuraties zijn. Als deze optie is uitgeschakeld, wordt dit bestand verwijderd.

- Afhankelijkheidsgrafieken weergeven op een Commerce-pagina.

  A _gebiedsdeelgrafiek_ is een lijst van objecten gebiedsdelen en elk van hun gebiedsdelen, en alle gebiedsdelen voor die gebiedsdelen, etc.

  U zou in de lijst van _ongebruikte gebiedsdelen_ bijzonder geinteresseerd moeten zijn, die voorwerpen zijn die werden gecreeerd omdat zij in één of andere aannemer werden gevraagd, maar nooit werden gebruikt (namelijk werd geen van hun methodes geroepen). Dientengevolge, worden de bewerkertijd en het geheugen besteed om deze gebiedsdelen tot stand te brengen verspild.

Commerce biedt de basisfunctionaliteit in [`Magento\Framework\Profiler`][profiler] .

U kunt profiler toelaten en vormen gebruikend een variabele MAGE_PROFILER of de bevellijn.

## MAGE_PROFILER instellen

U kunt de waarde van `MAGE_PROFILER` op om het even welke die manieren plaatsen in [ worden besproken de waarde van laarzentrekkerparameters ](../bootstrap/set-parameters.md) plaatsen.

`MAGE_PROFILER` ondersteunt de volgende waarden:

- `1` om de uitvoer van een specifieke analyse in te schakelen.

  U kunt een van de volgende waarden gebruiken om een specifieke analyse in te schakelen:

   - `csvfile` gebruikt [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Elke andere waarde (behalve `2`), inclusief een lege waarde, die [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html] gebruikt

- `2` om afhankelijkheidsgrafieken in te schakelen.

  Afhankelijkheidsgrafieken worden doorgaans onder aan een pagina weergegeven. In de volgende afbeelding ziet u een gedeelte van de uitvoer:

  ![ grafieken van de Afhankelijkheid ](../../assets/configuration/depend-graphs.png)

## CLI-opdrachten

U kunt profiler toelaten of onbruikbaar maken gebruikend bevelen CLI:

- `dev:profiler:enable <type>` schakelt de analyse in met `type` van `html` (standaardwaarde) of `csvfile` . Als deze optie is ingeschakeld, wordt een bestand met een vlag `var/profiler.flag` gemaakt.
- `dev:profiler:disable` schakelt de analyse uit. Wanneer deze optie is uitgeschakeld, wordt het vlaggenbestand `var/profiler.flag` verwijderd.

Gebruik de optie Variabele om afhankelijkheidsgrafieken in te schakelen.

**om profiler** toe te laten of onbruikbaar te maken:

1. Meld u aan bij uw Commerce-server.
1. Ga naar de installatiemap van Commerce.
1. Als eigenaar van het bestandssysteem schakelt u de analyse in:

   De analyse inschakelen met behulp van type `html` en een markeringsbestand maken:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   De analyse inschakelen met behulp van type `csvfile` en een markeringsbestand maken:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   De uitvoer wordt opgeslagen naar `<project-root>/var/log/profiler.csv` . `profiler.csv` wordt met voeten getreden op elke pagina verfrist zich.

   U schakelt de analyse uit en verwijdert het markeringsbestand:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
