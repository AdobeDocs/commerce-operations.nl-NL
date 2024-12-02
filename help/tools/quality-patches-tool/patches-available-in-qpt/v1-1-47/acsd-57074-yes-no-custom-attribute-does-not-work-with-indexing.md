---
title: 'ACSD-57074: *Yes/No*, aangepast kenmerk met prefix ` price_*` in ` attribute_code` kenmerk werkt niet met indexeren'
description: Pas het ACSD-57074 flard toe om de kwestie van Adobe Commerce te bevestigen waar het *Yes/No* douanekenmerk met ` price_* ` prefix in ` attribuut_code ` niet met indexeren werkt.
feature: Products, Categories, Catalog Management
role: Admin, Developer
exl-id: 718b8f2d-4d3d-4755-8a91-5c2f97114813
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-57074: *ja/neen* douaneattribuut met `price_*` prefix in `attribute_code` attributen werkt niet met het indexeren

Het ACSD-57074 flard lost de kwestie op waar *ja/Nr* douaneattribuut met `price_*` prefix in het `attribute_code` attribuut niet met het indexeren werkt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.47 wordt geïnstalleerd. De patch-id is ACSD-57074. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

*ja/Nr* douaneattribuut met `price_*` prefix in het `attribute_code` attribuut werkt niet met het indexeren.

<u> Stappen om </u> te reproduceren:

1. Maak een aangepast productkenmerk met de volgende opties:
   * *[!UICONTROL Catalog Input Type]*: *ja/Nr*
   * *[!UICONTROL Scope]*: *StoreView*
   * *[!UICONTROL Use in Search]*: *ja*
1. Wijs het kenmerk toe aan de standaardkenmerkset.
1. Maak een product met het kenmerk dat we hebben gemaakt.
1. Wijs het product dat we zojuist hebben gemaakt toe aan een categorie.
1. Voer de volledige redex uit.

<u> Verwachte resultaten </u>:

Het product wordt weergegeven in de toegewezen categorie.

<u> Ware resultaten </u>:

Het product staat niet op de voorpagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
