---
title: 'ACSD-55238: De lege productmeta-beschrijving opslaan'
description: Pas ACSD-55238 flard toe om de kwestie van Adobe Commerce te bevestigen waar een productbeschrijving die HTML code bevat die door  [!DNL Page Builder]  wordt geproduceerd of een andere redacteur van HTML altijd in de meta beschrijving wordt getoond, en er is geen manier om het aan leeg te plaatsen.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 39ccf1bb-a71a-47a0-b252-e6331e2df9b0
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-55238: De lege productmeta-beschrijving opslaan

De ACSD-55238-patch verhelpt het probleem dat een productbeschrijving met door een HTML-editor gegenereerde HTML-code altijd wordt weergegeven in de metabeschrijving. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-55238. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een productbeschrijving die door [!DNL Page Builder] of een andere redacteur van de HTML gegenereerde HTML code bevat wordt altijd getoond in de meta beschrijving, en er is geen manier om het aan leeg te plaatsen.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** en maak een nieuw blok met alle inhoud.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** en maak een nieuw product. Stel de metabeschrijving in op leeg.
1. Voeg het hierboven gemaakte blok toe met *[!DNL Page Builder]* op het tabblad *[!UICONTROL Content]* en sla het product op.
1. Open het product op de winkel en controleer het documentelement `meta name = "description"` ervan.

<u> Verwachte resultaten </u>:

De beschrijving van de meta is leeg.

<u> Ware resultaten </u>:

Wanneer een product een blok in zijn beschrijving heeft, wordt het gebruikt voor de productbeschrijving van meta.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
