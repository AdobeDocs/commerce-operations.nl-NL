---
title: 'ACSD-63326: probleem met omleiding van beheerders verhelpen nadat een bestelling van de achterkant is geplaatst'
description: Pas de ACSD-63326-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de beheerder na het plaatsen van een bestelling vanaf de achtergrond wordt omgeleid naar een verbroken pagina.
feature: Orders, Admin Workspace
role: Admin, Developer
source-git-commit: 47603deecdf5ac3e6be18efeef38cba52ec936ec
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63326: probleem met omleiding van beheerders verhelpen nadat een bestelling van de achterkant is geplaatst

De ACSD-63326-patch verhelpt het probleem waarbij de beheerder na het plaatsen van een bestelling vanaf de achtergrond wordt omgeleid naar een verbroken pagina. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-63326. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beheerders worden omgeleid naar een pagina met een verbroken lay-out nadat ze een bestelling voor een klant hebben geplaatst vanaf de achtergrond.

<u> Stappen om </u> te reproduceren:

1. Navigeer naar de sectie **[!UICONTROL Customers]** in het deelvenster Beheer.
1. Selecteer een klant en klik op **[!UICONTROL Edit]** .
1. Klik op de detailpagina van de klant op **[!UICONTROL Create Order]** in het bovenste menu.
1. Selecteer de [!UICONTROL FR French] -winkel en voeg een beschikbaar product toe aan de bestelling.
1. Vul de vereiste gegevens bij het uitchecken in en klik op **[!UICONTROL Get shipping methods and rates]** .
1. Klik **[voorleggen Orde]** om de orde te plaatsen.

<u> Verwachte resultaten </u>:

De beheerder wordt omgeleid naar de ordesbevestiging of bedankt pagina met de correcte lay-out.

<u> Ware resultaten </u>:

De beheerder wordt omgeleid naar een pagina met een verbroken indeling. De lay-out wordt pas gecorrigeerd nadat de pagina is vernieuwd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
