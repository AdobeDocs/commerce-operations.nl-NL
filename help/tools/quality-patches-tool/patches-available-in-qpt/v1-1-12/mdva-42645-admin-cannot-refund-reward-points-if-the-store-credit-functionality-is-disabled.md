---
title: 'MDVA-42645: Admin kan geen bonuspunten terugbetalen voor creditering van winkels met een handicap'
description: De MDVA-42645-patch lost het probleem op waarbij de beheerder geen bonuspunten kan terugbetalen als de functionaliteit voor winkelkrediet is uitgeschakeld. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 is geïnstalleerd. De patch-id is MDVA-42645. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
exl-id: 8053fcc7-d30c-424a-9494-df6e8630b095
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42645: Admin kan geen bonuspunten terugbetalen voor creditering van winkels met een handicap

De MDVA-42645-patch lost het probleem op waarbij de beheerder geen bonuspunten kan terugbetalen als de functionaliteit voor winkelkrediet is uitgeschakeld. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 geïnstalleerd is. De patch-id is MDVA-42645. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De beheerder kan geen bonuspunten terugbetalen als de functionaliteit voor winkelkrediet is uitgeschakeld.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Maak een nieuwe klantenaccount en voeg wat bonuspunten toe.
1. Maak de Functionaliteit van het Krediet van de Opslag door te gaan **> Montages >** Configuratie **>** Klant **>** de Configuratie van de Klant **>** de Kredietopties van de Opslag **.**
1. Meld u aan als de klant aan wie de bonuspunten zijn toegewezen.
1. Voeg een product toe aan de winkelwagentje en navigeer naar de kassa.
1. Gebruik de bonuspunten in de betalingssectie en plaats de bestelling.
1. Open de bestelling in de beheerder en factureer de bestelling.
1. Klik op de **verbinding van het Memo van het Krediet** om een nieuw creditnota tot stand te brengen.
1. Tik de Terugbetaalde Punten van de Terugkeer bij de bodem en klik de **Offline Terugkeer**.

<u> Verwachte resultaten </u>:

* Het creditmemo is gemaakt.
* De bonuspunten worden met succes terugbetaald.

<u> Ware resultaten </u>:

U krijgt het volgende foutenbericht: *u kunt niet meer opslagkrediet dan het ordebedrag gebruiken.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
