---
title: 'ACSD-48059: handelaren kunnen [!UICONTROL Match product by rule] niet opslaan voor het kenmerk Categorieën.'
description: Pas de ACSD-48059-patch toe om het Adobe Commerce-probleem op te lossen, waarbij handelaren het [!UICONTROL Match product by rule] voor het kenmerk Categorieën niet kunnen opslaan.
feature: Admin Workspace, Attributes, Categories, Products
role: Admin
exl-id: e156a752-81b3-4404-81e2-af7ed29f2b1d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-48059: Merchants kunnen de *[!UICONTROL Match product by rule]* voor het categoriekenmerk niet opslaan

De ACSD-48059-patch verhelpt het probleem waarbij handelaren *[!UICONTROL Match product by rule]* voor het categoriekenmerk in [!DNL Visual Merchandiser] niet kunnen opslaan. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 wordt geïnstalleerd. De patch-id is ACSD-48059. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) >=2.3.7 &lt;2.4.7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Handelaars kunnen het kenmerk *[!UICONTROL Match product by rule]* for category niet opslaan in [!DNL Visual Merchandiser] .

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Visual Merchandiser]** > **[!UICONTROL Visible Attributes for Category Rules]** en voeg categorieën toe.
1. Ga naar Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** .
   * Ga naar de sectie [!UICONTROL Products in Category] .
   * Voeg een nieuwe voorwaarde *[!UICONTROL Match products by rule]* met het categoriekenmerk toe.

<u> Verwachte resultaten </u>:

De categorie is opgeslagen.

<u> Ware resultaten </u>:

* U kunt de categorie niet opslaan met de nieuwe regel en voorwaarde.
* *ging het iets verkeerd terwijl het bewaren van de categorie* fout wordt getoond.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
