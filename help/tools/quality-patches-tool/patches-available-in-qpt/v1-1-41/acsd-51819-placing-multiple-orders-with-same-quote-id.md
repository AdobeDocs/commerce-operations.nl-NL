---
title: 'ACSD-51819: het plaatsen van veelvoudige orden met één enkele citaat identiteitskaart'
description: Pas de ACSD-51819-patch toe om het Adobe Commerce-probleem op te lossen, waarbij meerdere bestellingen via dezelfde aanhalings-id kunnen worden geplaatst.
feature: Orders, Checkout
role: Admin, Developer
exl-id: dbca8790-d947-4104-bba9-b29abcfc0344
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-51819: het plaatsen van veelvoudige orden met één enkele citaat identiteitskaart

De ACSD-51819-patch verhelpt het probleem waarbij meerdere bestellingen via dezelfde aanhalings-id kunnen worden geplaatst. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41 wordt geïnstalleerd. De patch-id is ACSD-51819. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2, 2.4.5-p5, 2.4.6, 2.4.6-p4, 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p11, 2.4.5-p3 - 2.4.5-p10, 2.4.6 - 2.4.6-p8, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Meerdere bestellingen kunnen met dezelfde aanhalings-id worden geplaatst.

<u> Stappen om </u> te reproduceren:

1. Meld u aan als gebruiker.
1. Voeg items aan het winkelwagentje toe en ga door met het afrekenen.
1. Kies een betalingsmethode, maar klik niet op de knop **[!UICONTROL Place Order]** .
1. Meld u aan bij hetzelfde account in een andere browser.
1. Ga door met het uitchecken van dezelfde items zonder op de knop **[!UICONTROL Place Order]** te klikken.
1. Klik op de knop **[!UICONTROL Place Order]** in beide systemen tegelijk.
1. Valideer de orders die in beide browsers zijn geplaatst.

<u> Verwachte resultaten </u>:

Alleen de eerste bestelling die vanuit één browser is geplaatst, wordt verwerkt.

<u> Ware resultaten </u>:

Bestellingen zijn in beide browsers geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
