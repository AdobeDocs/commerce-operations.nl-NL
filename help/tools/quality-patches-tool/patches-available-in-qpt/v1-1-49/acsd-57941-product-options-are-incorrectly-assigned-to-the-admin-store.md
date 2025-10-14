---
title: 'ACSD-57941: de opties van het product worden verkeerd toegewezen aan de adminstore'
description: Pas de ACSD-57941-patch toe om het Adobe Commerce-probleem op te lossen, waarbij productopties onjuist aan de beheerwinkel worden toegewezen in plaats van aan de respectievelijke winkels.
feature: Products
role: Admin, Developer
exl-id: a78c1797-c366-4931-b036-966d3dcf59bb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-57941: de opties van het product worden verkeerd toegewezen aan de adminstore

De ACSD-57941-patch verhelpt het probleem waarbij de productopties ten onrechte aan de beheerwinkel worden toegewezen in plaats van aan de respectievelijke winkels. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-57941. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Productopties worden ten onrechte toegewezen aan de beheerwinkel in plaats van aan hun respectievelijke winkels.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Importeer hetzelfde product met enkele aangepaste opties.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en open het gemaakte product. Klik op **[!UICONTROL Customizable options]** en controleer of de geïmporteerde opties zichtbaar zijn.
1. Importeer hetzelfde bestand nog een paar keer.

<u> Verwachte resultaten </u>:

Aangepaste opties worden bijgewerkt.

<u> Ware resultaten </u>:

Aangepaste opties voor het product worden gedupliceerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
