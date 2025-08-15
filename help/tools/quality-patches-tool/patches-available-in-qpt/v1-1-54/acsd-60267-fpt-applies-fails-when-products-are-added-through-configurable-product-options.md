---
title: 'ACSD-60267: FPT is onjuist van toepassing wanneer producten via configureerbare productopties worden toegevoegd'
description: Pas de ACSD-60267-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de vaste productbelasting (FPT) correct wordt toegepast wanneer u eenvoudige producten rechtstreeks aan het winkelwagentje toevoegt, maar mislukt wanneer u dezelfde producten selecteert via configureerbare productopties.
feature: Taxes
role: Admin, Developer
exl-id: 919b3b96-1995-4faf-aaf1-b5cbb20e46bf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267: FPT is onjuist van toepassing wanneer producten via configureerbare productopties worden toegevoegd

De ACSD-60267-patch verhelpt het probleem dat de vaste productbelasting (FPT) correct wordt toegepast wanneer eenvoudige producten rechtstreeks aan het winkelwagentje worden toegevoegd, maar mislukt wanneer dezelfde producten via configureerbare productopties worden geselecteerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.54 wordt geïnstalleerd. De patch-id is ACSD-60267. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De Vaste Belasting van het Product (FPT) werkt behoorlijk wanneer de eenvoudige producten met FPT aan de kar worden toegevoegd, maar FPT wordt niet toegevoegd wanneer de producten via configureerbare productselectie worden toegevoegd.

<u> Stappen om </u> te reproduceren:

1. Plaats *[!UICONTROL Enable FPT]* aan *ja* door aan *Admin* te navigeren > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > **[!UICONTROL Fixed Product Taxes]**.
1. Maak een FPT-kenmerk en wijs dit toe aan een *[!UICONTROL Attribute Set]* .
1. Open **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** .
1. Voer bij *[!UICONTROL Default Label]* een label in dat het kenmerk identificeert.
1. Stel *[!UICONTROL Catalog Input for Store Owner]* in op *[!UICONTROL Fixed Product Tax]* .
1. Maak een nieuwe belasting en zone en wijs deze toe aan een nieuwe *[!UICONTROL Tax Rule]* .
1. Maak een configureerbaar product met twee eenvoudige producten.
1. Wijs nu twee verschillende waarden FPT aan die eenvoudige producten toe.
1. De prijzen opnieuw indexeren en controleren op de winkel.
1. Voeg de producten toe aan het winkelwagentje en controleer de subtotalen.

<u> Verwachte resultaten </u>:

* Op de pagina *[!UICONTROL Catalog]* worden prijzen weergegeven, inclusief FPT.
* Subtotalen in het winkelwagentje zijn inclusief FPT.

<u> Ware resultaten </u>:

* Op de pagina *[!UICONTROL Catalog]* worden de prijzen niet weergegeven, inclusief de FPT-waarde.
* Subtotalen en samenvatting zijn ongeldig.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
