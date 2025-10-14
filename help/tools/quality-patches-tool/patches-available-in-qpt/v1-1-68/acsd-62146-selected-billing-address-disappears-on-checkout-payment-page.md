---
title: 'ACSD-62146: Het geselecteerde factuuradres verdwijnt op de betalingspagina voor kassa'
description: Pas de ACSD-62146-patch toe om het Adobe Commerce-probleem op te lossen waarbij het geselecteerde factuuradres verdwijnt op de pagina voor de betaling van betalingen wanneer het zoeken naar adressen is ingeschakeld en de Limiet voor het aantal klantadressen is ingesteld op 1.
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3de3de80383372d0e3bec5485fd65b9d70fe8860
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-62146: Het geselecteerde factuuradres verdwijnt op de betalingspagina voor kassa

De ACSD-62146-patch verhelpt het probleem waarbij het geselecteerde factuuradres verdwijnt op de pagina voor het afrekenen van betalingen wanneer het zoeken naar adressen is ingeschakeld en [!UICONTROL Number of Customer Addresses Limit] is ingesteld op 1. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-62146. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het geselecteerde factuuradres verdwijnt op de betalingspagina voor kassa wanneer adreszoekactie is ingeschakeld en **[!UICONTROL Number of Customer Addresses Limit]** is ingesteld op 1.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** om Zoeken in adressen in te schakelen.
1. Stel **[!UICONTROL Number of Customer Addresses Limit]** in op 1.
1. Maak een klant en voeg twee verschillende adressen toe.
1. Voeg een product toe aan het winkelwagentje en ga verder met het afrekenen.
1. Klik op **[!UICONTROL Change Address]** en wijzig het adres in het pop-upmenu.
1. Selecteer Adres 2 als het verzendadres.
1. Klik op **[!UICONTROL Next]** om door te gaan naar de betalingsstap.
1. Controleer of de facturering en het verzendadres gelijk zijn.
1. Vernieuw de pagina zonder de betaling uit te voeren.

<u> Verwachte resultaten </u>:

Het verzendadres is zichtbaar wanneer de facturering en het verzendadres hetzelfde zijn.

<u> Ware resultaten </u>:

Het standaardfactuuradres en het geselecteerde verzendadres zijn niet zichtbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
