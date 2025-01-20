---
title: 'ACSD-62758: Het probleem met videorendering op configureerbare productpagina''s is opgelost'
description: Pas de ACSD-62758-patch toe om het Adobe Commerce-probleem op te lossen waarbij productvideo's op configureerbare productdetailpagina's niet correct worden weergegeven wanneer URL's vooraf geselecteerde staalopties bevatten.
feature: Catalog Management
role: Admin, Developer
exl-id: 084b497d-4471-4458-bc1d-2a452bfe2662
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-62758: Het probleem met videorendering op configureerbare productpagina&#39;s is opgelost

De ACSD-62758-patch verhelpt het probleem dat productvideo&#39;s op configureerbare productdetailpagina&#39;s niet correct worden weergegeven wanneer URL&#39;s vooraf geselecteerde staalopties bevatten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-62758. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Productvideo&#39;s worden niet correct weergegeven op configureerbare productdetailpagina&#39;s wanneer de URL vooraf geselecteerde staalopties bevat, wat resulteert in de weergave van een statisch beeld in plaats van de video.

<u> Stappen om </u> te reproduceren:

1. Navigeer naar [!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product] .
1. Selecteer het kenmerk **[!UICONTROL Color]** en bewerk het.
1. Werk de volgende instellingen bij:
   1. Stel [!UICONTROL Catalog Input Type for Store Owner] in op [!UICONTROL Visual Swatch] .
   1. Stel **[!UICONTROL Update Product Preview Image]** in op **[!UICONTROL Yes]** .
1. Maak enkele opties voor dit kenmerk.
1. Maak een nieuwe categorie en voeg er een nieuw configureerbaar product aan toe met het kenmerk **[!UICONTROL Color]** .
1. Voeg één willekeurige afbeelding toe aan het bovenliggende product.
1. Bewerk de nieuw gemaakte configureerbare onderliggende producten en voeg een video toe aan de mediagalerie:
   1. Klik op **[!UICONTROL Add Video]** en gebruik de URL van de testvideo: https://vimeo.com/12860646.
1. Sla het product op, verwijder de cache en indexeer de winkel opnieuw.
1. Open het nieuwe product in de winkel, selecteer een van de staalopties en bevestig dat de video correct wordt geladen terwijl de spelerknop wordt weergegeven.
1. De video moet op de verwachte wijze worden geladen en de afspeelknop moet worden weergegeven.
1. Klik nu met de rechtermuisknop op een van de staalopties, selecteer **[!UICONTROL Inspect]** en zoek de kenmerk-id en optie-id. Kopieer de product-URL en voeg het volgende aan het einde toe: `www.product-url.com/producit-test#attribute_id=option_id` . Hiermee selecteert u de staaloptie vooraf. Open de bijgewerkte URL in een nieuw venster.

<u> Verwachte resultaten </u>:

De video moet correct worden geladen, net als wanneer een staaloptie handmatig wordt geselecteerd.

<u> Ware resultaten </u>:

In plaats van de video wordt een statische afbeelding weergegeven. Consolefouten worden geregistreerd, wat aangeeft dat de video niet is geïnitialiseerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

