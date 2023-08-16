---
title: '[!DNL Upgrade Compatibility Tool] Foutberichten'
description: Meer informatie over foutberichten die u tegenkomt bij het gebruik van de [!DNL Upgrade Compatibility Tool] op uw Adobe Commerce-project.
exl-id: fe4a17a9-a807-4315-b3cd-e35f34e39f6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4113'
ht-degree: 4%

---

# [!DNL Upgrade Compatibility Tool] foutberichten

{{commerce-only}}

Deze naslaggids voor foutberichten bevat informatie over fouten die kunnen optreden tijdens het uitvoeren van de opdracht [!DNL Upgrade Compatibility Tool].

Foutberichten worden ingedeeld op niveau (kritieke problemen, fouten en waarschuwingen) en type (kerncode, aangepaste code en GraphQL-schema&#39;s). Elk type bevat de volgende informatie:

- **Foutcode**: De door Adobe Commerce toegewezen id voor het foutbericht.
- **Foutbeschrijving**: Een beschrijving die de oorzaak van de fout samenvat.
- **Door fout voorgestelde actie**: Indien van toepassing, verstrekt raad om de fout problemen op te lossen en op te lossen.

## Kritieke kwesties

### Basiscode

Deze fouten worden gerapporteerd wanneer sommige kernbestanden ontbreken of niet overeenkomen met het origineel.

| Foutcode | Foutbeschrijving | Voorgestelde actie |
| --- | --- | --- |
| 2001 | Kernbestand niet gevonden | Voer de `composer install` opdracht uit de hoofdmap van het project. |
| 2002 | Het kernbestand is gewijzigd | Voer de `composer install` opdracht uit de hoofdmap van het project. |
| 2003 | Composerafhankelijkheid is niet geïnstalleerd | Ontbrekende composer-afhankelijkheid kan mogelijk problemen veroorzaken. Afhankelijkheid herstellen door uit te voeren `composer require package_name`. |
| 2005 | Kernmap niet gevonden | Voer de `composer install` opdracht uit de hoofdmap van het project. |

{style="table-layout:auto"}

### Aangepaste code

Er treden kritieke fouten op wanneer de aangepaste code verwijst naar entiteiten die niet aanwezig zijn in de Adobe Commerce-doelversie. Deze fouten worden ook gemeld wanneer de kritieke coderingsnormen zijn geschonden.

| Foutcode | Foutbeschrijving | Voorgestelde actie |
| --- | --- | --- |
| 1110 | Niet-bestaande Adobe Commerce-klasse/interface instantiëren | Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. Niet-bestaande Adobe Commerce-klasse/interface instantiëren. |
| 1111 | Uitbreiden vanaf een niet-bestaande Adobe Commerce-klasse | De uitgebreide klasse is niet meer aanwezig in de codebase. Overerving wordt niet aanbevolen voor het uitbreiden van de Adobe Commerce-functionaliteit. Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. |
| 1112 | Niet-bestaande Adobe Commerce-klasse importeren | Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. |
| 1113 | Niet-bestaande Adobe Commerce-klasse laden | Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. |
| 1114 | Niet-bestaande Adobe Commerce-klasse gebruiken | Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. |
| 1214 | Niet-bestaande Adobe Commerce-constante gebruiken | Overweeg in plaats hiervan een privéconstante van de vereiste waarde in de aangepaste code te introduceren en te gebruiken. |
| 1215 | Niet-bestaande Adobe Commerce-constante overschrijven | Overweeg in plaats hiervan een privéconstante van de vereiste waarde in de aangepaste code te introduceren en te gebruiken. |
| 1216 | Toewijzing van een niet-bestaande Adobe Commerce-constante | Overweeg in plaats hiervan een privéconstante van de vereiste waarde in de aangepaste code te introduceren en te gebruiken. |
| 1312 | Niet-bestaande Adobe Commerce-interface geïmporteerd | Overweeg de overerving te verwijderen of het te vervangen met de interface die in het werkingsgebied van de aanpassing wordt geïntroduceerd. |
| 1314 | Gebruikte niet-bestaande Adobe Commerce-interface | Overweeg de overerving te verwijderen of het te vervangen met de interface die in het werkingsgebied van de aanpassing wordt geïntroduceerd. |
| 1317 | Overgenomen, niet-bestaande Adobe Commerce-interface | Overweeg de overerving te verwijderen of het te vervangen met de interface die in het werkingsgebied van de aanpassing wordt geïntroduceerd. |
| 1318 | Niet-bestaande Adobe Commerce-interface geïmplementeerd | Overweeg de overerving te verwijderen of het te vervangen met de interface die in het werkingsgebied van de aanpassing wordt geïntroduceerd. |
| 1410 | Adobe Commerce-methode zonder aanroep | Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. |
| 1514 | Niet-bestaande Adobe Commerce-eigenschap gebruiken | Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. |
| 1515 | Niet-bestaande Adobe Commerce-eigenschap overschrijven | Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. |
| 1516 | Toewijzing van niet-bestaande Adobe Commerce-eigenschap | Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. Werk het toegangsniveau van het bezit aan privé bij als het binnen één enkele klasse slechts kan worden gebruikt. |
| 5002 | De openingstag PHP moet de eerste inhoud in het bestand zijn | Zorg ervoor dat het bestand geen inhoud bevat voordat de PHP-openingstag wordt weergegeven. |
| 5003 | Functie is vervangen | Gebruik een vervanging die in het foutbericht wordt voorgesteld. Als het bericht geen vervanging voorstelt, is een nauw overzicht nodig om een alternatieve functie of implementatie te selecteren. |
| 5005 | PHP-syntaxisfout | De code moet worden bijgewerkt om te voldoen aan de PHP syntaxisstandaarden. |
| 5072 | Mogelijke schending van het ontwerp van Magento 2. Doorgaans een Magento 1.x-constructie gedetecteerd | Constructie bijwerken naar Magento 2-standaarden. |
| 5076 | Kan niet gebruiken in naamruimte zoals deze is gereserveerd sinds PHP 7 | Vervang het gereserveerde woord in de naamruimte door een niet-gereserveerd trefwoord. |
| 5077 | Kan niet gebruiken als klassenaam omdat deze is gereserveerd sinds PHP 7 | Vervang de gereserveerde klassenaam door een niet-gereserveerde naam. |

{style="table-layout:auto"}

### DB-schema

Kritieke problemen met het DB-schema worden gerapporteerd als verwijderde kerntabellen of kolommen worden aangeduid door aangepaste beperkingen.

| Foutcode | Foutbeschrijving | Voorgestelde actie |
| --- | --- | --- |
| 7009 | Aangepaste beperking verwijst naar een kerntabel die is verwijderd in de doelversie | De kenmerken constraint of update referenceTable en referenceColumn verwijderen |
| 7010 | Aangepaste beperking verwijst naar een kernkolom die is verwijderd in de doelversie | De beperking verwijderen of het kenmerk referenceColumn bijwerken |

{style="table-layout:auto"}

### GraphQL Schema

De kritieke kwesties van het Schema van GraphQL worden opgeheven als de schemapunten niet aanwezig in de doelversie zijn.

| Foutcode | Foutbeschrijving | Voorgestelde actie |
| --- | --- | --- |
| 3101 | Type is verwijderd | Maak een lijst van alle vragen die naar dit gebied van verwijzingen voorzien. Controleer of deze query&#39;s door de aanpassingsimplementatie worden gebruikt. Werk de cliëntcode bij om de veranderde vraaginterface te behandelen. |
| 3102 | Type verwijderd uit samenvoeging | Als het union-type wordt gebruikt in de GraphQL-aanvraag voor constructie of verwerking van reacties, moet het mogelijk worden bijgewerkt. |
| 3103 | Veld verwijderd | Controleer of naar het veld wordt verwezen in de aanpassingscodebase. Pas de implementatie aan om het nieuwe veldtype correct af te handelen. |
| 3105 | Geïmplementeerde interface verwijderd | Controleer of het type dat de verwijderde interface implementeert, wordt gebruikt in de aanpassing. De implementatie moet mogelijk worden bijgewerkt als deze afhankelijk is van de verwijderde interface. |
| 3106 | Waarde verwijderd uit opsommingsteken | Als de verwijderde enum-waarde wordt gebruikt in de GraphQL-aanvraagconstructie of -implementatie voor reactieverwerking, moet deze mogelijk worden bijgewerkt. |
| 3107 | Argument verwijderd | Controleer of het veld wordt gebruikt in de aanpassingscodebase. Verwijder het argument voor dit veld. |
| 3109 | Richtlijn verwijderd | Controleer of de instructie wordt gebruikt in de aanpassingscodebase. Pas de implementatie aan om de verwijzing naar de richtlijn te verwijderen. |
| 3110 | Het argument Directive is verwijderd | Controleer of de instructie wordt gebruikt in de aanpassingscodebase. Verwijder het argument van de compilerinstructie. |
| 3111 | Richtlijn herhaalbaar verwijderd | Controleer of de instructie wordt gebruikt in de aanpassingscodebase. Pas de implementatie aan om de interfaceveranderingen te behandelen. |
| 3112 | Locatie van aanwijzing verwijderd | Controleer of de instructie wordt gebruikt in de aanpassingscodebase. Pas de implementatie aan om de interfaceveranderingen te behandelen. |
| 3201 | Type gewijzigd type | Maak een lijst van alle vragen die naar dit gebied van verwijzingen voorzien. Controleer of deze query&#39;s door de aanpassingsimplementatie worden gebruikt. Werk de cliëntcode bij om de veranderde vraaginterface te behandelen. |
| 3203 | Gewijzigd veld | Controleer of naar het veld wordt verwezen in de aanpassingscodebase. Pas de implementatie aan om het nieuwe veldtype correct af te handelen. |
| 3207 | Oorspronkelijk gewijzigd argument | Controleer of het veld wordt gebruikt in de aanpassingscodebase. Werk het argumenttype voor dit gebied bij. |
| 3303 | Vereist invoerveld toegevoegd | Het veld moet aan het verzoek worden toegevoegd als de query met dit veld wordt gebruikt voor de aanpassing. |
| 3307 | Vereist argument toegevoegd | Controleer of het veld wordt gebruikt in de aanpassingscodebase. Het nieuwe vereiste argument moet worden opgegeven wanneer het veld wordt gebruikt. |
| 3310 | Vereist argument voor compilatie toegevoegd | Controleer of de instructie wordt gebruikt in de aanpassingscodebase. Voeg het argument van de compilerinstructie toe. |

{style="table-layout:auto"}

## Fouten

### Aangepaste code

Er worden aangepaste codefouten gegenereerd wanneer aangepaste code gebruikmaakt van Adobe Commerce-entry-punten die niet worden beschouwd als/gemarkeerd als `@api`. Het gedrag van dergelijke toegangspunten blijft niet gegarandeerd. De aanpassing moet `@api` ingangspunten. De functionaliteit die is gebaseerd op niet-API Adobe Commerce-code moet na de upgrade worden getest. Deze fouten worden ook gemeld wanneer belangrijke coderingsnormen zijn overtreden.

| Foutcode | Foutbeschrijving | Voorgestelde actie |
| --- | --- | --- |
| 1104 | De niet-API-klasse gebruiken die de API-interface overerft | Klassen die niet zijn gemarkeerd als `@api` kan worden gewijzigd. U kunt overwegen de code bij te werken om te vertrouwen op de interface die als `@api` in plaats daarvan. Anders, zou de functionaliteit die op deze implementatie baseert na de verbetering moeten worden getest. |
| 1121 | Uitbreiden vanaf niet-Adobe Commerce API-klasse | De uitgebreide klasse is niet meer aanwezig in de codebase. Overerving wordt niet aanbevolen voor het uitbreiden van de Adobe Commerce-functionaliteit. Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. |
| 1122 | Niet-Adobe Commerce API-klasse importeren | De uitgebreide klasse is niet meer aanwezig in de codebase. Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. Anders, zou de functionaliteit die op deze implementatie baseert na de verbetering moeten worden getest. |
| 1123 | Niet-Adobe Commerce API-klasse laden | De uitgebreide klasse is niet meer aanwezig in de codebase. Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. Anders, zou de functionaliteit die op deze implementatie baseert na de verbetering moeten worden getest. |
| 1124 | Niet-Adobe Commerce API-klasse gebruiken | De uitgebreide klasse is niet meer aanwezig in de codebase. Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. Anders, zou de functionaliteit die op deze implementatie baseert na de verbetering moeten worden getest. |
| 1224 | Niet-Adobe Commerce API-constante gebruiken | Constanten die niet zijn gemarkeerd als `@api` kan worden gewijzigd. Overweeg in plaats hiervan een privéconstante van de vereiste waarde in de aangepaste code te introduceren en te gebruiken. |
| 1225 | Niet-Adobe Commerce API-constante overschrijven | Constanten die niet zijn gemarkeerd als `@api` kan worden gewijzigd. Overweeg in plaats hiervan een privéconstante van de vereiste waarde in de aangepaste code te introduceren en te gebruiken. |
| 1226 | Toewijzing van een niet-Adobe Commerce API-constante | Constanten die niet zijn gemarkeerd als `@api` kan worden gewijzigd. Overweeg in plaats hiervan een privéconstante van de vereiste waarde in de aangepaste code te introduceren en te gebruiken. |
| 1322 | Geïmporteerde niet-Adobe Commerce API interface | Interfaces niet gemarkeerd als `@api` kan worden gewijzigd. U kunt deze overerving verwijderen of vervangen door overerving van de Adobe Commerce-interface die is gemarkeerd als `@api` of een interface die in het werkingsgebied van aanpassingscode wordt geïntroduceerd. |
| 1324 | Gebruikte niet-Adobe Commerce API-interface | Interfaces niet gemarkeerd als `@api` kan worden gewijzigd. U kunt deze overerving verwijderen of vervangen door overerving van de Adobe Commerce-interface die is gemarkeerd als `@api` of een interface die in het werkingsgebied van aanpassingscode wordt geïntroduceerd. |
| 1327 | Overgenomen niet-Adobe Commerce API-interface | Constanten die niet zijn gemarkeerd als `@api` kan worden gewijzigd. Overweeg in plaats hiervan een privéconstante van de vereiste waarde in de aangepaste code te introduceren en te gebruiken. |
| 1328 | Geïmplementeerde niet-Adobe Commerce API-interface | Interfaces niet gemarkeerd als `@api` kan worden gewijzigd. U kunt deze overerving verwijderen of vervangen door overerving van de Adobe Commerce-interface die is gemarkeerd als `@api` of een interface die in het werkingsgebied van aanpassingscode wordt geïntroduceerd. |
| 1420 | Niet-Adobe Commerce API-klasse/interface instantiëren | Klassen die niet zijn gemarkeerd als `@api` kan worden gewijzigd. U kunt overwegen de code bij te werken om te vertrouwen op de interface die als `@api` in plaats daarvan. Anders, zou de functionaliteit die op deze implementatie baseert na de verbetering moeten worden getest. De aanbevolen manier om een instantie van de klasse op te halen, is ook het gebruik van DI. U kunt een factory gebruiken als een nieuwe instantie van de klasse is vereist. |
| 1428 | Mogelijke afhankelijkheid van uitvoeringsdetails. | Klassen die niet zijn gemarkeerd als `@api` kan worden gewijzigd. U kunt overwegen de code bij te werken om te vertrouwen op de interface die als `@api` in plaats daarvan. Anders, zou de functionaliteit die op deze implementatie baseert na de verbetering moeten worden getest. |
| 1429 | Niet-Adobe Commerce API-methoden aanroepen | Methoden die niet zijn gemarkeerd als `@api` of niet zijn gedeclareerd binnen de API-klasse/interface, kunnen worden gewijzigd. Zelfs als de interface van de methode niet in de nieuwe versie wordt bijgewerkt, kan zijn gedrag of output verschillend zijn. U kunt ook op een interfacemethode vertrouwen. Anders, zou de functionaliteit die op deze implementatie baseert na de verbetering moeten worden getest. |
| 1449 | Oproep aan niet-interfacemethode (die in implementatie aanwezig is) | Methoden die niet in de interface worden gedeclareerd, kunnen worden gewijzigd. U kunt ook op een interfacemethode vertrouwen. Anders, zou de functionaliteit die op deze implementatie baseert na de verbetering moeten worden getest. |
| 1524 | Niet-Adobe Commerce API-eigenschap gebruiken | Waarden van de eigenschappen die niet zijn gemarkeerd als `@api` kan worden gewijzigd. U kunt in plaats daarvan ook de API-interfacemethode gebruiken. |
| 1525 | Niet-Adobe Commerce API-eigenschap overschrijven | Waarden van de eigenschappen die niet zijn gemarkeerd als `@api` kan worden gewijzigd. U kunt in plaats daarvan ook de API-interfacemethode gebruiken. |
| 1526 | Toewijzing van niet-Adobe Commerce API-eigenschap | Waarden van de eigenschappen die niet zijn gemarkeerd als `@api` kan worden gewijzigd. U kunt in plaats daarvan ook de API-interfacemethode gebruiken. |
| 5004 | Functie zonder argument is vervangen | Geef de invoer door die moet worden gevalideerd als het eerste argument van de functie. |
| 5007 | Het gebruik van bepaalde functies wordt afgeraden | Gebruik deze functies niet. |
| 5009 | Sjabloonrichtlijnen kunnen geen methoden aanroepen. Alleen scalaire arraytoegang is toegestaan | Methodeaanroepen uit de sjabloon verwijderen. |
| 5010 | Sjabloon `@vars` commentaarblok bevat ongeldige JSON | Ongeldige JSON corrigeren. |
| 5011 | Sjabloon `@vars` commentaarblok bevat ongeldig label | Ongeldig label corrigeren. |
| 5012 | Sjabloon `@vars` commentaarblok bevat geen variabele die in de sjabloon wordt gebruikt | Voeg ontbrekende variabele toe aan @vars-commentaarblok. |
| 5013 | Vermijd het gebruik van zelfsluitende tag met niet-void HTML-element | Gebruik in plaats hiervan de afsluitende tag. |
| 5014 | De `"active"` kenmerk is verouderd | De lijst van actieve modules wordt bepaald in plaatsingsconfiguratie. |
| 5015 | De `<param>` knooppunt is verouderd | Gebruiken `<argument name="..." xsi:type="...">` in plaats daarvan. |
| 5016 | De `<instance>` knooppunt is verouderd | Gebruiken `<argument name="..." xsi:type="object">` in plaats daarvan. |
| 5017 | De `<array>` knooppunt is verouderd | Gebruiken `<argument name="..." xsi:type="array">` in plaats daarvan. |
| 5018 | De `<item key="...">` knooppunt is verouderd | Gebruiken `<item name="..." xsi:type="...">` in plaats daarvan. |
| 5019 | De `<value>` knooppunt is verouderd | Geef in plaats daarvan de werkelijke waarde op als letterlijk teken in de tekst. |
| 5020 | Verouderd knooppunt: `<supported_blocks>` | Te vervangen door `<supported_containers>`. |
| 5021 | Verouderd knooppunt: `<block_name>` | Te vervangen door `<container_name>`. |
| 5022 | Fabrieksnaam gedetecteerd | Het type widget mag niet beginnen met /. |
| 5023 | Verouderde ACL structuur die in lijn wordt ontdekt | Ga naar lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Achterhaalde menustructuur aangetroffen in regel | Ga naar app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Verouderde systeemconfiguratiestructuur aangetroffen in bestand | Ga naar app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Niet gebruiken `"text/javascript"` type, kenmerk | Gebruik alleen leden van het type public. |
| 5028 | Toegang tot beschermde en particuliere leden van `Block` klasse is verouderd in HTML-sjablonen | Gebruik alleen leden van het type public. |
| 5031 | Bevat verouderde methode | Gebruiken `getConnection()` in plaats daarvan. |
| 5042 | Onjuiste indeling van PHP-klasseverwijzing | Controleer of er naar de klasse wordt verwezen met alleen hoofdletters, cijfers en geen slash. |
| 5043 | Onjuiste indeling van moduleverwijzing | Controleer of er alleen naar de module wordt verwezen met behulp van letters, cijfers, onderstrepingstekens en geen slash. |
| 5044 | Klasse `Zend_Db_Select` is beperkt | Voorgestelde vervanging: `\Magento\Framework\DB\Select`. |
| 5045 | Klasse `Zend_Db_Adapter_Pdo_Mysql` is beperkt | Voorgestelde vervanging: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | Klasse `Magento\Framework\Serialize\Serializer\Serialize` is beperkt | Voorgestelde vervanging: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | Klasse `ArrayObject` is beperkt | Suggesties voor vervanging: aangepaste klasse, uitgebreid van `ArrayObject` met overschreven serialize/unserialize methodes. |
| 5048 | Klasse `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` is beperkt | Suggesties voor vervanging: in de fabriek wordt een aangepaste klasse gemaakt, uitgebreid van `ArrayObject` met overschreven serialize/unserialize methodes. |
| 5050 | Het blok waarnaar wordt verwezen, wordt verwijderd | Verwijzing naar blok verwijderen. |
| 5051 | `output="toHtml"` is verouderd | Gebruiken `output="1"`. |
| 5052 | De klasse `\Magento\Framework\View\Element\Text\ListText` niet meer in layout wordt gebruikt | Klasse verwijderen `\Magento\Framework\View\Element\Text\ListText` van layout. |
| 5053 | Aanroep van methode via indelingsinstructie `<action>` is niet toegestaan | Vermijd het gebruik van de desbetreffende methode in `<action>`. |
| 5054 | `helper` attribute contains `/` | Verwijderen `/` van helperkenmerk. |
| 5055 | `helper` attribute does not contain `::` | Toevoegen `::` naar helper, kenmerk. |
| 5056 | Scripts installeren is verouderd | Gebruik declaratieve schemabenadering in module \&#39;s etc/db_schema.xml- dossier. |
| 5057 | Scripts voor InstallSchema zijn verouderd | Gebruik declaratieve schemabenadering in module \&#39;s etc/db_schema.xml- dossier. |
| 5058 | InstallData-scripts zijn verouderd | Gebruik gegevenspatches in de map Setup/Patch/Data van module. |
| 5059 | Scripts installeren is verouderd | Maak een klasse InstallData in de map Setup van de module. |
| 5060 | Upgradescripts zijn verouderd | Gebruik declaratieve schemabenadering in module \&#39;s etc/db_schema.xml- dossier. |
| 5061 | UpgradeSchema-scripts zijn verouderd | Gebruik declaratieve schemabenadering in module \&#39;s etc/db_schema.xml- dossier. |
| 5062 | UpgradeData-scripts zijn verouderd | Gebruik gegevenspatches in de map Setup/Patch/Data van module. |
| 5063 | Upgradescripts zijn verouderd | De de flardbenadering van het gebruik van gegevenspatches in de module \ van de Opstelling/van het Patch/van Gegevens dir. |
| 5064 | Terugkerende scripts zijn verouderd | Klasse Terugkeren maken in de map Setup van de module. |
| 5065 | &#39;data&#39; staat in een ongeldige map | Creeer een gegevenspatch binnen de omslag van de Opstelling/van het Patch/van Gegevens van de module voor gegevensverbeteringen of gebruik verklarende schemabenadering in het dossier van module etc/db_schema.xml voor schemaveranderingen. |
| 5066 | &#39;sql&#39; staat in een ongeldige map | Creeer een gegevenspatch binnen de omslag van de Opstelling/van het Patch/van Gegevens van de module voor gegevensverbeteringen of gebruik verklarende schemabenadering in het dossier van module etc/db_schema.xml voor schemaveranderingen. |
| 5067 | Knooppunten die door XPath worden geïdentificeerd zijn verouderd | Verouderde XML-code die in de fout is vermeld, moet worden bijgewerkt. Volg de suggesties in het foutbericht. |
| 5068 | Richtlijn `{{htmlescape}}` is verouderd | Gebruiken `{{var}}` in plaats daarvan. |
| 5069 | Richtlijn `{{escapehtml}}` is verouderd | Gebruiken `{{var}}` in plaats daarvan. |
| 5070 | De derde parameter is niet meer nodig voor `getChildHtml()` | 3de parameter van vraag verwijderen aan `getChildHtml()`. |
| 5071 | De vierde parameter is niet meer nodig voor `getChildHtml()` | Vierde parameter verwijderen van aanroep naar `getChildHtml()`. |
| 5073 | Oudere tabelnamen met schuine streep moeten worden gecorrigeerd voor directe tabelnamen | Gebruik in plaats hiervan de directe tabelnaam. |
| 5075 | Toepassingsmodules mogen geen klassen uit testmodules gebruiken | Gebruik van klassen uit testmodules verwijderen. |
| 5078 | Klasse moet in constructor worden aangevraagd, anders kan compiler deze klassen niet vinden en genereren | Klasse toevoegen aan constructor. |
| 5079 | Het gebruik van variabelen van var-klassen wordt afgeraden | Gebruik &#39;var&#39; niet om een klassevariabele te declareren. |
| 5080 | Mogelijke onbewerkte SQL-instructie gedetecteerd | Gebruik in plaats hiervan repositories of gegevenspatches. |
| 5081 | Het gebruik van hulpstukken in sjablonen wordt afgeraden | Gebruik in plaats hiervan ViewModel. |
| 5082 | Het gebruik van $this in sjablonen is afgekeurd | Gebruik in plaats hiervan $block. |
| 5083 | Constanten zijn niet toegestaan als het eerste argument van een vertaalfunctie | Gebruik in plaats hiervan letterlijke tekenreeks. |
| 5085 | Het gebruik van bepaalde functies wordt afgeraden | Gebruik in plaats hiervan de alternatieve functie die op het bericht wordt geadviseerd. |
| 5087 | Probleem met compatibiliteit met PHP-kruisversies | Volg de suggesties in het bericht en controleer de [migratiehulplijn](https://www.php.net/manual/en/migration81.php). |
| 5088 | Optionele parameters gevonden na vereiste parameters | Verplaats vereiste parameters na optionele parameters. |
| 5089 | Zichtbaarheid van methode `final private` gevonden | Zichtbaarheid methode wijzigen vanuit `final private` alleen `private`. |
| 5090 | Magisch, methode `__set_state` is niet gedefinieerd als `static` | Magisch, methode `__set_state` moet worden gedefinieerd als `static`. |
| 5091 | Klasse met `__toString()` methode niet overerven van `Stringable` interface | Toevoegen `Stringable` interface naar klasse met `__toString()` methode. |
| 5092 | `is_resource()` methode gebruikt voor functies die nu Object retourneren | Wijzigen `is_resource()` tot `instanceof` Object. |
| 6001 | `jQuery.andSelf()` verwijderd | Gebruiken `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` en `$.unbind` zijn afgekeurd | Gebruiken `$.on` en `$.off` in plaats daarvan. |
| 6003 | De jQuery-methode voor abonneren op gebeurtenis is afgekeurd en mag niet worden gebruikt | Gebruiken `.on("event name", fn)` in plaats van zich op die gebeurtenis te abonneren. |
| 6003 | jQuery-methode om gebeurtenis te activeren is afgekeurd en mag niet worden gebruikt | Gebruiken `.trigger("event name")` in plaats daarvan om die gebeurtenis te activeren. |
| 6004 | jQuery `$.delegate` en `$.undelegate` zijn afgekeurd | Gebruiken `$.on` en `$.off` in plaats daarvan. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) is verwijderd | Gebruik (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`). |
| 6006 | `jQuery.size()` verwijderd | Gebruiken `jQuery.length`. |
| 6007 | `jQuery.trim` is vervangen | Gebruiken `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, thema &#39;inlite&#39;, thema &#39;mobile&#39;, thema &#39;modern&#39;) is verwijderd | Code bijwerken om compatibel te zijn met tinymce5. |
| 6009 | `jQuery.isFunction()` is vervangen | In de meeste gevallen kan het worden vervangen door [typeof x == &quot;function&quot;]. |
| 6009 | `jQuery.type()` is vervangen | Vervangen door een typecontrole zoals [typeof x == &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` is vervangen | Gebruik in plaats hiervan de methode native Array.isArray. |
| 6009 | `jQuery.parseJSON()` is vervangen | Als u JSON-tekenreeksen wilt parseren, gebruikt u in plaats daarvan de native JSON.parse-methode. |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) is vervangen | Gebruik in plaats hiervan jQuery.expr.pseudo. |

{style="table-layout:auto"}

### DB-schema

De fouten van het schema van OB worden opgeheven als de gegevensbestandlijsten, de kolommen, de indexen of de beperkingen, die in de versie van doelAdobe Commerce worden toegevoegd of worden verwijderd, in conflicten met het schema van het douanegegevensbestand kunnen resulteren.

| Foutcode | Foutbeschrijving | Voorgestelde actie |
| --- | --- | --- |
| 7001 | De doelkernversie introduceert een tabel met dezelfde naam als een tabel die is gedeclareerd door een aangepaste module | De nieuwe kerntabel gebruiken (indien van toepassing) of de naam van de aangepaste tabel wijzigen |
| 7002 | De kernlijst die door een douanemodule wordt uitgebreid werd verwijderd in de doelversie | Alle verwijderde verwijzingen naar kerntabellen moeten uit de codebase worden verwijderd |
| 7003 | De doelkernversie introduceert een kolom met de zelfde naam zoals een kolom die door een douanemodule wordt verklaard | De nieuwe kernkolom gebruiken (indien van toepassing) of de naam van de aangepaste kolom wijzigen |
| 7004 | De kernkolom die door een douanemodule wordt uitgebreid werd verwijderd in de doelversie | Alle verwijderde verwijzingen naar kernkolommen moeten uit de codebase worden verwijderd |
| 7005 | De doelkernversie introduceert een index met zelfde referenceId zoals een index die door een douanemodule wordt verklaard | Verwijderen (als gedupliceerd naar de nieuwe kernindex) of de naam van de aangepaste index wijzigen |
| 7006 | De kernindex die met een aangepaste module is uitgebreid, is verwijderd uit de doelversie | Alle verwijderde verwijzingen naar de kernindex moeten uit de codebase worden verwijderd |
| 7007 | De doelkernversie introduceert een beperking met dezelfde naam als een beperking die is gedeclareerd door een aangepaste module | Verwijderen (als deze waarde gelijk is aan de nieuwe kernbeperking) of de naam van de aangepaste restrictie wijzigen |
| 7008 | De kernbeperking die door een douanemodule wordt uitgebreid werd verwijderd in de doelversie | Gebruik de nieuwe kernbeperking (indien van toepassing) of wijzig de naam van de aangepaste restrictie |

{style="table-layout:auto"}

## Waarschuwingen

### Basiscode

Deze waarschuwingen worden gemeld wanneer er kleine inconsistenties zijn in de kerncodebase.

| Foutcode | Foutbeschrijving | Voorgestelde actie |
| --- | --- | --- |
| 2004 | Versie composerafhankelijkheid komt niet overeen | De kwestie wijst erop dat de versie van de afhankelijkheid van Composer in metalon en daadwerkelijke project verschillend is. Afhankelijkheid bijwerken door uit te voeren `composer update <package_name>`. |

{style="table-layout:auto"}

### Aangepaste code

Aangepaste waarschuwingen voor de code worden weergegeven wanneer verwijzingen naar afgekeurde code worden gedetecteerd. Dergelijke verwijzingen moeten worden vervangen door de ondersteunde extensiepunten. Let op de `@see` aantekening van vervangen item voor aanbevelingen. Deze fouten worden ook gemeld wanneer minder belangrijke coderingsnormen zijn overtreden.

| Foutcode | Foutbeschrijving | Voorgestelde actie |
| --- | --- | --- |
| 1131 | Uitbreiding vanuit Adobe Commerce ``@deprecated`` class | De uitgebreide klasse wordt in toekomstige versies verwijderd. Overerving wordt niet aanbevolen voor het uitbreiden van de Adobe Commerce-functionaliteit. Code bijwerken voor het gebruik van een klasse die is gemarkeerd als `@api`. |
| 1132 | Adobe Commerce importeren `@deprecated` class | De uitgebreide klasse wordt in toekomstige versies verwijderd. Gebruik Adobe Commerce-klasse die is gemarkeerd als `@api` in plaats daarvan. |
| 1133 | Adobe Commerce laden `@deprecated` class | De uitgebreide klasse wordt in toekomstige versies verwijderd. Gebruik Adobe Commerce-klasse die is gemarkeerd als `@api` in plaats daarvan. |
| 1134 | Adobe Commerce gebruiken `@deprecated` class | De uitgebreide klasse wordt in toekomstige versies verwijderd. Gebruik Adobe Commerce-klasse die is gemarkeerd als `@api` in plaats daarvan. |
| 1234 | Adobe Commerce gebruiken `@deprecated` constante | De vervangen constante wordt in de volgende versies verwijderd. Gebruik een constante die is gemarkeerd als `@api` of een privéconstante in uw implementatie. |
| 1235 | Adobe Commerce overschrijven `@deprecated` constante | De vervangen constante wordt in de volgende versies verwijderd. Gebruik een constante die is gemarkeerd als `@api` of een privéconstante in uw implementatie. |
| 1236 | Toewijzing van Adobe Commerce `@deprecated` constante | De vervangen constante wordt in de volgende versies verwijderd. Gebruik een constante die is gemarkeerd als `@api` of een privéconstante in uw implementatie. |
| 1332 | Geïmporteerde Adobe Commerce `@deprecated` interface | De vervangen interface wordt in de volgende versies verwijderd. Gebruik een interface of klasse die is gemarkeerd als `@api` in plaats daarvan. |
| 1334 | Gebruikte Adobe Commerce `@deprecated` interface | De vervangen interface wordt in de volgende versies verwijderd. Gebruik een interface of klasse die is gemarkeerd als `@api` in plaats daarvan. |
| 1337 | Overgenomen uit Adobe Commerce `@deprecated` interface | De vervangen interface wordt in de volgende versies verwijderd. U kunt overwegen de interfaceovererving te verwijderen door een interface te gebruiken die als `@api` of een interface die in plaats daarvan binnen uw implementatie wordt geïntroduceerd. |
| 1338 | Geïmplementeerde Adobe Commerce `@deprecated` interface | De vervangen interface wordt in de volgende versies verwijderd. U kunt overwegen de interfaceovererving te verwijderen door een interface te gebruiken die als `@api` of een interface die in plaats daarvan binnen uw implementatie wordt geïntroduceerd. |
| 1430 | Niet-gedeclareerde gegevensobjectmethode aanroepen | De magische methoden die niet worden gedeclareerd, kunnen worden gewijzigd. U kunt in plaats daarvan ook op interfacemethoden vertrouwen. |
| 1439 | Adobe Commerce bellen `@deprecated` methode | De vervangen methode wordt in de volgende versies verwijderd. U kunt in plaats daarvan ook vertrouwen op methoden die zijn gedeclareerd in API-interfaces. |
| 1440 | Verkeerde methodehandtekening | Een aanroep of overschrijving van de kernmethode wordt gedetecteerd met parameters, argumenten of retourneringstype die niet overeenkomen met de methodehandtekening. |
| 1534 | Adobe Commerce gebruiken `@deprecated` eigenschap | De vervangen methode wordt in de volgende versies verwijderd. U kunt in plaats daarvan ook vertrouwen op methoden die zijn gedeclareerd in API-interfaces. |
| 1535 | Adobe Commerce overschrijven `@deprecated` eigenschap | De vervangen eigenschap wordt in de volgende versies verwijderd. U kunt ook vertrouwen op methoden die zijn gedeclareerd in API-interfaces of op het gebruik van een eigenschap van het type private in uw implementatie. |
| 1536 | Toewijzing van Adobe Commerce `@deprecated` eigenschap | De vervangen methode wordt in de volgende versies verwijderd. U kunt in plaats daarvan ook vertrouwen op methoden die zijn gedeclareerd in API-interfaces. |
| 5006 | Proxy&#39;s en afluisteraars MOGEN nooit expliciet worden aangevraagd in constructors | De oorspronkelijke klasse moet worden gedeclareerd als een type van de constructorparameter. De Interceptor/Proxy-klasse wordt doorgegeven door de injectie-implementatie van frameafhankelijkheden. |
| 5074 | Gebruik van afgekeurde methode `getResource()` aan (sparen / laden / verwijderen) gegevens gedetecteerd. | Gebruik in plaats hiervan een repository. |
| 5086 | Zichtbaarheid wordt niet gedeclareerd op een constante | Declareer de zichtbaarheid van alle constanten. |

{style="table-layout:auto"}

### GraphQL Schema

De waarschuwingen van het Schema van GraphQL worden opgeheven wanneer de extra punten aan het schema in de nieuwe versie worden toegevoegd. Het wordt aanbevolen de implementatie te herzien om te zien of deze voor verzoeken moeten worden gebruikt.

| Foutcode | Foutbeschrijving | Voorgestelde actie |
| --- | --- | --- |
| 3206 | Standaardwaarde argument gewijzigd | Als de vraag in de aanpassing wordt gebruikt, kan de argumentwaarde uitdrukkelijk moeten worden gespecificeerd. |
| 3302 | Tekst toegevoegd aan samenvoeging | Het type is toegevoegd aan de union. Controleer de implementatie die het resultaat verwerkt van de query die dit vaktype retourneert en zorg ervoor dat het toegevoegde type kan verwerken. |
| 3304 | Optioneel invoerveld toegevoegd | Optioneel invoerveld toegevoegd. Controleer de implementatie om te controleren. |
| 3305 | Geïmplementeerde interface toegevoegd | Het veld kan meer informatie accepteren/verstrekken die in overweging kan worden genomen bij de implementatie. |
| 3306 | Waarde toegevoegd aan opsommingswaarde | Er is een waarde toegevoegd aan een opsomming. Als de cliënten een schakelaarverklaring op de waarde van de opsomming bevatten en geen standaardgeval omvatten, zou deze verandering onverwacht gedrag kunnen veroorzaken. |
| 3308 | Optioneel argument toegevoegd | Als de vraag een nieuw argument in de aanpassing gebruikt kan het aan het verzoek moeten worden toegevoegd. |

{style="table-layout:auto"}
