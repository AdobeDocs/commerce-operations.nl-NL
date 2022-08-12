---
title: '"De [!UICONTROL Cron] tab"'
description: Meer informatie over de [!UICONTROL Cron] tabblad van [!DNL Observation for Adobe Commerce].
source-git-commit: 3c1e50b3bff1bd2b2760e2e763173275161b0044
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# De [!UICONTROL Cron] tab

Dit tabblad is een poging om problemen en oorzaken van snijproblemen snel te isoleren.

## [!UICONTROL Cron transaction duration in seconds]

![Transactieduur bijsnijden in seconden](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

De **[!UICONTROL Cron transaction duration in seconds]** in frame wordt de duur van de transactie uitgedrukt in korrels in seconden. Hiermee worden transacties met lange runtimes weergegeven. Een diepere duik in APM zal meer details tonen over welke vraag de transactie/de verrichting kan lopen.

## [!UICONTROL MySql Non-Sleeping Threads by Node]

![MySql niet-slaapende threads per knooppunt](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

De **[!UICONTROL MySql Non-Sleeping Threads by Node]** frame toont de MySql niet-slaapende verbindingen per knooppunt over de geselecteerde tijdlijn.

## [!UICONTROL SQL Trace count by path]

![Aantal SQL-overtrekken per pad](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

De **[!UICONTROL SQL Trace count by path]** Het kader kijkt naar MySql spoortellingen door weg, die SQL verklaringen over een geselecteerd tijdskader kunnen helpen vinden.

## [!UICONTROL Cron database call]

![Aanroep van Cron-database](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

De **[!UICONTROL Cron database call]** frame bekijkt het aantal manden die aan het gegevensbestand over een geselecteerd tijdkader roepen.

## [!UICONTROL Cron schedule table locks]

![Tabelvergrendelingen uitsnijden](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

De **[!UICONTROL Cron schedule table locks]** frame bekijkt de tabelvergrendelingen voor de uitsnijdplanning over een geselecteerd tijdkader.

## [!UICONTROL Cron schedule clean cron fired]

![Tabelvergrendelingen uitsnijden](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

De **[!UICONTROL Cron schedule clean cron fired]** frame bekijkt het aantal manen dat over een geselecteerd tijdsbestek wordt schoongemaakt. Als er in dit frame geen gegevens worden weergegeven, kan dit wijzen op een probleem met de juiste werking van bakens. Als het programma voor de uitsnijdtaak niet wordt schoongemaakt, worden de crons niet optimaal uitgevoerd en kan het langer duren om deze uit te voeren.

## [!UICONTROL Cron schedule clean records details table]

![Detailstabel met gegevens over uitgesneden planning](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

De **[!UICONTROL Cron schedule clean records details table]** tabel bevat details over de taak die moet worden gebruikt voor het opschonen van records uit de `cron_schedule` een tabel in een geselecteerd tijdkader plaatsen.

## [!UICONTROL cron_schedule table updates]

![tabel-updates uitsnijden_plannen](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

De **[!UICONTROL cron_schedule table updates]** frame bekijkt het aantal geplande bijgesneden tabelupdates over een geselecteerd tijdkader. Een hoge activiteit bij het verwijderen of bijwerken van deze tabel kan wijzen op een probleem met bakens. Ook, werken de bakens deze lijst bij wanneer zij lopen en voltooien, zodat als er geen activiteit op deze lijst is en er gevormde bakens zijn, er een probleem met kronnen zou kunnen zijn.

## [!UICONTROL Datastore Operations Tables]

![Tabellen voor bewerkingen in datastore](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

De **[!UICONTROL Datastore Operations Tables]** bekijkt de verrichtingen van de gegevensbestandlijst, met inbegrip van `SELECT`, `DELETE`, en `UPDATE` over een geselecteerd tijdkader. Dit kader toont de gegevensbestandlijsten met de hoogste verrichtingsfrequentie tegen hen.
