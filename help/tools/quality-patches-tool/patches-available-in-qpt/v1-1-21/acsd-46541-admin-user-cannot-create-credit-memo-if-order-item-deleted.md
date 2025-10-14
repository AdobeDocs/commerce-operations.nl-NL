---
title: 'ACSD-46541: Een beheerder kan geen creditmemo maken als een orderitem wordt verwijderd'
description: Pas de ACSD-46541-patch toe om het Adobe Commerce-probleem op te lossen. Als een product eenmaal is verwijderd, kunt u geen creditmemo maken in Adobe Commerce Admin.
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: c46ee888-92b1-4798-bd2b-1a082fd1406a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-46541: Een beheerder kan geen creditmemo maken als een orderitem wordt verwijderd

De ACSD-46541-patch verhelpt het probleem waarbij een beheerder geen creditmemo kan maken als een orderitem wordt verwijderd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 wordt geïnstalleerd. De patch-id is ACSD-46541. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als een product eenmaal is verwijderd, kunt u geen creditcard meer maken in Commerce Admin.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de Commerce-beheerder.
1. Maak een bestelling.
1. Factuur de bestelling.
1. Verwijder het product uit de bestelling.
1. Klik op de koppeling **[!UICONTROL Credit Memo]** op de pagina Bewerken van de bestelling.
1. Klik op **[!UICONTROL Refund Offline]** om een creditnota te maken.

<u> Verwachte resultaten </u>:

Er is een creditmemo gemaakt.

<u> Ware resultaten </u>:

De _volgende producten met gevraagde SKUs werden niet gevonden: SKU001_ foutenvertoningen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
