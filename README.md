---
source-git-commit: 7f23a1b123d2ca2e1d116eb66344a67cfe45e409
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 3%

---
# Adobe Commerce - Operationele technische documentatie

We verwelkomen de bijdragen van de gemeenschap en van Adobe-medewerkers van buiten de documentatieteams.

## Koppelingen vooraf toewijzen voor optimalisatie van afbeeldingen

Deze opslagplaats omvat geautomatiseerde haken die vooraf worden vastgelegd en die afbeeldingen optimaliseren voordat ze worden vastgelegd. **Alle contribuanten zouden deze haken** moeten toelaten om verenigbare beeldoptimalisering en verminderde bewaarplaatsgrootte te verzekeren.

### Snelle installatie

Nadat u de opslagplaats hebt gekloond, voert u het volgende uit:

```bash
.githooks/setup-hooks.sh
```

### Wat de haken doen

- Gelaagde afbeeldingsbestanden automatisch detecteren (PNG, JPG, JPEG, GIF, SVG)
- `image_optim` uitvoeren om afbeeldingen te comprimeren en te optimaliseren
- Geoptimaliseerde afbeeldingen automatisch opnieuw plaatsen
- Zorg ervoor dat alle toegewezen images correct zijn geoptimaliseerd

### Voordelen

- Beperkte grootte opslagplaats
- Snellere paginabelasting voor documentatie
- Consistente beeldkwaliteit voor alle contribuanten
- Geen handmatige optimalisatie vereist

Zie [`.githooks/README.md`](.githooks/README.md) voor gedetailleerde installatie-instructies, probleemoplossing en configuratie.

## Adobe Open Source-gedragscode

