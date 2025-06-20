---
title: 'ACSD-64732: controllers van derden worden niet correct in cache geplaatst met klantsegmenten'
description: Pas de ACSD-64732-patch toe om het Adobe Commerce-probleem op te lossen, waarbij controllers van derden niet correct in de cache worden geplaatst met klantsegmenten.
feature: Cache
role: Admin, Developer
exl-id: 378e5a96-06dd-4796-9e45-a67cf539fcce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-64732: controllers van derden worden niet correct in cache geplaatst met klantsegmenten

De ACSD-64732-patch verhelpt het probleem waarbij de controllers van derden niet correct in de cache worden geplaatst met klantsegmenten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 wordt geïnstalleerd. De patch-id is ACSD-64732. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De controlemechanismen van de derde worden niet correct in het voorgeheugen ondergebracht met klantensegmenten.

<u> Stappen om </u> te reproduceren:

1. Ga naar de aangepaste controller (catalogus/categorie/variatie).
1. Ga naar het tabblad **[!UICONTROL Network]** en controleer de waarde van **[!DNL X-Magento-Vary]** .

<u> Verwachte resultaten </u>:

De waarde **[!UICONTROL X-Magento-Vary]** moet hetzelfde zijn op de aangepaste controller.

<u> Ware resultaten </u>:

De waarde van **[!UICONTROL X-Magento-Vary]** is anders, wat cachevervallen veroorzaakt. Dit betekent het eerder geproduceerde geheime voorgeheugen kan niet worden gebruikt wanneer het bezoeken van het douanecontroller.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce on cloud Infrastructure: Upgrades and Patches > Apply Patches in the Commerce on Cloud Infrastructure guide.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
