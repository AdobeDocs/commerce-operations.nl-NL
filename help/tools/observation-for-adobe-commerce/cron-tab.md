---
title: Het  [!DNL Cron]  lusje
description: Leer over het  [!DNL Cron]  lusje van  [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Het tabblad [!DNL Cron]

Dit tabblad is een poging om problemen en oorzaken van [!DNL cron] -problemen snel te isoleren.

## [!UICONTROL Cron transaction duration in seconds]

![ de transactieduur van het Gewas in seconden ](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

In het frame **[!UICONTROL Cron transaction duration in seconds]** wordt de transactieduur [!DNL crons] in seconden weergegeven. Hiermee worden transacties met lange runtimes weergegeven. Een diepere duik in APM zal meer details tonen over welke vraag de transactie/de verrichting kan lopen.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![ MySQL het Niet Slepen Threads door Knoop ](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

In het frame **[!UICONTROL MySQL Non-Sleeping Threads by Node]** ziet u de MySQL-verbindingen die niet uit elkaar liggen, nochtans over de geselecteerde tijdlijn.

## [!UICONTROL SQL Trace count by path]

![ SQL de telling van het Spoor door weg ](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

In het frame **[!UICONTROL SQL Trace count by path]** wordt gekeken naar het aantal MySQL-sporen per pad, zodat SQL-instructies in een geselecteerd tijdskader kunnen worden getraceerd.

## [!UICONTROL Cron database call]

![ de gegevensbestandvraag van de Kroon ](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

In het frame **[!UICONTROL Cron database call]** wordt gekeken naar het aantal [!DNL crons] dat binnen een geselecteerd tijdsbestek naar de database wordt aangeroepen.

## [!UICONTROL Cron schedule table locks]

![ de sloten van de de planningstabel van het Gewas ](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

In het **[!UICONTROL Cron schedule table locks]** -frame wordt gekeken naar [!DNL cron] -planningstabel die over een geselecteerd tijdframe wordt vergrendeld.

## [!UICONTROL Cron schedule clean cron fired]

![ de sloten van de de planningstabel van het Gewas ](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

In het frame **[!UICONTROL Cron schedule clean cron fired]** wordt gekeken naar het aantal [!DNL crons] dat binnen een geselecteerd tijdsbestek is opgeschoond. Als er in dit frame geen gegevens worden weergegeven, kan dit wijzen op een probleem met de juiste uitvoering van [!DNL crons] . Als het [!DNL cron] -taakschema niet wordt schoongemaakt, wordt [!DNL crons] niet optimaal uitgevoerd en kan het langer duren om het uit te voeren.

## [!UICONTROL Cron schedule clean records details table]

![ het programma van het Gewas schone verslag- detaillijst ](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

De tabel **[!UICONTROL Cron schedule clean records details table]** bevat gegevens over de taak waarmee records uit de tabel `cron_schedule` in een geselecteerd tijdsbestek kunnen worden gewist.

## [!UICONTROL cron_schedule table updates]

![ cron_planning lijstupdates ](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

In het frame **[!UICONTROL cron_schedule table updates]** wordt gekeken naar het aantal [!DNL cron] geplande tabelupdates over een geselecteerd tijdsbestek. Hoge activiteit bij het verwijderen of bijwerken van deze tabel kan wijzen op een probleem met [!DNL crons] . [!DNL crons] werkt deze tabel ook bij wanneer deze wordt uitgevoerd en voltooid. Als er geen activiteit is in deze tabel en [!DNL crons] is geconfigureerd, kan er een probleem optreden met [!DNL crons] .

## [!UICONTROL Datastore Operations Tables]

![ de Lijsten van de Verrichtingen van de Datastore ](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

In **[!UICONTROL Datastore Operations Tables]** worden tabelbewerkingen met databases, waaronder `SELECT` , `DELETE` en `UPDATE` , in een geselecteerd tijdkader weergegeven. Dit kader toont de gegevensbestandlijsten met de hoogste verrichtingsfrequentie tegen hen.
