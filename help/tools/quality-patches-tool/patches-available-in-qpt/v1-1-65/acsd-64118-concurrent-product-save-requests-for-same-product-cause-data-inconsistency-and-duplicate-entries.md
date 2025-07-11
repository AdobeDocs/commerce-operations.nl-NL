---
title: 'ACSD-64118: Gelijktijdige opslagaanvragen voor hetzelfde product veroorzaken inconsistentie van gegevens en dubbele vermeldingen'
description: Pas de ACSD-64118-patch toe om het Adobe Commerce-probleem op te lossen waarbij gelijktijdige aanvragen om hetzelfde product op te slaan en bij te werken leiden tot inconsistentie van gegevens of gedupliceerde producten.
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4235511ccbef028e1564d7626daadaa5beae0fd4
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ACSD-64118: Gelijktijdige opslagaanvragen voor hetzelfde product veroorzaken inconsistentie van gegevens en dubbele vermeldingen

De ACSD-64118-patch verhelpt het probleem waarbij gelijktijdige aanvragen om hetzelfde product op te slaan en bij te werken leiden tot inconsistentie van gegevens of gedupliceerde producten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 wordt geïnstalleerd. De patch-id is ACSD-64118. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p7

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gelijktijdige aanvragen om hetzelfde product op te slaan en bij te werken, leiden tot inconsistentie van gegevens of tot dubbele producten.

<u> Stappen om </u> te reproduceren:

1. Meerdere processen voor consumenten instellen in `env.php` :

   ```
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. Voeg een extra winkel en een nieuwe voorvertoning toe aan de hoofdwebsite.
1. Verzend een bulk API verzoek naar het standaardstoreview eindpunt `/rest/default/async/bulk/V1/products` met de volgende nuttige lading om een product tot stand te brengen:

   ```
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. Gebruik dezelfde payload om een bulkaanvraag voor een API naar het nieuwe opslagrevisieeindpunt `/rest/store/async/bulk/V1/products` te verzenden om het product bij te werken.
1. Cachegeheugen leegmaken.
1. Snijtaken uitvoeren.
1. Controleer in de tabel `catalog_product_entity` of het product uit de vorige stappen is ingevoerd.

<u> Verwachte resultaten </u>:

* Eén item voor de product-SKU moet aanwezig zijn in de tabel `catalog_product_entity` .
* Bij de eerste REST API-aanvraag moet één database-item worden gemaakt en bij alle volgende aanvragen moet die database-vermelding worden bijgewerkt.

<u> Ware resultaten </u>:

De tabel `catalog_product_entity` bevat meerdere items voor dezelfde SKU.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
