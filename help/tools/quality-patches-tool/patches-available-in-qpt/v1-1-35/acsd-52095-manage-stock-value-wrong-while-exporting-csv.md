---
title: 'ACSD-52095: De voorraadwaarde beheren is onjuist tijdens het exporteren van CSV'
description: Pas de ACSD-52095-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het product de voorraadwaarde beheert tijdens het exporteren van CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-52095: [!UICONTROL Manage Stock] -waarde is onjuist tijdens het exporteren van CSV

De ACSD-52095-patch verhelpt het probleem waarbij de `manage_stock` -waarde van het product onjuist is tijdens het exporteren van CSV. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-52095. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De waarde `manage_stock` wordt in het CSV-bestand na het exporteren ten onrechte op 0 ingesteld.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** en stel **[!UICONTROL Manage Stock]** = *[!UICONTROL No]* in.
1. Maak een nieuw product en sla dit op.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Export]** .
1. Selecteer *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* en exporteer de producten.
1. Controleer het gegenereerde CSV-bestand: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Ga nogmaals naar **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** en stel **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]* in.
1. Ga naar **Systeem** > **Uitvoer**.
Selecteer *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]* .
1. Controleer het gegenereerde CSV-bestand: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Open het product in Beheer, ga naar **[!UICONTROL Advanced Inventory]** en controleer de waarde **[!UICONTROL Manage Stock]** .

<u> Verwachte resultaten </u>

De **[!UICONTROL Manage Stock]** waarde is *1* wanneer het voor de producten wordt toegelaten.

<u> Ware resultaten </u>

De **[!UICONTROL Manage Stock]** waarde is *0* wanneer het voor de producten wordt toegelaten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] gids.
