---
title: 'ACSD-61348: items op de ishlist die zichtbaar zijn via GraphQL, maar niet op de winkel'
description: Pas de ACSD-61348-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de wenslijstonderdelen zichtbaar zijn via GraphQL, maar niet op de winkel in een omgeving met meerdere websites.
feature: Customers
role: Admin, Developer
exl-id: fcba2c28-077d-4663-b129-7da436e2791d
source-git-commit: c1d3d3056d1ee3c33db6c14ed10a1df08f962795
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-61348: items op de ishlist die zichtbaar zijn via GraphQL, maar niet op de winkel

De ACSD-61348-patch verhelpt het probleem waarbij de wenslijstonderdelen zichtbaar zijn via GraphQL, maar niet op de winkel in een omgeving met meerdere websites. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-61348. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6-p5

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De items van de ishlist zijn zichtbaar via GraphQL, maar niet op de winkel in een omgeving met meerdere websites.

<u> Stappen om </u> te reproduceren:

1. Configureer twee websites.
1. Ga naar **[!UICONTROL Config Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** en stel **[!UICONTROL Share Customer Accounts]** in op *[!UICONTROL Global]* .
1. Ga naar **[!UICONTROL Config Customers]** > **[!UICONTROL Wishlist]** > **[!UICONTROL General Options]** en plaats **[!UICONTROL Enable Multiple Wish Lists]** aan *ja*.
1. Ga naar **[!UICONTROL Config General]** > **[!UICONTROL Web]** en reeks **[!UICONTROL Add Store Code to URLs]** aan *ja*.
1. Maak een eenvoudig product en wijs dit toe aan de tweede website.
1. Maak een klant en meld u aan.
1. Voeg een product toe aan de verlanglijst.
1. Wijs het product toe aan de standaardwebsite.
1. Ga naar de pagina *[!UICONTROL Wishlist]* op de standaardwebsite.

<u> Verwachte resultaten </u>:

Het product staat op de verlanglijst.

<u> Ware resultaten </u>:

Er staan geen producten op de verlanglijst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
