---
title: 'ACSD-60326: GraphQL-query voor status van klant [!UICONTROL Returns] geeft een fout'
description: Pas de ACSD-60326-patch toe om het Adobe Commerce-probleem op te lossen waarbij een fout optreedt in de GraphQL-query voor de status [!UICONTROL Returns] van de klant.
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326: GraphQL-query voor status van klant [!UICONTROL Returns] geeft een fout

De ACSD-60326-patch verhelpt het probleem waarbij een fout optreedt in de GraphQL-query voor de status [!UICONTROL Returns] van de klant. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 wordt geïnstalleerd. De patch-id is ACSD-60326. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL-query over de status van de klant [!UICONTROL Returns] geeft een fout.

<u> Stappen om </u> te reproduceren:

1. Initialiseer een nieuwe instantie met voorbeeldgegevens.
1. Op *[!UICONTROL Admin]* sidebar, ga **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]** en plaats **[!UICONTROL Enable RMA on Storefront]** aan *ja*.
1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** en vul het adres in.
1. Wijzig het wachtwoord voor de klant `roni_cost@example.com` .
1. Meld u aan bij het beheerpaneel en plaats een bestelling voor de klant `roni_cost@example.com` met de volgende producten:
   * *WSH12-32-rood*
   * *WSH12-32-paars*
   * *WSH12-32-Groen*
1. Maak een *[!UICONTROL Invoice]* en *[!UICONTROL Shipment]* voor deze volgorde.
1. Selecteer **[!UICONTROL Create Returns]** .
1. Ga naar **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]** en:
   * Selecteer *WSH12-32-Rood* en *WSH12-32-Paars*
   * Klik op **[!UICONTROL Add Selected Products to returns]** :
      * Plaats **[!UICONTROL Requested]** = *1*
      * Plaats **[!UICONTROL Return Reason]** aan *uit Dienst*
      * Plaats **[!UICONTROL Item Condition]** aan *Geopend*
      * Plaats **[!UICONTROL Resolution]** aan *Terugkeer*
   * Klik op **[!UICONTROL Submit Returns]**.
1. Open **[!UICONTROL Returns]** en selecteer **[!UICONTROL Return Items]** aan de linkerkant.
   * Plaats **[!UICONTROL Authorized]** = *1* voor beide producten
   * Plaats **[!UICONTROL Status]** als *Gemachtigd* voor *WSH12-32-Paars*
   * Plaats **[!UICONTROL Status]** als *ontkend* voor *WSH12-32-rood*
   * Klikken **[!UICONTROL Save]**
1. Maak een nieuwe bestelling met dezelfde producten.
1. Maak een *[!UICONTROL Invoice]* , *[!UICONTROL Shipment]* en *[!UICONTROL Returns]* voor dezelfde producten. Beide autoriseren en doorgaan tot het einde van het [!UICONTROL Returns] -proces.
1. Een klanttoken genereren met behulp van de volgende GraphQL-query:

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. Autoriseer met het ontvangen teken en voer volgende vraag uit:

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u> Verwachte resultaten </u>:

Er wordt geen fout weergegeven in de query. Het statuut van de tweede terugkeer is niet *ongeldig*.

<u> Ware resultaten </u>:

De query retourneert een interne serverfout:

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
