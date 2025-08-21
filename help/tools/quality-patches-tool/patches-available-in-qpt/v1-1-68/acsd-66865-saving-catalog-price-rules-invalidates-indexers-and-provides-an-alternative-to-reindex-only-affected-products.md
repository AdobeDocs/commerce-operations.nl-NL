---
title: 'ACSD-66865: het opslaan van een [!UICONTROL Catalog Price Rule] maakt indexen ongeldig en biedt een alternatief voor het opnieuw indexeren van alleen betrokken producten'
description: Pas de ACSD-66865-patch toe om het Adobe Commerce-probleem op te lossen, waarbij  Als u een [!UICONTROL Catalog Price Rules] opslaat, worden indexen ongeldig en wordt een alternatief geboden voor alleen de betreffende producten.
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-66865: het opslaan van een **[!UICONTROL Catalog Price Rule]** maakt indexen ongeldig en biedt een alternatief voor het opnieuw indexeren van alleen betrokken producten

De ACSD-66865-patch verhelpt het probleem dat het opslaan van een **[!UICONTROL Catalog Price Rule]** de indexen ongeldig maakt en een alternatief biedt voor het opnieuw indexeren van alleen de betrokken producten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-66865. Dit probleem is opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een **[!UICONTROL Catalog Price Rule]** opslaat, worden alle indexen ongeldig, waardoor volledige herindexen worden geactiveerd in plaats van alleen de betrokken producten opnieuw te indexeren.

<u> Stappen om </u> te reproduceren:

1. Zorg ervoor dat de uitsnede niet wordt uitgevoerd en dat alle indexen zijn ingesteld op bijwerken volgens schema (behalve `customer_grid` dat bij het opslaan kan worden bijgewerkt).
2. Voer een volledige handmatige herindex uit met de opdracht: `php bin/magento indexer:reindex` .
3. Verifieer alle indexen tonen status *[!UICONTROL Ready]* met *0* punten in de backlog.
4. Ga op de zijbalk Beheerder naar **[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]** . Creeer een actieve regel van de catalogusprijs voor één enkel product (bijvoorbeeld, gebruikend a *SKU* voorwaarde).
5. Voer de opdracht: `php bin/magento indexer:status` uit om de indexeerstatus te controleren.
6. Houd er rekening mee dat meerdere indexen als **[!UICONTROL Reindex Required]** zijn gemarkeerd, ook al wordt slechts één product beïnvloed.

<u> Verwachte resultaten </u>:

Alleen de desbetreffende productgegevens worden geïdentificeerd en er wordt een gedeeltelijke herindex gestart in plaats van een volledige herindex voor alle indexen.

<u> Ware resultaten </u>:

Er wordt een volledige redex geactiveerd voor alle indexen, zelfs als de **[!UICONTROL Catalog Price Rule]** invloed heeft op slechts één product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
