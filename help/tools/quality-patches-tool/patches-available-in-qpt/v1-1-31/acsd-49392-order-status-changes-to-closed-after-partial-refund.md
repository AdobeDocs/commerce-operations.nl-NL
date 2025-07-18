---
title: 'ACSD-49392: Wijzigingen in de status van bestellingen die na gedeeltelijke terugbetaling worden gesloten'
description: Pas de ACSD-49392-patch toe om het Adobe Commerce-probleem op te lossen waarbij de status van de order verandert in gesloten na een gedeeltelijke terugbetaling voor een gebundeld product.
feature: Orders
role: Admin
exl-id: e12cbf2d-219e-4cb5-a226-6c7ae4929549
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49392: Wijzigingen in de status van bestellingen die na gedeeltelijke terugbetaling worden gesloten

>[!NOTE]
>
>De flard ACSD-49392 werd vervangen met flard [ ACSD-57003 ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-57003-order-status-changed-to-complete-instead-of-processing) voor versies 2.4.6-p7 aan 2.4.6-p10.

De ACSD-49392-patch verhelpt het probleem waarbij de status van de bestelling verandert in gesloten na een gedeeltelijke terugbetaling voor een gebundeld product. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.31 wordt geïnstalleerd. De patch-id is ACSD-49392. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.3.7-p4 en 2.4.1 - 2.4.6-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De status van de bestelling verandert in gesloten na een gedeeltelijke terugbetaling voor een gebundeld product.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij Adobe Commerce en maak een gebundeld product of gebruik het bestaande gebundelde product.
1. Plaats een bestelling met dit gebundelde product met een hoeveelheid groter dan 1.
1. Ga naar Beheer, open de volgorde die u in stap 2 hebt gemaakt via **[!UICONTROL Sales]** > **[!UICONTROL Order]** en maak een factuur. Bekijk de status van de order. Het wordt verwerkt.
1. Maak een gedeeltelijke creditnota (verbeter niet alle producten in de bundel).
1. Controleer de orderstatus.

<u> Verwachte resultaten </u>

Nadat u een gedeeltelijke creditnota voor het gebundelde product hebt gemaakt, wordt de status van de bestelling verwerkt.

<u> Ware resultaten </u>

Na het maken van een gedeeltelijke creditnota voor het gebundelde product, is de ordestatus volledig.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
