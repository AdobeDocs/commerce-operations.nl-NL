---
title: 'ACSD-56616: Storefront-weergave van gebundelde producten bij een eenvoudig voorraadtekort'
description: Pas de ACSD-56616-patch toe om het Adobe Commerce-probleem op te lossen, waarbij gebundelde producten onverwachts in de winkel verschijnen wanneer alle bijbehorende eenvoudige producten uit voorraad zijn.
feature: Products
role: Admin, Developer
exl-id: 8b225d9d-1898-4c4d-81be-7b92cbf7d06f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-56616: Storefront-weergave van gebundelde producten bij een eenvoudig voorraadtekort.

De ACSD-56616-patch verhelpt het probleem waarbij gebundelde producten onverwachts in de winkel verschijnen wanneer alle bijbehorende eenvoudige producten uit voorraad zijn. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 wordt geïnstalleerd. De patch-id is ACSD-56616. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onjuiste storefront display van gebundelde producten tijdens eenvoudig voorraadtekort.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe website/winkel/winkel.
1. Maak een nieuwe bron.
1. Maak een nieuwe voorraad en wijs deze toe aan de nieuwe website.
1. Configureer indexen om op schema bij te werken.
1. Genereer twee eenvoudige producten, S1 (qty = 1) en S2 (qty = 1), en wijs deze toe aan het nieuwe bestand en de nieuwe website.
1. Creeer *gebundeld1* product en associeer het met nieuwe website, plaatsend het in categorie *KAT*.
1. Bepaal twee vereiste dropdown opties en verbind eenvoudig product *S1* aan option1 en *S2* aan option2.
1. Sla de producten op.
1. Navigeer aan **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** en laat *toe toevoegt opslagcode aan URL* = *ja*.
1. Open de winkel en koop het gebundelde product.
1. Draai twee keer om.
1. Keer terug naar de *KAT* categorie.

<u> Verwachte resultaten </u>:

Het *bundle1* product is uit voorraad.

<u> Ware resultaten </u>:

Het *bundle1* product is zichtbaar met prijs = *$0*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
