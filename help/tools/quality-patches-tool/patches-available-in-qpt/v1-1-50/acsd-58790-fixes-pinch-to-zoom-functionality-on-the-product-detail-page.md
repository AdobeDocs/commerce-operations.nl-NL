---
title: 'ACSD-58790: hiermee wordt de zoomfunctie met knijpbeweging op de pagina-afbeeldingen met productdetails in de mobiele weergave gecorrigeerd  [!DNL Chrome]'
description: ACSD-58790 bevestigt de kwestie van Adobe Commerce waar het beeld in mobiele mening op  [!DNL Chrome]  niet binnen op het beeld zoals verwacht zoomde.
feature: Storefront
role: Admin, Developer
exl-id: 46b324bf-c2a0-4086-87ee-96e8c4883494
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-58790: hiermee wordt de zoomfunctie met knijpbeweging op de pagina-afbeeldingen met productdetails in de mobiele weergave gecorrigeerd [!DNL Chrome]

De ACSD-58790-patch verhelpt het Adobe Commerce-probleem waarbij de afbeelding in de mobiele weergave op [!DNL Chrome] niet naar behoren in de afbeelding is inzoomd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-58790. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee corrigeert u de zoomfunctie met knijpbeweging voor de afbeeldingen van de detailpagina in de mobiele weergave op [!DNL Chrome] .

<u> Stappen om </u> te reproduceren:

1. Maak een product met een afbeelding.
1. Open het product vanuit een [!DNL Chrome] browser.
1. Klik op de afbeelding en controleer of op de afbeelding wordt ingezoomd door te dubbelklikken.
1. Schakel over naar de mobiele weergave met de ontwikkelaars van [!DNL Chrome] .
1. Klik op de afbeelding.
1. Dubbeltik.

<u> Verwachte resultaten </u>:

De afbeelding wordt ingezoomd wanneer u dubbelklikt.

<u> Ware resultaten </u>:

De afbeelding wordt niet ingezoomd wanneer u dubbelklikt. Dit probleem geldt specifiek voor [!DNL Chrome] in de mobiele weergave, omdat de zoomfunctionaliteit werkt zoals u had verwacht in [!DNL Firefox] .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
