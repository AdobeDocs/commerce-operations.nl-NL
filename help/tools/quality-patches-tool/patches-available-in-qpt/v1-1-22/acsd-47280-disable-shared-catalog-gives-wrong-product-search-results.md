---
title: '[!DNL ACSD-47280]: wanneer u de gedeelde catalogus uitschakelt, krijgt u onjuiste zoekresultaten voor het product'
description: Pas het  [!DNL ACSD-47280]  flard toe om het tonen van de correcte onderzoeksresultaten te bevestigen wanneer de gedeelde cataloguseigenschap gehandicapt is.
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# [!DNL ACSD-47280]: Als u de gedeelde catalogus uitschakelt, worden onjuiste zoekresultaten voor het product weergegeven

De patch [!DNL ACSD-47280] corrigeert de weergave van de juiste zoekresultaten wanneer de functie [!DNL shared catalog] is uitgeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.22 wordt geïnstalleerd. De waarde [!DNL patch ID] is [!DNL ACSD-47280] . Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik [!DNL patch ID] als zoektrefwoord om de patch te zoeken.

## Probleem

Als u [!DNL shared catalog] uitschakelt, levert dit onjuiste zoekresultaten op.

<u> Eerste vereisten </u>:

* [!DNL B2B] geïnstalleerde modules

<u> Stappen om </u> te reproduceren:

1. Maak een tweede website.
1. Een product toewijzen aan de tweede website.
1. De producten van de controle op de **tweede website** gebruikend [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. **[!UICONTROL Shared Catalog]** inschakelen bij standaard [!DNL scope] .
1. In de aanvraag [!DNL GraphQL] worden geen producten voor de tweede website meer weergegeven. Dit is het juiste resultaat.
1. Ga naar de [!DNL scope] tweede website en schakel **[!UICONTROL Company]** uit.

<u> Verwachte resultaten </u>:

In de aanvraag [!DNL GraphQL] moeten nog steeds producten voor de tweede website worden weergegeven.

<u> Ware resultaten </u>:

In de aanvraag [!DNL GraphQL] worden geen producten voor de tweede website weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
