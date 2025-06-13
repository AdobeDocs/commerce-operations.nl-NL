---
title: 'ACSD-51471: Admin-gebruiker kan geplande update voor gebundeld product niet opslaan'
description: Pas de ACSD-51471-patch toe om het Adobe Commerce-probleem op te lossen waarbij een beheerder geen geplande update kan opslaan voor een gebundeld product dat een eenvoudig product met een geplande update gebruikt.
exl-id: d8134111-63f0-4476-a407-677bda52fa90
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-51471: Admin-gebruiker kan geplande update voor gebundeld product niet opslaan

De ACSD-51471-patch verhelpt het probleem waarbij een beheerder geen geplande update kan opslaan voor een gebundeld product dat een eenvoudig product met een geplande update gebruikt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 wordt geïnstalleerd. De patch-id is ACSD-51471. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruikers kunnen geen geplande update opslaan voor een gebundeld product dat een eenvoudig product gebruikt waarvoor zelf een geplande update beschikbaar is.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Voeg een geplande update voor het eenvoudige product met slechts de *Datum van het Begin* en geen *Datum van het Eind* toe.
1. Nadat de update is toegepast, wijzigt u de SKU van het product.
1. Maak een gebundeld product en voeg het eenvoudige product dat in Stap 1 is gemaakt toe als een onderliggend product.
1. Maak een geplande update voor het gebundelde product om het gebundelde product mogelijk te maken. Verstrek zowel *Datum van het Begin* als *Datum van het Eind* voor de geplande update.
1. Sla de geplande update op.

<u> Verwachte resultaten </u>:

De geplande update is opgeslagen.

<u> Ware resultaten </u>:

De volgende fout komt voor wanneer het bewaren van de geplande update: *het product dat werd gevraagd bestaat niet. Verifieer het product en probeer opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
