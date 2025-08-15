---
title: 'ACSD-51739: Fout bij het aanvragen van ` structure_id` in ` CompanyTeam` GraphQL request'
description: Pas ACSD-51739 flard toe om de kwestie van Adobe Commerce te bevestigen waar een fout is teruggekeerd wanneer ` structure_id ` in een ` CompanyTeam ` GraphQL verzoek wordt gevraagd.
exl-id: 74c78278-779d-4fb6-ba10-501b25b9f1fe
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-51739: Fout bij aanvragen `structure_id` in `CompanyTeam` GraphQL-verzoek

De ACSD-51739-patch verhelpt het probleem waarbij een fout wordt geretourneerd wanneer `structure_id` wordt aangevraagd in een `CompanyTeam` GraphQL-aanvraag. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 wordt geïnstalleerd. De patch-id is ACSD-51739. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een fout geretourneerd wanneer `structure_id` wordt aangevraagd in een `CompanyTeam` GraphQL-aanvraag.

<u> Stappen om te reproduceren </u>

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**, en reeks *[!UICONTROL Enable Company]* aan *ja*.
1. Creeer een bedrijf samen met een bedrijf admin gebruiker.
1. Creeer een nieuwe klant (*customer1*), en wijs het bedrijf (hierboven gecreeerd) aan deze klant toe.
1. Voor frontend, login als bedrijf admin gebruiker.
1. Creeer een bedrijfteam, en wijs *customer1* aan het team toe gebruikend belemmering en daling.
1. Voer de volgende GraphQl-query van het bedrijf uit, die `CompanyTeam` met `structure_id` bevat:

   ```GraphQL
   query{
       company {
           id
           name
           structure {
               items {
               id
               parent_id
               entity {
                   __typename
                   ... on Customer {
                       firstname
                       lastname
                       email
                       structure_id
                   }
                   ... on CompanyTeam {
                       id
                       name
                       structure_id
                   }
               }
       }
   }
   }
   }
   ```

1. Controleer het GraphQL-antwoord.

<u> Verwachte resultaten </u>:

Er worden geen fouten geretourneerd en alle aangevraagde gegevens bevinden zich in de GraphQL-reactie.

<u> Ware resultaten </u>:

* De reactie bevat een *Interne serverfout*.
* `var/log/exception.log` bevat:

  ```
  report.ERROR: Cannot return null for non-nullable field "CompanyTeam.structure_id"
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
