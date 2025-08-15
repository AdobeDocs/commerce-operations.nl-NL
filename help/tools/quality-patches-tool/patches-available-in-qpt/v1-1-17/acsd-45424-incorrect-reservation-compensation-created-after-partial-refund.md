---
title: 'ACSD-45424: Onjuiste reserveringscompensatie na gedeeltelijke terugbetaling'
description: De ACSD-45424-patch verhelpt het probleem dat na een gedeeltelijke terugbetaling een onjuiste reserveringscompensatie wordt gecreëerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 is geïnstalleerd. De patch-id is ACSD-45424. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Orders
role: Admin
exl-id: 94435816-9f4a-40f9-be80-05836ed7781f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424: Onjuiste reserveringscompensatie na gedeeltelijke terugbetaling

De ACSD-45424-patch verhelpt het probleem dat na een gedeeltelijke terugbetaling een onjuiste reserveringscompensatie wordt gecreëerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 geïnstalleerd is. De patch-id is ACSD-45424. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na een gedeeltelijke terugbetaling wordt een onjuiste reserveringscompensatie tot stand gebracht.

<u> Stappen om </u> te reproduceren:

1. Verzendmethode voor in-store levering inschakelen.
1. Maak drie inventarisbronnen en zorg ervoor dat de ophaallocatie actief is in elke bron (bron1, bron2, bron3).
1. Maak een nieuw bestand en wijs de drie bronnen toe aan het nieuwe bestand.
   * Dit bestand moet worden toegewezen aan de hoofdwebsite.
1. Creeer een eenvoudig product, P3, en wijs alle bronnen aan het toe.
1. Voeg de volgende hoeveelheden voor de bronnen van het eenvoudige product toe en laat backorders toe:
   * Standaardbron - 100
   * bron1 - 0
   * bron2 - 10
   * bron3 - 0
1. Voeg het eenvoudige product vanaf de voorkant toe aan de winkelwagentje en ga door naar het verzendformulier.
1. Selecteer &quot;source1&quot; als verzendlocatie.
1. Voltooi de orde en voer de volgende vraag in het gegevensbestand uit:

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   U krijgt de geplaatste record in de `inventory_reservation` -tabel. De hoeveelheid is 10, wat juist is.
1. Factureer deze volgorde vanaf de achterkant.
1. Maak nu een creditmemo voor slechts één product. Selecteer NIET de *Terugkeer aan voorraad* checkbox.
1. Voer de zelfde vraag van Stap 8 uit.

<u> Verwachte resultaten </u>:

Als u niet de *Terugkeer aan Voorraad* tijdens de verwezenlijking van het creditmemo selecteerde, zal de `inventory_reservation` lijst geen verslag hebben die aan het creditmemo beantwoordt.

<u> Ware resultaten </u>:

Alhoewel u niet de *Terugkeer aan Voorraad* tijdens de verwezenlijking van het creditmemo selecteerde, voegt het een verslag aan `inventory_reservation` lijst met `creditmemo_created` gebeurtenistype toe. Bovendien heeft de in de tabel `inventory_reservation` toegevoegde creditmemo-record een hoeveelheid van 10, ook al hebt u de creditmemo voor slechts één hoeveelheid gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
