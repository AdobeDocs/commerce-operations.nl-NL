---
title: 'ACSD-52906: Het probleem met X-Magento-Vary cookie oplossen voor het in cache plaatsen van aangemelde klanten'
description: Pas de ACSD-52906-patch toe om het Adobe Commerce-probleem op te lossen waarbij het X-Magento-Vary-cookie onjuist is ingesteld voor aangemelde klanten.
feature: Cache
role: Admin, Developer
exl-id: 487b7588-7131-4502-b714-05f37520991f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-52906: Het probleem met X-Magento-Vary cookie oplossen voor aangemelde klanten

De ACSD-52906-patch verhelpt het probleem waarbij het X-Magento-Vary-cookie onjuist is ingesteld voor aangemelde klanten. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.36 wordt geïnstalleerd. De patch-id is ACSD-52906. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

X-Magento-Vary cookie wordt onjuist ingesteld voor aangemelde klanten die tot hetzelfde klantensegment behoren, waardoor sommige pagina&#39;s niet correct in cache worden geplaatst.

<u> Eerste vereisten </u>:

Adobe Commerce Inventory management (MSI)-modules worden geïnstalleerd en ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Configureer [!DNL Varnish] of [!DNL Fastly] cache.
1. Creeer een nieuw klantensegment en wijs het aan de *Geregistreerde* klanten toe.
1. Maak twee klanten, bijvoorbeeld klant1 en klant2.
1. Wis de cache.
1. Meld u aan als klant1 en ga naar de startpagina.
1. Open een incognitopagina in uw browser.
1. Ga naar een andere pagina dan de startpagina.
1. Meld u aan als klant2.
1. Ga naar de startpagina.
1. Controleer of de pagina in het cachegeheugen is opgeslagen in de browserDev-console.

<u> Verwachte resultaten </u>:

De pagina wordt opgehaald uit de cache.

<u> Ware resultaten </u>:

De pagina is niet in cache geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
