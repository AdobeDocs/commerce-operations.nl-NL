---
title: Vooraf geselecteerde winkel in 'Ophalen in winkel' werkt niet bij wanneer het verzendadres verandert
description: Pas de ACSD-64753-patch toe om het Adobe Commerce-probleem op te lossen waarbij de vooraf geselecteerde winkel niet werd bijgewerkt toen een nieuw verzendadres buiten de serviceradius van de geselecteerde winkel werd ingevoerd.
feature: Inventory
role: Admin, Developer
exl-id: 4efc99d6-88a3-43f9-88d4-dedb9d8a269e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# ACSD-64753: vooraf geselecteerde opslag in &quot;Ophalen in winkel&quot; wordt niet bijgewerkt wanneer het verzendadres verandert

De ACSD-64753-patch verhelpt het probleem waarbij de vooraf geselecteerde winkel niet was bijgewerkt toen een nieuw verzendadres buiten de serviceradius van de geselecteerde winkel werd ingevoerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 wordt geïnstalleerd. De patch-id is ACSD-64753. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De vooraf geselecteerde winkel is niet bijgewerkt toen een nieuw verzendadres werd ingevoerd buiten de serviceradius van de geselecteerde winkel.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL In-Store Delivery]** in door naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** te navigeren.
1. Geef een geldige [!DNL Google] API-sleutel op voor [!DNL Google Distance Provider] . Navigeer hiertoe naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]** .
1. Voeg een nieuwe bron toe (**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]** ) en stel de volgende waarden in:
   * **[!UICONTROL Latitude]**: *-41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *ja*
   * **[!UICONTROL Country United]**: *Staten*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Carol Stream*
   * **[!UICONTROL Postcode]**: *60188*
1. Voeg een nieuwe voorraad toe (**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]** ) en wijs de nieuwe bron en de hoofdwebsite hieraan toe.
1. Bewerk om het even welk product, wijs het product aan nieuwe Source toe, in Voorraad en hoeveelheid > *0*.
1. Wacht tot de redex volledig is.
1. Voor de winkel, creeer een nieuwe klant, en voeg dan een adres van Californië als standaardfacturerings en het verschepen toe.
1. Voeg een ander niet-standaard Illinois adres aan deze klant toe.
1. Voeg het product toe aan het winkelwagentje en ga verder met het afrekenen.
1. Laat het verzendadres van Californië geselecteerd en kies **[!UICONTROL Pick in Store]** verzendmethode. Klik op **[!UICONTROL Next]**.

<u> Verwachte resultaten </u>:

Aangezien het adres van Californië buiten de maximumonderzoeksstraal (200km) is, zou Illinois Source niet aan de klant beschikbaar moeten zijn.

<u> Ware resultaten </u>:

De Illinois-bron kan worden gekozen en de klant kan doorgaan met uitchecken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
