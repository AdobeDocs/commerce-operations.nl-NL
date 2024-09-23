---
title: 'MDVA-39605: Redis cache TTL (vervaldatum) heeft onjuiste waarde'
description: De patch MDVA-39605 lost het probleem op waar de Redis cache TTL (vervaldatum) een verkeerde waarde heeft. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 is geïnstalleerd. De patch-id is MDVA-39605. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Cache, Console, Services
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# MDVA-39605: Redis cache TTL (vervaldatum) heeft onjuiste waarde

De patch MDVA-39605 lost het probleem op waar de Redis cache TTL (vervaldatum) een verkeerde waarde heeft. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 geïnstalleerd is. De patch-id is MDVA-39605. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De Redis cache-TTL (vervaldatum) heeft een onjuiste waarde.

<u> Stappen om </u> te reproduceren:

Om de moeilijke situatie te testen, spoel geheim voorgeheugen en open een configureerbaar product op de winkel. Open vervolgens een terminal (console) en volg de onderstaande stappen:

1. Voer de opdracht uit: `redis-cli`.
1. Uitvoeren `KEYS "*PRICE"` (er mag slechts één toets in het resultaat voorkomen, bijvoorbeeld `zc:ti:e54_PRICE` ). Kopieer de toets.
1. Voer `SMEMBERS` uit, gevolgd door de toets van de vorige stap (bijvoorbeeld `SMEMBERS zc:ti:e54_PRICE` ). Kopieer een willekeurige sleutel uit het resultaat (bijvoorbeeld e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Voer `KEYS "*<key>"` uit met de toetsnaam van de vorige stap om de volledige toetsnaam op te halen (bijvoorbeeld `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"` ). Het resultaat mag slechts één toets bevatten (bijvoorbeeld `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421` ). Zoals u merkt, is de volledige zeer belangrijke naam eenvoudig de zeer belangrijke naam met prefix &quot;`zc:k:`&quot;. Kopieer nu de volledige sleutelnaam.
1. Voer `HGETALL` uit, gevolgd door de volledige toetsnaam uit stap 4 om de waarde te controleren. De waarde zou geserialiseerde gegevens van bijbehorende producten van een verwant configureerbaar product moeten bevatten.
1. Voer `TTL` uit, gevolgd door de volledige toetsnaam uit stap 4, om te controleren of de toets een vervaldatum heeft. Het resultaat moet anders zijn dan **-1** en **-2** en moet ongeveer 2592000 (30 dagen) zijn. Hoewel de vervaldatum in de code één jaar is, geldt voor de Redis-bibliotheek die in Adobe Commerce wordt gebruikt een maximale vervaldatum van 2592000.

<u> Verwachte resultaten </u>:

Vervallimiet is 2592000s

<u> Ware resultaten </u>:

Vervallimiet wordt ingesteld op **-1** of **-2** .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
