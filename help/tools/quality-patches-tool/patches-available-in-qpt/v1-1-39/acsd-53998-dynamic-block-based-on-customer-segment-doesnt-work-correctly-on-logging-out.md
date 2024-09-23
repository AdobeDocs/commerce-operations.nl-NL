---
title: 'ACSD-53998: Dynamisch blok op basis van klantensegment werkt onjuist na afmelden.'
description: Pas de ACSD-53998-patch toe om het Adobe Commerce-probleem op te lossen waarbij een dynamisch blok op basis van een klantsegment niet correct werkt nadat u zich hebt afgemeld bij een klantenaccount.
feature: Customers, Page Builder, Personalization
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# ACSD-53998: Dynamisch blok op basis van klantensegment werkt verkeerd na het afmelden

De ACSD-53998-patch verhelpt het probleem waarbij een dynamisch blok op basis van een klantensegment niet correct werkt nadat u zich hebt afgemeld bij een klantenaccount. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.39 wordt geïnstalleerd. De patch-id is ACSD-53998. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2 - 2.4.4-p6, 2.4.5-p1 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een dynamisch blok dat op een klantensegment wordt gebaseerd werkt niet correct na het programma openen van een klantenrekening.

<u> Eerste vereisten </u>:

Installeer en schakel [!DNL Page Builder] modules in.

<u> Stappen om </u> te reproduceren:

1. Maak twee klantsegmenten zonder voorwaarden.
1. Maak twee dynamische blokken voor elk segment.
1. Maak een blok met de twee dynamische blokken als [!DNL Page Builder] dynamische blokken.
1. Maak een widget met het bovenstaande blok en maak het blok zichtbaar onder de voettekstsectie van alle pagina&#39;s.
1. Wis de cache.
1. Open de startpagina.
1. Meld u aan als klant.
1. Afmelden.

<u> Verwachte resultaten </u>:

De banner die voor het programma geopende klanten wordt gecreeerd wordt niet getoond voor gastgebruikers.

<u> Ware resultaten </u>:

De banner die voor het het programma geopende klantensegment wordt gecreeerd wordt getoond zelfs na het programma openen van de klantenrekening.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
