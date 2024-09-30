---
title: "ACSD-51240: Geüploade bestand ontbreekt bij registratie via bedrijfsregistratieformulier"
description: Pas de ACSD-51240-patch toe om het Adobe Commerce-probleem op te lossen waarbij het geüploade bestand ontbreekt tijdens de registratie via het bedrijfsregistratieformulier.
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-51240: Geüploade bestand ontbreekt bij registratie via bedrijfsregistratieformulier

>[!NOTE]
>
>Dit flard wordt vervangen door [ ACSD-55628 ](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-42/acsd-55628-upload-file-company-registration-form-replace-file-customer-attribute-storefront.md).

De ACSD-51240-patch verhelpt het probleem waarbij het geüploade bestand ontbreekt tijdens de registratie via het bedrijfsregistratieformulier. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.33 wordt geïnstalleerd. De patch-id is ACSD-51240. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 &lt; 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) . Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Probleem

Geüpload bestand ontbreekt bij registratie via bedrijfsregistratieformulier.

<u> Stappen om </u> te reproduceren:

1. Plaats **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B >Company]** > **[!UICONTROL Enable]** = *ja*.
1. Creeer een nieuw klantenattribuut van **[!UICONTROL File]** type, plaats **[!UICONTROL Show in StoreFront]** = *ja*, en selecteer **[!UICONTROL all forms]**.
1. Creeer een nieuw bedrijf op de Storefront en upload een beeld voor het nieuwe attribuut.
Open het bedrijf en de admin gebruiker op de Storefront.

<u> Verwachte resultaten </u>:

Het geüploade bestand wordt weergegeven.

<u> Ware resultaten </u>:

Het geüploade bestand wordt niet weergegeven op de bedrijfspagina of op de pagina voor de beheerder van de klant in de [!UICONTROL Commerce Admin] .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
