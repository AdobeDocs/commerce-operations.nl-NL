---
title: 'MDVA-38852: Catalogusinventarislijsten vergrendelen tabellen die de prestaties verminderen'
description: Met de MDVA-38852-patch wordt het probleem opgelost waarbij de catalogusvoorraad tabellen vergrendelt voor updates die de prestaties aanzienlijk verminderen wanneer meerdere parallelle orders worden geplaatst. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 is geïnstalleerd. De patch-id is MDVA-38852. De kwestie is opgelost in Adobe Commerce 2.3.6.
feature: Catalog Management, Inventory, Orders
role: Admin
exl-id: ce93130b-8d96-47b8-96c6-da5988b34ae0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-38852: Catalogusinventarislijsten vergrendelen tabellen die de prestaties verminderen

Met de MDVA-38852-patch wordt het probleem opgelost waarbij de catalogusvoorraad tabellen vergrendelt voor updates die de prestaties aanzienlijk verminderen wanneer meerdere parallelle orders worden geplaatst. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 geïnstalleerd is. De patch-id is MDVA-38852. De kwestie is opgelost in Adobe Commerce 2.3.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Met Catalogusinventarisatie worden tabellen vergrendeld voor updates die de prestaties aanzienlijk verminderen wanneer meerdere parallelle orders worden geplaatst.

<u> Stappen om </u> te reproduceren:

1. Voeg een product toe aan de kar.
1. Ga door met de kassa en probeer een bestelling te plaatsen.

<u> Verwachte resultaten </u>:

* Er zijn geen patstellingen.
* De prestaties worden niet verminderd wanneer meerdere parallelle orders worden geplaatst.

<u> Ware resultaten </u>:

* Het plaatsen van een orde is uiterst langzaam wanneer er veelvoudige gezamenlijke gebruikers zijn.
* Er treden fouten op die er als volgt uitzien:

```SQL
"SQLSTATE[40001]: Serialization failure: 1213 Deadlock found when trying to get lock; try restarting transaction, query was:
INSERT INTO `quote_payment` (`quote_id`, `method`, `additional_information`) VALUES (?, ?, ?)"
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
