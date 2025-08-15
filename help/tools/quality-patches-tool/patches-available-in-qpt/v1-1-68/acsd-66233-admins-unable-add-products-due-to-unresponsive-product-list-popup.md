---
title: 'ACSD-66233: Admins cannot add products due to unresponsive product list popup'
description: Pas de ACSD-66233-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij beheerders geen producten aan categorieën kunnen toevoegen omdat [!UICONTROL Add Product] popup in Visual Merchandiser oneindig wordt geladen.
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
exl-id: 2e01e62d-b6f9-4aa5-9040-7908aa83d422
source-git-commit: a1241f709fc1b7128d1d267c54586c60dadab436
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-66233: Admins die geen producten kunnen toevoegen omdat de productlijst niet reageert

De ACSD-66233-patch verhelpt een probleem waarbij beheerders geen producten aan categorieën kunnen toevoegen omdat [!UICONTROL Add Product] popup in Visual Merchandiser oneindig wordt geladen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-66233. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Probleem waarbij de pop-up [!UICONTROL Add Product] in Visual Merchandiser oneindig wordt geladen, zodat beheerders geen producten aan categorieën kunnen toevoegen.

<u> Stappen om </u> te reproduceren:

1. De inventarismodules installeren en inschakelen.
1. Maak een groot aantal inventarisbronnen (bijvoorbeeld 700).
1. Meerdere voorraden aanmaken (bijvoorbeeld 12) en de inventarisbronnen aan deze voorraden toewijzen.
1. Maak enkele producten en wijs deze toe aan de inventarisbronnen.
1. Maak een categorie.
1. Vouw de sectie [!UICONTROL Products in Category] uit.
1. Klik op [!UICONTROL Add Product] .
1. Bekijk het pop-upvenster met de lijst met producten.

<u> Verwachte resultaten </u>:

De productlijst wordt binnen een redelijke tijd in de pop-up geladen.

<u> Ware resultaten </u>:

De pop-up wordt voor onbepaalde tijd geladen en geeft de productlijst niet weer.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
