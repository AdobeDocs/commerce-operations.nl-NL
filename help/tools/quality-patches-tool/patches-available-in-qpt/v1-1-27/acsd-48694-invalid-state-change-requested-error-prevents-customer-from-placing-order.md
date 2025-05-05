---
title: 'ACSD-48694: Door de aangevraagde fout met betrekking tot een ongeldige statuswijziging kan de klant geen order plaatsen'
description: Pas de ACSD-48694-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de fout *Ongeldige statuswijziging aangevraagd* een klant belet een bestelling te plaatsen.
feature: Admin Workspace, Orders
role: Admin
exl-id: 6b9fa474-1d9d-411d-bbca-ce7463cfeb0d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-48694: *Ongeldige gevraagde staatsverandering* fout verhindert klant orde te plaatsen

ACSD-48694 herstelt de flard de kwestie waar de fout *Ongeldige gevraagde staatsverandering* een klant verhindert een orde te plaatsen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 wordt geïnstalleerd. De patch-id is ACSD-48694. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.37-p4, 2.4.1 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De fout *Ongeldige gevraagde staatsverandering* verhindert een klant een orde te plaatsen.

<u> Stappen om </u> te reproduceren:

1. Voeg een kleine vertraging toe tijdens de `/estimate-shipping-methods` request door een `sleep()` at `app/code/Magento/Quote/Model/GuestCart/GuestShippingMethodManagement.php::estimateByExtendedAddress()` functie op te nemen, zodat de `/estimate-shipping-methods` request is voltooid na de `/shipping-information` wanneer tijdens het afrekenen van de verzendstap naar de betalingsstap wordt gegaan.
1. Vorm de zitting om [!DNL Redis] met *disable_locking te gebruiken: 1* het plaatsen.
1. Open **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** en schakel *[!UICONTROL Persistent Shopping Cart]* in.
1. Meld u aan als klant en voeg een product toe aan het winkelwagentje.
1. Laat de klantenzitting verlopen. Blijvende cookie en het winkelwagentje blijven bestaan.
1. Ga nu naar Afhandeling, voeg het verzendadres toe en navigeer naar de betalingssectie.
1. Ga terug naar de homepage of een andere pagina en meld u aan bij de klantenaccount.
1. Laat de zitting opnieuw verlopen.
1. Ga nu rechtstreeks naar de betalingspagina en navigeer naar de betalingsstap.
1. Plaats de bestelling.

<u> Verwachte resultaten </u>:

* Er is geen fout.
* De orde wordt met succes geplaatst en a *bedankt* pagina wordt getoond.

<u> Ware resultaten </u>:

De fout *Ongeldige gevraagde staatsverandering* wordt getoond, maar de orde wordt geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
