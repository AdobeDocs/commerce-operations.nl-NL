---
title: 'ACSD-54983: Company user UID met GraphQL niet beschikbaar bij inactieve gebruiker'
description: Pas de ACSD-54983-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het niet mogelijk is om de aanvraag van UID voor bedrijfsgebruikers met GraphQL op te halen als de gebruikersstatus is ingesteld op inactief.
feature: GraphQL
role: Admin, Developer
exl-id: b188270f-5454-41c9-8370-f4c396095297
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-54983: Company user UID met GraphQL niet beschikbaar bij inactieve gebruiker

De ACSD-54983-patch verhelpt het probleem waarbij het niet mogelijk is om een UID-aanvraag van bedrijfsgebruikers op te halen met GraphQL als de gebruikersstatus is ingesteld op inactief. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43 wordt geïnstalleerd. De patch-id is ACSD-54983. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Kan het bedrijf UID niet ophalen met GraphQL-verzoek als de gebruikersstatus is ingesteld op inactief.

<u> Stappen om </u> te reproduceren:

1. Maak een bedrijf met een beheerder. Bijvoorbeeld company@test.com.
1. Maak een nieuwe klant.
1. Wijs de nieuwe klant aan een bedrijf toe.
1. Get a **[!UICONTROL company admin token]**.
1. Haal met de **[!UICONTROL company admin token]** de bedrijfsstructuur op. Zie [ de bedrijfstructuur ](https://developer.adobe.com/commerce/webapi/graphql/schema/b2b/company/queries/company/#return-the-company-structure) in onze ontwikkelaarsdocumentatie terugkeren.
1. De reactie bevat slechts *ACTIEVE* klanten met hun IDs.
1. Werk de bedrijfgebruiker bij aan *INACTIEF*.
1. Haal de bedrijfsstructuur opnieuw op.

<u> Verwachte resultaten </u>:

Het is mogelijk om de bedrijfgebruiker UID te krijgen wanneer de status aan inactief wordt geplaatst.

<u> Ware resultaten </u>:

De niet-actieve klanten staan niet in de lijst. Kan UID van bedrijfsgebruiker niet ophalen wanneer de status is ingesteld op inactief.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
