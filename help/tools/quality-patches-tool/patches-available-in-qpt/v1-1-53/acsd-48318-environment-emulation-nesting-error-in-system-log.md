---
title: '"ACSD-48318: Omgevingsnestfout in ` system.log`'
description: Pas de ACSD-48318-patch toe om het Adobe Commerce-probleem op te lossen waarbij een foutbericht *main.ERROR:Environment emulation nesting is not allowed* weergegeven wordt in ` system.log` telkens wanneer een factuur-e-mail wordt verzonden.
feature: System, Orders
role: Admin, Developer
source-git-commit: 94b68d18bc46065b5803a2eb88f0e844f71f0386
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-48318: Fout bij nesten van emulatie in omgeving in `system.log`

ACSD-48318 herstelt de flard de kwestie waar een foutenmelding *main.ERROR:Het nestelen van de wedijver van het Milieu niet wordt toegestaan* verschijnt in `system.log` telkens als een factuur e-mail wordt verzonden. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 wordt geïnstalleerd. De patch-id is ACSD-48318. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het foutenbericht *het nesten van de wedijver van het Milieu wordt niet toegestaan* verschijnt in `system.log` telkens als een factuur e-mail wordt verzonden.

<u> Stappen om </u> te reproduceren:

1. Plaats een bestelling en G een factuur.
1. Open de factuur van Admin en klik op **[!UICONTROL Send Email]** .
1. Volg de zelfde stap voor *creditmemo* en *lading* door **[!UICONTROL Send Email]** te klikken.

<u> Verwachte resultaten </u>:

Geen fouten in `system.log`.

<u> Ware resultaten </u>:

`system.log` wordt overstroomd met *main.ERROR: Het nesten van de wedijver van het milieu wordt niet toegestaan* fout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

[[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
