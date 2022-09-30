---
title: Releasebeleid
description: Leer meer over de verschillende typen Adobe Commerce-releases, zoals kleine patches, beveiligingspatches, functies, hotfix, afzonderlijke patches en aangepaste patches.
source-git-commit: 79f36e3728e6bc436e8093bd4051143a48e681d6
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 0%

---


# Adobe Commerce-releasebeleid

Adobe Commerce en Magento Open Source gebruiken [semantische versie](https://semver.org/) op het niveau van de afzonderlijke modules (bijvoorbeeld `magento/framework 101.1.1`), maar niet voor het versienummer van de marketingversie. Bijvoorbeeld:

- **MAJOR release**—2
- **MINOR release**—2,4
- **PATCH release**—2.4.1
   - **VEILIGHEIDSpatchrelease**—2.4.1-p1
      - Beveiligingsfout verhelpen
      - Verbeterde beveiliging
- **Functierelease**
- **Hotfix**
- **Individuele patch**
- **Aangepaste patch**

## MINOR release

De volgende richtsnoeren zijn van toepassing op kleine introducties:

- Scheidingswijzigingen zijn mogelijk; code geschreven voor Adobe Commerce 2.2.x werkt mogelijk niet meer met Adobe Commerce 2.3.x. Bijvoorbeeld, kunnen de minder belangrijke versies steun voor belangrijke systeemvereisten en gebiedsdelen, zoals PHP introduceren.
- De versies van de module kunnen variëren. Sommige modulewijzigingen worden bijvoorbeeld in een nieuwe patch geïntroduceerd, terwijl andere in een kleine release worden geïntroduceerd.
- De kleine versies kunnen nieuwe eigenschappen omvatten die extra werk door u of uw oplossingspartner tijdens verbetering kunnen vereisen om verenigbaarheid te verzekeren.
- Kleine releases kunnen oplossingen voor beveiligings- en kwaliteitsproblemen bevatten.

## PATCH release

Patchreleases zijn vooral gericht op het bieden van oplossingen voor beveiliging, prestaties, naleving en hoge prioriteit, zodat uw sites optimaal presteren.

De volgende richtlijnen zijn van toepassing op patchreleases:

- De nieuwste, ondersteunde secundaire release ontvangt oplossingen en verbeteringen voor volledige functionele kwaliteit.
- Wijzigingen die extensies of compatibiliteit met code kunnen onderbreken, worden vermeden. Code die is geschreven voor versie 2.2.0 werkt bijvoorbeeld nog steeds op versie 2.2.7.
- Bij wijze van uitzondering kunnen verbreken van wijzigingen of extra patches of hotfixes worden vrijgegeven om beveiligings- of nalevingsproblemen en kwaliteitsproblemen met een hoog effect aan te pakken. Op moduleniveau zijn dit meestal veranderingen op PATCH-niveau; soms kleine wijzigingen.

## VEILIGHEIDSpatchrelease

**Opgeloste beveiligingsproblemen**: Een wijziging in de softwarecode die een geïdentificeerd beveiligingsprobleem verhelpt en verwachte resultaten oplevert in een betrokken productgebied. Deze correcties zijn over het algemeen compatibel met oudere versies.

**Verbeterde beveiliging**: Een softwareverbetering of configuratieverandering om de veiligheid binnen de toepassing proactief te verbeteren. Deze beveiligingsverbeteringen helpen beveiligingsrisico&#39;s aan te pakken die van invloed zijn op de beveiligingspositie van de Adobe Commerce-toepassing, maar die mogelijk niet compatibel zijn met oudere versies.

Met beveiligingspatchreleases kunt u uw site veiliger houden zonder aanvullende kwaliteitsoplossingen en -verbeteringen toe te passen die zijn opgenomen in een volledige driemaandelijkse patchrelease. Beveiligingspatchreleases worden toegevoegd met &#39;-pN&#39;, waarbij N de incrementele patchversie is die begint met 1 (bijvoorbeeld 2.3.5-p1). Beveiligingspatchreleases kunnen ook hotfixes bevatten die vereist zijn om kritieke problemen die de Adobe Commerce-toepassing beïnvloeden, aan te pakken.

Elke beveiligingspatchrelease is gebaseerd op de vorige volledige patchrelease. Het bevat kwaliteits- en beveiligingsoplossingen van eerdere patchreleases en beveiligingsoplossingen die zijn gemaakt tussen de vorige volledige patchrelease en de beveiligingspatchrelease.

Met de aankondiging van onze [nieuwe releasestrategie en bijgewerkt levenscyclusbeleid](https://business.adobe.com/blog/how-to/accelerating-innovation-through-simplified-release-strategy) (16-09-2021), worden onze beveiligingspatchreleases gedifferentieerd op basis van de vraag of ze van toepassing zijn op de meest recente ondersteunde secundaire release of een onderdeel van een eerder gemaakte, minder belangrijke release met nog steeds ondersteuning:

- **Beveiligingspatchreleases voor de meest recente ondersteunde secundaire release**:

   - De beveiligingspatchrelease voor de meest recente ondersteunde secundaire release (momenteel Adobe Commerce 2.4) bevat:

      - Beveiligingsproblemen zijn opgelost die zijn gemaakt sinds de vorige volledige patchrelease.

      - Deze beveiligingspatchreleases kunnen ook hotfixes bevatten die nodig zijn om kritieke problemen op te lossen die de Adobe Commerce-toepassing kunnen beïnvloeden.
   - De beveiligingspatchrelease voor de meest recente ondersteunde secundaire release (momenteel Adobe Commerce 2.4) bevat doorgaans geen beveiligingsverbeteringen. In plaats daarvan worden deze meegeleverd in de volledige patchrelease voor de meest recente ondersteunde secundaire release.


- **Beveiligingspatchreleases voor ondersteunde eerdere secundaire releases**:

   - De beveiligingspatchrelease voor een vorige secundaire release die nog wordt ondersteund (momenteel Adobe Commerce 2.3) bevat:

      - Beveiligingsproblemen verhelpen die zijn gemaakt sinds de vorige patch- of beveiligingspatchrelease en nieuwe beveiligingsverbeteringen.

      - Deze beveiligingspatchreleases kunnen ook hotfixes bevatten die nodig zijn om kritieke problemen op te lossen die van invloed zijn op de Adobe Commerce-toepassing.

      |  | Beveiligingsfout | Verbeterde beveiliging |
      |--------------------------------------------------------------------------------|--------------|----------------------|
      | Beveiligingspatchreleases voor de meest recente ondersteunde secundaire release (momenteel 2.4) | X |  |
      | Beveiligingspatchreleases voor vorige, ondersteunde secundaire releases (momenteel 2.3) | X | X |


Voor algemene informatie over veiligheidsversies, zie [Introductie van de nieuwe beveiligings-enige Versie van de Reparatie](https://community.magento.com:443/t5/Magento-DevBlog/Introducing-the-New-Security-Patch-Release/ba-p/141287). Voor instructies over het downloaden en toepassen van beveiligingspatches raadpleegt u [Snelle start met installeren](../installation/composer.md).

## Functierelease

De versies van de eigenschap bevatten nieuwe eigenschappen en eigenschapsupdates die als onafhankelijke diensten, los van de flardversies worden geleverd. Voorbeelden zijn services zoals Product Recommendations en Live Search, onafhankelijke modules zoals PWA Studio en Inventory management (MSI) en updates voor onze cloudservices en -infrastructuur.

## Hotfix

Hotfixes zijn flarden die high-impact veiligheid of kwaliteitsmoeilijke situaties, zoals moeilijke situaties aan nul-dag kwetsbaarheid bevatten, die vele verkopers beïnvloeden. Adobe geeft hotfixes voor Adobe Commerce-versies uit die nog steeds worden ondersteund en waar nodig worden beïnvloed door kritieke beveiligings- of kwaliteitsproblemen. Hotfixes worden gepubliceerd naar de [Sectie Bekende problemen](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) van onze kennisbasis. Deze correcties zijn opgenomen in de volgende geplande patchrelease.

>[!NOTE]
>
>Hotfixes kunnen achterwaartse onverenigbare veranderingen bevatten.

## Individuele patch

Afzonderlijke patches bevatten oplossingen voor een bepaalde kwestie met een lage-effectkwaliteit. Deze correcties worden toegepast op de ondersteunde kleine versies van Adobe Commerce. Adobe geeft individuele pleisters vrij zoals nodig voor Adobe Commerce in overeenstemming met onze [Levenscyclusbeleid software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!NOTE]
>
>Afzonderlijke patches bevatten geen achterwaartse incompatibele wijzigingen.

## Aangepaste patch

Gemaakt door niet-Adobe-personeel om een probleem op te lossen of om verschillende redenen de Adobe Commerce-code te wijzigen. Aangepaste patches worden geleverd via de [Kwaliteitspatches](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).

## Verwante onderwerpen

- [Planning en budgettering voor upgradecycli voor handel](https://magento.com/sites/default/files8/2019-08/Magento-Release-Cycle-Infosheet_Aug_2019.pdf)
- [Versioning](https://developer.adobe.com/commerce/php/development/versioning/)
- [Volgende releases](schedule.md)
- [Levenscyclusbeleid software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
