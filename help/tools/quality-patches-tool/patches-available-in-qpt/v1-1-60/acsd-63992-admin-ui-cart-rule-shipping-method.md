---
title: 'ACSD-63992: [!UICONTROL Cart Price Rule] met fout bij de coupon- en verzendmethode in de beheerinterface'
description: Pas de ACSD-63992-patch toe om het Adobe Commerce-probleem op te lossen, waarbij [!UICONTROL Cart Price Rule] met een coupon en een voorwaarde op basis van een verzendmethode niet correct kan worden toegepast via de beheerinterface.
feature: Price Rules, Admin Workspace
role: Admin, Developer
exl-id: 80f407c7-4552-4cfb-96ae-43773d2ec398
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-63992: [!UICONTROL Cart Price Rule] met fout bij de coupon- en verzendmethode in de beheerinterface

De ACSD-63992-patch verhelpt het probleem waarbij [!UICONTROL Cart Price Rule] met een coupon en een voorwaarde op basis van een verzendmethode niet correct kan worden toegepast via de beheerdersinterface. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 wordt geïnstalleerd. De patch-id is ACSD-63992. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een tekenregel een voorwaarde voor de verzendmethode bevat in de sectie **[!UICONTROL Conditions]** , is de bijbehorende couponcode niet van toepassing wanneer u een order maakt via het deelvenster Beheer. In plaats daarvan geeft het systeem de volgende fout weer:

_De &lt;> couponcode is niet geldig. Verifieer de code en probeer opnieuw._

<u> Stappen om </u> te reproduceren:

1. Maak een regel voor de kartprijs en beschrijf de voorwaarden ervan:
   * Onder *[!UICONTROL Conditions]*: voeg een voorwaarde toe om de verzendmethode op te nemen (bijvoorbeeld *[!UICONTROL Flat Rate]* ).
   * Onder *[!UICONTROL Rule Information]*: Plaats **[!UICONTROL Coupon]** aan *[!UICONTROL Specific Coupon]* en ga dan **[!UICONTROL Coupon Code]** als *TEST* in.
1. Creeer een nieuwe orde van het Comité Admin en ga de couponcode *TEST* op het **[!UICONTROL Apply Coupon]** gebied in.

<u> Verwachte resultaten </u>:

De coupon wordt toegepast.

<u> Ware resultaten </u>:

Het volgende foutbericht wordt weergegeven:

```
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
