---
title: 'ACSD-65822: bundel en configureerbare producthoeveelheden die niet correct in het winkelwagentje zijn weergegeven'
description: Pas de ACSD-65822-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de hoeveelheid in het gedeelte Winkelwagentje van de klant in het beheerpaneel als 0 werd weergegeven bij het toevoegen van bundelproducten.
feature: Admin Workspace, Checkout, Orders
role: Admin, Developer
source-git-commit: d8421ba07a5d2fa3a3174541ed8cd6a2bc76f157
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---


# ACSD-65822: bundel en configureerbare producthoeveelheden die niet correct worden weergegeven in de [!UICONTROL Shopping Cart]

De ACSD-65822-patch verhelpt het probleem waarbij bundel- en configureerbare producthoeveelheden niet correct worden weergegeven in de sectie **[!UICONTROL Shopping Cart]** onder *[!UICONTROL Customer's Activities]* . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 wordt geïnstalleerd. De patch-id is ACSD-65822. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De bundel en configureerbare producthoeveelheden worden niet correct weergegeven in de sectie **[!UICONTROL Shopping Cart]** onder *[!UICONTROL Customer's Activities]* .

<u> Stappen om </u> te reproduceren:

1. Maak een gebruiker in de winkel.
2. Maak een **[!UICONTROL Bundle product]** in het deelvenster Beheer.
3. Voeg op de winkel, als aangemelde gebruiker, het bundelproduct met een bepaalde hoeveelheid toe aan het winkelwagentje.
4. In het *Admin* paneel, ga naar **[!UICONTROL Customers]** en klik **[!UICONTROL Edit]** voor de klant die in Stap 1 wordt gecreeerd.
5. Klik op **[!UICONTROL Create Order]**.
6. Controleer links onder *[!UICONTROL Customer's Activities]* de sectie **[!UICONTROL Shopping Cart]** . U moet het bundelproduct samen met de geselecteerde hoeveelheid zien.

<u> Verwachte resultaten </u>:

De hoeveelheid van het bundelitem moet overeenkomen met de hoeveelheid die in de winkel wordt weergegeven.

<u> Ware resultaten </u>:

Het volume van het bundelitem wordt weergegeven als 0.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
