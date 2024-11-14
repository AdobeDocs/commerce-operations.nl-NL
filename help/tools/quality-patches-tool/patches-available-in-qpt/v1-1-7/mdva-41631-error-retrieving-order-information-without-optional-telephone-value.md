---
title: '''MDVA-41631: Fout bij het ophalen van bestelgegevens zonder optionele waarde ''phone'''
description: De flard MDVA-41631 lost de kwestie op waar de gebruikers een fout krijgen die bestelinformatie zonder facultatieve "telefoon"waarde door  [!DNL GraphQL] terugwinnen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 is geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
source-git-commit: 3f14d93eca09967e320aae4af5e94c6d0c16cd20
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-41631: Fout bij het ophalen van bestelgegevens zonder optionele waarde &quot;phone&quot;

De MDVA-41631-patch verhelpt het probleem waarbij gebruikers een fout krijgen bij het ophalen van bestelgegevens zonder de optionele waarde &quot;phone&quot; via [!DNL GraphQL] . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 wordt geïnstalleerd. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers krijgen een fout bij het ophalen van bestelgegevens zonder optionele waarde &quot;phone&quot; via [!DNL GraphQL] .

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Configuratie** > **Klanten** > **de Configuratie van de Klant** > **Naam en de Opties van het Adres** > **tonen Telefoon** en plaatsen het telefoonaantal als facultatief.
1. Plaats een bestelling met [!DNL GraphQL API] als aangemelde klant.
   * Stel het telefoonnummer niet in wanneer u het factuuradres en het verzendadres instelt. Volg de instructies die in [[!DNL GraphQL]  het Leerprogramma van de Controle ](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) in onze ontwikkelaarsdocumentatie worden gegeven.
1. Haal de orde terug gebruikend [!DNL GraphQL] [`customerOrders` vraag ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/).

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u> Verwachte resultaten </u>:

De gebruikers krijgen de ordeinformatie.

<u> Ware resultaten </u>:

Gebruikers krijgen de volgende fout: *&quot;message&quot;: &quot;Internal server error&quot;,*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
