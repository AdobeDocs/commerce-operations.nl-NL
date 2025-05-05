---
title: 'ACSD-54007: Ongedefinieerde fout _scope met arraysleutel bij het importeren van klantgegevens'
description: Pas de ACSD-54007-patch toe om het Adobe Commerce-probleem op te lossen waarbij een Undefined array key_scope-fout wordt weergegeven bij het importeren van klantgegevens.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-54007: Ongedefinieerde fout _scope met arraysleutel bij het importeren van klantgegevens

Het ACSD-54007 flard bevestigt de kwestie waar er een *Onbepaalde serie zeer belangrijke _scope* fout bij het invoeren van klantengegevens is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-54007. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het invoeren van klantengegevens, ziet u een *Onbepaalde serie zeer belangrijke _scope* fout.

<u> Stappen om </u> te reproduceren:

1. Ga naar Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** en stel **[!UICONTROL Entity Type]** in op **[!UICONTROL Stock Sources]** en importeer het CSV-bestand van de stockbron (dat broncode, SKU, hoeveelheid en status bevat).
1. Kies Klanten en adressen (één bestand) en importeer het CSV-bestand, dat de adresgegevens van de klant bevat.

<u> Verwachte resultaten </u>:

Er treden geen fouten op.

<u> Ware resultaten </u>:

U krijgt de volgende fout: *Waarschuwing: Onbepaalde seriesleutel &quot;_scope&quot;in /var/www/html/vendor/magento/module-customer-import-export/Model/ResourceModel/Import/CustomerComposite/Data.php op lijn 84*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
