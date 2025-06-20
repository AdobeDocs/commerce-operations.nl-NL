---
title: 'ACSD-59366: teams met gedeactiveerde gebruikers verwijderen die niet zichtbaar zijn in de teamlijst'
description: Pas de ACSD-59366-patch toe om het Adobe Commerce-probleem op te lossen wanneer een fout optreedt bij het verwijderen van een team dat gedeactiveerde gebruikers bevat die niet zichtbaar zijn in de teamlijst.
feature: GraphQL, Companies
role: Admin, Developer
exl-id: 406d2242-38f9-4852-b311-0ee57c4a7c26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366: teams met gedeactiveerde gebruikers verwijderen die niet zichtbaar zijn in de teamlijst

De ACSD-59366-patch verhelpt het probleem waarbij een fout optreedt wanneer u probeert een team te verwijderen dat gedeactiveerde gebruikers bevat die niet zichtbaar zijn in de teamlijst. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 wordt geïnstalleerd. De patch-id is ACSD-59366. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fout op wanneer u een team verwijdert dat gedeactiveerde gebruikers bevat die niet zichtbaar zijn in de teamlijst.

<u> Eerste vereisten </u>:

Adobe Commerce B2B-modules zijn geïnstalleerd en bedrijven zijn ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Creeer en login met een bedrijfgebruiker.
1. Onder bedrijfstructuur, creeer een nieuw team.
1. Onder het nieuwe team, creeer een nieuwe gebruiker.
1. Bewerk de nieuwe gebruiker en deactiveer.
1. Selecteer het team en verwijder het.

<u> Verwachte resultaten </u>:

Het team heeft een of meer inactieve gebruikers. Als u het team verwijdert, wordt de toewijzing van deze gebruikers ongedaan gemaakt. Niet-actieve gebruikers kunt u vinden in de sectie [!UICONTROL Company Users] .

<u> Ware resultaten </u>:

Er treedt een fout op wanneer u probeert een team met een gedeactiveerde gebruiker te verwijderen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
