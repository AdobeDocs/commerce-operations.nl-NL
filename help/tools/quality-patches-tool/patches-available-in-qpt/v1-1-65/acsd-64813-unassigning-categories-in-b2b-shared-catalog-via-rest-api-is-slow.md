---
title: 'ACSD-64813: Het ongedaan maken van categorieën in  [!DNL B2B]  gedeelde catalogus via REST API is langzaam'
description: Pas ACSD-64813 flard toe om de kwestie van Adobe Commerce te bevestigen waar het unsigning van categorieën in a  [!DNL B2B]  gedeelde catalogus via REST API langzaam is.
feature: B2B, REST, Categories
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0ed4bde6d78429da5a375a8c50f6b348db5a5ad5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---


# ACSD-64813: het ongedaan maken van de toewijzing van categorieën in [!DNL B2B] gedeelde catalogus via REST API gaat langzaam

De ACSD-64813-patch verhelpt het probleem dat het verwijderen van de toewijzing van categorieën in een [!DNL B2B] gedeelde catalogus via de REST API traag verloopt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 wordt geïnstalleerd. De patch-id is ACSD-64813. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het verwijderen van de toewijzing van categorieën in een [!DNL B2B] gedeelde catalogus via de REST API gaat langzaam.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL B2B]** , **[!UICONTROL Company]** en **[!UICONTROL Shared Catalog]** in.
1. Genereer 30.000 actieve producten in voorraad.
1. Creeer a [ douane gedeelde catalogus ](https://experienceleague.adobe.com/nl/docs/commerce-admin/b2b/shared-catalogs/catalog-shared#actions-controls) en wijs alle producten aan het toe.
1. Maak een nieuwe categorie onder de standaardhoofdcategorie en wijs er een aantal producten aan toe.
1. Gebruik het beheerdertoken om het REST API-eindpunt `rest/all/V1/sharedCatalog/<shared_catalog_id>/assignCategories` aan te roepen met de nieuwe categorie-id.

```
{
  "categories": [
    { "id": <new category id> }
  ]
}
```

1. Bevestig de reactie *waar* is.
1. Voer `bin/magento cron:run` twee keer uit of voer een nieuwe index uit.
1. Gebruik het beheerdertoken om het REST API-eindpunt `rest/all/V1/sharedCatalog/<shared_catalog_id>/unassignCategories` aan te roepen met de nieuwe categorie-id.

```
{
  "categories": [
    { "id": <new category id> }
  ]
}
```

<u> Verwachte resultaten </u>:

De bewerking moet binnen een redelijke tijd worden voltooid (binnen een paar minuten).

<u> Ware resultaten </u>:

De uitvoering neemt ongeveer 30 minuten in beslag of resulteert in een time-outfout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
