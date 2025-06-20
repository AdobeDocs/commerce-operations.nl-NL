---
title: 'ACSD-51853: gekopieerde tekststijlen worden niet toegepast met behulp van de paginaontwikkelaar'
description: Pas de ACSD-51853-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de gekopieerde tekststijlen niet worden toegepast wanneer de paginaontwikkelaar wordt gebruikt.
feature: Page Builder
role: Admin
exl-id: fda5ba6e-4786-473c-a3a2-7356aa20f5ae
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-51853: gekopieerde tekststijlen worden niet toegepast met behulp van de paginaontwikkelaar

De ACSD-51853-patch verhelpt het probleem waarbij de gekopieerde tekststijlen niet worden toegepast wanneer de paginaontwikkelaar wordt gebruikt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.34 is geïnstalleerd. De patch-id is ACSD-51853. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gekopieerde tekststijlen worden niet toegepast wanneer de paginaontwikkelaar wordt gebruikt

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij Beheer.
1. Ga naar > **inhoud** > **pagina&#39;s** > **Open om het even welke pagina** > **geef met de Bouwer van de Pagina uit**.
1. De Rij van de belemmering en *Tekst* van **[!UICONTROL Elements]**.
1. Kopieer **verrijkte inhoud**, kleef die tekst in a **[!UICONTROL Page Builder]**.

<u> Verwachte resultaten </u>

De gekopieerde tekst wordt met alle stijlen geplakt.

<u> Ware resultaten </u>

De gekopieerde tekst wordt als platte tekst geplakt en alle stijlen gaan verloren.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
