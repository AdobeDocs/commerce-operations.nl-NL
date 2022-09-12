---
title: Vertaalwoordenboeken en taalpakketten
description: Leer hoe u vertaalwoordenboeken kunt genereren en taalpakketten kunt maken.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 0%

---


# Lokalisatie

{{file-system-owner}}

De vertalingen van de handel laten u toe om uw opslag voor veelvoudige gebieden en markten aan te passen en te lokaliseren door te produceren:

- **Vertaalwoordenboeken**, die een handige manier zijn om aan te passen of te vertalen _sommige_ woorden en zinnen, zoals die voor een aangepaste module of een aangepast thema.
- **Taalpakketten** waarmee u kunt vertalen _alle_ woorden en zinsdelen in de aanvraag voor de handel.

Zie [Overzicht van vertalingen].

## Een vertaalwoordenboek genereren

U kunt een [vertaalwoordenboek] bestaande tekenreeksen aanpassen, woorden en woordgroepen vertalen in een aangepaste module, een thema lokaliseren of [taalpakketten](https://glossary.magento.com/language-package).

Als u wilt beginnen met het vertalen, gebruikt u een opdracht om een CSV-woordenboekbestand te genereren met een verzamelde lijst van alle bestaande woordgroepen en woorden.

U genereert het woordenboek als volgt en u begint met vertalen:

1. Extraheer vertaalbare woorden en woordgroepen uit ingeschakelde componenten met behulp van de opdracht Vertaalverzameling. Inhoud wordt geëxtraheerd naar een CSV-bestand.
1. Vertaal de bestaande woorden en woordgroepen. Desgewenst kunt u aanvullende aangepaste voorwaarden toevoegen.

   U hebt opties voor het gebruik van het vertaalde woordenboek:

1. U kunt de vertaalwoordenboeken in een taalpakket verpakken en het pakket aan de de opslagbeheerder van de Handel verstrekken.

1. In Admin, de opslagbeheerder [configureert de vertalingen].

Opdrachtopties:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

In de volgende tabel worden parameters en waarden beschreven:

| Parameter | Waarde | Vereist? |
|--- |--- |--- |
| `<path to directory to translate>` | Pad naar een map met vertaalbare code; met andere woorden, PHP-, PHTML- of XML-bestanden met zinnen die moeten worden vertaald.<br><br>Het gereedschap zoekt naar het pad dat u invoert en doorzoekt alle bestanden en submappen die het bevat.<br><br>Gebruik deze parameter niet als u `-m --magento`. | Ja (woordenboeken), nee (pakketten). |
| `-m --magento` | Vereist voor het maken van een taalpakket op basis van dit vertaalwoordenboek. Indien gebruikt, zoekt naar de folders die bak/magento bevatten. Met deze optie voegt u thema&#39;s of modules toe aan elke regel in het woordenboek.<br><br>Hieronder volgt een monster:<br><br>&quot;Geen items gevonden&quot;,&quot;Geen items gevonden&quot;, module,Magento_lijst | Nee |
| `-o --output="<path>"` | Hier geeft u het absolute pad naar het bestandssysteem en de bestandsnaam op van het CSV-bestand voor het vertaalwoordenboek dat u wilt maken. De waarde die u invoert, is hoofdlettergevoelig. De naam van het CSV-bestand moet exact overeenkomen met de naam van de landinstelling, inclusief het hoofdlettergebruik.<br><br>Wanneer u deze parameter weglaat, wordt de uitvoer naar stdout gestuurd. | Nee |

>[!INFO]
>
>Als u een taalpakket wilt maken op basis van een vertaalwoordenboek, _moet_ gebruiken `-m|--magento` optie.

### Richtlijnen voor vertaling

Gebruik de volgende richtlijnen bij het vertalen van woorden en woordgroepen:

- Wijzig alleen de inhoud van de tweede kolom. Zet de zinnen uit het Engels om (`US`) naar de gewenste taal.
- Wanneer u woordenboeken voor landinstellingen maakt, gebruikt u de standaardhandelreeksen.
- Let tijdens het vertalen op plaatsaanduidingen: `%1`, `%2`

De handel gebruikt placeholders om contextwaarden op te nemen; zij zijn _niet_ gebruikt voor vertalingen. Bijvoorbeeld:

```text
Product '%1' has been added to shopping cart.
```

Populaten met een waarde:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

De resulterende uitdrukking moet minstens één van elke placeholder bevatten. Stel dat er plaatsaanduidingen zijn van `%1` tot `%3` in de oorspronkelijke zin. De vertaling kan zo veel van deze plaatsaanduidingen in om het even welke orde hebben, maar er moet minstens één voorkomen van `%1`, `%2`, en `%3`. De vertaling kan geen plaatsaanduidingswaarden bevatten die niet voorkomen in de oorspronkelijke waarde (bijvoorbeeld `%4`, `%5`, enzovoort).

Een voorbeeld van het vertalen van een woordgroep:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Een taalpakket maken

In tegenstelling tot een vertaalwoordenboek kunt u een of meer woorden en woordgroepen in de toepassing Handel vertalen met behulp van een taalpakket. U kunt een bepaalde component, zoals een module of een thema, vertalen met een vertaalwoordenboek. [Meer informatie over taalpakketten].

In deze sectie wordt besproken hoe u een taalpakket kunt maken, waarin CSV-bestanden naar modules en thema&#39;s worden geschreven. Als u een taalpakket wilt maken, moet u de in de volgende secties beschreven taken uitvoeren:

1. [Woorden en woordgroepen verzamelen en vertalen](#generate-a-translation-dictionary). (De `--magento` parameter is vereist.)
1. [De opdracht Taalpakket uitvoeren](#run-the-language-package-command).
1. [Mappen en bestanden maken](#create-directories-and-files).
1. (Optioneel.) [Meerdere pakketten voor een taal configureren](#configure-multiple-packages-for-a-language).

### De opdracht Taalpakket uitvoeren

Opdrachtgebruik:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

In de volgende tabel worden de parameters en waarden voor de opdracht Taalpakket uitgelegd:

| Parameter | Waarde | Vereist? |
|--- |--- |--- |
| `<source>` | Absoluut pad naar bestandssysteem en bestandsnaam van een CSV-bestand met het gecombineerde vertaalwoordenboek en de metagegevens die nodig zijn voor de indeling in een taalpakket.<br><br>Gebruiken [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) om het CSV-bestand te maken en vervolgens het taalpakket te maken zoals beschreven in [Mappen en bestanden maken](#m2devgde-xlate-files). | Ja |
| `<locale>` | [ISO 639-1] (taal) en [ISO 3166] (land)-id van de taal die wordt gebruikt als bestandsnaam voor alle resulterende CSV-bestanden. Voorbeelden: `de_DE`, `pt_PT`, `pt_BR`. | Ja |
| `-m --mode` | Als er een doelbestand bestaat, geeft u op of het bestaande taalpakket moet worden vervangen of moet worden samengevoegd met het nieuwe taalpakket. Bij het samenvoegen worden alle bestaande woordgroepen overschreven en worden er nieuwe toegevoegd.<br><br>Waarden: samenvoegen of vervangen (standaard). | Nee |
| `-d --allow-duplicates` | Neem deze optie op als u duplicaten in het taalpakket wilt toestaan. Anders mislukt de opdracht met een fout als dezelfde woordgroep wordt aangetroffen in meerdere items met verschillende vertalingen. | Nee |

### Mappen en bestanden maken

Taalpakketten bevinden zich in een map onder `app/i18n/<VendorName>` in het systeem van het handelsdossier met de volgende inhoud:

- Vereiste licentiebestanden
- `composer.json`
- `registration.php` dat [registers] het taalpakket
- [`language.xml`](#language-package-languagexml) meta-informatiebestand

>[!INFO]
>
>U moet het hele pad in kleine letters plaatsen. Zie bijvoorbeeld [`de_de`].

U kunt als volgt deze bestanden maken:

1. Een map maken onder `app/i18n`.

   De taalpakketten Handel bevinden zich bijvoorbeeld in `app/i18n/magento`

1. Voeg de vereiste licentiebestanden toe.
1. Toevoegen [`composer.json`] die gebiedsdelen voor uw taalpakket specificeert.
1. Het taalpakket registreren bij [`registration.php`]
1. Toevoegen `language.xml` meta-informatiedossier zoals besproken in de volgende sectie.

#### Taalpakket taal.xml

Bij het declareren van een taalpakket in de `language.xml` configuratiebestand, moet u de volgorde van de taalovererving voor dit pakket opgeven.

Met talenovererving kunt u een vertaling maken die een _onderliggend_ op basis van een bestaande vertaling die een _parent_. De onderliggende vertalingen overschrijven het bovenliggende element. Als de onderliggende vertaling echter niet kan worden geüpload of weergegeven of een woordgroep of woord ontbreekt, gebruikt de Handel de bovenliggende vertaling [landinstelling](https://glossary.magento.com/locale). [Voorbeelden van taalpakketovererving](#example-of-language-inheritance).

Geef de volgende informatie op om een pakket te declareren:

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

Waar:

- `code`—Landinstelling taalpakket (vereist)
- `vendor`—Naam leverancier van de module (vereist)
- `package`—Taalpakketnaam (vereist)
- `sort_order`—Prioriteit bij het uploaden van een pakket wanneer er meerdere taalpakketten beschikbaar zijn voor een winkel
- `use`—Landinstelling van het bovenliggende taalpakket waaruit woordenboeken moeten worden overgenomen

Indien nodig kunt u verschillende bovenliggende pakketten opgeven. De bovenliggende pakketten worden toegepast op een eerst weergegeven, eerst gebruikte basis.

#### Voorbeeld van taalovererving

Veronderstel dat een taalpakket van twee andere pakketten erft, en dat die pakketten ook ouder en &quot;grootouder&quot;pakketten hebben.

Als een taalpakket overerft van twee pakketten, wordt `language.xml` zou als het volgende kunnen kijken:

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

In het vorige voorbeeld:

- `language_package_one` overerven van `en_au_package` en `en_au_package` overerven van `en_ie_package`
- `language_package_two` overerven van `en_ca_package` en `en_ca_package` overerven van `en_us_package`

Als in de toepassing Handel geen woord of woordgroep kan worden gevonden in het dialoogvenster `en_GB` pakket, zoekt het in andere pakketten in de volgende opeenvolging:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Als u alle overervingen tussen de taalpakketten opgeeft, kan dit leiden tot circulaire overervingsketens. Gebruiken [Magento\Test\Integrity\App\Language\CircularDependencyTest] test om dergelijke ketens te vinden en te herstellen.

### Meerdere pakketten voor een taal configureren

Om uw winkel flexibeler te maken, kunt u verschillende taalpakketten voor dezelfde taal in uw winkel uploaden. U kunt dus verschillende aangepaste pakketten gebruiken voor verschillende onderdelen van uw winkel, omdat het systeem één pakket compileert van alle pakketten die beschikbaar zijn voor een taal.

Om een extra pakket voor een bestaande taal toe te laten, noem het nieuwe pakket om het even welke naam behalve een bestaande taalcodenaam (om verwarring te vermijden). Configuraties van een pakket opgeven in de taalpakketten `language.xml` meta-informatiedossier zoals besproken in de volgende sectie.

## Voorbeelden van het gebruik van vertaalopdrachten

De volgende secties verstrekken voorbeelden van begin tot eind van het gebruiken van de bevelen die in dit onderwerp worden besproken om vertaalwoordenboeken en vertaalpakketten tot stand te brengen:

### Voorbeeld: Een vertaalwoordenboek maken voor een module of thema

U voegt als volgt een Duitse vertaling toe aan een module of thema dat u wilt verspreiden onder andere verkopers:

1. Verzamel zinnen uit uw module:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >De CSV-bestandsnaam moet _exact overeenkomen_ de landinstelling, inclusief het hoofdlettergebruik.

1. De woorden en zinnen vertalen met [deze richtsnoeren](#translation-guidelines).
1. Indien nodig, kopie `xx_YY.csv` tot `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` of naar de themamap van de module (afhankelijk van of het vertaalwoordenboek voor een module of een thema is).

### Voorbeeld: Een taalpakket maken

Vergelijkbaar met het vorige voorbeeld, produceer een Csv- dossier, maar in plaats van het specificeren van een module of themafolder, specificeer de volledige folder van de de toepassingswortel van de Handel. Het resulterende CSV-bestand bevat alle woordgroepen die de opdracht in de code kan vinden.

1. Verzamel zinnen uit uw module:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >De CSV-bestandsnaam moet _exact overeenkomen_ de landinstelling, inclusief het hoofdlettergebruik.

1. De woorden en zinnen vertalen met [deze richtsnoeren](#translation-guidelines).
1. Maak het taalpakket.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Maak een map voor het taalpakket.

   Bijvoorbeeld: `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. Voeg in die map de volgende elementen toe:

   - Een vergunning, indien vereist
   - `composer.json` (voorbeeld hieronder)
   - `registration.php` (voorbeeld hieronder)
   - `language.xml` (voorbeeld hieronder)

   **Monster`composer.json`**:

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **Monster`registration.php`**:

   ```php
   <?php
   /**
    * Copyright &copy; Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **Monster`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   /**
   * Copyright &copy; Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Overzicht van vertalingen]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[vertaalwoordenboek]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[configureert de vertalingen]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[Meer informatie over taalpakketten]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registers]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[` de_de`]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&quot;composer.json&quot;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&quot;registration.php&quot;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
