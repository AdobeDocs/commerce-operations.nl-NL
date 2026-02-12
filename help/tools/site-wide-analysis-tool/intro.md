---
title: '[!DNL Site-Wide Analysis Tool]'
description: Leer over het  [!DNL Site-Wide Analysis]  Hulpmiddel, zijn gebruik, het installatieproces, en hoe te om toegang te krijgen
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: e22d4fffdd61a8480bf20b10b848514856d661df
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>Met ingang van 23 april 2024 wordt de [!DNL Site-Wide Analysis Tool] voor alle Adobe Commerce-klanten op locatie buiten bedrijf gesteld.

Deze handleiding biedt een holistisch overzicht van de [!DNL Site-Wide Analysis Tool] . Hierin worden het gebruik, de stapsgewijze instructies voor de installatie en de manier waarop u het gereedschap kunt gebruiken beschreven.

## Wat is de [!DNL Site-Wide Analysis Tool] ?

[!DNL Site-Wide Analysis Tool] is een proactief zelfbedieningshulpmiddel en een centrale opslagplaats die gedetailleerde systeeminzichten en aanbevelingen omvat om de veiligheid en de operabiliteit van uw installatie van Adobe Commerce te verzekeren. Het biedt 24/7 real-time prestatiescontrole, rapporten, en advies om potentiële kwesties en betere zichtbaarheid in plaatsgezondheid, veiligheid, en toepassingsconfiguraties te identificeren. Het helpt de resolutietijd te verminderen en de stabiliteit en prestaties van de site te verbeteren.

>[!NOTE]
>
>Nadat u een aanbeveling hebt toegepast, kan het enkele dagen duren voordat deze wordt bijgewerkt in het dashboard of het gegenereerde rapport van het hulpprogramma voor de analyse voor de hele site.
>
>De [!DNL Site-Wide Analysis Tool] rapporteert gegevens op systeemniveau. Voor rapporten over het product van Adobe Commerce, verkoop, marketing, en andere gegevens van de handelstoepassing, zie [&#x200B; Rapporten van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/reporting/reports-menu).

![&#x200B; plaats-brede het dashboard van het Hulpmiddel van de Analyse &#x200B;](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Zie deze [&#x200B; inleidende video &#x200B;](https://www.youtube.com/watch?v=KW2R8ki_RG4) om meer te leren.

## Overzicht van gereedschappen

- **Dashboard**
   - Toont de algemene gezondheid van uw systeem met berichten van ontdekte kwesties en specifieke aanbevelingen door prioriteit.<br>
Het bevat ook een historisch overzicht waarin wordt bijgehouden hoe de gezondheid van uw website in de loop der tijd verandert.
   - Toont **[!UICONTROL Security Center Widget]** die verbindingen aan de volgende middelen verstrekt:
      - [&#x200B; Naleving van de Versie van 1&rbrace; Tech  [!DNL Stack]   [!DNL end of life (EOL)]](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/system-requirements)
      - [&#x200B; Bulletin van de Veiligheid van Adobe &#x200B;](https://helpx.adobe.com/nl/security/security-bulletin.html)
      - [&#x200B; Aanbevelingen van  [!DNL Security Scan Tool] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/security/security-scan)
      - [[!DNL Site-Wide Analysis Tool]  Aanbevelingen van de Veiligheid van de Beste praktijken &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations)

- **Informatie** - verstrekt de informatie van het klantencontact en een samenvatting van huidige kaartjes, van gedetailleerde informatie over elk geïnstalleerd product van Adobe Commerce.

- **Aanbevelingen** - Verstrekt de Score van de Index van de Gezondheid van de a [&#x200B; SWAT &#x200B;](#swat-health-index.md) aan de gezondheid van de spoorplaats en lijsten aanbevelingen die op beste praktijken worden gebaseerd om kwesties te richten die op uw plaats worden ontdekt:
   - Voor wijzigingen die een infrastructuurupdate vereisen, dient u een supportverzoek in.
   - Breng de wijzigingen zelf aan voor wijzigingen die een toepassingsupdate vereisen.
   - Voor veranderingen die handinterventie zoals de plaatsing van de a [&#x200B; code &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow#deployment-workflow) vereisen, vraag uw systeembeheerder of ontwikkelaars voor hulp.

- **Uitzonderingen** - maakt een lijst van fouten die door de toepassing worden geworpen die door abnormale voorwaarden zonder een foutenmanager wordt veroorzaakt.

- **Uitbreidingen** - maakt een lijst van alle derdeuitbreidingen en derdebibliotheken.

- **Patches** - Geïntegreerd met [!DNL Quality Patches Tool], verstrekt het een lijst van alle beschikbare flarden specifiek voor uw Instantie van Adobe Commerce.

## Integratie met andere Adobe Commerce Support Tools

Belangrijke inzichten van uw site op één locatie weergeven. Met [!DNL Site-Wide Analysis Tool] hebt u rechtstreeks toegang tot en informatie van de [!UICONTROL Security Center Widget] , [!DNL Upgrade Compatibility Tool] en [!DNL Managed Alerts] .

- **[!UICONTROL Security Center Widget]** - Geeft beveiligingsinzichten voor uw site weer.<br>
De veiligheidsinformatie omvat [&#x200B; de Naleving van de Versie van de Tech  [!DNL Stack]  met  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/nl/docs/commerce-operations/installation-guide/system-requirements), [Adobe Security Bulletin](https://helpx.adobe.com/nl/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/security/security-scan), and [[!DNL Site-Wide Analysis Tool]  Aanbevelingen van de Veiligheid van de Beste praktijken &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations).

  [[!DNL Security Scan Tool] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/security/security-scan) voorziet Adobe Commerce en Magento open-Source klanten van inzicht in real time in de veiligheidshouding van hun opslag door malware proactively te ontdekken en hen te waarschuwen als hun opslag wordt gecompromitteerd.

- **[[!DNL Upgrade Compatibility Tool]](../../upgrade/upgrade-compatibility-tool/overview.md)** - Controleert uw Adobe Commerce-exemplaar op de upgradeversie en geeft kritieke problemen, fouten en waarschuwingen weer die moeten worden verholpen voordat de upgrade wordt uitgevoerd. Het oplossen van deze kwesties stroomlijnt het verbeteringsproces.&quot;

- **[[!DNL Managed Alerts]](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/managed-alerts-for-adobe-commerce/managed-alerts-for-magento-commerce)** - de belangrijkste metriek van de Monitor (CPU, toepassingsprestaties, schijf, geheugen, en gegevensbestandgezondheid), en verstrekt duidelijke het oplossen van problemenstappen helpen handelaren vóór kwesties blijven en onderbreking vermijden.

## Voor wie is deze gids?

Handelaren en partners die meer zichtbaarheid willen krijgen op hun Adobe Commerce-websites. Het biedt verkopers de mogelijkheid om hun klanten meer ervaring te geven en zich beter aan te passen aan de aanbevelingen van best practices en fundamentele kwesties.

## [!DNL Site-Wide Analysis Tool] demo

Bekijk deze video voor meer informatie over [!DNL Site-Wide Analysis Tool] :

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
