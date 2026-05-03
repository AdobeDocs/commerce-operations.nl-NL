---
title: 'ACSD-53845: Time-outprobleem met MySQL-verbinding wanneer consument max_messages = 0'
description: Pas de ACSD-53845-patch toe om het Adobe Commerce-probleem op te lossen waarbij MySQL-verbinding uitvalt wanneer de consument  max_messages = 0&grave;.
feature: REST, Configuration
role: Admin, Developer
exl-id: 437e29f4-b11a-466c-9928-3867821d2b8d
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-53845: Time-outprobleem met MySQL-verbinding bij consument `max_messages = 0`

De ACSD-53845-patch verhelpt het probleem waarbij MySQL-verbindingen uitvallen wanneer een gebruiker `max_messages = 0` . Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-53845. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

MySQL-verbinding loopt uit als de gebruiker `max_messages = 0` .

De verbinding met de database wordt echter hersteld wanneer een transactie wordt gestart.

<u> Stappen om </u> te reproduceren:

1. Verzend een aanvraag naar bulkupdateproducten met behulp van het `async/bulk/V1/products` REST API-eindpunt.
1. Controleer de status in de tabel `magento_operation` .

<u> Verwachte resultaten </u>:

De producten worden bijgewerkt.

<u> Ware resultaten </u>:

1. Er is een fout geregistreerd:

   ```yaml
   report.CRITICAL: Message has been rejected: SQLSTATE[HY000]: General error: 2006 MySQL server has gone away [] []
   ```

1. *status* voor deze verrichting blijft *4* in de `magento_operation` lijst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] hulplijn
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de gids van de Infrastructuur van Commerce op de Wolk toe

## Gerelateerde lezing

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf te dienen
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids
* [&#x200B; Beste praktijken voor het wijzigen van gegevensbestandlijsten &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce

Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
