---
title: Het tabblad [!UICONTROL Redis]
description: Leer meer over het [!UICONTROL Redis] lusje van  [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 4caabd1578e56b74600441c9c779b7b2dfd06987
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Het tabblad [!DNL Redis]

## [!UICONTROL Redis Node summary]

![ Redis Overzicht van de Knoop ](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

**[!UICONTROL Redis Node summary]** is inclusief alle knooppunten in een omgeving. In het bovenstaande voorbeeld staan de knooppunten voor gedeelde staging. Er zijn één primaire en twee secundaire werknemers in productie en ook een primaire en twee secundaire staging.

## [!UICONTROL Redis node detail]

![ Redis de metriek van serverprestaties en de details van de knoopconfiguratie ](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

Het frame **[!UICONTROL Redis node detail]** geeft de omgeving, [!DNL Redis] rol, softwareversie en knooppuntgrootte aan.

## [!UICONTROL Redis node roles timeline]

![ herdiept de chronologie van knooprollen ](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

Het frame **[!UICONTROL Redis node roles timeline]** geeft het verlies aan van [!DNL Redis] -service in bepaalde rollen aan. Als een lijn dips, wijst het erop dat de bepaalde rol die de lijn vertegenwoordigt een knoop of knopen heeft verloren.

## [!UICONTROL Connection to Redis]

![ Verbinding aan Redis ](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

In het frame **[!UICONTROL Connection to Redis]** wordt de waarde net.connectedClients uit de voorbeeldgegevens van [!DNL New Relic Redis] weergegeven. Het toont het aantal verbindingen door [!DNL New Relic] toepassing (milieu) en knoop.

## [!UICONTROL Commands per second by node]

![ Bevelen per seconde door knoop ](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

In het frame **[!UICONTROL Commands per second by node]** worden de [!DNL Redis] -opdrachten per knooppunt per seconde gedurende de geselecteerde tijdlijn weergegeven.

## [!UICONTROL Redis % of memory used]

![ Redis % van gebruikt geheugen ](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

In het frame **[!UICONTROL Redis % of memory used]** wordt het percentage weergegeven van het maximale geheugen dat door de [!DNL Redis] -servers wordt gebruikt.

## [!UICONTROL Redis used memory]

![ opnieuw wordt gebruikt geheugen ](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

In het frame **[!UICONTROL Redis used memory]** wordt het knooppuntgebruik in GB/MB weergegeven.

## [!UICONTROL Redis changes since last db save]

![ herstelt veranderingen sinds laatste db sparen ](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] is een geheugeningezetene en slaat de informatie op voor opslag. Het frame **[!UICONTROL Redis changes since last db save]** geeft het aantal wijzigingen in het geheugen aan dat is opgetreden sinds de laatste database naar de opslaglocatie is opgeslagen. Verwijs naar [ Redis persistentie ](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/) voor meer verklaring over [!DNL Redis's] persistentie.

## [!UICONTROL Redis synchronization from Log]

![ herstelt synchronisatie van Logboek ](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

Het **[!UICONTROL Redis synchronization from Log]** -frame richt zich op de fouten die optreden tijdens [!DNL Redis] -synchronisatie of op fouten die optreden als gevolg van synchronisatieproblemen. Voor meer informatie over [!DNL Redis], verwijs naar [[!DNL Redis]  Documentatie ](https://redis.io/docs/).
