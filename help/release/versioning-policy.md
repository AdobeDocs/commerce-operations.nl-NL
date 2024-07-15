---
title: Releasebeleid
description: Leer meer over de verschillende typen Adobe Commerce-releases, zoals kleine patches, beveiligingspatches, functies, hotfix, afzonderlijke patches en aangepaste patches.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Adobe Commerce-releasebeleid

Adobe Commerce gebruikt [ semantische versioning ](https://semver.org/) op het individuele moduleniveau (bijvoorbeeld `magento/framework 101.1.1`), maar niet voor het marketing versieaantal. Bijvoorbeeld:

- **MAJOR versie** - 2
- **MINDERE versie** - 2.4
- **versie van PATCH** - 2.4.5
   - **de flardversie van de BEVEILIGING**-2.4.5-p1
      - Beveiligingsfout verhelpen
      - Verbeterde beveiliging
- **de flardversie van BETA**-2.4.7-beta2
- **Vermogen van de Uitbreidbaarheid, van de Infrastructuur, en van de Diensten**
- **Hotfix**
- **Individueel flard**
- **Eigen flard**

## MINOR release

De volgende richtsnoeren zijn van toepassing op kleine introducties:

- Breukwijzigingen zijn mogelijk; code die is geschreven voor Adobe Commerce 2.2.x werkt mogelijk niet meer met Adobe Commerce 2.3.x. Kleine versies kunnen bijvoorbeeld ondersteuning introduceren voor belangrijke systeemvereisten en afhankelijkheden, zoals PHP.
- De versies van de module kunnen variëren. Sommige modulewijzigingen worden bijvoorbeeld in een nieuwe patch geïntroduceerd, terwijl andere in een kleine release worden geïntroduceerd.
- De kleine versies kunnen nieuwe eigenschappen omvatten die extra werk door u of uw oplossingspartner tijdens verbetering kunnen vereisen om verenigbaarheid te verzekeren.
- Kleine releases kunnen oplossingen voor beveiligings- en kwaliteitsproblemen bevatten.

## PATCH release

Patchreleases zijn vooral gericht op het bieden van oplossingen voor beveiliging, prestaties, naleving en hoge prioriteit, zodat uw sites optimaal presteren.

De volgende richtlijnen zijn van toepassing op patchreleases:

- De nieuwste, ondersteunde secundaire release ontvangt oplossingen en verbeteringen voor volledige functionele kwaliteit.
- Wijzigingen die extensies of compatibiliteit met code kunnen onderbreken, worden vermeden. Code die is geschreven voor versie 2.2.0 werkt bijvoorbeeld nog steeds op versie 2.2.7.
- Bij wijze van uitzondering kunnen verbreken van wijzigingen of extra patches of hotfixes worden vrijgegeven om beveiligings- of nalevingsproblemen en kwaliteitsproblemen met een hoog effect aan te pakken. Op moduleniveau, zijn dit meestal PATCH-vlakke veranderingen; soms kleine veranderingen.

### VEILIGHEIDSpatchrelease

{{$include /help/_includes/security-patch-release-overview.md}}

## BETA patch release

De pre-algemene beschikbaarheidsversies van de eigenschappen van Adobe Commerce worden openbaar gemaakt aan alle klanten van Adobe Commerce en Adobe partners. Het staat voor extra tijd vóór Algemene Beschikbaarheid toe om code en beïnvloede componenten te herzien.

Beta-releases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht om de Beta-releases te onderhouden, te corrigeren, bij te werken, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Klanten wordt aangeraden voorzichtig te zijn en op geen enkele wijze te vertrouwen op de correcte werking of prestaties van de Beta-releases en/of begeleidende documentatie of materialen. Daarom is elk gebruik van de Beta-releases volledig op eigen risico van de Klant.

## Uitzetbaarheid, Infrastructuur en de versie van de Diensten

De versies van de eigenschap die nieuwe eigenschappen en eigenschapupdates bevatten die als onafhankelijke diensten, los van flardversies worden geleverd. Voorbeelden zijn uitbreidbaarheidstechnologie zoals API Mesh en Event, SaaS-producten zoals Product Recommendations en Live Search, onafhankelijke modules zoals B2B en PWA Studio, en updates voor onze cloudhostingservices en -infrastructuur.

## Hotfix

Hotfixes zijn flarden die high-impact veiligheid of kwaliteitsmoeilijke situaties, zoals moeilijke situaties aan nul-dag kwetsbaarheid bevatten, die vele verkopers beïnvloeden. Adobe geeft hotfixes voor Adobe Commerce-versies vrij die nog steeds worden ondersteund en waar nodig worden beïnvloed door kritieke beveiligings- of kwaliteitsproblemen. Hotfixes worden gepubliceerd aan de [ Bekende sectie van Kwesties ](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) van onze Kennisbank. Deze correcties zijn opgenomen in de volgende geplande patchrelease.

>[!NOTE]
>
>Hotfixes kunnen achterwaartse onverenigbare veranderingen bevatten.

## Individuele patch

Afzonderlijke patches bevatten oplossingen voor een bepaalde kwestie met een lage-effectkwaliteit. Deze correcties worden toegepast op de ondersteunde kleine versies van Adobe Commerce. De Adobe geeft individuele flarden zoals nodig voor Adobe Commerce in overeenstemming met ons [ Beleid van de Levenscyclus van de Software ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf) vrij.

>[!NOTE]
>
>Afzonderlijke patches bevatten geen achterwaartse incompatibele wijzigingen.

## Aangepaste patch

Gemaakt door personeel van een andere Adobe om een probleem op te lossen of de Adobe Commerce-code om verschillende redenen te wijzigen. De flarden van de douane worden geleverd door het [ Hulpmiddel van de Patches van de Kwaliteit ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Verwante onderwerpen

- [ Versioning ](https://developer.adobe.com/commerce/php/development/versioning/)
- [Volgende releases](schedule.md)
- [ Beleid van de Levenscyclus van de Software ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
