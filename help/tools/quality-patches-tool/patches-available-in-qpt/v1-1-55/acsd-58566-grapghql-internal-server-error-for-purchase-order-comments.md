---
title: 'ACSD-58566: interne serverfout van GraphQL voor opmerkingen over inkooporders'
description: Pas de ACSD-58566-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij GraphQL een interne serverfout retourneert bij het opvragen van het ` created_at'-veld in de addPurchaseOrderComment-mutatie.
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
exl-id: 6d051f57-7a2f-44a5-a1c9-834917ed986c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566: interne serverfout van GraphQL voor opmerkingen over inkooporders

De ACSD-58566-patch verhelpt het probleem waarbij het opvragen van het `created_at` -veld in de `addPurchaseOrderComment` -mutatie een null-waarde retourneert in plaats van de verwachte datetime. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-58566. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL retourneert een interne serverfout bij het opvragen van het veld `created_at` in de mutatie `addPurchaseOrderComment` .

<u> Eerste vereisten </u>:

B2B-modules zijn geïnstalleerd en de optie Bedrijf en inkooporders zijn ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Produceer een klantenteken voor een bedrijfgebruiker.
1. Voer de volgende reeks GraphQL-verzoeken uit:
   1. Creeer a *kar* gebruikend `customerCart`.
   1. Voeg een product aan de *kar* toe gebruikend `addProductsToCart`.
   1. Plaats de volgorde met `placePurchaseOrder` .
   1. Voeg met `addPurchaseOrderComment` een opmerking toe aan de inkooporder.

   ```
   mutation {
       addPurchaseOrderComment(
           input: { purchase_order_uid: "MQ==", comment: "Looks good to me" }
   ) {
           comment {
               uid
               created_at
               author {
                   firstname
                   lastname
                   email
               }
               text
           }
       }
   }
   ```

<u> Verwachte resultaten </u>:

Het veld `created_at` retourneert de datum van de opmerking bij de inkooporder.

<u> Ware resultaten </u>:

Geeft null weer in plaats van de `created_at` -datum.

```
{
  "errors": [
    {
      "message": "Internal server error",
      "locations": [
        {
          "line": 10,
          "column": 1
        }
      ],
      "path": [
        "addPurchaseOrderComment",
        "comment",
        "created_at"
      ]
    }
  ],
  "data": {
    "addPurchaseOrderComment": null
  }
}
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

[[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
