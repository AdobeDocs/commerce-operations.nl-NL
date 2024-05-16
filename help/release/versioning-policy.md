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

Adobe Commerce gebruikt [semantische versie](https://semver.org/) op het niveau van de afzonderlijke modules (bijvoorbeeld `magento/framework 101.1.1`), maar niet voor het versienummer van de marketingversie. Bijvoorbeeld:

- **MAJOR release**—2
- **MINOR release**—2,4
- **PATCH release**—2.4.5
   - **VEILIGHEIDSpatchrelease**—2.4.5-p1
      - Beveiligingsfout verhelpen
      - Verbeterde beveiliging
- **BÈTA-patchrelease**—2.4.7-bèta2
- **Uitzetbaarheid, Infrastructuur en de versie van de Diensten**
- **Hotfix**
- **Individuele patch**
- **Aangepaste patch**

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

## BÈTA-patchrelease

De pre-algemene beschikbaarheidsversies van de eigenschappen van Adobe Commerce worden openbaar gemaakt aan alle klanten van Adobe Commerce en Adobe partners. Het staat voor extra tijd vóór Algemene Beschikbaarheid toe om code en beïnvloede componenten te herzien.

Bètareleases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. De Adobe zal niet verplicht zijn om (via de Diensten van de Steun van de Adobe of anderszins) de Versies van Beta te handhaven, te verbeteren, bij te werken, te veranderen, te wijzigen, of anders te steunen. Klanten wordt aangeraden voorzichtig te zijn en op geen enkele wijze te vertrouwen op de correcte werking of prestaties van de bètareleases en/of begeleidende documentatie of materialen. Daarom is elk gebruik van de bètareleases volledig op eigen risico van de klant.

## Uitzetbaarheid, Infrastructuur en de versie van de Diensten

De versies van de eigenschap die nieuwe eigenschappen en eigenschapupdates bevatten die als onafhankelijke diensten, los van flardversies worden geleverd. Voorbeelden zijn uitbreidbaarheidstechnologie zoals API Mesh en Event, SaaS-producten zoals Product Recommendations en Live Search, onafhankelijke modules zoals B2B en PWA Studio, en updates voor onze cloudhostingservices en -infrastructuur.

## Hotfix

Hotfixes zijn flarden die high-impact veiligheid of kwaliteitsmoeilijke situaties, zoals moeilijke situaties aan nul-dag kwetsbaarheid bevatten, die vele verkopers beïnvloeden. Adobe geeft hotfixes voor Adobe Commerce-versies vrij die nog steeds worden ondersteund en waar nodig worden beïnvloed door kritieke beveiligings- of kwaliteitsproblemen. Hotfixes worden gepubliceerd naar de [Sectie Bekende problemen](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) van onze kennisbasis. Deze correcties zijn opgenomen in de volgende geplande patchrelease.

>[!NOTE]
>
>Hotfixes kunnen achterwaartse onverenigbare veranderingen bevatten.

## Individuele patch

Afzonderlijke patches bevatten oplossingen voor een bepaalde kwestie met een lage-effectkwaliteit. Deze correcties worden toegepast op de ondersteunde kleine versies van Adobe Commerce. Adobe geeft individuele pleisters vrij zoals nodig voor Adobe Commerce overeenkomstig onze [Levenscyclusbeleid software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Afzonderlijke patches bevatten geen achterwaartse incompatibele wijzigingen.

## Aangepaste patch

Gemaakt door personeel van een andere Adobe om een probleem op te lossen of de Adobe Commerce-code om verschillende redenen te wijzigen. Aangepaste patches worden geleverd via de [Gereedschap Kwaliteitspatches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Verwante onderwerpen

- [Versioning](https://developer.adobe.com/commerce/php/development/versioning/)
- [Volgende releases](schedule.md)
- [Levenscyclusbeleid software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
