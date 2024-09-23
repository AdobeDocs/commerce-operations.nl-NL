---
title: "MDVA-37897: Onjuiste omleiding bij het toevoegen van producten van Recent Bekeken"
description: Met de MDVA-37897-patch wordt het probleem van onjuiste omleiding opgelost wanneer gebruikers proberen producten toe te voegen met opties van de onlangs bekeken widget. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1 is geïnstalleerd. De patch-id is MDVA-37897. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4.
feature: Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# MDVA-37897: Onjuiste omleiding bij het toevoegen van producten van Recent Bekeken

Met de MDVA-37897-patch wordt het probleem van onjuiste omleiding opgelost wanneer gebruikers proberen producten toe te voegen met opties van de onlangs bekeken widget. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1 geïnstalleerd is. De patch-id is MDVA-37897. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce over onze cloudinfrastructuur 2.4.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een gebruiker een product probeert toe te voegen vanuit de sectie Onlangs bekeken waarvoor opties moeten worden geselecteerd, wordt de gebruiker omgeleid naar de pagina met productdetails in plaats van naar de pagina met productdetails.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product met aanpasbare opties (Type: keuzerondje).
1. Configureer de widget Onlangs bekeken om producten weer te geven.
1. Bezoek producten met aanpasbare opties, zodat deze worden weergegeven in de widget Onlangs bekeken.
1. Klik **toevoegen aan Kar** op één van de producten in Recently Bekeken widget.

<u> Verwachte resultaten </u>:

U wordt omgeleid naar de pagina met productdetails om de opties te kiezen.

<u> Ware resultaten </u>:

Je wordt doorgestuurd naar de pagina met productaanbiedingen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Adobe Commerce op-gebouw: [ Gids van de Update van de Software > pas Patches ](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in onze ontwikkelaarsdocumentatie toe.
* Adobe Commerce op onze wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://devdocs.magento.com/cloud/project/project-patch.html) in onze ontwikkelaarsdocumentatie toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

* [ vrijgegeven Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitsflarden ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html-) sectie.