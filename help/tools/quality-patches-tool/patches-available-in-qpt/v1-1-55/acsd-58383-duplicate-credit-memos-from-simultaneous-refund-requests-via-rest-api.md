---
title: 'ACSD-58383: Dubbele creditnota''s van gelijktijdige terugbetalingsverzoeken via  [!DNL REST API]'
description: Pas ACSD-58383 flard toe om de kwestie van Adobe Commerce te bevestigen waar het uitgeven van een restitutie via  [!DNL REST API]  met twee identieke verzoeken die gelijktijdig worden uitgevoerd, tot dubbele creditmemo's leidt.
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
source-git-commit: 28390659fe180180c9b2c8d16239008a1f8a510b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-58383 Adobe Commerce-patch: dubbele creditnota&#39;s van gelijktijdige verzoeken om terugbetaling via [!DNL REST API]

De ACSD-58383-patch verhelpt het probleem dat het uitgeven van een restitutie via de [!DNL REST API] met twee identieke verzoeken die tegelijkertijd worden uitgevoerd, resulteert in dubbele creditmemo&#39;s.

Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-58383. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Dubbele creditmemo&#39;s zijn het resultaat van twee restituties die tegelijkertijd zijn gemaakt.

<u> Stappen om </u> te reproduceren:

1. Configureer [!DNL Paypal Express] in de Commerce [!UICONTROL Admin] .
1. Plaats betalingsactie aan *Verkoop*.
1. Configureer de [!DNL PayPal] IPN (Instant Payment Notification) op de [!DNL PayPal] Sandbox-website.
1. Restitutie uitvoeren op de website van de [!DNL PayPal] sandbox.
1. Emuleer een IPN-bericht vanuit [!DNL PayPal] met behulp van ontwikkelaarsgereedschappen. IPN moet een creditnota tot stand brengen.
1. Maak een tweede creditmemo met een [!DNL API] oproep.

<u> Verwachte resultaten </u>:

Er wordt slechts één creditmemo gemaakt voor hetzelfde object.


<u> Ware resultaten </u>:

Voor hetzelfde object worden twee creditmemo&#39;s gemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
