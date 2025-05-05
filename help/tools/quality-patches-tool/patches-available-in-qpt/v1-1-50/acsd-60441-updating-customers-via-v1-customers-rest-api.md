---
title: 'ACSD-60441: Het bijwerken van klanten via V1/klanten  [!DNL REST]  API eindpunt werpt een fout'
description: Pas ACSD-60441 flard toe om de kwestie van Adobe Commerce te bevestigen waar het bijwerken van klanten via V1/klanten  [!DNL REST]  API wanneer het gebruiken van het teken van de integratietoegang dat van backend wordt geproduceerd een fout veroorzaakt.
feature: REST, Customers
role: Admin, Developer
exl-id: 3936c065-41a6-4860-8313-e054f9b23ac7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-60441: Het bijwerken van klanten via het API-eindpunt `V1/customers` [!DNL REST] veroorzaakt een fout

De ACSD-60441-patch verhelpt het probleem dat het bijwerken van klanten via de `V1/customers` [!DNL REST] -API wanneer het gebruik van het toegangstoken voor integratie dat via de back-end wordt gegenereerd, een fout veroorzaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-60441. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p8

**Compatibel met de versies van Adobe Commerce**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p9, 2.4.5-p8, 2.4.6-p6, 2.4.7-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u klanten bijwerkt via het API-eindpunt `V1/customers` [!DNL REST] wanneer u het toegangstoken voor integratie gebruikt dat op basis van de back-end is gegenereerd, treedt er een fout op.

<u> Stappen om </u> te reproduceren:

1. Maak een integratie van de beheerder.
1. Verzend een [!DNL POST] aanvraag naar `rest/default/V1/customers/<customer_id>` met het integratietoken.

   ```json
   {
     "customer": {
       "email": "roni_cost@example.com",
       "firstname": "Veronica",
       "lastname": "Costello"
     }
   }
   ```

<u> Verwachte resultaten </u>:

De klantgegevens worden bijgewerkt.

<u> Ware resultaten </u>:

De volgende fout treedt op:

     &quot;json 
     &lbrace;
     &quot;bericht&quot;: &quot;Een klant met het zelfde e-mailadres bestaat reeds in een bijbehorende website.&quot;, 
     &quot;spoor&quot;: ... 
     
    &quot;

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
