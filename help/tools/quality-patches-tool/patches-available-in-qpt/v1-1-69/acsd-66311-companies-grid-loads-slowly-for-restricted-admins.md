---
title: 'ACSD-66311: Het raster van bedrijven wordt traag geladen voor gebruikers met beperkte beheerfuncties'
description: Pas de ACSD-66311-patch toe om het Adobe Commerce-probleem op te lossen, waarbij bedrijven het raster langzaam laden voor beheerders met beperkte toegang tot websites.
role: Admin, Developer
feature: B2B
type: Troubleshooting
source-git-commit: 841e660136354800dd9758d8c10e86c966be3a1e
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---


# ACSD-66311: Het raster van bedrijven wordt traag geladen voor gebruikers met beperkte beheerfuncties

De ACSD-66311-patch verhelpt het probleem dat het bedrijfsraster traag wordt geladen voor beheerders met beperkte toegang tot de website. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-66311. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het bedrijfsraster wordt langzaam geladen voor beheerders met beperkte toegang tot de website.

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce met **[!UICONTROL B2B features]** .
1. Maak twee extra websites (naast de hoofdwebsite) met winkels/weergaven:
   * Hoofdwebsite (gemaakt tijdens installatie)
   * Website 2 → Store 2 → StoreView 2
   * Website 3 → Store 3 → StoreView 3
1. Maak de gebruikersrol **[!UICONTROL Admins in Scope]** :
   * Werkingsgebied: slechts twee opslag: *Belangrijkste Website* + *Website 3/Opslag 3*.
   * Middelen: slechts *dashboard* + *Bedrijven*.
1. Creeer een admingebruiker met een rol **[!UICONTROL Admins in Scope]**, bijvoorbeeld, **adminscope**.
1. Genereer specifieke gedistribueerde klant- en bedrijfsgegevens:
   1. **Klanten die aan websites** worden toegewezen

      | Website-id | Aantal klanten |
      |------------|---------------------|
      | 1 | 600.000 |
      | 2 | 1.500 |
      | 3 | 500 |


   1. Voer de volgende query uit om de distributie te verifiëren:

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **Klanten die aan bedrijven** worden toegewezen

      | Aantal klanten | Aantal ondernemingen |
      |---------------------|---------------------|
      | 1 | 4.500 |
      | 2 | ~1.000 |
      | ~595k | 1 |

   1. Voer de volgende query uit om de distributie te verifiëren:

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
      
            SELECT company_id, COUNT(customer_id) AS customer_count
            VAN bedrijf_advanced_customer_entiteit
            GROEP OP bedrijf_id
) AS-subquery
GROEP OP klant_count
ORDER BY customer_count;
&quot;

1. Herindexeer alle gegevens om ingangen in **te produceren customer_grid_flat**.
1. Login als **adminscope**.
1. Ga naar **[!UICONTROL Customers]** > **[!UICONTROL Companies]** .

<u> Verwachte resultaten </u>:

De pagina wordt in minder dan 1 seconde geladen.

<u> Ware resultaten </u>:

Het laden van de pagina duurt meer dan 14 minuten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
