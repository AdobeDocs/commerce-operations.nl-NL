---
title: Patchrelease-schema
description: Leer wanneer Adobe de release van nieuwe patches en beveiligingsoplossingen voor Adobe Commerce wil aankondigen.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 5f9f0e1dab7f5e4580f077693039ea387df23880
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Patchrelease-schema

Adobe streeft voortdurend naar het juiste evenwicht tussen het maken van productverbeteringen eenvoudig en voorspelbaar terwijl het leveren van verbeteringen aan vroege adopters sneller (zie [ versioning beleid ](versioning-policy.md)).

Het doel van dit programma is data te verstrekken voor wanneer Adobe van plan is de versie van [ flarden ](versioning-policy.md#patch-release) voor elke gesteunde versielijn van de kernAdobe Commerce PHP toepassing aan te kondigen. De versies van de flard zijn kansen om de kern codebase te bevorderen om uw platform veilig, betrouwbaar, en prestatieshoog te houden.

>[!NOTE]
>
>Om meer over nieuwe eigenschappen, wolkeninfrastructuur, en uitbreidingsversies te leren, zie de [ de versiedocumentatie van de Diensten van Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all).

Naast de geplande kwaliteit, veiligheid, en bètaflarden die op deze pagina worden vermeld, verleent Adobe toegang tot [ individuele flarden ](versioning-policy.md#individual-patch) door het [ Hulpmiddel van de Patches van de Kwaliteit ](../tools/quality-patches-tool/usage.md). Met dit gereedschap kunt u algemene informatie over alle afzonderlijke patches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce, toepassen, herstellen en weergeven.

Vanaf januari 2026 gaat Adobe Commerce over naar een maandelijks patchreleaseschema met de volgende strategie:

- **Geïsoleerde veiligheidsmoeilijke situaties** - Individuele, niet-cumulatieve [ veiligheidsmoeilijke situaties ](versioning-policy.md#isolated-patch) kunnen maandelijks worden vrijgegeven en veiligheidsmoeilijke situaties voor alle [ omvatten ](lifecycle-policy.md) gesteunde versielijnen (omvat regelmatige en uitgebreide steun).

- **de flarden van de Veiligheid** - bij minimium, [ veiligheidspatches ](versioning-policy.md#security-patch-release) worden vrijgegeven jaarlijks (Mei) voor alle [ gesteunde ](lifecycle-policy.md) versielijnen. Deze flarden omvatten alle eerder vrijgegeven geïsoleerde veiligheidsmoeilijke situaties. Adobe kan indien nodig in november extra beveiligingspatches vrijgeven, maar dit is niet gegarandeerd.

- **Reparatie** - een volledig [ flard ](versioning-policy.md#patch-release) voor Adobe Commerce 2.4.x LTS versielijn (3 jaar steunperiode) wordt jaarlijks vrijgegeven (Mei).

- **de flarden van Beta** - Twee [ bètaflarden ](versioning-policy.md#beta-patch-release) voor Adobe Commerce 2.4.x LTS worden de versielijn tweemaal per jaar vrijgegeven (Maart en november).

Zie de volgende afbeelding voor meer informatie:

![ 2026 de versiekalender van Adobe Commerce ](../assets/release/release-calendar.drawio.svg)
