---
title: 'ACSD-66434: [!UICONTROL Customer ID] het ontbreken van bedrijf  [!DNL GraphQL]  vragen'
description: Pas ACSD-66434 flard toe om de kwestie van Adobe Commerce te bevestigen waar [!UICONTROL Customer ID] van de bedrijf  [!DNL GraphQL]  vragen mist.
feature: B2B, GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 422e5a9eb9948032cccaac98415cf4b92895d5a9
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---


# ACSD-66434: [!UICONTROL Customer ID] ontbreekt in bedrijf [!DNL GraphQL] query&#39;s

De ACSD-66434-patch verhelpt het probleem waarbij **[!UICONTROL Customer ID]** ontbreekt in bedrijf [!DNL GraphQL] -query&#39;s. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 wordt geïnstalleerd. De patch-id is ACSD-66434. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p10 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De [!DNL GraphQL] bedrijfsquery retourneert `null` for the **[!UICONTROL Customer ID]** in de bedrijfsstructuur.

<u> Stappen om </u> te reproduceren:

1. Installeer de Adobe Commerce 2.4-ontwikkeling met B2B- en inventarismodules.
1. Schakel via Commerce Admin B2B-functies in en maak een testbedrijf.
1. Genereer een token voor de bedrijfbeheerder met de volgende [!DNL GraphQL] -mutatie:

```
mutation {
  generateCustomerToken(email: "admin_email@example.com", password: "admin_password") {
    token
  }
}
```

1. Gebruik het gegenereerde token om de bedrijfsstructuur van de klant op te halen met de volgende [!DNL GraphQL] -query:

```
query {
  company {
    id
    name
    legal_name
    structure {
      items {
        entity {
          __typename
          ... on Customer {
            firstname
            lastname
            email
            job_title
            id
          }
        }
      }
    }
  }
}
```

<u> Verwachte resultaten </u>:

**[!UICONTROL Customer ID]** moet worden geretourneerd in de query van het bedrijf [!DNL GraphQL] .

<u> Ware resultaten </u>:

**[!UICONTROL Customer ID]** geeft als `null` in de query van het bedrijf [!DNL GraphQL] .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
