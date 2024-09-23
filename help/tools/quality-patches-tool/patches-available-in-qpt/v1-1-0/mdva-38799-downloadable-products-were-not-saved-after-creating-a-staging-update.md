---
title: 'MDVA-38799: Downloadbare producten die niet zijn opgeslagen na het maken van een gefaseerde update'
description: Met de MDVA-38799-patch wordt het probleem opgelost waarbij downloadbare producten niet worden opgeslagen na het maken van een testupdate. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 is geïnstalleerd. De patch-id is MDVA-38799. Het probleem is opgelost in Adobe Commerce versie 2.4.3.
feature: Products, Staging
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799: Downloadbare producten die niet zijn opgeslagen na het maken van een testupdate

Met de MDVA-38799-patch wordt het probleem opgelost waarbij downloadbare producten niet worden opgeslagen na het maken van een testupdate. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0 geïnstalleerd is. De patch-id is MDVA-38799. Het probleem is opgelost in Adobe Commerce versie 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce over wolkeninfrastructuur 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Downloadbare producten worden niet opgeslagen nadat een testupdate is gemaakt. Gebruikers krijgen het foutbericht: *het downloadbare voorbeeld is niet gerelateerd aan het product. Verifieer de verbinding en probeer opnieuw*.

<u> Stappen om </u> te reproduceren:

1. Navigeer aan **Catalogus** > **Producten**.
1. Klik op het vervolgkeuzemenu naast Product toevoegen en selecteer Downloadbaar product.
   * Vul de naam, SKU, prijs en hoeveelheid van het product in.
1. Blader omlaag naar de pagina Downloadbare gegevens.
1. Onder Steekproeven, klik **toevoegen Verbinding**.
   * Vul de Titel in, Bestand uploaden (het bestandstype is niet van belang).
1. Klik **sparen**. U zult het volgende bericht krijgen: *u bewaarde het product*.
1. Klik **Nieuwe Update van het Programma** bij de bovenkant van de pagina.
   * Vul de Naam van de Update en een wettige Datum van het Begin en van het Eind in.
1. Klik **sparen** op de het opvoeren update.
1. Klik **sparen** op het product.

<u> Verwachte resultaten </u>:

Het product wordt zonder fout opgeslagen.

<u> Ware resultaten </u>:

U krijgt het foutenbericht: *het downloadbare monster is niet verwant met het product. Verifieer de verbinding en probeer opnieuw*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.