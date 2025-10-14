---
title: 'ACSD-51120: GraphQL GET request cache not clear for CMS pages that contain CMS block'
description: Pas de ACSD-51120-patch toe om het Adobe Commerce-probleem op te lossen waarbij de GraphQL GET-aanvraagcache niet wordt gewist voor CMS-pagina's die CMS-blokken bevatten.
exl-id: e1b84db0-2441-4729-aeeb-8486a623aebf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-51120: GraphQL GET request cache not clear for CMS pages that contain CMS block

De ACSD-51120-patch verhelpt het probleem dat de GraphQL GET-aanvraagcache niet wordt gewist voor CMS-pagina&#39;s die CMS-blokken bevatten die via een testupdate worden bijgewerkt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 wordt geïnstalleerd. De patch-id is ACSD-51120. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL GET request cache is niet gewist voor CMS-pagina&#39;s die CMS-blokken bevatten die via een testupdate zijn bijgewerkt.

<u> Stappen om </u> te reproduceren:

1. Maak een CMS-blok.
1. Neem het CMS-blok met de [!DNL Page Builder] op in een CMS-pagina.
1. Zoek de CMS-pagina met de opgegeven GraphQL-query op een GET-aanvraag:

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Controleer of de GraphQL-reactie in de cache is opgeslagen in [!DNL Varnish] .
1. Maak een geplande update voor het blok.
1. Wacht tot de geplande update is toegepast en voer de uitsnijdtaak uit om de geplande update toe te passen.
1. Zoek de CMS-pagina opnieuw met de opgegeven GraphQL-query op een GET-aanvraag.

<u> Verwachte resultaten </u>:

In het antwoord wordt de bijgewerkte inhoud weergegeven.

<u> Ware resultaten </u>:

De reactie toont nog steeds de oude inhoud.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
