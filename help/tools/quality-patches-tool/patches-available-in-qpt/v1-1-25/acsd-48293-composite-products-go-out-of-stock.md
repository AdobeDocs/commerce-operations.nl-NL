---
title: 'ACSD-48293: samengestelde producten uit voorraad bij de verkoop van in voorraad zijnde kinderproducten'
description: Pas de ACSD-48293-patch toe om het Adobe Commerce-probleem op te lossen waarbij de samengestelde producten uit voorraad verdwijnen wanneer de verkochte onderliggende producten naar voorraad worden teruggestuurd.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 2aa75e97-373e-4e4a-a545-69bce807ca4d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48293: samengestelde producten uit voorraad bij de verkoop van in voorraad zijnde kinderproducten

De ACSD-48293-patch verhelpt het probleem waar de samengestelde producten uit voorraad verdwijnen wanneer de uitverkochte kinderproducten naar voorraad worden teruggestuurd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-48293. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Samengestelde producten gaan uit voorraad wanneer de uitgekozen kinderproducten naar voorraad worden teruggebracht.

<u> Stappen om </u> te reproduceren:

1. Maak een secundaire website, sla deze op en sla de weergave op.
1. Maak twee bronnen en voorraden en wijs deze toe aan elke website.
1. Schakel de optie voor het weergeven van producten buiten de voorraad in onder **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]* .
1. Maak een configureerbaar product met één gekoppeld product met behulp van de voorraadbron van de primaire website (set qty = 1).
1. Plaats een orde voor het configureerbare product.
1. Voer de uitsnede uit.
1. Open het configureerbare product vanuit de winkel en bevestig dat het uit voorraad is.
1. Open het configureerbare product vanuit de [!UICONTROL Admin] en stel de **[!UICONTROL Manage Stock Option]** in op *[!UICONTROL No]* .
1. Voer de uitsnede uit.
1. Verplaats de bestelling en voeg hoeveelheid toe aan het eenvoudige product dat de bestelling in voorraad maakt.
1. Voer de uitsnede uit.
1. Controleer de beschikbaarheid van het product op de winkel.

<u> Verwachte resultaten </u>:

Het configureerbare product is in voorraad.

<u> Ware resultaten </u>:

Het configureerbare product is uit voorraad.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
