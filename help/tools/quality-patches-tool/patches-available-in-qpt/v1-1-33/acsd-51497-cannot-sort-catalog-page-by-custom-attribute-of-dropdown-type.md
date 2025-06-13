---
title: 'ACSD-51497: Kan cataloguspagina niet sorteren op aangepast kenmerk van het type Dropdown'
description: Pas de ACSD-51497-patch toe om het Adobe Commerce-probleem op te lossen waarbij een klant een cataloguspagina niet kan sorteren op aangepast kenmerk van het type Dropdown.
feature: Attributes, Cache, Catalog Management, Categories
role: Developer
exl-id: c66a7e04-fd2a-47be-8f7a-7982780a5414
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-51497: Kan cataloguspagina niet sorteren door douanekenmerken van type *Dropdown*

ACSD-51497 herstelt de flard de kwestie waar een klant geen cataloguspagina door een douanekenmerk van het type *Dropdown* kan sorteren. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 wordt geïnstalleerd. De patch-id is ACSD-51497. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een klant kan een cataloguspagina niet sorteren door een douanekenmerk van het type *Dropdown*.

<u> Stappen om te reproduceren </u>

1. Maak ongeveer zes eenvoudige producten en wijs deze toe aan één categorie.
1. Maak een productkenmerk om het als sorteeroptie toe te voegen aan de aanbiedingspagina&#39;s.

   * Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Add New Attribute]** .
   * Stel op het tabblad **[!UICONTROL Properties]** het volgende in:

      * *[!UICONTROL Default Label]* = *test*
      * *[!UICONTROL Catalog Input Type]* voor de Eigenaar van de Opslag = *Dropdown*
      * *[!UICONTROL Options]*:

         * *eerst*
         * *tweede*
         * *derde*
         * *vierde*

   * Stel op het tabblad **[!UICONTROL Storefront Properties]** het volgende in:

      * *[!UICONTROL Used for sorting in product listing]* = *ja*
      * Verlaat alle andere opties als *Gebrek*.

1. Wijs het *test* attribuut aan *Standaard* attributen toe die in **[!UICONTROL Admin]** worden geplaatst > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Vorm de producten om *test* attributenwaarden te hebben.

   * SKU: s00001, test: vierde
   * SKU: s00002, test: derde
   * SKU: s00003, test: tweede
   * SKU: s00004, test: eerste
   * SKU: s00005, test: vierde
   * SKU: s00006, test: derde

1. Cache opnieuw indexeren en wissen.
1. Ga naar de categorie op de winkelpagina.
1. De soort door het *test* attribuut.

<u> Verwachte resultaten </u>:

De producten worden gesorteerd door het *test* attribuut.

<u> Ware resultaten </u>:

De producten worden niet gesorteerd door het *test* attribuut.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
