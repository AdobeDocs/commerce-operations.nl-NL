---
title: 'ACSD-52929: Overbodig verzoek om standaardbronitems opnieuw te indexeren'
description: Pas de markering ACSD-52929 toe om het Adobe Commerce-probleem op te lossen waarbij er een overtollig verzoek is om de standaardbronitems opnieuw te indexeren wanneer de inventarisindexator in de asynchrone modus is geconfigureerd.
feature: Configuration, Inventory
role: Admin, Developer
exl-id: 904aed0e-a6cd-4a0f-949d-bb32fcd77356
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-52929: Overbodig verzoek om standaardbronitems opnieuw te indexeren

De markering ACSD-52929 lost het probleem op waar er een overtolligheid van verzoeken om standaardbronpunten opnieuw te indexeren is wanneer de inventarisindexator op async wijze wordt gevormd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.38 wordt geïnstalleerd. De patch-id is ACSD-52929. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er is een overtolligheid van verzoeken om standaardbronpunten opnieuw te indexeren wanneer de inventarisindexeerder op asynchrone wijze wordt gevormd.

<u> Stappen om </u> te reproduceren:

1. Configureer [!DNL RabbitMQ].
1. Schakel asynchrone herindexstrategie in door naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** en stel **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]** in.
1. Een aangepaste inventarisbron maken.
1. Meld u aan bij het dashboard van [!DNL RabbitMQ] en ga naar het tabblad Wachtrijen.
1. Controleer de `inventory.indexer.sourceItem` wachtrij en controleer of deze geen berichten bevat.
1. Open een eenvoudig product vanaf de achtergrond en voeg *[!UICONTROL stock only]* toe aan de aangepaste bron en sla het product op.
1. Laad de `inventory.indexer.sourceItem` wachtrij in het [!DNL RabbitMQ] -dashboard en controleer de berichten.

<u> Verwachte resultaten </u>:

Er is slechts één bericht in de wachtrij voor de aangepaste bron.

<u> Ware resultaten </u>:

Twee berichten worden getoond in de rij: voor de standaardbron en andere voor de douanebron.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
