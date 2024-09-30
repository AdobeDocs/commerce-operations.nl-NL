---
title: "ACSD-45049: kenmerkinstelling 'Is vereist' van de klant werkt niet volgens het bereik van de website in Admin"
description: Pas de ACSD-45049-patch toe om het Adobe Commerce-probleem op te lossen waarbij het kenmerk "[!UICONTROL Is required]" van de klant niet correct wordt overschreven volgens het websitebereik in Admin.
feature: Attributes, Customers
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-45049: kenmerkinstelling van de klant *[!UICONTROL Is required]* werkt niet volgens het bereik van de website in Admin

De ACSD-45049-patch verhelpt het probleem waarbij de instelling van het kenmerk *[!UICONTROL Is required]* van de klant niet correct werkt volgens het bereik van de website in Admin. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/usage.md) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-45049. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p7 en 2.4.5 - 2.4.5-p9

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De kenmerkinstelling van de klant *[!UICONTROL Is required]* werkt niet correct volgens het bereik van de website in Admin.

<u> Stappen om </u> te reproduceren:

1. Maak twee websites.
1. Open **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Customer attribute]** .
1. Creeer een nieuw attribuut, plaats **[!UICONTROL Is value required]** = *Nr*.
1. Schakelaar aan de standaardwebsite, en verandering **[!UICONTROL Is value required]** = *ja*. De andere website heeft de standaardwaarde.
1. Maak een nieuwe klant van Admin voor de niet-standaard website.

<u> Verwachte resultaten </u>:

Het kenmerk is niet vereist voor de niet-standaardwebsite.

<u> Ware resultaten </u>:

* Het kenmerk is vereist voor de niet-standaard website wanneer u een klant maakt in Admin.
* Het kenmerk is niet vereist voor de niet-standaard website wanneer een klant in de winkel wordt geregistreerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
