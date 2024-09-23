---
title: 'MDVA-40545: Alleen het eerste knooppunt voor een pagina wordt opgehaald'
description: Met de MDVA-40545-patch wordt het probleem opgelost waarbij alleen het eerste knooppunt voor een pagina wordt opgehaald, zelfs als er meer dan één knooppunt voor dezelfde pagina is. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 is geïnstalleerd. De patch-id is MDVA-40545. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: CMS, Cache
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# MDVA-40545: Alleen het eerste knooppunt voor een pagina wordt opgehaald

Met de MDVA-40545-patch wordt het probleem opgelost waarbij alleen het eerste knooppunt voor een pagina wordt opgehaald, zelfs als er meer dan één knooppunt voor dezelfde pagina is. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 geïnstalleerd is. De patch-id is MDVA-40545. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Alleen het eerste knooppunt voor een pagina wordt opgehaald, zelfs als er meerdere knooppunten voor dezelfde pagina zijn.

<u> Stappen om </u> te reproduceren:

1. In het Admin Comité, ga naar **Hiërarchie** en voeg twee menupunten/knopen toe.
1. Voeg dezelfde CMS-pagina toe aan elk knooppunt.
1. Cache wissen en de voorzijde controleren.
1. Controleer de koppeling en de broodkruimels voor het eerste toegevoegde submenu.
1. Controleer de koppeling en de broodkruimels voor het tweede toegevoegde submenu.

<u> Verwachte resultaten </u>:

Broodkruimels en koppelingen in het tweede submenu zijn relevant voor het tweede knooppunt.

<u> Ware resultaten </u>:

Broodkruimels en koppelingen in het tweede submenu zijn hetzelfde als het eerste submenu.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
