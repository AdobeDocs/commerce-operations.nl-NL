---
title: 'ACSD-66212: Het importeren van CSV-bestand van klanten heeft twee keer fouten veroorzaakt bij tweede en volgende pogingen'
description: Pas de ACSD-66212-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het importeren van een CSV-bestand van een klant tweemaal fouten veroorzaakte bij de tweede en volgende poging.
feature: Data Import/Export, Customers
role: Admin, Developer
source-git-commit: 97a5979a189e43b737c44cfe7a65025effae711c
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# ACSD-66212: Het importeren van CSV-bestand van klanten heeft twee keer fouten veroorzaakt bij tweede en volgende pogingen

De ACSD-66212-patch verhelpt het probleem dat het importeren van een CSV-bestand van een klant tweemaal fouten veroorzaakte op de tweede en volgende poging. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 wordt geïnstalleerd. De patch-id is ACSD-66212. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het importeren van een CSV-bestand van een klant heeft tweemaal fouten veroorzaakt bij de tweede en volgende poging.

<u> Stappen om </u> te reproduceren:

Importeer een CSV die klantgegevens bevat, inclusief de status van de klant.

<u> Verwachte resultaten </u>:

De status wordt correct geïmporteerd en geëxporteerd.

<u> Ware resultaten </u>:

Er treedt een fout op tijdens het importeren:

```
General system exception happened
Additional data: <div class="messages"><div class="message message-error error"><div data-ui-id="messages-message-error" >SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near " at line 1, query was: INSERT INTO company_advanced_customer_entity (customer_id*) VALUES </div></div></div>
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
