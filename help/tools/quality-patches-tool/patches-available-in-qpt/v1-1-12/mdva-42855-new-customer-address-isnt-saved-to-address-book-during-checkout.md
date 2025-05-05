---
title: 'MDVA-42855: Het nieuwe klantenadres wordt niet bewaard aan adresboek tijdens controle '
description: De patch MDVA-42855 lost het probleem op waar het nieuwe klantenadres niet aan het adresboek tijdens controle wordt bewaard. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 is geïnstalleerd. De patch-id is MDVA-42855. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Checkout, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-42855: Het nieuwe klantenadres wordt niet bewaard aan adresboek tijdens controle

De patch MDVA-42855 lost het probleem op waar het nieuwe klantenadres niet aan het adresboek tijdens controle wordt bewaard. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 geïnstalleerd is. De patch-id is MDVA-42855. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het nieuwe klantenadres wordt niet opgeslagen aan het adresboek tijdens het afrekenen.

<u> Stappen om </u> te reproduceren:

1. Maak een klantenaccount en werk het standaardadres voor verzending en facturering bij.
1. Voeg een product toe aan de winkelwagentje en navigeer naar de afrekenpagina.
1. Klik bij verzending op **+ Nieuw adres** .
1. Ga uw nieuw adres in en houd **sparen in het Boek van het Adres** checkbox aangekruist.
1. Bij Betaling, tik **Mijn het factureren en verschepen adres het zelfde** checkbox zijn.
1. Plaats de bestelling.
1. Controleer het adresboek.

<u> Verwachte resultaten </u>:

Het nieuwe verzendadres wordt opgeslagen in het adresboek.

<u> Ware resultaten </u>:

Het nieuwe verzendadres wordt niet opgeslagen in het adresboek.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
