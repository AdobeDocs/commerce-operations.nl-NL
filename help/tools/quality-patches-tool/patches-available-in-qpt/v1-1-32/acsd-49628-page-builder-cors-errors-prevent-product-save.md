---
title: 'ACSD-49628: [!DNL Page Builder]  de fouten van CORS verhinderen product sparen'
description: Pas ACSD-49628 flard toe om de kwestie van Adobe Commerce te bevestigen waar de  [!DNL Page Builder]  fouten CORS product sparen verhinderen.
feature: Categories, Page Builder, Products
role: Admin
exl-id: 5bceddfa-5fbf-4ebe-a233-de7720764849
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-49628: [!DNL Page Builder] CORS-fouten voorkomen dat het product wordt opgeslagen

De ACSD-49628-patch verhelpt het probleem waarbij [!DNL Page Builder] CORS-fouten voorkomen dat een beheerder een product opslaat. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-49628. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL Page Builder] CORS-fouten verhinderen het opslaan van een product.

<u> Stappen om </u> te reproduceren:

1. Meld u aan als beheerder.
1. Maak een gebruikersrol met de volgende machtigingen:

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]** .
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]** .

1. Voeg geen *[!UICONTROL Content]* -machtigingen toe.
1. Maak nog een beheerder en wijs de rollen die hierboven zijn gemaakt toe aan deze gebruiker.
1. Maak een product en meld u af.
1. Meld u aan als tweede beheerder.
1. Probeer het product te bewerken en op te slaan.

<u> Verwachte resultaten </u>:

De tweede beheerder kan het product opslaan, maar de knop **[!UICONTROL Edit with Page Builder]** wordt zonder *[!UICONTROL Content]* -machtigingen niet weergegeven aan de beheerder.

<u> Ware resultaten </u>:

De tweede beheerder kan het product niet opslaan vanwege meerdere [!DNL Page Builder] -fouten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
