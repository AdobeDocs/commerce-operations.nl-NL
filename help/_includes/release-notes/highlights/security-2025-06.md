---
source-git-commit: f9cc5ab0cb1b64455e12081ffbf719e0f2a791ad
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---
# Juni 2025 de flardhoogtepunten van de veiligheidspatch

Deze release bevat de volgende hooglichten:

* **API prestatiesverhoging** - lost prestatiesdegradatie in bulk asynchrone Web API eindpunten op die na het vorige veiligheidspatch werden geïntroduceerd.<!-- AC-14078 -->

* **de toegangsmoeilijke situatie van de Blokken van CMS** - lost een kwestie op waar de gebruikers Admin met beperkte toestemmingen (zoals handel-enige toegang) niet de [!UICONTROL CMS Blocks] lijstpagina konden bekijken.

  Eerder, ontmoetten deze gebruikers een fout toe te schrijven aan ontbrekende configuratieparameters na het installeren van vorige veiligheidspatches.<!-- AC-14087 -->

* **de beperkingsverenigbaarheid van het Koekje** - lost een achteruit-onverenigbaar verandering op die de `MAX_NUM_COOKIES` constante in het kader impliceert. Deze update herstelt verwacht gedrag en verzekert verenigbaarheid voor uitbreidingen of aanpassingen die met koekjesgrenzen in wisselwerking staan.<!-- AC-14475 -->

* **Repareren voor CVE-2024-34104** - lost een onjuiste vergunningskwetsbaarheid op.<!-- AC-13917 -->

* **moeilijke situatie voor CVE-2025-47110** - lost een kwetsbaarheid van e-mailmalplaatjes op.<!-- AC-14695 -->

* **Repareren voor VULN-31547** - lost een categorie canonical verbindingskwetsbaarheid op.<!-- AC-14713 -->

>[!BEGINSHADEBOX]

Correcties voor CVE-2025-47110 VULN-31547 zijn ook beschikbaar als een geïsoleerde patch. Zie het [ artikel van de Kennisbank ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50) voor details.

>[!ENDSHADEBOX]
