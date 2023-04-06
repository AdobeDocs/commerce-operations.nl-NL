---
title: Statische weergavebestanden gebruiken
description: Leer om statische dossiers aan het het dossiersysteem van de Handel tijdens productiemodus te schrijven.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# Statische weergavebestanden gebruiken

{{file-system-owner}}

Het statische bevel van de de plaatsing van meningsdossiers laat u toe om statische dossiers aan het het dossiersysteem van de Handel te schrijven wanneer de software van de Handel wordt geplaatst voor [productiemodus](../bootstrap/application-modes.md#production-mode).

De term _statisch weergavebestand_ verwijst naar het volgende:

- &quot;Statisch&quot; betekent dat het bestand voor een site in de cache kan worden geplaatst (het bestand wordt dus niet dynamisch gegenereerd). Voorbeelden zijn afbeeldingen en CSS die zijn gegenereerd op basis van LESS.
- De &quot;Mening&quot;verwijst naar presentatielaag (van MVC).

De statische meningsdossiers worden gevestigd in `<magento_root>/pub/static` en sommige worden in de cache opgeslagen `<magento_root>/var/view_preprocessed` ook map.

De plaatsing van statische meningsdossiers wordt beïnvloed door toepassingswijzen als volgt:

- [Standaard](../bootstrap/application-modes.md#default-mode) en [ontwikkelaar](../bootstrap/application-modes.md#developer-mode) modi: De handel produceert hen op bestelling, maar de rest wordt in een dossier voor snelheid van toegang in het voorgeheugen ondergebracht.
- [Productie](../bootstrap/application-modes.md#production-mode) modus: Statische bestanden zijn _niet_ gegenereerd of in cache geplaatst.

U moet statische meningsdossiers aan het het dossiersysteem van de Handel manueel schrijven gebruikend het bevel dat in dit onderwerp wordt besproken; daarna kunt u machtigingen beperken om uw kwetsbaarheden te beperken en te voorkomen dat bestanden per ongeluk of kwaadwillig worden overschreven.

>[!WARNING]
>
>_Alleen modus Ontwikkelaar_: Wanneer u een nieuwe module installeert of inschakelt, wordt mogelijk nieuwe JavaScript, CSS, lay-outs enzovoort geladen. Als u problemen met statische bestanden wilt voorkomen, moet u de oude bestanden opschonen om ervoor te zorgen dat alle wijzigingen voor de nieuwe module worden doorgevoerd. U kunt gegenereerde statische weergavebestanden op verschillende manieren opschonen. Zie [Cache-onderwerp van statische bestanden opschonen voor meer informatie](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) voor meer informatie .

**Statische weergavebestanden implementeren**:

1. Log in bij de Commerce-server als, of [schakelen naar de eigenaar van het bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. De inhoud van `<magento_root>/pub/static`, met uitzondering van de `.htaccess` bestand. Verwijder dit bestand niet.
1. Het implementatieprogramma voor statische weergavebestanden uitvoeren `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >Als u samenvoeging van statische weergavebestanden inschakelt in de beheerfunctie, `pub/static` het directorysysteem moet schrijfbaar zijn.

   Opdrachtopties:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

De volgende lijst verklaart de parameters en de waarden van dit bevel.

| Option | Beschrijving | Vereist? |
| ------ | ----------- | --------- |
| `<languages>` | Lijst met door spaties gescheiden [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) taalcodes waarvoor statische weergavebestanden moeten worden uitgevoerd. (Standaard is `en_US`.)<br>Zoek de lijst door deze uit te voeren: `bin/magento info:language:list` | Nee |
| `--language (-l)` | Genereer bestanden alleen voor de opgegeven talen. Als er geen optie is opgegeven, worden standaard bestanden voor alle ISO-639-taalcodes gegenereerd. U kunt de naam van één taalcode tegelijk opgeven. Standaardwaarde is **alles**.<br>Bijvoorbeeld: `--language en_US --language es_ES` | Nee |
| `--exclude-language` | Genereer bestanden voor de opgegeven taalcodes. Als er geen optie is opgegeven, wordt standaard niets uitgesloten. U kunt de naam van één taalcode of een komma-gescheiden lijst van taalcodes specificeren. Standaardwaarde is **none**. | Nee |
| `--theme <theme>` | Thema&#39;s waarvoor statische inhoud moet worden geïmplementeerd. Standaardwaarde is **alles**.<br>Bijvoorbeeld: `--theme Magento/blank --theme Magento/luma` | Nee |
| `--exclude-theme <theme>` | Thema&#39;s die moeten worden uitgesloten bij het implementeren van statische inhoud. Standaardwaarde is **none**.<br>Bijvoorbeeld: `--exclude-theme Magento/blank` | Nee |
| `--area (-a)` | Alleen bestanden genereren voor de opgegeven gebieden. Als er geen optie is opgegeven, worden standaard bestanden voor alle gebieden gegenereerd. Geldige waarden zijn `adminhtml` en `frontend`. Standaardwaarde is **alles**.<br>Bijvoorbeeld: `--area adminhtml` | Nee |
| `--exclude-area` | Genereer geen bestanden voor de opgegeven gebieden. Als er geen optie is opgegeven, wordt standaard niets uitgesloten. Standaardwaarde is **none**. | Nee |
| `--jobs (-j)` | Schakel parallelle verwerking in met het opgegeven aantal taken. De standaardwaarde is 0 (niet in parallelle processen). Standaardwaarde is **0**. | Nee |
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
| `-s <quick\|standard\|compact>` | Definieer de implementatiestrategie. Gebruik deze opties alleen als u meerdere lokale instellingen hebt.<ul><li>Gebruik de [snelle strategie](static-view-file-strategy.md#quick-strategy) om de implementatietijd te minimaliseren. Dit is de standaardoptie van het bevel als niet gespecificeerd.</li><li>Gebruik de [standaardstrategie](static-view-file-strategy.md#standard-strategy) om alle statische meningsdossiers voor alle pakketten op te stellen.</li><li>Gebruik de [compacte strategie](static-view-file-strategy.md#compact-strategy) om schijfruimte op de server te besparen.</li></ul> | Nee |
| `--no-parent` | Genereer geen bestanden voor de bovenliggende thema&#39;s van het huidige thema. Het wordt sterk geadviseerd om deze vlag te gebruiken als u niet uitdrukkelijk het ouderthema van het huidige thema gebruikt u probeert op te stellen. Dit verhoogt de snelheid van het proces aanzienlijk. Deze markering is beschikbaar in Commerce 2.4.2 | Nee |
| `--force (-f)` | Bestanden in elke modus implementeren. (standaard kan het hulpprogramma voor het implementeren van statische inhoud alleen worden uitgevoerd in de productiemodus. Gebruik deze optie als u deze wilt uitvoeren (standaard of in de ontwikkelaarsmodus). | Nee |

>[!INFO]
>
>Als u waarden opgeeft voor beide `<languages>` en `--language`, `<languages>` heeft voorrang.

## Voorbeelden

Hier volgen enkele voorbeelden van opdrachten.

### Een thema en HTML-miniatuur uitsluiten

Het volgende bevel stelt statische inhoud voor het Engels van de V.S. op (`en_US`), sluit het Luminantiemenu-thema uit dat bij Handel wordt geleverd en minieme HTML-bestanden niet.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Voorbeelduitvoer:

```terminal
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

De volgende opdracht implementeert alleen JavaScript, met 4 taken, met een standaard implementatiestrategie:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

De volgende opdracht implementeert alleen CSS en LESS met 3 taken en een snelle implementatiestrategie:

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Statische weergavebestanden genereren voor één thema en één gebied

Met de volgende opdracht genereert u statische weergavebestanden voor alle talen, alleen het voorste gebied, alleen het thema Luminantie voor handel, zonder lettertypen te genereren:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Voorbeelduitvoer:

```terminal
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

## Statische weergavebestanden implementeren zonder handel te installeren

U zou het plaatsingsproces in een afzonderlijk, niet-productie, milieu kunnen willen in werking stellen, om het even welke bouwstijlprocessen op gevoelige productiemachines te vermijden.

Voer hiertoe de volgende stappen uit:

1. Uitvoeren [`bin/magento app:config:dump`](../cli/export-configuration.md) om de configuratie uit uw productiesysteem uit te voeren.
1. Kopieer de geëxporteerde bestanden naar de basis van de niet-productiecode.
1. Statische weergavebestanden gebruiken: `bin/magento setup:static-content:deploy`

## Problemen met het implementatieprogramma voor statische weergavebestanden oplossen

[Eerst de Commerce-software installeren](../../installation/overview.md); anders, kunt u niet het statische hulpmiddel van de plaatsing van meningsdossiers in werking stellen.

**Symptoom**: De volgende fout wordt getoond wanneer u het statische hulpmiddel van de plaatsing van meningsdossiers in werking stelt:

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**Oplossing**:

Voer de volgende stappen uit:

1. Installeer de software Commerce met de [opdrachtregel](../../installation/composer.md).
1. Meld u aan bij de toepassingsserver als, of [schakelen naar](../../installation/prerequisites/file-system/overview.md), de eigenaar van het bestandssysteem.
1. De inhoud van `<app_root>/pub/static` map, behalve de map `.htaccess` bestand. Verwijder dit bestand niet.
1. Statische weergavebestanden gebruiken: `bin/magento setup:static-content:deploy`

## Tip voor ontwikkelaars die het statische hulpmiddel van de inhoudsimplementatie aanpassen

Wanneer u een aangepaste implementatie van het hulpprogramma voor de implementatie van statische inhoud maakt, gebruikt u alleen het schrijven van atomische bestanden voor bestanden die op de client beschikbaar moeten zijn. Als u niet-atomische bestanden schrijft, kunnen deze bestanden op de client worden geladen met gedeeltelijke inhoud.

Een van de opties om het atomisch te maken is naar bestanden te schrijven die zijn opgeslagen in een tijdelijke map en deze na schrijven naar de doelmap te kopiëren of te verplaatsen (van waar ze naar de client zijn geladen). Zie voor meer informatie over het schrijven naar bestanden [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
