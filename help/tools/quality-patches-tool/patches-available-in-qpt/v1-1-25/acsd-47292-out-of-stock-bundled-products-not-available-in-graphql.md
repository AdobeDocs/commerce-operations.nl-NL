---
title: 'ACSD-47292: gebundelde producten uit de voorraad zijn niet beschikbaar in GraphQL-respons'
description: Pas de ACSD-47292-patch toe om het Adobe Commerce-probleem op te lossen waarbij de gebundelde producten uit de voorraad niet beschikbaar zijn in de GraphQL-respons, zelfs als de "producten uit de voorraad tonen" op Ja is ingesteld.
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
exl-id: 3b8114a3-cc45-4d65-af74-cb3e905d7f75
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-47292: gebundelde producten uit de voorraad zijn niet beschikbaar in GraphQL-respons

De ACSD-47292-patch verhelpt het probleem dat gebundelde producten uit de voorraad niet beschikbaar zijn in de GraphQL-respons, zelfs als de [!UICONTROL Display Out-of-Stock Products] is ingesteld op *[!UICONTROL Yes]* . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-47292. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebundelde producten uit de out-of-stock zijn niet beschikbaar in de GraphQL-respons, zelfs niet als de [!UICONTROL Display Out-of-Stock Products] is ingesteld op *[!UICONTROL Yes]* .

<u> Stappen om </u> te reproduceren:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** en stel de [!UICONTROL Display Out-of-Stock Products] in op *[!UICONTROL Yes]* .
1. Maak twee eenvoudige producten, s1 en s2.
1. Maak s1 uit-van-voorraad en niet zichtbaar individueel en s2 in-voorraad en niet zichtbaar individueel, en wijs hen aan een categorie toe.
1. Maak een gebundeld product met ten minste één optieproduct en wijs s1 en s2 aan deze optie toe (invoertype &quot;RadioButton&quot;).
1. Sla het gebundelde product op en wijs het toe aan een categorie.
1. Ga naar de winkel en open dit gebundelde product. U zult zien dat de optie s1 buiten de voorraad grijs maar zichtbaar is.
1. Een GraphQL-aanvraag verzenden:

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u> Verwachte resultaten </u>:

s1-bundeloptie wordt vermeld in de GraphQL-reactie omdat [!UICONTROL Display Out-of-Stock Products] is ingesteld op *[!UICONTROL Yes]* en deze zichtbaar is in de winkel.

<u> Ware resultaten </u>:

s1-bundeloptie wordt niet vermeld in GraphQL-reactie.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
