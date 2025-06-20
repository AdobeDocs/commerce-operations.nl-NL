---
title: 'MDVA-41061: Voorraadstatus kan opnieuw worden verkocht wanneer het product wordt opgeslagen bij Admin'
description: De MDVA-41061-patch verhelpt het probleem waarbij de status van de voorraad wordt hersteld naar de verkoopbaarheid wanneer het product wordt opgeslagen bij de Admin. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 is geïnstalleerd. De patch-id is MDVA-41061. De nieuwste patchversie is beschikbaar in QPT 1.1.15 met MDVA-41061-V3 patch-id. De kwestie is opgelost in Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: ddbc30ef-bc88-4878-8bd8-6880823819a2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-41061: Voorraadstatus kan opnieuw worden verkocht wanneer het product wordt opgeslagen bij Admin

De MDVA-41061-patch verhelpt het probleem waarbij de status van de voorraad wordt hersteld naar de verkoopbaarheid wanneer het product wordt opgeslagen bij de Admin. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5 geïnstalleerd is. De patch-id is MDVA-41061. De nieuwste patchversie is beschikbaar in QPT 1.1.15 met MDVA-41061-V3 patch-id. De kwestie is opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van de voorraad kan opnieuw worden verkocht wanneer het product bij de beheerder wordt opgeslagen.

<u> Eerste vereisten </u>:

De inventarismodules worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product met Aantal = 1.
1. Plaats een bestelling met het product dat u in stap 1 hebt gemaakt.
1. Uitsnijden uitvoeren - zorg ervoor dat de `inventory.reservations.updateSalabilityStatus` wachtrij wordt uitgevoerd en de status van de productvoorraad in de `cataloginventory_stock_status` -tabel is gewijzigd in nul.
1. Controleer het product op de voorzijde. Het zou als **uit Voorraad** moeten worden gemerkt.
1. Sla het product zonder wijzigingen op in de Admin.

<u> Verwachte resultaten </u>:

* De voorraadstatus moet niet worden bijgewerkt.
* Het product zou **uit Voorraad** op frontend moeten zijn.

<u> Ware resultaten </u>:

* Het eenvoudige product wordt duidelijk als **in Voorraad** op het front.
* De gebruikers krijgen *de gevraagde hoeveelheid is niet beschikbaar* bericht wanneer het proberen om het aan de kar toe te voegen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
