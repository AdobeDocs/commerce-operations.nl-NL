---
source-git-commit: 8b82081057af7d134528988d3f9f7cf53f4d7525
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 5%

---
# Technische documentatie van Adobe Commerce

Wij verwelkomen de bijdragen van onze gemeenschap en van Adobe werknemers van buiten de documentatieteams.

## Adobe Open Source Code of Conduct

Dit project heeft de [Adobe-gedragscode voor open source](code-of-conduct.md) of de [.NET Foundation-gedragscode](https://dotnetfoundation.org/code-of-conduct) overgenomen. Zie het artikel [Bijdragen](contributing.md) voor meer informatie.

## Over uw bijdragen aan Adobe-inhoud

Zie de [Handleiding Adobe Docs Contributor](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Hoe u een bijdrage levert, hangt af van wie u bent en van het soort veranderingen dat u wilt bijdragen:

### Kleine wijzigingen

Als u kleine updates aanbrengt uit uw goedheid, bezoek het artikel en klik op **Bewerken** verbinding in het artikel dat naar de bron GitHub voor het artikel gaat. Dan, gebruik enkel GitHub UI om uw updates te maken. Zie het algemene gedeelte [Handleiding Adobe Docs-contributor](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) voor meer informatie .

Kleine correcties of verduidelijkingen die u ter documentatie en codevoorbeelden in dit antwoord aanbrengt, vallen onder de gebruiksvoorwaarden van de Adobe.

### Belangrijke wijzigingen of nieuwe artikelen van leden van de gemeenschap

Als u deel uitmaakt van de gemeenschap van de Adobe en u een nieuw artikel wilt creëren of belangrijke veranderingen voorleggen, gelieve het lusje van Kwesties in de bewaarplaats van de it te gebruiken om een kwestie voor te leggen om een gesprek met het documentatieteam te beginnen. Zodra u met een plan hebt ingestemd, zult u met een werknemer moeten werken helpen die nieuwe inhoud door een combinatie van het werk in de openbare en privé bewaarplaatsen brengen.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Belangrijkste veranderingen ten opzichte van Adobe werknemers

Als u een technisch schrijver, programmamanager, of ontwikkelaar van het productteam voor een oplossing van Adobe Experience Cloud bent en het uw baan is om aan of auteur technische artikelen bij te dragen, zou u de privé bewaarplaats op moeten gebruiken `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Gereedschappen en instellen

Communautaire contribuanten kunnen GitHub UI voor basishet uitgeven of vork gebruiken het repo om belangrijke bijdragen te leveren.

Zie de [Handleiding Adobe Docs Contributor](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) voor meer informatie.

## Hoe te om prijsdaling te gebruiken om uw onderwerp te formatteren

Alle artikelen in deze repository gebruiken GitHub gearomatiseerde prijsopgave. Als u niet vertrouwd bent met markering, zie:

* [Grondbeginselen van markeringen](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Afdrukbare opmaakmodel](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Sjablonen

De `_jekyll` map bevat sjabloononderwerpen en vereiste elementen.
De sjablonen die de taal voor vloeiende sjablonen gebruiken, bevinden zich in de `_jekyll/templated` als HTML-bestanden.
De `_jekyll/_data` map bevat bestanden met de gegevens die worden gebruikt om de sjablonen te renderen.

Alle sjablonen renderen:

1. Ga naar de `_jekyll` directory.

   cd_jekyll

1. Voer het renderscript uit.

```
_scripts/render
```

> **OPMERKING:** U moet het script uitvoeren vanuit het dialoogvenster `_jekyll` directory.
> **OPMERKING:** U moet Ruby hebben geïnstalleerd om dit manuscript in werking te stellen.

Het script voert rendering uit en schrijft gerenderde sjablonen naar de `help/_includes/templated` directory.

Raadpleeg de documentatie bij Jekyll voor meer informatie over [Gegevensbestanden](https://jekyllrb.com/docs/datafiles), [Vloeibare filters](https://jekyllrb.com/docs/liquid/filters/)en andere functies.
