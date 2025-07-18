---
title: 'ACSD-50895: [!DNL Google Analytics]  3 GTM de markeringen worden niet in brand gestoken als  [!DNL Google Analytics]  4 GTM niet wordt gevormd'
description: Pas ACSD-50895 flard toe om de kwestie van Adobe Commerce te bevestigen waar  [!DNL Google Analytics]  3 GTM de markeringen niet in brand worden gestoken als  [!DNL Google Analytics]  4 GTM niet wordt gevormd.
role: Admin
exl-id: 871e2ca1-dc10-435c-9325-62f5b9b673ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 3 GTM-tags worden niet geactiveerd als [!DNL Google Analytics] 4 GTM niet is geconfigureerd

De ACSD-50895-patch verhelpt het probleem waarbij [!DNL Google Analytics] 3 GTM-tags niet worden geactiveerd als [!DNL Google Analytics] 4 GTM niet is geconfigureerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 wordt geïnstalleerd. De patch-id is ACSD-50895. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL Google Analytics] 3 GTM-tags worden niet geactiveerd als [!DNL Google Analytics] 4 GTM niet is geconfigureerd.

<u> Stappen om </u> te reproduceren:

1. Meld u aan als beheerder.
1. Laat **[!DNL Google Analytics 3]** en **[!DNL Google Tag Manager]** in **Admin** toe > **Opslag** > **Configuratie** > **Verkoop** > **Google API** > **Google Analytics**.
1. Schakel **[!DNL Google Analytics 4]** en **[!DNL Google Tag Manager]** niet in.
1. Open de productpagina in de winkelruimte.

<u> Verwachte resultaten </u>:

De GTM-tags worden geactiveerd wanneer alleen **[!DNL Google Analytics]** 3 GTM is ingeschakeld.

<u> Ware resultaten </u>:

De GTM-tags worden niet geactiveerd wanneer **[!DNL Google Analytics]** 4 GTM wordt uitgeschakeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
