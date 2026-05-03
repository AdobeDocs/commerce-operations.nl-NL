---
title: 'ACSD-62979: Onjuiste winkel-id in de GraphQL-header leidt tot een fatale geheugenfout'
description: Pas de ACSD-62979-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het gebruik van de onjuiste Store-id in de GraphQL-header een fatale geheugenfout veroorzaakt
feature: GraphQL
role: Admin, Developer
exl-id: 832baae1-34b4-4ca8-bfa9-221aa60da67e
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-62979: Onjuiste winkel-id in de GraphQL-header leidt tot een fatale geheugenfout

De ACSD-62979-patch verhelpt het probleem dat het gebruik van de onjuiste Store-id in de GraphQL-header een fatale geheugenfout veroorzaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-62979. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6, 2.4.6-p7, 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee verhelpt u het probleem dat het gebruik van de onjuiste winkel-id in de GraphQL-header een fatale geheugenfout veroorzaakt.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]** ). Schakel **[!UICONTROL Add Store Code to Urls]** in.
1. Voer de query uit onder de GraphQL-query met de onjuiste waarde voor de winkelkoptekst.

```graphql
{
  categoryList(filters: { ids: { eq: "2" } }) {
    uid
    level
    name
    url_path
    image
    children {
      uid
      level
      name
      url_path
      image
      children {
        uid
        level
        name
        url_path
        image
        children {
          uid
          level
          name
          url_path
          image
        }
      }
    }
  }
}
```

<u> Verwachte resultaten </u>:

Foutbericht: &quot;De aangevraagde winkel is niet gevonden. De winkel controleren en het opnieuw proberen&quot;

<u> Ware resultaten </u>:

Fatale fout zoals:

`Allowed memory size of 792723456 bytes exhausted`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
