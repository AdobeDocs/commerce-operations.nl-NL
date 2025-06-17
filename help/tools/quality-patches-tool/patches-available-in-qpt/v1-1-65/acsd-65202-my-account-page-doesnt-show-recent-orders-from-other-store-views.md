---
title: 'ACSD-65202: Mijn accountpagina bevat geen recente bestellingen uit andere winkelweergaven'
description: Pas de ACSD-65202-patch toe om het Adobe Commerce-probleem op te lossen, waarbij op de pagina Mijn account geen recente bestellingen van andere winkelweergaven in dezelfde winkel worden weergegeven.
feature: Orders, User Account
role: Admin, Developer
source-git-commit: 0af6ab4ef15e8aa56354886b341b70a080662eae
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---


# ACSD-65202: [!UICONTROL My Account] pagina bevat geen recente bestellingen uit andere winkelweergaven

De ACSD-65202-patch verhelpt het probleem dat op de pagina **[!UICONTROL My Account]** geen recente bestellingen van andere winkelweergaven in dezelfde winkel worden weergegeven. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 wordt geïnstalleerd. De patch-id is ACSD-65202. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p12

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer u naar de pagina met klantenaccounts gaat (sectie **[!UICONTROL My Account]** ), worden er geen recente bestellingen weergegeven die in een andere winkelweergave zijn geplaatst. Als u echter naar de ordergeschiedenis gaat (sectie *[!UICONTROL My Orders]* ), ziet u alle bestellingen in beide winkelweergaven.

<u> Stappen om </u> te reproduceren:

1. Adobe Commerce installeren.
1. In het *Admin* paneel, creeer een nieuwe Mening van de Opslag en ga zijn code als, *tweede* in, om de mening te identificeren.
1. Maak een eenvoudig product en herdex.
1. Creeer een klantenrekening en plaats een orde in de standaardopslagmening de waarvan code *gebrek* is.
1. Ga naar de pagina **[!UICONTROL My Orders]** en controleer of de volgorde zichtbaar is in beide winkelweergaven, bijvoorbeeld:
1. Standaard: https://localhost/pub/default/sales/order/history/
1. Tweede: https://localhost/pub/second/sales/order/history/

1. Ga naar de pagina **[!UICONTROL My Account]** in beide winkelweergaven:
1. Standaard: https://localhost/pub/default/customer/account/
1. Tweede: https://localhost/pub/second/customer/account/

<u> Verwachte resultaten </u>:

U kunt orders van beide opslagmeningen op de pagina van Orden zien. Het is dezelfde winkel, gewoon een andere winkelweergave.

<u> Ware resultaten </u>:

Het gedrag is inconsistent. Bestellingen worden niet weergegeven in de tweede winkelweergave.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
