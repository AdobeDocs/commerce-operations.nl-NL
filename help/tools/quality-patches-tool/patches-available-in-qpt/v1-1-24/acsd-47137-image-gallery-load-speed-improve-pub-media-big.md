---
title: 'ACSD-47137: verbeter de laadsnelheid van de afbeeldingsgalerie van de map pub/media'
description: Pas de ACSD-47137-patch toe om de laadsnelheid van de afbeeldingsgalerie te verbeteren wanneer de map 'pub/media' erg groot is.
feature: Cache, Catalog Management, Categories, Media
role: Admin
exl-id: 8a5dd930-1940-486e-96db-ee1b166cf312
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-47137: verbeter de snelheid waarmee afbeeldingsgalerie wordt geladen wanneer de map `pub/media` groot is

De ACSD-47137-patch verbetert de laadsnelheid van de afbeeldingsgalerie wanneer de map `pub/media` erg groot is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 wordt geïnstalleerd. De patch-id is ACSD-47137. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De laadsnelheid van de afbeeldingsgalerie neemt af wanneer de map `pub/media` erg groot is.

<u> Stappen om </u> te reproduceren:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** aan _Nr_.
1. Reinig het configuratiecache.
1. Meld u af en meld u opnieuw aan als beheerder.
1. Ga in het zijpaneel Beheer naar **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** en selecteer de hoofdcategorie.
1. Vouw de sectie **[!UICONTROL Content]** uit en klik op **[!UICONTROL Select from Gallery]** .

Bij het laden van de pagina verzendt Adobe Commerce de aanvraag `media_gallery/directories/gettree` om de mediamappenstructuur te laden.

<u> Verwachte resultaten </u>:

De aanvraag `media_gallery/directories/gettree` moet alleen inhoud laden uit de benodigde mappen, anders dan de padlijst in zijn geheel vanuit de map `pub/media/` .

<u> Ware resultaten </u>:

Het laden van de aanvraag `media_gallery/directories/gettree` duurt lang wanneer de map `pub/media/` veel inhoud bevat.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
