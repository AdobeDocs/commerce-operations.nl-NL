---
title: 'MDVA-41139: configureerbaar product komt uit voorraad na import van product'
description: De MDVA-41139-patch verhelpt het probleem waarbij het configureerbare product na het importeren van het product uit voorraad raakt wanneer het eenvoudige product qty = 0 voor een van de bronnen is. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 is geïnstalleerd. De patch-id is MDVA-41139. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
exl-id: 7366230c-3b7f-4211-9f0d-55a528dffdbd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41139: configureerbaar product komt uit voorraad na import van product

De MDVA-41139-patch verhelpt het probleem waarbij het configureerbare product na het importeren van het product uit voorraad raakt wanneer het eenvoudige product qty = 0 voor een van de bronnen is. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8 geïnstalleerd is. De patch-id is MDVA-41139. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het configureerbare product wordt uit voorraad na het importeren van het product wanneer het eenvoudige productaantal = 0 voor een van de bronnen.

<u> Eerste vereisten </u>:

De inventarismodules worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe bron en voorraad.
1. Creeer een configureerbaar product met kindproducten die aan de standaardbron en de nieuwe bron worden toegewezen.
1. Stel de waarde in van de standaardvoorraad voor elk onderliggende product = 0 en voor andere voorraad > 0.
1. Het configureerbare product is in voorraad.
1. Exporteer dit product en importeer het opnieuw.

<u> Verwachte resultaten </u>:

Het configureerbare product is in voorraad aangezien de tweede bron hoeveelheid > 0 heeft.

<u> Ware resultaten </u>:

Het configureerbare product is uit voorraad.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
