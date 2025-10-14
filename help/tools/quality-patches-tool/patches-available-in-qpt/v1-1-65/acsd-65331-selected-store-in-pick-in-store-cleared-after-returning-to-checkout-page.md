---
title: 'ACSD-65331: de geselecteerde opslag in [!UICONTROL Pick in Store] wordt gewist nadat u het uitchecken hebt hersteld'
description: Pas de ACSD-65331-patch toe om het Adobe Commerce-probleem op te lossen waarbij de geselecteerde opslag onder de optie [!UICONTROL Pick In Store] wordt gewist wanneer gebruikers herhaaldelijk terugkeren naar de uitcheckpagina.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
exl-id: 10aaf898-feca-4485-90f6-6b3a9ea013b2
source-git-commit: dc5df9e918adffe8d6901478a676d9da36b33bcc
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-65331: de geselecteerde opslag in **[!UICONTROL Pick in Store]** wordt gewist nadat u het uitchecken hebt hersteld

De ACSD-65331-patch verhelpt het probleem waarbij de geselecteerde opslag onder de optie **[!UICONTROL Pick In Store]** wordt gewist wanneer gebruikers herhaaldelijk terugkeren naar de uitcheckpagina. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 wordt geïnstalleerd. De patch-id is ACSD-65331. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De geselecteerde opslag onder de optie **[!UICONTROL Pick In Store]** wordt gewist wanneer gebruikers herhaaldelijk terugkeren naar de uitcheckpagina.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL In-Store Delivery]** in door naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** te navigeren.
1. Configureer een geldige [!DNL Google] API-sleutel voor [!UICONTROL Google Distance Provider] door naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]** te navigeren.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]** om een nieuwe bron toe te voegen met de volgende details:

   * **[!UICONTROL Latitude]**: *41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *ja*
   * **[!UICONTROL Country]**: *Verenigde Staten*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Carol Stream*
   * **[!UICONTROL Street]**: *565 E. Fullerton Ave.*
   * **[!UICONTROL Postcode]**: *60188*

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]** om een nieuwe voorraad te maken.

   Wijs de nieuwe bron en de hoofdwebsite toe aan deze voorraad.
1. Elk product bewerken en:

   1. Wijs het toe aan de pas gecreëerde bron.
   1. Stel de status in op *[!UICONTROL In Stock]* en op groter dan 0.

1. Voer je herdexers uit.
1. Voor de winkel, creeer een nieuwe klant en plaats een adres van Californië als standaardfacturerings en verschepend adres.
1. Voeg een extra adres van Illinois aan de zelfde klant (niet-gebrek) toe.
1. Voeg het geconfigureerde product toe aan de winkelwagentje en ga verder met **[!UICONTROL Checkout]** .
1. Selecteer het Illinois-adres, kies **[!UICONTROL Pick In Store]** als verzendmethode en klik op **[!UICONTROL Next]** .
1. Wacht tot de bron is geladen en klik op **[!UICONTROL Next]** .
1. Ga terug naar de startpagina.
1. Reviseer de pagina **[!UICONTROL Checkout]** .

<u> Verwachte resultaten </u>:

De geselecteerde opslag moet beschikbaar blijven onder **[!UICONTROL Pick In Store]** .

<u> Ware resultaten </u>:

De verzendstap begint te laden en wordt omgeleid naar **[!UICONTROL Pick In Store]** , maar er is geen winkel zichtbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
