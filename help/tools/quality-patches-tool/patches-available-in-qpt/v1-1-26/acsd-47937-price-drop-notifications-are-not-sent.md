---
title: 'ACSD-47937: meldingen voor prijsdaling zijn niet verzonden vanwege caching op toepassingsniveau'
description: Pas de ACSD-47937-patch toe om het Adobe Commerce-probleem op te lossen, waarbij prijsdalingsmeldingen niet altijd worden verzonden als gevolg van caching op toepassingsniveau.
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47937: meldingen voor prijsdaling zijn niet verzonden vanwege caching op toepassingsniveau

De ACSD-47937-patch verhelpt het probleem dat prijsdalingsmeldingen niet altijd worden verzonden vanwege caching op toepassingsniveau. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 wordt geïnstalleerd. De patch-id is ACSD-47937. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 en 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4, 2.4.5 en 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Klanten krijgen geen e-mail met prijsverlaging voor producten voor latere prijswijzigingen.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL Product Alert]** in voor zowel *[!UICONTROL Price Changes]* als *[!UICONTROL Back in Stock]* in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** .
1. Schakel **[!UICONTROL Display Out of Stock Products]** in.
1. Maak een eenvoudig product (ABC) met qty = 0.
1. Maak een klant van de winkel en meld u aan voor het bovenstaande product om productwaarschuwingen voor prijsdalingen te ontvangen.
1. Start de productwaarschuwing voor klanten.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Verlaag de prijs voor het ABC-product.
1. Trigger de waarschuwing voor het product.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Verlaag de prijs voor het ABC-product opnieuw.
1. Trigger de waarschuwing voor het product.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Als u niet bekend bent met [!DNL n98] , kunt u `bin/magento cron:run command` as usual en de `cron_schedule` tabel uitvoeren om te controleren of de `catalog_product_alert` taak de status van succes krijgt.

<u> Verwachte resultaten </u>:

De tweede e-mail voor prijsverlaging wordt verzonden.

<u> Ware resultaten </u>:

De tweede e-mail voor prijsverlaging wordt niet verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Patches toepassen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de basis van de steunkennis zelf-te dienen
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
