---
title: Releasebeleid
description: Meer informatie over de verschillende typen Adobe Commerce-releases.
exl-id: 61a83de6-6a7b-4a88-8fff-1638b4fe472a
source-git-commit: 0ea8c2bfffe81d27547c0330abdd75fc078542cf
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# Adobe Commerce-releasebeleid

Adobe Commerce gebruikt [ semantische versioning ](https://semver.org/) op het individuele moduleniveau (bijvoorbeeld `magento/framework 101.1.1`), maar niet voor het marketing versieaantal. Bijvoorbeeld:

- **MAJOR versie** - 2
- **MINDERE versie** - 2.4
- **versie van PATCH** - 2.4.8
   - **de flardversie van de BEVEILIGING**-2.4.8-p1
      - Beveiligingsfout verhelpen
      - Verbeterde beveiliging
- **de flardversie van ALPHA**-2.4.8-alpha1
- **de flardversie van BETA**-2.4.8-beta1
- **Vermogen van de Uitbreidbaarheid, van de Infrastructuur, en van de Diensten**
- **Hotfix**
- **Individueel flard**
- **Eigen flard**

## MINOR release

De volgende richtsnoeren zijn van toepassing op kleine introducties:

- Breukwijzigingen zijn mogelijk; code die is geschreven voor Adobe Commerce 2.2.x werkt mogelijk niet meer met Adobe Commerce 2.3.x. Kleine versies kunnen bijvoorbeeld ondersteuning introduceren voor belangrijke systeemvereisten en afhankelijkheden, zoals PHP.
- De versies van de module kunnen variëren. Sommige modulewijzigingen worden bijvoorbeeld in een nieuwe patch geïntroduceerd, terwijl andere in een kleine release worden geïntroduceerd.
- De kleine versies kunnen nieuwe eigenschappen omvatten die extra werk door u of uw oplossingspartner tijdens een verbetering kunnen vereisen om verenigbaarheid te verzekeren.
- Kleine releases kunnen oplossingen voor beveiligings- en kwaliteitsproblemen bevatten.

## PATCH-release

Patchreleases zijn vooral gericht op het bieden van oplossingen voor beveiliging, prestaties, naleving en hoge prioriteit, zodat uw sites optimaal presteren.

De volgende richtlijnen zijn van toepassing op patchreleases:

- De nieuwste, ondersteunde secundaire release ontvangt oplossingen en verbeteringen voor volledige functionele kwaliteit.
- Wijzigingen die extensies of compatibiliteit met code kunnen onderbreken, worden vermeden. Code die is geschreven voor versie 2.2.0 werkt bijvoorbeeld nog steeds op versie 2.2.7.
- Bij wijze van uitzondering kunnen verbreken van wijzigingen of extra patches of hotfixes worden vrijgegeven om beveiligings- of nalevingsproblemen en kwaliteitsproblemen met een hoog effect aan te pakken. Op moduleniveau zijn deze wijzigingen meestal op PATCH-niveau; soms op MINOR-niveau.

### VEILIGHEIDSpatchrelease

{{$include /help/_includes/release-notes/security-patch-overview.md}}

## ALPHA patch release

Pre-Beta releases van Adobe Commerce-functies worden openbaar gemaakt voor alle Adobe Commerce-klanten en Adobe-partners. Alpha-releases zijn bedoeld voor vroegtijdige feedback en evaluatie van functies die zich nog in actieve ontwikkeling bevinden. Deze releases bieden een mogelijkheid voor vroege test- en integratieplanning in de aanloop naar de Beta- en General Availability-releases.

Alpha-releases kunnen onvolledig zijn en kunnen waarschijnlijk defecten bevatten. Ze worden geleverd &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht om Alpha-releases te onderhouden, te corrigeren, bij te werken, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Klanten mogen niet vertrouwen op de correcte werking of prestaties van Alpha-releases of begeleidende documentatie of materialen. Het gebruik van Alpha-releases is volledig op eigen risico van de klant.

## BETA patch release

Pre-General Availability-releases van Adobe Commerce-functies worden openbaar gemaakt voor alle Adobe Commerce-klanten en Adobe-partners. Het staat voor extra tijd vóór Algemene Beschikbaarheid toe om code en beïnvloede componenten te herzien.

Beta-releases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht om Beta-releases te onderhouden, te corrigeren, bij te werken, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Klanten mogen niet vertrouwen op de correcte werking of prestaties van Beta-releases of begeleidende documentatie of materialen. Bijgevolg is elk gebruik van de Beta-releases volledig op eigen risico van een klant.

## Functies, cloudinfrastructuur en uitbreidingsrelease

Cloudinfrastructuur- en functiereleases bevatten nieuwe functies en functies-updates die als onafhankelijke services worden geleverd, apart van patchreleases. Voorbeelden zijn onder meer:

- Updates voor cloudhostservices en -infrastructuur
- B2B
- SaaS-producten (Catalog Service, Data Connection, Product Recommendations en Live Search)
- Uitbreidingstechnologie (Admin UI SDK, API Mesh, App Builder Starter Kits, Event, en Webhooks)

## Hotfix

Hotfixes zijn flarden die high-impact veiligheid of kwaliteitsmoeilijke situaties, zoals moeilijke situaties aan nul-dag kwetsbaarheid bevatten, die vele verkopers beïnvloeden. Adobe brengt hotfixes (indien nodig) voor ondersteunde Adobe Commerce-versies uit wanneer deze van invloed zijn op kritieke beveiligings- of kwaliteitsproblemen. Hotfixes worden gepubliceerd aan de [ Bekende sectie van Kwesties ](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) van de Kennisbank. Deze correcties zijn opgenomen in de volgende geplande patchrelease.

>[!NOTE]
>
>Hotfixes kunnen achterwaartse onverenigbare veranderingen bevatten.

## Individuele patch

Afzonderlijke patches bevatten oplossingen voor een bepaalde kwestie met een lage-effectkwaliteit. Deze correcties worden toegepast op de ondersteunde kleine versies van Adobe Commerce. Adobe geeft individuele flarden zoals nodig voor Adobe Commerce in overeenstemming met het [ Beleid van de Levenscyclus van de Software ](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf) vrij.

>[!NOTE]
>
>Afzonderlijke patches bevatten geen achterwaarts incompatibele wijzigingen.

## Geïsoleerde patch

Geïsoleerde patchescBevat een standalone moeilijke situatie die in het recentste veiligheid-enige flard of een aanstaande veiligheid-enige flard inbegrepen is, die afzonderlijk voor snellere implementatie wordt vrijgegeven.

## Aangepaste patch

Gemaakt door niet-Adobe-personeel om een probleem op te lossen of om verschillende redenen de Adobe Commerce-code te wijzigen. De flarden van de douane worden geleverd door het [ Hulpmiddel van de Patches van de Kwaliteit ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/usage).
