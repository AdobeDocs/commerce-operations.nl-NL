---
title: "ACSD-56280: Aankopen van cadeauregisters zijn niet voltooid"
description: Pas de ACSD-56280-patch toe om het Adobe Commerce-probleem op te lossen waarbij de aankopen van het cadeauregister niet zijn voltooid
feature: Checkout
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-56280: aankopen van cadeauregisters worden niet voltooid

De ACSD-56280-patch verhelpt het probleem waarbij de aankopen van het cadeauregister niet zijn voltooid. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-56280. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aankopen van het cadeauregister worden niet voltooid.

<u> Stappen om </u> te reproduceren:

1. Meld u aan als klant en voeg een **[!UICONTROL product]** toe aan een cadeauregister.
1. Deel de koppeling voor het cadeauregister.
1. Open de koppeling voor het cadeauregister in een andere browser/incognito-venster.
1. Voeg de hoeveelheid toe en voeg de items toe aan het winkelwagentje.
1. Ga naar **[!UICONTROL Checkout Page]** en selecteer **[!UICONTROL shipping method]** (Aangezien het verzendadres al is geselecteerd, opgegeven door de registrant).
1. Selecteer de betalingsmethode.
1. Klik op de knop Plaatsvolgorde.

<u> Verwachte resultaten </u>:

De volgorde moet worden geplaatst.

<u> Ware resultaten </u>:

De volgorde wordt niet geplaatst en de weergegeven fout is: `Call to a member function getUpdatedQty() on null` .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
