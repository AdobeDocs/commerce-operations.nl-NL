---
title: 'MDVA-43201: Fout bij gebruik van DOB-veld met landinstelling PT'
description: De patch MDVA-43201 lost het probleem op waar een fout voorkomt wanneer het gebruiken van het DOB klantenattribuut in de vorm van de klantenregistratie voor de Portugese scène. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 is geïnstalleerd. De patch-id is MDVA-43201. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: B2B, Cache
role: Admin
exl-id: be087420-1ee3-40cc-8ff7-62c5641609cc
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-43201: Fout bij gebruik van DOB-veld met landinstelling PT

De patch MDVA-43201 lost het probleem op waar een fout voorkomt wanneer het gebruiken van het DOB klantenattribuut in de vorm van de klantenregistratie voor de Portugese scène. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 geïnstalleerd is. De patch-id is MDVA-43201. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het DOB klantenattribuut aan de vorm van de klantenregistratie voor Portugese scène wordt toegevoegd, geeft de vorm het fout *Argument 1 die tot iterator_to_array () wordt overgegaan interfacetravesable, ongeldig op gegeven* moet uitvoeren.

<u> Eerste vereisten </u>:

B2B-modules worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Ga naar Admin > **Opslag** > **Configuratie** > **Algemeen** > **Opties van de Plaats**, plaats Plaats Plaats Plaats aan **Portugees (Portugal)** en klik **sparen**.
1. Cache opnieuw indexeren en wissen.
1. Ga naar **Slaat** > **Attribuut** > **Klant** op.
1. Open DOB klantenattributen en reeks **tonen op Storefront** aan **ja**.
1. Selecteer allen van **Vorm in** te gebruiken.
1. Sla het kenmerk op.
1. Ga naar de pagina Nieuw account maken aan de voorkant.

<u> Verwachte resultaten </u>:

Het registratieformulier voor klanten in de Portugese winkel geeft geen enkele fout bij het toevoegen van het DOB-kenmerk.

<u> Ware resultaten </u>:

Het registratieformulier voor klanten van de Portugese winkel geeft een fout bij het toevoegen van het DOB-kenmerk.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
