---
title: Profielen inschakelen
description: Meer informatie over het inschakelen van de MAGE Profiler om met uw analysehulpmiddelen te gebruiken.
exl-id: a46289ed-16dc-4a72-84ff-85fe825dac11
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Profielen inschakelen

Met de Profilering van de Handel, kunt u:

- Een ingebouwde analyse inschakelen.

   U kunt ingebouwde profiler met Handel gebruiken om taken uit te voeren zoals het analyseren van prestaties. De aard van het profileren hangt van de analytische hulpmiddelen af die u gebruikt. We ondersteunen meerdere indelingen, waaronder HTML. Wanneer u profiler toelaat, `var/profiler.flag` bestand wordt gegenereerd om aan te geven dat profiler is ingeschakeld en configuraties. Als deze optie is uitgeschakeld, wordt dit bestand verwijderd.

- U kunt afhankelijkheidsgrafieken weergeven op een pagina Handel.

   A _afhankelijkheidsgrafiek_ is een lijst van objecten gebiedsdelen en al hun gebiedsdelen, en alle gebiedsdelen voor die gebiedsdelen, etc.

   U zou in het bijzonder geïnteresseerd moeten zijn in de lijst van _ongebruikte afhankelijkheden_, dit zijn objecten die zijn gemaakt omdat ze in een constructor zijn aangevraagd, maar die nooit zijn gebruikt (dat wil zeggen dat geen van de methoden ervan is aangeroepen). Dientengevolge, worden de bewerkertijd en het geheugen besteed om deze gebiedsdelen tot stand te brengen verspild.

De handel verstrekt de basisfunctionaliteit in [`Magento\Framework\Profiler`][profiler].

U kunt profiler toelaten en vormen gebruikend een variabele MAGE_PROFILER of de bevellijn.

## MAGE_PROFILER instellen

U kunt de waarde instellen van `MAGE_PROFILER` op de in [De waarde van bootstrap-parameters instellen](../bootstrap/set-parameters.md).

`MAGE_PROFILER` ondersteunt de volgende waarden:

- `1` om de uitvoer van een specifieke analyse in te schakelen.

   U kunt een van de volgende waarden gebruiken om een specifieke analyse in te schakelen:

   - `csvfile` die [`Magento\Framework\Profiler\Driver\Standard\Output\Csvfile`][csvfile]
   - Andere waarden (behalve `2`), met inbegrip van een lege waarde die gebruikt [`Magento\Framework\Profiler\Driver\Standard\Output\Html`][html]

- `2` om afhankelijkheidsgrafieken in te schakelen.

   Afhankelijkheidsgrafieken worden doorgaans onder aan een pagina weergegeven. In de volgende afbeelding ziet u een gedeelte van de uitvoer:

   ![Afhankelijkheidsgrafieken](../../assets/configuration/depend-graphs.png)

## CLI-opdrachten

U kunt profiler toelaten of onbruikbaar maken gebruikend bevelen CLI:

- `dev:profiler:enable <type>` stelt de analyse in met `type` van `html` (standaardwaarde) of `csvfile`. Indien ingeschakeld, een markeringsbestand `var/profiler.flag` wordt gemaakt.
- `dev:profiler:disable` Schakelt profiler uit. Als deze optie is uitgeschakeld, wordt het markeringsbestand `var/profiler.flag` wordt verwijderd.

Gebruik de optie Variabele om afhankelijkheidsgrafieken in te schakelen.

**De analyse in- of uitschakelen**:

1. Meld u aan bij uw Commerce-server.
1. Verandering in uw de installatiemap van de Handel.
1. Als eigenaar van het bestandssysteem schakelt u de analyse in:

   De analyse met behulp van tekst inschakelen `html` en maak een markeringsbestand:

   ```bash
   bin/magento dev:profiler:enable html
   ```

   De analyse met behulp van tekst inschakelen `csvfile` en maak een markeringsbestand:

   ```bash
   bin/magento dev:profiler:enable csvfile
   ```

   De uitvoer wordt opgeslagen naar `<project-root>/var/log/profiler.csv`. De `profiler.csv` wordt overschreven bij elke pagina die wordt vernieuwd.

   U schakelt de analyse uit en verwijdert het markeringsbestand:

   ```bash
   bin/magento dev:profiler:disable
   ```

<!-- link definitions -->

[csvfile]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Csvfile.php
[html]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler/Driver/Standard/Output/Html.php
[profiler]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Profiler.php
