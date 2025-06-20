---
title: 'ACSD-64546: generiek foutbericht in UI en array naar uitzondering van tekenreeksomzetting tijdens het maken van UPS-labels'
description: Pas de ACSD-64546-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een algemeen foutbericht wordt weergegeven in de gebruikersinterface en de array op een uitzondering voor tekenreeksomzetting wordt geregistreerd tijdens het maken van UPS-labels. De patch zorgt ervoor dat de juiste fout wordt weergegeven in de gebruikersinterface en de logboeken.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 458371bc-4afe-4675-b090-5797e05c5b88
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-64546: Generic foutenmelding in UI en *Serie aan koordomzetting* uitzondering tijdens het etiketverwezenlijking van UPS

ACSD-64546 flardfixes de kwestie waar een generisch foutenbericht in UI verschijnt en de *Serie aan koordomzetting* uitzondering wordt geregistreerd tijdens het etiketverwezenlijking van UPS, die de correcte fout verzekeren wordt getoond in UI en logboeken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 wordt geïnstalleerd. De patch-id is ACSD-64546. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een generisch foutenbericht toont omhoog in UI en de *Serie aan koordomzetting* uitzondering komt tijdens de het etiketverwezenlijking van UPS voor.

<u> Stappen om </u> te reproduceren:

1. Maak een klantenaccount met een geldig adres.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL GENERAL]** > **[!UICONTROL General]** > **[!UICONTROL Store Information]** en voeg een geldig adres toe.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Shipping settings]** > **[!UICONTROL Origin]** en voeg een geldig adres toe.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL SALES]** > **[!UICONTROL Delivery methods]** > **[!UICONTROL UPS]** en configureer UPS.
1. Plaats een volgorde met [!UICONTROL UPS] .
1. Verwijder de UPS-gebruikersnaam en -wachtwoord uit `core_config_data` in de database.
1. Clean config-cache.
1. Open de gemaakte volgorde in de **[!UICONTROL Admin]** .
1. Maak een nieuwe verzending.
   1. Schakel het selectievakje **[!UICONTROL Create Shipping Label]** in.
   1. Klik op **[!UICONTROL Submit shipment]**.
   1. Voeg het product toe aan een pakket. Geef de pakketgrootte op (lengte, breedte en hoogte).
   1. Klik op **[!UICONTROL Save]**.

<u> Verwachte resultaten </u>:

Het daadwerkelijke foutenbericht wordt getoond in UI en de logboeken.

<u> Ware resultaten </u>:

* De volgende fout verschijnt in UI:
  *een fout kwam terwijl het creëren van het verschepen etiket voor.*
* De *Serie aan koordomzetting* uitzondering verhindert het daadwerkelijke foutenbericht in de logboeken worden getoond of worden opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:
* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce on cloud Infrastructure: Upgrades and Patches > Apply Patches in the Commerce on Cloud Infrastructure guide.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:
* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
