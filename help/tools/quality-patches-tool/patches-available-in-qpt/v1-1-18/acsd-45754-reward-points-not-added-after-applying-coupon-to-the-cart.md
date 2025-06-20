---
title: 'ACSD-45754: Achterwaartse punten niet toegevoegd na het toepassen van coupon op winkelwagentje'
description: De ACSD-45754-patch lost de kwestie op waarbij geen bonuspunten worden toegevoegd nadat een coupon op de wagen is aangebracht. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 is geïnstalleerd. De patch-id is ACSD-45754. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Orders, Rewards, Shopping Cart
role: Admin
exl-id: 02f3bfc4-440b-4d77-adf5-0824d1b21073
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-45754: Achterwaartse punten niet toegevoegd na het toepassen van coupon op winkelwagentje

De ACSD-45754-patch lost de kwestie op waarbij geen bonuspunten worden toegevoegd nadat een coupon op de wagen is aangebracht. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 geïnstalleerd is. De patch-id is ACSD-45754. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Retourpunten worden niet toegevoegd na het toepassen van een coupon op de winkelwagentje.

<u> Eerste vereisten </u>:

PayPal-betalingsmethode is geconfigureerd.

<u> Stappen om </u> te reproduceren:

1. Creeer de wisselkoersen van het beloningspunt door naar **opslag** > **Andere Montages** > **Ware Tarieven van de Uitwisseling** te gaan.
1. Maak een prijsregel voor winkelwagentjes met een couponcode om 100 bonuspunten toe te passen voor aangemelde klanten.
1. Bekijk een product als aangemelde klant met PayPal en de waardeboncode.
1. Controleer de bonusgeschiedenis onder de klantenrekening in admin.

<u> Verwachte resultaten </u>:

De punten van beloningen worden toegevoegd aan de klant volgens de prijsregel.

<u> Ware resultaten </u>:

Er worden geen bonuspunten aan de klant toegevoegd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
