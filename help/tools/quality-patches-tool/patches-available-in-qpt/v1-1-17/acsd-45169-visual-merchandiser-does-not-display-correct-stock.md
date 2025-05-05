---
title: 'ACSD-45169: Visuele Merchandiser toont onjuiste voorraad en prijs voor configureerbaar product'
description: De ACSD-45169 flard moeilijke situatie waar Visuele Merchandiser niet de correcte voorraad en de prijs voor een configureerbaar product na een het opvoeren update wordt toegepast toont. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 is geïnstalleerd. De patch-id is ACSD-45169. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Categories, Configuration, Merchandising, Orders, Products
role: Admin
exl-id: 3f1218ee-2fd0-4f3e-80d7-7e6f9342e0fb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-45169: Visuele Merchandiser toont onjuiste voorraad en prijs voor configureerbaar product

De ACSD-45169 flard moeilijke situatie waar Visuele Merchandiser niet de correcte voorraad en de prijs voor een configureerbaar product na een het opvoeren update wordt toegepast toont. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 geïnstalleerd is. De patch-id is ACSD-45169. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Visuele Merchandiser toont niet de correcte voorraad en de prijs voor een configureerbaar product nadat een het opvoeren update wordt toegepast.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Maak een geplande update voor het eenvoudige product (u hebt alleen andere rij- en entiteitsgegevens nodig).
1. Maak een configureerbaar product.
1. Wijs het configureerbare product aan een categorie toe.
1. Open de categorie en bekijk het configureerbare product onder de sectie Visuele Merchandiser.

<u> Verwachte resultaten </u>:

Visuele Merchandiser toont de correcte voorraad en de prijs.

<u> Ware resultaten </u>:

Visual Merchandiser toont een onjuiste voorraad en een prijs.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
