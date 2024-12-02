---
title: 'ACSD-48784: Prijzen van klantensegmenten worden onjuist in cache geplaatst tussen klantengroepen'
description: Pas de ACSD-48784-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de prijzen van klantensegmenten onjuist tussen klantgroepen worden vastgelegd.
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
exl-id: a691c61c-fdba-4d6a-8314-095dfb0ba4a1
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48784: Prijzen van klantensegmenten worden onjuist in cache geplaatst tussen klantengroepen

De ACSD-48784-patch verhelpt het probleem waarbij de prijzen van klantensegmenten onjuist tussen klantengroepen worden vastgelegd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 wordt geïnstalleerd. De patch-id is ACSD-48784. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De de segmentprijzen van de klant worden in het voorgeheugen ondergebracht verkeerd tussen klantengroepen.

<u> Eerste vereisten </u>:

Configureer [!DNL Varnish] of [!DNL Fastly] .

<u> Stappen om </u> te reproduceren:

1. Schakel het in cache plaatsen van volledige pagina&#39;s in uw winkel in.
1. Meld u aan bij de site als een gebruiker met speciale klantgroepprijzen.
1. Ga naar een productpagina voor een product met speciale klantgroepprijzen. Neem de *speciale prijs* waar.
1. Open in een aparte browser dezelfde productpagina als een gastgebruiker zonder u aan te melden. Neem de normale prijs waar.
1. Open de Adobe Commerce-beheerinterface en wis de Adobe Commerce- en [!DNL Fastly] cache voor deze winkel.
1. Verwijder het cookie `X-Magento-Vary` in de aangemelde browser.
1. Laad in de aangemelde browser dezelfde productpagina meerdere keren opnieuw totdat het in cache plaatsen volledig is leeggemaakt.
1. In niet-het programma geopende browser, herlaad de productpagina om de prijs van de klantengroep nu te zien.

<u> Verwachte resultaten </u>:

Op de productpagina wordt de juiste prijs voor specifieke klantengroepen weergegeven.

<u> Ware resultaten </u>:

* Gastgebruikers zien de speciale aangemelde gebruikersprijs.
* Als het product eenmaal is toegevoegd, wordt op de minikaart de juiste prijs vermeld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
