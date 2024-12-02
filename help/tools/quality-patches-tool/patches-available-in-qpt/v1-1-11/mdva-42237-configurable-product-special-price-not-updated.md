---
title: 'MDVA-42237: configureerbare speciale prijs van het product niet bijgewerkt'
description: De MDVA-42237-patch verhelpt het probleem waarbij de speciale prijs van het configureerbare product niet wordt bijgewerkt na wijzigingen in de prijs van het subproduct. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 is geïnstalleerd. De patch-id is MDVA-42237. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Admin Workspace, Configuration, Orders, Personalization, Products
role: Admin
exl-id: 1bae9a14-d6c1-4ee3-85aa-5d80ef479385
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-42237: configureerbare speciale prijs van het product niet bijgewerkt

De MDVA-42237-patch verhelpt het probleem waarbij de speciale prijs van het configureerbare product niet wordt bijgewerkt na wijzigingen in de prijs van het subproduct. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11 geïnstalleerd is. De patch-id is MDVA-42237. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De speciale prijs van het configureerbare product wordt niet bijgewerkt na wijzigingen in de prijs van het subproduct.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Admin** > **Systeem** > **Indexbeheer** en plaats **Wijze van de Index** aan **Update door Programma** voor alle indexen.
1. Maak een configureerbaar product met één eenvoudig product en stel een speciale prijs in voor het subproduct.
1. Controleer of de speciale prijs wordt weergegeven in de Storefront.
1. Verwijder de speciale prijs met GraphQL en controleer de productprijs op de winkelserver.

<u> Verwachte resultaten </u>:

De speciale prijs wordt niet meer weergegeven in de winkelruimte.

<u> Ware resultaten </u>:

De prijs wordt niet bijgewerkt in de winkel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
