---
title: 'ACSD-49497: nog te verwerken order na verzending en gedeeltelijke terugbetaling'
description: Pas de ACSD-49497-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de status van de bestelling na verzending behouden blijft en een gedeeltelijke terugbetaling wordt toegepast.
feature: Admin Workspace, Orders, Shipping/Delivery
role: Admin
exl-id: e2e3d2b3-24be-4827-a735-aebfc6f475ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-49497: nog te verwerken order na verzending en gedeeltelijke terugbetaling

De ACSD-49497-patch verhelpt het probleem dat de status van de bestelling blijft bestaan als verwerking na verzending en dat een gedeeltelijke terugbetaling wordt toegepast. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 wordt geïnstalleerd. De patch-id is ACSD-49497. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van een nieuwe bestelling blijft in de status *[!UICONTROL Processing]* behouden, zelfs na verzending en er wordt een gedeeltelijke terugbetaling toegepast.

<u> Stappen om </u> te reproduceren:

1. Maak een volgorde met meerdere items.
1. Maak vanuit **[!UICONTROL Admin]** een factuur voor de bestelling.
1. Maak vanuit **[!UICONTROL Admin]** een creditcard en restitueer een object slechts gedeeltelijk.
1. Vul bij **[!UICONTROL Admin]** aan om verzending te vragen voor de resterende objecten in de bestelling.
1. Bekijk de status van de order.

<u> Verwachte resultaten </u>:

De status van de volgorde moet *[!UICONTROL Complete]* zijn.

<u> Ware resultaten </u>:

De status van de volgorde blijft *[!UICONTROL Processing]*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
