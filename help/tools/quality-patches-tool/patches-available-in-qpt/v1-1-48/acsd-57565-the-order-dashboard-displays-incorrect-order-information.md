---
title: 'ACSD-57565: Het dashboard voor bestellingen bevat onjuiste bestelgegevens'
description: Pas de ACSD-57565-patch toe om het Adobe Commerce-probleem op te lossen, waarbij op het orderdashboard onjuiste bestelgegevens worden weergegeven, totdat de tijdsperiode is bijgewerkt.
feature: Roles/Permissions
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-57565: op het dashboard voor bestellingen worden onjuiste ordegegevens weergegeven

De ACSD-57565-patch verhelpt het probleem waarbij het orderdashboard onjuiste ordergegevens weergeeft tot de tijdsperiode is bijgewerkt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-57565. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als zoektrefwoord om de patch te zoeken

## Probleem

Het orderdashboard geeft onjuiste ordegegevens weer.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL dashboard charts]** in.
1. Maak een bestelling en factureer deze.
1. Wacht ten minste 24 uur na het aanmaken van de bestelling.
1. Controleer de **[!UICONTROL dashboard chart]** -gegevens.
1. Noteer het totale aantal bestellingen.
1. Verander de tijd in de *huidige maand*, en verander het dan terug naar *vandaag*.

<u> Verwachte resultaten </u>:

Het dashboarddiagram zou de correcte statistieken moeten voortdurend tonen.

<u> Ware resultaten </u>:

Het dashboarddiagram toont onjuiste statistieken bij de eerste lading. De nauwkeurige statistieken van de grafiek worden na de tijdsperiode bijgewerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.