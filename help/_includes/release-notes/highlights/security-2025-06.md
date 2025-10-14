---
source-git-commit: a841412309095c6efeb8d84d8612598fd6f1bd32
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---
# Juni 2025 de flardhoogtepunten van de veiligheidspatch

Deze release bevat de volgende hooglichten:

- **API prestatiesverhoging** - lost prestatiesdegradatie in bulk asynchrone Web API eindpunten op die na het vorige veiligheidspatch werden geïntroduceerd.<!-- AC-14078 -->

- **de toegangsmoeilijke situatie van de Blokken van CMS** - lost een kwestie op waar de gebruikers Admin met beperkte toestemmingen (zoals handel-enige toegang) niet de [!UICONTROL CMS Blocks] lijstpagina konden bekijken.

  Eerder, ontmoetten deze gebruikers een fout toe te schrijven aan ontbrekende configuratieparameters na het installeren van vorige veiligheidspatches.<!-- AC-14087 -->

- **de beperkingsverenigbaarheid van het Koekje** - lost een achteruit-onverenigbaar verandering op die de `MAX_NUM_COOKIES` constante in het kader impliceert. Deze update herstelt verwacht gedrag en verzekert verenigbaarheid voor uitbreidingen of aanpassingen die met koekjesgrenzen in wisselwerking staan.<!-- AC-14475 -->

- **verrichtingen Async** - Beperkte async verrichtingen voor het met voeten treden van vorige klantenorden.<!-- AC-13917 -->

- **moeilijke situatie voor CVE-2025-47110** - lost een kwetsbaarheid van e-mailmalplaatjes op.<!-- AC-14695 -->

>[!BEGINSHADEBOX]

De oplossing voor CVE-2025-47110 is ook beschikbaar als een geïsoleerde patch. Zie het [&#x200B; artikel van de Kennisbank &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb25-50) voor details.

>[!ENDSHADEBOX]