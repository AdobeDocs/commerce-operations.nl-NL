---
title: Releaseplanning
description: Leer wanneer specifieke versies van Adobe Commerce zijn gepland voor bèta, pre-release en algemene beschikbaarheid.
source-git-commit: 5e02f300bb0b5601c653fdea1dd5b85f4e18ed9c
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---


# Releaseplanning

Adobe streeft voortdurend naar de juiste balans tussen het eenvoudig en voorspelbaar maken van productupgrades en het sneller aanbieden van verbeteringen en nieuwe functies voor vroege gebruikers. Het afgelopen jaar hebben we verfijnd hoe we software leveren om dit evenwicht te ondersteunen. Raadpleeg voor meer informatie onze [versiebeleid](versioning-policy.md).

Adobe geeft beveiligings- en functionele patches uit voor elke ondersteunde releaselijn van Adobe Commerce.

De volgende tabel bevat de datums voor geplande releases (datums kunnen worden gewijzigd):

| Geen | Versies | Pre-release | Algemene beschikbaarheid |
|--------------------------------------------------------------------|-------------------------------------------------|--------------------|----------------------|
| Januari 2023 van de Eigenschap versie | \-\- | \-\- | 17 januari 2023 |
| Maart 2023 Functie + patchrelease + beveiligingspatchrelease | 2.4.6.<sup>1</sup><br>2.4.5-p2<br>2.4.4-p3 | 28 februari 2023 | 14 maart 2023 |
| April 2023 Feature release | \-\- | \-\- | 25 april 2023 |
| Juni 2023 Functie + bètapatchrelease + beveiligingspatchrelease | 2.4.7-bèta1<br>2.4.6-p1<br>2.4.5-p3<br>2.4.4-p4 | 30 mei 2023 | 13 juni 2023 |
| Augustus 2023 Uitgave van de eigenschap + van de veiligheidspatch | 2.4.6-p2<br>2.4.5-p4<br>2.4.4-p5 | 25 juli 2023 | 8 augustus 2023 |
| Oktober 2023 de Versie van de Eigenschap + van de bètaflard + van de veiligheidsflard | 2.4.7-bèta2<br>2.4.6-p3<br>2.4.5-p5<br>2.4.4-p6 | 26 september 2023 | 10 oktober 2023 |

{style="table-layout:auto"}

<sup>\-\- wijst op punten die niet op deze versie van toepassing zijn.</sup><br>
<sup>1 Beta gepland voor januari 2023</sup><br>

>[!TIP]
>
>Patch- en beveiligingspatchreleases zijn mogelijkheden om de kerncodebase te upgraden, zodat uw platform veilig, betrouwbaar en prestatiever blijft. De Versies van de Eigenschap komen om de andere maand voor. De Versies van de eigenschap zijn onafhankelijk van de kerncodebase en zijn beschikbaar door externe module of uitbreiding. Om het even welke updates aan bestaande onafhankelijke eigenschappen worden vrijgegeven tijdens de periodes van de Versie van de Eigenschap en gebeuren niet automatisch als de eigenschap reeds wordt uitgevoerd.

## Vroege toegang

De pre-versie is de Algemene code van de Beschikbaarheid die aan de verkopers van Adobe Commerce en alle partners twee weken vóór Algemene Beschikbaarheid beschikbaar is. Het staat voor snellere plaatsing van code vóór Algemene Beschikbaarheid toe.

Raadpleeg voor meer informatie [bèta-releases](beta.md).

## Releasetypen

- **Patchreleases**—Updates van de belangrijkste Adobe Commerce-toepassing die oplossingen voor beveiliging, naleving, prestaties en hoge prioriteit bevatten.

   >[!IMPORTANT]
   >
   >Adobe zal bètaversie patchreleases (&quot;Beta Releases&quot;) vrijgeven. Dit zijn pre-algemene beschikbaarheidsreleases van Adobe Commerce-functies die openbaar worden gemaakt aan alle Adobe Commerce-klanten en Adobe-partners. Bètareleases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht om de bètareleases te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). De klant wordt geadviseerd voorzichtig te zijn en op geen enkele wijze te vertrouwen op de correcte werking of prestaties van de bètareleases en/of eventuele bijbehorende documentatie of materialen. Daarom is elk gebruik van de bètareleases volledig op eigen risico van de klant.

- **Versies van patch voor bètaversie**—Niet-algemene beschikbaarheidscode wordt bijgewerkt naar de belangrijkste Adobe Commerce-toepassing die oplossingen voor beveiliging, naleving, prestaties en hoge prioriteit bevat. Er is extra tijd nodig om de code en de desbetreffende componenten te controleren.
- **Beveiligingspatchreleases**—Alleen beveiliging-updates van de Adobe Commerce-toepassing die worden uitgebracht om handelaren veilig en conform te houden.
- **Functiereleases**—Nieuwe eigenschappen en eigenschapupdates die als onafhankelijke diensten, los van de flardversies worden geleverd. Voorbeelden zijn services zoals Product Recommendations en Live Search, onafhankelijke modules zoals PWA Studio en Inventory management (MSI) en updates voor onze cloudservices en -infrastructuur.
