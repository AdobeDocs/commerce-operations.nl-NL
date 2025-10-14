---
title: 'MDVA-44044: Product wordt niet op categoriepagina weergegeven nadat het aan een nieuwe website is toegewezen'
description: Met de MDVA-44044-patch wordt het probleem opgelost waarbij een product niet op de categoriepagina wordt weergegeven nadat het aan een nieuwe website is toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 is geïnstalleerd. De patch-id is MDVA-44044. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Categories, Products
role: Admin
exl-id: ae797cdc-5977-40b8-82da-ccf364466bdf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# MDVA-44044: Product wordt niet op categoriepagina weergegeven nadat het aan een nieuwe website is toegewezen

Met de MDVA-44044-patch wordt het probleem opgelost waarbij een product niet op de categoriepagina wordt weergegeven nadat het aan een nieuwe website is toegewezen. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 geïnstalleerd is. De patch-id is MDVA-44044. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het product wordt niet op de categoriepagina weergegeven nadat het aan een nieuwe website is toegewezen.

<u> Stappen om </u> te reproduceren:

1. Stel de indexeermodus in op plannen.
1. Maak een secundaire website, sla deze op en sla de weergave op.
1. Voeg een secundaire archiefcode toe in `index.php`:

   ```php
   $_SERVER["MAGE_RUN_CODE"]="en_us";
   $_SERVER["MAGE_RUN_TYPE"]="store";
   ```

1. Maak een nieuwe categorie.
1. Maak een nieuw product dat is toegewezen aan de nieuwe categorie. Let erop dat u het alleen toewijst aan de primaire website.
1. Voer de uitsnede uit.
1. Open de categorie vanuit de winkel.
1. Wijs het product toe aan de secundaire website.
1. Voer de uitsnede opnieuw uit.

<u> Verwachte resultaten </u>:

Het product wordt op de categoriepagina weergegeven na een geplande indexeerprogramma.

<u> Ware resultaten </u>:

Het product wordt pas op de categoriepagina weergegeven als het volledig opnieuw is samengesteld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
