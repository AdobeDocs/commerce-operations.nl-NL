---
title: Patchrelease-schema
description: Leer wanneer Adobe de release van nieuwe patches en beveiligingsoplossingen voor Adobe Commerce wil aankondigen.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: f4601034e3e988b3058946b263ec5e8da41fce16
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Patchrelease-schema

Adobe streeft voortdurend naar het juiste evenwicht tussen het maken van productverbeteringen eenvoudig en voorspelbaar terwijl het leveren van verbeteringen aan vroege adopters sneller (zie [&#x200B; versioning beleid &#x200B;](versioning-policy.md)).

Het doel van dit programma is data te verstrekken voor wanneer Adobe van plan is de versie van [&#x200B; flarden &#x200B;](versioning-policy.md#patch-release) voor elke gesteunde versielijn van de kernAdobe Commerce PHP toepassing aan te kondigen. De versies van de flard zijn kansen om de kern codebase te bevorderen om uw platform veilig, betrouwbaar, en prestatieshoog te houden.

>[!NOTE]
>
>Om meer over nieuwe eigenschappen, wolkeninfrastructuur, en uitbreidingsversies te leren, zie de [&#x200B; de versiedocumentatie van de Diensten van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all).

Naast de geplande kwaliteit, veiligheid, en bètaflarden die op deze pagina worden vermeld, verleent Adobe toegang tot [&#x200B; individuele flarden &#x200B;](versioning-policy.md#individual-patch) door het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit &#x200B;](../tools/quality-patches-tool/usage.md). Met dit gereedschap kunt u algemene informatie over alle afzonderlijke patches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce, toepassen, herstellen en weergeven.

Vanaf januari 2026 gaat Adobe Commerce over naar een maandelijks patchreleaseschema met de volgende strategie:

- **Geïsoleerde veiligheidsmoeilijke situaties** - Individuele, niet-cumulatieve [&#x200B; veiligheidsmoeilijke situaties &#x200B;](versioning-policy.md#isolated-patch) kunnen maandelijks worden vrijgegeven en veiligheidsmoeilijke situaties voor alle [&#x200B; omvatten &#x200B;](lifecycle-policy.md) gesteunde versielijnen (omvat regelmatige en uitgebreide steun).

- **de flarden van de Veiligheid** - bij minimium, [&#x200B; veiligheidspatches &#x200B;](versioning-policy.md#security-patch-release) worden vrijgegeven jaarlijks (Mei) voor alle [&#x200B; gesteunde &#x200B;](lifecycle-policy.md) versielijnen. Deze flarden omvatten alle eerder vrijgegeven geïsoleerde veiligheidsmoeilijke situaties. Adobe kan indien nodig in november extra beveiligingspatches vrijgeven, maar dit is niet gegarandeerd.

- **Reparatie** - een volledig [&#x200B; flard &#x200B;](versioning-policy.md#patch-release) voor Adobe Commerce 2.4.x LTS versielijn (3 jaar steunperiode) wordt jaarlijks vrijgegeven (Mei).

- **de flarden van Beta** - Twee [&#x200B; bètaflarden &#x200B;](versioning-policy.md#beta-patch-release) voor Adobe Commerce 2.4.x LTS worden de versielijn tweemaal per jaar vrijgegeven (Maart en november).

Zie de volgende afbeelding voor meer informatie:

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![&#x200B; 2026 de versiekalender van Adobe Commerce &#x200B;](../assets/release/release-calendar.drawio.png)
