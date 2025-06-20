---
title: 'MDVA-32776: voorraadstatus niet bijgewerkt met orderplaatsing'
description: De MDVA-32776-patch verhelpt het probleem waarbij de voorraadstatus niet wordt bijgewerkt wanneer een bestelling wordt geplaatst, maar niet wordt verzonden. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 is geïnstalleerd. De patch-id is MDVA-32776. De kwestie is opgelost in Adobe Commerce 2.4.2.
feature: Orders
role: Admin
exl-id: 6f872c72-c96f-4c23-b6df-44e3da3a81c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-32776: voorraadstatus niet bijgewerkt met orderplaatsing

De MDVA-32776-patch verhelpt het probleem waarbij de voorraadstatus niet wordt bijgewerkt wanneer een bestelling wordt geplaatst, maar niet wordt verzonden. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 geïnstalleerd is. De patch-id is MDVA-32776. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.0

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De voorraadstatus wordt niet bijgewerkt wanneer een bestelling wordt geplaatst maar niet verzonden.

<u> Eerste vereisten </u>:

1. De voorraadmodule is geïnstalleerd.
1. De producten van de vertoning uit-van-voorraad worden geplaatst aan *ja*.

   Om te plaatsen, ga **>** Configuratie **>** Catalogus **>** Voorraad **>** Vertoning uit-van-voorraad Producten **= *ja*.**

<u> Stappen om </u> te reproduceren:

1. Maak twee eenvoudige producten met qty = 11 en 22.
1. Maak een gegroepeerd product met de eenvoudige producten die in stap 1 worden gemaakt.
1. Voeg gegroepeerde producten aan de kar toe door één van de producthoeveelheid aan 11 te plaatsen en het andere eenvoudige product uit voorraad te maken.
1. Voltooi het afrekenen en plaats de bestelling.

<u> Verwachte resultaten </u>:

Gegroepeerde producten geven `out-of-stock` -labels weer wanneer bijbehorende eenvoudige producten uit voorraad verdwijnen.

<u> Ware resultaten </u>:

1. Het eenvoudige product met qty = 11 is uit voorraad.
1. Het gegroepeerde product toont geen *uit-van-voorraad* bericht voor het product met hoeveelheid = 11. Alhoewel, geeft het toevoegen van dit product aan het karretje een *uit-van-voorraad* fout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) sectie.
