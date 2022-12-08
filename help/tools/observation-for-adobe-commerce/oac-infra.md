---
title: "De [!DNL Infra] tab"
description: De [!DNL Infra] -tabblad isoleert problemen en oorzaken van infrastructuurproblemen.
source-git-commit: 38467ebd2ec29f9e1679182fb1ee7076d738664b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# De [!DNL Infra] tab

De **[!DNL Infra]** -tabblad isoleert problemen en oorzaken van infrastructuurproblemen. Verder worden de frames beschreven die u op het tabblad kunt zien.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Servicewaarschuwingen](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

De **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** grafiek toont de door de [!DNL New Relic] infrastructuuragent. Dit zal de dienstherstart tonen, velen verbonden aan plaatsingen.

## [!UICONTROL Inode usage by mount]

![Gebruik van knooppunt door koppelen](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

De **[!UICONTROL Inode usage by mount]** frame shows [!DNL inode] het gebruik door over het geselecteerde tijdkader te koppelen. Ook al is er misschien veel opslagruimte vrij, als een knooppunt op is [!DNL inodes], zal er een gebrek aan beschikbare opslag zijn. Als u bestanden verwijdert (vooral kleine bestanden), wordt er ruimte vrijgemaakt en wordt [!DNL inodes] beschikbaar.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![vCPU-rijweergave over tijdlijn GROTER 2 weken](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

De **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** frame toont de vCPU-rijweergave gedurende het geselecteerde tijdsbestek van meer dan twee weken. In dit frame wordt gekeken naar het aantal vCPU&#39;s dat is toegewezen aan de [!DNL New Relic] toepassingsnaam weergegeven.

## [!UICONTROL vCPU tier view over timeline]

![vCPU-rijweergave over tijdlijn](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

De **[!UICONTROL vCPU tier view over timeline]** frame toont de vCPU-rijweergave gedurende het geselecteerde tijdkader van meer dan 24 uur. In dit frame wordt gekeken naar het aantal vCPU&#39;s dat is toegewezen aan de [!DNL New Relic] toepassingsnaam weergegeven. Het zal zowel cluster upsizes als downsizes tonen.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![vCPU-rijweergave over tijdlijn door NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

De **[!UICONTROL vCPU tier view over timeline BY NODE]** frame toont vCPU-rijweergaven in de geselecteerde tijdlijn per knooppunt. Dit frame is handig voor het detecteren van verlies van knooppunten of wanneer knooppunten groter of kleiner worden gemaakt. In de vCPU-rijweergave gedurende de tijdlijn BY NODE moet u naar een tijdlijn van MINDER dan 24 uur kijken.

## [!UICONTROL Instance details]

![Instantiedetails](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

De **[!UICONTROL Instance details]** tabel bevat instantiedetails van elk [!DNL New Relic] toepassing.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![non-responsive-node](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

De **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** frame toont de knooppunten die niet reageren gedurende een tijdsperiode.
