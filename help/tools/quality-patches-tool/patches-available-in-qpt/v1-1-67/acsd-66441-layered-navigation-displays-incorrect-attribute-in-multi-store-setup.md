---
title: 'ACSD-66441: De gelaagde Navigatie toont onjuiste attributenopties in multi-store opstelling'
description: Pas de ACSD-66441-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij de kenmerken van andere winkels in een multi-store-instelling onjuist worden weergegeven door gelaagde navigatie.
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
exl-id: d61c6b9e-bbcf-4285-b97b-b1fee67048e5
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-66441: De gelaagde Navigatie toont onjuiste attributenopties in multi-store opstelling

De ACSD-66441-patch verhelpt het probleem waarbij gelaagde navigatie de kenmerken van andere winkels verkeerd weergeeft in een multi-store installatie. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 wordt geïnstalleerd. De patch-id is ACSD-66441. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gelaagde Navigatie op de opslagplaats omvat attributenwaarden van andere opslag, zelfs wanneer die producten niet beschikbaar in de huidige archiefmening zijn.

<u> Stappen om </u> te reproduceren:

1. Maak een secundaire website, sla deze op en sla de weergave op.
1. Maak een configureerbaar product met een aangepast kenmerk (bijvoorbeeld grootte).
1. Wijs het configureerbare product toe aan de hoofdwebsite en een categorie.
1. Alle gegevens opnieuw indexeren.
1. Navigeer naar de toegewezen categorie in de winkelbrowser. De opties voor alle formaten worden correct weergegeven in Gelaagde navigatie.
1. U kunt twee eenvoudige producten van de hoofdwebsite verwijderen en deze aan de secundaire website toewijzen of van de hoofdwebsite verwijderen.
1. Alle gegevens opnieuw indexeren.
1. Reviseer de pagina met de opslagcategorie en controleer de gelaagde navigatie.

<u> Verwachte resultaten </u>:

In gelaagde navigatie worden alleen kenmerkopties weergegeven van producten die zijn toegewezen aan de huidige winkel of website.

<u> Ware resultaten </u>:

De gelaagde Navigatie toont attribuutopties (grootte) van producten die aan andere opslag of websites worden toegewezen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
