---
title: 'ACS2E-3753: E-mails met voorraadwaarschuwingen waarin geen gebruik wordt gemaakt van winkelspecifieke themasjablonen in multi-store-instellingen'
description: Pas de ACP2E-3753-patch toe om het Adobe Commerce-probleem op te lossen, waarbij e-mails met productwaarschuwingen in een multi-store-instelling altijd met het standaardthema worden verzonden, ongeacht de winkel- of themaconfiguratie.
feature: Themes, Personalization
role: Admin, Developer
exl-id: ad44ffdd-f122-4119-83e3-1816951b662c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACS2E-3753: E-mails met voorraadwaarschuwingen waarin geen gebruik wordt gemaakt van winkelspecifieke themasjablonen in multi-store-instellingen

De ACP2E-3753-patch verhelpt het probleem waarbij e-mails met productwaarschuwingen in een multi-store setup altijd werden verzonden met het standaardthema, ongeacht de winkel- of themaconfiguratie. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 wordt geïnstalleerd. De patch-id is ACP2E-3753. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p11

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mailberichten met productrelewaakzaamheid in een meerarchiefconfiguratie worden altijd verzonden met het standaardthema, ongeacht de winkel- of themaconfiguratie.

<u> Stappen om </u> te reproduceren:

1. Maak twee websites, sla weergaven op en sla deze op.
1. Maak twee aparte thema&#39;s en wijs deze toe aan verschillende winkels.
1. Het waakzame plaatsen van het product is het standaardwerkingsgebied dat elke minuut in werking stelt.
1. Hef enkele inhoud voor beide thema&#39;s op of voeg deze toe aan het `stock.phtml` -bestand. Voorbeeld van de bestandslocatie:

   ```text
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

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
