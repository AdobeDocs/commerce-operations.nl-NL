---
title: 'ACSD-45520: Staalopties zijn niet geselecteerd op de pagina met productdetails'
description: De ACSD-45520-patch verhelpt het probleem dat staalopties niet vooraf zijn geselecteerd op de pagina met productdetails wanneer een gebruiker configureerbare producten bewerkt in het winkelwagentje. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 is geïnstalleerd. De patch-id is ACSD-45520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Products
role: Admin
exl-id: a8b37dba-5a02-45a9-8e43-5288352a9d75
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-45520: Staalopties zijn niet geselecteerd op de pagina met productdetails

De ACSD-45520-patch verhelpt het probleem dat staalopties niet vooraf zijn geselecteerd op de pagina met productdetails wanneer een gebruiker configureerbare producten bewerkt in het winkelwagentje. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 geïnstalleerd is. De patch-id is ACSD-45520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Staalopties worden niet op de pagina met productdetails geselecteerd wanneer een gebruiker configureerbare producten uit de winkelwagentje bewerkt.

<u> Stappen om </u> te reproduceren:

1. Maak een configureerbaar product met productopties (bijvoorbeeld kleur).
1. Voeg het configureerbare product aan de kar toe.
1. Ga naar de pagina Mijn winkelwagentje.
1. Klik op de knop Bewerken op het configureerbare product dat in Stap 1 wordt toegevoegd.
1. Bekijk de productopties op de bewerkingspagina.

<u> Verwachte resultaten </u>:

Er zijn productopties geselecteerd.

<u> Ware resultaten </u>:

Productopties zijn niet geselecteerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
