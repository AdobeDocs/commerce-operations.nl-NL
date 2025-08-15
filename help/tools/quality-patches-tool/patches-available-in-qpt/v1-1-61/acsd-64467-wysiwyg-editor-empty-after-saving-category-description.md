---
title: 'ACSD-64467: WYSIWYG-editor is leeg na het opslaan van categoriebeschrijving op winkelweergaveniveau'
description: Pas de ACSD-64467-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de WYSIWYG-editor leeg lijkt nadat een categoriebeschrijving is opgeslagen op het niveau van de winkelweergave.
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467: WYSIWYG-editor is leeg na het opslaan van categoriebeschrijving op winkelweergaveniveau

De ACSD-64467-patch verhelpt het probleem dat de WYSIWYG-editor leeg lijkt nadat een categoriebeschrijving is opgeslagen op het niveau van de winkelweergave. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 wordt geïnstalleerd. De patch-id is ACSD-64467. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De WYSIWYG-editor wordt leeg weergegeven nadat een categoriebeschrijving is opgeslagen op het niveau van de winkelweergave.

<u> Stappen om </u> te reproduceren:

1. Bewerk een categorie in Commerce Admin op het weergaveniveau van de winkel.
1. Schakel het selectievakje *[!UICONTROL Use default value]* naast de beschrijving van de categorie uit.
1. Voer een beschrijving in de WYSIWYG-editor in.
1. Klik op **[!UICONTROL Save]**.

<u> Verwachte resultaten </u>:

De beschrijving wordt opgeslagen en correct weergegeven.

<u> Ware resultaten </u>:

De beschrijving is leeg nadat de pagina opnieuw is geladen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
