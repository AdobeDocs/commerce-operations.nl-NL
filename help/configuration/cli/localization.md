---
title: Vertaalwoordenboeken en taalpakketten
description: Leer hoe u vertaalwoordenboeken kunt genereren en taalpakketten kunt maken.
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---

# Lokalisatie

{{file-system-owner}}

Met Commerce-vertalingen kunt u uw winkel voor meerdere regio&#39;s en markten aanpassen en lokaliseren door het volgende te genereren:

- **Vertaal woordenboeken**, die een geschikte manier zijn om _sommige_ woorden en uitdrukkingen, zoals die voor een douanemodule of een thema aan te passen of te vertalen.
- **pakketten van de Taal** die u toelaten om _om het even welk of alle_ woorden en uitdrukkingen in de toepassing van Commerce te vertalen.

Zie [ Overzicht van Vertalingen ].

## Een vertaalwoordenboek genereren

U kunt a [ vertaalwoordenboek ] produceren om bestaande koorden aan te passen, woorden en uitdrukkingen in een douanemodule vertalen, een thema lokaliseren, of taalpakketten tot stand brengen.

Als u wilt beginnen met het vertalen, gebruikt u een opdracht om een CSV-woordenboekbestand te genereren met een verzamelde lijst van alle bestaande woordgroepen en woorden.

U genereert het woordenboek als volgt en u begint met vertalen:

1. Extraheer vertaalbare woorden en woordgroepen uit ingeschakelde componenten met behulp van de opdracht Vertaalverzameling. Inhoud wordt uitgepakt in een CSV-bestand.
1. Vertaal de bestaande woorden en woordgroepen. Desgewenst kunt u aanvullende aangepaste voorwaarden toevoegen.

   U hebt opties voor het gebruik van het vertaalde woordenboek:

1. U kunt de vertaalwoordenboeken verpakken in een taalpakket en het pakket leveren aan de beheerder van de Commerce-winkel.

1. In Admin, vormt de opslagbeheerder [ de vertalingen ].

Opdrachtopties:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

In de volgende tabel worden parameters en waarden beschreven:

| Parameter | Waarde | Vereist? |
|--- |--- |--- |
| `<path to directory to translate>` | Pad naar een map met vertaalbare code, met andere woorden PHP-, PHTML- of XML-bestanden met te vertalen zinnen.<br><br> het hulpmiddel begint bij de weg te zoeken die u ingaat en alle dossiers en subdirectories zoekt het bevat.<br><br> gebruik deze parameter niet als u `-m --magento` gebruikt. | Ja (woordenboeken), nee (pakketten). |
| `-m --magento` | Vereist voor het maken van een taalpakket op basis van dit vertaalwoordenboek. Indien gebruikt, zoekt naar de folders die bak/magento bevatten. Met deze optie voegt u thema&#39;s of modules toe aan elke regel in het woordenboek.<br><br> een steekproef volgt:<br><br> &quot;Geen Gevonden Punten&quot;, &quot;Geen Gevonden Punten&quot;, module, Magento_Wishlist | Nee |
| `-o --output="<path>"` | Hier geeft u het absolute pad naar het bestandssysteem en de bestandsnaam op van het CSV-bestand voor het vertaalwoordenboek dat u wilt maken. De waarde die u invoert, is hoofdlettergevoelig. De naam van het CSV-bestand moet exact overeenkomen met de naam van de landinstelling, inclusief het hoofdlettergebruik.<br><br> als u deze parameter weglaat, wordt de output geleid aan stdout. | Nee |

>[!INFO]
>
>Om een taalpak van een vertaalwoordenboek tot stand te brengen, moet u __ de `-m|--magento` optie gebruiken.

### Richtlijnen voor vertaling

Gebruik de volgende richtlijnen bij het vertalen van woorden en woordgroepen:

- Wijzig alleen de inhoud van de tweede kolom. Vertaal de uitdrukkingen van het Engels (`US`) aan de gewenste taal.
- Gebruik de standaard Commerce-tekenreeksen wanneer u woordenboeken voor landinstellingen maakt.
- Let tijdens het vertalen op de plaatsaanduidingen: `%1`, `%2`

Commerce gebruikt placeholders om contextwaarden op te nemen; zij worden _niet_ gebruikt voor vertalingen. Bijvoorbeeld:

```text
Product '%1' has been added to shopping cart.
```

Populaten met een waarde:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

