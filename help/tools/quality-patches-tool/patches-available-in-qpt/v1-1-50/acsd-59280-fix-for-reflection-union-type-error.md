---
title: 'ACSD-59280: Fout "RefCollectionUnionType::getName()" in 2.4.4-pX-installaties'
description: Pas de ACSD-59280-patch toe om het Adobe Commerce-probleem te verhelpen waarbij de fout 'call to undefined method RefCollectionUnionType::getName()' optreedt tijdens de installatie van 2.4.4-pX-versies.
feature: Install, Upgrade
role: Admin, Developer
exl-id: 5a47dad4-4490-4e3d-93f2-9b176fb144d9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# ACSD-59280: `ReflectionUnionType::getName()` fout in 2.4.4-pX-installaties

De ACSD-59280-patch verhelpt het probleem waarbij de `call to undefined method ReflectionUnionType::getName()` -fout optreedt tijdens de installatie van 2.4.4-pX-versies. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-59280. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`ReflectionUnionType::getName()` fout tijdens installatie 2.4.4-pX.

<u> Stappen om </u> te reproduceren:

Voer een nieuwe installatie uit met *[!UICONTROL Composer]* .

<u> Verwachte resultaten </u>:

Het installatieproces wordt zonder fouten voltooid.

<u> Ware resultaten </u>:

De volgende fout wordt tijdens het `setup:upgrade` -proces weergegeven:

`Call to undefined method ReflectionUnionType::getName()`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
