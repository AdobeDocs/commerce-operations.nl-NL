---
title: '[!DNL Site-Wide Analysis Tool]'
description: Leer over het  [!DNL Site-Wide Analysis]  Hulpmiddel, zijn gebruik, het installatieproces, en hoe te om toegang te krijgen
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 99e5cf727d88de3e03c8076bbd11114e758c19ab
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>Met ingang van 23 april 2024 wordt de [!DNL Site-Wide Analysis Tool] voor alle Adobe Commerce-klanten op locatie buiten bedrijf gesteld.

Deze handleiding biedt een holistisch overzicht van de [!DNL Site-Wide Analysis Tool] . Hierin worden het gebruik, de stapsgewijze instructies voor de installatie en de manier waarop u het gereedschap kunt gebruiken beschreven.

## Wat is [!DNL Site-Wide Analysis Tool]?

[!DNL Site-Wide Analysis Tool] is een proactief zelfbedieningshulpmiddel en een centrale opslagplaats die gedetailleerde systeeminzichten en aanbevelingen omvat om de veiligheid en de operabiliteit van uw installatie van Adobe Commerce te verzekeren. Het biedt 24/7 real-time prestatiescontrole, rapporten, en advies om potentiële kwesties en betere zichtbaarheid in plaatsgezondheid, veiligheid, en toepassingsconfiguraties te identificeren. Het helpt de resolutietijd te verminderen en de stabiliteit en prestaties van de site te verbeteren.

>[!NOTE]
>
>De [!DNL Site-Wide Analysis Tool] rapporteert gegevens op systeemniveau. Voor rapporten over het product van Adobe Commerce, verkoop, marketing, en andere gegevens van de handelstoepassing, zie [&#x200B; Rapporten van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/start/reporting/reports-menu).

![&#x200B; plaats-brede het dashboard van het Hulpmiddel van de Analyse &#x200B;](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Zie deze [&#x200B; inleidende video &#x200B;](https://www.youtube.com/watch?v=KW2R8ki_RG4) om meer te leren.

## Overzicht van gereedschappen

- **Dashboard**
   - Toont de algemene gezondheid van uw systeem met berichten van ontdekte kwesties en specifieke aanbevelingen door prioriteit.<br>
Het bevat ook een historisch overzicht waarin wordt bijgehouden hoe de gezondheid van uw website in de loop der tijd verandert.
   - Toont **[!UICONTROL Security Center Widget]** die u tot laat toegang hebben:
      - [&#x200B; Naleving van de Versie van 1&rbrace; Tech  [!DNL Stack]   [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=nl-NL)
      - [&#x200B; Bulletin van de Veiligheid van Adobe &#x200B;](https://helpx.adobe.com/nl/security/security-bulletin.html)
      - [&#x200B; Aanbevelingen van  [!DNL Security Scan Tool] &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=nl-NL)
      - [[!DNL Site-Wide Analysis Tool]  Aanbevelingen van de Veiligheid van de Beste praktijken &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=nl-NL)

- **Informatie** - verstrekt de informatie van het klantencontact en een samenvatting van huidige kaartjes, van gedetailleerde informatie over elk geïnstalleerd product van Adobe Commerce.

- **Aanbevelingen** - maakt een lijst van aanbevelingen die op beste praktijken worden gebaseerd om kwesties te richten op uw plaats worden ontdekt:
   - Voor wijzigingen die een infrastructuurupdate vereisen, dient u een supportverzoek in.
   - Breng de wijzigingen zelf aan voor wijzigingen die een toepassingsupdate vereisen.
   - Voor veranderingen die handinterventie zoals de plaatsing van de a [&#x200B; code &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=nl-NL#deployment-workflow) vereisen, vraag uw systeembeheerder of ontwikkelaars voor hulp.

- **Uitzonderingen** - maakt een lijst van fouten die door de toepassing worden geworpen die door abnormale voorwaarden zonder een foutenmanager wordt veroorzaakt.

- **Uitbreidingen** - maakt een lijst van alle derdeuitbreidingen en derdebibliotheken.

- **Patches** - Geïntegreerd met [!DNL Quality Patches Tool], verstrekt het een lijst van alle beschikbare flarden specifiek voor uw Instantie van Adobe Commerce.

## Integratie met andere Adobe Commerce Support Tools

Bekijk alle belangrijke inzichten van uw site op één plaats. Met [!DNL Site-Wide Analysis Tool] hebt u rechtstreeks toegang tot en informatie van de [!UICONTROL Security Center Widget] , [!DNL Upgrade Compatability Tool] en [!DNL Managed Alerts] .

- [**[!UICONTROL Security Center Widget]**] - Geeft beveiligingsinzichten voor uw site weer.<br>
De getoonde veiligheidsinformatie omvat [&#x200B; de Naleving van de Versie van de Tech  [!DNL Stack]  met  [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=nl-NL), [Adobe Security Bulletin](https://helpx.adobe.com/nl/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=nl-NL), and [[!DNL Site-Wide Analysis Tool]  Aanbevelingen van de Veiligheid van de Beste praktijken &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=nl-NL).<br>
[[!DNL Security Scan Tool] &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=nl-NL) voorziet Adobe Commerce en Magento open-Source klanten van inzicht in de veiligheidsstatus van hun opslag in real time door malware proactively te ontdekken en hen op de hoogte te brengen als hun opslag wordt gecompromitteerd.

- [**[!DNL Upgrade Compatability Tool]**](../../upgrade/upgrade-compatibility-tool/overview.md) - Hiermee wordt een aangepaste Adobe Commerce-instantie uitgevoerd op basis van de upgradeversie van het doel en wordt een overzicht gegeven van de kritieke problemen, fouten en waarschuwingen die moeten worden opgelost, zodat de upgrade sneller, sneller en goedkoper kan worden geanalyseerd.

- [**[!DNL Managed Alerts]**](https://support.magento.com/hc/en-us/sections/360010758472-Managed-alerts-for-Adobe-Commerce) - monitor veelvoudige metriek om de prestaties van het platform proactively te volgen en specifieke instructies op te geven hoe te om kwesties problemen op te lossen zodat de handelaren kritieke onderbreking kunnen vermijden en over hun CPU, toepassingsprestaties, schijf, geheugen, en gegevensbestand op de hoogte blijven.

## Voor wie is deze gids?

Handelaren en partners die meer zichtbaarheid willen krijgen op hun Adobe Commerce-websites. Het biedt verkopers de mogelijkheid om hun klanten meer ervaring te geven en zich beter aan te passen aan de aanbevelingen van best practices en fundamentele kwesties.

## [!DNL Site-Wide Analysis Tool] demo

Bekijk deze video voor meer informatie over [!DNL Site-Wide Analysis Tool] :

>[!VIDEO](https://video.tv.adobe.com/v/344001?quality=12)
