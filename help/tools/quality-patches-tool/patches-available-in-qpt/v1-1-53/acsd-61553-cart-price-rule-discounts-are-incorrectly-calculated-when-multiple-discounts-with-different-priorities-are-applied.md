---
title: 'ACSD-61553: [!UICONTROL Cart Price Rule] wordt onjuist berekend wanneer meerdere kortingen met verschillende prioriteiten worden toegepast'
description: Pas de ACSD-61553-patch toe om het Adobe Commerce-probleem op te lossen, waarbij [!UICONTROL Cart Price Rule] onjuist wordt berekend wanneer meerdere kortingen met verschillende prioriteiten worden toegepast.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: 0fb7a988-d391-49e5-a59d-62315a16132c
source-git-commit: b182fc0cd2f00f36138675277ac1de8a7179135a
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-61553: [!UICONTROL Cart Price Rule] wordt onjuist berekend wanneer meerdere kortingen met verschillende prioriteiten worden toegepast

De ACSD-61553-patch verhelpt het probleem waarbij [!UICONTROL Cart Price Rule] onjuist wordt berekend wanneer meerdere kortingen met verschillende prioriteiten worden toegepast. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53 wordt geïnstalleerd. De patch-id is ACSD-61553. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5-p8

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!UICONTROL Cart Price Rule] wordt onjuist berekend wanneer meerdere kortingen met verschillende prioriteiten worden toegepast.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product met een prijs van $9.000.
1. Maak een [!UICONTROL Cart Price Rule]: regel A met een vaste korting van € 700 zonder voorwaarden en zonder daaropvolgende regels te verwijderen.
1. Maak nog een [!UICONTROL Cart Price Rule]: regel B met een vaste korting van € 1000 zonder voorwaarden en zonder de volgende regels te verwijderen.
1. Voeg het product met de hoeveelheid 13 toe aan de kar.
1. Werk de regels bij met een van de volgende scenario&#39;s:

   scenario 01

        Regel A 
        Prioriteit: 1 
        Maximale Korting van de Aantal wordt toegepast op: 1 
       
        Regel B 
        Prioriteit: 0 
        Maximale Korting van de Aantal wordt toegepast op: 0 
   
   scenario 02

        Regel A 
        Prioriteit: 0 
        Maximale Korting van de Aantal wordt toegepast op: 0 
       
        Regel B 
        Prioriteit: 1 
        Maximale Korting van de Aantal wordt toegepast op: 1 
   
   scenario 03

        Regel A 
        Prioriteit: 0 
        Maximale Korting van de Aantal wordt toegepast op: 0 
       
        Regel B 
        Prioriteit: 0 
        Maximale Korting van de Aantal wordt toegepast op: 1 
   
1. Klik op de knop **[!UICONTROL Update Shopping Cart]** om de kortingen opnieuw te berekenen.

<u> Verwachte resultaten </u>:

U ziet de volgende totale korting voor verschillende scenario&#39;s:

     Scenario 01: $13.700 
     Scenario 02: $10.100 
     Scenario 03: $10.100 

<u> Ware resultaten </u>:

In alle drie scenario&#39;s, is de totale korting $9.000.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
