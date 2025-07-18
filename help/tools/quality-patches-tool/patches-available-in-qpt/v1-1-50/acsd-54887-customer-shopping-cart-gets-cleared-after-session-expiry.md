---
title: 'ACSD-54887: Winkelwagentje van klanten wordt gewist nadat de sessie van de klant is verlopen'
description: Pas de ACSD-54887-patch toe om het Adobe Commerce-probleem op te lossen waarbij het winkelwagentje van de klant wordt gewist nadat de klantensessie is verlopen en [!UICONTROL Persistent Shopping Cart] ingeschakeld is.
feature: Shopping Cart
role: Admin, Developer
exl-id: de2a96b2-48ce-4b9b-93bc-f7b64c37463a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-54887: Winkelwagentje van klanten wordt gewist nadat de sessie van de klant is verlopen

De ACSD-54887-patch verhelpt het probleem waarbij het winkelwagentje van de klant wordt gewist nadat de klantensessie is verlopen en [!UICONTROL Persistent Shopping Cart] ingeschakeld is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-5487. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p8, 2.4.5-p3 - 2.4.5-p7, en 2.4.6-p1 - 2.4.6-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Winkelwagentje voor klanten wordt gewist nadat de klantensessie is verlopen met [!UICONTROL Persistent Shopping Cart] ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Schakel [!UICONTROL Persistent Shopping Cart] in. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** = *ja*.

   Log in met persistentie ingeschakeld (Opmerking: deze is niet beschikbaar op de popup-autorisatie, maar alleen op de directe [!UICONTROL Sign in] -pagina).

1. Voeg een product toe aan de kar.
1. Ga door met de kassa en selecteer een betalingsmethode.
1. Verloop de sessie (verwijder `PHPSESSID` ).
1. Vernieuw de pagina. Let erop dat het aanhalingsteken direct wordt omgezet in een gastcitaat omdat er al een betalingsmethode is geselecteerd en het cookie [!UICONTROL Persistent Cart] wordt verwijderd.
1. Verloop de sessie (verwijder `PHPSESSID` ).
1. Vernieuw de pagina. Zie dat de wagen leeg is.
1. Log opnieuw in.

<u> Verwachte resultaten </u>:

Het product van de winkelwagen is beschikbaar wanneer u zich weer aanmeldt.

<u> Ware resultaten </u>:

Het winkelwagentje is leeg wanneer je opnieuw inlogt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
