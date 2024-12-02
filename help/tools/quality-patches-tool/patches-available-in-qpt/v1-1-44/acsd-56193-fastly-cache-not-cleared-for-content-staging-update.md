---
title: 'ACSD-56193: [!DNL Fastly]  het geheime voorgeheugen wordt niet ontruimd voor inhoud die update opneemt'
description: Pas ACSD-56193 flard toe om de kwestie van Adobe Commerce te bevestigen waar het  [!DNL Fastly]  geheime voorgeheugen niet voor inhoud het opvoeren update wordt ontruimd.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: a702ce22-cc85-4f58-8766-637a1b93d405
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-56193: [!DNL Fastly] cache wordt niet gewist voor update van inhoudstaging

De ACSD-56193-patch verhelpt het probleem waarbij de [!DNL Fastly] -cache niet wordt gewist voor de update van de inhoudstaging. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-56193. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De cache van [!DNL Fastly/Varnish] wordt niet gewist voor de update van de inhoudstaging

<u> Stappen om </u> te reproduceren:

1. Installeer en configureer [!DNL Varnish] cache.
1. Maak een statisch blok met een geplande update.
1. Maak een categorie waarin het statische blok wordt ingesloten.
1. Zoek de inhoud van de categorie met de onderstaande GraphQL-query:

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. Voer deze query meerdere keren uit en zorg ervoor dat de reactie in de [!DNL Varnish] in de cache is opgeslagen.
1. Voer het uitsnijden uit om de geplande wijziging toe te passen.
1. Voer de bovenstaande GraphQL-query opnieuw uit.
1. Maak een nieuw schema voor hetzelfde statische blok.
1. Herhaal de stappen met nummer 5-9.

<u> Verwachte resultaten </u>:

De bijgewerkte inhoud wordt geretourneerd nadat de geplande updates zijn uitgevoerd.

<u> Ware resultaten </u>:

De verouderde inhoud wordt geretourneerd nadat de geplande updates zijn uitgevoerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
