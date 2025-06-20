---
title: 'ACSD-53176: Productregel met &grave; is één van &grave; is voorwaarde één van &grave; niet aanpassen'
description: Pas de ACSD-53176-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de gerelateerde productregel 'één van' niet correct werkt voor 'Producten afstemmen'.
feature: Marketing Tools
role: Admin
exl-id: 8260c6ac-3ca2-4361-9e36-a8a58468fa95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-53176: productregel met `is one of` -voorwaarde komt niet overeen

ACSD-53176 flardfixes de kwestie waar de verwante productregel `is one of` voorwaarde niet correct voor **Producten werkt om** aan te passen. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.36 wordt geïnstalleerd. De patch-id is ACSD-53176. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De verwante productregel `is one of` voorwaarde werkt correct niet voor **Producten om** aan te passen.

<u> Stappen om </u> te reproduceren:

1. Maak 3-4 producten.
1. Maak een nieuwe regel voor verwante producten.

   Stel de regel in op twee of meer producten:
   * `SKU is one of "S1,S2".`

   Stel de regel in om twee of meer items weer te geven:
   * `Product SKU is one of constant value "S2,S3".`

1. Open het S1 product op de Storefront.

<u> Verwachte resultaten </u>:

De verwante producten &quot;S2&quot; en &quot;S3&quot; worden weergegeven op zowel productpagina&#39;s &quot;S1&quot; als &quot;S2&quot;.

<u> Ware resultaten </u>:

Verwante producten worden niet weergegeven op de productpagina&#39;s.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
