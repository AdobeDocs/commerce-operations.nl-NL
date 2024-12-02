---
title: 'MDVA-31763: Catalogusprijsregels worden teruggedraaid totdat ze handmatig opnieuw worden berekend'
description: De patch MDVA-31763 lost het probleem op waarbij de prijsregels voor catalogi worden teruggedraaid tot de redex handmatig wordt uitgevoerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 is geïnstalleerd. De patch-id is MDVA-31763. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Catalog Management, Orders, Price Rules
role: Admin
exl-id: 1d144bfc-c26b-43d0-a80c-26a9c2d8ef32
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# MDVA-31763: Catalogusprijsregels worden teruggedraaid totdat ze handmatig opnieuw worden berekend

De patch MDVA-31763 lost het probleem op waarbij de prijsregels voor catalogi worden teruggedraaid tot de redex handmatig wordt uitgevoerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5 geïnstalleerd is. De patch-id is MDVA-31763. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer `catalogrule_product` gedeeltelijke indexeer op configureerbare producten wordt uitgevoerd, worden de catalogusregels verdwenen.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de beheerder-back-end.
1. Ga naar **Opslag** > **Attributen** > **Product** en onderzoek naar de &quot;fabrikant&quot;attributen.
   * Voeg een paar opties toe en plaats &quot;Gebruik voor de Voorwaarden van de Regel van de Bevordering&quot;aan *ja*.
1. Ga naar **Slaat** > **Attributen** > **Reeksen van Attributen** op.
   * Selecteer de standaardkenmerkset en voeg het kenmerk &quot;manufacturer&quot; eraan toe.
1. Maak een configureerbaar product met een paar variaties.
1. Stel de waarde van het kenmerk &quot;manufacturer&quot; in voor eerder gemaakt configureerbaar product.
1. Catalogusregels maken:
   * Actief = Ja
   * Websites = hoofdwebsite
   * Klantengroepen = NIET AANGEMELD
   * Voorwaarden: fabrikant = \&lt;geselecteerde waarde voor configureerbaar product>
   * Handelingen: elke korting
1. Voer een volledige index uit.
1. Controleer de productprijs op PDP en controleer of de prijs correct is.
1. Werk het &quot;gewicht&quot;attribuut van het gecreeerde configureerbare product bij.
1. Controleer de productprijs op PDP.

<u> Verwachte resultaten </u>:

De catalogusprijsregels die zijn ingesteld voor configureerbare producten worden niet verwijderd tijdens een gedeeltelijke herindex.

<u> Ware resultaten </u>:

De catalogusprijsregels die zijn ingesteld voor configureerbare producten, zijn verdwenen tijdens een gedeeltelijke herindexering.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
