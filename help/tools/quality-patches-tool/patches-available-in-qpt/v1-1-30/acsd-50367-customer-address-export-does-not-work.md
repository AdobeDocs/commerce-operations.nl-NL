---
title: 'ACSD-50367: Exporteren van klantadres werkt niet met kenmerk voor meerdere selecties'
description: Pas de ACSD-50367-patch toe om het Adobe Commerce-probleem op te lossen waarbij het exporteren van het klantadres niet werkt wanneer een multi-select **'kenmerk Customer Address&grave;** zonder waarden wordt gemaakt.
feature: Admin Workspace, Attributes, Data Import/Export, Shipping/Delivery
role: Admin
exl-id: 3f33a590-e7c2-424e-aacd-2df7ab893c3e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-50367: Exporteren van klantadres werkt niet

De ACSD-50367-patch verhelpt het probleem dat het exporteren van het adres van de klant niet werkt wanneer een multi-select **`Customer Address`** -kenmerk zonder waarden wordt gemaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 wordt geïnstalleerd. De patch-id is ACSD-50367. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het exporteren van het adres van de klant werkt niet wanneer een attribuut **`Customer Address`** multi-select zonder waarden wordt gecreeerd.

<u> Eerste vereisten </u>:

Maak een klant met een adres.

<u> Stappen om </u> te reproduceren:

1. Maak een multi-select **`Customer Address`** -kenmerk in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer Addresses]** .
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Export]** en selecteer **`Customer Address`** entiteitstype.
1. Exporteer de klantadressen. U zult zien dat niets wordt uitgevoerd.
1. Verwijder het kenmerk multi-select **`Customer Address`** en exporteer de klantadressen opnieuw. Dit keer wordt het CSV-bestand van de adressen gegenereerd.

<u> Verwachte resultaten </u>:

De adressen van de klant kunnen als CSV- dossier worden uitgevoerd wanneer multi-select **`Customer Address`** attribuut wordt gecreeerd.

<u> Ware resultaten </u>:

De adressen van de klant kunnen niet als Csv- dossier worden uitgevoerd wanneer multi-select **`Customer Address`** attribuut wordt gecreeerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
