---
title: 'MDVA-43348: GraphQL request shows error'
description: De patch MDVA-43348 verhelpt het probleem waarbij het GraphQL-verzoek van de Gift Card een fout toont als "gift_card_options" "uid" bevat. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43348. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Gift, GraphQL
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# MDVA-43348: GraphQL-aanvraag voor een kaartje geeft een fout weer

De MDVA-43348-patch verhelpt het probleem waarbij in het GraphQL-verzoek van de Gift Card een fout wordt weergegeven als `gift_card_options` &quot;uid&quot; bevat. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 geïnstalleerd is. De patch-id is MDVA-43348. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL-aanvraag voor een kaartje met een kaartje geeft een fout weer als gift_card_options &quot;uid&quot; bevat.

<u> Stappen om </u> te reproduceren:

1. Maak een Cadeauproduct.
1. Voer opnieuw index uit.
1. Maak een GraphQL-aanroep waarbij de URL-sleutel &quot;cadeau-card&quot; is:

<pre>
<code class="language-graphql">
query getProductOptionsForProductPage_bypassFastly($urlKey: String!) &lbrace;
  products(filter: { url_key: { eq: $urlKey } }) &lbrace;
    items &lbrace;
      id
      url_key
      ... on GiftCardProduct &lbrace;
        allow_open_amount
        open_amount_min
        open_amount_max
        giftcard_type
        is_redeemable
        lifetime
        allow_message
        message_max_length
        gift_card_options &lbrace;
          uid
          title
          required
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u> Verwachte resultaten </u>:

Cadeaugegevens worden op verzoek geretourneerd.

<u> Ware resultaten </u>:

De volgende fout treedt op bij een verzoek om Cadeaugegevens:

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        0,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        1,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        2,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        3,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        4,
        "uid"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "products": &lbrace;
      "items": &lbrack;
        &lbrace;
          "id": 2,
          "url_key": "gitf-card",
          "allow_open_amount": false,
          "open_amount_min": null,
          "open_amount_max": null,
          "giftcard_type": "VIRTUAL",
          "is_redeemable": true,
          "lifetime": 0,
          "allow_message": true,
          "message_max_length": 255,
          "gift_card_options": &lbrack;
            null,
            null,
            null,
            null,
            null
          &rbrack;
        &rbrace;
      &rbrack;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
