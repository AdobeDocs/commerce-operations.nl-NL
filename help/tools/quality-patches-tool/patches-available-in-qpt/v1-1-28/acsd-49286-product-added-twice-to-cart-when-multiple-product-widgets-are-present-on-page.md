---
title: 'ACSD-49286: product dat tweemaal aan het winkelwagentje wordt toegevoegd als er meerdere product-widgets aanwezig zijn'
description: Pas de ACSD-49286-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het product tweemaal aan een winkelwagentje wordt toegevoegd wanneer er meerdere producten op de pagina aanwezig zijn.
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
exl-id: 03fdaafe-5566-4b75-a0eb-e0cba3dad3e7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286: product dat tweemaal aan het winkelwagentje wordt toegevoegd als er meerdere product-widgets aanwezig zijn

De ACSD-49286-patch verhelpt het probleem waarbij het product tweemaal aan een winkelwagentje wordt toegevoegd als er meerdere producten op de pagina aanwezig zijn. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28 wordt geïnstalleerd. De patch-id is ACSD-49286. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het product wordt twee keer aan een winkelwagentje toegevoegd als er meerdere productwidgets op de pagina aanwezig zijn.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de beheerder en ga naar **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. Klik in de inhoudssectie op **[!UICONTROL Edit]** gebruiken [!DNL Page Builder] .
1. Voeg twee rijelementen toe aan **[!UICONTROL Content]** .
1. Voeg producten in beide rijelementen toe.
1. Stel in de eerste rij de vormgeving van het product in op [!UICONTROL Product Grid] en selecteer een categorie die u wilt weergeven.
1. Stel in de tweede rij de vormgeving van het product in op [!UICONTROL Product Carousel] en selecteer een andere categorie die u wilt weergeven.
1. Ga naar de winkel **[!UICONTROL Home Page]** en voeg één product toe via Productraster.
1. Voeg nog een product toe vanuit [!UICONTROL Product Carousel] .

<u> Verwachte resultaten </u>:

De hoeveelheid product mag niet worden verdubbeld nadat u een product vanuit [!UICONTROL Product Grid] aan de winkelwagen hebt toegevoegd.

<u> Ware resultaten </u>:

De hoeveelheid product wordt verdubbeld nadat een product vanuit [!UICONTROL Product Grid] aan de winkelwagen is toegevoegd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe. 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
