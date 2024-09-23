---
title: 'MDVA-40134: GraphQL retourneert geen verwante producten als gedeelde catalogus is ingeschakeld.'
description: De MDVA-40134-patch verhelpt het probleem dat GraphQL geen verwante producten retourneert wanneer de gedeelde catalogus is ingeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 is geïnstalleerd. De patch-id is MDVA-40134. De kwestie is opgelost in Adobe Commerce 2.4.3.
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-40134: GraphQL retourneert geen verwante producten als gedeelde catalogus is ingeschakeld

De MDVA-40134-patch verhelpt het probleem dat GraphQL geen verwante producten retourneert wanneer de gedeelde catalogus is ingeschakeld. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 geïnstalleerd is. De patch-id is MDVA-40134. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL retourneert geen verwante producten wanneer de gedeelde catalogus is ingeschakeld.

<u> Eerste vereisten </u>:

B2B-modules moeten worden geïnstalleerd.
Het exemplaar moet schoon zijn met alleen de monstergegevens.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Configuratie** > **Algemeen** > **B2B eigenschappen** en laat **Bedrijf en Gedeelde Catalogus** toe.
1. Ga naar **Catalogus** > **Gedeelde Catalogus** en voeg alle producten aan de **Algemene Catalogus** toe.
1. Gebruik de voorbeeldgegevens en wijzig de joust Duffle Bag (SKU 24-MB01).
1. Onder **Verwante Producten**, voeg de twee Dubbele zakken (identiteitskaart 7 en 13) toe.
1. Verzend a **Post** verzoek:

<pre>{
  products(filter: {sku: {eq: "24-MB01"}, sort: {name: ASC}) {
    items {
      related_products {
        uid
        name
      }
    }
  }
}</pre>

<u> Verwachte resultaten </u>:

Verwante producten worden weergegeven in de reactie van GraphQL.

<u> Ware resultaten </u>:

Gebruikers krijgen de volgende fout:

<pre>Retourwaarde van Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() moet van het type int zijn, null geretourneerd {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Retourwaarde van Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() moet van het type int zijn, null geretourneerd </pre>

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
