---
title: 'ACSD-50814: Admin-gebruiker kan geen creditmemo maken'
description: Pas de ACSD-50814-patch toe om het Adobe Commerce-probleem op te lossen waarbij een beheerder geen creditmemo kan maken.
feature: Admin Workspace, Orders, Returns
role: Admin
exl-id: 87ee7166-7492-4948-9a85-a183ecf54fa7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-50814: Admin-gebruiker kan geen creditmemo maken

De ACSD-50814-patch verhelpt het probleem waarbij een beheerder geen creditmemo kan maken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-50814. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een beheerder kan geen creditnota maken.

<u> Stappen om </u> te reproduceren:

1. Navigeer in Adobe Commerce Admin naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Shipping methods]** > **[!UICONTROL Free shipping]** en stel **[!UICONTROL Enable free shipping]** in op *[!UICONTROL Yes]*
1. Ga nogmaals naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** , vouw de berekeningsinstellingen uit en stel deze in:
   * [!UICONTROL Shipping prices] = [!UICONTROL Including tax]
   * [!UICONTROL Enable cross border trade] = [!UICONTROL No]
1. Vouw de weergave-instellingen voor prijzen uit en stel [!UICONTROL Display shipping prices] = [!UICONTROL Including tax] in.
1. Vouw de weergave-instellingen [!UICONTROL Orders] , [!UICONTROL Invoices] , [!UICONTROL Credit memo] uit en stel [!UICONTROL Display shipping amount] = [!UICONTROL Including tax] in.
1. caches wissen.
1. Plaats een bestelling op de winkel.
1. Maak een factuur voor de bestelling in de beheerder.
1. Maak een creditmemo.

<u> Verwachte resultaten </u>:

De creditmemo wordt gemaakt.

<u> Ware resultaten </u>:

De volgende fout wordt gegenereerd:

*de pagina kan niet wegens de fout* worden getoond

```
report.CRITICAL: DivisionByZeroError: Division by zero in vendor/magento/module-sales/Model/Order/Creditmemo/Total/Tax.php:139*
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
