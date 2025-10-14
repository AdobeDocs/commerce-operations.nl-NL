---
title: Integreer  [!DNL Site-Wide Analysis Tool]
description: Volg deze stappen om het  [!DNL Upgrade Compatibility Tool]  rapport van het  [!DNL Site-Wide Analysis Tool]  dashboard op uw project van Adobe Commerce terug te winnen.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# De [!DNL Site-Wide Analysis Tool] integreren

[!DNL Site-Wide Analysis Tool] biedt 24/7 real-time prestatiebewaking, rapporten en aanbevelingen voor de beveiliging en operabiliteit van Adobe Commerce-instanties.

[!DNL Upgrade Compatibility Tool] is nu geïntegreerd met [!DNL Site-Wide Analysis Tool] om de capaciteit voor niet-technische mensen te verstrekken om [!DNL Upgrade Compatibility Tool] in werking te stellen en a [&#x200B; rapport &#x200B;](../upgrade-compatibility-tool/reports.md) te krijgen die een lijst van kwesties voor elk dossier bevatten.

Zie de [[!DNL Site-Wide Analysis Tool]  gebruikersgids &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/site-wide-analysis-tool/access) voor meer informatie.

## Voer de [!DNL Upgrade Compatibility Tool] uit vanaf de [!DNL Site-Wide Analysis Tool]

Navigeer naar het [!DNL Site-Wide Analysis Tool] dashboard voor uw project en zoek de [!DNL Upgrade Compatibility Tool] -widget.

![&#x200B; UCT SWAT widget - Aanvankelijk &#x200B;](../../assets/upgrade-guide/uct-swat-initial.png)

Klik op **[!UICONTROL Run Upgrade Scan]**. Afhankelijk van de grootte van het project kan de scan enige tijd duren. Een spinner geeft aan dat de scan wordt uitgevoerd.

![&#x200B; UCT SWAT widget - Bezig &#x200B;](../../assets/upgrade-guide/uct-swat-progress.png)

Nadat de scan is voltooid, worden de resultaten op hoog niveau weergegeven in de widget.

![&#x200B; UCT SWAT widget - Resultaten &#x200B;](../../assets/upgrade-guide/uct-swat-results.png)

Klik **[!UICONTROL Download Report]** om het [!DNL Upgrade Compatibility Tool] [&#x200B; HTML rapport &#x200B;](../upgrade-compatibility-tool/reports.md#html-report) terug te winnen en de details te herzien.


>[!NOTE]
>
> Als u [!DNL Upgrade Compatibility Tool] doorloopt via [!DNL Site-Wide Analysis Tool] , worden uw resultaten geoptimaliseerd en kunt u zich richten op nieuwe en kritieke problemen voor de doelupgrade. Hierbij wordt de optie [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) gebruikt en worden altijd resultaten weergegeven die de versie van uw project vergelijken met de meest recente uitgebrachte versie.
