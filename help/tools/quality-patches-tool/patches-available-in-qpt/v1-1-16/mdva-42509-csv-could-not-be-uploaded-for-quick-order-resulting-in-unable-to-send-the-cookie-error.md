---
title: 'MDVA-42509: CSV kan niet worden geüpload voor snelle bestelling, waardoor de fout ''Kan het cookie niet verzenden'' optreedt'
description: De MDVA-42509-patch lost het probleem op waarbij een CSV niet kon worden geüpload voor snelle bestelling, wat resulteert in *Kan de cookie*-fout niet verzenden. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 is geïnstalleerd. De patch-id is MDVA-42509. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: B2B, Orders
role: Admin
exl-id: 6319931b-9cf1-4004-b302-737863c53ff8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-42509: CSV kan niet worden geüpload voor snelle bestelling, waardoor de fout &#39;Kan het cookie niet verzenden&#39; optreedt

Het flard MDVA-42509 lost de kwestie op waar CSV niet voor snelle orde kon worden geupload die in *onbekwaam resulteert om de koekjesfout* te verzenden. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 geïnstalleerd is. De patch-id is MDVA-42509. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Creërend een snelle orde met een groot aantal producten die een CSV gebruiken toont een koekjesfout: *Onbekwaam om het koekje* te verzenden

<u> Stappen om </u> te reproduceren:

1. Laat Snelle Orde toe door aan **Sporen** te navigeren > **Montages** > **Configuraties** > **Algemene** > **B2B Eigenschappen**.
1. Creeer een klantenrekening en ga naar **Snelle Orde** bij de hoogste verbinding.
1. Probeer een snelle orde tot stand te brengen gebruikend CSV die meer dan 100 SKUs heeft.

<u> Verwachte resultaten </u>:

U kunt een snelle orde met een groot aantal SKUs tot stand brengen.

<u> Ware resultaten </u>:

Er wordt een foutbericht weergegeven met betrekking tot de grootte van cookies.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
