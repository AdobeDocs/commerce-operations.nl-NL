---
title: 'ACSD-64178: [!UICONTROL Edit Attribute Set] pagina wordt langzaam geladen met duizenden productkenmerken'
description: Pas de ACSD-64178-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de pagina [!UICONTROL Edit Attribute Set] langzaam wordt geladen als er duizenden productkenmerken zijn.
feature: Catalog Management
role: Admin, Developer
exl-id: 959d825d-1b7b-49f0-b49f-64e149106e91
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# ACSD-64178: [!UICONTROL Edit Attribute Set] pagina wordt langzaam geladen met duizenden productkenmerken

De ACSD-64178-patch verhelpt het probleem waarbij de pagina **[!UICONTROL Edit Attribute Set]** langzaam wordt geladen als er duizenden productkenmerken zijn. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 wordt geïnstalleerd. De patch-id is ACSD-64178. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De pagina **[!UICONTROL Edit Attribute Set]** wordt langzaam geladen als er duizenden productkenmerken zijn.

<u> Stappen om </u> te reproduceren:

1. Maak ten minste 4200 kenmerken die niet zijn toegewezen aan een van de kenmerksets.
1. Ga op de zijbalk Beheerder naar **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Attribute Set]** . Klik op een kenmerk dat u wilt bewerken.

<u> Verwachte resultaten </u>:

De pagina wordt binnen een redelijke tijd geladen.

<u> Ware resultaten </u>:

Het laden van de pagina duurt enkele minuten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
