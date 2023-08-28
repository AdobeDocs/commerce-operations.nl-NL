---
title: Aanbevolen werkwijzen voor algemene ontwikkeling
description: Meer informatie over algemene best practices bij het ontwikkelen van Adobe Commerce-projecten.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor algemene ontwikkeling in Adobe Commerce

Dit onderwerp beschrijft de basislijn voor een gezond ontwikkelingsproces van Adobe Commerce. Hierin worden fundamentele processen, codeerbeginselen en ontwerpprincipes voor toepassingen beschreven om ontwikkelaars te begeleiden.

>[!NOTE]
>
>Technische architecten van de Adobe gebruiken deze beste praktijken als referentie tijdens overeenkomsten met betrekking tot ontwikkeling.

Deze beste praktijken zijn ontwikkeld op basis van jarenlange ervaring met het ontwikkelen en uitvoeren van handelsprojecten. De Adobe beveelt aan dat technische initiatieven deze beste praktijken volgen en dat u bestaande processen en code verbetert om met hen in overeenstemming te brengen.

## Tekstconventies

De sleutelwoorden &quot;MOET&quot;, &quot;MOET NIET&quot;, &quot;VEREIST&quot;, &quot;DIENT&quot;, &quot;DIENT NIET&quot;, &quot;DIENT NIET&quot;, &quot;AANBEVOLEN&quot;, &quot;MEI&quot; en &quot;OPTIONEEL&quot; in dit onderwerp moeten worden geïnterpreteerd zoals beschreven in [RFC 219](https://datatracker.ietf.org/doc/html/rfc2119).

## Proces

1. Voordat met de projectactiviteiten wordt begonnen, moet overeenstemming worden bereikt over een welomschreven projectmethode. Het kan gaan om een methode voor de bestrijding van trommel, waterval of een andere methodologie of combinatie van methoden, mits deze gedefinieerd is.
1. De ontwikkeling MOET NIET beginnen totdat het ontwikkelingsteam een vertakkingsstrategie voor het versiecontrolesysteem heeft.
1. De ontwikkeling MOET NIET beginnen na de aftekening van technische specificaties, de aftekening van gebruikersartikelen en gebruiksgevallen en de aftekening van testgevallen is beschikbaar voor het ontwikkelingsteam.
1. De ontwikkeling MAG NIET beginnen totdat ten minste een ontwikkelings- en kwaliteitscontroleomgeving beschikbaar is.
1. Projectspecifieke eisen die verplicht zijn voor het begin van de ontwikkeling, kunnen in een _Definitie van klaar_.
1. Afmelding DIENT te worden gedaan door een vertegenwoordiger van de klant die gemachtigd is om af te tekenen bij te leveren projecten.
1. In de methoden van het Agile-project kunnen aanvullende vereisten volgen. Deze eisen dienen als nieuwe eisen te worden beschouwd en dienen dienovereenkomstig te worden vastgelegd, opgesteld en gepland.
1. Alle ontwikkelingen MOETEN vóór de indiening door de ontwikkelaar functioneel worden getest.
1. Alle ontwikkelingen MOETEN geautomatiseerde tests doorstaan voordat ze worden ingediend voor herziening van de code. Dit kan als geautomatiseerd proces na het creëren van trekkingsverzoek worden gevormd.
1. Elke ontwikkeling MOET een technische architect of een ontwikkelaar met handmatige codecontrole doorstaan voordat deze voor kwaliteitsborging wordt ingediend.
1. Alle ontwikkelingen MOETEN een kwaliteitsborging doorstaan voordat zij aan de klant worden geleverd.
1. Projectspecifieke vereisten die verplicht zijn voor levering, kunnen worden gedocumenteerd in een &quot;Definitie van Gereed&quot;.

## Omgeving

1. Alle ontwikkelaars MOETEN zelfde winde gebruiken. PhpStorm is de aanbevolen IDE voor Adobe Commerce-ontwikkeling.
1. Alle ontwikkelaars MOETEN zich ontwikkelen en testen gebruikend de zelfde technologiestapel zoals die op de (toekomstige) productieservers wordt gebruikt. De versies van de software in deze technologiestapel MOETEN de belangrijkste en minder belangrijke versie van de software aanpassen die op de productieservers wordt geïnstalleerd. Zie [systeemvereisten](../../../installation/system-requirements.md) voor meer informatie over de typische technologiestapel voor Adobe Commerce.
1. De systeembeheerder of technische architect kan het team voorzien van een centraal onderhouden lokale ontwikkelomgeving om gelijke en actuele lokale omgevingen te verzekeren en te bevorderen.
1. De ontwikkelaars en de ingenieurs QA MOETEN toegang tot de bevellijn, het gegevensbestand, en de logboekdossiers van het milieu hebben QA. Dit kan een verbinding van VPN vereisen.

## Codeerstandaarden

1. Alle code DIENT conventies in architectuur, methodologie en coderingsnormen te volgen. Creativiteit is gewenst in functie, niet in vorm.
1. Alle code DIENT in overeenstemming te zijn met de [Adobe Commerce Architecture Guide](https://developer.adobe.com/commerce/php/architecture/){target="_blank}.
1. Alle code DIENT de [Adobe Commerce-coderingsstandaarden](https://developer.adobe.com/commerce/php/coding-standards/).
1. Alle code DIENT de [Technische Adobe Commerce-richtlijnen](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).
1. Alle code DIENT de [Aanbevolen praktijken voor Adobe Commerce](../phases.md), indien van toepassing.
1. Alle code DIENT de [PHP-Framework Interoperability Group (FIG)-standaarden](https://www.php-fig.org/).
1. Indien mogelijk wordt aanbevolen [Adobe Commerce Technical Visions](https://developer.adobe.com/commerce/php/architecture/technical-vision/) rekening.
1. Alle integraties met externe systemen MOETEN integratietests hebben die het bedrijfsproces valideren.
1. Alle modules MOETEN een testdekking hebben. Wat precies moet worden getest, DIENT te worden bepaald door het ontwikkelingsteam in samenwerking met de technische architect of de belangrijkste ontwikkelaar. Deze vaststelling dient te berusten op kwalitatieve maatregelen en niet op kwantitatieve maatregelen; een hoog percentage van de dekking van de code is geen indicator van succes en houdt evenmin een hoge kwaliteit van de code in. In plaats daarvan moet u het risico bepalen dat een deel van de code niet wordt gedekt door de waarschijnlijkheid en de ernst van de regressies in dat deel van het programma te beoordelen.

## Versioning

Moduleversies MOETEN zich houden aan de [Semantische versie 2.0.0 standaard](https://semver.org/).
Afhankelijkheden van de Adobe Commerce-codebase dienen de [Richtlijnen voor versies van module Vereisten](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## HERZIENINGSCONTROLE

Verbintenissen MOETEN vergezeld gaan van zinvolle &quot;commit messages&quot;.

## Beveiliging

1. [Niet-beveiligde functies](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) MAG NIET WORDEN gebruikt.
1. [XSS-preventiestrategieën](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) DIENT TE worden toegepast.
1. [Beveiligingsbeleid voor inhoud](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) DIENT TE worden toegepast.
1. Nieuwe Adobe Commerce-instanties DIENEN te worden afgeleverd op de meest recente beveiligingsrelease van een versie die nog niet de datum &quot;Einde van beveiligingscorrecties&quot; heeft bereikt. Zie [Beleid voor levenscyclus van Adobe Commerce-software](../../../release/lifecycle-policy.md).
