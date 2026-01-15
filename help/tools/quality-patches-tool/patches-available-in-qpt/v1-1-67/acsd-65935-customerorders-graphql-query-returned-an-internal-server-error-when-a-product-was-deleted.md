---
title: 'ACSD-65935: &grave; customerOrders'' GraphQL-query heeft een interne serverfout geretourneerd wanneer een product wordt verwijderd'
description: Pas de ACSD-65935-patch toe om het Adobe Commerce-probleem te verhelpen waarbij de GraphQL-query 'customerOrders' een interne serverfout heeft geretourneerd wanneer een product wordt verwijderd.
feature: Orders, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: fd0b7043770bbbd12fbb9aad8cddaa2434d2ea5b
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---


# ACSD-65935: `customerOrders` GraphQL-query heeft een interne serverfout geretourneerd wanneer een product wordt verwijderd

De ACSD-65935-patch verhelpt het probleem waarbij de `customerOrders` GraphQL-query een interne serverfout heeft geretourneerd wanneer een product wordt verwijderd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 wordt geïnstalleerd. De patch-id is ACSD-65935. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `customerOrders` GraphQL-query retourneert een interne serverfout wanneer een product wordt verwijderd.

<u> Stappen om </u> te reproduceren:

1. Twee eenvoudige producten maken
1. Maak een klant en plaats een bestelling met twee producten van de voorzijde.
1. Ga naar de achtergrond en verwijder één product.
1. Een klanttoken maken:

```
https://localhost/pub/graphql
mutation {
  generateCustomerToken(email: "test@test.com", password: "123123qA") {
    token
  }
}
```

1. Haal de lijst met bestellingen op met het filter `eligible_for_return` (in PWA wordt gebruikt om bestellingen van klanten op te halen):

```
https://localhost/pub/graphql
{
  customerOrders {
    items {
      order_number
      id
      created_at
      grand_total
      status
			items{
				eligible_for_return
			}
    }
  }
}
```

<u> Verwachte resultaten </u>:

Orderlijst wordt zonder fouten verzameld.

<u> Ware resultaten </u>:

Uitzondering: *Interne serverfout*

```
[2025-05-16T23:42:15.174025+00:00] report.ERROR: Call to a member function getIsReturnable() on null

{"exception":"[object] (GraphQL\\Error\\Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/vendor/webonyx/graphql-php/src/Error/Error.php:170) [previous exception] [object] (Error(code: 0): Call to a member function getIsReturnable() on null at /var/www/html/localhost/magento2ee/app/code/Magento/Rma/Helper/Data.php:644)"}

[]
```


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
