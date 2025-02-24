---
title: 'ACSD-46703: slepen en neerzetten van producten werkt niet'
description: Dit artikel biedt een oplossing voor het probleem waarbij slepen en neerzetten van de aanpasbare opties van het product niet naar behoren werkt.
feature: Products
role: Developer
exl-id: 38b9490a-c9d4-4f8e-b90f-69bf50a6b571
source-git-commit: a1c5898626fb8419af017a29a009a0a2c069326e
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-46703: slepen en neerzetten van producten werkt niet

De ACSD-46703-patch verhelpt het probleem waarbij de aanpasbare opties (slepen en neerzetten) van het product niet naar behoren werken. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 geïnstalleerd is. De patch-id is ACSD-46703. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5

>[!NOTE]
>
>Het flard zou op andere versies met nieuwe [ versies van het Hulpmiddel van de Patches van de Kwaliteit ] van toepassing kunnen worden. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers kunnen de aanpasbare opties niet van de ene pagina naar de andere slepen.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Voeg aanpasbare opties toe aan het eenvoudige product en zorg ervoor dat u meer dan 20 opties toevoegt die resulteren in paginering.
1. Probeer een aanpasbare optie (slepen en neerzetten) op dezelfde pagina te plaatsen.
1. Verplaats nu een aanpasbare optie van pagina twee naar pagina één.

<u> Verwachte resultaten </u>:

* U kunt de aanpasbare opties van de ene pagina naar de andere slepen.
* U kunt de waarden sorteren met slepen en neerzetten, zelfs voor meerdere pagina&#39;s.

<u> Ware resultaten </u>:

U kunt geen waarde naar een andere pagina verplaatsen met de functie slepen en neerzetten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op-gebouw: [ Hulpmiddelen van de Patches van de Kwaliteit > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de gids van het Hulpmiddel van de Patches van de Kwaliteit.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de gids van het Hulpmiddel van de Patches van de Kwaliteit.
