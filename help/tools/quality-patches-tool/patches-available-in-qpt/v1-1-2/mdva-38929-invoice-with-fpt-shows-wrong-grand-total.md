---
title: "MDVA-38929: FPT heeft een onjuist totaal"
description: De patch MDVA-38929 lost het probleem op waarbij de factuur met FPT een onjuist totaal geeft wanneer de bestelling wordt betaald met winkelkrediet. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 is geïnstalleerd. De patch-id is MDVA-38929. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Invoices, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-38929: FPT toont onjuist totaal

De patch MDVA-38929 lost het probleem op waarbij de factuur met FPT een onjuist totaal geeft wanneer de bestelling wordt betaald met winkelkrediet. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 geïnstalleerd is. De patch-id is MDVA-38929. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De factuur met FPT geeft een onjuist totaal als de bestelling wordt betaald met winkelkrediet.

<u> Stappen om </u> te reproduceren:

1. Maak een klant en zorg ervoor dat de klant voldoende krediet heeft om de bestelling te dekken.
1. Schakel FPT in en voeg FPT toe aan een product.
1. Van het vooreind, login zoals de klant enkel creeerde.
1. Voeg het product met FPT toe aan de kar.
1. Afhandeling en betaling met winkelkrediet. Het moet een betalingsopdracht van nul zijn.
1. Ga naar Bestellingen en factureer de bestelling handmatig.
1. Controleer het totaal van de factuur.

<u> Verwachte resultaten </u>:

* Het totaal van de factuur is nul.
* Het totaalbedrag van de bestelling is nul.

<u> Ware resultaten </u>:

* Het totaalbedrag op de factuur toont nog steeds het FPT-bedrag.
* Het betaalde totaalbedrag toont nog steeds het FPT-bedrag.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.