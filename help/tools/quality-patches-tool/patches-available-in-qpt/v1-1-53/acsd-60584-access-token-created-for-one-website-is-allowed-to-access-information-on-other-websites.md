---
title: "ACSD-60584: toegangstoken die voor één website zijn gemaakt, heeft toegang tot informatie op andere websites"
description: Pas de ACSD-60584-patch toe om het probleem op te lossen waarbij het toegangstoken dat voor de gebruiker op een website is gemaakt, toegang heeft tot klantgegevens op andere websites of deze kan wijzigen.
feature: Customers, GraphQL
role: Admin, Developer
source-git-commit: eba4a8fd7bbf52fbc4295feab0d5bb79e7383b66
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584: toegangstoken die voor één website zijn gemaakt, heeft toegang tot informatie op andere websites

De ACSD-60584-patch verhelpt het probleem waarbij het toegangstoken dat voor de gebruiker op een website is gemaakt, toegang heeft tot klantgegevens op andere websites of deze kan wijzigen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.53 wordt geïnstalleerd. De patch-id is ACSD-60584. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Met de API-token die op één website voor de gebruiker is gemaakt, hebt u toegang tot klantgegevens, kunt u een winkelwagentje maken en producten aan het winkelwagentje toevoegen in andere webweergaven.

<u> Stappen om </u> te reproduceren:

1. Zorg ervoor dat **[!DNL Share Customer Accounts configuration]** is ingesteld op **[!UICONTROL Per Website]** .
1. Creeer extra *website*, *opslag*, en *storeview*.
1. Creeer twee klanten met zelfde e-mail op de belangrijkste *website* en de *website* van de vorige stap.
1. Een klanttoken genereren via [!DNL GraphQL] op de hoofdwebsite.
1. Met het gegenereerde token verzendt u een query van de klant **[!DNL GraphQL]** met de tweede website in de koptekst om klantgegevens op te halen.
1. Bekijk het geretourneerde resultaat.

<u> Verwachte resultaten </u>:

De informatie van de klant van de belangrijkste *website* is teruggekeerd omdat het teken van de belangrijkste *website* in [!DNL GraphQL] vraag wordt gebruikt.

<u> Ware resultaten </u>:

De klantgegevens van de tweede website worden geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
