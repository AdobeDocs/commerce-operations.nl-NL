---
title: '[!DNL Dashboard]'
description: Leer over het  [!DNL Dashboard]  lusje in  [!DNL Site-Wide Analysis Tool], elementen, wanneer te gebruiken, voordelen, en beste praktijken.
exl-id: 37d848ff-2cff-48b1-8391-520531300bbc
source-git-commit: 786be8bfa915fe82d9316f51662b20bde71abbaa
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# [!UICONTROL Dashboard]

Op de pagina [!UICONTROL Dashboard] vindt u in één oogopslag [!DNL widgets] die een &#39;enkele ruit van glasweergave&#39; van de status en status van uw Adobe Commerce-website bevat. Elke [!DNL widget] bevat een toegangskoppeling naar de pagina van elke functie, naar elk gereedschap zelf of naar rapporten (afhankelijk van de [!DNL widget] ).
Er is ook een lijst van [!UICONTROL External Resources] verbindingen voor Adobe Commerce, met inbegrip van de [&#x200B; Kennisbank van de Steun van het Centrum van Adobe Commerce (het Centrum van de Hulp) &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=nl-NL), [&#x200B; Documentatie van de Ontwikkelaar van Adobe Commerce (DevDocs) &#x200B;](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL){target="_blank"}, [&#x200B; Centrum van de Veiligheid &#x200B;](https://helpx.adobe.com/nl/security.html), en [&#x200B; Waarneming voor Adobe Commerce (OAC) &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=nl-NL).

## Elementen

* **[!UICONTROL Recommendations]**: geeft aanbevelingen voor aanbevolen procedures voor uw site weer. De aanbevelingen (kwesties die en aanbevelingen worden gevonden om te bevestigen) worden gesorteerd door prioriteit-P0 (Kritiek) aan P4 (Bericht).
De aanbevelingen omvatten Beschrijving, Aanbeveling, Effect van de Plaats, Hoofdoorzaak, Scenario&#39;s/Voorwaarden, en Gebruikte Hulpmiddelen.

* **[!UICONTROL Upgrade Compatibility Tool]**: hiermee wordt een aangepaste Adobe Commerce-instantie gecontroleerd op basis van een specifieke versie door alle daarin geïnstalleerde modules en kerncode te analyseren. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert. Het identificeert ook potentiële problemen die in uw code moeten worden opgelost alvorens om aan een nieuwere versie van Adobe Commerce te proberen te bevorderen.
Met [!UICONTROL Upgrade Compatibility Tool] kunt u bepalen wanneer kerncode-wijzigingen zijn aangebracht in aangepaste functies.

* **[!UICONTROL Security Center Widget]**: geeft beveiligingsinzichten voor uw site weer.
De getoonde veiligheidsinformatie omvat [&#x200B; de Naleving van de Versie van de Tech  [!DNL Stack]  &lbrace; [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=nl-NL), [Adobe Security Bulletin](https://helpx.adobe.com/nl/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=nl-NL), and [[!DNL Site-Wide Analysis Tool]  Aanbevelingen van de Veiligheid van de Beste praktijken &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=nl-NL).<br>
[[!UICONTROL Security Scan Tool] &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=nl-NL) controleert de plaatsen van Adobe Commerce voor veiligheidsrisico&#39;s. Het kan proactief en efficiënt malware op winkels ontdekken en handelaars op de hoogte brengen als er om het even welke veiligheidsrisico&#39;s, malware, of bedreigingen zijn, en kan ontbrekende patches en updates van Adobe Commerce identificeren.

* **[!UICONTROL Extensions]**: geeft de extensies weer die momenteel op uw Adobe Commerce-instantie zijn geïnstalleerd. [&#x200B; de informatie van de Marketplace van 0&rbrace; Adobe Commerce &lbrace;wordt verstrekt, waar beschikbaar, voor uitbreidingen die daar worden vermeld.](https://marketplace.magento.com/extensions.html)

* **[!UICONTROL Alerts]**: geeft de meest recente [!DNL New Relic Managed Alerts] voor de Adobe Commerce-instantie weer. Leer meer over [&#x200B; Beheerde alarm voor Adobe Commerce &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/managed-alerts/managed-alerts-for-magento-commerce.html?lang=nl-NL) en hoe te [&#x200B; de diensten van New Relic van de Toegang &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/access-new-relic-services.html?lang=nl-NL) in de Kennisbank van de Steun van Adobe Commerce.

* **[!UICONTROL Non-recommended software in use]**: geeft de niet-aanbevolen software weer die uw Adobe Commerce-exemplaar momenteel gebruikt, op basis van uw Adobe Commerce-versie. De niet-aanbevolen software wordt vermeld door [!UICONTROL Name] , [!UICONTROL Installed Version] en [!UICONTROL Recommended Version] .

* **[!UICONTROL Recommended Patches]**: geeft een korte lijst met aanbevolen patches weer op basis van de patches die u mogelijk al hebt geïnstalleerd en uw Adobe Commerce-versie. De volledige lijst met aanbevolen patches vindt u op het tabblad **[!UICONTROL Patches]** -functie, dat zich ook binnen [!DNL Site-Wide Analysis Tool] bevindt. De patches worden geleverd door [[!DNL Quality Patches Tool]: zoek naar patches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL){target="_blank"} . Alle vermelde patches zijn compatibel met uw huidige Adobe Commerce-exemplaar.
Als er geen aanbevolen patches voor uw Adobe Commerce-instantie worden weergegeven, wordt deze [!DNL widget] weergegeven, **[!UICONTROL No Recommended Patches]** .

## Wanneer gebruiken

De pagina **[!UICONTROL Dashboard]** is uw opdrachtcentrum in één oogopslag in [!DNL Site-Wide Analysis Tool] om niet alleen het &quot;grote beeld&quot; van de gezondheid van uw site als geheel te kunnen bekijken, maar u kunt ook via elke [!DNL widget] specifieke gereedschappen, aanbevelingen en rapporten voor uw Adobe Commerce-website bekijken en openen.

## Voordelen

* De [!DNL widgets] for [!UICONTROL Security Center] , [!UICONTROL Recommendations] , [!UICONTROL Extensions] en [!UICONTROL Security Scan] gebruiken gemakkelijk-aan-gelezen kleuren-gecodeerde interactieve cirkelgrafieken met grafieklegenda aan de zijkant en tellingstotalen in het centrum om aan te geven hoeveel [!UICONTROL Recommendations], [!UICONTROL Extensions], en [!UICONTROL Security Scan Tool] punten elke eigenschap heeft. [!UICONTROL Recommendations] - en [!UICONTROL Security Scan Tool] -grafieken worden gescheiden door de ernst. [!UICONTROL Extensions] worden gescheiden in vier classificaties: huidige versie, oude versie, uitgeschakeld en onbekend.

* [!DNL New Relic Alerts] wordt bovenaan weergegeven met de meest recente waarschuwing, inclusief een korte beschrijving en hoe lang geleden de waarschuwing plaatsvond.

* De [!UICONTROL Recommendations] en [!UICONTROL Extensions] [!DNL widgets] hebben toegang tot de volledige pagina met gegevens voor elke functie door op **[!UICONTROL View All]** te klikken.

* De [!UICONTROL Security Scan Tool] heeft een **[!UICONTROL View Report]** -koppeling in het [!DNL widget] -venster die u naar de [!UICONTROL Recommendations] -pagina stuurt.

* De [!DNL Upgrade Compatibility Tool] heeft een **[!UICONTROL Run Upgrade Scan]** knop in het [!DNL widget] venster.

## Aanbevolen procedures voor het gebruik van de [!UICONTROL Dashboard]

* Klik op elke [!DNL widget] om toegang te krijgen tot de gedetailleerde gegevens die deze biedt, zodat insight en uw website een beter inzicht krijgen in de beveiliging, gezondheid, aanbevelingen en aanbevolen procedures van uw website.

* Ga naar [!UICONTROL Security Scan Tool] [!DNL widget] en klik [!UICONTROL View Report] om een [!UICONTROL Recommendations] -rapport voor uw site weer te geven.

* Gebruik de [!DNL External Resources] verbindingen om of meer informatie te leren, bijgewerkt op veiligheidspatches, updates, en beste praktijken te houden, of uit insight van de [&#x200B; van de Kennisbank van de Steun van het Centrum van de Hulp van Adobe Commerce (het Centrum van de Hulp) voordeel te halen &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html?lang=nl-NL), [&#x200B; de Documentatie van de Ontwikkelaar van Adobe Commerce (DevDocs) &#x200B;](https://developer.adobe.com/commerce/docs/), [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL){target="_blank"}, [&#x200B; het Centrum van de Veiligheid &#x200B;](https://helpx.adobe.com/nl/security.html) en [&#x200B; Waarneming voor Adobe Commerce (OAC) &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=nl-NL).
