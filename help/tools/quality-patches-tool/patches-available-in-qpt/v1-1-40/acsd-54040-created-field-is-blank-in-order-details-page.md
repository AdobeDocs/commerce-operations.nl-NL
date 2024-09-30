---
title: 'ACSD-54040: Het veld [!UICONTROL Created] is leeg in de volgorde waarin B2B-modules zijn ingeschakeld.'
description: Pas de ACSD-54040-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het veld [!UICONTROL Created] leeg is op de pagina met orderdetails wanneer B2B-modules zijn ingeschakeld.
feature: B2B
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-54040: *[!UICONTROL Created]* veld is leeg in de volgorde waarin de B2B-modules zijn ingeschakeld.

De ACSD-54040-patch verhelpt het probleem waarbij het *[!UICONTROL Created]* -veld leeg blijft op de pagina met gegevens over bestellingen wanneer B2B-modules zijn ingeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-54040. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p5, 2.4.4-p6, 2.4.5-p4, 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer B2B-modules zijn ingeschakeld, blijft het veld *[!UICONTROL Created]* leeg op de pagina met orderdetails.

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce met de B2B-module.
1. Maak een nieuwe klant en plaats een bestelling.
1. Ga naar de orderdetails op de voorzijde en controleer het veld *[!UICONTROL Created]* .

<u> Verwachte resultaten </u>:

In het veld *[!UICONTROL Created]* wordt de datum weergegeven waarop de volgorde is gemaakt.

<u> Ware resultaten </u>:

Het veld *[!UICONTROL Created]* is leeg

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
