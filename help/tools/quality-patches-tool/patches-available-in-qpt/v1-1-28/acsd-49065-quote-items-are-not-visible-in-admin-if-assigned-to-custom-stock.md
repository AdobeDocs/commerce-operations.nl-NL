---
title: 'ACSD-49065: Offertepunten zijn niet zichtbaar in admin'
description: Pas de ACSD-49065-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de aanhalingstekens niet zichtbaar zijn in de beheerder als ze alleen zijn toegewezen aan de aangepaste voorraad.
feature: Admin Workspace, B2B, Orders, Quotes
role: Admin
exl-id: fc3bea92-305b-4598-9915-3422d61c76ec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-49065: Offertepunten zijn niet zichtbaar in admin

De ACSD-49065-patch verhelpt het probleem waarbij de aanhalingstekens niet zichtbaar zijn in de beheerder als deze alleen zijn toegewezen aan de aangepaste voorraad. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 wordt geïnstalleerd. De patch-id is ACSD-49065. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De aanhalingstekens zijn niet zichtbaar in de beheerder als deze alleen zijn toegewezen aan de aangepaste voorraad.

Vereisten:

**[!UICONTROL B2B]** en **[!UICONTROL Inventory]** modules moeten zijn geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL Company]** en **[!UICONTROL B2B Quote]** onder **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** in.
1. Maak een secundair **[!UICONTROL Inventory Source]** en wijs het toe aan een secundair **[!UICONTROL Inventory Stock]** .
1. Maak een nieuw product door alleen het secundaire (niet-standaard) **[!UICONTROL Inventory Source]** toe te wijzen.
1. Ga naar de winkel en maak een nieuw bedrijfsaccount. Meld u aan als de **[!UICONTROL Company Admin]** en voeg het gemaakte product toe aan de winkelwagentje.
1. Navigeer naar het winkelwagentje en *[!UICONTROL Request a Quote]* .
1. Ga naar de beheerder en bekijk de gevraagde prijsopgave op **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** .

<u> Verwachte resultaten </u>:

De punten zijn zichtbaar in het nieuwe citaat dat met nieuwe producten wordt gecreeerd zonder de producten opnieuw te bewaren.

<u> Ware resultaten </u>:

De sectie *[!UICONTROL Items Quoted]* is leeg. Als u het nieuwe product opnieuw opslaat, worden de items weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
