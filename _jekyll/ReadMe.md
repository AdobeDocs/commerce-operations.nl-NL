---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# Overzicht

Dit project bevat verschillende taken voor het automatiseren van verschillende aspecten van de workflow, zoals het genereren van gegevens voor nieuwsfragmenten, het renderen van sjabloonbestanden, het optimaliseren van afbeeldingen en het genereren van kaarten. Hieronder vindt u de beschrijvingen en gebruiksrichtlijnen voor elke taak van Rake die in het Rakefile is gedefinieerd.

## Taken voor Raken

### `render`

Hiermee worden de sjabloonbestanden in de map `_jekyll/templates` weergegeven met gegevens van `_jekyll/_data/` . Het resultaat wordt gevonden in de map `help/includes/templated` .

**Gebruik:**

```sh
rake render
```

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
