---
title: 'ACS2E-3838: [!DNL Page Builder]  de fouten van CORS verhinderen besparingsveranderingen in het admin paneel op productiemodus'
description: Pas ACS2E-3838 flard toe om de kwestie van Adobe Commerce te bevestigen waar  [!DNL Page Builder]  de fouten van CORS sparen veranderingen in het admin paneel op productiemodus verhinderen.
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
exl-id: 0d590c0e-e21c-4553-a0a3-9332e22796f3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACP2E-3838: [!DNL Page Builder] CORS-fouten voorkomen dat wijzigingen in de productiemodus worden opgeslagen in het deelvenster Beheer

De ACP2E-3838-patch verhelpt het probleem waarbij [!DNL Page Builder] CORS-fouten voorkomen dat wijzigingen in de productiemodus in het deelvenster Beheer worden opgeslagen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 is geïnstalleerd. De patch-id is ACP2E-3838. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL Page Builder] Met CORS-fouten kunnen wijzigingen in de productiemodus niet worden opgeslagen in het deelvenster Beheer.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij het deelvenster Beheer.
1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Pages]** .
1. Klik op **[!UICONTROL Add New Page]** of selecteer een bestaande CMS-pagina en klik op **[!UICONTROL Edit]** .
1. Klik op **[!UICONTROL Edit with Page Builder]** om een nieuw inhoudsblok toe te voegen of een bestaand blok te bewerken.
1. Breng wijzigingen aan in de inhoud, zoals tekst, afbeeldingen of andere elementen.
1. Klik op **[!UICONTROL Save]** .

<u> Verwachte resultaten </u>:

De pagina-inhoud moet zonder fouten worden opgeslagen.

<u> Ware resultaten </u>:

1. De [!DNL Page Builder] -wijzigingen worden niet opgeslagen.
1. De browserconsole registreert CORS-gerelateerde fouten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
