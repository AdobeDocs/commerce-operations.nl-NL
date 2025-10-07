---
title: Statische weergavebestanden gebruiken
description: Leer hoe u statische weergavebestanden in de productiemodus kunt implementeren in het Adobe Commerce-bestandssysteem. Ontdek plaatsingsbevelen en optimalisatietechnieken.
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---

# Statische weergavebestanden gebruiken

{{file-system-owner}}

Het statische bevel van de meningsdossiers plaatsing laat u toe om statische dossiers aan het het dossiersysteem van Commerce te schrijven wanneer de software van Commerce voor [&#x200B; productiemodus &#x200B;](../bootstrap/application-modes.md#production-mode) wordt geplaatst.

Het termijn _statische meningsdossier_ verwijst naar het volgende:

- &quot;Statisch&quot; betekent dat het bestand voor een site in de cache kan worden geplaatst (het bestand wordt dus niet dynamisch gegenereerd). Voorbeelden zijn afbeeldingen en CSS die zijn gegenereerd op basis van LESS.
- De &quot;Mening&quot;verwijst naar presentatielaag (van MVC).

Statische weergavebestanden bevinden zich in de map `<magento_root>/pub/static` en sommige bestanden worden in de map `<magento_root>/var/view_preprocessed` opgeslagen.

De plaatsing van statische meningsdossiers wordt beïnvloed door toepassingswijzen als volgt:

- [&#x200B; Gebrek &#x200B;](../bootstrap/application-modes.md#default-mode) en [&#x200B; ontwikkelaar &#x200B;](../bootstrap/application-modes.md#developer-mode) wijzen: Commerce produceert hen op bestelling, maar de rest wordt in het voorgeheugen ondergebracht in een dossier voor snelheid van toegang.
- [&#x200B; Productie &#x200B;](../bootstrap/application-modes.md#production-mode) wijze: De statische dossiers worden _niet_ geproduceerd of in het voorgeheugen ondergebracht.

U moet statische meningsdossiers aan het het dossiersysteem van Commerce manueel schrijven gebruikend het bevel in dit onderwerp wordt besproken; daarna kunt u toestemmingen beperken om uw kwetsbaarheid te beperken en toevallig of kwaadwillig het beschrijven van dossiers te verhinderen.

>[!WARNING]
>
>_wijze van de Ontwikkelaar slechts_: Wanneer u installeert of een nieuwe module toelaat, zou het nieuwe JavaScript, CSS, lay-outs, etc. kunnen laden. Als u problemen met statische bestanden wilt voorkomen, moet u de oude bestanden opschonen om ervoor te zorgen dat alle wijzigingen voor de nieuwe module worden doorgevoerd. U kunt gegenereerde statische weergavebestanden op verschillende manieren opschonen. Verwijs naar [&#x200B; Schone statische onderwerp van het dossiergeheime voorgeheugen voor details &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) voor meer informatie.

**om statische meningsdossiers** op te stellen:

1. Login aan de server van Commerce als, of [&#x200B; schakelaar aan de eigenaar van het dossiersysteem &#x200B;](../../installation/prerequisites/file-system/overview.md).
1. Verwijder de inhoud van `<magento_root>/pub/static` , met uitzondering van het `.htaccess` -bestand. Verwijder dit bestand niet.
1. Voer het gereedschap voor het implementeren van statische weergavebestanden `<magento_root>/bin/magento setup:static-content:deploy` uit.

   >[!INFO]
   >
   >Als u het samenvoegen van statische weergavebestanden inschakelt in Admin, moet het directorysysteem van `pub/static` schrijfbaar zijn.

   Opdrachtopties:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

De volgende lijst verklaart de parameters en de waarden van dit bevel.

| Optie | Beschrijving | Vereist? |
| ------ | ----------- | --------- |
| `<languages>` | Ruimte-gescheiden lijst van [&#x200B; ISO-639 &#x200B;](https://www.loc.gov/standards/iso639-2/php/code_list.php) taalcodes waarvoor aan output statische meningsdossiers. (Standaard is dit `en_US` .)<br> vind de lijst door te lopen: `bin/magento info:language:list` | Nee |
| `--language (-l)` | Genereer bestanden alleen voor de opgegeven talen. Als er geen optie is opgegeven, worden standaard bestanden voor alle ISO-639-taalcodes gegenereerd. U kunt de naam van één taalcode tegelijk opgeven. De standaardwaarde is **allen**.<br> Bijvoorbeeld: `--language en_US --language es_ES` | Nee |
| `--exclude-language` | Genereer bestanden voor de opgegeven taalcodes. Als er geen optie is opgegeven, wordt standaard niets uitgesloten. U kunt de naam van één taalcode of een komma-gescheiden lijst van taalcodes specificeren. De standaardwaarde is **niets**. | Nee |
| `--theme <theme>` | Thema&#39;s waarvoor statische inhoud moet worden geïmplementeerd. De standaardwaarde is **allen**.<br> Bijvoorbeeld: `--theme Magento/blank --theme Magento/luma` | Nee |
| `--exclude-theme <theme>` | Thema&#39;s die moeten worden uitgesloten bij het implementeren van statische inhoud. De standaardwaarde is **niets**.<br> Bijvoorbeeld, `--exclude-theme Magento/blank` | Nee |
| `--area (-a)` | Alleen bestanden genereren voor de opgegeven gebieden. Als er geen optie is opgegeven, worden standaard bestanden voor alle gebieden gegenereerd. Geldige waarden zijn `adminhtml` en `frontend` . De standaardwaarde is **allen**.<br> Bijvoorbeeld: `--area adminhtml` | Nee |
| `--exclude-area` | Genereer geen bestanden voor de opgegeven gebieden. Als er geen optie is opgegeven, wordt standaard niets uitgesloten. De standaardwaarde is **niets**. | Nee |
| `--jobs (-j)` | Laat [&#x200B; parallelle verwerking &#x200B;](manage-indexers.md#reindexing-in-parallel-mode) toe gebruikend het gespecificeerde aantal banen. De standaardwaarde is 0 (niet in parallelle processen). De standaardwaarde is **0**. | Nee |
| `--symlink-locale` | Creeer symlinks voor de dossiers van die scènes, die voor plaatsing worden overgegaan, maar geen aanpassingen hebben. | Nee |
| `--content-version=CONTENT-VERSION` | Aangepaste versie van statische inhoud kan worden gebruikt als implementatie op meerdere knooppunten wordt uitgevoerd om ervoor te zorgen dat de versie van statische inhoud identiek is en dat caching correct werkt. | Nee |
| `--no-javascript` | JavaScript-bestanden niet implementeren | Nee |
| `--no-css` | CSS-bestanden niet implementeren. | Nee |
| `--no-less` | Implementeer geen LESS-bestanden. | Nee |
| `--no-images` | Implementeer geen afbeeldingen. | Nee |
| `--no-fonts` | Implementeer geen lettertypebestanden. | Nee |
| `--no-html` | Implementeer geen HTML-bestanden. | Nee |
| `--no-misc` | Andere bestandstypen niet implementeren: MD, JBF, CSV, JSON, TXT, HTC, SWF | Nee |
| `--no-html-minify` | Maak geen minieme HTML-bestanden. | Nee |
| `-s <quick\|standard\|compact>` | De implementatiestrategie definiëren. Gebruik deze opties alleen als u meerdere lokale instellingen hebt.<ul><li>Gebruik de [&#x200B; snelle strategie &#x200B;](static-view-file-strategy.md#quick-strategy) om plaatsingstijd te minimaliseren. Dit is de standaardoptie van het bevel als niet gespecificeerd.</li><li>Gebruik de [&#x200B; standaardstrategie &#x200B;](static-view-file-strategy.md#standard-strategy) om alle statische meningsdossiers voor alle pakketten op te stellen.</li><li>Gebruik de [&#x200B; compacte strategie &#x200B;](static-view-file-strategy.md#compact-strategy) om schijfruimte op de server te besparen.</li></ul> | Nee |
| `--no-parent` | Genereer geen bestanden voor de bovenliggende thema&#39;s van het huidige thema. Het wordt sterk geadviseerd om deze vlag te gebruiken als u niet uitdrukkelijk het ouderthema van het huidige thema gebruikt u probeert op te stellen. Dit verhoogt de snelheid van het proces aanzienlijk. Deze markering is beschikbaar in Commerce 2.4.2 | Nee |
| `--force (-f)` | Bestanden in elke modus implementeren. (standaard kan het hulpprogramma voor het implementeren van statische inhoud alleen worden uitgevoerd in de productiemodus. Gebruik deze optie als u deze wilt uitvoeren in de standaard- of ontwikkelmodus.) | Nee |

>[!INFO]
>
>Als u waarden opgeeft voor zowel `<languages>` als `--language` , heeft `<languages>` voorrang.

## Voorbeelden

Hier volgen enkele voorbeelden van opdrachten.

### Een thema en HTML-miniatuur uitsluiten

De volgende opdracht implementeert statische inhoud voor de Engelse taal (`en_US`) van de VS, sluit het Luma-thema uit dat bij Commerce wordt geleverd en minieme HTML-bestanden niet.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Voorbeelduitvoer:

```
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

Het volgende bevel stelt slechts JavaScript, met 4 banen, met een standaardplaatsingsstrategie op:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

De volgende opdracht implementeert alleen CSS en LESS met 3 taken en een snelle implementatiestrategie:

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Statische weergavebestanden genereren voor één thema en één gebied

Met de volgende opdracht genereert u statische weergavebestanden voor alle talen, alleen het voorste gebied, alleen het Commerce Luma-thema, zonder lettertypen te genereren:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Voorbeelduitvoer:

```
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## Statische weergavebestanden implementeren zonder Commerce te installeren

U zou het plaatsingsproces in een afzonderlijk, niet-productie, milieu kunnen willen in werking stellen, om het even welke bouwstijlprocessen op gevoelige productiemachines te vermijden.

Voer hiertoe de volgende stappen uit:

1. Voer [`bin/magento app:config:dump`](../cli/export-configuration.md) uit om de configuratie vanuit uw productiesysteem te exporteren.
1. Kopieer de geëxporteerde bestanden naar de basis van de niet-productiecode.
1. Statische weergavebestanden gebruiken: `bin/magento setup:static-content:deploy`

## Problemen met het implementatieprogramma voor statische weergavebestanden oplossen

[&#x200B; installeer eerst de software van Commerce &#x200B;](../../installation/overview.md); anders, kunt u niet het statische hulpmiddel van de de plaatsingsdossiers van meningsdossiers in werking stellen.

**Symptom**: De volgende fout wordt getoond wanneer u het statische hulpmiddel van de de plaatsingsdossiers van meningsdossiers in werking stelt:

```
ERROR: You need to install the Commerce application before running this utility.
```

**Oplossing**:

Voer de volgende stappen uit:

1. Installeer de software van Commerce gebruikend de [&#x200B; bevellijn &#x200B;](../../installation/composer.md).
1. Login aan de toepassingsserver als, of [&#x200B; schakelaar aan &#x200B;](../../installation/prerequisites/file-system/overview.md), de eigenaar van het dossiersysteem.
1. Verwijder de inhoud van de map `<app_root>/pub/static` , behalve het bestand `.htaccess` . Verwijder dit bestand niet.
1. Statische weergavebestanden gebruiken: `bin/magento setup:static-content:deploy`

## Tip voor ontwikkelaars die het statische hulpmiddel van de inhoudsimplementatie aanpassen

Wanneer u een aangepaste implementatie van het hulpprogramma voor de implementatie van statische inhoud maakt, gebruikt u alleen het schrijven van atomische bestanden voor bestanden die op de client beschikbaar moeten zijn. Als u niet-atomische bestanden schrijft, kunnen deze bestanden op de client worden geladen met gedeeltelijke inhoud.

Een van de opties om het atomisch te maken is naar bestanden te schrijven die zijn opgeslagen in een tijdelijke map en deze na schrijven naar de doelmap te kopiëren of te verplaatsen (van waar ze naar de client zijn geladen). Voor details over het schrijven aan dossiers, zie [&#x200B; php schrijven &#x200B;](https://www.php.net/manual/en/function.fwrite.php).
