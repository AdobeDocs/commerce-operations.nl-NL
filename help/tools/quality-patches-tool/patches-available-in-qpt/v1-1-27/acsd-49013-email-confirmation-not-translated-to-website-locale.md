---
title: 'ACSD-49013: e-mailbevestiging niet vertaald naar landinstelling van website'
description: Pas de ACSD-49013-patch toe om het Adobe Commerce-probleem op te lossen, waarbij e-mailbevestiging niet naar de landinstelling van de website wordt vertaald wanneer klanten met de bulk-API worden gemaakt.
feature: Admin Workspace, Communications
role: Admin
exl-id: 1b0dc6aa-d5ee-4adf-882d-88f29a7eab34
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-49013: e-mailbevestiging niet vertaald naar landinstelling van website

De ACSD-49013-patch verhelpt het probleem waarbij e-mailbevestiging niet wordt vertaald naar de landinstelling van de website wanneer klanten met de bulk-API worden gemaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27 wordt geïnstalleerd. De patch-id is ACSD-49013. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mailbevestiging wordt niet vertaald naar de landinstelling van de website wanneer klanten met de bulk-API worden gemaakt.

<u> Stappen om </u> te reproduceren:

1. Installeer een andere landinstelling, bijvoorbeeld `de_DE` .
1. Vorm *RabbitMQ*.
1. Voer `bin/magento setup:upgrade` uit om de wachtrijen in RabbitMQ te installeren en het taalpakket in te stellen.
1. Maak een aanvullende website in [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** .
1. Stel de landinstelling van deze nieuwe website in op `de_DE` in [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]** .
1. Voer een API-aanroep uit om een klantenaccount te maken met de bulk-API. Gebruik de bijbehorende `website_id` .

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. Uitvoeren `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`.
1. U kunt zien dat de klantenaccount op de opgegeven website correct is gemaakt.
1. Controleer het ontvangen e-mailbericht voor klantenregistratie.

<u> Verwachte resultaten </u>:

Aangezien de klant op een opgegeven website is gemaakt, wordt de registratie-e-mail verzonden met de landinstelling van die website.

<u> Ware resultaten </u>:

De klant is op de juiste wijze gemaakt op de opgegeven website, maar de registratie-e-mail wordt verzonden met de standaardlandinstelling wanneer de bulk-API wordt gebruikt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
