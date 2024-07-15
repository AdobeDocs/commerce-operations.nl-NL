---
title: Het  [!DNL Infra]  lusje
description: Het  [!DNL Infra]  lusje isoleert kwesties en oorzaken van infrastructuurproblemen.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Het tabblad [!DNL Infra]

Het tabblad **[!DNL Infra]** isoleert problemen en oorzaken van infrastructuurproblemen. Verder worden de frames beschreven die u op het tabblad kunt zien.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![ alarm van de Dienst ](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

In de grafiek **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** worden de servicewaarschuwingen weergegeven die door de [!DNL New Relic] Infrastructure Agent zijn verzameld. Dit zal de dienstherstart tonen, velen verbonden aan plaatsingen.

## [!UICONTROL Inode usage by mount]

![ gebruik van de knoop door onderstel ](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

In het **[!UICONTROL Inode usage by mount]** -frame wordt [!DNL inode] -gebruik weergegeven door de koppeling over de geselecteerde tijdlijn te plaatsen. Hoewel er mogelijk genoeg opslagruimte vrij is, zal een knooppunt dat uit [!DNL inodes] loopt, een gebrek aan beschikbare opslag tonen. Als u bestanden verwijdert (met name kleine bestanden), wordt er zowel ruimte vrijgemaakt als wordt [!DNL inodes] beschikbaar gesteld.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![ vCPU rijmening over chronologie GROTER 2 weken ](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

In het frame **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** wordt de vCPU-rijweergave gedurende de geselecteerde periode van meer dan twee weken weergegeven. In dit frame wordt gekeken naar het aantal vCPU&#39;s dat is toegewezen aan de weergegeven toepassingsnaam van [!DNL New Relic] .

## [!UICONTROL vCPU tier view over timeline]

![ vCPU rijmening over chronologie ](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

Het frame **[!UICONTROL vCPU tier view over timeline]** toont de vCPU-rijweergave gedurende de geselecteerde tijdlijn van meer dan 24 uur. In dit frame wordt gekeken naar het aantal vCPU&#39;s dat is toegewezen aan de weergegeven toepassingsnaam van [!DNL New Relic] . Het zal zowel cluster upsizes als downsizes tonen.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![ vCPU rijmening over chronologie door NODE ](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

In het frame **[!UICONTROL vCPU tier view over timeline BY NODE]** worden de vCPU-rijweergaven over het geselecteerde tijdframe per knooppunt weergegeven. Dit frame is handig voor het detecteren van verlies van knooppunten of wanneer knooppunten groter of kleiner worden gemaakt. In de vCPU-rijweergave gedurende de tijdlijn BY NODE moet u naar een tijdlijn van MINDER dan 24 uur kijken.

## [!UICONTROL Instance details]

![ Details van de Instantie ](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

In de tabel **[!UICONTROL Instance details]** worden instantiedetails van elke [!DNL New Relic] -toepassing weergegeven.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![ non-responsive-node ](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

In het frame **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** worden niet-responsieve knooppunten over een tijdsperiode weergegeven.
