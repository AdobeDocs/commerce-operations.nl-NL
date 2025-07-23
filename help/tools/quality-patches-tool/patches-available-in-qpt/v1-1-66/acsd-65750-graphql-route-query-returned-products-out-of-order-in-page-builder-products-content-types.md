---
title: 'ACSD-65750: [!DNL GraphQL]  "route"vraag keert producten uit orde in  [!DNL Page Builder]  Inhoudstype van Producten terug'
description: Pas ACSD-65750 flard toe om de kwestie van Adobe Commerce te bevestigen waar de "route"vraag van GraphQL producten uit orde in  [!DNL Page Builder]  inhoudstype van Producten terugkeert.
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 2555327c02985a51e7f34a36dd256227b12b5924
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-65750: [!DNL GraphQL] &quot;route&quot;-query retourneert producten in [!DNL Page Builder] Productinhoudstype

De ACSD-65750-patch verhelpt het probleem waarbij de query [!DNL GraphQL] &quot;route&quot; producten in volgorde retourneert in [!DNL Page Builder] Producten-inhoudssoort. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 wordt geïnstalleerd. De patch-id is ACSD-65750. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De query [!DNL GraphQL] &quot;route&quot; retourneert geen producten in de juiste sorteervolgorde wanneer u het inhoudstype [!DNL Page Builder] Producten gebruikt.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe categorie en enkele producten in de catalogus en koppel de producten aan deze categorie.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** , bewerk de gemaakte categorie en open het tabblad **[!UICONTROL Products in Category]** .
1. Stel de aangepaste waarde **[!UICONTROL Position]** in voor elk product in deze categorie.
1. Sla de categorie op en voer de herindex uit.
1. Navigeer naar **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]** en klik op **[!UICONTROL Add New Page]** .
1. Vouw het tabblad **[!UICONTROL Content]** uit en klik op **[!UICONTROL Edit with Page Builder]** .
1. Sleep een **[!UICONTROL Row]** -element naar het inhoudsgebied en sleep vervolgens een **[!UICONTROL Products]** -element in de rij.
1. Vorm het element van Producten als volgt:
   * **[!UICONTROL Select Products By]**: *Categorie*
   * **[!UICONTROL Category]**: *selecteer de pas gecreëerde categorie*
   * **[!UICONTROL Sort By]**: *Positie*
1. Schakelaar aan het **[!UICONTROL Search Engine Optimization]** lusje, en plaats **[!UICONTROL URL Key]** aan *test-widget*.
1. Sla de pagina op.
1. Voer de volgende [!DNL GraphQL] aanvraag uit:

```
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u> Verwachte resultaten </u>:

Het systeem retourneert producten in de volgorde die wordt gedefinieerd door de positie van de categorie.

<u> Ware resultaten </u>:

Het systeem retourneert producten in een volgorde die niet overeenkomt met hun categoriepositie in het GraphQL-antwoord.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
