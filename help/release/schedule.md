---
title: Patchrelease-schema
description: Leer wanneer Adobe de release van nieuwe patches en beveiligingsoplossingen voor Adobe Commerce wil aankondigen.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 0f46bdfd0afbca07e0d60e995ee9426f5408671d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Patchrelease-schema

Adobe streeft voortdurend naar het juiste evenwicht tussen het maken van productverbeteringen eenvoudig en voorspelbaar terwijl het leveren van verbeteringen aan vroege adopters sneller (zie [&#x200B; versioning beleid &#x200B;](versioning-policy.md)).

Het doel van dit programma is data te verstrekken voor wanneer Adobe van plan is de versie van [&#x200B; flarden &#x200B;](versioning-policy.md#patch-release) voor elke gesteunde versielijn van de kernAdobe Commerce PHP toepassing aan te kondigen. De versies van de flard zijn kansen om de kern codebase te bevorderen om uw platform veilig, betrouwbaar, en prestatieshoog te houden.

>[!NOTE]
>
>Om meer over nieuwe eigenschappen, wolkeninfrastructuur, en uitbreidingsversies te leren, zie de [&#x200B; de versiedocumentatie van de Diensten van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all).

Naast de geplande kwaliteit, veiligheid, en bètaflarden die op deze pagina worden vermeld, verleent Adobe toegang tot [&#x200B; individuele flarden &#x200B;](versioning-policy.md#individual-patch) door het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit &#x200B;](../tools/quality-patches-tool/usage.md). Met dit gereedschap kunt u algemene informatie over alle afzonderlijke patches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce, toepassen, herstellen en weergeven.

Adobe Commerce-patchreleases worden uitgebracht op basis van de volgende richtlijnen:

- **Geïsoleerd dossier van het veiligheidspatch** - Individuele, niet-cumulatieve [&#x200B; dossiers van het veiligheidspatch &#x200B;](versioning-policy.md#isolated-security-patch-file) worden vrijgegeven onafhankelijk om snellere sanering toe te laten en in het volgende volledige veiligheidspatch opgenomen. Om een geïsoleerd dossier van het veiligheidspatch toe te passen, moeten de klanten op de recentste veiligheid-enige flardversie (de recentste - p versie) voor hun gesteunde versielijn zijn, aangezien de geïsoleerde veiligheidsmoeilijke situaties exclusief tegen die versie worden getest.

- **de flarden van de Veiligheid** - bij minimium, [&#x200B; veiligheidspatches &#x200B;](versioning-policy.md#security-patch-release) worden vrijgegeven jaarlijks voor alle [&#x200B; gesteunde &#x200B;](lifecycle-policy.md) versielijnen. Deze patches omvatten alle eerder vrijgegeven beveiligings-, compatibiliteits- en kwaliteitshotfixes.  Adobe kan indien nodig extra beveiligingspatches vrijgeven, maar dit is niet gegarandeerd.

- **Reparatie** - een volledig [&#x200B; flard &#x200B;](versioning-policy.md#patch-release) voor Adobe Commerce 2.4.x LTS versielijn (3 jaar steunperiode) wordt jaarlijks vrijgegeven (Mei).

- **- Één** alpha- flardflard van 0&rbrace; Alpha [&#x200B; voor Adobe Commerce 2.4.x LTS wordt de versielijn jaarlijks vrijgegeven.](versioning-policy.md#alpha-patch-release)

- **de flarden van Beta** - Één [&#x200B; bètaflarden &#x200B;](versioning-policy.md#beta-patch-release) voor Adobe Commerce 2.4.x LTS de versielijn wordt jaarlijks vrijgegeven.

Zie de volgende afbeelding voor meer informatie:

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![&#x200B; 2026 de versiekalender van Adobe Commerce &#x200B;](../assets/release/release-calendar.png)


## Waarschuwingskanalen vrijgeven

Adobe brengt klanten via de volgende kanalen op de hoogte van nieuwe patchreleases:

- [&#x200B; Bulletins en Advisories van de Veiligheid van Adobe &#x200B;](https://helpx.adobe.com/security/security-bulletin.html#magento)
- E-mail
- Waarschuwingen in producten

>[!NOTE]
>
> Voor versiedata voor elke minder belangrijke, flard, en veiligheidsversie en data voor het eind van regelmatige steun, zie [&#x200B; Vrijgegeven versies &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions).
