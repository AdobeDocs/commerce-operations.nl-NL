---
title: De [!DNL Site-Wide Analysis Tool]
description: Voer de volgende stappen uit om de [!DNL Upgrade Compatibility Tool] verslag van de [!DNL Site-Wide Analysis Tool] dashboard op uw Adobe Commerce-project.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# De [!DNL Site-Wide Analysis Tool]

De [!DNL Site-Wide Analysis Tool] biedt 24/7 real-time prestatiebewaking, rapporten en aanbevelingen om de beveiliging en operabiliteit voor Adobe Commerce-instanties te garanderen.

De [!DNL Upgrade Compatibility Tool] is nu geïntegreerd met de [!DNL Site-Wide Analysis Tool] om niet-technische personen in staat te stellen de [!DNL Upgrade Compatibility Tool] en krijg een [verslag](../upgrade-compatibility-tool/reports.md) bevat een lijst met problemen voor elk bestand.

Zie de [[!DNL Site-Wide Analysis Tool] gebruikershandleiding](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) voor meer informatie .

## Voer de [!DNL Upgrade Compatibility Tool] van de [!DNL Site-Wide Analysis Tool]

Ga naar de [!DNL Site-Wide Analysis Tool] dashboard voor uw project en zoek het [!DNL Upgrade Compatibility Tool] widget.

![UCT SWAT-widget - Oorspronkelijk](../../assets/upgrade-guide/uct-swat-initial.png)

Klik op **[!UICONTROL Run Upgrade Scan]**. Afhankelijk van de grootte van het project kan de scan enige tijd duren. Een spinner geeft aan dat de scan wordt uitgevoerd.

![UCT SWAT-widget - Bezig](../../assets/upgrade-guide/uct-swat-progress.png)

Nadat de scan is voltooid, worden de resultaten op hoog niveau weergegeven in de widget.

![UCT SWAT-widget - Resultaten](../../assets/upgrade-guide/uct-swat-results.png)

Klikken **[!UICONTROL Download Report]** om de [!DNL Upgrade Compatibility Tool] [HTML-rapport](../upgrade-compatibility-tool/reports.md#html-report) en bekijk de details.


>[!NOTE]
>
> De [!DNL Upgrade Compatibility Tool] via de [!DNL Site-Wide Analysis Tool] optimaliseert uw resultaten en helpt u zich op kwesties concentreren die nieuw en kritiek voor uw doelverbetering zijn. Het gebruikt de [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) en geeft altijd resultaten weer die de versie van uw project vergelijken met de meest recente uitgebrachte versie.
