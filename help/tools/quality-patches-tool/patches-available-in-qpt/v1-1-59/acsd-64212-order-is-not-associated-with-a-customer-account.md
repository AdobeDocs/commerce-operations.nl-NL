---
title: 'ACSD-64212: Orde niet verbonden aan een klantenrekening die via  [!DNL GraphQL]  wordt gecreeerd na het plaatsen van orde'
description: Pas ACSD-64212 flard toe om de kwestie van Adobe Commerce te bevestigen waar een orde niet verbonden met een klantenrekening wordt die via  [!DNL GraphQL]  na het plaatsen van de orde wordt gecreeerd.
feature: GraphQL, Checkout, Customers
role: Admin, Developer
exl-id: be62e635-2a61-41ed-9c1d-b2c54ee01024
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-64212: Bestelling niet gekoppeld aan een klantenaccount die via [!DNL GraphQL] is gemaakt na het plaatsen van de bestelling

De ACSD-64212-patch verhelpt het probleem dat een bestelling niet wordt gekoppeld aan een klantenaccount die via [!DNL GraphQL] wordt gemaakt nadat de bestelling is geplaatst. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 wordt geïnstalleerd. De patch-id is ACSD-64212. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De bestelling is niet gekoppeld aan een klantenaccount wanneer de account via [!DNL GraphQL] wordt gemaakt nadat de bestelling is geplaatst.

<u> Stappen om </u> te reproduceren:

1. Plaats een gastbestelling op de voorkant.
1. Verzend het volgende verzoek om het account te maken:

```graphql
mutation CreateAccountAfterCheckout(
$email: String!
$firstname: String!
$lastname: String!
$password: String!
$is_subscribed: Boolean!
) {
  createCustomer(
    input: {
      email: $email
      firstname: $firstname
      lastname: $lastname
      password: $password
      is_subscribed: $is_subscribed
    }
  ) {
    customer {
      email
      __typename
    }
    __typename
  }
}
```

```json
{
  "email": "guest@example.com",
  "firstname": "first",
  "lastname": "last",
  "password": "password",
  "is_subscribed": false
}
```

<u> Verwachte resultaten </u>:

De gastorde wordt geassocieerd met de klant nadat de klantenrekening wordt gecreeerd.

<u> Ware resultaten </u>:

De rekening van de klant werd gecreeerd, maar de gastorde wordt niet geassocieerd met de klant.


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
