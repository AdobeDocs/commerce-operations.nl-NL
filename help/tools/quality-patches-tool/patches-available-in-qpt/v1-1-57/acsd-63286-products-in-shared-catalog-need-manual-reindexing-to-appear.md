---
title: 'ACSD-63286: producten die zijn toegewezen aan een gedeelde catalogus, moeten handmatig opnieuw worden gecompileerd om te worden weergegeven'
description: Pas de ACSD-63286-patch toe om het Adobe Commerce-probleem op te lossen waarbij producten die via API aan een gedeelde catalogus zijn toegewezen, pas op de winkel worden weergegeven als een handmatige herindex is uitgevoerd.
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-63286: producten die zijn toegewezen aan een gedeelde catalogus, moeten handmatig opnieuw worden gecompileerd om te worden weergegeven

De ACSD-63286-patch verhelpt het probleem dat producten die via API aan een gedeelde catalogus zijn toegewezen, pas op de opslagplaats worden weergegeven als een handmatige herindex wordt uitgevoerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-63286. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer producten via API aan een gedeelde catalogus worden toegewezen, worden ze niet op de voorgrond weergegeven nadat de gedeeltelijke indexeerfunctie en de snijtaken van de consument zijn uitgevoerd. Ze worden echter wel weergegeven na een handmatige volledige redex.

<u> Stappen om </u> te reproduceren:

1. Stel [!DNL RabbitMQ] in als de service in de wachtrij.
1. Maak een gedeelde catalogus en wijs er een bedrijf aan toe.
1. Maak een eenvoudig product en wijs het toe aan een categorie.
1. Gedeeltelijke redex uitvoeren.

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Gebruik de volgende API-aanvraag om het gemaakte product toe te wijzen aan de gedeelde catalogus `pub/rest/all/V1/sharedCatalog/<id>/assignProducts` :

   ```
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Voer de volgende uitsnede uit om de rijen te wissen en de gedeeltelijke herdex uit te voeren.

   ```
   bin/magento cron:run --group=consumers
   ```

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Meld u als bedrijfsgebruiker aan bij de frontend.
1. Controleer de voorste categoriepagina. De nieuw toegewezen producten zijn niet zichtbaar.
1. Een handmatige herindex uitvoeren:

   ```
   bin/magento index:reindex
   ```

<u> Verwachte resultaten </u>:

Het product verschijnt op de voorzijde zonder een handmatige herdex.

<u> Ware resultaten </u>:

Het product wordt alleen op de voorzijde weergegeven na handmatige herdex.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