Dit project heeft de [Adobe-gedragscode voor open source](code-of-conduct.md) of de [.NET Foundation-gedragscode](https://dotnetfoundation.org/code-of-conduct) overgenomen. Zie het artikel [Bijdragen](contributing.md) voor meer informatie.

## Over je bijdragen aan Adobe-inhoud

Zie de [ Gids van de Medewerker van de Docent van Adobe ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Hoe u een bijdrage levert, hangt af van wie u bent en van het soort veranderingen dat u wilt bijdragen:

### Kleine wijzigingen

Als u minder belangrijke updates bijdraagt, bezoek het artikel en klik het terugkoppelen gebied dat bij de bodem van het artikel verschijnt, klik **Gedetailleerde terugkoppelt opties**, en klik dan **Voorstellen en** uitgeven om naar het prijsonderdrukkingsbrondossier op GitHub te gaan. Gebruik GitHub UI om uw updates te maken. Zie de algemene [ de contributorgids van Adobe Docs ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) voor meer informatie.

Kleine correcties of verduidelijkingen die u ter documentatie en codevoorbeelden in dit antwoord aanbrengt, worden behandeld in de gebruiksvoorwaarden van Adobe.

### Belangrijke wijzigingen of nieuwe artikelen van leden van de gemeenschap

Als u deel uitmaakt van de Adobe-community en u een nieuw artikel wilt maken of belangrijke wijzigingen wilt indienen, gebruikt u het tabblad Problemen in de Git-opslagplaats om een uitgave in te dienen die een gesprek met het documentatieteam kan starten. Zodra u met een plan hebt ingestemd, zult u met een werknemer moeten werken helpen die nieuwe inhoud door een combinatie van het werk in de openbare en privé bewaarplaatsen brengen.

### Belangrijke wijzigingen van werknemers van Adobe

Als u een technisch schrijver, programmamanager, of ontwikkelaar van het productteam voor een oplossing van Adobe Experience Cloud bent en het uw baan is om aan of auteur technische artikelen bij te dragen, zou u de privé bewaarplaats bij `https://git.corp.adobe.com/AdobeDocs` moeten gebruiken.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Gereedschappen en instellen

Communautaire contribuanten kunnen GitHub UI voor basishet uitgeven of vork gebruiken het repo om belangrijke bijdragen te leveren.

Zie de [ Gids van de Medewerker van de Docent van Adobe ](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) voor details.

## Hoe te om prijsdaling te gebruiken om uw onderwerp te formatteren

Alle artikelen in deze repository gebruiken GitHub gearomatiseerde prijsopgave. Als u niet vertrouwd bent met markering, zie:

- [ Grondbeginselen van de Prijsverlaging ](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
- [ Afdrukbare prijsdaling ](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Sjablonen

Voor sommige onderwerpen, gebruiken wij gegevensdossiers en malplaatjes om gepubliceerde inhoud te produceren. De gevallen van het gebruik voor deze benadering omvatten:

- Grote sets met programmatisch gegenereerde inhoud publiceren
- Het verstrekken van één enkele bron van waarheid voor klanten over veelvoudige systemen die machine-leesbare dossierformaten, zoals YAML, voor integratie vereisen (b.v., het Hulpmiddel van de Analyse van de Plaats-Brede)

Voorbeelden van sjablooninhoud zijn onder andere:

- [ CLI hulpmiddelverwijzing ](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
- [ de beschikbaarheidstabellen van het Product ](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
- [ de lijsten van de systeemvereisten ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### Sjablooninhoud genereren

In het algemeen, moeten de meeste schrijvers slechts een versieversie aan de de productbeschikbaarheid en lijsten van de systeemvereisten toevoegen. Het onderhoud voor alle andere sjablooninhoud wordt automatisch of beheerd door een toegewezen teamlid. Deze instructies zijn bedoeld voor de meeste schrijvers.

>**NOTA:**
>
>- Voor het genereren van gesjabloonde inhoud moet u op de opdrachtregel in een terminal werken.
>- Ruby moet zijn geïnstalleerd om het renderscript uit te voeren. Zie [_jekyll/.ruby-version ](_jekyll/.ruby-version) voor de vereiste versie.

Zie het volgende voor een beschrijving van de bestandsstructuur voor sjablooninhoud:

- `_jekyll`—Bevat sjablonen voor onderwerpen en vereiste elementen
- `_jekyll/_data`—Bevat de machineleesbare bestandsindelingen die worden gebruikt om sjablonen te renderen
- `_jekyll/templated`—Bevat op HTML gebaseerde sjabloonbestanden die de taal voor vloeiende sjablonen gebruiken
- `help/_includes/templated`—Bevat de gegenereerde uitvoer voor sjablooninhoud in `.md` -bestandsindeling zodat deze kan worden gepubliceerd in Experience League-onderwerpen; het renderscript schrijft automatisch gegenereerde uitvoer naar deze map voor u

Sjablooninhoud bijwerken:

1. Open een gegevensbestand in de map `/jekyll/_data` in de teksteditor. Bijvoorbeeld:

   - [ de beschikbaarheidstabellen van het Product ](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   - [ Eisen van het Systeem lijsten ](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. Gebruik de bestaande YAML-structuur om items te maken.

   Als u bijvoorbeeld een versie van Adobe Commerce wilt toevoegen aan de tabellen voor productbeschikbaarheid, voegt u het volgende toe aan elke vermelding in de secties `extensions` en `services` van het bestand `/jekyll/_data/product-availability.yml` (wijzig zo nodig de versienummers):

   ```yaml
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Navigeer naar de map `_jekyll` .

   ```bash
   cd _jekyll
   ```

1. Genereer sjablooninhoud en schrijf de uitvoer naar de map `help/_includes/templated` .

   ```bash
   rake render
   ```

   >**NOTA:** u moet het manuscript van de `_jekyll` folder in werking stellen. Als dit de eerste keer is om het script uit te voeren, moet u Ruby-afhankelijkheden eerst installeren met de opdracht `bundle install` .

1. Navigeer terug naar de map `root` .

   ```bash
   cd ..
   ```

1. Controleer of de verwachte `help/_includes/templated` -bestanden zijn gewijzigd.

   ```bash
   git status
   ```

   U zou output gelijkend op het volgende moeten zien:

   ```bash
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. Druk op de wijzigingen.

   ```bash
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

Zie de documentatie van Jekyll voor meer details over [ Dossiers van Gegevens ](https://jekyllrb.com/docs/datafiles), [ Vloeiende filters ](https://jekyllrb.com/docs/liquid/filters/), en andere eigenschappen.
