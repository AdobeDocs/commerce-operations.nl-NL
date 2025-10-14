---
title: 'MDVA-37592: Sorteren op prijs die niet werkt voor producten met prijs nul'
description: De MDVA-37592 Adobe Commerce-patch lost het probleem op dat sorteren op prijs niet correct werkt voor producten met prijs nul die aan een gedeelde catalogus worden toegewezen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 is geïnstalleerd. De patch-id is MDVA-37592. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-37592: Sorteren op prijs die niet werkt voor producten met prijs nul

De MDVA-37592 Adobe Commerce-patch lost het probleem op dat sorteren op prijs niet correct werkt voor producten met prijs nul die aan een gedeelde catalogus worden toegewezen. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0 geïnstalleerd is. De patch-id is MDVA-37592. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce op onze cloudarchitectuur 2.4.0-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatietypen) 2.3.6-2.4.2-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Sorteren op prijs werkt niet correct voor producten met prijs nul die aan een gedeelde catalogus wordt toegewezen.

<u> Eerste vereisten </u>:

B2B is geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Gedeelde catalogus inschakelen.
1. Maak vier producten met de volgende prijzen en wijs deze toe aan een categorie: $50, $60, $70 en $80.
1. Maak een gedeelde catalogus met de bovenstaande producten.
1. Stel de aangepaste prijs in op nul voor het product met een prijs van $70.
1. Creëer nu een bedrijfgebruiker en wijs het aan de gedeelde gemaakte catalogus toe.
1. Meld u aan met het bedrijfsaccount en blader naar de categorie waaraan de producten zijn toegewezen.
1. Probeer te sorteren op prijs.

<u> Verwachte resultaten </u>:

Het product met prijs nul wordt correct gesorteerd.

<u> Ware resultaten </u>:

Het product met prijs nul wordt NIET correct gesorteerd. In plaats daarvan wordt het gesorteerd op basis van de oorspronkelijke prijs.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
