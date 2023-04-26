---
title: '[!DNL Dashboard]'
description: Meer informatie over de [!DNL Dashboard] in de [!DNL Site-Wide Analysis Tool], elementen, wanneer te gebruiken, voordelen, en beste praktijken.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

De [!UICONTROL Dashboard] paginaweergaven in één oogopslag [!DNL widgets] die een &quot;enkel venster van de mening van het glas&quot;van de gezondheid en huidige status van uw website van Adobe Commerce verstrekken. Elk [!DNL widget] bevat een toegangskoppeling naar de pagina van elke functie, naar elk gereedschap zelf of naar rapporten (afhankelijk van de [!DNL widget]).
Er is ook een lijst met [!UICONTROL External Resources] koppelingen voor Adobe Commerce, inclusief de [Adobe Commerce Help Center Support Knowledge Base (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce Developer Documentation (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Beveiligingscentrum](https://helpx.adobe.com/security.html), en [Waarneming voor Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).

## Elementen

* **[!UICONTROL Recommendations]**: Hier worden aanbevolen aanbevolen procedures voor uw site weergegeven. Recommendations (kwesties die en aanbevelingen worden gevonden om te bevestigen) worden gesorteerd door prioriteit-P0 (Kritiek) aan P4 (Bericht).
Recommendations omvat Beschrijving, Aanbeveling, Siteeffect, Hoofdoorzaak, Scenario&#39;s/Voorwaarden en gebruikte gereedschappen.

* **[!UICONTROL Upgrade Compatibility Tool]**: Controleert een aangepaste Adobe Commerce-instantie op een specifieke versie door alle daarin geïnstalleerde modules en kerncode te analyseren. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert. Het identificeert ook potentiële problemen die in uw code moeten worden opgelost alvorens om aan een nieuwere versie van Adobe Commerce te proberen te bevorderen.
De [!UICONTROL Upgrade Compatibility Tool] kunt u identificeren wanneer de veranderingen van de kerncode aan aangepaste eigenschappen zijn aangebracht.

* **[!UICONTROL Security Center Widget]**: Hiermee geeft u beveiligingsinzichten voor uw site weer.
De weergegeven beveiligingsinformatie omvat [Tech [!DNL Stack] Versienormen met [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html), [Adobe Security Bulletin](https://helpx.adobe.com/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html), and [[!DNL Site-Wide Analysis Tool] Best Practice Security Recommendations](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html).<br>
De [[!UICONTROL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html) controleert Adobe Commerce-sites op beveiligingsrisico&#39;s. Het kan proactief en efficiënt malware op winkels ontdekken en handelaars op de hoogte brengen als er om het even welke veiligheidsrisico&#39;s, malware, of bedreigingen zijn, en kan ontbrekende patches en updates van Adobe Commerce identificeren.

* **[!UICONTROL Extensions]**: Hiermee geeft u de extensies weer die momenteel op uw Adobe Commerce-exemplaar zijn geïnstalleerd. [Adobe Commerce Marketplace](https://marketplace.magento.com/extensions.html) informatie wordt verstrekt, indien beschikbaar, voor uitbreidingen die daar worden vermeld.

* **[!UICONTROL Alerts]**: De nieuwste [!DNL New Relic Managed Alerts] voor de Adobe Commerce-instantie. Meer informatie over [Beheerde waarschuwingen voor Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html) en hoe [Toegang tot New Relic-services](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html) in de Adobe Commerce Support Knowledge Base.

* **[!UICONTROL Non-recommended software in use]**: Geeft de niet-aanbevolen software weer die uw Adobe Commerce-exemplaar momenteel gebruikt, op basis van uw Adobe Commerce-versie. De niet-aanbevolen software wordt vermeld door [!UICONTROL Name], [!UICONTROL Installed Version], en [!UICONTROL Recommended Version].

* **[!UICONTROL Recommended Patches]**: Geeft een korte lijst met aanbevolen patches weer op basis van de patches die u mogelijk al hebt geïnstalleerd en uw Adobe Commerce-versie. De volledige lijst met aanbevolen pleisters staat op het tabblad **[!UICONTROL Patches]** eigenschap tabel, die ook binnen [!DNL Site-Wide Analysis Tool]. De pleisters worden geleverd door de [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Alle vermelde patches zijn compatibel met uw huidige Adobe Commerce-exemplaar.
Als er geen aanbevolen patches voor uw Adobe Commerce-instantie worden weergegeven, gaat u [!DNL widget] wordt weergegeven, **[!UICONTROL No Recommended Patches]**.

## Wanneer gebruiken

De **[!UICONTROL Dashboard]** pagina is uw in één oogopslag opdrachtcentrum in het [!DNL Site-Wide Analysis Tool] om niet alleen gemakkelijk het &quot;grote beeld&quot;van de gezondheid van uw plaats als geheel te bekijken, maar u kunt ook specifieke hulpmiddelen, aanbevelingen, en rapporten voor uw website van Adobe Commerce door elke [!DNL widget].

## Voordelen

* De [!DNL widgets] for [!UICONTROL Security Center], [!UICONTROL Recommendations], [!UICONTROL Extensions], en [!UICONTROL Security Scan] gebruiken gemakkelijk-aan-gelezen kleur-gecodeerde interactieve cirkelgrafieken met grafieklegenda aan de kant en tellingstotalen in het centrum om aan te geven hoeveel [!UICONTROL Recommendations], [!UICONTROL Extensions], en [!UICONTROL Security Scan Tool] objecten die elke functie heeft. [!UICONTROL Recommendations] en [!UICONTROL Security Scan Tool] grafieken worden gescheiden door de ernst. [!UICONTROL Extensions] worden ingedeeld in vier indelingen: huidige versie, oude versie, uitgeschakeld en onbekend.

* [!DNL New Relic Alerts] worden vermeld met de meest recente waarschuwing bovenaan, met inbegrip van een korte beschrijving en hoe lang geleden de waarschuwing plaatsvond.

* De [!UICONTROL Recommendations] en [!UICONTROL Extensions] [!DNL widgets] toegang hebben tot de volledige pagina met gegevens voor elke functie door op **[!UICONTROL View All]**.

* De [!UICONTROL Security Scan Tool] heeft een **[!UICONTROL View Report]** in de [!DNL widget] venster dat u naar het [!UICONTROL Recommendations] pagina.

* De [!DNL Upgrade Compatibility Tool] heeft een **[!UICONTROL Run Upgrade Scan]** in de [!DNL widget] venster.

## Aanbevolen procedures voor het gebruik van de [!UICONTROL Dashboard]

* Klik op elk [!DNL widget] om toegang te krijgen tot de gedetailleerde gegevens die het biedt, zodat u inzicht krijgt in en inzicht krijgt in de beveiliging, gezondheid, aanbevelingen en aanbevolen procedures van uw website om deze te verbeteren.

* Ga naar de [!UICONTROL Security Scan Tool] [!DNL widget] en klik op [!UICONTROL View Report] om een [!UICONTROL Recommendations] rapport voor uw site.

* Gebruik de [!DNL External Resources] de verbindingen om of meer informatie te leren, bijgewerkt op veiligheidspatches, updates, en beste praktijken te houden, of voordeel te halen uit het inzicht van [Adobe Commerce Help Center Support Knowledge Base (Help Center)](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html), [Adobe Commerce Developer Documentation (DevDocs)](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}, [Beveiligingscentrum](https://helpx.adobe.com/security.html), en [Waarneming voor Adobe Commerce (OAC)](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html).
