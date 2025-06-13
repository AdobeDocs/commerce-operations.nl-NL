---
title: 'ACSD-56023: Widget-inhoud wordt niet bijgewerkt op de CMS-pagina'
description: Pas de ACSD-56023-patch toe om het Adobe Commerce-probleem op te lossen waarbij de widgetinhoud niet wordt bijgewerkt op de CMS-pagina
feature: CMS
role: Admin, Developer
exl-id: 723b7f64-ed8a-45f9-9151-f99169cd1a04
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56023: Widget-inhoud wordt niet bijgewerkt op de CMS-pagina

De ACSD-56023-patch verhelpt het probleem waarbij de widgetinhoud niet wordt bijgewerkt op de CMS-pagina. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-56023. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Widget-inhoud wordt niet bijgewerkt op de CMS-pagina.

<u> Stappen om </u> te reproduceren:

1. Maak een paar producten.
1. Maak de nieuwe CMS-pagina en voeg een nieuwe widget producten toe aan de inhoud:

   ```
      {{widget type="Magento\Catalog\Block\Product\Widget\NewWidget" display_type="new_products" show_pager="1" products_per_page="5" products_count="10" template="product/widget/new/content/new_grid.phtml" page_var_name="pnetpm"}} 
   ```

1. Open de gemaakte pagina in de winkel. Zorg ervoor dat u de sjabloon in de cache plaatst.
1. Open vanuit Beheer **[!UICONTROL Catalog]** > **[!UICONTROL Products]** .
1. Kies om het even welk product voor uitgeven en schakelaar **[!UICONTROL Set Product as New]** aan *ja*.
1. Ga opnieuw naar de gecreeerde *pagina van CMS* op de storefront.

<u> Verwachte resultaten </u>:

De pagina bevat *Nieuwe widget van Producten* met de producten.

<u> Ware resultaten </u>:

De pagina bevat *geen Nieuwe widget van Producten*, en de nieuwe producten verschijnen niet.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
