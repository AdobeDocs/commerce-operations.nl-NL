---
title: "ACSD-51431: De status van de indexeerder is *[!UICONTROL Working]* alhoewel er geen ingangen in de changelog zijn"
description: Pas ACSD-51431 flard toe om de kwestie van Adobe Commerce te bevestigen waar de indexeerstatus * [!UICONTROL Working]* is alhoewel er geen ingangen in de verandering zijn.
feature: Logs, Price Indexer
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-51431: Indexerstatus is *[!UICONTROL Working]* , ook al bevat het wijzigen geen items

De ACSD-51431-patch verhelpt het prestatieprobleem waarbij de indexeerstatus *[!UICONTROL Working]* is, ook al bevat de wijziging geen items. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.33 is geïnstalleerd. De patch-id is ACSD-51431. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De indexeerstatus is *[!UICONTROL Working]* , ook al bevat het wijzigen geen items.

<u> Stappen om </u> te reproduceren:

1. Stel **[!UICONTROL indexers]** in op [!UICONTROL Update on Schedule] .
1. Configureer de uitsnijdtaak die elke minuut moet worden uitgevoerd.
1. Sla de wijzigingen in verschillende producten tegelijk op.
1. Voer `bin/magento indexer:status` over een paar minuten uit.

<u> Verwachte resultaten </u>:

De wijzigingen worden verwerkt en de indexen hebben de status *[!UICONTROL Ready]* . De *[!UICONTROL Schedule]* status is *[!UICONTROL idle (0 in the backlog)]* .

<u> Ware resultaten </u>:

De wijzigingen worden verwerkt en de indexen hebben de status *[!UICONTROL Ready]* . De status *[!UICONTROL Schedule]* wordt echter wel weergegeven *[!UICONTROL working (0 in the backlog)]* .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
