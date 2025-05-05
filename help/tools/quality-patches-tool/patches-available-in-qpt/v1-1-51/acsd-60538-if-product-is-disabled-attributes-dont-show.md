---
title: 'ACSD-60538: kenmerken worden niet correct weergegeven als het product is uitgeschakeld in [!UICONTROL All Store Views]'
description: Pas de ACSD-60538-patch toe om het Adobe Commerce-probleem op te lossen, waarbij als een product wordt uitgeschakeld in *All Store Views* en alleen ingeschakeld in specifieke store view scope, de productkenmerken niet correct worden weergegeven in het GraphQL-antwoord, waardoor het product niet correct wordt weergegeven.
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538: kenmerken worden niet correct weergegeven als het product is uitgeschakeld in *[!UICONTROL All Store Views]*

De ACSD-60538-patch verhelpt het probleem dat als een product in *[!UICONTROL All Store Views]* is uitgeschakeld en alleen is ingeschakeld in specifieke weergavebereiken van de winkel, de productkenmerken niet correct worden weergegeven in de GraphQL-reactie, waardoor het product niet correct wordt weergegeven. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 wordt geïnstalleerd. De patch-id is ACSD-60538. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als een product is uitgeschakeld in *[!UICONTROL All Store Views]* en alleen is ingeschakeld in specifieke weergavebereiken, worden de productkenmerken niet correct weergegeven in de GraphQL-respons, wat tot gevolg heeft dat het product niet correct wordt weergegeven.

<u> Eerste vereisten </u>:

De voorraadmodule is geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Creeer een configureerbaar product met het *kleur* attribuut en drie kindproducten (*blauw*, *zwart*, en *bruin*).
1. Maak twee bijbehorende kindproducten (*blauw* en *zwart*) op het *[!UICONTROL All Store Views]* werkingsgebied onbruikbaar.
1. Ga naar **[!UICONTROL Store View]** bereik.
1. Laat kindproducten (*blauw* en *zwart*) op *[!UICONTROL Store View]* werkingsgebied toe.
1. Voer de onderstaande GraphQL-aanvraag uit:

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u> Verwachte resultaten </u>:

GraphQL-respons bevat de kenmerkwaarden voor het onderliggende gekoppelde product dat is uitgeschakeld op *[!UICONTROL All Store Views]* en ingeschakeld in het *[!UICONTROL Store View]* -bereik.

<u> Ware resultaten </u>:

GraphQL-respons heeft lege kenmerkwaarden voor het onderliggende gekoppelde product wanneer het product is uitgeschakeld op *[!UICONTROL All Store Views]* en ingeschakeld in het *[!UICONTROL Store View]* -bereik.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
