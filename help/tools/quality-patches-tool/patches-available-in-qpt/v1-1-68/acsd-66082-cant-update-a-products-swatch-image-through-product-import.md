---
title: 'ACSD-66082: kan de staalafbeelding van een product niet bijwerken via het importeren van producten'
description: Pas de ACSD-66082-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het uploaden van een CSV-bestand met het veld swatch_image ingesteld op EMPTY_VALUE naar ongeordende staalafbeeldingen ertoe leidt dat het importproces mislukt.
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 0bfff90e-5f1f-4c87-8a99-efc5bb0d814b
source-git-commit: e0d2e42b070591f3fefc0e9adb1bf5c1ba580fd9
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-66082: kan de staalafbeelding van een product niet bijwerken via het importeren van producten

De ACSD-66082-patch verhelpt het probleem dat het niet mogelijk was om de staalafbeelding van een product bij te werken via het importeren van producten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-66082. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een CSV-bestand uploadt terwijl het veld `swatch_image` is ingesteld op `EMPTY_VALUE` om de set staalafbeeldingen te verwijderen, treedt er een fout op tijdens het importeren.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** . Klik op de pijl-omlaag naast de knop **[!UICONTROL Add Product]** en kies **[!UICONTROL Simple Product]** . Plaats zijn **[!UICONTROL SKU]** aan *ABC*.
1. Upload een beeld PNG genoemd *testing.png* aan `var/import/images/`.
1. Maak een CSV-bestand met de volgende inhoud:

   ```
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Import]** om het bestand te importeren door de volgende instellingen aan te passen:
   * **[!UICONTROL Entity type]**: *Producten*
   * **[!UICONTROL Import Behavior]**: *toevoegen/bijwerken*
   * Klik op **[!UICONTROL Choose File]** om het CSV-bestand te selecteren dat in de vorige stap is gemaakt en dat u wilt importeren. Het importeren is voltooid en het staal wordt toegevoegd.
1. De CSV bijwerken met de volgende inhoud:

   ```
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. Herhaal het importproces.

<u> Verwachte resultaten </u>:

De staalafbeelding is niet ingesteld.

<u> Ware resultaten </u>:

Tijdens het importeren treedt een fout op.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
