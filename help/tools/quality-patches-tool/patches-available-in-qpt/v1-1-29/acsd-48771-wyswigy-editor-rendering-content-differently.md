---
title: 'ACSD-48771: inhoud wordt in de WYSIWYG-editor anders weergegeven'
description: Pas de ACSD-48771-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de inhoud in de WYSIWYG-editor anders wordt weergegeven.
feature: Cache, Page Content
role: Admin
exl-id: 9480af54-800b-4802-b1a3-65d1a6e169ec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-48771: inhoud wordt in de WYSIWYG-editor anders weergegeven

De ACSD-48771-patch verhelpt het probleem waarbij de WYSIWYG-editor inhoud anders weergeeft. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-48771. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

In de WYSIWYG-editor wordt inhoud anders weergegeven.

<u> Stappen om </u> te reproduceren:

1. Ga naar Adobe Commerce Admin, creeer een nieuwe pagina met een rij met drie kolommen, en sla de pagina op.
1. Werk Adobe Commerce bij naar een van de meest recente versies.
1. Plaats [!DNL Chrome] browser om geheim voorgeheugen en snelheid aan *Snelle 3G* onbruikbaar te maken.
1. Ga nogmaals naar de bewerkingspagina en vernieuw deze totdat de kolommen rijen worden.
1. Sla de pagina op terwijl de kolommen in rijen staan.

<u> Verwachte resultaten </u>:

De constructor van de Admin-pagina mag geen kolommen in rijen weergeven.

<u> Ware resultaten </u>:

Kolommen worden in verschillende rijen weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
