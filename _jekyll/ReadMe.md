---
source-git-commit: 9994f486c38df4c0dc2ff477c48f3e8f3259aa9f
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---
# Overzicht

Dit project bevat verschillende taken voor het automatiseren van verschillende aspecten van de workflow, zoals het genereren van gegevens voor nieuwsfragmenten, het renderen van sjabloonbestanden, het optimaliseren van afbeeldingen en het genereren van kaarten. Hieronder vindt u de beschrijvingen en gebruiksrichtlijnen voor elke taak van Rake die in het Rakefile is gedefinieerd.

## Taken voor Raken

### `render`

Hiermee worden de sjabloonbestanden in de map `_jekyll/templates` weergegeven met gegevens van `_jekyll/_data/` . Het resultaat wordt gevonden in de map `help/includes/templated` . Deze taak onderhoudt automatisch relaties en tijdstempels na rendering.

**Gebruik:**

```sh
rake render
```

**wat het doet:**
- Hiermee wordt het renderscript uitgevoerd om sjabloonbestanden te genereren
- Runs `includes:maintain_all` die moeten worden bijgewerkt, bevatten relaties en tijdstempels
- Zorgt ervoor dat alle include-metagegevens actueel zijn na rendering

### `image_optim`

Hiermee optimaliseert u afbeeldingen in gewijzigde, niet-toegewezen bestanden. Voor andere afbeeldingen gebruikt u het argument `path` om de map of het bestand op te geven.

**Gebruik:**

```sh
rake image_optim
```

**met `path` argument:**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

Hiermee genereert u gegevens voor een nieuwsoverzicht. De standaardtijdlijn is verstreken sinds de laatste update. U kunt een andere periode opgeven met het argument `since` .

**Gebruik:**

```sh
rake whatsnew
```

**met `since` argument:**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

Genereert gegevens voor een nieuwssamenvatting op Beste praktijken. De standaardtijdlijn is verstreken sinds de laatste update. U kunt een andere periode opgeven met het argument `since` .

**Gebruik:**

```sh
rake whatsnew_bp
```

**met `since` argument:**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Genereert een kaart met Azure-gebieden. Het invoergegevensbestand moet in `_jekyll/tmp/azure-regions.json` worden geplaatst. Het resultaat wordt gevonden in `_jekyll/tmp/azure-regions.svg` . Merk op dat u Python, [ PyGMT ](https://www.pygmt.org/latest/install.html) nodig hebt, en [ pdf2svg ](https://formulae.brew.sh/formula/pdf2svg) geïnstalleerd.

**Gebruik:**

```sh
rake azure_regions
```

### `includes:maintain_relationships`

Detecteert en werkt het `include-relationships.yml` -bestand bij door alle markeringsbestanden in de map `help` te scannen voor instructies die het patroon gebruiken `{{$include /help/_includes/filename.md}}` . Met deze taak blijven de relaties tussen de hoofdinhoudsbestanden en de bijbehorende opgenomen bestanden automatisch behouden.

**Gebruik:**

```sh
rake includes:maintain_relationships
```

**wat het doet:**
- Leest de lijst met bestaande include-bestanden uit de map `help/_includes` .
- Hiermee doorzoekt u alle hoofdmarkeringsbestanden om te zoeken welke verwijzingen elk bevatten
- Gebruikt het `{{$include /help/_includes/filename.md}}` -patroon om verwijzingen te identificeren
- Het `include-relationships.yml` -bestand wordt bijgewerkt met ontdekte relaties
- Geeft een overzicht van aangebrachte wijzigingen en identificeert include-bestanden zonder referenties

### `includes:maintain_timestamps`

Houdt tijdstempels op door de meest recente tijdstempels voor het wijzigen van het bestand aan de hoofdbestanden toe te voegen. Deze taak leest het `include-relationships.yml` dossier, controleert git geschiedenis voor elk inbegrepen dossier, en voegt of bijwerkt timestamps aan het eind van belangrijkste dossiers toe.

**Gebruik:**

```sh
rake includes:maintain_timestamps
```

**wat het doet:**
- Lading omvat relaties van `include-relationships.yml`
- Voor elk hoofdbestand zoekt u de meest recente datum voor vastlegging tussen de include-bestanden
- Hiermee voegt u HTML-opmerkingen toe of werkt u deze bij met tijdstempels aan het einde van hoofdbestanden
- Gebruikt de indeling: `<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- Verstrekt gedetailleerde output die toont welke dossiers werden gecontroleerd en hun timestamps

**output van het Voorbeeld:**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

Een handige taak die zowel `includes:maintain_relationships` als `includes:maintain_timestamps` op volgorde uitvoert. Dit is de aanbevolen manier om relaties en tijdstempels te behouden.

**Gebruik:**

```sh
rake includes:maintain_all
```

### `unused_includes`

Zoekt naar include-bestanden in de map `help/_includes` die niet worden genoemd door markeringsbestanden. Zo kunt u zwevende include-bestanden identificeren die veilig kunnen worden verwijderd.

**Gebruik:**

```sh
rake unused_includes
```

## Beschikbare taken weergeven

Als u alle beschikbare lijntaken met de bijbehorende beschrijvingen wilt weergeven, gebruikt u:

```sh
rake --tasks
```

Voor meer gedetailleerde informatie over een specifieke taak, gebruik:

```sh
rake -T [task_name]
```

## Inclusief beheertaken

Alle taken met betrekking tot include-bestanden worden geordend onder de naamruimte `includes` voor een betere organisatie:

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## Inclusief bestandsindeling voor relaties

In het `include-relationships.yml` -bestand worden de relaties tussen hoofdinhoudsbestanden en de bijbehorende opgenomen bestanden bijgehouden. Dit bestand wordt automatisch onderhouden door de `maintain_include_relationships` -taak, die relaties detecteert door bestaande include-bestanden te lezen en hoofdbestanden te zoeken die ernaar verwijzen.

**structuur van het Dossier:**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**Gebieden:**
- `metadata.last_updated`: tijdstempel van de laatste update
- `metadata.total_relationships`: Totaal aantal hoofdbestanden met include-bestanden
- `metadata.auto_discovered`: geeft aan dat het bestand automatisch is gegenereerd
- `metadata.discovery_date`: Datum waarop relaties voor het eerst werden ontdekt
- `relationships`: Toewijzing van hoofdbestanden aan de opgenomen bestanden

**omvat verklaringsformaat:**
Hoofdinhoudsbestanden gebruiken de volgende syntaxis om andere bestanden op te nemen:

```markdown
{{$include /help/_includes/filename.md}}
```

## Vereisten

- Ruby en Bundler geïnstalleerd.
- Vereiste gems gespecificeerd in Gemfile.
- Python, [ PyGMT ](https://www.pygmt.org/latest/install.html), en [ pdf2svg ](https://formulae.brew.sh/formula/pdf2svg) voor de `azure_regions` taak.

## Instellen

1. Installeer de vereiste onderdelen:

   ```sh
   bundle install
   ```

2. Controleer of Python, PyGMT en pdf2svg zijn geïnstalleerd voor de `azure_regions` -taak. Voor meer details op de opstelling zie documentatie in commentaren in [ _scripts/azure_regions.py ](_scripts/azure_regions.py).
