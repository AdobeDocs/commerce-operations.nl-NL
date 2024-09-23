---
title: 'MDVA-41229: Afbeeldingen die beschikbaar zijn op de achtergrond worden niet weergegeven op de voorzijde na het importeren van configureerbare producten.'
description: Met de MDVA-41229-patch wordt het probleem opgelost waarbij afbeeldingen die op de achtergrond beschikbaar zijn, niet op de voorzijde worden weergegeven nadat configureerbare producten zijn geïmporteerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 is geïnstalleerd. De patch-id is MDVA-41229. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Data Import/Export, Configuration, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 2%

---

# MDVA-41229: Afbeeldingen die beschikbaar zijn op de achtergrond worden niet weergegeven op de voorzijde nadat configureerbare producten zijn geïmporteerd

Met de MDVA-41229-patch wordt het probleem opgelost waarbij afbeeldingen die op de achtergrond beschikbaar zijn, niet op de voorzijde worden weergegeven nadat configureerbare producten zijn geïmporteerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 geïnstalleerd is. De patch-id is MDVA-41229. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.2-p2 en 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Afbeeldingen die op de achtergrond beschikbaar zijn, worden niet op de voorzijde weergegeven nadat configureerbare producten zijn geïmporteerd.

<u> Stappen om </u> te reproduceren:

1. Een schone Adobe Commerce installeren.
1. Voeg een douaneattribuut toe door **te gaan Slaat** > **Attributen** > **Product** > **Nieuw Attribuut** met de montages hieronder toevoegen:

   * Eigenschappen:
      * Kenmerkeigenschappen:

         * Standaardlabel: Grootte instellen
         * Invoertype catalogus voor winkeleigenaar: Tekststaal
         * Vereiste waarden: geen
         * Afbeelding van productvoorvertoning bijwerken: Ja

      * Staal beheren (waarden van uw kenmerk):

        | Is standaard | Staal beheerder | Beschrijving beheerder | Standaardstaal voor winkelweergave | Standaardbeschrijving van winkelweergave |
        |---|---|---|---|---|
        | nee | 4 | 4 | 4 | 4 |
        | nee | 24 | 24 | 24 | 24 |
        | nee | 30 | 30 | 30 | 30 |
        | nee | 60 | 60 | 60 | 60 |
        | nee | 68 | 68 | 68 | 68 |

      * Geavanceerde kenmerkeigenschappen:

         * Kenmerkcode: set_size
         * Bereik: Algemeen
         * Unieke waarde: Geen
         * Invoervalidatie voor winkeleigenaar: geen
         * Toevoegen aan kolomopties: Nee
         * Gebruiken in filteropties: Nee

   * Labels beheren:

      * Titels beheren (grootte, kleur, enz.)

         * Standaardweergave winkel: grootte instellen

   * Eigenschappen van Storefront:

      * Gebruiken in zoekopdracht: Ja
      * Zoekdikte: 1
      * Zichtbaar in Geavanceerd zoeken: Nee
      * Vergelijkbaar op Storefront: Ja
      * Gebruiken in gelaagde navigatie: Filterbaar (met resultaten)
      * Gebruiken in gelaagde navigatie met zoekresultaten: Ja
      * Gebruik voor de Voorwaarden van de Regel van de Aanbieding: Nr
      * Zichtbaar op cataloguspagina&#39;s in winkel: Ja
      * Gebruikt in productaanbieding: Ja
      * Gebruikt voor sorteren in productaanbieding: Nee

1. Voeg deze attributen aan het StandaardAttribuut toe binnen de Groep van de Details van het Product (**opslag** > **Attributen** > **Vastgestelde Attributen**) wordt geplaatst.
1. Download afbeeldingen die zijn ingesteld in de var map in de hoofdmap van Adobe Commerce.
1. Ga naar **Systeem** > **Overdracht van Gegevens** > en voer het dossier in gebruikend de hieronder opties:

   * Instellingen importeren:

      * Type entiteit: producten

   * Gedrag bij importeren:

      * Gedrag bij importeren: Toevoegen/Bijwerken
      * Validatiestrategie: stoppen bij fout
      * Aantal toegestane fouten: 1
      * Veldscheidingsteken: `;`
      * Scheidingsteken voor meerdere waarden: `,`
      * Constante kenmerkwaarde: EMPTYVALUE
      * Veldbijlage: uitgeschakeld

   * Te importeren bestand:

      * Te importeren bestand selecteren
      * Afbeeldingsbestandsmap: leeg laten

1. Ga naar de winkel op de `/product-set.html` -pagina en schakel tussen de verschillende Grootte instellen. Voor Set Size 24 is er geen galerie.

<u> Verwachte resultaten </u>:

De galerie voor alle eenvoudige producten binnen een configureerbaar product is zichtbaar met alle verwante beelden.

<u> Ware resultaten </u>:

Er is geen galerie voor de producten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
