---
title: 'ACSD-52041: Bij het renderen van Page Builder worden geen vergrendelingen vrijgegeven'
description: Pas de ACSD-52041-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de Page Builder vijf seconden lang wordt weergegeven zonder vergrendelingen vrij te geven.
feature: Page Builder
role: Admin, Developer
exl-id: 48a7fc36-e98a-4a4e-bed3-248d7d73f6cb
source-git-commit: 1a78b2afa6e751d430700e72f512f7d82d1c1bdd
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-52041: Bij het renderen van Page Builder worden geen vergrendelingen vrijgegeven

De ACSD-52041-patch verhelpt het probleem waarbij de Page Builder vijf seconden lang rendert zonder vergrendelingen vrij te geven. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-52041-v2. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4, en 2.4.6 - 2.4.6-p2.



>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.


## Probleem

**[!DNL Page Builder]** geeft voor *5* seconden terug zonder de sloten vrij te geven.

<u> Stappen om </u> te reproduceren:

1. Bewerk een CMS-pagina, productpagina of iets anders dat **[!DNL Page Builder]** heeft.
1. Sla de wijzigingen op.
1. Let op de pagina die tijd bespaart.

<u> Verwachte resultaten </u>

De inhoud wordt opgeslagen. Er zijn geen fouten gevonden in het browserlogbestand.

<u> Ware resultaten </u>

De besparing duurt langer dan de gebruikelijke tijd om te voltooien.
Fout in console: ``Page Builder was rendering for 5 seconds without releasing locks``

## De patch toepassen

Om individuele flarden voor versies **toe te passen 2.4.4 - 2.4.4-p5, 2.4.5 - 2.4.5-p4, en 2.4.6 - 2.4.6-p2**, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) in de [!DNL Quality Patches Tool] gids.
