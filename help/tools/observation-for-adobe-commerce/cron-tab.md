---
title: De [!DNL Cron] tab
description: Meer informatie over de [!DNL Cron] tabblad van [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# De [!DNL Cron] tab

Dit tabblad is een poging om problemen en oorzaken van [!DNL cron] problemen.

## [!UICONTROL Cron transaction duration in seconds]

![Transactieduur bijsnijden in seconden](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

De **[!UICONTROL Cron transaction duration in seconds]** frame wordt weergegeven [!DNL crons] transactieduur in seconden. Hiermee worden transacties met lange runtimes weergegeven. Een diepere duik in APM zal meer details tonen over welke vraag de transactie/de verrichting kan lopen.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL niet-slaapende threads per knooppunt](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

De **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame toont de MySQL niet-slaapende threads per knooppunt over de geselecteerde tijdlijn.

## [!UICONTROL SQL Trace count by path]

![Aantal SQL-overtrekken per pad](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

De **[!UICONTROL SQL Trace count by path]** frame bekijkt MySQL spoor tellingen door weg, die SQL verklaringen over een geselecteerd tijdskader kunnen helpen vinden.

## [!UICONTROL Cron database call]

![Aanroep van Cron-database](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

De **[!UICONTROL Cron database call]** frame bekijkt het aantal [!DNL crons] het aanroepen van de database in een geselecteerd tijdskader.

## [!UICONTROL Cron schedule table locks]

![Tabelvergrendelingen uitsnijden](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

De **[!UICONTROL Cron schedule table locks]** frame kijkt naar [!DNL cron] planningstabel loopt over een geselecteerd tijdkader.

## [!UICONTROL Cron schedule clean cron fired]

![Tabelvergrendelingen uitsnijden](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

De **[!UICONTROL Cron schedule clean cron fired]** frame bekijkt het aantal [!DNL crons] opruimen over een geselecteerd tijdkader. Als er in dit frame geen gegevens worden weergegeven, kan dit wijzen op een probleem met [!DNL crons] correct wordt uitgevoerd. Als de [!DNL cron] de dienstregeling niet is schoongemaakt; [!DNL crons] niet optimaal wordt uitgevoerd en kan langer duren.

## [!UICONTROL Cron schedule clean records details table]

![Detailstabel met gegevens over uitgesneden planning](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

De **[!UICONTROL Cron schedule clean records details table]** tabel bevat details over de taak die moet worden gebruikt voor het opschonen van records uit de `cron_schedule` een tabel in een geselecteerd tijdkader plaatsen.

## [!UICONTROL cron_schedule table updates]

![tabel-updates uitsnijden_plannen](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

De **[!UICONTROL cron_schedule table updates]** frame bekijkt het aantal [!DNL cron] De geplande tabel wordt bijgewerkt over een geselecteerd tijdsbestek. Een hoge activiteit bij het verwijderen of bijwerken van deze tabel kan wijzen op een probleem met [!DNL crons]. Ook, [!DNL crons] werk deze tabel bij wanneer ze worden uitgevoerd en voltooid, dus als deze tabel geen activiteit bevat en er [!DNL crons] geconfigureerd, kan er een probleem zijn met [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tabellen voor bewerkingen in datastore](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

De **[!UICONTROL Datastore Operations Tables]** bekijkt de verrichtingen van de gegevensbestandlijst, met inbegrip van `SELECT`, `DELETE`, en `UPDATE` over een geselecteerd tijdkader. Dit kader toont de gegevensbestandlijsten met de hoogste verrichtingsfrequentie tegen hen.
