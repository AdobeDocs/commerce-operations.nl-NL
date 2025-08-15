---
title: Aanbevolen werkwijzen voor algemene ontwikkeling
description: Meer informatie over algemene best practices bij het ontwikkelen van Adobe Commerce-projecten.
feature: Best Practices
role: Developer
exl-id: 35de9849-2d19-4bb6-b920-9ce3838bc8bc
source-git-commit: 68dc4635df9fc411925fe0d48a578edece8895dc
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor algemene ontwikkeling in Adobe Commerce

Dit onderwerp beschrijft de basislijn voor een gezond ontwikkelingsproces van Adobe Commerce. Hierin worden fundamentele processen, codeerbeginselen en ontwerpprincipes voor toepassingen beschreven om ontwikkelaars te begeleiden.

>[!NOTE]
>
>Technische architecten van Adobe gebruiken deze best practices als referentie tijdens ontwikkelingstaken.

Deze beste praktijken zijn ontwikkeld op basis van jarenlange ervaring met het ontwikkelen en uitvoeren van Commerce-projecten. Adobe raadt aan dat technische initiatieven deze beste praktijken volgen en dat u bestaande processen en code verbetert om deze op elkaar af te stemmen.

## Tekstconventies

De sleutelwoorden &quot;MOET&quot;, &quot;MOET NIET&quot;, &quot;VEREIST&quot;, &quot;DIENT&quot;, &quot;DIENT NIET&quot;, &quot;DIENT NIET&quot;, &quot;AANBEVOLEN&quot;, &quot;MAY&quot;, en &quot;OPTIONEEL&quot;in dit onderwerp moeten worden geïnterpreteerd zoals die in [ RFC 2119 ](https://datatracker.ietf.org/doc/html/rfc2119) worden beschreven.

## Proces

1. Voordat met de projectactiviteiten wordt begonnen, moet overeenstemming worden bereikt over een welomschreven projectmethode. Het kan gaan om een methode voor de bestrijding van trommel, waterval of een andere methodologie of combinatie van methoden, mits deze gedefinieerd is.
1. De ontwikkeling MOET NIET beginnen totdat het ontwikkelingsteam een vertakkingsstrategie voor het versiecontrolesysteem heeft.
1. De ontwikkeling MOET NIET beginnen na de aftekening van technische specificaties, de aftekening van gebruikersartikelen en gebruiksgevallen en de aftekening van testgevallen is beschikbaar voor het ontwikkelingsteam.
1. De ontwikkeling MAG NIET beginnen totdat ten minste een ontwikkelings- en kwaliteitscontroleomgeving beschikbaar is.
1. De project-specifieke vereisten die voor ontwikkeling verplicht zijn te beginnen KUNNEN in a _Definitie van Klaar_ worden gedocumenteerd.
1. Afmelding DIENT te worden gedaan door een vertegenwoordiger van de klant die gemachtigd is om af te tekenen bij te leveren projecten.
1. In de methoden van het Agile-project kunnen aanvullende vereisten volgen. Deze eisen dienen als nieuwe eisen te worden beschouwd en dienen dienovereenkomstig te worden vastgelegd, opgesteld en gepland.
1. Alle ontwikkelingen MOETEN vóór de indiening door de ontwikkelaar functioneel worden getest.
1. Alle ontwikkelingen MOETEN geautomatiseerde tests doorstaan voordat ze worden ingediend voor herziening van de code. Dit kan als geautomatiseerd proces na het creëren van trekkingsverzoek worden gevormd.
1. Elke ontwikkeling MOET een technische architect of een ontwikkelaar met handmatige codecontrole doorstaan voordat deze voor kwaliteitsborging wordt ingediend.
1. Alle ontwikkelingen MOETEN een kwaliteitsborging doorstaan voordat zij aan de klant worden geleverd.
1. Projectspecifieke vereisten die verplicht zijn voor levering, kunnen worden gedocumenteerd in een &quot;Definitie van Gereed&quot;.

## Omgeving

1. Alle ontwikkelaars MOETEN zelfde winde gebruiken. PhpStorm is de aanbevolen IDE voor Adobe Commerce-ontwikkeling.
1. Alle ontwikkelaars MOETEN zich ontwikkelen en testen gebruikend de zelfde technologiestapel zoals die op de (toekomstige) productieservers wordt gebruikt. De versies van de software in deze technologiestapel MOETEN de belangrijkste en minder belangrijke versie van de software aanpassen die op de productieservers wordt geïnstalleerd. Zie [ systeemvereisten ](../../../installation/system-requirements.md) voor details over de typische technologiestapel voor Adobe Commerce.
1. De systeembeheerder of technische architect kan het team voorzien van een centraal onderhouden lokale ontwikkelomgeving om gelijke en actuele lokale omgevingen te verzekeren en te bevorderen.
1. De ontwikkelaars en de ingenieurs QA MOETEN toegang tot de bevellijn, het gegevensbestand, en de logboekdossiers van het milieu hebben QA. Dit kan een verbinding van VPN vereisen.

## Versioning

De versies van de module MOETEN aan de [ Semantische Versioning 2.0.0 norm ](https://semver.org/) naleven.
De gebiedsdelen op de codebase van Adobe Commerce MOETEN de [ richtlijnen van de Afhankelijkheid van de Versie van de Module volgen ](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## HERZIENINGSCONTROLE

Verbintenissen MOETEN vergezeld gaan van zinvolle &quot;commit messages&quot;.

## Beveiliging

1. [ niet-veilige functies ](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/) MOGEN NIET worden gebruikt.
1. [ XSS-preventie strategieën ](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) ZOU MOETEN worden toegepast.
1. [ het Beleid van de Veiligheid van de Inhoud ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) ZOU moeten worden toegepast.
1. Nieuwe Adobe Commerce-instanties DIENEN te worden afgeleverd op de meest recente beveiligingsrelease van een versie die nog niet de datum &quot;Einde van beveiligingscorrecties&quot; heeft bereikt. Zie [ het Beleid van de Levenscyclus van de Software van Adobe Commerce ](../../../release/lifecycle-policy.md).
