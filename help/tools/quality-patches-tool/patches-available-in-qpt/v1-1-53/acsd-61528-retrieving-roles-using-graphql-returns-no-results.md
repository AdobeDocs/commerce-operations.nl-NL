---
title: "ACSD-61528: Het ophalen van rollen met GraphQL retourneert geen resultaten"
description: Pas de ACSD-61528-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het ophalen van rollen van de beheerder van het bedrijf met GraphQL altijd een null-resultaat oplevert.
feature: GraphQL, B2B, Companies, Roles/Permissions
role: Admin, Developer
source-git-commit: 4a02bb524fd8d1caae02d909bc9f2e3fc0112042
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61528: Het ophalen van rollen met GraphQL retourneert geen resultaten

Het ACSD-61258 flard lost de kwestie op waar het terugwinnen van rollen van de beheerder van het bedrijf gebruikend GraphQL altijd een ongeldig resultaat terugkeert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 wordt geïnstalleerd. De patch-id is ACSD-61528. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6-p5

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het terugwinnen van rollen van de beheerder van het bedrijf gebruikend GraphQL, was het rolresultaat altijd ongeldig.

<u> Eerste vereisten:</u>:

Adobe Commerce B2B-modules installeren en inschakelen.

<u> Stappen om </u> te reproduceren:

1. Maak een bedrijf.
1. Meld u aan als bedrijfsleider op GraphQL met onderstaande mutatie:

   ```GraphQL
      mutation {
          generateCustomerToken(email: "company@admin.com", password: "PASSWORD") {
      token
      }
   }
   ```

1. Voeg het resulterende teken aan **Vergunning** verzoekkopballen als a `Bearer` teken toe en looppas onder de vraag van GraphQL:

   ```GraphQL
      {
      customer {
      email
      role{
       name
       id
      }
    }
   }
   ```

<u> Verwachte resultaten </u>:

De GraphQL-query retourneert de rol.

<u> Ware resultaten </u>:

De rol voor het bedrijf is ongeldig.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.