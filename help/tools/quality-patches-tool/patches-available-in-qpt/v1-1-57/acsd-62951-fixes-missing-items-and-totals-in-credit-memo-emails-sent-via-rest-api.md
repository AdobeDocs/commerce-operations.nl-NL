---
title: 'ACSD-62951: verhelpt ontbrekende items en totalen in [!UICONTROL Credit Memo] e-mails die via REST API worden verzonden'
description: Pas de ACSD-62951-patch toe om het Adobe Commerce-probleem op te lossen waarbij het [!UICONTROL Credit Memo] -e-mailbericht wordt verzonden zonder de orderitems en totalen op te nemen.
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-62951: verhelpt ontbrekende items en totalen in *[!UICONTROL Credit Memo]* e-mails die via REST API worden verzonden

De markering ACSD-62951 verhelpt de kwestie waar [!UICONTROL Credit Memo] e-mail wordt verzonden zonder de orde punten en totalen te omvatten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-62951. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5-p10

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De *[!UICONTROL Credit Memo]* -e-mail die wordt verzonden wanneer een creditmemo wordt gemaakt via de REST API `POST V1/order/:orderId/refund` , bevat niet de orderitems en totalen.

<u> Stappen om </u> te reproduceren:

1. Maak een bestelling met elk product.
1. Verzend en factureer de bestelling. Zorg ervoor dat de e-mail met de factuur wordt verzonden en dat deze de productgegevens bevat.
1. Genereer een beheerderstoken met de API-client.
1. Gebruik het token om een creditmemo te maken via de REST API.
   1. Eindpunt: `POST V1/order/:orderId/refund`
   1. Vragen om lading:

      ```
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u> Verwachte resultaten </u>:

Het e-mailadres van *[!UICONTROL Credit Memo]* moet de terugbetaalde items en totalen bevatten

<u> Ware resultaten </u>:

Het e-mailbericht van *[!UICONTROL Credit Memo]* bevat geen items of totalen, wat leidt tot onvolledige informatie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
