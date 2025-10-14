---
title: 'MDVA-37725: E-mails die via niet-standaardsites worden verzonden, bevatten standaard URL''s van het logo van de site'
description: De patch MDVA-37725 verhelpt het probleem dat e-mails met asynchrone bestellingen worden verzonden via niet-standaard websites met logo-URL's van de standaardwebsite.
feature: Communications, Orders
role: Admin
exl-id: 6e72897c-7652-4b5a-8575-090e94188daf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# MDVA-37725: E-mails die via niet-standaardsites worden verzonden, bevatten standaard URL&#39;s van het logo van de site

>[!WARNING]
>
> De MDVA-37725-pleister is afgekeurd.

De patch MDVA-37725 verhelpt het probleem dat e-mails met asynchrone bestellingen worden verzonden via niet-standaard websites met logo-URL&#39;s van de standaardwebsite. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 geïnstalleerd is. De patch-id is MDVA-37725. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mails met asynchrone bestellingen worden verzonden via niet-standaard websites met de URL&#39;s van het logo van de standaardwebsite.

<u> Eerste vereisten </u>:

1. De tweede website/store/store-view moet zijn gemaakt.
1. **Asynchrone Verzendende** configuratie moet van **Opslag** worden toegelaten > **Montages** > **Configuratie** > **Verkoop** > **E-mail van de Verkoop** > **Algemene Montages**.
1. **voeg de Code van de Opslag aan URLs** configuratie toe wordt aangezet voor de gemakkelijke toegang tot van de secundaire website van **Opslag** > **Montages** > **Configuratie** > **Opties URL**.

<u> Stappen om </u> te reproduceren:

1. Plaats bestellingen in zowel de eerste als de tweede winkel.
1. Voer een uitsnede uit om de e-mails over verkopen te verzenden.
1. Controleer de e-mail van de tweede website.

<u> Verwachte resultaten </u>:

De URL van het logo van de e-mail bevat de URL van de tweede website.

<u> Ware resultaten </u>:

De URL van het logo van de e-mail bevat de URL van de standaardwebsite.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [&#x200B; flarden beschikbaar in QPT &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) sectie.
