---
title: 'MDVA-37984: Visuele Merchandiser die niet correct werkt wanneer het opvoeren van updates wordt toegepast'
description: De flard MDVA-37984 lost de kwestie op waar de de "product van de Gelijke Merchandiser door regel"functionaliteit niet correct filtert wanneer de het opvoeren updates worden toegepast. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 is geïnstalleerd. De patch-id is MDVA-37984. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984: Visuele Merchandiser die niet correct werkt wanneer het opvoeren van updates wordt toegepast

De flard MDVA-37984 lost de kwestie op waar de de &quot;product van de Gelijke Merchandiser door regel&quot;functionaliteit niet correct filtert wanneer de het opvoeren updates worden toegepast. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 geïnstalleerd is. De patch-id is MDVA-37984. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De &quot;product van de Gelijke van de Merchandisator van Visual Merchandiser door regel&quot;functionaliteit filtert correct geen producten wanneer het opvoeren van updates worden toegepast.

<u> Stappen om </u> te reproduceren:

1. Een update voor een bestaand product maken.
   * Stel verschillende waarden in voor `entity_id` en `row_id` .
1. Maak een nieuw configureerbaar product en een eenvoudig product (het nieuwe product `entity_id` en `row_ids` zijn dus ook anders).
   * Om het makkelijker te maken om de kwestie te herhalen, plaats een merkbare kwaliteitswaarde voor het eenvoudige product - bijvoorbeeld 5000.
1. Ga naar een categorie > **Producten in categorie** en laat **Producten van de Gelijke door regel** toe.
1. Selecteer nu &quot;Quantity&quot; als kenmerk, &quot;Groter&quot; als operator en &quot;4500&quot; als waarde.
1. Klik **sparen**.

<u> Verwachte resultaten </u>:

Het nieuwe configureerbare product wordt vermeld.

<u> Ware resultaten </u>:

Het nieuwe configureerbare product wordt niet vermeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
