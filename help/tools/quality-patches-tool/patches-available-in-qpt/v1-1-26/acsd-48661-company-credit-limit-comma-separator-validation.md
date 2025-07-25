---
title: 'ACSD-48661: door het bedrijf afgegeven validatie van komma''s als scheidingsteken voor kredietlimiet'
description: Pas de ACSD-48661-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het komma-scheidingsteken het opslaan van het bedrijf verhindert vanwege een validatiefout wanneer de limiet van het bedrijfskrediet hoger is dan 999.
feature: Admin Workspace, B2B, Companies, Orders
role: Admin
exl-id: 7115226e-5942-4a8f-9dec-b1b6f665eef8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-48661: door het bedrijf afgegeven validatie van komma&#39;s als scheidingsteken voor kredietlimiet

De ACSD-48661-patch verhelpt het probleem dat wanneer de bedrijfskredietlimiet hoger is dan 999, het komma-scheidingsteken het bedrijf niet kan opslaan als gevolg van een validatiefout. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 wordt geïnstalleerd. De patch-id is ACSD-4861. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als de kredietlimiet van het bedrijf groter is dan 999, voorkomt het scheidingsteken met komma&#39;s dat het bedrijf opslaat als gevolg van een validatiefout.

<u> Stappen om </u> te reproduceren:

1. Schakel de bedrijffunctie in via **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** .
1. Maak een bedrijf en voeg een kredietlimiet toe die groter is dan 999 onder het tabblad **[!UICONTROL Company Credit]** .
1. Sla het bedrijf op.
1. Bewerk het bedrijf en sla het opnieuw op.

<u> Verwachte resultaten </u>:

U kunt het bedrijf opslaan zonder de kredietlimiet te bepalen. Komma wordt niet ondersteund voor invoervelden voor de bedragen en prijzen.

<u> Ware resultaten </u>:

U kunt het bedrijf niet opslaan vanwege een validatiefout in het veld *[!UICONTROL Credit Limit]* . Adobe Commerce voegt automatisch komma-scheidingstekens voor creditlimieten toe, ook al accepteert het veld [!UICONTROL Credit Limit] geen komma&#39;s.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
