---
title: 'ACP2E-3767: De laatste bundeloptie wordt opnieuw weergegeven nadat een bundelproduct is opgeslagen'
description: Pas de ACS2E-3767-patch toe om het Adobe Commerce-probleem op te lossen waarbij de laatste bundeloptie in een bundelproduct niet kan worden verwijderd.
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f39442925d9cc82087af9e84d91137a0fcd0ec14
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACP2E-3767: De laatste bundeloptie wordt opnieuw weergegeven nadat een bundelproduct is opgeslagen

De ACS2E-3767-patch verhelpt het probleem waarbij de laatste bundeloptie opnieuw verschijnt nadat het bundelproduct is opgeslagen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACP2E-3767. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De laatste bundeloptie in een bundelproduct kan niet worden verwijderd.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** .
1. Selecteer **[!UICONTROL Simple Product]** in de vervolgkeuzelijst.
1. Voer de vereiste gegevens in en sla deze op.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** .
1. Selecteer **[!UICONTROL Bundle Product]** in de vervolgkeuzelijst.
1. Voer de vereiste gegevens in.
1. Klik op **[!UICONTROL Add Option]** bij Bundelitems.
1. Voeg een titel toe aan de nieuwe optie en klik vervolgens op **[!UICONTROL Add Products to Option]** .
1. Selecteer vervolgens het eerder gemaakte eenvoudige product **[!UICONTROL Add Selected Products]** .
1. Sla het bundelproduct op.
1. Verwijder de bundeloptie en sla op.

<u> Verwachte resultaten </u>:

1. De bundeloptie is verwijderd.
1. Er wordt een bericht weergegeven als verwijdering niet is toegestaan.

<u> Ware resultaten </u>:

1. De bundeloptie blijft actief.
1. Er wordt geen fout of melding weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
