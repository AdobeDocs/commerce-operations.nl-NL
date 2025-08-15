---
title: 'ACSD-52398: Gevraagde hoeveelheid is niet beschikbaar wanneer wordt geprobeerd de hoeveelheid gebundeld product bij te werken'
description: Pas de ACSD-52398-patch toe om het Adobe Commerce-probleem op te lossen wanneer de gevraagde hoeveelheid niet beschikbaar is wanneer wordt geprobeerd de hoeveelheid van een gebundeld product in het winkelwagentje bij te werken.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 75fa5f96-22e7-40a2-8b8a-f44452e5124d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52398: Gevraagde hoeveelheid is niet beschikbaar wanneer wordt geprobeerd de hoeveelheid gebundeld product bij te werken

De ACSD-52398-patch verhelpt het probleem dat de gevraagde hoeveelheid niet beschikbaar is wanneer wordt geprobeerd de hoeveelheid van een gebundeld product in het winkelwagentje bij te werken. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-52398. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gevraagde hoeveelheid is niet beschikbaar wanneer wordt geprobeerd de hoeveelheid van een gebundeld product in het winkelwagentje bij te werken.

<u> Stappen om </u> te reproduceren:

1. Creeer twee eenvoudige producten met hoeveelheid *1* en *10*.
1. Maak een gebundeld product met de eenvoudige producten.
1. Voeg het gebundelde product aan de kar toe.
1. Bewerk het product en probeer om de hoeveelheid aan *3* voor de optie bij te werken waar *10* punten beschikbaar zijn.

<u> Verwachte resultaten </u>:

Er is geen fout. De hoeveelheid wordt met succes bijgewerkt aangezien er *10* punten in voorraad voor deze optie zijn.

<u> Ware resultaten </u>:

De volgende fout wordt geworpen: *de gevraagde hoeveelheid is niet beschikbaar*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
