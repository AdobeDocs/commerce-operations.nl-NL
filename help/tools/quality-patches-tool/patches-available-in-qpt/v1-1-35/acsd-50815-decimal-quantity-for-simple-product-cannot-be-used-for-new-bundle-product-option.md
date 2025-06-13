---
title: 'ACSD-50815: decimale hoeveelheid voor eenvoudig product kan niet worden gebruikt voor nieuwe gebundelde productoptie'
description: Pas de ACSD-50815-patch toe om het Adobe Commerce-probleem op te lossen waarbij de decimale hoeveelheid voor een eenvoudig product niet kan worden gebruikt voor een nieuwe gebundelde productoptie.
feature: Products
role: Admin
exl-id: 5cd69abe-bd88-497d-9696-804c787b73ef
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-50815: decimale hoeveelheid voor eenvoudig product kan niet worden gebruikt voor nieuwe gebundelde productoptie

De ACSD-50815-patch verhelpt de kwestie waarbij de decimale hoeveelheid voor een eenvoudig product niet kan worden gebruikt voor een nieuwe gebundelde productoptie. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-50815. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De decimale hoeveelheid voor een eenvoudig product kan niet worden gebruikt voor een nieuwe gebundelde productoptie.

<u> Stappen om </u> te reproduceren:

1. Meld u aan als beheerder.
1. Maak een nieuw eenvoudig product.
   * Stel in het **[!UICONTROL Advanced Inventory]** -venster [!UICONTROL Qty Uses Decimal] = [!UICONTROL Yes] in.
   * Sla het eenvoudige product op.
1. Maak een nieuw gebundeld product.
1. Voeg een willekeurige optie toe.
1. Voeg het eenvoudige product in deze optie toe.
1. Geef een decimale hoeveelheid voor het eenvoudige product op in de optie voor het gebundelde product. Bijvoorbeeld 1.5.

<u> Verwachte resultaten </u>:

Het is mogelijk decimale aantallen in te stellen. Er worden geen fouten weergegeven.

<u> Ware resultaten </u>:

De fout, *gelieve te gaan een geldig aantal op dit gebied* wordt getoond.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
