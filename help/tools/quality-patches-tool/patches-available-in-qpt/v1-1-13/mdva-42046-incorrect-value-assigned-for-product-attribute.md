---
title: "MDVA-42046: Onjuiste waarde toegewezen voor productkenmerk"
description: De patch MDVA-42046 verhelpt het probleem waarbij een onjuiste waarde wordt toegewezen aan het kenmerk product bij het bijwerken van een product met een invoerveld voor de datum. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 is geïnstalleerd. De patch-id is MDVA-42046. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Attributes, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-42046: Onjuiste waarde toegewezen voor productkenmerk

De patch MDVA-42046 verhelpt het probleem waarbij een onjuiste waarde wordt toegewezen aan het kenmerk product bij het bijwerken van een product met een invoerveld voor de datum. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 geïnstalleerd is. De patch-id is MDVA-42046. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.3.5-p2 en 2.4.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Nadat u een product hebt opgeslagen met `news_from_date` - en/of `news_to_date` -velden, worden de waarden van die velden opnieuw ingesteld op de standaardwaarde.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Exporteer het product dat in stap 1 is gemaakt.
1. Plaats enkele waarden in de velden `news_from_date` en `news_to_date` in het geëxporteerde CSV-bestand. Bijvoorbeeld 2021-05-15 en 2021-06-18.
1. Importeer het product met het gewijzigde CSV-bestand.
1. Voeg aanvullende kolommen &quot;Product instellen als nieuw vanaf datum&quot; en &quot;Product instellen als nieuw op datum&quot; toe aan het productraster.
1. Open uitgeven pagina voor het product, en zonder enige veranderingen, klik **sparen**.
1. Ga terug naar het productraster en controleer de gegevens voor het product.

<u> Verwachte resultaten </u>:

Zowel &#39;Product instellen als Nieuw vanaf datum&#39; als &#39;Product instellen als Nieuw op datum&#39; zijn hetzelfde als vóór opslaan.

<u> Ware resultaten </u>:

* De waarden in de kolommen &quot;Product instellen als nieuw vanaf datum&quot; en &quot;Product instellen als nieuw op datum&quot; worden gewijzigd.

* De kolom &quot;Product instellen als nieuw op datum&quot; toont de huidige datum en de kolom &quot;Product instellen als nieuw op datum&quot; is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
