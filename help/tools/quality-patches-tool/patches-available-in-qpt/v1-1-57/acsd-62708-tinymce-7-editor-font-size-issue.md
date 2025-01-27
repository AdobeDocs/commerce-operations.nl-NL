---
title: 'ACSD-62708: [!DNL TinyMCE]  7 grootte van de redacteursdoopvont in admin paneel toont PT'
description: Pas ACSD-62708 flard toe om de kwestie van Adobe Commerce te bevestigen waar  [!DNL TinyMCE]  7 de grootte van de redacteursdoopvont in admin PT en niet PX toont. U kunt nu ook de tekengrootte instellen in PX in plaats van PT.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: ecb04a058e858580dfbc7a1edcd319423be9eeaa
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# ACSD-62708: [!DNL TinyMCE] 7-editorlettergrootte in deelvenster Beheer toont PT

De ACSD-62708-patch verhelpt het probleem waarbij de [!DNL TinyMCE] 7 editor font size in the admin panel in PT wordt weergegeven in plaats van PX. Met deze patch kunt u de tekengrootte instellen in PX. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-62708. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

In de [!DNL TinyMCE] 7-editor in het deelvenster Beheer wordt de tekengrootte weergegeven in PT in plaats van PX.

<u> Stappen om </u> te reproduceren:

1. Open de productbewerkingspagina in het deelvenster Beheer.
1. Vouw de sectie [!UICONTROL Content] uit.
1. Controleer de besturingselementen voor lettertypen in de [!DNL TinyMCE] -editor.

<u> Verwachte resultaten </u>:

De tekengrootte moet in PX zijn.

<u> Ware resultaten </u>:

De tekengrootte is in PT.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.