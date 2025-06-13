---
title: 'MDVA-41350: Uitzondering wanneer admin producten buiten hun toegang toevoegt'
description: De flard MDVA-41350 lost de kwestie op waar een uitzonderingsfout in plaats van een beperkt toegangsbericht wordt geworpen wanneer een admin gebruiker een product in de orde door SKU toevoegt die buiten hun toegang is. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 is geïnstalleerd. De patch-id is MDVA-41350. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Admin Workspace, Products
role: Admin
exl-id: 4dc5ee5c-bd93-42e1-9c63-93ffb8e5f21c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-41350: Uitzondering wanneer admin producten buiten hun toegang toevoegt

De flard MDVA-41350 lost de kwestie op waar een uitzonderingsfout in plaats van een beperkt toegangsbericht wordt geworpen wanneer een admin gebruiker een product in de orde door SKU toevoegt die buiten hun toegang is. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.11 geïnstalleerd is. De patch-id is MDVA-41350. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een admin gebruiker met beperkte toegang een product door SKU buiten hun toegang in de orde toevoegt, komt een uitzondering in plaats van een bericht voor dat de gebruiker op de hoogte brengt van hun beperkte toegang.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de beheerder als een gebruiker met alleen toegang tot een specifieke website.
1. Ga naar **Verkoop** > **Orden** en klik **creeer Nieuwe Orde**.
1. Selecteer een klant en een winkelweergave.
1. Klik op **voeg Producten door SKU** toe.
1. Zoeken naar een SKU die niet is toegewezen aan een website of niet is toegewezen aan de website waartoe u toegang hebt.
1. Klik **toevoegen aan Orde**.

<u> Verwachte resultaten </u>:

Er wordt een geschikt foutbericht weergegeven.

<u> Ware resultaten </u>:

Er treedt een uitzondering op.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
