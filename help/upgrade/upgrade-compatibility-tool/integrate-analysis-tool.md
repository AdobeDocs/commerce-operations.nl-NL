---
title: Integreer  [!DNL Site-Wide Analysis Tool]
description: Volg deze stappen om het  [!DNL Upgrade Compatibility Tool]  rapport van het  [!DNL Site-Wide Analysis Tool]  dashboard op uw project van Adobe Commerce terug te winnen.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# De [!DNL Site-Wide Analysis Tool] integreren

[!DNL Site-Wide Analysis Tool] biedt 24/7 real-time prestatiebewaking, rapporten en aanbevelingen voor de beveiliging en operabiliteit van Adobe Commerce-instanties.

[!DNL Upgrade Compatibility Tool] is nu geïntegreerd met [!DNL Site-Wide Analysis Tool] om de capaciteit voor niet-technische mensen te verstrekken om [!DNL Upgrade Compatibility Tool] in werking te stellen en a [ rapport ](../upgrade-compatibility-tool/reports.md) te krijgen die een lijst van kwesties voor elk dossier bevatten.

Zie de [[!DNL Site-Wide Analysis Tool]  gebruikersgids ](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) voor meer informatie.

## Voer de [!DNL Upgrade Compatibility Tool] uit vanaf de [!DNL Site-Wide Analysis Tool]

Navigeer naar het [!DNL Site-Wide Analysis Tool] dashboard voor uw project en zoek de [!DNL Upgrade Compatibility Tool] -widget.

![ UCT SWAT widget - Aanvankelijk ](../../assets/upgrade-guide/uct-swat-initial.png)

Klik op **[!UICONTROL Run Upgrade Scan]**. Afhankelijk van de grootte van het project kan de scan enige tijd duren. Een spinner geeft aan dat de scan wordt uitgevoerd.

![ UCT SWAT widget - Bezig ](../../assets/upgrade-guide/uct-swat-progress.png)

Nadat de scan is voltooid, worden de resultaten op hoog niveau weergegeven in de widget.

![ UCT SWAT widget - Resultaten ](../../assets/upgrade-guide/uct-swat-results.png)

Klik **[!UICONTROL Download Report]** om het [!DNL Upgrade Compatibility Tool] [ rapport van de HTML ](../upgrade-compatibility-tool/reports.md#html-report) terug te winnen en de details te herzien.


>[!NOTE]
>
> Als u [!DNL Upgrade Compatibility Tool] doorloopt via [!DNL Site-Wide Analysis Tool] , worden uw resultaten geoptimaliseerd en kunt u zich richten op nieuwe en kritieke problemen voor de doelupgrade. Hierbij wordt de optie [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) gebruikt en worden altijd resultaten weergegeven die de versie van uw project vergelijken met de meest recente uitgebrachte versie.
