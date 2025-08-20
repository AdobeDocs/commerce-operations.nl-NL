---
title: 'ACSD-65983: Er treedt een fout op bij het opnieuw configureren van een gebundeld productcitaat in Admin'
description: Pas de ACSD-65983-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een fout optreedt bij het configureren van een bundelproduct in het scherm [!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit] op de achtergrond.
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983: Er treedt een fout op bij het opnieuw configureren van een gebundeld productcitaat in Admin

De ACSD-65983-patch verhelpt het probleem waarbij het opnieuw configureren van een gebundeld productcitaat in de Admin-backend een fout retourneert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-65983. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een gebundeld productcitaat opnieuw configureert in de Admin-backend, wordt een fout geretourneerd.

<u> Stappen om </u> te reproduceren:

1. Ga naar het deelvenster Beheer en schakel **[!UICONTROL B2B Feature]** **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]** in.
1. Creeer een bundelproduct met vaste hoeveelheid (bijvoorbeeld: *$10*) en voeg drie of meer eenvoudige producten met *0* hoeveelheid, *2* in **Optie 1** en *andere* in **Optie 2** toe.
1. Maak een bedrijfsaccount aan de voorzijde.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** en wijs het gemaakte bedrijf en de producten toe aan de nieuwe/aangepaste gedeelde catalogus.
1. Login als Gebruiker van het a **Bedrijf** op frontend, en voeg één eenvoudig product aan de kar van de bundel toe.
1. Open de wortelpagina en voorlegt als a **Verzoek een Citaat**.
1. Ga naar de achtergrond en bewerk het gemaakte citaat.
1. In de **sectie van het Punt van de Citaat**, klik **vormen** knoop.
1. Selecteer een ander eenvoudig product van **Optie 2**.
1. Klik nu op de **O.K.** knoop en zie het foutenbericht.

<u> Verwachte resultaten </u>:

U kunt de gevraagde citaatpunten van Admin met succes vormen normaal, zonder getoonde foutenmelding.

<u> Ware resultaten </u>:

Het foutbericht wordt weergegeven:

*Een technisch probleem met de server leidde tot een fout. Probeer opnieuw om door te gaan wat u aan het doen was. Probeer het later opnieuw als het probleem zich blijft voordoen.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Patches toepassen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen
