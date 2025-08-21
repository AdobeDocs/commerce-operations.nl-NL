---
title: 'ACP2E-3731: Productexporten met [!UICONTROL Catalog, Search] zichtbaarheid omvatten records uit andere winkelweergaven'
description: Pas de ACS2E-3731-patch toe om de Adobe Commerce te herstellen, waarbij het product wordt geëxporteerd met het zichtbaarheidsfilter ingesteld op [!UICONTROL Catalog, Search] . Dit filter bevat onjuiste rijen in instellingen voor meerdere winkels als gevolg van verschillen tussen kenmerken binnen het bereik van de winkel.
feature: Data Import/Export
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7a2e98b836fcc1759910777d1e9fe50e03dabb07
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# ACP2E-3731: Productexporten met [!UICONTROL Catalog, Search] zichtbaarheid omvatten records uit andere winkelweergaven

De ACP2E-3731-patch verhelpt het probleem dat bij het exporteren van producten met *[!UICONTROL Catalog, Search]* zichtbaarheid ten onrechte records uit andere winkelweergaven in multi-store omgevingen worden opgenomen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACP2E-3731. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p9

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het exporteren van producten bevat onjuiste rijen wanneer het zichtbaarheidsfilter is ingesteld op *[!UICONTROL Catalog, Search]* in instellingen voor meerdere winkels als gevolg van verschillen in kenmerken met winkelbereik.

<u> Stappen om </u> te reproduceren:

1. Ga in het deelvenster Beheer naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** om een extra website te maken, de weergave op te slaan en op te slaan.
1. Ga naar **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* **[!UICONTROL Attribute Set]** . Klik op **[!UICONTROL Add Attribute Set]** om een kenmerk te maken. Plaats **[!UICONTROL Based On]** aan *Gebrek*.
1. Maak een product en wijs het toe aan zowel de hoofdwebsite als de secundaire website.
1. Plaats een tekstwaarde voor het pas gecreëerde attribuut met **[!UICONTROL Scope]** plaatste aan *Alle Kijken van de Opslag*.
1. Verander het werkingsgebied in de secundaire opslagmening en werk de attributen met een verschillende waarde bij.
1. Verander het werkingsgebied in de standaard opslagmening en de secundaire opslagmening, dan plaats het productzicht aan *niet Zichtbaar individueel*.
1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Export]**, en selecteer *Producten* van het dropdown menu.
1. Stel een filter in waarbij **[!UICONTROL Visibility]** = *[!UICONTROL Catalog, Search]* en klik op **[!UICONTROL Continue]** .
1. Voer de volgende opdracht uit om het exporteren te verwerken:

   ```
   php bin/magento queue:consumers:start exportProcessor
   ```

1. Controleer het geëxporteerde bestand.

<u> Verwachte resultaten </u>:

Alleen de gefilterde records worden geëxporteerd.

<u> Ware resultaten </u>:

Het geëxporteerde bestand bevat een rij voor de weergave van de secundaire opslag, die niet overeenkomt met de filtercriteria die tijdens het exporteren zijn ingesteld.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
