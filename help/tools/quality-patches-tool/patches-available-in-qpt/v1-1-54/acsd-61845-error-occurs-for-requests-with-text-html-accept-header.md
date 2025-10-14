---
title: 'ACSD-61845: Fout treedt op bij aanvragen met text/html accepteert header'
description: Pas de ACSD-61845-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij het verzenden van een HTTP-aanvraag met alleen een *text/html* accept header een 500-fout veroorzaakt, waarbij B2B-modules zijn geïnstalleerd.
feature: B2B
role: Admin, Developer
exl-id: 6fa6c3ff-bb45-4b9e-afd4-95692acb0a90
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845: De fout komt voor voor verzoeken met *text/html* keurt kopbal goed

Het ACSD-61845 flard lost de kwestie op waar een HTTP- verzoek met slechts a *text/html* kopbal een 500 fout wegens media type wanverhoudingen in reactie behandeling veroorzaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 is geïnstalleerd. De patch-id is ACSD-61845. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het verzenden van een HTTP- verzoek met slechts *text/html* in goedkeurt kopbal, komt een fout 500 toe te schrijven aan een wanverhouding in de media typeconfiguratie.

<u> Eerste vereisten </u>:

B2B-modules worden geïnstalleerd en ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Verzend een verzoek met slechts *text/html* in goedkeurt kopbal, als volgt:

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u> Verwachte resultaten </u>:

De pagina is teruggekeerd met de statuscode van a *200*.

<u> Ware resultaten </u>:

Er wordt een fout van 500 geretourneerd, met het volgende foutbericht in de `exception.log` :

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

[[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
