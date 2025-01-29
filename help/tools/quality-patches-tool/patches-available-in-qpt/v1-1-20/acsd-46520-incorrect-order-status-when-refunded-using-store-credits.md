---
title: 'ACSD-46520: onjuiste orderstatus bij teruggave via winkelcredits'
description: Dit artikel biedt een oplossing voor het probleem waarbij gebruikers een onjuiste orderstatus krijgen wanneer ze deze terugbetalen met gebruik van winkelcredits.
feature: Orders, Returns
role: Admin
exl-id: 67740003-a71e-41bf-afda-ca3e32290115
source-git-commit: a1c5898626fb8419af017a29a009a0a2c069326e
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-46520: onjuiste orderstatus bij teruggave via winkelcredits

De ACSD-46520-patch lost het probleem op waarbij gebruikers een onjuiste orderstatus krijgen wanneer ze deze terugbetalen met gebruik van opslagkredieten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 wordt geïnstalleerd. De patch-id is ACSD-46520. De kwestie is opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 en 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gebruikers krijgen een onjuiste status van de bestelling wanneer ze deze terugbetalen met gebruik van winkelcredits.

<u> Stappen om </u> te reproduceren:

1. Maak een klantenaccount op de winkel en meld u aan.
1. Wijs opslagkredieten toe aan de klant vanuit de beheerder. De winkelkredieten moeten de hele bestelling dekken.
1. Plaats een bestelling met de winkelcredits.
1. Factuur de bestelling.
1. Maak een creditnota om het volledige bedrag van de bestelling terug te betalen.
Schakel het selectievakje **[!UICONTROL Refund to store credit]** in.
1. Controleer de orderstatus.

<u> Verwachte resultaten </u>:

De ordestatus is *Gesloten*.

<u> Ware resultaten </u>:

De ordestatus is *Volledig*, die niet de correcte status is.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of [!DNL Magento Open Source] op-gebouw: [ Hulpmiddelen van het Patroon van de Kwaliteit > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de gids van het Hulpmiddel van het Patroon van de Kwaliteit.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de gids van het Hulpmiddel van de Patches van de Kwaliteit.
