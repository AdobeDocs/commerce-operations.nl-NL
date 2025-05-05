---
title: 'ACSD-44851: Categorie met subcategorieën die niet kunnen worden geopend of uitgebreid'
description: Dit artikel biedt een oplossing voor het probleem waarbij de gebruiker een categorie met subcategorieën niet kan openen of uitbreiden.
feature: Categories
role: Admin
exl-id: c1ad13d8-94e1-47cf-ad65-9bc5ce1c26ad
source-git-commit: 33a9d54ce3e50df89b0455e4c1b2dfccb5bee32a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-44851: Categorie met subcategorieën die niet kunnen worden geopend of uitgebreid

De ACSD-44851-patch lost het probleem op waarbij de gebruiker een categorie met subcategorieën niet kan openen of uitbreiden. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 geïnstalleerd is. De patch-id is ACSD-44851. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebruiker kan een categorie met subcategorieën niet openen of uitbreiden.

<u> Stappen om </u> te reproduceren:

1. Maak in Adobe Commerce Admin een categoriestructuur met twee hoofdcategorieën en enkele subcategorieën voor elk hoofdknooppunt.
1. Open de mobiele weergave/emulator of maak de vensterbreedte kleiner totdat de lay-out mobiel wordt.
1. Open het hoofdmenu van de catalogus.
1. Probeer de hoofdcategorieën uit te vouwen.
1. Open de rubriek.

<u> Verwachte resultaten </u>:

Het menu is toegankelijk.

<u> Ware resultaten </u>:

Het tweede niveau van het mobiele menu wordt niet geopend.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Hulpmiddelen van het Patroon van de Kwaliteit > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de gids van het Hulpmiddel van het Patroon van de Kwaliteit.

* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
