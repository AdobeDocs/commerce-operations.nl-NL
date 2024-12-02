---
title: 'ACSD-55334: Labels die in GraphQL niet zijn vertaald via vertaalwoordenboeken'
description: Pas de ACSD-55334-patch toe om het Adobe Commerce-probleem op te lossen, waarbij labels in het GraphQL-antwoord niet via vertaalwoordenboeken worden vertaald.
feature: Categories, GraphQL
role: Admin, Developer
exl-id: c22e5007-c661-49d4-90b7-dcee9b97c823
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# ACSD-55334: Labels die in GraphQL niet zijn vertaald via vertaalwoordenboeken

De ASCD-55334-patch verhelpt het probleem dat labels niet via vertaalwoordenboeken worden vertaald in het GraphQL-antwoord. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 wordt geïnstalleerd. De patch-id is ASCD-55334. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Labels worden niet vertaald via vertaalwoordenboeken in het GraphQL-antwoord.

<u> Stappen om </u> te reproduceren:

1. Installeer een taalpakket.
1. Een GraphQL-aanvraag verzenden zoals:

   ```GrapQL
   query {
       products(filter: {}, pageSize: 25, sort: {}) {
           aggregations {
               label
           }
           total_count
       }
   }
   ```

1. Controleer het antwoord.

<u> Verwachte resultaten </u>:

Het label *[!UICONTROL Category]* wordt vertaald.

<u> Ware resultaten </u>:

Het label *[!UICONTROL Category]* wordt niet vertaald.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
