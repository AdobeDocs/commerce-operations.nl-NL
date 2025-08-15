---
title: 'ACSD-65848: Categorieën in beheer laden zeer langzaam'
description: Pas de ACSD-65848-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het totale aantal producten in een categorie werd berekend met behulp van een subselectie, waardoor de laadtijd van de categorie werd vertraagd.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: 0233db9b-86b1-4320-a566-7e7e207dab84
source-git-commit: 1ccb4c1dda5141934e04509b27fdafbfdc436a15
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-65848: Categorieën in beheer laden zeer langzaam

De ACSD-65848-patch verhelpt het probleem waarbij het totale aantal producten in een categorie werd berekend aan de hand van een subselectie, die de laadtijd van de categorie vertraagde. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 wordt geïnstalleerd. De patch-id is ACSD-65848. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De weergave-/bewerkingspagina van de categorie Admin heeft aanzienlijke vertraging bij het laden. De vertraging wordt veroorzaakt door de methode die wordt gebruikt om de totale producttelling in een categorie te berekenen, die op een sub-select vraag baseert. Het raffineren van deze logica om te gebruiken toetreedt in plaats daarvan verbetert prestaties en vermindert ladingstijd.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe Adobe Commerce Cloud-instantie met versie 2.4.8.
1. Maak 2.500 categorieën en ten minste 10.000 producten:
   1. Kopieer de map `setup/performance-toolkit` naar `./var` zodat u de profielen kunt bewerken.
   1. Open het `small.xml` -profiel en werk dit bij zodat het 2.500 categorieën en 250.000 producten bevat (zodat het overeenkomt met de setup van de leverancier).
   1. Voer de volgende opdracht uit om de correcties te genereren:

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. Nadat de producten en categorieën zijn gemaakt, moet u ervoor zorgen dat alle categorieën als ankers zijn ingesteld. Deze SQL-query uitvoeren:

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. Maak in het deelvenster Beheer een diepere categoriestructuur:
   * Verplaats categorie 2 onder categorie 1 om deze dieper in de boomstructuur te nesten.
1. Probeer een categoriepagina in het deelvenster Beheer te openen met bijvoorbeeld een URL:
   ```/admin/catalog/category/edit/id/xx/```

<u> Verwachte resultaten </u>:

Elke rubriekpagina wordt geopend bij de eerste poging binnen een paar seconden.

<u> Ware resultaten </u>:

Het duurt langer dan een minuut om rubriekpagina&#39;s te openen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
