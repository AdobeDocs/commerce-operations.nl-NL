---
title: 'ACSD-54106: Turks geaccentueerde tekensortering corrigeren in productcategorie'
description: Pas de ACSD-54106-patch toe om het Adobe Commerce-probleem op te lossen waarbij de sortering van categorieproducten op naam voor tekens met accent in het Turks onjuist is.
feature: Categories, Products, Search
role: Admin
exl-id: 45c8efbb-85d0-4d25-9d7e-9c41a97e80fa
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-54106: Turks geaccentueerde tekensortering corrigeren in productcategorie

De ACSD-54106-patch verhelpt het probleem waarbij de sortering van categorieproducten op naam voor tekens met accent in het Turks onjuist is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.39 wordt geïnstalleerd. De patch-id is ACSD-54106. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het sorteren van producten binnen categorieën op naam is onjuist voor tekens met accent in het Turks.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij het deelvenster Beheer.
1. Maak eenvoudige producten met de volgende naam en wijs deze aan elke gewenste categorie toe:

* Naam A
* Naam Rock
* Naam D
* Naam
* Naam M
* Naam Ö
* Naam Ü
* Naam Y
* Naam Z

1. Navigeer naar de winkel en open de categorie die de producten bevat.
1. Wijzig de sorteervolgorde in *[!UICONTROL By Name]* .

<u> Verwachte resultaten </u>:

De producten worden correct gesorteerd in de volgende orde:

* Naam A
* Naam Rock
* Naam D
* Naam
* Naam M
* Naam Ö
* Naam Ü
* Naam Y
* Naam Z

<u> Ware resultaten </u>:

De producten worden verkeerd gesorteerd in de volgende orde:

* Naam A
* Naam D
* Naam M
* Naam Y
* Naam Z
* Naam Rock
* Naam Ö
* Naam Ü
* Naam

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
