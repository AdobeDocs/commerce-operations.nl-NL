---
title: 'ACSD-51036: Onjuiste omstandigheden tijdens gelijktijdige REST API-aanroepen leiden tot een overschrijving van de verzendstatus'
description: Pas de ACSD-51036-patch toe om het Adobe Commerce-probleem op te lossen waarbij er rasvoorwaarden zijn tijdens gelijktijdige REST API-aanroepen die leiden tot het overschrijven van de verzendstatus in de tabel met items die zijn besteld.
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-51036: De omstandigheden van de ruimte tijdens gelijktijdige vraag REST API resulteren in een overschrijving van de verzendstatus in de punten bevolen lijst

De ACSD-51036-patch verhelpt het probleem waarbij de rasomstandigheden tijdens gelijktijdige REST API-aanroepen resulteren in een overschrijving van de verzendstatus in de geordende tabel. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.31 wordt geïnstalleerd. De patch-id is ACSD-51036. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De rassenvoorwaarden tijdens gelijktijdige REST API-aanroepen resulteren in een overschrijving van de verzendstatus in de items die zijn geordend in de tabel.

<u> Stappen om </u> te reproduceren:

1. Maak een bestelling met twee items.
1. Factuurpost A.
1. Verzend tegelijkertijd een aanvraag voor terugbetaling voor object A via REST API terwijl u een aanvraag voor het object B verzendt.
1. Ga naar de volgorde in **[!UICONTROL Admin Panel]** .

<u> Verwachte resultaten </u>

De status *[!UICONTROL Shipped 1]* moet aanwezig zijn voor item B in de *[!UICONTROL Items]* geordende tabel.

<u> Ware resultaten </u>

*[!UICONTROL Shipped 1]* status is niet aanwezig voor item B in de *[!UICONTROL Items]* geordende tabel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
