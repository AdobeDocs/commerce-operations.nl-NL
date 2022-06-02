---
title: '"[!DNL Upgrade Compatibility Tool] rapporten"'
description: Voer de volgende stappen uit [!DNL Upgrade Compatibility Tool] op uw Adobe Commerce-project.
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Rapporten

{{commerce-only}

Op grond van de analyse [!DNL Upgrade Compatibility Tool] Hiermee exporteert u een rapport dat een lijst bevat met problemen voor elk bestand en waarin de ernst, foutcode en beschrijving van de fout worden aangegeven.

Zie het onderstaande voorbeeld:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Controleer de [Verwijzing naar foutbericht](../upgrade-compatibility-tool/error-messages.md) voor meer informatie.

Het verslag bevat ook een gedetailleerde samenvatting die het volgende laat zien:

- *Huidige versie*: de versie die momenteel is geïnstalleerd.
- *Doelversie*: de versie waarnaar u wilt upgraden.
- *Uitvoeringstijd*: de hoeveelheid tijd die de analyse nodig had om het rapport op te stellen (mm:ss).
- *Modules die update vereisen*: het percentage modules dat compatibiliteitsproblemen bevat en moet worden bijgewerkt.
- *Bestanden die moeten worden bijgewerkt*: het percentage bestanden dat compatibiliteitsproblemen bevat en moet worden bijgewerkt.
- *Totaal aantal kritieke fouten*: het aantal aangetroffen kritieke fouten.
- *Totaal aantal fouten*: het aantal gevonden fouten.
- *Totaal aantal waarschuwingen*: het aantal gevonden waarschuwingen.

Zie het onderstaande voorbeeld:

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>Standaard worden de [!DNL Upgrade Compatibility Tool] het rapport wordt in twee verschillende formaten geëxporteerd: `json` en `html`.

## JSON-bestand

Het JSON-bestand bevat exact dezelfde informatie als wordt weergegeven bij uitvoer:

- Lijst van de geïdentificeerde problemen.
- Samenvatting van de analyse.

Voor elke ondervonden kwestie, verstrekt het rapport gedetailleerde informatie zoals de ernst en de beschrijving van het probleem.

Voer de volgende handelingen uit om dit rapport naar een andere uitvoermap te exporteren:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Waar de argumenten als volgt zijn:

- `<dir>`: Adobe Commerce-installatiemap.
- `[=JSON-OUTPUT-PATH]`: Padmap om het pad te exporteren `.json` uitvoerbestand.

>[!NOTE]
>
>Het standaardpad voor de uitvoermap is `var/output/[TIME]-results.json`.

## HTML-rapport

Het HTML-bestand bevat ook de analysesamenvatting en de lijst met geïdentificeerde problemen. U kunt het rapport van de HTML krijgen terwijl het in werking stellen van het hulpmiddel op een bevel-lijn interface of door [!DNL Site-Wide Analysis Tool].

![HTML-rapport - Samenvatting](../../assets/upgrade-guide/uct-html-summary.png)

U kunt gemakkelijk door de geïdentificeerde kwesties navigeren tijdens [!DNL Upgrade Compatibility Tool] analyse:

![HTML-rapport - Details](../../assets/upgrade-guide/uct-html-details.png)

Het rapport HTML bevat ook vier verschillende grafieken:

- **Modules naar uitgifteernst**: Toont strengheidsverdeling door modules.
- **Bestanden met de ernst van de uitgave**: Hiermee geeft u de verdeling van de ernst per bestand weer.
- **Modules geordend op totaal aantal emissies**: Toont de 10 meest gecompromitteerde modules rekening houdend met waarschuwingen, fouten, en kritieke fouten.
- **Modules met relatieve grootten en problemen**: Hoe meer bestanden een module bevat, hoe groter de cirkel. Hoe meer problemen een module heeft, hoe meer rood de cirkel wordt weergegeven.

Met deze grafieken kunt u (in één oogopslag) de onderdelen identificeren die het meest gecompromitteerd zijn en die waarvoor meer werk nodig is om een upgrade uit te voeren.

![HTML-rapport - Diagrammen](../../assets/upgrade-guide/uct-html-diagrams.png)

U kunt de problemen die in het rapport worden weergegeven, filteren op basis van het minimale niveau van de uitgave. De standaardwaarde is `WARNING`.

In de rechterbovenhoek bevindt zich een vervolgkeuzelijst waarmee u naar wens een andere vervolgkeuzelijst kunt selecteren. De lijst met geïdentificeerde problemen wordt dienovereenkomstig gefilterd.

![Rapport HTML - Vervolgkeuzemogelijkheden](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

Houd er rekening mee dat de problemen met een lager emissieniveau zijn opgelost, maar u krijgt een melding zodat u altijd op de hoogte bent van de geïdentificeerde problemen per module.

De diagrammen worden ook dienovereenkomstig bijgewerkt, met uitzondering van de `Modules with relative sizes and issues`, die met de `min-issue-level` oorspronkelijk ingesteld.

Als u verschillende resultaten wilt zien, zult u het bevel moeten opnieuw in werking stellen die een andere waarde voor het verstrekken van `--min-issue-level` optie.

![Rapport HTML - Bubble Chart Diagram](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Dit rapport exporteren naar een andere uitvoermap:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Waar de argumenten als volgt zijn:

- `<dir>`: installatiemap {site.data.var.ee} .
- `[=HTML-OUTPUT-PATH]`: Padmap om het pad te exporteren `.html` uitvoerbestand.

>[!NOTE]
>
> Het standaardpad voor de uitvoermap is `var/output/[TIME]-results.html`.
