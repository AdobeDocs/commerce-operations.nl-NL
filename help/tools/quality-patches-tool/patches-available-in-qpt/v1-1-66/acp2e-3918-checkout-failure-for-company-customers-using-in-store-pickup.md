---
title: 'ACP2E-3918: Afhandelingsfout voor klanten van bedrijven die in-store-pickup gebruiken'
description: Pas de ACS2E-3918-patch toe om het Adobe Commerce-probleem op te lossen waarbij het uitchecken mislukt voor aangemelde bedrijfklanten die in-store-pickup gebruiken zonder standaard factureringsadres.
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
source-git-commit: fcbc85eaa6aceb5c02929d5b9dbee24f184c03b4
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACP2E-3918: Afhandelingsfout voor klanten van bedrijven die in-store-pickup gebruiken

De ACS2E-3918-patch verhelpt het probleem waarbij het uitchecken mislukt voor aangemelde bedrijfklanten die in-store-pickup gebruiken zonder een standaardfactureringsadres. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 wordt geïnstalleerd. De patch-id is ACP2E-3918. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Afhandeling mislukt wanneer een klant van een aangemelde onderneming zonder standaardadres een inkooporder probeert te plaatsen met het in-store ophalen.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL Purchase Orders]** in.
1. Maak een **[!UICONTROL Company]** en schakel **[!UICONTROL Purchase Orders]** hiervoor in.
1. Maak een **[!UICONTROL Company User]** zonder opgeslagen adressen.
1. Schakel de verzendmethode **[!UICONTROL In-Store Delivery]** in.
1. Voeg een inventarisbron toe.
1. Voeg een voorraadvoorraad toe.
1. Een product een voorraad toewijzen.
1. Voor frontend, login als bedrijfgebruiker.
1. Voeg producten toe aan **[!UICONTROL Cart]**.
1. Ga door met de kassa.
1. Selecteer **[!UICONTROL In-Store Pick Up]** bij de verzendstap.
1. Ga door met de betaling.

<u> Verwachte resultaten </u>:

De betalingsstap wordt tijdens het uitchecken correct geladen en er worden geen fouten weergegeven in de browserconsole.

<u> Ware resultaten </u>:

De betalingsstap wordt niet geladen en de browserconsole geeft de volgende JavaScript-fout weer:

```
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
