---
title: 'MDVA-37364: Aangepast kenmerk van datumtype verbreekt raster UI'
description: De patch MDVA-37364 lost het probleem op waar het attribuut van de douaneklanker van datumtype de UI van het Net van de Klant breekt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 is geïnstalleerd. De patch-id is MDVA-37364. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4.
feature: Attributes, Cache
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# MDVA-37364: Aangepast kenmerk van datumtype verbreekt raster UI voor klant

De patch MDVA-37364 lost het probleem op waar het attribuut van de douaneklanker van datumtype de UI van het Net van de Klant breekt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2 geïnstalleerd is. De patch-id is MDVA-37364. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0-2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aangepast klantkenmerk van datumtype verbreekt de gebruikersinterface voor het raster van de klant.

<u> Stappen om </u> te reproduceren:

1. Een aangepast kenmerk met datumtype maken:
   * Ga naar **Sporen** > **Attributen** > **voeg Attribuut** toe.
   * Stel het invoertype in op Datum.
   * Stel de optie Toevoegen aan kolomopties in op Ja.
   * Sla het kenmerk op.
1. Ga naar **Admin** > **Klanten** > **Alle Klanten**.
   * Voeg het toegevoegde aangepaste kenmerk van de kolomoptie toe aan het raster.
1. Maak/bewerk een klant en stel de waarde van het gemaakte veld voor het aangepaste datumkenmerk in.
1. Cache opslaan, opnieuw indexeren en wissen.
1. Ga naar **Klanten** > **Alle Klanten**.
   * Controleer het raster van de Klant.

<u> Verwachte resultaten </u>:

Het Net van de Klant Admin toont alle gegevens met inbegrip van het nieuwe attribuut van de datumdouane zonder het Net van de Klant te breken UI.

<u> Ware resultaten </u>:

De interface voor het klantenraster van Admin is verbroken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.