De resulterende uitdrukking moet minstens één van elke placeholder bevatten. Stel dat de oorspronkelijke uitdrukking plaatsaanduidingen bevat van `%1` tot `%3` . De vertaling kan een onbeperkt aantal van deze plaatsaanduidingen bevatten, maar er moet minstens één voorkomen voorkomen van `%1` , `%2` en `%3` . De vertaling kan geen plaatsaanduidingswaarden bevatten die niet voorkomen in de oorspronkelijke waarde (bijvoorbeeld `%4` , `%5` , enzovoort).

Een voorbeeld van het vertalen van een woordgroep:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Een taalpakket maken

In tegenstelling tot een vertaalwoordenboek kunt u een of meer woorden en woordgroepen in de Commerce-toepassing vertalen met behulp van een taalpakket. U kunt een bepaalde component, zoals een module of een thema, vertalen met een vertaalwoordenboek. [ leer meer over taalpakketten ].

In deze sectie wordt besproken hoe u een taalpakket kunt maken, waarin CSV-bestanden naar modules en thema&#39;s worden geschreven. Als u een taalpakket wilt maken, moet u de in de volgende secties beschreven taken uitvoeren:

1. [ verzamel en vertaal woorden en uitdrukkingen ](#generate-a-translation-dictionary). (De parameter `--magento` is vereist.)
1. [ stel het bevel van het taalpakket in werking ](#run-the-language-package-command).
1. [ creeer folders en dossiers ](#create-directories-and-files).
1. (Facultatief.) [ vorm veelvoudige pakketten voor een taal ](#configure-multiple-packages-for-a-language).

### De opdracht Taalpakket uitvoeren

Opdrachtgebruik:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

In de volgende tabel worden de parameters en waarden voor de opdracht Taalpakket uitgelegd:

| Parameter | Waarde | Vereist? |
|--- |--- |--- |
| `<source>` | Absoluut pad naar bestandssysteem en bestandsnaam van een CSV-bestand met het gecombineerde vertaalwoordenboek en de metagegevens die nodig zijn voor de indeling in een taalpakket.<br><br> Gebruik [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) om het Csv- dossier tot stand te brengen dan tot het taalpakket zoals die in [ wordt besproken leidt tot folders en dossiers ](#m2devgde-xlate-files). | Ja |
| `<locale>` | [ ISO 639-1 ] (taal) en [ ISO 3166 ] (land) herkenningsteken van taal die als dossiernaam voor alle resulterende Csv- dossiers wordt gebruikt. Voorbeelden: `de_DE` , `pt_PT` , `pt_BR` . | Ja |
| `-m --mode` | Als er een doelbestand bestaat, geeft u op of het bestaande taalpakket moet worden vervangen of moet worden samengevoegd met het nieuwe taalpakket. Bij het samenvoegen worden alle bestaande woordgroepen overschreven en worden er nieuwe toegevoegd.<br><br> Waarden: fusie of vervang (gebrek). | Nee |
| `-d --allow-duplicates` | Neem deze optie op als u duplicaten in het taalpakket wilt toestaan. Anders mislukt de opdracht met een fout als dezelfde woordgroep wordt aangetroffen in meerdere items met verschillende vertalingen. | Nee |

### Mappen en bestanden maken

Taalpakketten bevinden zich in een map onder `app/i18n/<VendorName>` in het Commerce-bestandssysteem met de volgende inhoud:

- Vereiste licentiebestanden
- `composer.json`
- `registration.php` dat [ registers ] het taalpakket
- [`language.xml`](#language-package-languagexml) bestand met metagegevens

>[!INFO]
>
>U moet het hele pad in kleine letters plaatsen. Zie bijvoorbeeld [`de_de`] .

U kunt als volgt deze bestanden maken:

1. Maak een map onder `app/i18n` .

   Commerce-taalpakketten bevinden zich bijvoorbeeld in `app/i18n/magento`

1. Voeg de vereiste licentiebestanden toe.
1. Voeg [`composer.json`] toe die gebiedsdelen voor uw taalpakket specificeert.
1. Het taalpakket registreren bij [`registration.php`]
1. Voeg `language.xml` meta-informatiedossier toe zoals die in de volgende sectie wordt besproken.

#### Taalpakket taal.xml

Wanneer u een taalpakket in het configuratiebestand van `language.xml` declareert, moet u de volgorde van de taalovererving voor dit pakket opgeven.

De overerving van de taal laat u toe om een vertaling tot stand te brengen genoemd a _kind_ dat op een bestaande vertaling wordt gebaseerd geroepen a _ouder_. De onderliggende vertalingen overschrijven het bovenliggende element. Als de onderliggende vertaling echter niet kan worden geüpload of weergegeven of als er een woordgroep of woord ontbreekt, gebruikt Commerce de bovenliggende landinstelling. [ Voorbeelden van taalpakketovererving ](#example-of-language-inheritance).

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

Waarbij:

- `code`—Taalpakketlandinstelling (vereist)
- `vendor`—De leveranciersnaam van de module (vereist)
- `package`—Taalpakketnaam (vereist)
- `sort_order`—Prioriteit bij het uploaden van een pakket wanneer er meerdere taalpakketten beschikbaar zijn voor een winkel
- `use`—Landinstelling bovenliggende taalpakket waaruit woordenboeken moeten worden overgenomen

Indien nodig kunt u verschillende bovenliggende pakketten opgeven. De bovenliggende pakketten worden toegepast op een eerst weergegeven, eerst gebruikte basis.

#### Voorbeeld van taalovererving

Veronderstel dat een taalpakket van twee andere pakketten erft, en dat die pakketten ook ouder en &quot;grootouder&quot;pakketten hebben.

Als een taalpakket overerft van twee pakketten, ziet `language.xml` er als volgt uit:

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

- `language_package_one` neemt van `en_au_package` en `en_au_package` overerft van `en_ie_package`
- `language_package_two` neemt van `en_ca_package` en `en_ca_package` overerft van `en_us_package`

Als de Commerce-toepassing geen woord of woordgroep kan vinden in het `en_GB` -pakket, zoekt het in de volgende volgorde in andere pakketten:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Als u alle overervingen tussen de taalpakketten opgeeft, kan dit leiden tot circulaire overervingsketens. Gebruik [ Magento\Test\Integrity\App\Language\CircularDependencyTest ] test om van dergelijke ketens de plaats te bepalen en te bevestigen.

### Meerdere pakketten voor een taal configureren

Om uw winkel flexibeler te maken, kunt u verschillende taalpakketten voor dezelfde taal in uw winkel uploaden. U kunt dus verschillende aangepaste pakketten gebruiken voor verschillende onderdelen van uw winkel, omdat het systeem één pakket compileert van alle pakketten die beschikbaar zijn voor een taal.

Om een extra pakket voor een bestaande taal toe te laten, noem het nieuwe pakket om het even welke naam behalve een bestaande taalcodenaam (om verwarring te vermijden). Geef configuraties van een pakket op in het meta-informatiebestand `language.xml` van het taalpakket, zoals in de volgende sectie wordt besproken.

## Voorbeelden van het gebruik van vertaalopdrachten

De volgende secties verstrekken voorbeelden van begin tot eind van het gebruiken van de bevelen die in dit onderwerp worden besproken om vertaalwoordenboeken en vertaalpakketten tot stand te brengen:

### Voorbeeld: een vertaalwoordenboek maken voor een module of thema

U voegt als volgt een Duitse vertaling toe aan een module of thema dat u wilt verspreiden onder andere verkopers:

1. Verzamel zinnen uit uw module:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >Het CSV- dossier - naam moet _precies_ de scène aanpassen, met inbegrip van het geval van karakters.

1. Vertaal de woorden en de uitdrukkingen gebruikend [ deze richtlijnen ](#translation-guidelines).
1. Kopieer indien nodig `xx_YY.csv` naar `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` of naar de themamap van de module (afhankelijk van of het vertaalwoordenboek voor een module of een thema is).

### Voorbeeld: Een taalpakket maken

Vergelijkbaar met het voorgaande voorbeeld genereert u een CSV-bestand. In plaats van een module- of themamap op te geven, geeft u echter de volledige hoofdmap van de Commerce-toepassing op. Het resulterende CSV-bestand bevat alle woordgroepen die de opdracht in de code kan vinden.

1. Verzamel zinnen uit uw module:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >Het CSV- dossier - naam moet _precies_ de scène aanpassen, met inbegrip van het geval van karakters.

1. Vertaal de woorden en de uitdrukkingen gebruikend [ deze richtlijnen ](#translation-guidelines).
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

   **Voorbeeld`composer.json`** :

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

   **Voorbeeld`registration.php`** :

   ```php
   <?php
   /**
    * Copyright [first year code created] Adobe
    * All Rights Reserved.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **Voorbeeld`language.xml`** :

   ```xml
   <?xml version="1.0"?>
   <!--
   Copyright [first year code created] Adobe
   All Rights Reserved.
   -->
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Overzicht van vertalingen]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[vertaalwoordenboek]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[configureert de vertalingen]: https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/site-store/store-localize
[Meer informatie over taalpakketten]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registers]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[` de_`]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&quot;composer.json&quot;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&quot;registration.php&quot;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
