---
title: 'ACSD-66889: Fout tijdens voorraadredex in CLI'
description: Pas de ACSD-66889-patch toe om het Adobe Commerce-probleem dat een fout veroorzaakt, te verhelpen wanneer de inventarisindex wordt uitgevoerd.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9631e0864b2ad8fc09734aedd476e96852cd70fb
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# ACSD-66889: Fout tijdens voorraadredex in CLI

De ACSD-66889-patch verhelpt de fout die optreedt bij het uitvoeren van de inventarisindex. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-66889.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p13

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het runnen van de inventarisindexator, veroorzaakt het proces een afgekeuringswaarschuwing en niet te voltooien wegens verouderde koordsyntaxis.

<u> Stappen om </u> te reproduceren:

1. Voer de voorraadherindex uit gebruikend het CLI bevel:

   ```
   php bin/magento indexer:reindex inventory
   ```

<u> Verwachte resultaten </u>:

CLI herbouwt met succes de inventarisindexeerder.

<u> Ware resultaten </u>:

CLI werpt een verouderde functionaliteit fout, en de inventarisindexen blijven in de *Vereiste* staat opnieuw indexeren:

```
Deprecated Functionality: Using ${var} in strings is deprecated, use {$var} instead in /home/vendor/magento/module-elasticsearch-catalog-permissions/Model/Adapter/FieldMapper/Product/FieldProvider/FieldName/Resolver/CategoryPermission.php on line 24
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
