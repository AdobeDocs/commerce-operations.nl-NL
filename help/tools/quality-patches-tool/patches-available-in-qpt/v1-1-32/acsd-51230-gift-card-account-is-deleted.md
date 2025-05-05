---
title: 'ACSD-51230: Cadeaukaartaccount is verwijderd'
description: Pas de ACSD-51230-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de rekening van de cadeaukaart wordt verwijderd wanneer de gedeeltelijke terugbetaling van een eenvoudig product wordt verwerkt op basis van een bestelling.
feature: Customer Service, Gift, Marketing Tools
role: Admin
exl-id: a4aed574-3908-42e0-ac32-911f61b44995
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-51230: Cadeaukaartaccount is verwijderd

De ACSD-51230-patch verhelpt het probleem waarbij de rekening van de cadeaukaart wordt verwijderd wanneer de gedeeltelijke terugbetaling van een eenvoudig product wordt verwerkt op basis van een bestelling. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-51230. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De rekening van de cadeaukaart wordt geschrapt wanneer de gedeeltelijke terugbetaling van een eenvoudig product van een orde wordt verwerkt.

<u> Stappen om </u> te reproduceren:

1. Creeer een orde met a *Kaart van het Cadeautje* en a *eenvoudig product* (b.v., *voeg toe: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (om het even welke betaling en verzendmethode werken).
1. Factuur de bestelling.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]** . Er wordt een account gemaakt voor de cadeaukaart.
1. Ga nu naar **[!UICONTROL Order]** en maak een **[!UICONTROL Credit Memo]** .
1. Verander de hoeveelheid voor de *Kaart van het Cadeautje* in 0 en werk het bij. Dit zal tot een gedeeltelijke terugbetaling voor het *eenvoudige product* leiden.
1. Klik op **[!UICONTROL Refund]** .
1. Vernieuw nu **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Het nieuwe account wordt verwijderd.

<u> Verwachte resultaten </u>

De rekening van de cadeaukaart is beschikbaar voor gebruik omdat de terugbetaling niet is gemaakt voor de cadeaukaart.

<u> Ware resultaten </u>

Het kaartenaccount wordt verwijderd en de cadeaukaart wordt niet terugbetaald.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
