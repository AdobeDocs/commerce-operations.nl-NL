---
title: 'ACSD-47336: [!UICONTROL Something went wrong] fout bij het negeren van berichten in Adobe Commerce Admin'
description: Pas ACSD-47336 flard toe om de kwestie van Adobe Commerce te bevestigen waar de gebruiker [!UICONTROL Something went wrong] fout ziet wanneer het verwerpen van berichten in  [!DNL Commerce]  Admin.
feature: Admin Workspace
role: Admin
exl-id: da0c0119-6720-493f-a278-d573ed898a63
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47336: _[!UICONTROL Something went wrong]_&#x200B;fout bij het negeren van berichten in Adobe Commerce Admin

De ACSD-47336-patch verhelpt het probleem waarbij de gebruiker de _[!UICONTROL Something went wrong]_-fout ziet bij het negeren van meldingen in [!DNL Commerce] Admin. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24 wordt geïnstalleerd. De patch-id is ACSD-47336. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden): 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker krijgt _[!UICONTROL Something went wrong]_&#x200B;foutbericht te zien wanneer hij of zij meldingen in [!DNL Commerce] Admin verwijdert.

<u> Stappen om </u> te reproduceren:

1. Een bulkbewerking uitvoeren (bijvoorbeeld bulkupdate van productkenmerken uit het productraster).
1. Voltooi de bewerking (bijvoorbeeld uitvoeren `bin/magento queue:consumer:start product_action_attribute.update`).
1. Vernieuw de [!DNL Commerce] beheerpagina, vouw de sectie voor beheerdersmeldingen uit en klik op de koppeling **[!UICONTROL Dismiss All Completed Tasks]** .

<u> Verwachte resultaten </u>:

De fout _[!UICONTROL Something went wrong]_&#x200B;wordt niet weergegeven wanneer u de voltooide taken wist.

<u> Ware resultaten </u>:

De fout _[!UICONTROL Something went wrong]_&#x200B;wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
