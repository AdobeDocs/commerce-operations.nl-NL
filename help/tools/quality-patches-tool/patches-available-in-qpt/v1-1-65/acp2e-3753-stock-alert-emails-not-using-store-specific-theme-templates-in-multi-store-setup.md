---
title: 'ACP2E-3753: E-mailberichten met voorraadwaarschuwingen die geen winkelspecifieke themasjablonen gebruiken in multi-store installatie'
description: Pas de ACP2E-3753-patch toe om het Adobe Commerce-probleem op te lossen, waarbij e-mails met productwaarschuwingen in een multi-store-instelling altijd met het standaardthema worden verzonden, ongeacht de winkel- of themaconfiguratie.
feature: Themes, Personalization
role: Admin, Developer
source-git-commit: 6af6dc5d4880cc0cb80c443cab98cfb562949101
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACP2E-3753: E-mailberichten met voorraadwaarschuwingen die geen winkelspecifieke themasjablonen gebruiken in multi-store installatie

De ACP2E-3753-patch verhelpt het probleem waarbij e-mails met productwaarschuwingen in een multi-store setup altijd werden verzonden met het standaardthema, ongeacht de winkel- of themaconfiguratie. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 wordt geïnstalleerd. De patch-id is ACP2E-3753. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p11

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mailberichten met productrelewaakzaamheid in een meerarchiefconfiguratie worden altijd verzonden met het standaardthema, ongeacht de winkel- of themaconfiguratie.

<u> Stappen om </u> te reproduceren:

1. Maak twee websites, sla weergaven op en sla deze op.
1. Maak twee aparte thema&#39;s en wijs deze toe aan verschillende winkels.
1. Het waakzame plaatsen van het product is het standaardwerkingsgebied dat elke minuut in werking stelt.
1. Hef enkele inhoud voor beide thema&#39;s op of voeg deze toe aan het `stock.phtml` -bestand. Voorbeeld van de bestandslocatie:

   ```
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. Maak een gebruiker voor elke winkel en meld u aan voor de melding van de voorraad producten.
1. Trigger de voorraadwaarschuwing voor het product om de e-mails te verzenden.

<u> Verwachte resultaten </u>:

Het e-mailbericht moet de wijzigingen op themaniveau bevatten.

<u> Ware resultaten </u>:

De e-mails bevatten niet de sjablonen die zijn ingesteld in de betreffende website/winkel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
