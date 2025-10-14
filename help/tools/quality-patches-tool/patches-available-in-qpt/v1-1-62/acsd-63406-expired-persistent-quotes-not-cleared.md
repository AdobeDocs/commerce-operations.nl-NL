---
title: 'ACSD-63406: Verlopen permanente aanhalingstekens niet gewist wanneer de persistente_clear_expired cron-taak wordt uitgevoerd'
description: Pas de ACSD-63406-patch toe om het Adobe Commerce-probleem op te lossen waarbij de verlopen permanente aanhalingstekens niet worden gewist door een uitsnijdtaak wanneer de 'persistent_clear_expired''-uitsnijdtaak wordt uitgevoerd.
feature: Quotes, Shopping Cart
role: Admin, Developer
exl-id: 795d1ddf-0d5b-406c-870b-36cb92cf07fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-63406: Verlopen permanente aanhalingstekens worden niet gewist wanneer de `persistent_clear_expired` snijtaak wordt uitgevoerd

De ACSD-63406-patch verhelpt het probleem dat verlopen permanente aanhalingstekens niet worden gewist door een uitsnijdtaak wanneer de `persistent_clear_expired` -uitsnijdtaak wordt uitgevoerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 wordt geïnstalleerd. De patch-id is ACSD-63406. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Verlopen permanente aanhalingstekens worden door geen enkele snijtaak gewist wanneer de `persistent_clear_expired` -snijtaak wordt uitgevoerd.

<u> Stappen om </u> te reproduceren:

1. Maak een categorie en een product.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** .
   1. Plaats alle opties aan *ja*.
   1. Plaats **[!UICONTROL Persistence Lifetime (seconds)]** aan *60*.
1. Maak een klantenaccount op de winkel en meld u aan.
1. Voeg een product toe aan de kar.
1. Afmelden, 60 seconden wachten en opnieuw aanmelden.

<u> Verwachte resultaten </u>:

De `persistent_clear_expired` -snijtaak moet permanente aanhalingstekens verwijderen op basis van de instellingen voor de persistentielevensduur in de configuratie.

<u> Ware resultaten </u>:

De `is_persistent` waarde voor het klantencitaat blijft *1* in de citaatlijst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
