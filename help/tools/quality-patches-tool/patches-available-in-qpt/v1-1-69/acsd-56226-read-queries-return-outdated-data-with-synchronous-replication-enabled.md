---
title: 'ACSD-56226: De vragen van de LEZING keren verouderde gegevens met toegelaten &grave; synchrone_replication terug'
description: Pas ACSD-56226 flard toe om de kwestie van Adobe Commerce te bevestigen waar de vragen van de LEZING verouderde gegevens terugkeren wanneer de markering &grave; synchronous_replication &grave; voor slave verbinding op Cloud wordt toegelaten.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: a45cef14b7b37f1112d2ef82adf29b09d63b8e2b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# ACSD-56226: READ-query&#39;s retourneren verouderde gegevens met `synchronous_replication` ingeschakeld

De ACSD-56226-patch verhelpt het probleem waarbij READ-query&#39;s verouderde gegevens retourneren wanneer de `synchronous_replication` -vlag is ingeschakeld voor slave-verbinding op de cloud. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-56226. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

READ-query&#39;s retourneren verouderde gegevens wanneer de markering `synchronous_replication` is ingeschakeld. Hierdoor wordt de slave-verbinding uitgeschakeld, wat leidt tot databaseoverbelasting.

<u> Stappen om </u> te reproduceren:

1. Plaats `MYSQL_USE_SLAVE_CONNECTION` aan *waar* in de milieuvariabelen op Adobe Commerce op wolkeninfrastructuur.
1. Voeg de volgende configuratie aan `.magento.env.yaml` toe om `synchronous_replication` aan *vals* te plaatsen:

   ```
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. Herstel en voer frontend acties zoals login uit, voeg aan karretje toe, of plaats een orde.

<u> Verwachte resultaten </u>:

De verbinding van de slave blijft toegelaten wanneer `synchronous_replication` aan *vals* wordt geplaatst.

<u> Ware resultaten </u>:

De verbinding van de slave wordt onbruikbaar gemaakt wanneer `synchronous_replication` aan *vals* wordt geplaatst, veroorzakend gegevensbestandoverbelasting.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
