---
title: 'ACSD-56447: Als hetzelfde product via parallelle web REST API aan het winkelwagentje wordt toegevoegd, ontstaan er twee aparte items in het winkelwagentje'
description: Pas de ACSD-56447-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het toevoegen van hetzelfde product aan de winkelwagentje via parallel REST API-aanvragen resulteert in twee aparte items in de winkelwagentje.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: ef0b2ce7-74f5-47b6-a44c-bda898c444b2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56447: Als hetzelfde product via parallelle web REST API aan het winkelwagentje wordt toegevoegd, ontstaan er twee aparte items in het winkelwagentje

De ACSD-56447-patch verhelpt het probleem dat het toevoegen van hetzelfde product aan het winkelwagentje via parallelle REST API-aanvragen leidt tot twee afzonderlijke items in het winkelwagentje. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 wordt geïnstalleerd. De patch-id is ACSD-56447. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u hetzelfde product via een parallel web REST API-verzoek aan het winkelwagentje toevoegt, resulteert dit in twee aparte items in het winkelwagentje.

<u> Stappen om </u> te reproduceren:

1. Genereer een klanttoken voor het aanvragen van de REST API-aanroepen met [!DNL Postman] .
1. Maak een winkelwagentje voor de klant.
1. Gebruik het hierboven gegenereerde token om een lege winkelwagen voor de klant te maken.
1. Gebruik CURL om twee `AddProductsToCart` -verzoeken tegelijk uit te voeren. Volg de instructies in het [&#x200B; verwerkingsleerprogramma van de Orde &#x200B;](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) in de ontwikkelaarsdocumentatie.

<u> Verwachte resultaten </u>:

Items met meerdere hoeveelheden worden op één regel weergegeven.

<u> Ware resultaten </u>:

Dezelfde SKU&#39;s worden weergegeven in meerdere regelitems.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
