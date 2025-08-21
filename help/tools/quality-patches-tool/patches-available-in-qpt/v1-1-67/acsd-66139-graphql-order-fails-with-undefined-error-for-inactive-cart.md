---
title: 'ACSD-66139: GraphQL-volgorde mislukt met niet-GEDEFINIEERDE fout voor inactief winkelwagentje'
description: Pas de ACSD-66139-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij GraphQL bij het plaatsen van een order voor een niet-bestaand of inactief winkelwagentje een UNDEFINED-foutcode retourneert in plaats van een specifieke foutcode wanneer foutberichten worden vertaald.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 16d95ae0d58dfdc88a5fab725a37d353d3ee5c96
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# ACSD-66139: GraphQL-volgorde mislukt met &#39;UNDEFINED&#39;-fout voor inactief winkelwagentje

ACSD-66139 herstelt de flard waar, wanneer het plaatsen van een orde voor een niet-bestaand of inactief karretje, GraphQL een *ONGEDEFINIEERDE* foutencode in plaats van specifieke terugkeert wanneer de foutenmeldingen worden vertaald. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 wordt geïnstalleerd. De patch-id is ACSD-66139. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar het laatste pictogram en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL keert een *ONGEDEFINIEERDE* foutencode in plaats van specifieke terug wanneer het plaatsen van een orde voor een niet-bestaande of inactieve kar, als het foutenbericht wordt vertaald.

<u> Stappen om </u> te reproduceren:

1. Voeg `app/i18n/Magento/de_DE/de_DE.csv` toe en neem de volgende vertaling van de fouttekenreeks op:

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. Maak een winkelweergave in het deelvenster Beheer. Ga naar **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]** . Klik op **[!UICONTROL Create Store View]** en voer bij **[!UICONTROL Code]** de code in `test` .
1. Wijs `german` taal toe aan de nieuwe winkelweergave.
1. Voer `setup:upgrade` en `setup:static-content:deploy -f` uit.
1. Voer de volgende GraphQL-query met header &#39;Store :test&#39; uit:

```
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u> Verwachte resultaten </u>:

Correcte foutreactie:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "CART_NOT_FOUND"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

<u> Ware resultaten </u>:

`error_code` teruggekeerde is *ONGEDEFINIEERD*:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "UNDEFINED"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
