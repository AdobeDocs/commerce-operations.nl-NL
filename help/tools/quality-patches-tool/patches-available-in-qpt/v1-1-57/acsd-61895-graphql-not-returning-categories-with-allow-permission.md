---
title: 'ACSD-61895: [!DNL GraphQL]  categoriequery ontbreekt voor privé gedeelde catalogus met beperkte mening'
description: Pas ACSD-61895 flard toe om de kwestie van Adobe Commerce te bevestigen waar  [!DNL GraphQL]  reacties voor gastklanten (die een openbare gedeelde catalogus met alle toegestane categorieën gebruiken) geen categorieën terugbrachten toen een privé gedeelde catalogus met beperkingen voor de zelfde categorieën werd gecreeerd.
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
source-git-commit: f929f76dbe79c3764e2c157576b4f6db867673cf
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# ACSD-61895: [!DNL GraphQL] `categories` query mislukt voor gedeelde privécatalogus met beperkte weergave

De ACSD-61895-patch verhelpt het probleem dat [!DNL GraphQL] -reacties voor gastklanten (met een openbare gedeelde catalogus met alle toegestane categorieën) geen categorieën retourneren toen een persoonlijke gedeelde catalogus met beperkingen voor dezelfde categorieën werd gemaakt.

Na de moeilijke situatie, keert het alle categorieën met toestemmingen (openbare gedeelde catalogus) voor gastgebruikers toe, zelfs als de wortelcategorie geen toestemming in het werkingsgebied van een privé gedeelde catalogus heeft toegestaan.

Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-61895. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL GraphQL] reacties voor gastklanten (die een openbare gedeelde catalogus met alle toegestane categorieën gebruiken) retourneren geen categorieën wanneer voor dezelfde categorieën een persoonlijke gedeelde catalogus met beperkingen wordt gemaakt.

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce met B2B en monstergegevens.
1. Zorg ervoor dat B2B-functies zijn ingeschakeld.
1. Maak twee gedeelde catalogi: een openbare en een persoonlijke catalogus.

   * Openbare gedeelde catalogus:

      * Wijs alle categorieën toe aan de openbare catalogus.

   * Persoonlijke gedeelde catalogus:

      * Wijs alleen de categorie `Gear` en de onderliggende categorieën toe aan de persoonlijke catalogus.
      * Wijs de privé catalogus aan een testbedrijf toe.

1. Een bedrijfsgebruiker maken:

   * Creeer een gebruiker verbonden aan het testbedrijf met de privé gedeelde catalogus verbonden.
   * Zorg ervoor dat de gebruiker tot de `Gear` categorie en zijn kindcategorieën op de voorzijde slechts kan toegang hebben wanneer het programma wordt geopend.

1. Zoekcategorieën via API:

   * Gebruik de API-client om de volgende [!DNL GraphQL] -query uit te voeren zonder een klanttoken:

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. Bekijk het antwoord en controleer of de categorie `Gear` en andere categorieën worden geretourneerd.
1. Nu vraagcategorieën met een klantenteken:

   * Meld u aan als gebruiker van het testbedrijf.
   * Voer de zelfde [!DNL GraphQL] categoriequery uit, maar omvat het klantenteken voor het programma geopende gebruiker.
   * Bekijk de reactie en controleer of alleen de categorie `Gear` en de onderliggende categorieën worden geretourneerd.


<u> Verwachte resultaten </u>:

Wanneer het vragen als gebruiker van het gastbedrijf, zouden alle categorieën (zoals verwacht) moeten zijn teruggekeerd.

<u> Ware resultaten </u>:

De reactie van de `categories` vraag toont geen categorieën.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

