---
title: 'ACSD-51114: Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld'
description: Pas het ACSD-51114-patch toe om de Adobe Commerce-uitgave te corrigeren. Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld.
feature: Catalog Management, Categories, Products
role: Admin
exl-id: ab1816ef-fb09-46e7-8102-32865f806874
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51114: Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld

>[!NOTE]
>
>Deze patch is vervangen.

De markering ACSD-51114 verhelpt de producten van de kwestie Willekeurige verdwenen uit grote catalogi wanneer het asynchrone indexeren wordt toegelaten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-5114. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool]:Search pagina met patches].Gebruik de patch-id als een zoektrefwoord om de patch te zoeken.

## Probleem

Willekeurige producten verdwijnen uit grote catalogi wanneer asynchrone indexering is ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Maak een set van 10 producten.
1. Stel alle indexen in op de modus **[!UICONTROL Update on Save]** .
1. Maak een categorie en wijs er alle producten aan toe.
1. Alle producten uitschakelen.
1. Open de categorie en controleer of er geen producten zijn.
1. Stel alle indexen in op de modus **[!UICONTROL Update on Schedule]** .
1. Stel de `DEFAULT_BATCH_SIZE` in op 2 in `lib/internal/Magento/Framework/Mview/View.php#L31` .
1. Laat producten in de volgende orde toe: 1st, 9th, 2nd, 5th, 10th, 3rd.
1. Uitsnijden uitvoeren, opdracht.
1. Open de rubriek opnieuw.

<u> Verwachte resultaten </u>:

Alle ingeschakelde producten worden weergegeven.

<u> Ware resultaten </u>:

Alle toegelaten producten worden niet getoond.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
