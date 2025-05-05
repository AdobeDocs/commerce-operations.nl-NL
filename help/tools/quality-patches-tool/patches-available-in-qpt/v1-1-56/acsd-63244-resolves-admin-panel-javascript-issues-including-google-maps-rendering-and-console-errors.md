---
title: 'ACSD-63244: Los de kwesties van JavaScript van het admin paneel, met inbegrip van  [!DNL Google Maps]  teruggevende en consolefouten op'
description: ACSD-63244 herstelt de veelvoudige kwesties van JavaScript in het admin paneel, met inbegrip van problemen met  [!DNL Google Maps]  teruggevend en terugkerend "Uncaught TypeError dit._each is not a function&grave; errors in the browser console.
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
source-git-commit: 6b623811440238deee7a7fe859d887830f89782c
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-63244: Los JavaScript-problemen met het deelvenster Beheer op, inclusief [!DNL Google Maps] rendering en consolefouten

De ACSD-63244-patch verhelpt meerdere JavaScript-problemen in het beheerpaneel, zoals problemen met [!DNL Google Maps] rendering en terugkerende `Uncaught TypeError: this._each is not a function` fouten in de browserconsole. Deze patch is beschikbaar bij [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. De patch-id is ACSD-63244. De kwestie zou volgens de planning in Adobe Commerce 2.4.8 worden opgelost.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4, 2.4.4-p9, 2.4.6-p7, 2.4.7

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

* De fout `Uncaught TypeError: this._each is not a function` wordt weergegeven in de browserconsole, waardoor de functionaliteit van de interface van Admin wordt onderbroken.
* JavaScript-fout voorkomt dat [!DNL Google Maps] correct wordt weergegeven.

<u> Stappen om </u> te reproduceren:

1. Laad de gebruikersinterface voor Adobe Commerce-beheer.
1. Open de browserconsole en voer het volgende script uit:

   ```
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u> Verwachte resultaten </u>:

De JavaScript-functies die beschikbaar zijn in de standaard JS-bibliotheek worden correct uitgevoerd zonder fouten.

<u> Ware resultaten </u>:

JavaScript-fouten worden weergegeven in de browserconsole:

```
Uncaught TypeError: this._each is not a function
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
