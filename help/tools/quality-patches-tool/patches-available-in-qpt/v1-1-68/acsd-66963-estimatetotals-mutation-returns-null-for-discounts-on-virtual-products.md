---
title: 'ACSD-66963: de mutatie van &grave; estimals &grave; keert ongeldig voor kortingen op virtuele producten terug'
description: Pas de ACSD-66963-patch toe om het Adobe Commerce-probleem op te lossen waarbij &grave; estimals' *null* retourneert voor kortingen wanneer een kortingscode wordt toegepast op een winkelwagentje met alleen virtuele producten.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: b62e48f5-a9d6-456a-97e7-96f740d8e927
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# ACSD-66963: `estimateTotals` mutatie retourneert null voor kortingen op virtuele producten

ACSD-66963 flardfixes de kwestie waar `estimateTotals` *ongeldig* voor kortingen terugkeert wanneer een kortingscode op een kar met slechts virtuele producten wordt toegepast. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-66963. Dit probleem is opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `estimateTotals` mutatie keert *ongeldig* voor kortingen terug wanneer een kortingscode op een kar wordt toegepast die slechts virtuele producten bevat.

<u> Stappen om </u> te reproduceren:

1. Maak een winkelwagen die alleen virtuele producten bevat.
1. Een kortingscode toepassen:

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u> Verwachte resultaten </u>:

De informatie van de korting is inbegrepen voor wortels die slechts virtuele producten bevatten.

```
    {
      "data": {
        "estimateTotals": {
          "cart": {
            "prices": {
              "discounts": [
                {
                  "amount": {
                    "value": 100.5,
                    "currency": "USD"
                  },
                  "label": "A second discount code for testing",
                  "coupon": {
                    "code": "z3r0c00l"
                  },
                  "applied_to": "ITEM",
                  "type": null
                }
              ]
            }
          }
        }
      },
      "extensions": {}
    }
```

<u> Ware resultaten </u>:

De informatie van de korting keert terug als *ongeldig* voor wortels met slechts virtuele producten.

```
    {
      "data": {
        "estimateTotals": {
          "cart": {
            "prices": {
              "discounts": null
            }
          }
        }
      },
      "extensions": {}
    }
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
