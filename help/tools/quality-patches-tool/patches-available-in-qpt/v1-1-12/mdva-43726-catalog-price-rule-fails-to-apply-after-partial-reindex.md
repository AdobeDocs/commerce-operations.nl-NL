---
title: "MDVA-43726: Catalogusprijsregel is niet van toepassing na gedeeltelijke herindexering"
description: De patch MDVA-43726 verhelpt het probleem waarbij de regel voor catalogusprijzen die is gebaseerd op kenmerkovereenkomsten op archiefniveau niet van toepassing is na gedeeltelijke herindex. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 is geïnstalleerd. De patch-id is MDVA-43726. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# MDVA-43726: Catalogusprijsregel is niet van toepassing na gedeeltelijke herindexering

De patch MDVA-43726 verhelpt het probleem waarbij de regel voor catalogusprijzen die is gebaseerd op kenmerkovereenkomsten op archiefniveau niet van toepassing is na gedeeltelijke herindex. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 geïnstalleerd is. De patch-id is MDVA-43726. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De regel voor catalogusprijzen die is gebaseerd op kenmerkovereenkomsten op archiefniveau wordt niet toegepast na gedeeltelijke herindex.

<u> Stappen om </u> te reproduceren:

1. Stel de indexeermodus in om volgens schema te werken.
1. Maak twee configureerbare productkenmerken. Bijvoorbeeld: Kleur (visuele staal) en Grootte (tekststaal).
1. Creeer een configureerbaar product gebruikend beide attributen die in Stap 2 worden gecreeerd.
1. Na het creëren van de producten, creeer a **ja/nr** typekenmerk en maak het in de regelvoorwaarden zichtbaar.
1. Voeg dit kenmerk toe aan de standaardkenmerkset.
1. Creeer een regel van de catalogusprijs om toe te passen wanneer dit attribuut aan **ja** wordt geplaatst.
1. Open een van de eenvoudige producten met betrekking tot het configureerbare product.
1. Verander het werkingsgebied om mening op te slaan en de attributenwaarde aan **ja** bij te werken.
1. Voer de `CRON` uit en controleer de prijs op de voorzijde.
1. Voer een volledige herindex uit. Controleer nogmaals de prijs aan de voorzijde.
1. Werk de configureerbare productcategorie bij.
1. Voer de `CRON` uit en controleer de prijs opnieuw op de voorzijde.

<u> Verwachte resultaten </u>:

De catalogusregel wordt correct toegepast zonder een volledige herindex met behulp van incrementele indexen.

<u> Ware resultaten </u>:

De catalogusregel wordt niet toegepast zonder een volledige herindex uit te voeren.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
