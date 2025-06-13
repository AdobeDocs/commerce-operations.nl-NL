---
title: 'ACSD-45143: setShippingAddressOnCart-mutatie waarbij de numerieke regiocode niet wordt ingesteld als ''region'''
description: De ACSD-45143-patch verhelpt het probleem waarbij de setShippingAddressOnCart-mutatie het instellen van code voor numerieke gebieden als 'region' niet toestaat. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 is geïnstalleerd. De patch-id is ACSD-45143. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Orders, Shipping/Delivery, Shopping Cart
role: Admin
exl-id: c7d9d1f2-4731-406f-93bd-036f0fe75b1d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-45143: setShippingAddressOnCart-mutatie waarbij de numerieke regiocode niet wordt ingesteld als &#39;region&#39;

De ACSD-45143-patch verhelpt het probleem waarbij de setShippingAddressOnCart-mutatie het instellen van code voor numerieke gebieden als &#39;region&#39; niet toestaat. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 geïnstalleerd is. De patch-id is ACSD-45143. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Met de mutatie setShippingAddresOnCart kan geen numerieke regiocode worden ingesteld als &quot;regio&quot;.

<u> Stappen om </u> te reproduceren:

1. Maak een winkelwagentje met de onderstaande query.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      createEmptyCart
    &rbrace;
    </code>
    </pre>

1. Verzend een aanvraag om het verzendadres in te stellen op de winkelwagentje.

   <pre>
    <code class="language-graphql">
    mutation ($cartId: String!) &lbrace;
      setShippingAddressesOnCart(
        input: &lbrace;
          cart_id: $cartId
          shipping_addresses: &lbrace;
            address: &lbrace;
              firstname: "Tomek"
              lastname: "Nowak"
              company: "Company Name"
              street: ["234 Rue de Rivoli"]
              region: "58"
              city: "Lille"
              postcode: "59800"
              country_code: "FR"
              telephone: "123-456-0000"
              save_in_address_book: false
            &rbrace;
          &rbrace;
        &rbrace;
        ) &lbrace;
          cart &lbrace;
            shipping_addresses &lbrace;
              firstname
              lastname
              company
              street
              city
              region &lbrace;
                code
                label
              &rbrace;
              postcode
              telephone
              country &lbrace;
                code
                label
              &rbrace;
            &rbrace;
          &rbrace;
        &rbrace;
      &rbrace;
      </code>
      </pre>

   Opmerking: de landcode is in dit voorbeeld ingesteld op &quot;FR&quot; en de regiocode op &quot;58&quot;. Volgens de tabel van `directory_country_region` DB is regiocode 58 &quot;Nièvre&quot;.

1. Controleer de reactie die wordt geretourneerd.

<u> Verwachte resultaten </u>:

Adobe Commerce staat het instellen van code voor numerieke gebieden toe in de GraphQL-aanvraag.

<u> Ware resultaten </u>:

De regiocode wordt gewijzigd in 47.

<pre>
<code class="language-graphql">
&lbrace;
  "data": &lbrace;
    "setShippingAddressesOnCart": &lbrace;
      "cart": &lbrace;
        "shipping_addresses": &lbrack;
        &lbrace;
          "firstname": "Tomek",
          "lastname": "Nowak",
          "company": "Company Name",
          "street": &lbrack;
          "234 Rue de Rivoli"
          &rbrack;,
          "city": "Lille",
          "region": &lbrace;
            "code": "47",
            "label": "Lot-et-Garonne"
            &rbrace;,
            "postcode": "59800",
            "telephone": "123-456-0000",
            "country": &lbrace;
              "code": "FR",
              "label": "FR"
            &rbrace;
          &rbrace;
        &rbrack;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
